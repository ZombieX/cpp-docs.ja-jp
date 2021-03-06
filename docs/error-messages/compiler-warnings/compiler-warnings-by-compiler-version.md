---
title: コンパイラのバージョンによるコンパイラの警告 |Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- devlang-cpp
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- warnings, by compiler version
- cl.exe compiler, setting warning options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4d815ba1036a03042992d2715e49bbd8f74a28
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990387"
---
# <a name="compiler-warnings-by-compiler-version"></a>コンパイラのバージョンによるコンパイラの警告

コンパイラは、使用して指定するバージョンの後に導入された警告を抑制することができます、 [/Wv](../../build/reference/compiler-option-warning-level.md)コンパイラ オプション。 これは、新しいツールセットのバージョンを導入し、新しい警告を一時的に非表示にするときに、ビルド プロセスを管理するために役立ちます。 このオプションは、新しいエラー メッセージを抑制しません。 すべての新しい警告を抑制しないで完全に! 最上位の通常の警告レベルを常にコンパイルすることをお勧めします。 __/W4__、および削除、 __/Wv__をビルドにできるだけ早くオプション。

これらのバージョンのコンパイラでは、新しい警告が導入されています。

| 製品 | コンパイラのバージョン番号 |
|-|-|
| Visual C 2002 | 13.00.9466 |
| Visual C 2003 | 13.10.3077 |
| Visual C++ 2005 | 14.00.50727.762 |
| Visual C++ 2008 | 15.00.21022.08 |
| Visual C++ 2010 | 16.00.40219.01 |
| Visual C 2012 | 17.00.51106.1 |
| Visual C 2013 | 18.00.21005.1 |
| ビジュアルの C++ 2015 RTM | 19.00.23026.0 |
| Visual C 2015 Update 1 | 19.00.23506.0 |
| Visual C 2015 Update 2 | 19.00.23918.0 |
| Visual C 2015 Update 3 | 19.00.24215.1 |
| ビジュアルの C++ 2017 RTM | 19.10.25017.0 |
| Visual C 2017 バージョン 15.3 | 19.11.25506.0 |
| Visual C 2017 バージョン 15.5 | 19.12.25830.0 |
| Visual C 2017 バージョン 15.6 | 19.13.26128.0 |
| Visual C 2017 バージョン 15.7 | 19.14.26428.0 |
| Visual C 2017 バージョン 15.8 | 19.15.26726.0 |

メジャー番号のみ、メジャーおよびマイナー番号、またはメジャー、マイナーを指定し、ためにビルド番号、 __/Wv__オプション。 コンパイラは、指定した数値で始まるバージョンに一致するすべての警告を報告し、指定した数よりも大きいバージョンのすべての警告を抑制します。 たとえば、 __/Wv:17__中または任意のバージョンの Visual Studio 2012 では前に、導入されたすべての警告を報告し、Visual Studio 2013 (バージョン 18) から、またはそれ以降の任意のコンパイラで導入されたすべての警告を抑制します。 Visual Studio 2015 で導入された警告の update 2 を抑制して、使用することができます __/Wv:19.00.23506__します。 使用 __/Wv:19.11__を報告するすべての警告は、Visual Studio 2017 バージョン 15.5 では、前に Visual Studio の任意のバージョンで導入されましたが、Visual Studio 2017 バージョン 15.5 以降で導入された警告を抑制します。

次のセクションでは、Visual C を使用して抑制することができますの各バージョンで導入された警告を一覧表示、 __/Wv__コンパイラ オプション。 __/Wv__オプションは、以前指定したバージョンのコンパイラが一覧にない警告を抑制することはできません。

## <a name="warnings-introduced-in-visual-c-2017-version-158-compiler-version-1915267260"></a>Visual C 2017 15.8 (コンパイラ バージョン 19.15.26726.0) のバージョンで導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.14__します。

|||
|-|-|
C5046|'*関数*': シンボルが定義されていない内部リンケージを持つ型に関連します。|

## <a name="warnings-introduced-in-visual-c-2017-version-157-compiler-version-1914264280"></a>Visual C 2017 バージョン 15.7 (コンパイラ バージョン 19.14.26428.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.13__します。

|||
|-|-|
C4642|'*問題*': ジェネリック パラメーターの制約をインポートできませんでした'*パラメーター*'
C5045|/Qspectre スイッチする場合は、指定されたメモリの負荷にコンパイラが Spectre の軽減策を挿入します。

## <a name="warnings-introduced-in-visual-c-2017-version-156-compiler-version-1913261280"></a>Visual C 2017 バージョン 15.6 (コンパイラ バージョン 19.13.26128.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.12__します。

|||
|-|-|
C5044|コマンド ライン オプションに引数*オプション*パスを指す '*パス*' が存在しません。

## <a name="warnings-introduced-in-visual-c-2017-version-155-compiler-version-1912258300"></a>Visual C 2017 バージョン 15.5 (コンパイラ バージョン 19.12.25830.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.11__します。

|||
|-|-|
C4843|'*type1*': 配列または関数の型への参照の例外ハンドラーにアクセスできない、使用して'*type2*' 代わりに
C4844|' モジュールがエクスポート*module_name*;' がモジュール インターフェイスを宣言するための構文として推奨
C5039|'*関数*':-ehc の extern C 関数に渡されたポインターまたは参照関数をスローする可能性があることにします。 未定義の動作は、この関数が例外をスローした場合に発生する可能性があります。
C5040|動的例外指定は有効な c++ 14 でのみ、およびそれ以前noexcept (false) として扱う
C5041|'*定義*': constexpr 静的データ メンバーのアウトオブ ライン定義は不要で、c++ 17 では非推奨
C5042|'*宣言*': 関数宣言のブロック スコープでは、標準 C++ で指定された 'inline' をすることはできません 'inline' 指定子を削除。
C5043|'*仕様*': 例外の指定が以前の宣言と一致しません

## <a name="warnings-introduced-in-visual-c-2017-version-153-compiler-version-1911255060"></a>Visual C 2017 バージョン 15.3 (コンパイラ バージョン 19.11.25506.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.10__します。

|||
|-|-|
C4597|未定義の動作:*の説明*
C4604|'*型*': ネイティブとマネージの境界を越えて引数を値渡しには、有効なコピー コンス トラクターが必要です。 それ以外の場合、実行時の動作は定義されていません
C4749|条件付きでサポートされています:*の説明*
C4768|リンケージ指定の前に _ _declspec 属性は無視されます。
C4834|'nodiscard' 属性を持つ関数の戻り値を破棄します。
C4841|非標準の拡張機能が使用:*拡張機能*
C4842|'offsetof' の複数の継承を使用して、型に適用の結果は、コンパイラ リリース間において一貫性は保証されません。
C4869|'nodiscard' は、クラス、列挙型、および非 void 戻り値の型を持つ関数にのみ適用できます。
C5033|'*ストレージ クラス*' はサポートされているストレージ クラスでは不要になった
C5034|組み込みの使用 '*組み込み*' 関数をにより*関数*ゲスト コードとしてコンパイルするには
C5035|機能を使用して、'*機能*' 関数をにより*関数*ゲスト コードとしてコンパイルするには
C5036|/hybrid:x86arm64 でコンパイルするときに、varargs 関数ポインター変換 '*type1*'to'*type2*'
C5037|'*メンバー関数*': クラス テンプレートのメンバーのアウトオブ ライン定義を既定の引数を持つことはできません
C5038|データ メンバー '*member1*'後にデータ メンバー初期化が'*member2*'

