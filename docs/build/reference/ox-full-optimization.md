---
title: "/Ox (Optimizaci&#243;n completa) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.ToolOptimization"
  - "/ox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Ox (opción del compilador) [C++]"
  - "código rápido"
  - "optimización completa"
  - "Ox (opción del compilador) [C++]"
  - "-Ox (opción del compilador) [C++]"
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Ox (Optimizaci&#243;n completa)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La opción del compilador **\/Ox** genera código que da prioridad a la velocidad de ejecución sobre el menor tamaño.  
  
## Sintaxis  
  
```  
/Ox  
```  
  
## Comentarios  
 Especificar la opción del compilador **\/Ox** equivale al uso de las siguientes opciones:  
  
-   [\/Ob \(Expansión de funciones inline\)](../../build/reference/ob-inline-function-expansion.md), donde el parámetro de opción es 2 \(**\/Ob2**\)  
  
-   [\/Og \(optimizaciones globales\)](../../build/reference/og-global-optimizations.md)  
  
-   [\/Oi \(Generar funciones intrínsecas\)](../../build/reference/oi-generate-intrinsic-functions.md)  
  
-   [\/Ot \(Favorecer código rápido\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)  
  
-   [\/Oy \(Omisión de puntero de marco\)](../../build/reference/oy-frame-pointer-omission.md)  
  
 La opción **\/Ox** y las opciones que se muestran a continuación se excluyen mutuamente:  
  
-   [\/O1 \(Minimizar tamaño\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/O2 \(Maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)  
  
-   [\/Od \(Deshabilitar \(Depurar\)\)](../../build/reference/od-disable-debug.md)  
  
 La opción del compilador **\/Ox** también habilita la optimización del valor devuelto con nombre, que elimina el constructor y el destructor de copias de un valor devuelto basado en la pila.  Para obtener más información, vea [\/O1, \/O2 \(Minimizar tamaño, maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md).  
  
 Puede cancelar la opción del compilador **\/Ox** si especifica **\/Oxs**, que combina la opción del compilador **\/Ox** con [\/Os \(Favorecer código pequeño\)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md).  Las opciones combinadas favorecen un tamaño de código más reducido.  
  
 En general, especifique [\/O2 \(Maximizar velocidad\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en lugar de **\/Ox**, y [\/O1 \(Minimizar tamaño\)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) en lugar de **\/Oxs**.  
  
### Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener información detallada, vea [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Haga clic en la carpeta **C\/C\+\+**.  
  
3.  Haga clic en la página de propiedades **Optimización**.  
  
4.  Modifique la propiedad **Optimización**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.  
  
## Vea también  
 [\/O \(Opciones\) \(Optimizar código\)](../../build/reference/o-options-optimize-code.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)