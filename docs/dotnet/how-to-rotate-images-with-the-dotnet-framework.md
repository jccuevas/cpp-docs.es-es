---
title: "Cómo: girar imágenes con .NET Framework | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 387bd9733ad591f45ef206be8856d4dd4edd464d
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>Cómo: Girar imágenes con .NET Framework
En el ejemplo de código siguiente se muestra el uso de la <xref:System.Drawing.Image?displayProperty=fullName> clase para cargar una imagen desde el disco, girar 90 grados y guardarla como un archivo .jpg nuevo.  
  
> [!NOTE]
>  GDI + se incluye con Windows XP y está disponible como componente redistribuible para Windows NT 4.0 Service Pack 6, Windows 2000, Windows 98 y Windows Millennium Edition. Para descargar el último redistribuible, vea [http://go.microsoft.com/fwlink/p/?linkid=11232](http://go.microsoft.com/fwlink/p/?linkid=11232). 
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="see-also"></a>Vea también  
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)