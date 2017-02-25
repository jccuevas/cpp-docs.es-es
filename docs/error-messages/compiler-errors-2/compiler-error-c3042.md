---
title: "Error del compilador C3042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3042"
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las cláusulas 'copyprivate' y 'nowait' no pueden aparecer juntas en la directiva 'directive' de OpenMP  
  
 Las cláusulas [copyprivate](../../parallel/openmp/reference/copyprivate.md) y [nowait](../../parallel/openmp/reference/nowait.md) son mutuamente excluyentes en la directiva especificada. Para corregir este error, quite una de las cláusulas `copyprivate` o `nowait`, o bien ambas.  
  
 El ejemplo siguiente genera la advertencia C3042:  
  
```  
// C3042.cpp // compile with: /openmp /c #include <stdio.h> #include "omp.h" double d; int main() { #pragma omp parallel private(d) { #pragma omp single copyprivate(d) nowait   // C3042 { } } }  
```