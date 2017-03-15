---
title: "Error del compilador C3026 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3026"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3026"
ms.assetid: 3297060e-cc5b-4600-a2db-09bfc4ffa21f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3026
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clause': la expresión constante debe ser positiva  
  
 Se pasó un valor entero a una cláusula, pero el valor no era un número positivo. El número debe ser positivo.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3026:  
  
```  
// C3026.cpp // compile with: /openmp /link vcomps.lib #include <stdio.h> #include "omp.h" int main() { int i; const int i1 = 0; #pragma omp parallel for num_threads(i1)   // C3026 for (i = 1; i <= 2; ++i) printf_s("Hello World - thread %d - iteration %d\n", omp_get_thread_num(), i); #pragma omp parallel for num_threads(i1 + 1)   // OK for (i = 1; i <= 2; ++i) printf_s("Hello World - thread %d - iteration %d\n", omp_get_thread_num(), i); }  
```