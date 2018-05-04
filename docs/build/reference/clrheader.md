---
title: -CLRHEADER | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5896e12d5e3b3b3984884388d11c6380e900d73d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="clrheader"></a>/CLRHEADER
```  
/CLRHEADER file  
```  
  
## <a name="remarks"></a>Comentarios  
 donde:  
  
 `file`  
 Genera un archivo de imagen con [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="remarks"></a>Comentarios  
 CLRHEADER muestra información acerca de los encabezados .NET utilizados en cualquier programa administrado. El resultado muestra la ubicación y el tamaño, en bytes, de las secciones en el encabezado y el encabezado. NET.  
  
 Solo el [/HEADERS](../../build/reference/headers.md) está disponible para su uso en los archivos producidos con la opción de DUMPBIN el [/GL](../../build/reference/gl-whole-program-optimization.md) opción del compilador.  
  
 Cuando /CLRHEADER se utiliza en un archivo que se compiló con/CLR, habrá una **encabezado clr:** sección en el resultado de dumpbin.  El valor de **marcas** indica qué opción /clr se utilizó:  
  
-   0--/clr (la imagen puede contener código nativo).  
  
 Puede comprobar mediante programación si una imagen se generó para common language runtime.  Para obtener más información, consulte [Cómo: determinar si una imagen es nativa o CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y se quitará en una versión futura del compilador. El código que debe ser "pura" o "segura" se debe pasar a C#. 
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)