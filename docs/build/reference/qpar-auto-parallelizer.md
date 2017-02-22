---
title: "/Qpar (Paralelizador autom&#225;tico) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.EnableParallelCodeGeneration"
dev_langs: 
  - "C++"
ms.assetid: 33ecf49d-c0d5-4f34-bce3-84ff03f38918
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /Qpar (Paralelizador autom&#225;tico)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Permite a la característica de [Auto\-Parallelizer](../../parallel/auto-parallelization-and-auto-vectorization.md) de compilador automáticamente para paralelizar bucles en el código.  
  
## Sintaxis  
  
```  
/Qpar  
```  
  
## Comentarios  
 Cuando el compilador automáticamente paraleliza bucles en código, mejora el cálculo a través de varios núcleos de procesador.  Se paraleliza el bucle sólo si el compilador determina que se permite hacerlo y que la paralelización mejoraría el rendimiento.  
  
 Las directivas de `#pragma loop()` son que ayudan al optimizador a paralelizar bucles concretos.  Para obtener más información, vea [loop](../../preprocessor/loop.md).  
  
 Para obtener información sobre cómo habilitar los mensajes de salida para el auto \- parallelizer, vea [\/Qpar\-report \(Nivel de información de paralelizador automático\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  
  
### Para establecer la opción del compilador \/Qpar en Visual Studio  
  
1.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.  
  
2.  En el cuadro de diálogo de **Páginas de propiedades** , en **C\/C\+\+**, seleccione **Línea de comandos**.  
  
3.  En el cuadro de **Opciones adicionales** , entre en `/Qpar`.  
  
### Para establecer la opción del compilador \/Qpar mediante programación  
  
-   Utilice el ejemplo de código en <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## Vea también  
 [\/Q \(Opciones\) \(Operaciones de bajo nivel\)](../../build/reference/q-options-low-level-operations.md)   
 [\/Qpar\-report \(Nivel de información de paralelizador automático\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)   
 [bucle \#pragma \(\)](../../preprocessor/loop.md)   
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/?LinkId=263662)