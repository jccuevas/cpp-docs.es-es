---
title: "/CGTHREADS (Subprocesos compilador) | Microsoft Docs"
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
  - "/CGTHREADS (opción del vinculador)"
  - "CGTHREADS (opción del vinculador)"
  - "-CGTHREADS (opción del vinculador)"
ms.assetid: 4b52cfdb-3702-470b-9580-fabeb1417488
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# /CGTHREADS (Subprocesos compilador)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el número de subprocesos cl.exe que se deben usar para la optimización y la generación de código cuando se especifica la generación de código en tiempo de vínculo.  
  
## Sintaxis  
  
```  
/CGTHREADS:[1-8]  
```  
  
## Argumentos  
 número  
 El número máximo de subprocesos que debe usar cl.exe, en un intervalo de 1 a 8.  
  
## Comentarios  
 La opción **\/CGTHREADS** especifica el número máximo de subprocesos que usará cl.exe en paralelo para las fases de optimización y generación de código de la compilación cuando se especifique la generación de código en tiempo de vínculo \([\/LTCG](../../build/reference/ltcg-link-time-code-generation.md)\).  De forma predeterminada, cl.exe utiliza cuatro subprocesos, como si se especificara **\/CGTHREADS:4**.  Si hay más núcleos de procesador disponibles, al aumentar el valor `number`, se pueden mejorar los tiempos de compilación.  
  
 Se pueden especificar varios niveles de paralelismo para una compilación.  El modificador de msbuild.exe **\/maxcpucount** especifica el número de procesos de MSBuild que se pueden ejecutar en paralelo.  La marca del compilador [\/MP \(Compilar con varios procesos\)](../../build/reference/mp-build-with-multiple-processes.md) especifica el número de procesos de cl.exe que compilan simultáneamente los archivos de origen.  La opción del compilador [\/cgthreads](../../build/reference/cgthreads-code-generation-threads.md) especifica el número de subprocesos utilizados por cada proceso de cl.exe.  Dado que el procesador no puede ejecutar al mismo tiempo más subprocesos que núcleos de procesador hay, no resulta útil especificar valores mayores en todas estas opciones a la vez, y puede ser contraproducente.  Para más información sobre cómo compilar proyectos en paralelo, consulte [Compilar varios proyectos en paralelo](../Topic/Building%20Multiple%20Projects%20in%20Parallel%20with%20MSBuild.md).  
  
### Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Elija la carpeta **Propiedades de configuración**, **Vinculador**.  
  
3.  Seleccione la página de propiedades **Línea de comandos**.  
  
4.  Modifique la propiedad **Opciones adicionales** para incluir **\/CGTHREADS:**`number`, donde `number` es un valor del 1 al 8, y elija **Aceptar**.  
  
### Para establecer esta opción del vinculador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)