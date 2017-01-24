---
title: "Efectos secundarios | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "evaluación de expresiones, efectos secundarios"
  - "efectos secundarios de la evaluación de expresiones"
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Efectos secundarios
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El orden de evaluación de expresiones está definido por la implementación concreta, excepto cuando el lenguaje garantiza un orden concreto de evaluación \(de acuerdo con [Prioridad y orden de evaluación](../c-language/precedence-and-order-of-evaluation.md)\).  Por ejemplo, en las siguientes llamadas de función se producen efectos secundarios:  
  
```  
add( i + 1, i = j + 2 );  
myproc( getc(), getc() );  
```  
  
 Los argumentos de una llamada de función se pueden evaluar en cualquier orden.  Puede que la expresión `i + 1` se evalúe antes que `i = j + 2` o que `i = j + 2` se evalúe antes que `i + 1`.  En función de la elección, el resultado es diferente.  De igual manera, no es posible garantizar qué caracteres se pasan realmente a `myproc`.  Dado que las operaciones de incremento y decremento unario implican asignaciones, tales operaciones pueden producir efectos secundarios, tal y como se muestra en el ejemplo siguiente:  
  
```  
x[i] = i++;  
```  
  
 En este ejemplo, el valor de `x` que se modifica es imprevisible.  El valor del subíndice podría ser el valor nuevo o antiguo de `i`.  El resultado puede variar según los distintos compiladores o los diferentes niveles de optimización.  
  
 Dado que C no define el orden de evaluación de efectos secundarios, los dos métodos de evaluación descritos anteriormente son correctos y se puede implementar cualquiera de ellos.  Para asegurarse de que el código sea portátil y claro, evite las instrucciones que dependan de un orden de evaluación concreto para los efectos secundarios.  
  
## Vea también  
 [Evaluación de expresiones](../c-language/expression-evaluation-c.md)