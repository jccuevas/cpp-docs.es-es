---
title: "Error del compilador C3006 | Microsoft Docs"
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
  - "C3006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3006"
ms.assetid: 449082ec-fd45-4c47-8ab3-ba6a719e4dc4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cláusula': falta un argumento esperado en la cláusula de la directiva 'directiva' de OpenMP.  
  
 Una directiva de OpenMP no tenía un argumento esperado.  
  
 El ejemplo siguiente genera la advertencia C3006:  
  
```  
// C3006.c // compile with: /openmp int main() { #pragma omp parallel shared   // C3006 // Try the following line instead: // #pragma omp parallel shared(x) {} }  
```