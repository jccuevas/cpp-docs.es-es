---
title: "No se puede inferir un tipo com&#250;n para los operandos segundo y tercero del operador &#39;If&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc33106"
  - "bc33106"
helpviewer_keywords: 
  - "BC33106"
ms.assetid: 793eed88-a9f9-43e3-b657-c16795ecbbcc
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede inferir un tipo com&#250;n para los operandos segundo y tercero del operador &#39;If&#39;.
No se puede inferir un tipo común para los operandos segundo y tercero del operador 'If'. Uno debe tener una conversión de ampliación al otro.  
  
 Cuando se llama al operador `If` con tres argumentos, debe haber una conversión de ampliación entre los argumentos segundo y terceros. Por ejemplo, como no hay una conversión de ampliación en ambas direcciones entre `Integer` y `String`, el código siguiente provoca este error.  
  
```vb#  
Dim divisor = 3  
' Not valid.  
' Console.WriteLine(If(divisor <> 0, number \ divisor, "Division by zero"))  
```  
  
 **Identificador de error:** BC33106  
  
### Para corregir este error  
  
-   Proporcione una conversión explícita para uno de los operandos, si es posible en el código.  
  
-   Use una construcción de condición diferente, como una instrucción `If...Then...Else`.  
  
## Vea también  
 [If \(operador\)](../Topic/If%20Operator%20\(Visual%20Basic\).md)   
 [If...Then...Else \(Instrucción\)](../Topic/If...Then...Else%20Statement%20\(Visual%20Basic\).md)   
 [Conversiones de ampliación y de restricción](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)