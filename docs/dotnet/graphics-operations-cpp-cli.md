---
title: グラフィック操作 (C +/cli CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: fd3c988f28e8de864fd22790ad60b49f1b6340b3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438562"
---
# <a name="graphics-operations-ccli"></a>グラフィック操作 (C++/CLI)

Windows SDK を使用して画像の操作を示します。

次のトピックでは、<xref:System.Drawing.Image?displayProperty=fullName> クラスを使用してイメージ操作を実行する方法を説明します。

## <a name="display"></a> .NET Framework を使用したイメージを表示します。

次のコード例へのポインターを取得する OnPaint イベント ハンドラーを変更する、<xref:System.Drawing.Graphics>メイン フォームのオブジェクト。 <xref:System.Windows.Forms.Form.OnPaint%2A>関数は、Visual Studio アプリケーション ウィザードで作成されたほとんどの場合、Windows フォーム アプリケーションを対象としています。

イメージがによって表される、<xref:System.Drawing.Image>クラス。 使用して、.jpg ファイルからイメージ データが読み込まれる、<xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>メソッド。 イメージをフォームに描画前に、画像に合わせて、フォームがサイズ変更します。 イメージの描画が実行される、<xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>メソッド。

<xref:System.Drawing.Graphics>と<xref:System.Drawing.Image>クラスはどちらも、<xref:System.Drawing?displayProperty=fullName>名前空間。

### <a name="example"></a>例

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override
{
    Graphics^ g = pe->Graphics;
    Image^ image = Image::FromFile("SampleImage.jpg");
    Form::ClientSize = image->Size;
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );
}
```

## <a name="draw"></a> .NET Framework を使用して図形を描画します。

次のコード例では、<xref:System.Drawing.Graphics>を変更するクラス、<xref:System.Windows.Forms.Form.OnPaint%2A>へのポインターを取得するイベント ハンドラー、<xref:System.Drawing.Graphics>メイン フォームのオブジェクト。 このポインターは、フォームの背景色を設定し、行とを使用して、円弧の描画に使用し、<xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName>と<xref:System.Drawing.Graphics.DrawArc%2A>メソッド。

### <a name="example"></a>例

```cpp
#using <system.drawing.dll>
using namespace System;
using namespace System::Drawing;
// ...
protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override
{
   Graphics^ g = pe->Graphics;
   g->Clear(Color::AntiqueWhite);

   Rectangle rect = Form::ClientRectangle;
   Rectangle smallRect;
   smallRect.X = rect.X + rect.Width / 4;
   smallRect.Y = rect.Y + rect.Height / 4;
   smallRect.Width = rect.Width / 2;
   smallRect.Height = rect.Height / 2;

   Pen^ redPen = gcnew Pen(Color::Red);
   redPen->Width = 4;
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);

   Pen^ bluePen = gcnew Pen(Color::Blue);
   bluePen->Width = 10;
   g->DrawArc( bluePen, smallRect, 90, 270 );
}
```

## <a name="rotate"></a> .NET Framework を使用したイメージを回転させる

次のコード例は、の使用を示します、<xref:System.Drawing.Image?displayProperty=fullName>クラスをディスクからイメージを読み込む、90 度回転、および新しい .jpg ファイルとして保存します。

### <a name="example"></a>例

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert"></a> .NET Framework を使用してイメージ ファイル形式に変換します。

次のコード例に示します、<xref:System.Drawing.Image?displayProperty=fullName>クラスおよび<xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName>列挙型に変換し、イメージ ファイルを保存するために使用します。 次のコードでは、.jpg ファイルからイメージを読み込み、.gif、.bmp の両方のファイル形式で保存します。

### <a name="example"></a>例

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;
using namespace System::Drawing::Imaging;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->Save("SampleImage.png", ImageFormat::Png);
   image->Save("SampleImage.bmp", ImageFormat::Bmp);

   return 0;
}
```

## <a name="related-sections"></a>関連項目

[グラフィックス プログラミングについて](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[GDI+ マネージド コードについて](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
