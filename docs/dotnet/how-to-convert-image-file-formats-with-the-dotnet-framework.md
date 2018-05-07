---
title: 'Cómo: convertir formatos de archivo de imagen con .NET Framework | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 98d55c7ee4ca967a0b52bd87b22e5c316eb1e274
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>Cómo: Convertir formatos de archivo de imagen con .NET Framework
En el ejemplo de código siguiente se muestra la <xref:System.Drawing.Image?displayProperty=fullName> clase y el <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> enumeración que se usa para convertir y guardar archivos de imagen. El siguiente código carga una imagen desde un archivo .jpg y, a continuación, guarda en formatos de archivo .gif y .bmp.  
  
## <a name="example"></a>Ejemplo  
  
```  
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
  
## <a name="see-also"></a>Vea también  
 <xref:System.Drawing>   
 [Programación de .NET con C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)