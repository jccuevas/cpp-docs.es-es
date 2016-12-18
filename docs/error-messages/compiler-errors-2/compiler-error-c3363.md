---
title: "Error del compilador C3363 | Microsoft Docs"
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
  - "C3363"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3363"
ms.assetid: 41aa922f-608e-4f7a-ba66-451fc1161935
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3363
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': 'typeid' solamente se puede asignar a un tipo.  
  
 El operador [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) se usó incorrectamente.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3363.  
  
```  
// C3363.cpp // compile with: /clr int main() { System::typeid;   // C3363 }  
```