---
title: "Error del compilador C3484 | Microsoft Docs"
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
  - "C3484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3484"
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba '\-\>' antes del tipo de valor devuelto  
  
 Se debe proporcionar `->` antes del tipo de valor devuelto de una expresión lambda.  
  
### Para corregir este error  
  
-   Proporcione `->` antes del tipo de valor devuelto.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3484:  
  
```  
// C3484a.cpp int main() { return []() . int { return 42; }(); // C3484 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se resuelve el error C3484 al proporcionar `->` antes del tipo de valor devuelto de la expresión lambda:  
  
```  
// C3484b.cpp int main() { return []() -> int { return 42; }(); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)