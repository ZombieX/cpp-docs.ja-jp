---
title: ARM 例外処理 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fe0e615f-c033-4ad5-97f4-ff96af45b201
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae80e1f7f824f41f6bc0b3f979973f5867666354
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861656"
---
# <a name="arm-exception-handling"></a>ARM 例外処理

ARM 版 Windows は、ハードウェアで生成される非同期例外とソフトウェアで生成される同期例外に対して、同じ構造化例外処理メカニズムを使用します。 言語固有の例外ハンドラーは、言語ヘルパー関数を使用することで、Windows 構造化例外処理に付加して構築します。 このドキュメントでは、ARM、および Microsoft ARM アセンブラーおよび Visual C コンパイラによって生成されるコードで使用する言語ヘルパーでの Windows での例外処理について説明します。

## <a name="arm-exception-handling"></a>ARM 例外処理

ARM 上の Windows を使用して*アンワインド コード*中にスタック アンワインドを制御する[例外処理を構造化](https://msdn.microsoft.com/library/windows/desktop/ms680657)(SEH)。 アンワインド コードは、実行可能イメージの .xdata セクションに格納されるバイトのシーケンスです。 これらのコードには、関数のプロローグおよびエピローグ コードの演算を抽象的な方法で記述し、呼び出し元のスタック フレームへのアンワインドに備えて、関数のプロローグの効果を元に戻すことができるようにします。

ARM EABI (埋め込みアプリケーション バイナリ インターフェイス) には、アンワインド コードを使用する例外アンワインド モデルを指定しますが、Windows での SEH アンワインドの場合、プロセッサが関数のプロローグまたはエピローグの途中にある非同期の場合を処理する必要があるため、これは十分ではありません。 また、Windows では、アンワインド制御が関数レベルのアンワインドと言語固有スコープのアンワインドに分離されます。これは、ARM EABI で統合されます。 これらの理由から、ARM 版 Windows では、アンワインドのデータと手順の詳細が指定されます。

### <a name="assumptions"></a>外部からの影響

ARM 版 Windows 用の実行可能イメージでは、移植可能な実行可能 (PE) 形式が使用されます。 詳細については、次を参照してください。 [Microsoft PE and COFF 仕様](http://go.microsoft.com/fwlink/p/?linkid=84140)します。 例外処理情報は、イメージの .pdata および .xdata セクションに格納されます。

例外処理メカニズムでは、ARM 版 Windows の ABI に従うコードについて、次のことを想定しています。

- 関数本体内で例外が発生した場合に、プロローグの演算が元に戻されるか、先に進んでエピローグの演算が実行されるかは関係ありません。 両方の場合で同じ結果となります。

- 通常、プロローグとエピローグは、相互にミラー化されます。 このことを利用して、アンワインドの記述に必要なメタデータのサイズを削減できます。

- 関数は、比較的小さい傾向があります。 最適化のために、このことを利用してデータを効率的にパッキングすることがあります。

- エピローグに条件が置かれた場合、その条件はエピローグ内の各命令に一様に適用されます。

- スタック ポインター (SP) がプロローグで別のレジスタに保存される場合は、元の SP をいつでも復元できるように、そのレジスタを関数全体で変更なく保つ必要があります。

- SP が別のレジスタに保存されていない限り、SP に対するすべての操作は、厳密にプロローグおよびエピローグ内で発生する必要があります。

- 任意のスタック フレームをアンワインドするには、次の操作が必要です。

  - r13 (SP) を 4 バイト刻みで調整します。

  - 1 つ以上の整数レジスタをポップします。

  - 1 つ以上の VFP (仮想浮動小数点) レジスタをポップします。

  - 任意のレジスタ値を r13 (SP) にコピーします。

  - 小さな後置デクリメント演算を使用して、SP をスタックからロードします。

  - いくつかの適切に定義されたフレーム タイプの 1 つを解析します。

### <a name="pdata-records"></a>.pdata レコード

PE 形式イメージ内の .pdata レコードは、各スタック操作関数を記述する、固定長項目の順序付けされた配列です。 リーフ関数は他の関数を呼び出さないため、スタックを操作しない場合には .pdata レコードを必要としません (つまり、ローカル ストレージを必要とせず、非 volatile レジスタを保存または復元する必要がありません)。 領域を節約するために、これらの関数のレコードを.pdata セクションから省略できます。 これらの関数のいずれかからのアンワインド操作では、リンク レジスタ (LR) からプログラム カウンター (PC) へリターン アドレスをコピーして、呼び出し元に移動することのみが可能です。

ARM のすべての .pdata レコードは、8 バイトの長さです。 一般的なレコードの形式では、次の表に示すように、最初の 32 ビット ワードに関数の開始の相対仮想アドレス (RVA) が配置され、その後の 2 番目のワードには可変長 .xdata ブロックへのポインター、または標準関数アンワインド シーケンスを記述するパックされたワードが含まれます。

|ワード オフセット|ビット|目的|
|-----------------|----------|-------------|
|0|0-31|*関数の開始の RVA*は関数の先頭の 32 ビットの rva を示します。 関数に Thumb コードが含まれている場合は、このアドレスの下位ビットを設定する必要があります。|
|1|0-1|*フラグ*は 2 番目の .pdata ワードの残りの 30 ビットを解釈する方法を示す 2 ビット フィールドです。 場合*フラグ*は 0 です。 その後、残りのビット フォーム、*例外情報 RVA* (下位 2 ビットで暗黙的に 0)。 場合*フラグ*フォーム、残りのビットが 0 以外の場合、*パックされたアンワインド データ*構造体。|
|1|2-31|*例外情報 RVA*または*パックされたアンワインド データ*します。<br /><br /> *例外情報 RVA* .xdata セクションに格納された可変長例外情報構造のアドレスです。 このデータは、4 バイトでアラインされている必要があります。<br /><br /> *アンワインド データをパック*は正規の形式と仮定すると、関数からのアンワインドに必要な操作の圧縮の説明です。 この場合、.xdata レコードは必要ありません。|

### <a name="packed-unwind-data"></a>パックされたアンワインド データ

関数のプロローグおよびエピローグが下に示す標準形式に従っている場合、パックされたアンワインド データを使用できます。 これにより .xdata レコードが必要なくなり、アンワインド データの提供に必要な領域が大幅に削減されます。 標準のプロローグおよびエピローグは、例外ハンドラーを必要とせず、セットアップおよび終了操作を標準的な順序で実行する単純な関数に共通する要件を満たすように設計されています。

次の表は、パックされたアンワインド データが含まれる .pdata レコードの形式を示しています。

|ワード オフセット|ビット|目的|
|-----------------|----------|-------------|
|0|0-31|*関数の開始の RVA*は関数の先頭の 32 ビットの rva を示します。 関数に Thumb コードが含まれている場合は、このアドレスの下位ビットを設定する必要があります。|
|1|0-1|*フラグ*を次の意味を持つ 2 ビット フィールドです。<br /><br />-00 = パックされたアンワインド データは使用されません。残りのビットは .xdata レコードをポイントします。<br />-01 = パックされたアンワインド データです。<br />-10 = パックされたアンワインド データの場所、関数がプロローグがないと見なされます。 関数の開始から分離している関数フラグメントの記述に役立ちます。<br />-11 = 予約済み。|
|1|2-12|*関数の長さ*は 2 で割った値をバイト単位で関数全体の長さを提供する 11 ビット フィールドです。 関数が 4KB より大きい場合、フル .xdata レコードを代わりに使用する必要があります。|
|1|13-14|*Ret*は、関数を返す方法を示す 2 ビット フィールドです。<br /><br />-00 = pop {pc} を介して戻されます (、 *L*フラグのビットをここで 1 に設定する必要があります)。<br />-01 16 ビット分岐を使用して戻り値を = です。<br />-10 32 ビット分岐を使用して戻り値を = です。<br />-11 エピローグをまったく = なし。 プロローグのみが含まれ、エピローグは他の場所にある分離された関数フラグメントの記述に役立ちます。|
|1|16|*H*は、関数が整数パラメーターを「ホーム」しているかどうかを示す 1 ビット フラグは、関数の開始時にプッシュして (r0 r3) を登録し、戻る前にスタックの 16 バイトの割り当てを解除します。 (0 = レジスタを元に戻しません、1 = レジスタを元に戻します。)|
|1|16-18|*Reg*最後のインデックスを示す 3 ビット フィールドは非 volatile レジスタを保存します。 場合、 *R*ビットが 0 の場合、整数レジスタのみが保存されると、r4 rN、N は 4 の範囲であると見なされます + *Reg*します。場合、 *R*ビットが 1、その後のみ浮動小数点レジスタが保存されると、d8 dN、N は 8 の範囲であると見なされます + *Reg*します。特別な組み合わせ*R* = 1 と*Reg* = 7 では、レジスタが保存されていないことを示します。|
|1|19|*R*保存された非 volatile レジスタが整数レジスタ (0) かどうか、または浮動小数点レジスタ (1) を示す 1 ビット フラグです。 場合*R* 1 に設定されていると、 *Reg*フィールドが 7 に設定されている、非 volatile レジスタがプッシュされることはありません。|
|1|20|*L*かどうか、関数の保存/復元、LR で示されるその他のレジスタと共にを示す 1 ビット フラグは、 *Reg*フィールド。 (0 = 保存/復元を行わない、1 = 保存/復元を行う。)|
|1|21|*C*関数が (0) かどうか (1) のウォーク高速のスタックのフレーム チェーンを設定する追加の命令を含めるかどうかを示す 1 ビット フラグです。 このフラグが設定されている場合、保存された非 volatile 整数レジスタのリストに r11 が暗黙的に追加されています。 (場合は、次の制限を表示、 *C*フラグを使用します)。|
|1|22-31|*スタック調整*はこの関数は、4 で割った値に割り当てられているスタックのバイト数を示す 10 ビット フィールドです。 ただし、0x000 ～ 0x3F3 の間の値のみを直接エンコード可能です。 4,044 バイトを超えるスタックを割り当てる関数は、フル .xdata レコードを使用する必要があります。 場合、*スタック調整*フィールドが 0x3F4 以上、下位 4 ビットは特別な意味を持つ。<br /><br />ビット 0-1 は、スタック調整 (1 ~ 4) から 1 を引いたの単語の数を示します。<br />プロローグは、プッシュ操作には、この調整を組み合わせる場合、ビット 2 が 1 に設定されます。<br />エピローグこの調整をポップ操作にいる場合、ビット 3 が 1 に設定します。|

上のエンコーディングに冗長性がある可能性があるため、次の制限が適用されます。

- 場合、 *C*フラグが 1 に設定します。

   - *L*フレーム チェーン、r11 と LR の両方に必要なために、フラグを 1 に設定もする必要があります。

   - 記述されたレジスタのセットに r11 を含めることがない必要がある*Reg*します。つまり r4 r11 がプッシュされる場合は、 *Reg*ため、r4-r10 は説明する必要がありますのみ、 *C* r11 を意味するフラグ。

- 場合、 *Ret*フィールドが 0 に設定されている、 *L*フラグを 1 に設定する必要があります。

これらの制限に違反すると、サポートされないシーケンスが発生します。

以下の説明のために、2 つの擬似フラグがから派生した*スタック調整*:

- *PF*いることを示してプロローグの折りたたみ*スタック調整*が 0x3F4 以上で、ビット 2 が設定されます。

- *EF*いることを示してエピローグの折りたたみ*スタック調整*が 0x3F4 以上で、ビット 3 が設定されます。

標準関数のプロローグには、最大 5 個の命令を含めることができます (3a と 3b は同時に指定できません)。

|命令|オペコードが想定される条件|サイズ|オペコード|アンワインド コード|
|-----------------|-----------------------------------|----------|------------|------------------|
|1|*H*1 = =|16|`push {r0-r3}`|04|
|2|*C*1 = = または*L*1 = = または*R*0 または PF を = = 1 = =|16/32|`push {registers}`|80-BF/D0-DF/EC-ED|
|3a|*C*1 = = と (*L*0 を = = と*R*1 から PF を = = 0 を = =)|16|`mov r11,sp`|C0-CF/FB|
|3b|*C*1 = = と (*L*1 = = または*R*0 または PF を = = 1 = =)|32|`add r11,sp,#xx`|FC|
|4|*R*1 = = と*Reg* ! = 7|32|`vpush {d8-dE}`|E0-E7|
|5|*スタック調整*! = 0 および PF 0 を = =|16/32|`sub sp,sp,#xx`|00-7F/E8-EB|

命令 1 は常に存在場合、 *H*ビットが 1 に設定します。

フレーム チェーンを設定すると、命令 3a または 3b のどちらかが存在する場合、 *C*ビットが設定されます。 r11 および LR 以外のレジスタがプッシュされていない場合、16 ビット `mov` となり、その他の場合は 32 ビット `add` となります。

折りたたまれない調整が指定された場合、命令 5 は明示的なスタック調整です。

命令 2 および 4 は、プッシュが必要かどうかに基づいて設定されます。 この表では、レジスタの保存はに基づいて、 *C*、 *L*、 *R*、および*PF*フィールド。 すべてのケースで*N*と等しい*Reg*は + 4、 *E*と等しい*Reg* + 8、および*S*と等しい (~*スタック調整*)) (& 3。

|C|L|R|PF|プッシュされる整数レジスタ|プッシュされる VFP レジスタ|
|-------|-------|-------|--------|------------------------------|--------------------------|
|0|0|0|0|r4 r*N*|none|
|0|0|0|1|r*S*-r*N*|none|
|0|0|1|0|none|d8 d*E*|
|0|0|1|1|r*S*-r3|d8 d*E*|
|0|1|0|0|r4 r*N*、LR|none|
|0|1|0|1|r*S*-r*N*、LR|none|
|0|1|1|0|LR|d8 d*E*|
|0|1|1|1|r*S*-r3、LR|d8 d*E*|
|1|0|0|0|r4 r*N*、r11|none|
|1|0|0|1|r*S*-r*N*、r11|none|
|1|0|1|0|r11|d8 d*E*|
|1|0|1|1|r*S*-r3、r11|d8 d*E*|
|1|1|0|0|r4 r*N*r11、LR|none|
|1|1|0|1|r*S*-r*N*r11、LR|none|
|1|1|1|0|r11, LR|d8 d*E*|
|1|1|1|1|r*S*-r3、r11、LR|d8 d*E*|

標準関数のエピローグは同様の形式に従いますが、逆順になり、いくつかのオプションが追加されます。 エピローグは最大 5 命令の長さとなり、その形式はプロローグの形式によって厳密に規定されています。

|命令|オペコードが想定される条件|サイズ|オペコード|
|-----------------|-----------------------------------|----------|------------|
|6|*スタック調整*! = 0 と*EF*0 を = =|16/32|`add   sp,sp,#xx`|
|7|*R*1 = = と*Reg*! = 7|32|`vpop  {d8-dE}`|
|8|*C*1 = = または (*L*1 = = と*H*0 を = =) または*R*0 を = = または*EF*1 = =|16/32|`pop   {registers}`|
|9a|*H*1 = = と*L*0 を = =|16|`add   sp,sp,#0x10`|
|9b|*H*1 = = と*L*1 = =|32|`ldr   pc,[sp],#0x14`|
|10a|*Ret*1 = =|16|`bx    reg`|
|10b|*Ret*2 = =|32|`b     address`|

折りたたまれない調整が指定された場合、命令 6 は明示的なスタック調整です。 *PF*に依存しない*EF*命令 5 は存在せず、命令 6、またはその逆を含めることは可能になります。

命令 7 と 8 はプロローグと同じロジックを使用して、スタックから復元されるレジスタを決定するが、2 つ変更するとしますまず、 *EF*の代わりに使用されます*PF*もう 1 つは、場合*Ret。* LR が PC レジスタの一覧で置き換えられ、エピローグが直ちに終了し、0 を = です。

場合*H*命令 9a または 9b が存在し、設定されます。 命令 9a が使用されるときに*L*は 0、LR がスタックにないことを示すです。 この場合、スタックは手動で調整し、 *Ret* 1 または 2、明示的な戻り値を指定する必要があります。 命令 9b が使用されるときに*L*エピローグの早期終了を示すと戻りし、調整の同時に、スタックを 1 に設定されています。

値に基づいて、エピローグがまだ終了していない、し、命令 10a または 10b が存在する、16 ビットまたは 32 ビット分岐を示す、 *Ret*します。

### <a name="xdata-records"></a>.xdata レコード

パックされたアンワインド形式では関数のアンワインドの記述に十分でない場合、可変長の .xdata レコードを作成する必要があります。 このレコードのアドレスは、.pdata レコードの第 2 ワードに格納されています。 .xdata の形式は、次の 4 つのセクションのある、パックされた可変長ワード セットです。

1. .xdata 構造体全体のサイズを記述し、主な関数データを提供する 1 ～ 2 ワードのヘッダー。 2 番目の単語には場合にのみ存在、*エピローグ カウント*と*ごまかして*フィールドは両方とも 0 に設定します。 次の表で、各フィールドについて詳細に説明します。

   |Word|ビット|目的|
   |----------|----------|-------------|
   |0|0-17|*関数の長さ*は 2 で除算してバイト単位の関数の合計長を示す 18 ビット フィールドです。 関数が 512 KB より大きい場合、複数の .pdata および .xdata レコードを使用して関数を記述する必要があります。 詳細については、このドキュメントの「大きな関数」セクションを参照してください。|
   |0|18-19|*バージョン*は残りの xdata のバージョンを示す 2 ビット フィールドです。 現在、バージョン 0 のみが定義されています。値 1 ～ 3 は予約済みです。|
   |0|20|*X*は例外データの (0) がない場合、または (1) の存在を示す 1 ビット フィールドです。|
   |0|21|*E*以降 (0) の単語を追加のスコープを必要とするのではなく 1 つのエピローグを記述する情報が (1) ヘッダーにパックされていることを示す 1 ビット フィールドです。|
   |0|22|*F*関数フラグメント (1) か、関数全体 (0) にこのレコードについて説明することを示す 1 ビット フィールドです。 フラグメントは、プロローグが存在せず、すべてのプロローグ処理が無視されることを意味します。|
   |0|23-27|*エピローグ カウント*の状態に応じて 2 つの意味を持つ 5 ビット フィールド、 *E*ビット。<br /><br /> If *E*は 0、このフィールドは 3 のセクションで説明される例外スコープの合計数。 関数をこのフィールドに 31 を超えるスコープが存在しない場合、*ごまかして*フィールドする必要がありますどちらも 0 に設定する、拡張ワードが必要であることを示します。<br />If *E*は 1 です。 このフィールドはエピローグのみを記述する最初のアンワインド コードのインデックスを指定します。|
   |0|28-31|*コード ワード*はすべてセクション 4 では、アンワインド コードの格納に必要な 32 ビット ワードの数を指定する 4 ビット フィールドです。 15 を超える単語が 63 を超えるアンワインド コード バイト、このフィールドに必要な場合は、*エピローグ カウント*フィールドする必要がありますどちらも 0 に設定する、拡張ワードが必要であることを示します。|
   |1|0-15|*エピローグの数を拡張*はエピローグの数が異常に多いをエンコードするためのより多くの領域を提供する 16 ビット フィールドです。 このフィールドが含まれる拡張ワードは、場合にのみ存在、*エピローグ カウント*と*ごまかして*ヘッダーの最初の単語内のフィールドは両方とも 0 に設定します。|
   |1|16-23|*拡張コード ワード*はアンワインド コード ワードの数が異常に多いをエンコードするためのより多くの領域を提供する 8 ビット フィールドです。 このフィールドが含まれる拡張ワードは、場合にのみ存在、*エピローグ カウント*と*ごまかして*ヘッダーの最初の単語内のフィールドは両方とも 0 に設定します。|
   |1|24-31|予約されています。|

1. 例外データの後に (場合、 *E*ヘッダー内のビットが 0 に設定された) が 1 つの単語をまとめられ、開始オフセットの昇順に格納されているエピローグ スコープに関する情報の一覧を示します。 各スコープには、次のフィールドが含まれます。

   |ビット|目的|
   |----------|-------------|
   |0-17|*エピローグ開始オフセット*は関数の先頭からの相対 2 で除算してバイト単位で、エピローグのオフセットを記述する 18 ビット フィールドです。|
   |18-19|*Res* 2 ビット フィールドが将来拡張するために予約されています。 この値は 0 である必要があります。|
   |20-23|*条件*は、エピローグが実行される条件を提供する 4 ビット フィールドです。 条件を伴わないエピローグの場合、このフィールドは 0xE、つまり "常時" に設定する必要があります。 (エピローグは、全体が条件付きであるか全体が条件なしである必要があります。また、Thumb-2 モードでは、エピローグは IT オペコードの後の最初の命令で開始します。)|
   |24-31|*エピローグ開始インデックス*はこのエピローグを記述する最初のアンワインド コード バイトのインデックスを示す 8 ビット フィールドです。|

1. エピローグ スコープのリストの後には、アンワインド コードを含むバイトの配列 (詳細については、この記事の「アンワインド コード」セクションを参照) が存在します。 この配列は、最も近いフルワード境界の末尾に埋め込まれます。 バイトは、リトル エンディアン順で格納され、リトル エンディアン モードで直接フェッチ可能になっています。

1. 場合、 *X*ヘッダー内のフィールドが 1 の場合、アンワインド コード バイトの例外ハンドラーの情報が続きます。 1 つから成る*例外ハンドラーの RVA* (可変長) の例外ハンドラーで必要なデータ量をすぐに続く、例外ハンドラーのアドレスを格納しています。

.xdata レコードは、最初の 8 バイトをフェッチしてフル サイズのレコード (後続の可変サイズの例外の長さは含まれない) を計算できるように設計されています。 次のコード スニペットはレコードのサイズを計算します。

```cpp
ULONG ComputeXdataSize(PULONG *Xdata)
{
    ULONG EpilogueScopes;
    ULONG Size;
    ULONG UnwindWords;

    if ((Xdata[0] >> 23) != 0) {
        Size = 4;
        EpilogueScopes = (Xdata[0] >> 23) & 0x1f;
        UnwindWords = (Xdata[0] >> 28) & 0x0f;
    } else {
        Size = 8;
        EpilogueScopes = Xdata[1] & 0xffff;
        UnwindWords = (Xdata[1] >> 16) & 0xff;
    }

    if (!(Xdata[0] & (1 << 21))) {
        Size += 4 * EpilogueScopes;
    }
    Size += 4 * UnwindWords;
    if (Xdata[0] & (1 << 20)) {
        Size += 4;
    }
    return Size;
}
```

プロローグおよび各エピローグにはアンワインド コードのインデックスがありますが、表はこれらの間で共有されます。 これらすべてが同じアンワインド コードを共有できることは、ほとんどありません。 コンパイラの作成者がこの状況に合わせて最適化することをお勧めします。これは、指定可能な最も大きいインデックスは 255 であり、このことによって、特定の関数に対して許容されるアンワインド コードの合計数が制限されるためです。

### <a name="unwind-codes"></a>アンワインド コード

アンワインド コードの配列は、プロローグの効果を元に戻す方法を、操作を元に戻す順序に従って正確に記述した命令シーケンスのプールです。 アンワインド コードは、小型の命令セットで、バイト列としてエンコードされます。 実行が完了すると、呼び出し元関数へのリターン アドレスが LR レジスタに入り、すべての非 volatile レジスタが関数が呼び出された時点の値に復元されます。

例外が関数本体のみで発生し、プロローグまたはエピローグでは絶対に発生しないことが保証されている場合、必要なアンワインド シーケンスは 1 つのみです。 ただし、Windows アンワインド モデルでは、部分的に実行されたプロローグまたはエピローグからアンワインドする機能が求められます。 この要件に対応するため、アンワインド コードはプロローグおよびエピローグ内の関連オペコードへの明確な 1 対 1 のマッピングを持つように慎重に設計されています。 これは、次のような結果をもたらします。

- アンワインド コードの数のカウントによるプロローグおよびエピローグの長さの計算が可能です。 16 ビットおよび 32 ビット オペコードの明確なマッピングがあるため、これは可変長 Thumb-2 命令を使用しても可能です。

- エピローグ スコープの開始後の命令数をカウントすることにより、同等数のアンワインド コードをスキップし、残りのシーケンスを実行して、エピローグが実行していた部分的に実行されたアンワインドを完了することが可能です。

- プロローグの終了前の命令数をカウントすることにより、同等数のアンワインド コードをスキップし、残りのシーケンスを実行して、実行が完了したプロローグの部分のみを元に戻すことが可能です。

次の表に、アンワインド コードからオペコードへのマッピングを示します。 最も一般的なコードは、1 バイトのみです。あまり一般的ではないものは、2、3、または 4 バイトを必要とします。 各コードは、最上位バイトから最下位バイトへと格納されています。 このアンワインド コード構造体は、ARM EABI で記述されるエンコーディングとは異なります。これは、これらのアンワインド コードが、部分的に実行されたプロローグおよびエピローグのアンワインドを可能にするために、プロローグおよびエピローグ内のオペコードに 1 対 1 でマッピングするように設計されているためです。

|バイト 1|バイト 2|バイト 3|バイト 4|オペコード サイズ|説明|
|------------|------------|------------|------------|------------|-----------------|
|00-7F||||16|`add   sp,sp,#X`<br /><br /> X は (Code & 0x7F) \* 4|
|80-BF|00-FF|||32|`pop   {r0-r12, lr}`<br /><br /> Code & 0x2000 の場合 LR がポップされ、対応するビットが Code & 0x1FFF で設定されている場合 r0-r12 がポップされます。|
|C0-CF||||16|`mov   sp,rX`<br /><br /> X は Code & 0x0F|
|D0-D7||||16|`pop   {r4-rX,lr}`<br /><br /> X は (Code & 0x03) + 4、Code & 0x04 の場合 LR がポップされます|
|D8-DF||||32|`pop   {r4-rX,lr}`<br /><br /> X は (Code & 0x03) + 8、Code & 0x04 の場合 LR がポップされます|
|E0-E7||||32|`vpop  {d8-dX}`<br /><br /> X は (Code & 0x07) + 8|
|E8-EB|00-FF|||32|`addw  sp,sp,#X`<br /><br /> X は (Code & 0x03FF) \* 4|
|EC-ED|00-FF|||16|`pop   {r0-r7,lr}`<br /><br /> Code & 0x0100 の場合 LR がポップされ、対応するビットが Code & 0x00FF で設定されている場合 r0-r7 がポップされます。|
|EE|00-0F|||16|Microsoft 固有の仕様|
|EE|10-FF|||16|使用可能|
|EF|00-0F|||32|`ldr   lr,[sp],#X`<br /><br /> X は (Code & 0x000F) \* 4|
|EF|10-FF|||32|使用可能|
|F0-F4||||-|使用可能|
|F5|00-FF|||32|`vpop  {dS-dE}`<br /><br /> S は (Code & 0x00F0) >> 4、E は Code & 0x000F|
|F6|00-FF|||32|`vpop  {dS-dE}`<br /><br /> S は ((Code & 0x00F0) >> 4) + 16、E は (Code & 0x000F) + 16|
|F7|00-FF|00-FF||16|`add   sp,sp,#X`<br /><br /> X は (Code & 0x00FFFF) \* 4|
|F8|00-FF|00-FF|00-FF|16|`add   sp,sp,#X`<br /><br /> X は (Code & 0x00FFFFFF) \* 4|
|F9|00-FF|00-FF||32|`add   sp,sp,#X`<br /><br /> X は (Code & 0x00FFFF) \* 4|
|FA|00-FF|00-FF|00-FF|32|`add   sp,sp,#X`<br /><br /> X は (Code & 0x00FFFFFF) \* 4|
|FB||||16|nop (16 ビット)|
|FC||||32|nop (32 ビット)|
|FD||||16|end + エピローグに 16 ビットの nop|
|FE||||32|end + エピローグに 32 ビットの nop|
|FF||||-|end|

アンワインド コード バイトごとに 16 進数の値の範囲が表示されます*コード*、オペコード サイズと共に*Opsize*と対応する元の命令解釈します。 空白のセルは、短いアンワインド コードを示しています。 複数のバイトをカバーする大きな値を持つ命令では、最上位ビットが最初に格納されます。 *Opsize*フィールドには、各 thumb-2 演算に関連付けられている暗黙的なオペコード サイズが表示されます。 表内の異なるエンコーディングの明らかな重複項目は、異なるオペコード サイズの区別に使用されます。

アンワインド コードは、コードの最初のバイトがコードの合計サイズ (バイト) と命令ストリーム内の対応するオペコードのサイズの両方を示すように設計されています。 プロローグまたはエピローグのサイズを計算するには、アンワインド コードをシーケンスの最初から最後まで調べて、ルックアップ テーブルまたは同様の方法を使用して対応するオペコードの長さを特定します。

アンワインド コード 0xFD および 0xFE は、通常の終了コード 0xFF と同等ですが、エピローグの場合は 16 ビットまたは 32 ビットの特別な nop オペコードに相当します。 プロローグでは、コード 0xFD、0xFE および 0xFF は正確に同等です。 これは、一般的なエピローグの終了 `bx lr` または `b <tailcall-target>` に相当します。同等のプロローグ命令はありません。 これにより、アンワインド シーケンスをプロローグとエピローグの間で共有できる機会が増えます。

多くの場合、プロローグとすべてのエピローグで同じアンワインド コードのセットを使用することが可能です。 ただし、部分的に実行されたプロローグおよびエピローグのアンワインドを処理するには、順序や動作が異なる複数のアンワインド コード シーケンスが必要となる場合があります。 このため、それぞれのエピローグに、実行を開始する場所を示すアンワインド配列への独自のインデックスがあります。

### <a name="unwinding-partial-prologues-and-epilogues"></a>部分的なプロローグおよびエピローグのアンワインド

アンワインドが行われる状況としては、プロローグやすべてのエピローグではなく、関数の本体で例外が発生した場合が最も一般的です。 この場合は、アンワインダーが、アンワインド配列内のコードを、インデックス 0 から終了オペコードが検出されるまで実行します。

プロローグまたはエピローグの実行中に例外が発生した場合、スタック フレームは部分的にのみ構築されており、正しく元に戻すには、アンワインダーは実行された内容を正確に特定する必要があります。

たとえば、次のプロローグおよびエピローグ シーケンスの場合を考えます。

```asm
0000:   push  {r0-r3}         ; 0x04
0002:   push  {r4-r9, lr}     ; 0xdd
0006:   mov   r7, sp          ; 0xc7
...
0140:   mov   sp, r7          ; 0xc7
0142:   pop   {r4-r9, lr}     ; 0xdd
0146:   add   sp, sp, #16     ; 0x04
0148:   bx    lr
```

各オペコードの次には、この演算を記述する適切なアンワインド コードがあります。 プロローグのアンワインド コード シーケンスは、エピローグのアンワインド コードのミラー イメージになっています。 この状況は一般的であり、このため、プロローグのアンワインド コードがプロローグの実行順と逆の順序で格納されることが常に想定されます。 これにより、次のアンワインドコードの共通セットが提供されます。

```asm
0xc7, 0xdd, 0x04, 0xfd
```

0xFD コードは、シーケンスの終了用の特別なコードであり、エピローグがプロローグよりも長い、1 つの 16 ビット命令であることを意味します。 これにより、より多くのアンワインド コードの共有が可能になっています。

この例では、プロローグとエピローグの間の関数本体の実行中に例外が発生した場合、アンワインドはエピローグの場合で、エピローグ コード内のオフセット 0 で開始されます。 これは、例のオフセット 0x140 に対応します。 クリーンアップは行われていないため、アンワインダーは、アンワインド シーケンス全体を実行します。 一方、例外がエピローグ コードの開始後の 1 つの命令で発生した場合、アンワインダーは最初のアンワインド コードをスキップして正常にアンワインドできます。 オペコードの間の一対一のマッピングを指定し、命令からのアンワインドの場合、アンワインド コード*n* 、エピローグ内、アンワインダーは最初をスキップする必要があります*n*アンワインド コード。

プロローグでは同様のロジックが逆に機能します。 プロローグ内のオフセット 0 からのアンワインドの場合、処理を実行する必要はありません。 プロローグ内のある命令からのアンワインドの場合、プロローグ アンワインド コードは逆順で格納されているため、アンワインド シーケンスは 1 つのアンワインド コードを末尾から開始する必要があります。 命令からのアンワインドの場合は、一般的なケースで*n* 、プロローグのアンワインドする必要がありますの実行を開始で*n*アンワインド コードの一覧の末尾からのコード。

プロローグとエピローグのアンワインド コードは、正確に一致していない場合があります。 この場合、アンワインド コード配列にコードのシーケンスがいくつか含まれている必要がある場合があります。 コードの処理を開始するオフセットを特定するには、次のロジックを使用します。

1. 関数本体内からのアンワインドの場合、インデックス 0 でアンワインド コードの実行を開始し、終了オペコードに到達するまで続行します。

2. エピローグ内からのアンワインドの場合、エピローグ スコープにより提供されるエピローグ固有の開始インデックスを使用します。 エピローグの開始からの PC のバイト数を計算します。 既に実行済みの命令がすべて含まれるまでアンワインド コードを前方にスキップします。 その位置で開始するアンワインド シーケンスを実行します。

3. プロローグ内からのアンワインドの場合、アンワインド コードのインデックス 0 から開始します。 シーケンスからプロローグ コードの長さを計算し、プロローグの末尾から PC までのバイト数を計算します。 未実行の命令がすべて含まれるまでアンワインド コードを前方にスキップします。 その位置で開始するアンワインド シーケンスを実行します。

プロローグのアンワインド コードは、常に配列の最初に存在する必要があります。 これらは、本体内からのアンワインドという一般的な場合のアンワインドに使用されるコードでもあります。 すべてのエピローグ固有のシーケンスは、プロローグ コード シーケンスの直後に続く必要があります。

### <a name="function-fragments"></a>関数フラグメント

コードの最適化のために、関数を個別の部分に分割すると便利な場合があります。 このようにすると、各関数フラグメントには、個別の .pdata レコードと、場合によっては .xdata が必要となります。

関数プロローグが関数の先頭にあり分割できない場合は、4 つの関数フラグメントが考えられます。

- プロローグのみ: すべてのエピローグは別のフラグメントにあります。

- プロローグと 1 つ以上のエピローグ: 追加のエピローグが別のフラグメントにあります。

- プロローグまたはエピローグなし: プロローグおよび 1 つ以上のエピローグが別のフラグメントにあります。

- エピローグのみ: プロローグ、および場合によっては追加のエピローグが別のフラグメントにあります。

1 番目の場合では、プロローグのみを記述する必要があります。 これを通常どおりプロローグを記述し、指定コンパクト .pdata 形式で行うことができます、 *Ret*エピローグなしを指定する 3 の値。 フル .xdata 形式では、インデックス 0 に通常どおりプロローグ アンワインド コードを指定して、エピローグ カウントに 0 を指定することでこのことを実現できます。

2 番目の場合は、通常の関数です。 フラグメントにエピローグが 1 つのみ存在する場合で、それがフラグメントの末尾に位置する場合、コンパクト .pdata レコードを使用できます。 その他の場合は、フル .xdata レコードを使用する必要があります。 エピローグ開始用に指定されたオフセットは、フラグメントの開始からの相対値であり、元の関数からの相対値ではない点に留意してください。

3 番目および 4 番目の場合は、プロローグが含まれていない点を除いて、それぞれ 1 番目および 2 番目の場合の変化型です。 これらの状況においては、エピローグの開始前にコードがあることが想定され、そのコードは関数本体の一部と見なされます。通常、これはプロローグの効果を元に戻すことでアンワインドされます。 したがって、これらの場合は、擬似プロローグと共にエンコードする必要があります。擬似プロローグは本体内からアンワィンドする方法を記述しますが、フラグメントの開始で部分アンワインドを実行するかどうかを決定するときに 0 長として扱われます。 この擬似プロローグは、エピローグと同じアンワインド コードを使用して記述することもできます。これは、これらのコードが同等の演算を実行すると想定されるためです。

3 番目と 4 番目の場合、擬似プロローグの存在が指定されてか設定して、*フラグ*2、またはの設定によって、コンパクト .pdata レコードのフィールド、 *F*を 1 に、.xdata ヘッダー内のフラグ。 両方の場合で、部分的なプロローグ アンワインドのチェックが無視され、すべての非エピローグ アンワインドは完全なものであると見なされます。

#### <a name="large-functions"></a>大きな関数

フラグメントを使用して、.xdata ヘッダーのビット フィールドによって設定される 512 KB 制限を超える関数を記述できます。 非常に大きい関数を記述するには、512 KB より小さいフラグメントに関数を分割します。 各フラグメントは、エピローグが複数の部分に分割されないように調整する必要があります。

関数の最初のフラグメントにのみプロローグが含まれます。その他のすべてのフラグメントは、プロローグが含まれていないとマークされます。 エピローグの数に応じて、各フラグメントに 0 個以上のエピローグが含まれます。 フラグメント内の各エピローグ スコープでは、フラグメントの開始からの相対値で開始オフセットが指定されています。関数の開始からの相対値ではありません。

フラグメントにプロローグとエピローグが含まれていない場合でも、関数の本体内からのアンワインド方法を記述するための固有の .pdata レコード (場合によってはさらに .xdata レコードも) が必要です。

#### <a name="shrink-wrapping"></a>シュリンク ラップ

関数フラグメントの場合より複雑な特殊なケースは*シュリンク*レジスタの保存を必要としない単純なケースを最適化するために、関数の後半に関数の先頭から登録を延期するための手法を保存します。 これは、スタック領域を割り当てるが最小セットのレジスタを保存する外部の領域、および追加のレジスタの保存と復元を行う内部の領域として記述できます。

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatiles
    sub    sp, sp, #0x100    ; A: allocate all stack space up front
    ...                      ; A:
    add    r0, sp, #0xE4     ; A: prepare to do the inner save
    stm    r0, {r5-r11}      ; A: save remaining non-volatiles
    ...                      ; B:
    add    r0, sp, #0xE4     ; B: prepare to do the inner restore
    ldm    r0, {r5-r11}      ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C:
```

シュリンク ラップされた関数は、一般的には通常のプロローグ内に追加のレジスタ保存用領域を事前に割り当てて、次に `str` ではなく `stm` または `push` を使用してレジスタ保存を実行することが想定されています。 これにより、すべてのスタック ポインター操作が関数の元のプロローグ内で維持されます。

シュリンク ラップされた関数は、3 つの領域に分割されている必要があります。これらは、コメントで A、B、および C としてマークされています。 初めの A 領域は、関数の開始から追加の非 volatile 保存の終了までをカバーします。 .pdata レコードまたは .xdata レコードを構築し、プロローグは含め、エピローグは含めずに、このフラグメントを記述する必要があります。

中央の B 領域では、プロローグおよびエピローグのないフラグメントを記述する固有の .pdata レコードまたは .xdata レコードを取得します。 ただし、この領域は関数本体と見なされるため、アンワインド コードが存在する必要があります。 コードは、領域 A プロローグ内に保存された元のレジスタと領域 B に入る前に保存された追加のレジスタの両方を表す複合プロローグを、これらが 1 つのシーケンスの操作で生成されたように記述する必要があります。

領域 B のレジスタ保存は、"内部のプロローグ" と見なすことはできません。これは、領域 B 用に記述されたこの複合プロローグは、領域 A プロローグと保存された追加のレジスタの両方を記述する必要があるためです。 フラグメント B がプロローグを含めて記述された場合、アンワインド コードはそのプロローグのサイズも暗黙的に指定します。また、追加レジスタのみを保存するオペコードに 1 対 1 でマップする方法で複合プロローグを記述する方法はありません。

追加のレジスタ保存は、領域 A の一部と見なされる必要があります。これは、これらが完了するまで、複合プロローグはスタックの状態を正確に示さないためです。

最後の C 領域では、プロローグがなくエピローグがあるフラグメントを記述する固有の .pdata レコードまたは .xdata レコードを取得します。

領域 B に入る前に行われるスタック操作を 1 つの命令に削減できる場合、別のアプローチも機能できます。

```asm
ShrinkWrappedFunction
    push   {r4, lr}          ; A: save minimal non-volatile registers
    sub    sp, sp, #0xE0     ; A: allocate minimal stack space up front
    ...                      ; A:
    push   {r4-r9}           ; A: save remaining non-volatiles
    ...                      ; B:
    pop    {r4-r9}           ; B: restore remaining non-volatiles
    ...                      ; C:
    pop    {r4, pc}          ; C: restore non-volatile registers
```

ここで重要なことは、各命令の境界で、スタックは該当領域のアンワインド コードと完全に整合しているということです。 この例の内部のプッシュの前でアンワインドが発生した場合、これは領域 A の一部と見なされ、領域 A のプロローグのみがアンワインドされます。 内部のプッシュの後にアンワインドが発生した場合、内部のポップを保持する領域 B では、プロローグがありませんが、内部のプッシュと領域 A. 同様のロジックから元のプロローグの両方を記述したアンワインド コードの一部と見なされます。

### <a name="encoding-optimizations"></a>エンコーディングの最適化

アンワインド コードの多様性、およびコンパクト形式および拡張形式のデータを利用する能力により、エンコーディングを最適化して領域を削減する多くの機会が存在します。 これらの手法を積極的に使用することで、アンワインド コードの使用による関数およびフラグメントの記述の最終的なオーバーヘッドを最小化できます。

アンワインド目的のプロローグおよびエピローグの境界を、コンパイラの観点からのプロローグおよびエピローグの境界と混同しないように注意することが、最適化において最も重要です。 アンワインド境界は、縮小して緊密にし、効率を改善できます。 たとえば、プロローグにはスタックのセットアップ後に追加の検証チェックを実行するためのコードを含めることができます。 ただし、すべてのスタック操作が完了した後は、以降の演算をエンコードする必要はなく、以降のすべてのものをプロローグのアンワインドから除去できます。

同じルールが関数長にも適用されます。 データ (リテラル プールなど) が関数内のエピローグの後に存在する場合、関数長の一部として含めることは適切ではありません。 関数を短縮し、その関数の部分であるコードのみにすることにより、エピローグが末尾に置かれ、かつコンパクトになる可能性がかなり高くなります。 pdata レコードを使用することができます。

プロローグでは、スタック ポインターが別のレジスタに保存されると、一般的には以降のオペコードを記録する必要がなくなります。 関数をアンワインドするためには、保存されたレジスタからの SP の復元が最初に行われるため、以降の演算はアンワインドに影響しません。

単一命令エピローグは、スコープとしても、アンワインド コードとしても、エンコードする必要がありません。 命令の実行前にアンワインドが発生すると、アンワインドは関数本体からのものと想定でき、プロローグのアンワインド コードの実行のみで十分となります。 単一命令の実行後にアンワインドが発生した場合、本質的にそのアンワインドは別の領域で発生します。

複数命令エピローグは、エピローグの最初の命令をエンコードする必要がありません。これは、アンワインドが命令の実行前に実行された場合はプロローグ全体のアンワインドで十分であるという前述のポイントと同じ理由からです。 最初の命令以降にアンワインドが行われた場合は、後続の演算のみを考慮する必要があります。

アンワインド コードの再使用は積極的に行うべきです。 各エピローグ スコープにより指定されたインデックスは、アンワインド コードの配列内の任意の開始点をポイントします。 これは、前のシーケンスの開始をポイントする必要はありません。中間をポイントできます。 ここでの最良のアプローチは、必要なコードシーケンスを生成した後、既にエンコードされたシーケンスのプール内で一致する正確なバイトをスキャンして、完全に一致したすべてのものを再使用する開始点として使用することです。

単一命令エピローグが無視された後、残りのエピローグがない場合は、コンパクト .pdata 形式の使用を検討します。エピローグが 1 つも存在しない場合は、使用できる可能性がより高くなります。

## <a name="examples"></a>例

これらの例では、イメージ ベースは 0x00400000 です。

### <a name="example-1-leaf-function-no-locals"></a>例 1: リーフ関数、ローカルなし

```asm
Prologue:
  004535F8: B430      push        {r4-r5}
Epilogue:
  00453656: BC30      pop         {r4-r5}
  00453658: 4770      bx          lr
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x000535F8 (= 0x004535F8 0x00400000) を =

- Word 1

   - *フラグ*= 1、標準のプロローグおよびエピローグの形式を示す

   - *関数の長さ*= 0x31 (数 0x62/2 =)

   - *Ret* = 1、16 ビット分岐戻りをことを示します。

   - *H* = 0 の場合、パラメーターを示すが保存されなかったこと

   - *R*= 0 と*Reg* = 1、r4 r5 のプッシュ/ポップを示す

   - *L* = 0、LR の保存/復元がないことを示します。

   - *C* = 0、フレーム チェーンを示すなし

   - *スタック調整*= 0、スタック調整がないことを示します。

### <a name="example-2-nested-function-with-local-allocation"></a>例 2: ネストされた関数、ローカル割り当てあり

```asm
Prologue:
  004533AC: B5F0      push        {r4-r7, lr}
  004533AE: B083      sub         sp, sp, #0xC
Epilogue:
  00453412: B003      add         sp, sp, #0xC
  00453414: BDF0      pop         {r4-r7, pc}
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* = 0x000533AC (0x004533AC =-0x00400000)

- Word 1

   - *フラグ*= 1、標準のプロローグおよびエピローグの形式を示す

   - *関数の長さ*0x35 (0x6A/2 =)

   - *Ret* = 0、pop {pc} 戻り値

   - *H* = 0 の場合、パラメーターを示すが保存されなかったこと

   - *R*= 0 と*Reg* = 3、r4 r7 のプッシュ/ポップを示す

   - *L* = 1、LR を示す保存/復元されました

   - *C* = 0、フレーム チェーンを示すなし

   - *スタック調整*= 3 (0x0C/4 =)

### <a name="example-3-nested-variadic-function"></a>例 3: ネストされた可変個引数関数

```asm
Prologue:
  00453988: B40F      push        {r0-r3}
  0045398A: B570      push        {r4-r6, lr}
Epilogue:
  004539D4: E8BD 4070 pop         {r4-r6}
  004539D8: F85D FB14 ldr         pc, [sp], #0x14
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x00053988 (= 0x00453988 0x00400000) を =

- Word 1

   - *フラグ*= 1、標準のプロローグおよびエピローグの形式を示す

   - *関数の長さ*= 0x2A (0x54/2 =)

   - *Ret* = 0、pop {pc}-{pc} スタイル (この場合 ldr pc, [sp], #0x14 を返します)

   - *H* = 1、保存されたこと、パラメーターを示す

   - *R*= 0 と*Reg* = 2、r4 r6 のプッシュ/ポップを示す

   - *L* = 1、LR を示す保存/復元されました

   - *C* = 0、フレーム チェーンを示すなし

   - *スタック調整*= 0、スタック調整がないことを示します。

### <a name="example-4-function-with-multiple-epilogues"></a>例 4: 複数のエピローグを持つ関数

```asm
Prologue:
  004592F4: E92D 47F0 stmdb       sp!, {r4-r10, lr}
  004592F8: B086      sub         sp, sp, #0x18
Epilogues:
  00459316: B006      add         sp, sp, #0x18
  00459318: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  0045943E: B006      add         sp, sp, #0x18
  00459440: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  004595D4: B006      add         sp, sp, #0x18
  004595D6: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459606: B006      add         sp, sp, #0x18
  00459608: E8BD 87F0 ldm         sp!, {r4-r10, pc}
  ...
  00459636: F028 FF0F bl          KeBugCheckEx     ; end of function
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x000592F4 (= 0x004592F4 0x00400000) を =

- Word 1

   - *フラグ*= 0、.xdata レコードが存在する (複数のエピローグのために必要) を示す

   - *.xdata アドレス*-0x00400000

.xdata (可変、6 ワード):

- Word 0

   - *関数の長さ*0x0001A3 (0x000346/2 =) を =

   - *バージョン*= 0、xdata の最初のバージョン

   - *X* = 0、例外データがないことを示します。

   - *E* = 0、エピローグ スコープのリストを示します。

   - *F* = 0、プロローグを含む、完全な関数の説明

   - *エピローグ カウント*= 0x04、4 つの合計のエピローグを示す

   - *コード ワード*= 0x01、アンワインド コードの 1 つの 32 ビット ワードを示す

- ワード 1～4、4 か所の 4 つのエピローグを記述します。 各スコープには、アンワインド コードの共通セットがあり、オフセット 0x00 でプロローグと共有されています。条件 0x0E (常時) が指定されており、これは条件を伴いません。

- ワード 5 で始まるアンワインド コード: (プロローグとエピローグ共通)

   - アンワインド コード 0 = 0x06: sp += (6 << 2)

   - アンワインド コード 1 = 0xDE: pop {r4-r10, lr}

   - アンワインド コード 2 = 0xFF: end

### <a name="example-5-function-with-dynamic-stack-and-inner-epilogue"></a>例 5: 動的スタックと内部のエピローグを持つ関数

```asm
Prologue:
  00485A20: B40F      push        {r0-r3}
  00485A22: E92D 41F0 stmdb       sp!, {r4-r8, lr}
  00485A26: 466E      mov         r6, sp
  00485A28: 0934      lsrs        r4, r6, #4
  00485A2A: 0124      lsls        r4, r4, #4
  00485A2C: 46A5      mov         sp, r4
  00485A2E: F2AD 2D90 subw        sp, sp, #0x290
Epilogue:
  00485BAC: 46B5      mov         sp, r6
  00485BAE: E8BD 41F0 ldm         sp!, {r4-r8, lr}
  00485BB2: B004      add         sp, sp, #0x10
  00485BB4: 4770      bx          lr
  ...
  00485E2A: F7FF BE7D b           #0x485B28    ; end of function
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x00085A20 (= 0x00485A20 0x00400000) を =

- Word 1

   - *フラグ*= 0、.xdata レコードが存在する (複数のエピローグのために必要) を示す

   - *.xdata アドレス*-0x00400000

.xdata (可変、3 ワード):

- Word 0

   - *関数の長さ*0x0001A3 (0x000346/2 =) を =

   - *バージョン*= 0、xdata の最初のバージョン

   - *X* = 0、例外データがないことを示します。

   - *E* = 0、エピローグ スコープのリストを示します。

   - *F* = 0、プロローグを含む、完全な関数の説明

   - *エピローグ カウント*= 0x001、エピローグの合計の 1 のスコープを示す

   - *コード ワード*= 0x01、アンワインド コードの 1 つの 32 ビット ワードを示す

- ワード 1: オフセット 0xC6 (= 0x18C/2) のエピローグ スコープ、アンワインド コード インデックスを 0x00 で開始、条件は 0x0E (常時)

- ワード 2 で始まるアンワインド コード: (プロローグとエピローグ共通)

   - アンワインド コード 0 = 0xC6: sp = r6

   - アンワインド コード 1 = 0xDC: pop {r4-r8, lr}

   - アンワインド コード 2 = 0x04: sp += (4 << 2)

   - アンワインド コード 3 = 0xFD: end、エピローグの 16 ビット 命令としてカウント。

### <a name="example-6-function-with-exception-handler"></a>例 6: 例外ハンドラーを持つ関数

```asm
Prologue:
  00488C1C: 0059 A7ED dc.w  0x0059A7ED
  00488C20: 005A 8ED0 dc.w  0x005A8ED0
FunctionStart:
  00488C24: B590      push        {r4, r7, lr}
  00488C26: B085      sub         sp, sp, #0x14
  00488C28: 466F      mov         r7, sp
Epilogue:
  00488C6C: 46BD      mov         sp, r7
  00488C6E: B005      add         sp, sp, #0x14
  00488C70: BD90      pop         {r4, r7, pc}
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x00088C24 (= 0x00488C24 0x00400000) を =

- Word 1

   - *フラグ*= 0、.xdata レコードが存在する (複数のエピローグのために必要) を示す

   - *.xdata アドレス*-0x00400000

.xdata (可変、5 ワード):

- Word 0

   - *関数の長さ*0x000027 (0x00004E/2 =) を =

   - *バージョン*= 0、xdata の最初のバージョン

   - *X* = 1、例外データが存在することを示します

   - *E* = 1 で、単一のエピローグを示します

   - *F* = 0、プロローグを含む、完全な関数の説明

   - *エピローグ カウント*= 0x00、エピローグのアンワインド コードがオフセット 0x00 で開始を示す

   - *コード ワード*= 0x02、アンワインド コードの 2 つの 32 ビット ワードを示す

- ワード 1 で開始するアンワインド コード:

   - アンワインド コード 0 = 0xC7: sp = r7

   - アンワインド コード 1 = 0x05: sp += (5 << 2)

   - アンワインド コード 2 = 0xED/0x90: pop {r4, r7, lr}

   - アンワインド コード 4 = 0xFF: end

- ワード 3 指定の例外ハンドラー = 0x0019A7ED (= 0x0059A7ED - 0x00400000)

- ワード 4 およびそれ以降は、インライン化された例外データです。

### <a name="example-7-funclet"></a>例 7: funclet

```asm
Function:
  00488C72: B500      push        {lr}
  00488C74: B081      sub         sp, sp, #4
  00488C76: 3F20      subs        r7, #0x20
  00488C78: F117 0308 adds        r3, r7, #8
  00488C7C: 1D3A      adds        r2, r7, #4
  00488C7E: 1C39      adds        r1, r7, #0
  00488C80: F7FF FFAC bl          target
  00488C84: B001      add         sp, sp, #4
  00488C86: BD00      pop         {pc}
```

.pdata (固定、2 ワード):

- Word 0

   - *関数の開始 RVA* 0x00088C72 (= 0x00488C72 0x00400000) を =

- Word 1

   - *フラグ*= 1、標準のプロローグおよびエピローグの形式を示す

   - *関数の長さ*= 0x0B (0x16/2 =)

   - *Ret* = 0、pop {pc} 戻り値

   - *H* = 0 の場合、パラメーターを示すが保存されなかったこと

   - *R*= 0 と*Reg* = 7、レジスタがないことを示しますが、保存/復元

   - *L* = 1、LR を示す保存/復元されました

   - *C* = 0、フレーム チェーンを示すなし

   - *スタック調整*= 1, 1 × 4 バイトのスタック調整を示す

## <a name="see-also"></a>関連項目

[ARM ABI 規則の概要](../build/overview-of-arm-abi-conventions.md)<br/>
[Visual C++ の ARM への移行に関する一般的な問題](../build/common-visual-cpp-arm-migration-issues.md)
