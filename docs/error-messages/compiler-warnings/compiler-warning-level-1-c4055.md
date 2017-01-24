---
title: "Advertencia del compilador (nivel 1) C4055 | Microsoft Docs"
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
  - "C4055"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4055"
ms.assetid: f04b13ca-88a7-4f2b-8065-42e73e5ac353
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4055
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'conversion': del puntero de datos 'type1' al puntero de función 'type2'  
  
 Un puntero de datos se convierte \(quizás incorrectamente\) en un puntero de función. Se trata de una advertencia de nivel 1 en \/Za y una advertencia de nivel 4 en \/Ze.  
  
 El ejemplo siguiente genera la advertencia C4055:  
  
```  
// C4055.c // compile with: /Za /W1 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```  
  
 En \/Ze, esta es una advertencia de nivel 4.  
  
```  
// C4055b.c // compile with: /W4 /c typedef int (*PFUNC)(); int *pi; PFUNC f() { return (PFUNC)pi;   // C4055 }  
```