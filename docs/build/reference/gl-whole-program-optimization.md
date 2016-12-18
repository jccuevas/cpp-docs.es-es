---
title: "/GL (Optimizaci&#243;n de todo el programa) | Microsoft Docs"
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
  - "/gl"
  - "VC.Project.VCCLWCECompilerTool.WholeProgramOptimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GL (opción del compilador) [C++]"
  - "GL (opción del compilador) [C++]"
  - "-GL (opción del compilador) [C++]"
  - "optimizaciones completas del programa y compilador de C++"
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /GL (Optimizaci&#243;n de todo el programa)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la optimización completa del programa.  
  
## Sintaxis  
  
```  
/GL[-]  
```  
  
## Comentarios  
 La optimización de todo el programa permite al compilador realizar optimizaciones con información de todos los módulos del programa.  Sin la optimización de todo el programa, las optimizaciones se llevan a cabo módulo a módulo \(compilando\).  
  
 La optimización de todo el programa está desactivada de forma predeterminada y debe habilitarse explícitamente.  Sin embargo, también es posible deshabilitarla explícitamente mediante **\/GL\-**.  
  
 Con información de todos los módulos, el compilador puede:  
  
-   Optimizar el uso de los registros más allá de los límites de las funciones.  
  
-   Consiga efectuar un mejor seguimiento de las modificaciones a los datos globales, permitiendo una reducción del número de cargas y almacenes.  
  
-   Consiga efectuar un mejor seguimiento del posible conjunto de elementos modificados al desreferenciar un puntero, reduciendo los números de cargas y almacenes.  
  
-   Procesar una función inline en un módulo incluso si la función está definida en otro módulo.  
  
 Los archivos .obj generados con **\/GL** no estarán disponibles para utilidades de vinculador del tipo [EDITBIN](../../build/reference/editbin-reference.md) y [DUMPBIN](../../build/reference/dumpbin-reference.md).  
  
 Si compila un programa con **\/GL** y [\/c](../../build/reference/c-compile-without-linking.md), debe utilizar la opción del vinculador \/LTCG para crear el archivo de salida.  
  
 [\/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) no se puede usar con **\/GL**  
  
 El formato de los archivos generados con **\/GL** en la versión actual puede no ser legible con versiones posteriores de Visual C\+\+.  No distribuya un archivo .lib compuesto por archivos .obj generados con **\/GL** a menos que esté dispuesto a distribuir copias del archivo .lib para todas las versiones de Visual C\+\+ que puedan utilizar sus usuarios, ahora y en el futuro.  
  
 Los archivos .obj generados con **\/GL** y los archivos de encabezado precompilados no deben utilizarse para compilar un archivo .lib salvo que éste se vincule en el mismo equipo en que se generó el archivo .obj de **\/GL**.  La información del archivo de encabezado precompilado del archivo .obj se necesita para realizar la vinculación.  
  
 Para obtener más información sobre las optimizaciones disponible con y las limitaciones de la optimización completa del programa, vea [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md).  **\/GL** crea también la optimización guiada por perfiles \(PGO\) disponible; vea \/LTCG.  Cuando compile para obtener optimizaciones guiadas por perfiles, y si desea que haya ordenación de funciones desde estas optimizaciones, debe compilar con [\/Gy](../../build/reference/gy-enable-function-level-linking.md) o con una opción del compilador que implique \/Gy.  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Vea [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md) para obtener información sobre cómo especificar **\/GL** en el entorno de desarrollo.  
  
### Para establecer esta opción del vinculador mediante programación  
  
1.  Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)