---
title: "/Tc, /Tp, /TC, /TP (Especificar el tipo de archivo de c&#243;digo fuente) | Microsoft Docs"
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
  - "VC.Project.VCCLWCECompilerTool.CompileAs"
  - "VC.Project.VCCLCompilerTool.CompileAs"
  - "/Tp"
  - "/tc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Tc (opción del compilador) [C++]"
  - "/Tp (opción del compilador) [C++]"
  - "archivos de código fuente, especificar al compilador"
  - "Tc (opción del compilador) [C++]"
  - "-Tc (opción del compilador) [C++]"
  - "Tp (opción del compilador) [C++]"
  - "-Tp (opción del compilador) [C++]"
ms.assetid: 7d9d0a65-338b-427c-8b48-fff30e2f9d2b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Tc, /Tp, /TC, /TP (Especificar el tipo de archivo de c&#243;digo fuente)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción **\/Tc** especifica que `filename` es un archivo de código fuente de C, aunque no tenga una extensión .c.  La opción **\/Tp** especifica que `filename` es un archivo de código fuente de C\+\+, aunque no tenga la extensión .cpp o .cxx.  Dejar un espacio entre la opción y `filename` es opcional.  Cada opción especifica un solo archivo; si desea especificar otros archivos, repita la opción.  
  
 **\/TC** y **\/TP** son variantes globales de **\/Tc** y **\/Tp**.  Especifican al compilador que trate todos los archivos citados en la línea de comandos como archivos de código fuente de C \(**\/TC**\) o de C\+\+ \(**\/TP**\), independientemente de su ubicación en la línea de comandos con respecto a la opción.  Estas opciones globales se pueden reemplazar en un solo archivo por medio de **\/Tc** o **\/Tp**.  
  
## Sintaxis  
  
```  
/Tcfilename  
/Tpfilename  
/TC  
/TP  
```  
  
## Argumentos  
 `filename`  
 Archivo de código fuente de C o C\+\+.  
  
## Comentarios  
 De forma predeterminada, CL asume que los archivos con la extensión .c son archivos de código fuente de C y aquellos con la extensión .cpp o .cxx son archivos de código fuente de C\+\+.  
  
 Cuando se especifica **TC** o la opción de **Tc** , cualquier especificación de la opción de [\/Zc:wchar\_t \(wchar\_t es un tipo nativo\)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se omite.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Avanzadas**.  
  
4.  Modifique la propiedad **Compilar como**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.  
  
## Ejemplos  
 La línea de comandos de CL siguiente especifica que MAIN.c, TEST.prg y COLLATE.prg son archivos de código fuente de C.  CL no reconoce a PRINT.prg.  
  
```  
CL MAIN.C /TcTEST.PRG /TcCOLLATE.PRG PRINT.PRG  
```  
  
 La línea de comandos de CL siguiente especifica que TEST1.c, TEST2.cxx, TEST3.huh y TEST4.o se compilan como archivos de C\+\+, y TEST5.z se compila como un archivo de C.  
  
```  
CL TEST1.C TEST2.CXX TEST3.HUH TEST4.O /Tc TEST5.Z /TP  
```  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)