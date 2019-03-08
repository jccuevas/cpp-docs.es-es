---
title: Usar los operadores de adición
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], addition
- additive operators
ms.assetid: 7d54841e-436d-4ae8-9865-1ac1829e6f22
ms.openlocfilehash: 0e2d802a77c56b8f458b614b29e86e2e1d30a55e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151434"
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
