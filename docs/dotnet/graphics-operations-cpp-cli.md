---
title: Las operaciones de gráficos (C++ / c++ / CLI) | Microsoft Docs
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
ms.openlocfilehash: fd28a97b9e1b6238e4f231845282739a6d15aeb2
ms.sourcegitcommit: b8b1cba85ff423142d73c888be26baa8c33f3cdc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/17/2018
ms.locfileid: "39092986"
---
# <a name="graphics-operations-ccli"></a>Operaciones de gráficos (C++/CLI)
Muestra la manipulación de imágenes usando [!INCLUDE[winsdklong](../dotnet/includes/winsdklong_md.md)].  
  
 En los temas siguientes se muestra el uso de la clase <xref:System.Drawing.Image?displayProperty=fullName> para realizar la manipulación de imágenes.  
  
## <a name="display"></a> Mostrar imágenes con .NET Framework
En el ejemplo de código siguiente se modifica el controlador de eventos OnPaint para recuperar un puntero a la <xref:System.Drawing.Graphics> objeto para el formulario principal. El <xref:System.Windows.Forms.Form.OnPaint%2A> función está destinada a una aplicación de Windows Forms, más probable es que se creó con un Asistente para aplicaciones de Visual Studio.  
  
 La imagen se representa mediante el <xref:System.Drawing.Image> clase. Los datos de imagen se cargan desde un archivo .jpg mediante el <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> método. Antes de que se dibuje la imagen al formulario, el formulario cambia de tamaño para dar cabida a la imagen. El dibujo de la imagen se realiza con el <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> método.  
  
 El <xref:System.Drawing.Graphics> y <xref:System.Drawing.Image> clases están en el <xref:System.Drawing?displayProperty=fullName> espacio de nombres.  
  
### <a name="example"></a>Ejemplo  
  
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

## <a name="draw"></a> Dibujar formas con .NET Framework
El siguiente ejemplo de código utiliza el <xref:System.Drawing.Graphics> clase para modificar el <xref:System.Windows.Forms.Form.OnPaint%2A> controlador de eventos para recuperar un puntero a la <xref:System.Drawing.Graphics> objeto para el formulario principal. Este puntero, a continuación, se usa para establecer el color de fondo del formulario y dibujar una línea y un arco utilizando el <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> y <xref:System.Drawing.Graphics.DrawArc%2A> métodos.  
  
### <a name="example"></a>Ejemplo  
  
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

## <a name="rotate"></a> Girar imágenes con .NET Framework
En el ejemplo de código siguiente se muestra el uso de la <xref:System.Drawing.Image?displayProperty=fullName> clase para cargar una imagen de disco, girarlo 90 grados y guárdelo como un archivo .jpg nuevo.  
  
### <a name="example"></a>Ejemplo  
  
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

## <a name="convert"></a> Convertir formatos de archivo de imagen con .NET Framework
En el ejemplo de código siguiente se muestra el <xref:System.Drawing.Image?displayProperty=fullName> clase y el <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> enumeración que se usa para convertir y guardar archivos de imagen. El siguiente código carga una imagen desde un archivo .jpg y, a continuación, guarda en formatos de archivo .gif y. bmp.  
  
### <a name="example"></a>Ejemplo  
  
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
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Introducción a la programación de gráficos](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)  
  
 [About GDI+ Managed Code](/dotnet/framework/winforms/advanced/about-gdi-managed-code) (Acerca del código administrado de GDI+)    
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

 <xref:System.Drawing>
 