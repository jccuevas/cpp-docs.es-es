---
title: "Error del compilador C3499 | Microsoft Docs"
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
  - "C3499"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3499"
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3499
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una expresión lambda de la que se ha especificado que tiene un tipo de valor devuelto void no puede devolver un valor  
  
 El compilador genera este error cuando una expresión lambda que especifica `void` como el tipo de valor devuelto devuelve un valor; o cuando una expresión lambda contiene más de una instrucción y devuelve un valor, pero no especifica su tipo de valor devuelto.  
  
### Para corregir este error  
  
-   No devuelva un valor de la expresión lambda, o bien  
  
-   Facilite el tipo de valor devuelvo de la expresión lambda, o bien  
  
-   Combine las instrucciones que componen el cuerpo de la expresión lambda en una única instrucción.  
  
## Ejemplo  
 El ejemplo siguiente produce un error C3499 porque el cuerpo de una expresión lambda contiene varias instrucciones y devuelve un valor, pero la expresión lambda no especifica el tipo de valor devuelto:  
  
```  
// C3499a.cpp int main() { [](int x) { int n = x * 2; return n; } (5); // C3499 }  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra dos posibles soluciones para C3499. La primera solución facilita el tipo de valor devuelto de la expresión lambda. La segunda solución combina las instrucciones que componen el cuerpo de la expresión lambda en una única instrucción.  
  
```  
// C3499b.cpp int main() { // Possible resolution 1: // Provide the return type of the lambda expression. [](int x) -> int { int n = x * 2; return n; } (5); // Possible resolution 2: // Combine the statements that make up the body of // the lambda expression into a single statement. [](int x) { return x * 2; } (5); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)