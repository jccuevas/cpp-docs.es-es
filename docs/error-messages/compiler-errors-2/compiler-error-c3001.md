---
title: "Error del compilador C3001 | Microsoft Docs"
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
  - "C3001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3001"
ms.assetid: d0e03478-1b44-47e5-8f5b-70415fa1f8bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'error\_text': se esperaba un nombre de directiva de OpenMP  
  
 La pragma `omp` debe ir seguida de una directiva.  
  
 El ejemplo siguiente genera la advertencia C3001:  
  
```  
// C3001.c // compile with: /openmp int main() { #pragma omp   // C3001 missing token }  
```