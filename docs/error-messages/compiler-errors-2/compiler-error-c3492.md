---
title: "Error del compilador C3492 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3492"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3492"
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3492
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': no se puede capturar un miembro de una unión anónima.  
  
 No se puede capturar un miembro de una unión sin nombre.  
  
### Para corregir este error  
  
-   Asigne un nombre a la unión y pase la estructura de unión completa a la lista de captura de la expresión lambda.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3492 porque se captura en un miembro de una unión anónima:  
  
```  
// C3492a.cpp int main() { union { char ch; int x; }; ch = 'y'; [&x](char ch) { x = ch; }(ch); // C3492 }  
```  
  
## Ejemplo  
 En el ejemplo siguiente se resuelve C3492 dando un nombre a la unión y pasando la estructura de unión completa a la lista de captura de la expresión lambda:  
  
```  
// C3492b.cpp int main() { union { char ch; int x; } u; u.ch = 'y'; [&u](char ch) { u.x = ch; }(u.ch); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)