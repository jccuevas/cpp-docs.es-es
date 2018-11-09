---
title: Usar los operadores de adición
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 78dc559a83626057603027e30742435b1128e31c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557695"
---
# <a name="using-the-additive-operators"></a>Usar los operadores de adición

En los ejemplos siguientes, que muestran los operadores de suma y resta, se usan estas declaraciones:

```
int i = 4, j;
float x[10];
float *px;
```

Estas instrucciones son equivalentes:

```
px = &x[4 + i];
px = &x[4] + i;
```

El valor de `i` se multiplica por la longitud de un valor **float** y se agrega a `&x[4]`. El valor del puntero resultante es la dirección de `x[8]`.

```
j = &x[i] - &x[i-2];
```

En este ejemplo, la dirección del tercer elemento de `x` (proporcionado por `x[i-2]`) se resta de la dirección del quinto elemento de `x` (proporcionado por `x[i]`). La diferencia se divide por la longitud de un valor **float**; el resultado es el valor entero 2.

## <a name="see-also"></a>Vea también

[Operadores de adición de C](../c-language/c-additive-operators.md)