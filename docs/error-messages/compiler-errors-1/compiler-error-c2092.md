---
title: Error del compilador C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: b530663cae2292ebeab1b871e495e9a45e4633cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754672"
---
# <a name="compiler-error-c2092"></a>Error del compilador C2092

el tipo de elemento de matriz ' array name ' no puede ser function

No se permiten matrices de funciones. Use una matriz de punteros a funciones.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2092:

```cpp
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>Ejemplo

Solución posible:

```cpp
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```
