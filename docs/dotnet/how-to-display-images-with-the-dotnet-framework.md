---
title: "Cómo: mostrar imágenes con .NET Framework | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], displaying images
- graphics [C++], displaying images
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7c12d6a67f6fbe73802d3b876621a2ea606af553
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-display-images-with-the-net-framework"></a>Cómo: Mostrar imágenes con .NET Framework
En el ejemplo de código siguiente se modifica el controlador de eventos OnPaint para recuperar un puntero a la <xref:System.Drawing.Graphics> objeto para el formulario principal. El <xref:System.Windows.Forms.Form.OnPaint%2A> función está diseñado para una aplicación de formularios Windows Forms, probablemente creada con un Asistente para aplicaciones de Visual Studio.  
  
 La imagen se representa mediante la <xref:System.Drawing.Image> clase. Los datos de imagen se cargan desde un archivo .jpg utilizando el <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> método. Antes de que se dibuja la imagen al formulario, el formulario cambia de tamaño para dar cabida a la imagen. El dibujo de la imagen se realiza con el <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> método.  
  
 El <xref:System.Drawing.Graphics> y <xref:System.Drawing.Image> clases están en el <xref:System.Drawing?displayProperty=fullName> espacio de nombres.  
  
> [!NOTE]
>  GDI + se incluye con Windows XP y está disponible como componente redistribuible para Windows NT 4.0 Service Pack 6, Windows 2000, Windows 98 y Windows Millennium Edition. Para descargar el último redistribuible, vea [http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232).   
  
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