---
title: ADVERTENCIA del compilador (nivel 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: d595befc80d954c8fb84f83ad6c4e0cb5f4fcf26
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052168"
---
# <a name="compiler-warning-level-2-c4146"></a>ADVERTENCIA del compilador (nivel 2) C4146

operador unario menos aplicado a tipo sin signo, resultado sin signo

Los tipos sin signo solo pueden contener valores no negativos, por lo que el signo menos (negación) unario normalmente no tiene sentido cuando se aplica a un tipo sin signo. El operando y el resultado no son negativos.

En la práctica, esto ocurre cuando el programador está intentando expresar el valor entero mínimo, que es-2147483648. Este valor no se puede escribir como-2147483648 porque la expresión se procesa en dos fases:

1. Se evalúa el número 2147483648. Dado que es mayor que el valor entero máximo de 2147483647, el tipo de 2147483648 no es [int](../../c-language/integer-types.md), pero `unsigned int`.

1. Unario menos se aplica al valor, con un resultado sin signo, que también es 2147483648.

El tipo sin signo del resultado puede producir un comportamiento inesperado. Si el resultado se usa en una comparación, se podría usar una comparación sin firmar, por ejemplo, cuando el otro operando es un `int`. Esto explica por qué el siguiente programa de ejemplo imprime solo una línea.

La segunda línea esperada, `1 is greater than the most negative int`, no se imprime porque `((unsigned int)1) > 2147483648` es false.

Puede evitar C4146 con INT_MIN de limits. h, que tiene el tipo **signed int**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4146:

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```