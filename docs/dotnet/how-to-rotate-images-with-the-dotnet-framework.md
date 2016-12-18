---
title: "C&#243;mo: Girar im&#225;genes con .NET Framework | Microsoft Docs"
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
  - "GDI+ [C++], girar imágenes"
  - "gráficos [C++], girar imágenes"
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Girar im&#225;genes con .NET Framework
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el ejemplo de código siguiente se muestra el uso de la clase <xref:System.Drawing.Image?displayProperty=fullName> para cargar una imagen del disco, girarla 90 grados y guardarla como un archivo .jpg nuevo.  
  
> [!NOTE]
>  GDI\+ se incluye con Windows XP y está disponible como un componente redistribuible con Windows NT 4.0 SP 6, Windows 2000, Windows 98 y Windows Millennium.  Para descargar el último redistribuible, vea [http:\/\/go.microsoft.com\/fwlink\/?linkid\=11232](http://go.microsoft.com/fwlink/?linkid=11232).  Para obtener más información, vea [GDI\+](_gdiplus_GDI_start_cpp).  
  
## Ejemplo  
  
```  
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
  
## Vea también  
 [Programación de .NET con C\+\+\/CLI](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)