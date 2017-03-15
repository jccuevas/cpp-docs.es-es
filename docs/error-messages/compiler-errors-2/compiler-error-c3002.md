---
title: "Error del compilador C3002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3002"
ms.assetid: 2d4241a7-c8eb-4d43-a128-dca255d137bc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre1 nombre2': nombres de directiva de OpenMP múltiples  
  
 No se permite usar nombres de directiva múltiples.  
  
 El ejemplo siguiente genera la advertencia C3002:  
  
```  
// C3002.c // compile with: /openmp int main() { #pragma omp parallel single   // C3002 }  
```