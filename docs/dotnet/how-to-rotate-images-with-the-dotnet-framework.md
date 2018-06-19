---
title: 'Cómo: girar imágenes con .NET Framework | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], rotating images
- graphics [C++], rotating images
ms.assetid: e32104d5-87d0-47a9-a22f-9bc835b7e8d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 94290c05ecca9fc7211e2bc85640ec0308137804
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129039"
---
# <a name="how-to-rotate-images-with-the-net-framework"></a>Cómo: Girar imágenes con .NET Framework
En el ejemplo de código siguiente se muestra el uso de la <xref:System.Drawing.Image?displayProperty=fullName> clase para cargar una imagen desde el disco, girar 90 grados y guardarla como un archivo .jpg nuevo.  
  
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