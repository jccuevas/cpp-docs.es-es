---
title: "Error del compilador C3005 | Microsoft Docs"
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
  - "C3005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3005"
ms.assetid: 30bad565-e79f-4c3f-82cb-a74bd0baab8f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'texto\_de\_error': se encontró un token inesperado en la directiva 'directiva' de OpenMP  
  
 Hay una directiva de OpenMP con formato incorrecto.  
  
 El ejemplo siguiente genera la advertencia C3005:  
  
```  
// C3005.c // compile with: /openmp int main() { #pragma omp parallel + for   // C3005 }  
```  
  
 También puede producirse el error C3005 si se coloca una llave de apertura en la misma línea que el pragma.  
  
```  
// C3005b.c // compile with: /openmp int main() { #pragma omp parallel {   // C3005 put open brace on next line lbl2:; } goto lbl2; }  
```