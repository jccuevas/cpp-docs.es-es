---
title: Compilador advertencia (nivel 2) C4146 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4146
dev_langs:
- C++
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41d21f2be76e67c58599e214df764316dc845e59
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044631"
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