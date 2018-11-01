---
title: Advertencia del compilador (nivel 4) C4295
ms.date: 1/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: ed31ea19f9c36a9c6fab7452a4bfc3843a151059
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472195"
---
# <a name="compiler-warning-level-4-c4295"></a>Advertencia del compilador (nivel 4) C4295

> '*matriz*': matriz es demasiado pequeña para incluir un carácter nulo de terminación

Se puede inicializar una matriz, pero el último carácter de la matriz no es null; obtener acceso a la matriz como una cadena puede producir resultados inesperados.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4295. Para corregir este problema, podría declarar el tamaño de la matriz más grande para contener un carácter nulo final de la cadena de inicializador o podría usar una lista de inicializadores de matriz para realizar la intención clear que se trata de una matriz de `char`, no una cadena terminada en null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
