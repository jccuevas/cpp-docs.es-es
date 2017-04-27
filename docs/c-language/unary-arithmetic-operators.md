---
title: "Operadores aritméticos unarios | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 875fd5c87583f93a647cf51907d897603f923e7e
ms.lasthandoff: 04/01/2017

---
# <a name="unary-arithmetic-operators"></a>Operadores aritméticos unarios
Los operadores de C unario más, negación aritmética, complemento y negación lógica se analizan en la lista siguiente:  
  
|Operador|Descripción|  
|--------------|-----------------|  
|**+**|El operador unario más que precede a una expresión entre paréntesis fuerza la agrupación de las operaciones incluidas. Se utiliza con expresiones que implican más de un operador binario asociativo o conmutativo. El operando debe tener tipo aritmético. El resultado es el valor del operando. Un operando entero experimenta una promoción de entero. El tipo del resultado es el tipo del operando promovido.|  
|**-**|El operador negación aritmética genera el negativo (complemento de dos) de su operando. El operando debe ser un valor entero o flotante. Este operador realiza las conversiones aritméticas habituales.|  
|`~`|El operador complemento bit a bit (o NOT bit a bit) genera el complemento bit a bit de su operando. El operando debe ser de tipo entero. Este operador realiza las conversiones aritméticas habituales; el resultado tiene el tipo del operando después de la conversión.|  
|**!**|El operador negación lógica (NOT lógico) genera el valor 0 si su operando es true (distinto de cero) y el valor 1 si su operando es false (0). El resultado tiene el tipo `int`. El operando debe ser un valor entero, flotante o de puntero.|  
  
 Las operaciones aritméticas unarias en punteros no son válidas.  
  
## <a name="examples"></a>Ejemplos  
 En los ejemplos siguientes se muestran los operadores aritméticos unarios:  
  
```  
short x = 987;  
    x = -x;  
```  
  
 En el ejemplo anterior, el nuevo valor de `x` es el negativo de 987, o -987.  
  
```  
unsigned short y = 0xAAAA;  
    y = ~y;  
```  
  
 En este ejemplo, el nuevo valor asignado a `y` es el complemento de uno del valor sin signo 0xAAAA, o 0x5555.  
  
```  
if( !(x < y) )  
```  
  
 Si `x` es mayor o igual que `y`, el resultado de la expresión es 1 (true). Si `x` es menor que `y`, el resultado es 0 (false).  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)
