---
title: "Error del compilador C3485 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3485"
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una definición de lambda no puede tener ningún calificador cv  
  
 No puede usar un calificador `const` o `volatile` como parte de la definición de una expresión lambda.  
  
### Para corregir este error  
  
-   Quite el calificador `const` o `volatile` de la definición de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3485 porque usa el calificador `const` como parte de la definición de una expresión lambda:  
  
```  
// C3485.cpp int main() { auto x = []() const mutable {}; // C3485 }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)