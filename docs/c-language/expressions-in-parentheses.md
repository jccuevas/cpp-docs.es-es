---
title: Expresiones entre paréntesis
ms.date: 11/04/2016
helpviewer_keywords:
- parentheses
- expression evaluation, evaluation order
- expressions [C++], evaluating
- parentheses, expressions
ms.assetid: b8636147-6982-408c-9e64-29e40678ee43
ms.openlocfilehash: d0105556530161991b46c5ee25cd73f2f995063f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233753"
---
# <a name="expressions-in-parentheses"></a>Expresiones entre paréntesis

Puede agregar cualquier operando entre paréntesis sin cambiar el tipo o el valor de la expresión incluida. Por ejemplo, en la expresión:

```
( 10 + 5 ) / 5
```

Los paréntesis alrededor de `10 + 5` indican que el valor de `10 + 5` se evalúa primero y se convierte en el operando izquierdo del operador de división ( **/** ). El resultado de `( 10 + 5 ) / 5` es 3. Sin paréntesis, `10 + 5 / 5` se evaluaría como 11.

Aunque los paréntesis afectan a la manera en que los operandos se agrupan en una expresión, no se puede garantizar un orden concreto de evaluación en todos los casos. Por ejemplo, ni los paréntesis ni la agrupación de izquierda a derecha de la expresión siguiente garantiza cuál será el valor de `i` en cualquiera de las subexpresiones:

```
( i++ +1 ) * ( 2 + i )
```

El compilador es libre de evaluar los dos lados de la multiplicación en cualquier orden. Si el valor inicial de `i` es cero, la expresión completa se podría evaluar como cualquiera de estas dos instrucciones:

```
( 0 + 1 + 1 ) * ( 2 + 1 )
( 0 + 1 + 1 ) * ( 2 + 0 )
```

Las excepciones resultantes de los efectos secundarios se tratan en [Efectos secundarios](../c-language/side-effects.md).

## <a name="see-also"></a>Vea también

[Expresiones primarias de C](../c-language/c-primary-expressions.md)
