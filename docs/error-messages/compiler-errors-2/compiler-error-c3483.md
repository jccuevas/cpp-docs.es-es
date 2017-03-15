---
title: "Error del compilador C3483 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3483"
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' ya forma parte de la lista de capturas lambda  
  
 Pasó la misma variable a la lista de capturas de una expresión lambda más de una vez.  
  
### Para corregir este error  
  
-   Quite todas las instancias adicionales de la variable de la lista de capturas.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3483 porque la variable `n` aparece más de una vez en la lista de capturas de la expresión lambda:  
  
```  
// C3483.cpp int main() { int m = 6, n = 5; [m,n,n] { return n + m; }(); // C3483 }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)