## <a name="warnings-introduced-in-visual-c-2017-rtm-compiler-version-1910250170"></a>Visual C 2017 RTM (コンパイラ バージョン 19.10.25017.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.00__します。

|||
|-|-|
C4468|'fallthrough': 属性の後に、case ラベルまたは default ラベルで必要
C4698|'*機能*' は評価目的でのみ変更される可能性が更新または削除で将来のです。
C4839|クラスの標準でない使用*クラス*' 可変個引数関数に引数として
C4840|クラスの移植性のない使用*クラス*' 可変個引数関数に引数として

## <a name="warnings-introduced-in-visual-c-2015-update-3-compiler-version-1900242151"></a>Visual C 2015 Update 3 (コンパイラ バージョン 19.00.24215.1) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.00.23918__します。

|||
|-|-|
C4467|ATL 属性の使用は非推奨します。
C4596|'*名前*': メンバー宣言での無効な修飾名
C4598|' #include \<*ヘッダー*\>': ヘッダー番号*数*で、*ソース*と一致しません*ソース*です位置
C4599|'*引数*':*ソース*引数番号*数*と一致しません*ソース*

## <a name="warnings-introduced-in-visual-c-2015-update-2-compiler-version-1900239180"></a>Visual C 2015 Update 2 (コンパイラ バージョン 19.00.23918.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.00.23506__します。

|||
|-|-|
C4466|コルーチン ヒープの省略は実行できませんでした。
C4595|'*クラス*': 非メンバー operator new または delete 関数がインラインで宣言できません。
C4828|ファイルには、オフセット 0 から始まる文字が含まれています。 x*値*、現在のソース文字セットでは無効です (コードページ*数*)。
C4868|コンパイラは、中かっこで囲んだ初期化子リストで左から右の評価順序を強制しない可能性があります。

## <a name="warnings-introduced-in-visual-c-2015-update-1-compiler-version-1900235060"></a>Visual C 2015 Update 1 (コンパイラ バージョン 19.00.23506.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:19.00.23026__します。

|||
|-|-|
C4426|#pragma optimize() が原因で最適化フラグがヘッダーを含めた後に変更があります。
C4654|プリコンパイル済みヘッダーの前に配置されたコードは、行が無視されます。 コードをプリコンパイル済みヘッダーに追加します。
C5031|#pragma warning(pop): likely mismatch, popping warning state pushed in different file
C5032|#pragma warning (push) ない対応の #pragma warning (pop) が検出されました

## <a name="warnings-introduced-in-visual-c-2015-rtm-compiler-version-1900230260"></a>Visual C 2015 RTM (コンパイラ バージョン 19.00.23026.0) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:18__します。

