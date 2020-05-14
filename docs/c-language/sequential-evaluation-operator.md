---
title: Operador de evaluación secuencial
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: 2cbffc51fb7113ae442dbfcd1db01bbf27a67746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158526"
---
# <a name="sequential-evaluation-operator"></a>Operador de evaluación secuencial

El operador de evaluación-secuencial, denominado también "operador de coma", evalúa los dos operandos secuencialmente de izquierda a derecha.

## <a name="syntax"></a>Sintaxis

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

El operando izquierdo del operador de evaluación-secuencial se evalúa como una expresión `void`. El resultado de la operación tiene el mismo valor y tipo que el operando derecho. Cada operando puede ser de cualquier tipo. El operador de evaluación-secuencial no realiza conversiones de tipos entre sus operandos y no produce un valor L. Hay un punto de secuencia después del primer operando, lo que significa que todos los efectos secundarios de la evaluación del operando izquierdo se aplican antes de que se inicie la evaluación del operando derecho. Vea [Puntos de secuencia de C](../c-language/c-sequence-points.md) para obtener más información.

El operador de evaluación-secuencial se utiliza normalmente para evaluar dos o más expresiones en contextos donde solo se permite una expresión.

Se pueden usar comas como separadores en algunos contextos. Sin embargo, debe tener cuidado de no confundir el uso de la coma como separador con su uso como operador; los dos usos son completamente diferentes.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra el operador de evaluación-secuencial:

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

En este ejemplo, cada operando de la tercera expresión de la instrucción **for** se evalúa de manera independiente. El operando izquierdo `i += i` se evalúa primero y, después, se evalúa el operando derecho, `j--`.

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

En la llamada de función a `func_one`, se pasan tres argumentos separados por comas: `x`, `y + 2` y `z`. En la llamada de función a `func_two`, los paréntesis hacen que el compilador interprete la primera coma como el operador de evaluación secuencial. Esta llamada a función pasa dos argumentos a `func_two`. El primer argumento es el resultado de la operación de evaluación secuencial `(x--, y + 2)`, que tiene el valor y tipo de la expresión `y + 2`; el segundo argumento es `z`.

## <a name="see-also"></a>Vea también

[Operador de coma: ,](../cpp/comma-operator.md)
