---
title: "Establecer las opciones del compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), establecer opciones"
  - "opciones del compilador, establecer"
ms.assetid: 4b079f5b-0017-4124-aad6-0d2b58e427e0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Establecer las opciones del compilador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las opciones del compilador de C y C\+\+ pueden definirse en el entorno de desarrollo o en la línea de comandos.  
  
## En el entorno de desarrollo  
 Puede establecer opciones del compilador para cada proyecto en el cuadro de diálogo **Páginas de propiedades**.  En el panel izquierdo, seleccione **Propiedades de configuración**, **C\/C\+\+** y elija la categoría de la opción del compilador.  En el tema de cada opción del compilador se describe cómo puede definirse y dónde se encuentra en el entorno de desarrollo.  Vea [Opciones del compilador](../../build/reference/compiler-options.md) para obtener una lista completa.  
  
## Fuera del entorno de desarrollo  
 Las opciones del compilador \(CL.exe\) pueden definirse:  
  
-   [En la línea de comandos](../../build/reference/compiler-command-line-syntax.md)  
  
-   [En archivos de comandos](../../build/reference/cl-command-files.md)  
  
-   [En la variable de entorno de CL](../../build/reference/cl-environment-variables.md)  
  
 Las opciones especificadas en la variable de entorno de CL se usan cada vez que se invoca CL.  Si se menciona un archivo de comandos en la variable de entorno de CL o en la línea de comandos, se usarán las opciones especificadas en dicho archivo.  A diferencia de la línea de comandos o la variable de entorno de CL, un archivo de comandos permite utilizar varias líneas de opciones y nombres de archivo.  
  
 Las opciones del compilador se procesan "de izquierda a derecha" y, si se detecta un conflicto, tiene prioridad la última opción \(la que está situada más a la derecha\).  La variable de entorno de CL se procesa antes que la línea de comandos, por lo que siempre tendrá prioridad en caso de conflicto con la línea de comandos.  
  
## Temas adicionales relacionados con el compilador  
  
-   [Compilación rápida](../../build/reference/fast-compilation.md)  
  
-   [CL invoca el vinculador](../../build/reference/cl-invokes-the-linker.md)  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)