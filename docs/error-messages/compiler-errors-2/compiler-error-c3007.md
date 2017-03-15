---
title: "Error del compilador C3007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3007"
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'arg': la cláusula de la directiva 'directiva' de OpenMP no toma un argumento.  
  
 Una directiva de OpenMP tenía un argumento, pero la directiva no toma un argumento.  
  
 El ejemplo siguiente genera la advertencia C3007:  
  
```  
// C3007.c // compile with: /openmp int main() { #pragma omp parallel for ordered(2)   // C3007 }  
```