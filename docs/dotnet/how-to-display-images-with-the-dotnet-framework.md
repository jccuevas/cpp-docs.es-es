---
title: 'Cómo: mostrar imágenes con .NET Framework | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4a7f3ed2d8fe90501b5ef3d0ae5028890fe5290e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33128584"
---
# <a name="how-to-display-images-with-the-net-framework"></a>Cómo: Mostrar imágenes con .NET Framework
En el ejemplo de código siguiente se modifica el controlador de eventos OnPaint para recuperar un puntero a la <xref:System.Drawing.Graphics> objeto para el formulario principal. El <xref:System.Windows.Forms.Form.OnPaint%2A> función está diseñado para una aplicación de formularios Windows Forms, probablemente creada con un Asistente para aplicaciones de Visual Studio.  
  
 La imagen se representa mediante la <xref:System.Drawing.Image> clase. Los datos de imagen se cargan desde un archivo .jpg utilizando el <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> método. Antes de que se dibuja la imagen al formulario, el formulario cambia de tamaño para dar cabida a la imagen. El dibujo de la imagen se realiza con el <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> método.  
  
 El <xref:System.Drawing.Graphics> y <xref:System.Drawing.Image> clases están en el <xref:System.Drawing?displayProperty=fullName> espacio de nombres.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="see-also"></a>Vea también  
 <xref:System.Drawing?displayProperty=fullName>   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)