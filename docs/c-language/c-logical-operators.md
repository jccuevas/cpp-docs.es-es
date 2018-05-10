---
title: Operadores lógicos de C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- logical operators, expression sequence points
- logical operators, C
- logical AND operator
- '|| operator'
- operators [C], logical
- short-circuit evaluation
- '&& operator'
- logical OR operator
ms.assetid: c0a4e766-ad56-4300-bf76-b28dc0e19b43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f92adbeab4175178be8f41a09c4455d8a581131
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="c-logical-operators"></a>Operadores lógicos de C
Los operadores lógicos realizan operaciones AND lógicas (**&&**) y OR lógicas (`||`).  
  
 **Sintaxis**  
  
 *logical-AND-expression*:  
 *inclusive-OR-expression*  
  
 *logical-AND-expression*  **&&**  *inclusive-OR-expression*  
  
 *logical-OR-expression*:  
 *logical-AND-expression*  
  
 *logical-OR-expression*  **&#124;&#124;**  *logical-AND-expression*  
  
 Los operadores lógicos no realizan las conversiones aritméticas habituales. En su lugar, evalúan cada operando para ver su equivalencia con 0. El resultado de una operación lógica es 0 o 1. El tipo del resultado es `int`.  
  
 A continuación se describen los operadores lógicos de C:  
  
|Operador|Description|  
|--------------|-----------------|  
|**&&**|El operador AND lógico genera el valor 1 si ambos operandos tienen valores distintos de cero. Si alguno de los operandos es igual a 0, el resultado es 0. Si el primer operando de una operación AND lógica es igual a 0, el segundo operando no se evalúa.|  
|`&#124;&#124;`|El operador OR lógico realiza una operación OR inclusivo en sus operandos. El resultado es 0 si ambos operandos tienen valores 0. Si cualquiera de los operandos tiene un valor distinto de cero, el resultado es 1. Si el primer operando de una operación OR lógica tiene un valor distinto de cero, el segundo operando no se evalúa.|  
  
 Los operandos de las expresiones AND y OR lógicas se evalúan de izquierda a derecha. Si el valor del primer operando es suficiente para determinar el resultado de la operación, el segundo operando no se evalúa. Esto se denomina "evaluación de cortocircuito". Hay un punto de secuencia después del primer operando. Vea [Puntos de secuencia de C](../c-language/c-sequence-points.md) para obtener más información.  
  
## <a name="examples"></a>Ejemplos  
 En los ejemplos siguientes se muestran los operadores lógicos:  
  
```  
int w, x, y, z;  
  
if ( x < y && y < z )  
    printf( "x is less than z\n" );  
```  
  
 En este ejemplo, se llama a la función `printf` para imprimir un mensaje si `x` es menor que `y` e `y` es menor que `z`. Si `x` es mayor que `y`, el segundo operando (`y < z`) no se evalúa y no se imprime nada. Tenga en cuenta que esto puede producir problemas en aquellos casos en los que el segundo operando tenga efectos secundarios en los que se confíe por algún otro motivo.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 En este ejemplo, si `x` es igual a `w`, `y` o `z`, el segundo argumento de la función `printf` se evalúa como true y se imprime el valor 1. De lo contrario, se evalúa como false y se imprime el valor 0. En cuanto una de las condiciones se evalúe como true, se interrumpe la evaluación.  
  
## <a name="see-also"></a>Vea también  
 [Operador lógico AND: &&](../cpp/logical-and-operator-amp-amp.md)   
 [Operador lógico OR: &#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)