---
title: "Advertencia del compilador (nivel 1) C4054 | Microsoft Docs"
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
  - "C4054"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4054"
ms.assetid: bdd7f6d5-f6f2-44a7-a013-39f309de7a29
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4054
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversion': del puntero de función 'type1' al puntero de datos 'type2'  
  
 Un puntero de función se convierte \(quizás incorrectamente\) en un puntero de datos. Se trata de una advertencia de nivel 1 en \/Za y una advertencia de nivel 4 en \/Ze.  
  
 El ejemplo siguiente genera la advertencia C4054:  
  
```  
// C4054.c // compile with: /W1 /Za /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```  
  
 En \/Ze, esta es una advertencia de nivel 4.  
  
```  
// C4054b.c // compile with: /W4 /c int (*pfunc)(); int* f() { return (int*)pfunc;   // C4054 }  
```