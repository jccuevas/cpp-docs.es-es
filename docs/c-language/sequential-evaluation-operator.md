---
title: Operador de evaluación secuencial | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0cee62bdf19e6ba3196e0336cb29a7c7606775b5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808295"
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