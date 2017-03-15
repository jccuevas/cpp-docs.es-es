---
title: "Problemas comunes al crear versiones de lanzamiento | Microsoft Docs"
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
  - "compilaciones de depuración, diferencia con las versiones de lanzamiento"
  - "asignador de memoria de depuración"
  - "depurar [MFC], versiones de lanzamiento"
  - "problemas en la disposición del montón"
  - "memoria [C++], sobrescrituras"
  - "MFC [C++], versiones de lanzamiento"
  - "optimización [C++], compilador"
  - "punteros, perdidos"
  - "proyectos [C++], configuración de depuración"
  - "versiones de lanzamiento, compilar aplicaciones"
  - "versiones de lanzamiento, solucionar problemas"
  - "punteros perdidos"
  - "solución de problemas de las versiones de lanzamiento"
  - "solucionar problemas de Visual C++"
  - "generación de código no esperado"
ms.assetid: 73cbc1f9-3e33-472d-9880-39a8e9977b95
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Problemas comunes al crear versiones de lanzamiento
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Durante la fase de desarrollo, normalmente, se compila y se prueba con una versión de depuración del proyecto.  En ese caso, si la aplicación se compila para una versión de lanzamiento, se puede producir una infracción de acceso.  
  
 La siguiente lista muestra las diferencias principales entre una versión de depuración y una de lanzamiento.  Existen otras diferencias; sin embargo, a continuación, se indican las diferencias principales que producirían un error en una aplicación compilada para una versión de lanzamiento que funciona en una versión de depuración.  
  
-   [Disposición del montón](#_core_heap_layout)  
  
-   [Compilación](#_core_compilation)  
  
-   [Utilización de punteros](#_core_pointer_support)  
  
-   [Optimizaciones](#_core_optimizations)  
  
 Vea la opción [\/GZ \(Detectar errores de compilación de lanzamiento en compilaciones de depuración\)](../../build/reference/gz-enable-stack-frame-run-time-error-checking.md) del compilador para obtener información sobre cómo detectar errores de compilación de lanzamiento en compilaciones de depuración.  
  
##  <a name="_core_heap_layout"></a> Disposición del montón  
 La disposición del montón es la causa de cerca de un noventa por ciento de los problemas de una aplicación que funciona correctamente en modo de depuración pero no en su versión de lanzamiento.  
  
 Cuando el proyecto se compila para depuración, se utiliza el asignador de memoria de depuración.  Esto significa que todas las asignaciones de memoria disponen de bytes de protección asociados.  Estos bytes de protección detectan cualquier sobrescritura en memoria.  Como la disposición del montón difiere entre las versiones de lanzamiento y de depuración, una sobrescritura en memoria podría no producir ningún problema en una versión de depuración, pero podría tener efectos catastróficos en una versión de lanzamiento.  
  
 Para obtener más información, vea [Comprobar si se ha sobrescrito la memoria](../../build/reference/checking-for-memory-overwrites.md) y [Utilizar la versión de depuración para comprobar si se ha sobrescrito la memoria](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md).  
  
##  <a name="_core_compilation"></a> Compilación  
 Muchas de las macros de MFC y gran parte de la implementación de MFC cambian cuando se compila una versión de lanzamiento.  En particular, la macro ASSERT no se evalúa en una versión de lanzamiento, de modo que no se ejecuta el código incluido en instrucciones ASSERT.  Para obtener más información, vea [Examinar instrucciones ASSERT](../../build/reference/using-verify-instead-of-assert.md).  
  
 Algunas funciones se implementan inline para incrementar la velocidad en la versión de lanzamiento.  Normalmente, las optimizaciones se activan en las versiones de lanzamiento.  Además, se utiliza un asignador de memoria diferente.  
  
##  <a name="_core_pointer_support"></a> Utilización de punteros  
 La ausencia de información de depuración quita los datos de relleno de la aplicación.  En una versión de lanzamiento, los punteros perdidos tienen una gran probabilidad de apuntar a memoria sin inicializar en vez de apuntar a información de depuración.  
  
##  <a name="_core_optimizations"></a> Optimizaciones  
 Según la naturaleza de ciertos segmentos de código, el compilador de optimización podría generar código no esperado.  Ésta es la causa menos probable de problemas en versiones de lanzamiento, pero ocurre en ocasiones.  Para obtener una solución, vea [Optimizar el código](../../build/reference/optimizing-your-code.md).  
  
## Vea también  
 [Versiones de lanzamiento](../../build/reference/release-builds.md)   
 [Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)