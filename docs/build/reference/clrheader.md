---
title: -CLRHEADER | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRHEADER
dev_langs: C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d8ab1617cffd7560ab47d69f7304df0c76b661eb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
-   1--/ CLR: safe (la imagen es MSIL solo puede ejecutarse en cualquier plataforma CLR y, posiblemente comprobable).  
  
-   3--/ CLR: pure (imagen es sólo MSIL, pero solo puede ejecutarse en x86 plataformas).  
  
 Puede comprobar mediante programación si una imagen se generó para common language runtime.  Para obtener más información, consulte [Cómo: determinar si una imagen es nativa o CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
## <a name="see-also"></a>Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)