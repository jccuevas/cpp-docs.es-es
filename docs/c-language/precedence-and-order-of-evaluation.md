---
title: Precedencia y orden de evaluación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- associativity of operators [C++]
- precedence [C++], operators
- data binding [C++], operator precedence
- operators [C++], precedence
ms.assetid: 201f7864-0c51-4c55-9d6f-39c5d013bcb0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84c3ec69c936605729f6813f28450ee1194951c7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392190"
---
# <a name="precedence-and-order-of-evaluation"></a>Precedencia y orden de evaluación
La prioridad y asociatividad de los operadores de C afectan a la agrupación y evaluación de los operandos en las expresiones. La prioridad de un operador solo es significativa si otros operadores con una prioridad mayor o menor están presentes. Las expresiones con operadores de mayor prioridad se evalúan primero. La prioridad también se puede describir con la palabra “enlace”. Se dice que los operadores con mayor prioridad tienen un enlace más estricto.  
  
 En la tabla siguiente se resume la prioridad y asociatividad (el orden en que se evalúan los operandos) de los operadores de C, que se enumeran por orden de prioridad, de mayor a menor. Cuando varios operadores aparecen juntos, tienen la misma prioridad y se evalúan según su asociatividad. Los operadores de la tabla se describen en las secciones a partir de [Operadores de postfijo](../c-language/postfix-operators.md). En el resto de esta sección se proporciona información general sobre la prioridad y asociatividad.  
  
## <a name="precedence-and-associativity-of-c-operators"></a>Prioridad y asociatividad de los operadores de C  
  
