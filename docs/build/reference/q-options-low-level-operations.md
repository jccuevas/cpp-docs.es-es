---
title: "/Q (Opciones) (Operaciones de bajo nivel) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/q"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Q (opción del compilador) [C++]"
  - "-Q (opción del compilador) [C++]"
  - "/Q (opción del compilador) [C++]"
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# /Q (Opciones) (Operaciones de bajo nivel)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede usar las opciones del compilador **\/Q** para realizar las siguientes operaciones de compilador de bajo nivel:  
  
-   [\/Qfast\_transcendentals \(Force Fast Transcendentals\)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md): genera funciones transcendentales rápidas.  
  
-   [\/QIfist \(Suprimir \_ftol\)](../../build/reference/qifist-suppress-ftol.md): suprime `_ftol` cuando se requiere la conversión de un tipo de punto flotante a un tipo entero \(solo x86\).  
  
-   [\/Qimprecise\_fwaits \(Quitar comandos fwait en los bloques Try\)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md): quita los comandos `fwait` del interior de los bloques `try`.  
  
-   [\/Qpar \(Paralelizador automático\)](../../build/reference/qpar-auto-parallelizer.md): habilita la paralelización automática de los bucles marcados con la directiva [\#pragma loop\(\)](../../preprocessor/loop.md).  
  
-   [\/Qpar\-report \(Nivel de información de paralelizador automático\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): habilita los niveles de informe para la paralelización automática.  
  
-   [\/Qsafe\_fp\_loads](../../build/reference/qsafe-fp-loads.md): suprime las optimizaciones para las cargas de Registro de punto flotante y para los movimientos entre la memoria y los registros MMX.  
  
-   [\/Qvec\-report \(Nivel de información de vectorizador automático\)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): habilita los niveles de informe para la vectorización automática.  
  
## Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)