---
title: "/O (Opciones) (Optimizar c&#243;digo) | Microsoft Docs"
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
  - "VC.Project.VCCLCompilerTool.Optimization"
  - "/o"
  - "VC.Project.VCCLWCECompilerTool.Optimization"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cl.exe (compilador), rendimiento"
  - "rendimiento, cle.exe (compilador)"
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /O (Opciones) (Optimizar c&#243;digo)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las opciones **\/O** controlan diversas optimizaciones que facilitan la creación de código para alcanzar la máxima velocidad o reducir el tamaño al mínimo.  
  
-   [\/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md) optimiza el código para reducir el tamaño al mínimo.  
  
-   [\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md) optimiza el código para obtener la máxima velocidad.  
  
-   [\/Ob](../../build/reference/ob-inline-function-expansion.md) controla la expansión de funciones alineadas.  
  
-   [\/Od](../../build/reference/od-disable-debug.md) deshabilita la optimización, lo que acelera la compilación y simplifica la depuración.  
  
-   [\/Og](../../build/reference/og-global-optimizations.md) habilita las optimizaciones globales.  
  
-   [\/Oi](../../build/reference/oi-generate-intrinsic-functions.md) genera funciones intrínsecas para las llamadas de función apropiadas.  
  
-   [\/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) indica al compilador que dé prioridad a las optimizaciones de tamaño sobre las de velocidad.  
  
-   [\/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) \(valor predeterminado\) indica al compilador que dé prioridad a las optimizaciones de velocidad sobre las de tamaño.  
  
-   [\/Ox](../../build/reference/ox-full-optimization.md) selecciona la optimización completa.  
  
-   [\/Oy](../../build/reference/oy-frame-pointer-omission.md) suprime la creación de punteros de marco en la pila de llamadas para acelerar las llamadas a las funciones.  
  
## Comentarios  
 También puede combinar varias opciones de **\/O** en una sola instrucción option.  Por ejemplo, `/Odi` es igual que `/Od /Oi`.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)