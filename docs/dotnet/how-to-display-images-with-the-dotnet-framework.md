---
title: "C&#243;mo: Mostrar im&#225;genes con .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GDI+ [C++], mostrar imágenes"
  - "gráficos [C++], mostrar imágenes"
ms.assetid: c0eddfa1-4bd6-4af5-a533-1fa84b360325
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Mostrar im&#225;genes con .NET Framework
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El ejemplo de código siguiente modifica el controlador de eventos OnPaint para recuperar un puntero al objeto <xref:System.Drawing.Graphics> para el formulario principal.  La función <xref:System.Windows.Forms.Form.OnPaint%2A> se ha diseñado para una aplicación de Windows Forms, probablemente creada con un asistente para aplicaciones de Visual Studio.  
  
 La imagen se representa mediante la clase <xref:System.Drawing.Image>.  Los datos de la imagen se cargan desde un archivo .jpg utilizando el método <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName>.  Antes de llevar la imagen al formulario, se cambia el tamaño del formulario para que quepa la imagen.  El traslado de la imagen se realiza con el método <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName>.  
  
 Las clases <xref:System.Drawing.Graphics> y <xref:System.Drawing.Image> están en el espacio de nombres <xref:System.Drawing?displayProperty=fullName>.  
  
> [!NOTE]
>  GDI\+ se incluye con Windows XP y está disponible como componente redistribuible con Windows NT 4.0 SP 6, Windows 2000, Windows 98 y Windows Me.  Para descargar el último redistribuible, vea [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232).  Para obtener más información, consulte la documentación existente sobre SDK de GDI\+ en [GDI\+](_gdiplus_GDI_start_cpp).  
  
## Ejemplo  
  
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
  
## Vea también  
 <xref:System.Drawing?displayProperty=fullName>   
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)