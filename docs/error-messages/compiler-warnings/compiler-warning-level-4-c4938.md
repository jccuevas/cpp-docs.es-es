---
title: "Advertencia del compilador (nivel 4) C4938 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4938"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4938"
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4938
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la variable de reducción de punto flotante puede causar resultados incoherentes bajo \/fp:strict o \#pragma fenv\_access  
  
 No se debe usar [\/fp:strict](../../build/reference/fp-specify-floating-point-behavior.md) ni [fenv\_access](../../preprocessor/fenv-access.md) con reducciones de punto flotante de OpenMP, ya que la suma se calcula en un orden diferente. Por lo tanto, los resultados pueden diferir de los resultados sin \/openmp.  
  
 El ejemplo siguiente genera la advertencia C4938:  
  
```  
// C4938.cpp // compile with: /openmp /W4 /fp:strict /c // #pragma fenv_access(on) extern double *a; double test(int first, int last) { double sum = 0.0; #pragma omp parallel for reduction(+: sum)   // C4938 for (int i = first ; i <= last ; ++i) sum += a[i]; return sum; }  
```  
  
 Sin paralelización explícita, la suma se calcula como se indica a continuación:  
  
```  
sum = a[first] + a[first + 1] + ... + a[last];   
```  
  
 Con paralelización explícita \(y dos subprocesos\), la suma se calcula como se indica a continuación:  
  
```  
sum1 = a[first] + ... a[first + last / 2]; sum2 = a[(first + last / 2) + 1] + ... a[last]; sum = sum1 + sum2;  
```