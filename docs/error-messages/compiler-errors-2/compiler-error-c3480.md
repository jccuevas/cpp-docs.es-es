---
title: "Error del compilador C3480 | Microsoft Docs"
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
  - "C3480"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3480"
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3480
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': una variable de captura lambda debe pertenecer al ámbito de una función de inclusión  
  
 La variable de captura lambda no pertenece al ámbito de una función de inclusión.  
  
### Para corregir este error  
  
-   Quite la variable de la lista de captura de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3480 porque la variable `global` no pertenece al ámbito de una función de inclusión:  
  
```  
// C3480a.cpp int global = 0; int main() { [&global] { global = 5; }(); // C3480 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se resuelve C3480 quitando la variable `global` de la lista de captura de la expresión lambda:  
  
```  
// C3480b.cpp int global = 0; int main() { [] { global = 5; }(); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)