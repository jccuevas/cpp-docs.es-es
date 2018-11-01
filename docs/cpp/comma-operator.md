---
title: 'Operador coma: ,'
ms.date: 11/04/2016
f1_keywords:
- '%2C'
helpviewer_keywords:
- comma operator
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
ms.openlocfilehash: 8c6757f402cc7422824f1b701d3d1e4ae2566074
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50609929"
---
# <a name="comma-operator-"></a>Operador coma: ,

Permite agrupar dos instrucciones donde se espera una.

## <a name="syntax"></a>Sintaxis

```
expression , expression
```

## <a name="remarks"></a>Comentarios

El operador de comas tiene asociatividad de izquierda a derecha. Dos expresiones separadas por una coma se evalúan de izquierda a derecha. El operando izquierdo se evalúa siempre, y todos los efectos secundarios se completan antes de que se evalúe el operando derecho.

Las comas se pueden utilizar como separadores en algunos contextos, como las listas de argumentos de función. No confunda el uso de la coma como separador y como operador; los dos usos son completamente diferentes.

Considere la expresión `e1, e2`. El tipo y el valor de la expresión son el tipo y el valor de *e2*; el resultado de evaluar *e1* se descarta. El resultado es un valor L si el operando derecho es un valor L.

En los contextos en los que normalmente se utiliza la coma como separador (por ejemplo, en argumentos reales para funciones o inicializadores de agregado), el operador de la coma y sus operandos deben incluirse entre paréntesis. Por ejemplo:

```cpp
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

En la llamada de función a `func_one` de la parte superior, se pasan tres argumentos separados por comas: `x`, `y + 2` y `z`. En la llamada de función a `func_two`, los paréntesis hacen que el compilador interprete la primera coma como el operador de evaluación secuencial. Esta llamada a función pasa dos argumentos a `func_two`. El primer argumento es el resultado de la operación de evaluación secuencial `(x--, y + 2)`, que tiene el valor y tipo de la expresión `y + 2`; el segundo argumento es `z`.

## <a name="example"></a>Ejemplo

```cpp
// cpp_comma_operator.cpp
#include <stdio.h>
int main () {
   int i = 10, b = 20, c= 30;
   i = b, c;
   printf("%i\n", i);

   i = (b, c);
   printf("%i\n", i);
}
```

```Output
20
30
```

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operador de evaluación secuencial](../c-language/sequential-evaluation-operator.md)