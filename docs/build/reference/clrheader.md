---
title: "/CLRHEADER | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRHEADER"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRHEADER (opción de dumpbin)"
  - "CLRHEADER (opción de dumpbin)"
  - "-CLRHEADER (opción de dumpbin)"
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRHEADER
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRHEADER file  
```  
  
## Comentarios  
 donde:  
  
 `file`  
 Es un archivo de imagen compilado con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Comentarios  
 CLRHEADER muestra información acerca de los encabezados .NET utilizados en cualquier programa administrado.  Los resultados muestran la ubicación y el tamaño en bytes del encabezado .NET y de las secciones del encabezado.  
  
 En los archivos producidos con la opción de compilador [\/GL](../../build/reference/gl-whole-program-optimization.md) sólo está disponible la opción [\/HEADERS](../../build/reference/headers.md) de DUMPBIN.  
  
 Cuando \/CLRHEADER se utiliza en un archivo que se compiló con \/clr, habrá una sección **clr Header:** en el resultado de dumpbin.  El valor de los **marcadores** indica qué opción \/clr se utilizó:  
  
-   0  \-\- \/clr \(la imagen puede contener código nativo\).  
  
-   1 \-\- \/clr:safe \(la imagen es sólo MSIL, puede ejecutarse en cualquier plataforma CLR y es posiblemente comprobable\).  
  
-   3 \-\- \/clr:pure \(la imagen es sólo MSIL, pero sólo puede ejecutarse en plataformas x86\).  
  
 También puede comprobar mediante programación si una imagen se compiló para Common Language Runtime.  Para obtener más información, vea [Cómo: Determinar si una imagen es nativa o CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)