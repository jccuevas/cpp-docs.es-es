---
title: "Error del compilador C3052 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3052"
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la variable no aparece en la cláusula de uso compartido de datos bajo una cláusula default\(none\)  
  
 Si se usa [default\(none\)](../../parallel/openmp/reference/default-openmp.md), cualquier variable usada en el bloque estructurado se debe especificar explícitamente como [shared](../../parallel/openmp/reference/shared-openmp.md) o [private](../../parallel/openmp/reference/private-openmp.md).  
  
 El ejemplo siguiente genera la advertencia C3052:  
  
```  
// C3052.cpp // compile with: /openmp /c int main() { int n1 = 1; #pragma omp parallel default(none) // shared(n1) private(n1) { n1 = 0;   // C3052 use either a shared or private clause } }  
```