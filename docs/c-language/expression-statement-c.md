---
title: "Expression (Instrucci&#243;n) (C) | Microsoft Docs"
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
  - "instrucciones de expresión"
  - "instrucciones, expresión"
ms.assetid: 1085982b-dc16-4c1e-9ddd-0cd85c8fe2e3
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Expression (Instrucci&#243;n) (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se ejecuta una instrucción de expresión, la expresión se evalúa según las reglas descritas en [Expresiones y asignaciones](../c-language/expressions-and-assignments.md).  
  
## Sintaxis  
 *expression\-statement*:  
 *expression*  opt **;**  
  
 Todos los efectos secundarios de la evaluación de la expresión se completan antes de que se ejecute la instrucción siguiente.  Una instrucción de expresión vacía se conoce como instrucción nula.  Para obtener más información, vea [La instrucción Null](../c-language/null-statement-c.md).  
  
 En estos ejemplos se muestran instrucciones de expresión.  
  
```  
x = ( y + 3 );            /* x is assigned the value of y + 3  */  
x++;                      /* x is incremented                  */  
x = y = 0;                /* Both x and y are initialized to 0 */  
proc( arg1, arg2 );       /* Function call returning void      */  
y = z = ( f( x ) + 3 );   /* A function-call expression        */  
```  
  
 En la última instrucción, la expresión de llamada de función, el valor de la expresión, que incluye cualquier valor devuelto por la función, se incrementa en 3 y, a continuación, se asigna a las variables `y` y `z`.  
  
## Vea también  
 [Instrucciones](../c-language/statements-c.md)