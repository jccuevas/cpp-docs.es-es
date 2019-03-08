---
title: Operadores aritméticos unarios
ms.date: 11/04/2016
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
ms.openlocfilehash: f64bc5107cf0df55fd445d04d557e952702deaee
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150836"
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
