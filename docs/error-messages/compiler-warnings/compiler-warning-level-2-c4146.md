---
title: Compilador advertencia (nivel 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: 8b3090f1bc3a64752ede4dab2b1e1b5cd800057d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555576"
---
# <a name="compiler-warning-level-2-c4146"></a>Compilador advertencia (nivel 2) C4146

operador unario menos aplicado a un tipo sin signo, resultado aún sin signo

Tipos sin signo pueden contener valores de solo no negativo, por lo que el operador unario menos (negación) suele tener sentido cuando se aplica a un tipo sin signo. El operando y el resultado son no negativos.

En la práctica, esto se produce cuando el programador intenta expresar el valor entero mínimo, que está entre -2147483648. Este valor no se puede escribir como -2147483648 porque la expresión se procesa en dos fases:

1. Se evalúa el número 2147483648. Dado que es mayor que el valor entero máximo de 2147483647, no es el tipo de 2147483648 [int](../../c-language/integer-types.md), pero `unsigned int`.

1. Unaria se aplica al valor, con un resultado sin signo, que también resulta ser 2147483648.

El tipo sin signo del resultado puede provocar un comportamiento inesperado. Si se utiliza el resultado en una comparación, una comparación unsigned podría utilizarse, por ejemplo, cuando el otro operando es un `int`. Esto explica por qué el programa de ejemplo siguiente imprime una sola línea.

La segunda línea esperada, `1 is greater than the most negative int`, no se imprime porque `((unsigned int)1) > 2147483648` es false.

Puede evitar la advertencia C4146 usando INT_MIN de limits.h, que tiene el tipo **firmado int**.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4146:

```
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