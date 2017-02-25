---
title: "Error del compilador C3045 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3045"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3045"
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3045
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se esperaba una instrucción compuesta después de la directiva 'sections' de OpenMP. Falta '{'.  
  
 Un bloque de código delimitado por llaves debe seguir a una directiva [sections](../../parallel/openmp/reference/sections-openmp.md).  
  
 El ejemplo siguiente genera la advertencia C3045:  
  
```  
// C3045.cpp // compile with: /openmp /c #include "omp.h" int main() { int n2 = 2, n3 = 3; #pragma omp parallel { ++n2; #pragma omp sections ++n2;   // C3045 #pragma omp sections   // OK { ++n3; } } }  
```