---
title: 'Operadores unarios más y de negación: + y -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: c1d5fc926b396f1ec44b9e44e79721e2ca4a0908
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580913"
---
# <a name="unary-plus-and-negation-operators--and--"></a>Operadores unarios más y de negación: + y -

## <a name="syntax"></a>Sintaxis

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ (operador)

El resultado del operador unario más (**+**) es el valor de su operando. El operando del operador unario más debe ser de tipo aritmético.

La promoción de entero se realiza en operandos enteros. El tipo resultante es el tipo al que se promueve el operando. Por lo tanto, la expresión `+ch`, donde `ch` es de tipo **char**, da como resultado de tipo **int**; no se modifica el valor. Consulte [conversiones estándar](standard-conversions.md) para obtener más información sobre cómo se realiza la promoción.

## <a name="--operator"></a>- (operador)

El operador unario de negación (**-**) genera el negativo de su operando. El operando del operador de negación unario debe ser un tipo aritmético.

La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando. Consulte [conversiones estándar](standard-conversions.md) para obtener más información acerca de cómo se realiza la promoción.

## <a name="microsoft-specific"></a>Específicos de Microsoft

La negación unaria de cantidades sin signo se realiza restando el valor del operando de 2^n, donde n es el número de bits de un objeto del tipo sin signo especificado.

## <a name="see-also"></a>Vea también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)