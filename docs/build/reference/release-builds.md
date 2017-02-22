---
title: "Versiones de lanzamiento | Microsoft Docs"
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
  - "compilaciones de depuración, convertir a una versión de lanzamiento"
  - "depurar [C++], versiones de lanzamiento"
  - "versiones de lanzamiento"
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Versiones de lanzamiento
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las versiones de lanzamiento utilizan optimizaciones.  Cuando se utilizan optimizaciones para crear una versión de lanzamiento, el compilador no produce información simbólica de depuración.  La ausencia de información simbólica de depuración, junto con el hecho de que no se genera código para llamadas TRACE y ASSERT, implica que el archivo ejecutable es más reducido y, por lo tanto, más rápido.  
  
 Esta sección presenta información sobre por qué y cuándo cambiar de una versión de depuración a una versión de lanzamiento.  Asimismo, trata algunos de los problemas que se pueden encontrar al cambiar de una versión de depuración a una versión de lanzamiento:  
  
-   [Crear versiones de lanzamiento](../../build/reference/how-to-create-a-release-build.md)  
  
-   [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
-   [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)  
  
    -   [Examinar instrucciones ASSERT](../../build/reference/using-verify-instead-of-assert.md)  
  
    -   [Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)  
  
    -   [Depurar versiones de lanzamiento](../../build/reference/how-to-debug-a-release-build.md)  
  
    -   [Comprobar si se ha sobrescrito la memoria](../../build/reference/checking-for-memory-overwrites.md)  
  
## Vea también  
 [Compilar proyectos de C\+\+ en Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)   
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)