|||
|-|-|
C4427|'*エラー*': 定数除算、未定義の動作でオーバーフロー
C4438|'*型*':/await で安全に呼び出すことはできません:/await:clrcompat モード。 場合 '*型*' CLR ヘッドが破損の可能性がある CLR への呼び出し
C4455|' operator*名前*': アンダー スコアで始まらないリテラル サフィックス識別子は予約されています
C4456|宣言 '*名前*' 前のローカル宣言を隠します
C4457|宣言 '*名前*' 関数のパラメーターを非表示にします
C4458|宣言 '*名前*' クラスのメンバーを非表示にします
C4459|宣言 '*名前*' グローバル宣言を隠します
C4462|'*型*': 型の GUID を特定できません。 プログラムは、実行時に失敗する可能性があります。
C4463|オーバーフローです。割り当てる*値*のみからの値を保持できるビット フィールドに*値*に*値*
C4473|'*関数*': 書式指定文字列の引数が不足しています
C4474|'*関数*': 書式指定文字列に渡された引数が多すぎます
C4475|'*関数*': 長さ修飾子'*修飾子*'の型フィールド文字を使用することはできません'*文字*' で書式指定子
C4476|'*関数*': 不明な型フィールド文字'*文字*' で書式指定子
C4477|'*関数*': 書式文字列'*文字列*'型の引数が必要です'*型*'、可変個引数が、*数*型が '*型*'
C4478|'*関数*': 位置指定と位置指定以外のプレース ホルダーは、同じ書式指定文字列に混在させることはできません
C4494|'*型*': ポインターまたは参照できませんが、関数型を返すため、__declspec(allocator) は無視されます
C4495|標準の拡張機能を使用して '_ _super': 明示的な基本クラス名で置き換えます
C4496|'for each' 標準の拡張機能の使用: ranged-for ステートメントに置き換えます
C4497|'シールド' を使用する標準の拡張機能: 'final' で置き換えます
C4498|標準の拡張機能を使用します '*拡張子*'。
C4499|'*特殊化*': 明示的な特殊化 (無視) ストレージ クラスを含めることはできません
C4576|初期化子リストの後にかっこで囲まれた型は非標準の明示的な型変換の構文
C4577|' noexcept' の処理モードが指定されていない例外の併用例外で終了処理は保証されません。 /EHsc を指定します。
C4578|'abs': からの変換 '*型*'to'*型*'、データ損失の可能性 (呼び出すもしかして'*名前*' または #include \<cmath >?)
C4582|'*型*': コンス トラクターが暗黙的に呼び出されません
C4583|'*型*': デストラクターは暗黙的に呼び出されません
C4587|'*型*': 動作変更: コンス トラクターが不要になった暗黙的に呼び出されます
C4588|'*型*': 動作変更: デストラクターは呼び出されなく
C4589|抽象クラスのコンス トラクター*型*'仮想基底クラスの初期化子は無視されます'*型*'
C4591|'constexpr' 呼び出し深さ制限*数*を超えています (//constexpr:depth\<番号 >)
C4592|'*型*': シンボルは動的になります (実装の制限) の初期化
C4593|'*型*': 'constexpr' 呼び出し評価ステップ制限の*値*を超えました/constexpr:steps を使用して\<番号 > の制限を上げます。
C4647|動作変更: _ _is_pod (*型*) 別の値が、以前のバージョン
C4648|標準属性 'carries_dependency' は無視されます。
C4649|このコンテキストで属性は無視されます。
C4753|ポインターの境界を見つけることができません。MPX 組み込み関数は無視されます。
C4771|単純なポインターでは; を使用して境界を作成する必要があります。MPX 組み込み関数は無視されます。
C4774|'*説明*': 書式指定文字列の引数で想定される*数*リテラル文字列はありません
C4775|書式指定文字列で使用される標準の拡張機能 '*文字列*'function' の*関数*'
C4776|' %*文字*'は関数の書式指定文字列で許可されていません'*関数*'
C4777|'*説明*': 書式文字列'*文字列*'型の引数が必要です'*型*'、可変個引数が、*数*型が '*型*'
C4778|'*説明*': 書式指定文字列の終端されていない'*文字列*'
C4838|変換 '*型*'to'*型*' 縮小変換が必要です
C5022|'*型*': 指定された複数の移動コンス トラクター
C5023|'*型*': 指定された複数の移動代入演算子
C5024|'*宣言*': 移動コンス トラクターが暗黙的に削除済みとして定義
C5025|'*宣言*': 移動代入演算子が暗黙的に削除済みとして定義
C5026|'*型*': 移動コンス トラクターが暗黙的に削除済みとして定義
C5027|'*型*': 移動代入演算子が暗黙的に削除済みとして定義
C5028|'*名前*': アラインメントは前の宣言で指定された (*数*) 定義で指定されていません
C5029|標準の拡張機能を使用します C++ のアラインメント属性は、変数、データ メンバーおよびタグの種類のみに適用。
C5030|属性 '*属性*' は認識されません

## <a name="warnings-introduced-in-visual-c-2013-compiler-version-1800210051"></a>Visual C 2013 (コンパイラ バージョン 18.00.21005.1) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:17__します。

|||
|-|-|
C4301|'*型*': 仮想関数をオーバーライドするとだけ'*宣言*' const または volatile 修飾子
C4316|'*型*': ヒープで割り当てられたオブジェクトがアラインされていない*数*
C4380|'*型*': 既定のコンス トラクターは非推奨にできません
C4388|'*トークン*' signed/unsigned が一致しません。
C4423|'std::bad_alloc': クラスによってキャッチされます ('*型*') の行に*数*
C4424|catch の '*型*'続く'*型*' の行に*数*; 予期しない 'std::bad_alloc' がスローされた場合の動作があります
C4425|SAL 注釈を '...' に適用できません。
C4464|相対インクルード パスを含む '… '
C4575|'_ _vectorcall' と互換性のない、'/clr' オプション: '_ _stdcall' に変換します。
C4609|'*型*'既定のインターフェイスから派生した'*型*'type' で*型*'。 別の既定のインターフェイスを使用して '*型*'、または基本/派生リレーションシップを中断します。
C4754|における比較時の算術演算の変換規則*説明*(*数*) という意味ではその 1 つの分岐を実行することはできません。 Cast '*型*'to'*型*' (または類似する型の*数*バイト)。
C4755|における比較時の算術演算の変換規則*説明*(*数*) という意味では、インライン関数でその 1 つの分岐は実行できません。 Cast '*型*'to'*型*' (または類似する型の*数*バイト)。
C4767|セクション名 '*名前*' が 8 文字より長いと、リンカーによって切り詰められます
C4770|部分的に検証された列挙型 '*名前*' インデックスとして使用
C4827|パブリックの 'ToString' メソッド パラメーターの 0 を virtual としてマークする必要があり、上書き
C4882|非 const 呼び出し演算子のファンクターを concurrency::parallel_for_each に渡すことは推奨されていません
C4973|'*型*': 非推奨としてマーク
C4974|'*型*': 非推奨としてマーク
C4981|Warbird: 関数 '*宣言*' マーク _ _forceinline としてインライン化された例外のセマンティクスが含まれています
C4990|Warbird:*メッセージ*
C4991|Warbird: 関数 '*宣言*' マーク _ _forceinline としてインライン インライン展開先の保護レベルが親よりも大きいため、
C4992|Warbird: 関数 '*宣言*' マーク _ _forceinline としてインライン保護できないインライン アセンブリが含まれています

## <a name="warnings-introduced-in-visual-c-2012-compiler-version-1700511061"></a>Visual C 2012 (コンパイラ バージョン 17.00.51106.1 である) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:16__します。

|||
|-|-|
C4330|属性 '*属性*'section' for*セクション*' は無視されます
C4415|duplicate __declspec(code_seg('*name*'))
C4416|__declspec(code_seg(...) に空の文字列が含まれています無視されます。
C4417|明示的なテンプレート インスタンス化は __declspec(code_seg(...) を含めることはできません無視されます。
C4418|__declspec(code_seg(...) 列挙型では無視されます。
C4419|'*名前*'プライベート ref クラスに適用する場合の影響を与えません'*型*'。
C4435|'*型*':/vd2 下のオブジェクトのレイアウトは仮想ベースにより変更されます'*型*'
C4436|仮想基本から dynamic_cast '*型*'to'*型*' コンス トラクターまたはデストラクターで部分的に構築されたオブジェクトが失敗します。
C4437|仮想基本から dynamic_cast '*型*'to'*型*' 一部のコンテキストで失敗する可能性があります
C4443|プラグマ パラメーターに '0'、'1' または '2' を指定
C4446|'*型*': メンバーをマップすることはできません'*名前*' に、この型を型名の競合が原因です。 変更されましたが、メソッド '*名前*'
C4447|'main' シグネチャがないスレッド モデルが見つかりません。 使用を検討して ' int main (platform::array\<platform::string ^ > ^ args)' です。
C4448|'*型*' メタデータで指定された既定のインターフェイスはありません。 ピッキング: '*型*'、実行時に失敗する可能性があります。
C4449|'*型*' アンシールド型は '[WebHostHidden]' とマークする必要があります
C4450|'*型*'としてマーク '[WebHostHidden]' から派生するため、'*型*'
C4451|'*型*': ref クラスの使用状況*型*' 内でこのコンテキストがコンテキスト間でオブジェクトの無効なマーシャ リングにつながることができます
C4452|'*型*': パブリック型がグローバル スコープですることはできません。 これは、出力の .winmd ファイルの名前の子である名前空間に存在する必要があります。
C4453|'*型*': '[WebHostHidden]' 型は、パブリック型でない発行サーフェスで使用されませんする必要があります '[WebHostHidden]'
C4454|'*型*' は、[defaultoverload] を指定することがなく入力パラメーター数よりも多いでオーバー ロードします。 ピッキング '*宣言*' として既定のオーバー ロード
C4471|'*名前*': スコープを持たない列挙型の事前宣言は、基になる型 (int が想定されます) をいる必要があります
C4472|'*名前*' ネイティブ列挙型は、: マネージまたは WinRT 列挙型を宣言するアクセス指定子 (秘密/公開) の追加
C4492|'*型*': 一致する基本 ref クラス メソッド'*型*'、'override' がマークされていないが、
C4493|削除式のデストラクターとして効果はありません '*型*' が 'public' アクセシビリティ
C4585|'*型*': A WinRT 'public ref class' 封印する必要がありますか、または既存の派生には、クラスが封印されていません。
C4586|'*型*': 'Windows' と呼ばれる最上位レベルの名前空間では、パブリック型を宣言できません
C4695|#pragma execution_character_set: '*引数*' はサポートされている引数ではありません現在は 'utf-8' がサポートされています
C4703|初期化されていない可能性があるローカル ポインター変数 '*名前*' を使用
C4728|/Yl-オプションは PCH 参照が必要なため、無視されます。
C4745|揮発性アクセス '*名前*' そのサイズにより有効にすることはできません
C4746|揮発性アクセス '*名前*' は/volatile:\<iso\|ms > 設定; _iso_volatile_load/store 組み込み関数を使用を検討してください
C4872|concurrency::parallel_for_each の呼び出し先をコンパイルするときに 0 による浮動小数点除算: '*説明*'
C4880|型にキャスト '*型*'to'*型*': 未定義の動作は amp 制限関数にキャストして const 性からポインターまたは参照があります
C4881|コンス トラクターおよびデストラクターは呼び出されません tile_static 変数 '*型*'
C4966|'*説明*' が _code_seg 注釈でサポートされていないセグメント名、注釈は無視されます
C4988|'*型*': 変数には、外側のクラス/関数スコープが宣言されています
C4989|'*説明*': 型が競合する定義。

## <a name="warnings-introduced-in-visual-c-2010-compiler-version-16004021901"></a>Visual C 2010 (コンパイラ バージョン 16.00.40219.01) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:15__します。

|||
|-|-|
C4352|'*名前*': 既に定義されている組み込み関数
C4573|使用量 '*型*' が 'this' をキャプチャするコンパイラが必要です、現在の既定のキャプチャ モードが許可していません。
C4574|'*名前*'は' 0': 候補を使用して、' #if*名前*' でしょうか。
C4689|'*文字*': #pragma detect_mismatch にサポートされていない文字; #pragma は無視されました
C4751|/arch AVX フラグは、intel (r) ストリーミング SIMD 拡張命令はインライン ASM 内にあるには適用されません。
C4752|intel (r) Advanced Vector Extensions; が見つかりません適切な/arch AVX フラグの使用を検討します。
C4837|検出されたトライグラフ: '??*文字*'置き換え'*文字*'
C4986|'*宣言*': 例外の指定が以前の宣言と一致しません
C4987|非標準の拡張機能が使用されています: 'throw (...)' です。

## <a name="warnings-introduced-in-visual-c-2008-compiler-version-15002102208"></a>Visual C 2008 (コンパイラ バージョン 15.00.21022.08) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:14__します。

|||
|-|-|
C4396|'*型*': フレンド宣言が関数テンプレートの特殊化を参照するときに、インライン指定子を使用できません
C4413|'*宣言*': 参照メンバーがコンス トラクターの終了後は維持されませんを一時的に初期化されます
C4491|'*説明*': 無効な IDL バージョン形式があります
C4603|'*名前*': マクロが定義されていないか、プリコンパイル済みヘッダーを使用している定義とは異なります
C4627|'*説明*': プリコンパイル済みヘッダーの使用を検索するときにスキップ
C4750|'*説明*': _alloca() ループにインライン関数
C4910|'*型*': '関数' と 'extern' 明示的なインスタンス化の互換性がありません
C4985|'*宣言*': 前の宣言に属性が存在しません。

## <a name="warnings-introduced-in-visual-c-2005-compiler-version-140050727762"></a>Visual C 2005 (コンパイラ バージョン 14.00.50727.762) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:13__します。

|||
|-|-|
C4000|不明な警告ください Visual C ヘルプ メニューに、サポート情報コマンドを選択するかの詳細については、サポート情報ヘルプ ファイルを開く
C4272|'*型*': _declspec がマークされている; 関数をインポートするときに、ネイティブの呼び出し規約を指定する必要があります。
C4333|'*式*': 右シフトによってデータが失われる回数が多すぎます
C4334|'*式*': 32 ビット シフトの結果が暗黙的に変換する 64 ビット (64 ビット シフトのためのものでしたか?)
C4335|Mac ファイル形式が検出されました: ソース ファイルを DOS または UNIX のいずれかの形式に変換してください
C4342|動作変更: '*型*' 呼び出されると、メンバー演算子が以前のバージョンで呼び出されましたが、
C4350|動作変更: '*宣言*'の代わりに呼び出す'*宣言*'
C4357|デリゲートに対する仮引数リストで param 配列引数が見つかった '*宣言*'を生成するときに無視されます'*型*'
C4358|'*式*': 複合デリゲートの戻り値の型は 'void' ではありません戻り値が定義されていません。
C4359|'*型*': アラインメント指定子が実際のアラインメントより小さい (*数*)、無視されます。
C4362|'*型*': 8 バイトより大きいアラインメントは CLR でサポートされていません
C4364|# アセンブリ using '*名前*' で以前に確認された*説明*(*数*) as_friend 属性なし as_friend は適用されません
C4365|'*式*': から変換'*型*'to'*型*'、signed/unsigned が一致しません
C4366|単項の結果 '*演算子*' 演算子を配置できない可能性があります
C4367|変換 '*型*'to'*型*' データ型の不整合例外が発生する可能性があります
C4368|定義できません '*名前*'のメンバーが管理対象' として*型*': 型が混在はサポートされていません。
C4369|'*型*': 列挙子の値'*数*'として表すことができない'*型*'、値は'*数*'
C4374|'*宣言*': インターフェイス メソッドは、非仮想メソッドでは実装されません'*宣言*'
C4375|非パブリック メソッド '*宣言*'オーバーライドしない'*宣言*'
C4376|アクセス指定子 '*指定子*:' はサポートされなく: を使用してください'*指定子*:' 代わりに
C4377|ネイティブ型は既定ではプライベート-d1PrivateNativeTypes が非推奨とされます
C4378|初期化子を実行する関数ポインターを取得する必要があります。System::ModuleHandle::ResolveMethodHandle を検討してください。
C4379|バージョン*バージョン*共通言語ランタイムでサポートされていないこのコンパイラ。 このバージョンを使用して予期しない結果が発生する可能性があります。
C4381|'*宣言*': インターフェイス メソッドは、非パブリック メソッドでは実装されません'*宣言*'
C4382|スロー '*型*': _ _clrcall デストラクターまたはコピー コンス トラクターを持つ型のみを/clr でキャッチできます純粋なモジュール。
C4383|'*型*': ユーザー定義時に、ハンドルの逆参照の意味を変更できます'*演算子*' 演算子が存在しますオペランドに対して明示的に指定する静的関数として、演算子の書き込み。
C4384|#pragma '*ディレクティブ*' は、グローバル スコープでのみ使用します。
C4393|'*型*': const も何も起こりません*説明*データ メンバーは無視されます
C4394|'*型*': appdomain ごとのシンボルは _ _declspec をマークしない必要があります (*値*)
C4395|'*型*': initonly データ メンバーのコピーで、メンバー関数が呼び出される'*型*'
C4397|DefaultCharSetAttribute は無視されます。
C4398|'*型*': プロセスごとのグローバル オブジェクトは複数の appdomain と共に動作しない可能性があります、__declspec(appdomain) を使用してみてください。
C4399|'*型*': _ _declspec でプロセスごとのシンボルをマークしない必要があります (*値*)/clr でコンパイルした場合: 純粋な
C4400|'*型*': この型での const/volatile 修飾子はサポートされていません
C4412|'*宣言*': 関数のシグネチャには、型が含まれています'*型*';。C++ オブジェクトは、純粋なコードの間で渡すため安全でないと混合またはネイティブです。
C4429|考えられる不完全または形式の正しくないユニバーサル文字名
C4430|型指定子がありません - int と仮定しました。 注: C++ は int を既定値をサポートしていません
C4431|型指定子がありません - int と仮定しました。 メモ: C は、現在 int を既定値としてサポートしていません
C4434|静的コンス トラクターはプライベート アクセシビリティをいる必要があります。プライベート アクセスに変更します。
C4439|'*型*': シグネチャのマネージ型と関数定義は、_ _clrcall 呼び出し規約をいる必要があります
C4441|呼び出し規約 '*規則*' を無視する場合'*規則*' 代わりに使用
C4445|'*宣言*': マネージまたは WinRT 型では、仮想メソッドをプライベートにすることはできません
C4460|CLR または WinRT 演算子 '*型*' では、参照によって渡されるパラメーター。 CLR または WinRT 演算子 '*演算子*'C++ の演算子から別のセマンティクスがあります'*演算子*'、値渡しするつもりでしたか?。
C4461|'*型*': このクラスはファイナライザー '!*型*'が、デストラクター' ~*型*'
C4470|浮動小数点の制御 pragmas は/clr で無視されます。
C4480|使用される標準の拡張機能: 列挙型の基になる型を指定する '*型*'
C4481|使用される標準の拡張機能: オーバーライド指定子 '*指定子*'
C4482|使用される標準の拡張機能: enum '*型*' 修飾名で使用されます。
C4483|構文エラー: C++ のキーワードが必要です
C4484|'*型*': 一致する基本 ref クラス メソッド'*型*'、'virtual'、'new' または 'override'; に設定されていませんが、'new' (および 'virtual') と見なされます
C4485|'*型*': 一致する基本 ref クラス メソッド'*型*' がマークされている 'new' または 'override'; ではありません'new' (および 'virtual') と見なされます
C4486|'*型*': ref クラスまたは値クラスのプライベート仮想メソッドは、'シールド' マークする必要があります
C4487|'*型*': 一致する非仮想メソッドの継承'*型*' が 'new' に明示的に設定されていません
C4488|'*型*': が必要です'*キーワード*'インターフェイス メソッドを実装するためにキーワード'*型*'
C4489|'*キーワード*': インターフェイス メソッドでは使用できません'*名前*'。 オーバーライド指定子は、ref クラスおよび値クラスのメソッドでのみ使用できます。
C4490|'*キーワード*': オーバーライド指定子の不適切な使用'*型*' 基本 ref クラスのメソッドと一致しません
C4538|'*型*': この型での const/volatile 修飾子はサポートされていません
C4559|'*型*': 再定義; 関数が _ _declspec (*値*)
C4565|'*型*': 再定義; シンボルが以前に宣言されたを _ _declspec (*値*)
C4566|ユニバーサル文字名で表される文字 '*文字*' 現在のコード ページで表すことができない (*数*)
C4568|'*型*': 明示的なオーバーライドのシグネチャに一致するメンバーがありません
C4569|'*型*': 明示的なオーバーライドのシグネチャに一致するメンバーがありません
C4570|'*型*': 抽象ですが、抽象関数として明示的に宣言されていません
C4571|情報: catch (...) セマンティクスが Visual C 7.1; から変更構造化例外 (SEH) はキャッチされません。
C4572|[ParamArray] 属性は/clr で非推奨、'…' を使用して、代わりに
C4580|[attribute] は非推奨とされます。代わりに指定*指定*基底クラスとして属性
C4581|非推奨の動作: '"*名前*"' に置き換えられます '*名前*' 属性を処理
C4606|#pragma 警告: '*数*' を無視する場合コード分析の警告が警告レベルに関連付けられていません。
C4631|MSXML または XPath は使用できません。XML ドキュメント コメントは処理されません。 *description*
C4632|XML ドキュメント コメント:*説明*-アクセスが拒否されました:*の説明*
C4633|XML ドキュメント コメント*説明*: エラー:*の説明*
C4634|XML ドキュメント コメント*説明*: 適用できません:*の説明*
C4635|XML ドキュメント コメント*説明*: 正しくない XML の形式:*の説明*
C4636|XML ドキュメント コメント*説明*: タグが空でない必要があります '*説明*' 属性。
C4637|XML ドキュメント コメント*説明*:\<含める > タグは破棄されます。 *description*
C4638|XML ドキュメント コメント*説明*: 不明なシンボルへの参照を '*説明*'。
C4639|MSXML エラーの場合は、XML ドキュメント コメントは処理されません。 *description*
C4641|XML ドキュメント コメントには、あいまいなの相互参照があります。
C4678|基底クラス*宣言*'のアクセシビリティより低く is'*名前*'
C4679|'*説明*': メンバーをインポートできませんでした
C4687|'*型*': シールドされた抽象クラスはインターフェイスを実装できません'*型*'
C4688|'*名前*': 制約リストには、アセンブリ プライベート型が含まれています'*宣言*'。
C4690|\[ emitidl (pop)]: ポップがプッシュ
C4691|'*型*': 参照型で参照されない*モジュール*'*説明*'、代わりに使用される現在の翻訳単位で定義された型
C4692|'*名前*': 公開されたメンバーのシグネチャはアセンブリ プライベート ネイティブ型を含む'*宣言*'
C4693|'*型*': シールドされた抽象クラスのインスタンス メンバーを持つことはできません*名前*'
C4694|'*型*': シールドされた抽象クラスは基底クラス' を含めることはできません*型*'
C4720|インライン アセンブラー レポート: '*説明*'
C4721|'*説明*': 組み込み関数として使用できません。
C4722|'*説明*': デストラクターに値がメモリ リークの可能性
C4726|ARM arch4/4T だけがサポートされます '\<cpsr_f > または\<spsr_f >' では、イミディ エイト値
C4727|という名前の PCH*名前*にある同じタイムスタンプを持つ*名前*と*名前*します。  最初の PCH を使用します。
C4729|フロー グラフ ベースの警告の関数が大きすぎます。
C4730|'*説明*': _m64 と浮動小数点式は、不適切なコード、可能性があります
C4731|'*説明*': フレーム ポインター レジスタ'*登録*' インライン アセンブラー コードによって変更されました。
C4732|組み込み '*組み込み*' は、このアーキテクチャではサポートされていません
C4733|インライン asm は 'FS:0 'に割り当てる: ハンドラーは安全なハンドラーとして登録されていません
C4734|64 k 以上の行番号 coff デバッグ情報のセクションで;モジュールの COFF デバッグ行番号の生成を中止して '*モジュール*'
C4738|メモリに 32 ビットの浮動結果を格納します。パフォーマンスが低下する可能性があります
C4739|変数への参照を '*変数*' のストレージ領域を超えています
C4740|インライン asm コードの内外でのフローは、グローバルな最適化を抑制します。
C4742|'*変数*'異なるアラインメントを has'*場所*'と'*場所*':*数*と*数*
C4743|'*名前*'別のサイズが、'*場所*'と'*場所*':*数*と*数*バイト
C4744|'*名前*'別の型を持つ'*場所*'と'*場所*':'*型*'と'*型*'
C4747|管理対象の呼び出し '*型*': マネージ コードは DLL エントリ ポイントおよび DLL エントリ ポイントから到達した呼び出しを含むローダー ロック下で実行できません
C4761|引数は整数のサイズが一致しません指定した変換
C4764|キャッチ オブジェクトを16 バイトを超えて整列することはできません
C4788|'*識別子*': 識別子は切り詰められました'*数*' 文字
C4789|バッファー '*名前*' のサイズの*数*(バイト) でオーバーランが発生されます。*数*オフセットから始まるバイトが書き込まれます*数*
C4801|参照による戻り値は、検証できません:*の説明*
C4819|ファイルには、現在のコード ページで表現できない文字が含まれています (*数*)。 データ損失を防ぐために Unicode 形式でファイルを保存します。
C4826|変換 '*型*'to'*型*' は符号拡張します。 これにより、予期しない実行時の動作が発生する可能性があります。
C4829|関数 main への正しくないパラメーターである可能性があります。 検討 ' int main (platform::array\<platform::string ^ > ^ argv)'
C4835|'*型*': マネージ コードがホスト アセンブリで最初に実行されるまで、エクスポートされたデータの初期化子は実行されません
C4867|'*型*': 非標準の構文は使用して '&' は、メンバーへのポインターを作成するには
C4936|この __declspec は、/clr または /clr:pure でコンパイルされるときのみサポートされます
C4937|'*名前*'と'*名前*'が引数として区別'*オプション*'
C4938|'*型*': 浮動小数点の減少変数で矛盾する結果が発生する可能性があります厳密なまたは #pragma fenv_access。
C4939|#pragma vtordisp は非推奨とされます。今後の Visual C++ バージョンからは削除されます
C4947|'*型*': 廃止としてマークされています。
C4949|マネージドおよびアンマネージドのプラグマはコンパイルした場合にのみ意味のある '/clr [: オプション]'
C4950|'*型*': 廃止としてマークされています。
C4955|'*説明*': インポートは無視されますから既にインポートされて'*ソース*'。
C4956|'*型*': この型は、検証できません
C4957|'*式*': 明示的なキャストから'*型*'to'*型*' は、検証できません
C4958|'*式*': ポインター演算は検証可能ではありません
C4959|非管理対象を定義できません*クラス*'*型*'/clr:safe で検証できないコードを生成するそのメンバーにアクセスするため、
C4960|'*説明*' が大きすぎるため、プロファイリングします。
C4961|プロファイル データはマージされませんでした '*場所*'、プロファイル ガイド付き最適化の無効になっています
C4962|'*説明*': プロファイル ガイド付き最適化の最適化によってプロファイル データに矛盾が生じたために無効です
C4963|'*説明*': プロファイル データが見つかりません別のコンパイラ オプションは、インストルメント化されたビルドで使用されました。
C4964|最適化オプションが指定されていません。プロファイル情報は収集されません。
C4965|整数 0 の暗黙的なボックスです。nullptr または明示的なキャストを使用して、
C4970|delegate コンス トラクター: からターゲット オブジェクトが無視されます '*宣言*' が静的
C4971|引数の順序:\<ターゲット オブジェクト >、\<ターゲット関数 > デリゲート コンス トラクターが非推奨とを使用して、\<ターゲット関数 >、\<ターゲット オブジェクト >
C4972|アンボックス操作の結果を左辺の値として扱う、または直接変更することは検証可能ではありません

## <a name="warnings-introduced-in-visual-c-2003-compiler-version-13103077"></a>Visual C 2003 (コンパイラ バージョン 13.10.3077) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:13.00.9466__します。

|||
|-|-|
C4343|#pragma optimize (*説明*、オフ)/Og オプションをオーバーライドします
C4344|動作変更: への呼び出しで明示的なテンプレート引数を使用して '*宣言*'
C4346|'*型*': 依存名が型ではありません
C4348|'*宣言*': 既定のパラメーターの再定義: パラメーター*数*
C4356|'*型*': 静的データ メンバーは派生クラスを使って初期化できません
C4408|匿名*構造体*データ メンバーの宣言がありません
C4544|'*宣言*': 既定のテンプレート引数がこのテンプレート宣言では無視されます
C4545|コンマ前の式は、引数リストのない関数として評価します。
C4546|コンマの前の関数呼び出しに引数一覧がありません。
C4547|'*式*': コンマも何も起こりません前の演算子の副作用が予想される演算子。
C4548|コンマ前の式は無効です。有効な式を指定してください。
C4549|'*式*': コンマの前に、の演算子は無効です。 つもりでした'*式*' でしょうか。
C4628|digraphs は -Ze でサポートされていません。 文字のシーケンス '*シーケンス*'の代替トークンとして解釈されない'*トークン*'
C4629|digraph が使用される、文字シーケンス '*シーケンス*'トークンとして解釈'*トークン*' (これが意図しない場合は、2 文字の間にスペースを挿入する)
C4671|'*説明*': コピー コンス トラクターにアクセスできません
C4676|'*説明*': デストラクターにアクセスできません
C4677|'*名前*': 公開されたメンバーのシグネチャはアセンブリ プライベート型を含む'*宣言*'
C4686|'*型*': 動作の変更可能な UDT の戻り値の呼び出し規則
C4812|宣言スタイル: を使用してください '*型*::*名前*' 代わりに
C4813|'*型*': ローカル クラスの friend 関数する必要がありますが宣言されていません
C4821|Unicode エンコードの種類を特定するには、シグネチャ (BOM) を持つファイルを保存してくださいできません。
C4822|'*型*': ローカル クラス メンバー関数には、本文はありません。
C4823|'*型*': を使用して固定ポインターは、アンワインド セマンティクスが有効になっていません。 /EHa を使用してください。
C4913|ユーザー定義のバイナリ演算子 ',' は存在しますが、すべてのオペランドに適用できるオーバーロードは見つかりませんでした。既定のビルドインバイナリ演算子 ',' を使用します。
C4948|型を返す '*宣言*' が対応する setter の最後のパラメーターの型と一致しません
C4951|'*説明*' からプロファイル データが収集された関数のプロファイル データは使用されませんが編集されました
C4952|'*説明*': プログラム データベースにプロファイル データが見つかりません'*説明*'
C4953|インライン展開先 '*説明*' からプロファイル データが収集されたプロファイル データは使用されませんが編集されました
C4954|'*説明*': プロファイルされません (_ _int64 スイッチ式が含まれています)

## <a name="warnings-introduced-in-visual-c-2002-compiler-version-13009466"></a>Visual C 2002 (コンパイラ バージョン 13.00.9466) で導入された警告

コンパイラ オプションを使用してこれらの警告と以降のバージョンですべての警告を抑制 __/Wv:12__します。

|||
|-|-|
C4096|'*型*': インターフェイスは COM インターフェイスではありません IDL には出力されません。
C4097|プラグマ パラメーターに 'restore' または 'off' が必要です。
C4165|'HRESULT' は 'bool'; に変換されます。本当にこれが望ましいこと?
C4183|'*名前*': 'int' を返すメンバー関数としてと見なされます戻り値の型がありません。
C4199|*description*
C4255|'*名前*': 関数プロトタイプがありません: '()' を '(void)' に変換します。
C4256|'*宣言*': 仮想基底クラスのコンス トラクターが '…' には、呼び出しは Visual C の以前のバージョンと互換性がない可能性があります
C4258|'*名前*': 定義から、外側のスコープから定義を使用になっているループは無視されます。
C4263|'*宣言*': メンバー関数はどの基底クラス仮想メンバー関数をオーバーライドしません
C4264|'*宣言*': ベースからの仮想メンバー関数用のオーバーライドはありません'*クラス*'; 関数が非表示
C4265|'*型*': クラスは仮想関数を含んでいますが、デストラクターが仮想ではありませんこのクラスのインスタンスが正しく消滅されない可能性があります。
C4266|'*宣言*': ベースからの仮想メンバー関数用のオーバーライドはありません'*クラス*'; 関数が非表示
C4267|'*式*': 変換するには、'size_t' から'*型*'、データ損失の可能性
C4274|#ident は無視されます。#pragma comment (exestr, 'string') のドキュメントを参照してください。
C4277|インポートされたアイテム '*型*::*名前*' データ メンバーおよび関数メンバーの両方として存在するデータ メンバーが無視されます
C4278|'*名前*': タイプ ライブラリ内の識別子'*説明*' は既にマクロです 'rename' 修飾子。
C4279|'*名前*': タイプ ライブラリ内の識別子'*説明*' はキーワードです 'rename' 修飾子を使用して、。
C4287|'*式*': 符号なし/負の定数が一致しません
C4288|標準の拡張機能を使用します '*名前*': は for ループ スコープの外側のループで宣言したループ コントロール変数が使用されます。 外側のスコープの宣言と競合。
C4289|標準の拡張機能を使用します '*名前*': for ループで宣言したループ コントロール変数が for ループ スコープの外側で使用。
C4293|'*式*': シフト数が負の値または大きすぎて、未定義の動作
C4295|'*型*': 配列が小さすぎる、終端の null 文字を含める
C4296|'*式*': 式は常に*値*
C4297|'*型*': 関数が例外をスローしないはず
C4298|'*名前*': タイプ ライブラリ内の識別子'*説明*'は既にマクロ; の名前に変更' _ _*名前*'
C4299|'*名前*': タイプ ライブラリ内の識別子'*説明*'キーワードの名前に変更は' _ _*名前*'
C4302|'*式*': から切り捨て'*型*'to'*型*'
C4303|*変換*から '*型*'to'*型*' は static_cast、_ _try_cast または dynamic_cast を使用して、非推奨とされます。
C4314|プラグマ パラメーターに '32' または '64' にします。
C4315|'*型*': メンバー 'this' ポインター'*型*' には配置できません*数*コンス トラクターによって期待どおりに
C4318|memset に対する長さとして定数ゼロを渡す
C4319|'*式*': ゼロ拡張'*型*'to'*型*' より大きいサイズの
C4321|インターフェイスの IID を自動的に生成する '*型*'
C4322|クラスの CLSID を自動的に生成する*型*'
C4323|クラスの CLSID を使用して再登録*型*'
C4324|'*型*': アラインメント指定子のため、構造体がパッドされました
C4325|標準のセクションの属性 '*説明*' は無視されます
C4326|型を返す '*名前*'は'*型*' の代わりに '*型*'
C4327|'*式*': LHS の間接アラインメント (*数*) RHS より大きい (*数*)
C4328|'*説明*': 仮パラメーターの間接アラインメント*数*(*数*) が、実引数アラインメントより大きい (*数*)
C4329|アラインメント指定子は列挙型で無視されます。
C4336|クロスレファレンスしたタイプ ライブラリ '*ライブラリ*'' をインポートする前に*説明*'
C4337|クロスレファレンスしたタイプ ライブラリ '*ライブラリ*'in'*説明*' が自動的にインポートされています。
C4338|#pragma*説明*: 標準セクション '*セクション*' 使用
C4339|'*型*': この型を使用して、ランタイム例外が生じる/WinRT CLR meta-data で未定義の型の使用が検出されました
C4353|標準の拡張機能を使用します。 関数式として定数 0。  組み込みの '_ _noop' 関数を使用してください。
C4370|'*宣言*': パッキングの改善のため、コンパイラの以前のバージョンからのクラスのレイアウトが変更されました
C4371|'*宣言*': クラスのレイアウトは、メンバーのパッキングの改善のため、コンパイラの以前のバージョンから変更された可能性があります'*メンバー*'
C4373|'*型*': 仮想関数のオーバーライド*宣言*'、const/volatile 修飾子によってのみと一致しませんパラメーターの場合、以前のバージョンのコンパイラはオーバーライドしませんでした。
C4387|'*説明*': と見なされていました
C4389|'*式*' signed/unsigned が一致しません。
C4391|'*宣言*': 組み込み関数の戻り値の型が正しくない'*型*'
C4392|'*宣言*': 組み込み関数の引数の数が正しくない'*数*' 引数
C4407|メンバー表記に異なるポインターの間でのキャスト、コンパイラは正しくないコードを生成可能性があります。
C4420|'*名前*': 演算子は使用できませんを使用して'*名前*' ランタイム チェックが低下代わりにします。
C4440|呼び出し規約の再から '*説明*'to'*説明*' は無視されます
C4442|_annotation 引数に null 終端文字が埋め込まれます。  値は切り捨てられます。
C4444|'*名前*': このコンテキストで最上位レベルの '_ _unaligned' が実装されていません
C4526|'*型*': 静的メンバー関数は、仮想関数をオーバーライドできません'*宣言*' オーバーライドを無視するには、仮想関数は非表示にします。
C4531|C++ 例外処理は Windows CE では使用できません。 構造化例外処理を使用します。
C4532|'*説明*': の外部にジャンプ*最後に*ブロックでが終了処理中に、動作が定義されていません
C4533|初期化 '*宣言*' の初期化が ' goto*宣言*'
C4534|'*宣言*' の既定のコンス トラクターはできません*クラス*'*型*' により、既定の引数。
C4535|_set_se_translator() の呼び出し元が必要です。
C4536|'*説明*': 型名では、メタ データの上限を超えています'*数*' 文字。
C4537|'*宣言*':'.'UDT 以外の型に適用
C4542|書き込むことはできません、マージされた挿入されたテキスト ファイルの生成をスキップ*型*ファイル: '*filename*':*エラー*
C4543|テキスト属性を挿入 ' ありません\_injected_text'
C4555|式の影響はありません; 式の副作用が必要です。
C4557|効果を含む '_assume' '*効果*'
C4558|オペランドの値 '*数*'が範囲外です'*数* - *数*'
C4561|'_ _fastcall' と互換性のない、'/clr' オプション: '_ _stdcall' に変換します。
C4562|完全なプロトタイプ関数を必要と、'/clr' オプション: '()' を '(void)' に変換します。
C4564|メソッド '*名前*' の*クラス*'*型*'はサポートされていない既定のパラメーター'*パラメーター*'
C4584|'*型*': 基底クラス'*宣言*'は、基本クラスでは既に'*宣言*'
C4608|共用体の複数のメンバーを初期化しています: '*型*'と'*型*'
C4619|#pragma warning: 警告番号がありません '*数*'
C4623|'*型*': 削除済みとして、既定のコンス トラクターが暗黙的に定義されています。
C4624|'*型*': デストラクターは暗黙的に削除済みとして定義
C4625|'*型*': 削除済みとして、コピー コンス トラクターが暗黙的に定義されています。
C4626|'*型*': 代入演算子が暗黙的に削除済みとして定義
C4645|'noreturn' で宣言された関数に return ステートメント
C4646|'noreturn' で宣言された関数が非 void 戻り値の型
C4659|#pragma '*説明*': 予約されたセグメントの使用'*名前*' #pragma を使用してコメント (linker,...) の動作が定義されていません
C4667|'*宣言*': 強制インスタンス化に一致するように定義された関数テンプレートはありません
C4668|'*名前*'は '0' に置き換える、プリプロセッサ マクロとして定義されていない'*値*'
C4669|'*式*': 安全でない変換:'*型*' は、マネージまたは WinRT 型のオブジェクト
C4674|'*名前*' 'static' と宣言しなければなりません、正確に 1 つのパラメーター
C4680|'*型*': コクラスは既定のインターフェイスを指定していません
C4681|'*型*': コクラスは、イベント ソースである既定のインターフェイスを指定していません
C4682|'*型*': 方向性のあるパラメーター属性がいません指定すると、[in]
C4683|'*宣言*': イベント ソースが 'out' のパラメーターは複数のイベント ハンドラーをフックするときに注意
C4684|'*説明*': 警告!! 属性が原因で、無効なコードの生成: 慎重に使用
C4685|テンプレート パラメーターの解析中に '> >' が必要ですが、'>>' が見つかりました。
C4700|初期化されていないローカル変数 '*名前*' を使用
C4701|ローカル変数が初期化されていない可能性がある '*名前*' を使用
C4702|到達できないコード
C4711|関数 '*名前*' 自動インライン展開の選択
C4714|関数 '*宣言*' インラインされています _ _forceinline として記述できません
C4715|'*関数*': 値を返さないコントロール パスのすべて
C4716|'*関数*': 値を返す必要があります
C4717|'*関数*': すべてのコントロール パスで再帰的で、関数には、ランタイム スタック オーバーフローが発生します
C4718|'*関数*': 再帰呼び出しに削除する副作用がありません
C4719|Qfast が指定された使用 'f' を 1 つの有効桁数を示すサフィックスとして時に検出された、二重の定数
C4723|0 による除算の潜在的です
C4724|剰余の 2 番目のオペランドは、コンパイル時に 0 と評価され、不定の結果を返します。
C4725|Pentium のモデルによっては、命令が不正確になります。
C4757|添字が大きな unsigned の値を負の定数を意図しましたか。
C4772|#import; 不足しているタイプ ライブラリから型を参照します。'*説明*' プレース ホルダーとして使用
C4792|関数 '*関数*' sysimport を使用して宣言されていて、参照されているネイティブ コードからのインポート ライブラリが リンクに必要な
C4794|スレッド ローカル ストレージ変数のセグメント '*名前*'から変更された'*セグメント*'to'*セグメント*'
C4798|p-code 関数に対して生成されたネイティブ コード '*名前*' 例外ハンドラーを持つか、アンワインド セマンティクス
C4799|関数 '*名前*' EMMS 命令がありません
C4803|'*宣言*': raise メソッドが、イベントと異なるストレージ クラス'*宣言*'
C4810|pragma の値 = =*数*
C4811|pragma の値に準拠して (forScope, show) = =*値*
C4820|'*型*':'*数*'バイトのパディングを追加した後*型*'*型*'
C4905|ワイド文字列リテラルをキャスト '*型*'
C4906|キャストされたリテラル文字列 '*型*'
C4912|'*属性*': 属性には、入れ子になった UDT 上で動作が定義されていません
C4916|dispid を指定するには、するには '*型*': インターフェイスによって導入されなければなりません
C4917|'*型*': GUID はクラス、インターフェイスまたは名前空間に関連付けできます。
C4918|'*文字*': プラグマ最適化リスト内の無効な文字
C4920|列挙型*名前*メンバー*名前*=*数*列挙型では既に*名前*として*名前*=*数*
C4921|'*名前*': 属性の値'*値*' 乗算は指定しないでください
C4925|'*宣言*': dispinterface メソッドは、スクリプトから呼び出すことはできません
C4926|'*宣言*': シンボルは既に定義されています属性は無視されます。
C4927|変換が正しくありません。1 つ以上のユーザー定義の変換が暗黙的に適用されています。
C4928|コピー初期化が正しくありません。複数のユーザー定義の変換が暗黙的に適用されています。
C4929|'*説明*': タイプ ライブラリには、共用体が含まれています 'embedded_idl' 修飾子は無視されます。
C4930|'*宣言*': プロトタイプ宣言された関数が呼び出されません (でした変数の定義が対象としていますか?)
C4931|用の種類のライブラリがビルドを想定しています*数*-ビットのポインター
C4932|_ _identifier (*説明*) と _ _identifier (*説明*) と区別することはできません
C4934|'__delegate(multicast)' の非推奨とされますが、代わりに ' _delegate' を使用して、
C4935|アセンブリ アクセス指定子 '*説明*'
C4944|'*名前*': シンボルをからインポートできません'*ソース*': '*宣言*'、現在のスコープに既に存在します
C4945|'*名前*': シンボルをからインポートできません'*ソース*': '*宣言*'が既にインポートされて別のアセンブリから'*ソース*'
C4946|reinterpret_cast が関連クラス間で使用されました: '*宣言*'と'*宣言*'
C4995|'*名前*': 名前が非推奨の #pragma としてマークされました
C4996|'*問題*':*の説明*
C4997|'*型*': コクラスは COM インターフェイスまたは擬似インターフェイスを実装していません
C4998|予測は失敗しました:*説明*(*数*)

## <a name="see-also"></a>関連項目

- [/Wv コンパイラ オプション](../../build/reference/compiler-option-warning-level.md)
- [既定で無効になっているコンパイラの警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md)
- [warning](../../preprocessor/warning.md)
