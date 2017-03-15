---
title: "/cgthreads (Subprocesos de generaci&#243;n de c&#243;digo) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/cgthreads"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/cgthreads (opción del compilador) (C++)"
  - "cgthreads"
  - "cgthreads (opción del compilador) (C++)"
  - "-cgthreads (opción del compilador) (C++)"
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /cgthreads (Subprocesos de generaci&#243;n de c&#243;digo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el número de subprocesos de cl.exe que se deben usar para la optimización y la generación de código.  
  
## Sintaxis  
  
```  
/cgthreads[1-8]  
```  
  
## Argumentos  
 número  
 El número máximo de subprocesos que debe usar cl.exe, en un intervalo de 1 a 8.  
  
## Comentarios  
 La opción **\/cgthreads** especifica el número máximo de subprocesos que usará cl.exe en paralelo para las fases de optimización y generación de código de la compilación.  No puede haber ningún espacio entre **\/cgthreads** y el argumento `number`.  De forma predeterminada, cl.exe utiliza cuatro subprocesos, como si se especificara **\/cgthreads4**.  Si hay más núcleos de procesador disponibles, al aumentar el valor `number`, se pueden mejorar los tiempos de compilación.  Esta opción es especialmente útil cuando se combina con [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md).  
  
 Se pueden especificar varios niveles de paralelismo para una compilación.  El modificador de msbuild.exe **\/maxcpucount** especifica el número de procesos de MSBuild que se pueden ejecutar en paralelo.  La marca del compilador [\/MP \(Compilar con varios procesos\)](../../build/reference/mp-build-with-multiple-processes.md) especifica el número de procesos de cl.exe que compilan simultáneamente los archivos de origen.  La opción **\/cgthreads** especifica el número de subprocesos utilizados por cada proceso de cl.exe.  Dado que el procesador no puede ejecutar al mismo tiempo más subprocesos que núcleos de procesador hay, no resulta útil especificar valores mayores en todas estas opciones a la vez, y puede ser contraproducente.  Para más información sobre cómo compilar proyectos en paralelo, consulte [Compilar varios proyectos en paralelo](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md).  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Elija la carpeta **Propiedades de configuración**, **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir **\/cgthreads**`N`, donde `N` es un valor del 1 al 8, y elija **Aceptar**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)