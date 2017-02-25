---
title: "Optimizar el c&#243;digo | Microsoft Docs"
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
  - "cl.exe (compilador), rendimiento"
  - "código, optimizar"
  - "optimización"
  - "optimización, código C++"
  - "rendimiento, compilador"
  - "rendimiento, optimizar código"
ms.assetid: 4f33e6c7-9870-43b3-9c2f-d7e44f764971
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# Optimizar el c&#243;digo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Si optimiza un ejecutable, puede lograr un equilibrio entre una velocidad de ejecución rápida y un tamaño de código pequeño.  En este tema se analizan algunos mecanismos que proporciona Visual C\+\+ para ayudarle a optimizar el código.  
  
## Características del lenguaje  
 En los siguientes temas se describen algunas de las características de optimización del lenguaje de C\/C\+\+.  
  
 [Directivas pragma y palabras clave de optimización](../../build/reference/optimization-pragmas-and-keywords.md)  
 Una lista de palabras clave y pragmas que puede utilizar en el código para mejorar el rendimiento.  
  
 [Opciones del compilador por categoría](../../build/reference/compiler-options-listed-by-category.md)  
 Una lista de opciones del compilador **\/O** que afectan específicamente a la velocidad de ejecución o al tamaño del código.  
  
 [Declarador de referencia a un valor R: &&](../../cpp/rvalue-reference-declarator-amp-amp.md)  
 Las referencias a valor R \(Rvalue\) admiten la implementación de la *semántica de transferencia de recursos*.  Si se utiliza la semántica de transferencia de recursos para implementar las bibliotecas de plantillas, el rendimiento de las aplicaciones que utilizan esas plantillas puede mejorar significativamente.  
  
### La directiva pragma Optimize  
 Si una sección optimizada del código origina errores o ralentiza la ejecución, puede utilizar la directiva pragma [optimize](../../preprocessor/optimize.md) para desactivar la optimización en esa sección.  
  
 Limite la sección de código con dos directivas pragma, según se indica a continuación.  
  
```  
#pragma optimize("", off)  
// some code here   
#pragma optimize("", on)  
```  
  
## Programar prácticas  
 Puede que vea algunos mensajes de advertencia adicionales al compilar el código con optimización.  Este es el comportamiento previsto, ya que algunas advertencias solo están relacionadas con el código optimizado.  Puede evitar muchos problemas de optimización si tiene en cuenta estas advertencias.  
  
 Paradójicamente, la optimización de un programa para aumentar la velocidad, puede hacer que el código se ejecute más despacio.  Esto se debe a que algunas optimizaciones de velocidad aumentan el tamaño del código.  Por ejemplo, al poner las funciones en línea se elimina la sobrecarga de las llamadas de función.  Sin embargo, incluir demasiadas funciones en línea podría hacer su programa tan grande que el número de errores de página de memoria virtual aumentase.  Así, la velocidad ganada al eliminar las llamadas a funciones puede perderse a causa del intercambio de memoria.  
  
 En los siguientes temas se analizan procedimientos de programación adecuados.  
  
 [Sugerencias para mejorar código en el que la velocidad de ejecución es importante](../../build/reference/tips-for-improving-time-critical-code.md)  
 Técnicas mejores de codificación pueden producir mejor rendimiento.  En este tema se sugieren técnicas de codificación que pueden ayudarle a asegurarse de que las partes del código que llevan mucho tiempo funcionan correctamente.  
  
 [Procedimientos recomendados para la optimización](../../build/reference/optimization-best-practices.md)  
 Proporciona directrices generales sobre la mejor forma de optimizar la aplicación.  
  
## Depurar código optimizado  
 Dado que la optimización puede cambiar el código creado por el compilador, se recomienda depurar la aplicación y medir su rendimiento antes y después de optimizar el código.  
  
 Los temas siguientes proporcionan información básica sobre cómo depurar.  
  
-   [Depurar en Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md)  
  
-   [Problemas comunes al crear versiones de lanzamiento](../../build/reference/common-problems-when-creating-a-release-build.md)  
  
 En los temas siguientes se ofrece información más avanzada sobre cómo depurar.  
  
-   [Cómo: Depurar código optimizado](../Topic/How%20to:%20Debug%20Optimized%20Code.md)  
  
-   [Por qué los números de punto flotante pierden precisión](../../build/reference/why-floating-point-numbers-may-lose-precision.md)  
  
 El siguiente gran variedad de temas proporciona información sobre cómo optimizar la compilación, la carga y ejecutar el código.  
  
-   [Mejorar el rendimiento del compilador](../../build/reference/improving-compiler-throughput.md)  
  
-   [La utilización de un nombre de función sin \(\) no genera código](../../build/reference/using-function-name-without-parens-produces-no-code.md)  
  
-   [Optimizar un ensamblado alineado](../../assembler/inline/optimizing-inline-assembly.md)  
  
-   [Especificar optimizaciones del compilador para un proyecto ATL](../../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)  
  
-   [¿Qué técnicas de optimización se deben utilizar para mejorar el rendimiento de las aplicaciones cliente al cargarlas?](../../build/what-optimization-techniques-should-i-use.md)  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)] cómo reducir el tiempo de carga de métodos DLL, vea “optimizing DLL load time performance” en la columna “Under the Hood” de “MSDN Magazine” en[MSDN Library](http://go.microsoft.com/fwlink/?linkid=556) el sitio Web.  
  
-   [!INCLUDE[crabout](../../build/reference/includes/crabout_md.md)] cómo minimizar la paginación en aplicaciones, vea “rendimiento en tiempo de ejecución de Artículos con la herramienta suavizado del espacio de trabajo” y “rendimiento en tiempo de ejecución de Artículos con la herramienta \- Part suavizado 2 " del espacio de trabajo en la columna “Bugslayer” de “MSDN Magazine” en[MSDN Library](http://go.microsoft.com/fwlink/?linkid=556) el sitio Web.  
  
## Vea también  
 [Referencia de compilación de C\/C\+\+](../../build/reference/c-cpp-building-reference.md)