---
title: "Operadores de incremento y decremento postfijos de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores de incremento, sintaxis"
  - "operadores escalares"
  - "tipos [C], escalares"
ms.assetid: 56ba218d-65f9-405f-8684-caccc0ca33aa
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Operadores de incremento y decremento postfijos de C
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operandos de los operadores de incremento y decremento de postfijo son tipos escalares que son valores L modificables.  
  
## Sintaxis  
 *postfix\-expression*:  
 *postfix\-expression*  **\+\+**  
  
 *postfix\-expression*  **––**  
  
 El resultado de la operación de incremento y decremento de postfijo es el valor del operando.  Una vez obtenido el resultado, se incrementa \(o se reduce\) el valor del operando.  En el código siguiente se muestra el operador de incremento de postfijo.  
  
```  
if( var++ > 0 )  
    *p++ = *q++;  
```  
  
 En este ejemplo, la variable `var` se compara con 0 y luego se incrementa.  Si `var` era positivo antes de que se incrementara, se ejecuta la siguiente instrucción.  En primer lugar, se asigna el valor del objeto indicado por `q` al objeto indicado por `p`.  A continuación, se incrementan `q` y `p`.  
  
## Vea también  
 [Operadores de incremento y decremento postfijos: \+\+ y \-\-](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)