|Símbolo <sup>1</sup>|Tipo de operación|asociatividad|  
|-------------|-----------------------|-------------------|  
|**\[ ] ( ) . ->**<br /><br />**++** **--** (postfijo)|Expresión|De izquierda a derecha|  
**sizeof & \* + - ~ !**<br /><br />**++ --** (prefijo)|Unario|De derecha a izquierda|  
|*typecasts*|Unario|De derecha a izquierda|  
|**\* / %**|Multiplicativo|De izquierda a derecha|  
|**+ -**|Aditivo|De izquierda a derecha|  
|**\<\< >>**|Desplazamiento bit a bit|De izquierda a derecha|  
|**\< > \<= >=**|Relacional|De izquierda a derecha|  
|**== !=**|Igualdad|De izquierda a derecha|  
|**&**|AND bit a bit|De izquierda a derecha|  
|**^**|OR exclusivo bit a bit|De izquierda a derecha|  
|**&#124;**|OR inclusivo bit a bit|De izquierda a derecha|  
|**&&**|AND lógico|De izquierda a derecha|  
|**&#124;&#124;**|OR lógico|De izquierda a derecha|  
|**? :**|Expresión condicional|De derecha a izquierda|  
|**= \*= /= %=**<br /><br /> **+= -= \<\<= >>= &=**<br /><br /> **^= &#124;=**|Asignación simple y compuesta <sup>2</sup>|De derecha a izquierda|  
|**,**|Evaluación secuencial|De izquierda a derecha|  
  
 1. Los operadores se enumeran por prioridad, de mayor a menor. Si aparecen varios operadores en la misma línea o en un grupo, tienen la misma prioridad.  
  
 2. Todos los operadores de asignación simples y compuestos tienen la misma prioridad.  
  
 Una expresión puede contener varios operadores con la misma prioridad. Cuando varios operadores de este tipo aparecen en el mismo nivel en una expresión, la evaluación continúa según la asociatividad del operador, de derecha a izquierda y de izquierda a derecha. La dirección de evaluación no afecta a los resultados de las expresiones que incluyen más de un operador de multiplicación (**\***), adición (**+**) o binario bit a bit (**& &#124; ^**) en el mismo nivel. El orden de las operaciones no lo define el lenguaje. El compilador es libre de evaluar estas expresiones en cualquier orden, si puede garantizar un resultado coherente.  
  
 Solo los operadores de evaluación secuencial (**,**), AND lógico (**&&**), OR lógico (`||`), expresión condicional (**? :**) y llamada a función constituyen puntos de secuencia y, por lo tanto, garantizan un orden de evaluación concreto para sus operandos. El operador de llamada a función es el conjunto de paréntesis que siguen al identificador de función. Está garantizado que el operador de evaluación secuencial (**,**) evalúa sus operandos de izquierda a derecha. (Observe que el operador de coma en una llamada a función no es igual que el operador de evaluación secuencial y no proporciona esta garantía). Para obtener más información, vea [Puntos de secuencia](../c-language/c-sequence-points.md).  
  
 Los operadores lógicos también garantizan la evaluación de sus operandos de izquierda a derecha. Sin embargo, evalúan el número más pequeño de operandos necesarios para determinar el resultado de la expresión. Esto se denomina evaluación de "cortocircuito". Por tanto, es posible que algunos operandos de la expresión no se evalúen. Por ejemplo, en la expresión  
  
`x && y++`  
  
 se evalúa el segundo operando, `y++`, solo si `x` es true (distinto de cero). Así, `y` no se incrementa si `x` es false (0).  
  
## <a name="examples"></a>Ejemplos
  
 La lista siguiente muestra cómo el compilador enlaza varias expresiones de ejemplo automáticamente:  

|Expresión|Enlace automático|  
|----------------|-----------------------|  
|a & b &#124;&#124; c|(a & b) &#124;&#124; c|  
|a = b &#124;&#124; c|a = (b &#124;&#124; c)|  
|q && r &#124;&#124; s--|(q && r) &#124;&#124; s--|  

 En la primera expresión, el operador AND bit a bit (`&`) tiene prioridad sobre el operador OR lógico (`||`), por lo que `a & b` forma el primer operando de la operación OR lógica.  
  
 En la segunda expresión, el operador OR lógico (`||`) tiene una mayor prioridad que el operador de asignación simple (`=`), por lo que `b || c` se agrupa como el operando derecho de la asignación. Observe que el valor asignado a `a` es 0 o 1.  
  
 La tercera expresión muestra una expresión correctamente formada que puede generar un resultado inesperado. El operador AND lógico (`&&`) tiene una mayor prioridad que el operador OR lógico (`||`), por lo que `q && r` se agrupa como operando. Puesto que los operadores lógicos garantizan la evaluación de los operandos de izquierda a derecha, `q && r` se evalúa antes de `s--`. En cambio, si `q && r` se evalúa como un valor distinto de cero, `s--` no se evalúa y `s` no se reduce. Si la no reducción de `s` puede provocar un problema en el programa, `s--` debe aparecer como el primer operando de la expresión, o bien `s` se debería reducir en una operación independiente.  
  
 La siguiente expresión no es válida y muestra un mensaje de diagnóstico en tiempo de compilación:  
  
|Expresión no válida|Agrupación predeterminada|  
|------------------------|----------------------|  
|p == 0 ? p += 1: p += 2|( p == 0 ? p += 1 : p ) += 2|  
  
 En esta expresión, el operador de igualdad (`==`) tiene una prioridad superior, por lo que `p == 0` se agrupa como operando. El operador de expresión condicional (`? :`) tiene la siguiente prioridad más alta. Su primer operando es `p == 0` y su segundo operando es `p += 1`. Sin embargo, el último operando del operador de expresión condicional se considera `p` en lugar de `p += 2`, puesto que esta instancia de `p` se enlaza de una forma más directa con el operador de expresión condicional que con el operador de asignación compuesta. Se produce un error de sintaxis, porque `+= 2` no tiene un operando izquierdo. Debe utilizar paréntesis para evitar errores de esta clase y que el código sea más legible. Por ejemplo, podría utilizar paréntesis, como se muestra a continuación, para corregir y aclarar el ejemplo anterior:  
  
`( p == 0 ) ? ( p += 1 ) : ( p += 2 )`  
  
## <a name="see-also"></a>Vea también  
 [Operadores de C](../c-language/c-operators.md)
