---
title: "Error del compilador C3057 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3057"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3057"
ms.assetid: b0b2ba88-9c74-4bec-bf60-8fc72eade34c
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3057
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo': la inicialización dinámica de los símbolos 'threadprivate' no se admite actualmente.  
  
 El valor inicializado de un símbolo usado en una cláusula [threadprivate](../../parallel/openmp/reference/threadprivate.md) debe conocerse en tiempo de compilación.  
  
 El ejemplo siguiente genera la advertencia C3057:  
  
```  
// C3057.cpp // compile with: /openmp /c extern int f(); int x, y = f(); int a, b; #pragma omp threadprivate(x, y)   // C3057 #pragma omp threadprivate(a, b) int main() { // Delete the following 4 lines to resolve. #pragma omp parallel copyin(x, y) { x = y; } #pragma omp parallel copyin(a, b) { a = b; } }  
```  
  
 El ejemplo siguiente genera la advertencia C3057:  
  
```  
// C3057b.cpp // compile with: /openmp /c extern int Initialize(); int main() { #pragma omp parallel { static int var = Initialize(); #pragma omp threadprivate(var)   // C3057 } // OK #pragma omp parallel { static int var2; static bool initialized2; #pragma omp threadprivate(var2, initialized2) if (!initialized2) { var2 = Initialize(); initialized2 = true; } } }  
```