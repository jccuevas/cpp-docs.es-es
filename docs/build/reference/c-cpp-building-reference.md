---
title: "Referencia de compilaci&#243;n de C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compilaciones [C++], información adicional"
  - "cl.exe (compilador) [C++], compilar programas"
  - "compilar código fuente [C++], información adicional"
  - "vinculador [C++], referencia de compilación"
ms.assetid: 100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Referencia de compilaci&#243;n de C/C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ ofrece dos métodos para compilar un programa de C\/C\+\+.  El más sencillo \(y utilizado\) consiste en [compilar desde el entorno de desarrollo de Visual C\+\+](../../ide/building-cpp-projects-in-visual-studio.md).  El otro método consiste en [compilar desde el símbolo del sistema mediante las herramientas de la línea de comandos](../../build/building-on-the-command-line.md).  En ambos casos, es posible crear archivos de código fuente tanto con el editor de código fuente de Visual C\+\+ como con cualquier editor de otro fabricante.  
  
 En caso de que el programa utilice un archivo Make en lugar de un archivo .vcxproj, será posible compilarlo en el entorno de desarrollo en forma de [proyecto externo](../../ide/building-external-projects.md).  
  
## En esta sección  
 [Compilar un programa escrito en C\/C\+\+](../../build/reference/compiling-a-c-cpp-program.md)  
 Describe el compilador, que crea un archivo objeto con código máquina, directivas de vinculador, secciones, referencias externas y nombres de funciones y datos.  
  
 [Vinculación](../../build/reference/linking.md)  
 Describe el vinculador, que combina código de los archivos objeto creados por el compilador y de bibliotecas vinculadas estáticamente, resuelve las referencias de nombres y crea un archivo ejecutable.  
  
 [Versiones de lanzamiento](../../build/reference/release-builds.md)  
 Explica por qué y cuándo debería cambiar de una versión de depuración a una de lanzamiento y algunos problemas que puede encontrarse en ese cambio.  
  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)  
 Proporciona vínculos a temas que describen los mecanismos para optimizar código:  
  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)  
 Proporciona las siguientes herramientas de línea de comandos para ver y manipular el resultado de la compilación:  
  
 [Errores de compilación de C\/C\+\+](../../error-messages/compiler-errors-1/c-cpp-build-errors.md)  
 Presenta la sección de errores de compilación en la tabla de contenido.  
  
## Secciones relacionadas  
 [Referencia del preprocesador de C\/C\+\+](../../preprocessor/c-cpp-preprocessor-reference.md)  
 Describe el preprocesador, que prepara los archivos de código fuente para el compilador mediante la conversión de macros, operadores y directivas.  
  
 [Introducción a los pasos de generación personalizada y los eventos de compilación](../../ide/understanding-custom-build-steps-and-build-events.md)  
 Describe cómo personalizar el proceso de compilación.  
  
 [Compilar un programa escrito en C\/C\+\+](../../build/building-c-cpp-programs.md)  
 Contiene vínculos a temas en los que se describe la generación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.  
  
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
 Describe cómo configurar las opciones del compilador en el entorno de desarrollo o en la línea de comandos.  
  
 [Opciones del compilador](../../build/reference/compiler-options.md)  
 Proporciona vínculos a temas que describen las opciones del compilador.  
  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
 Describe cómo configurar las opciones del vinculador dentro y fuera del entorno de desarrollo integrado.  
  
 [Opciones del vinculador](../../build/reference/linker-options.md)  
 Proporciona vínculos a temas que describen las opciones del vinculador.  
  
 [Referencia de BSCMAKE](../../build/reference/bscmake-reference.md)  
 Describe la Utilidad de mantenimiento de información de examen de Microsoft \(BSCMAKE.EXE\), que genera un archivo de información de examen \(.bsc\) a partir de los archivos .sbr creados durante la compilación.  
  
 [Referencia de LIB](../../build/reference/lib-reference.md)  
 Describe el Administrador de bibliotecas de Microsoft \(LIB.exe\), que permite crear y administrar una biblioteca de archivos objeto COFF \(formato de archivo objeto común\).  
  
 [Referencia de EDITBIN](../../build/reference/editbin-reference.md)  
 Describe el Editor de archivos binarios COFF de Microsoft \(EDITBIN.EXE\), que modifica archivos binarios COFF \(formato de archivo objeto común\).  
  
 [Referencia de DUMPBIN](../../build/reference/dumpbin-reference.md)  
 Describe Microsoft COFF Binary File Dumper \(DUMPBIN.EXE\), que muestra información acerca de archivos binarios COFF \(formato de archivo objeto común\).  
  
 [Referencia de NMAKE](../../build/nmake-reference.md)  
 Describe Microsoft Program Maintenance Utility \(NMAKE.EXE\), que es una herramienta que compila proyectos tomando como base los comandos contenidos en un archivo de descripción.