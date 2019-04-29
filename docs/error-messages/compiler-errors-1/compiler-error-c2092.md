---
title: Error del compilador C2092
ms.date: 11/04/2016
f1_keywords:
- C2092
helpviewer_keywords:
- C2092
ms.assetid: 037e44ae-16c8-489a-a512-dcdf7f7795a6
ms.openlocfilehash: d3d0b0e62fbc5f8ad90b3fee5fe39c6bdaba7c2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376015"
---
# <a name="compiler-error-c2092"></a>Error del compilador C2092

tipo de elemento de matriz 'nombre de la matriz' no puede ser una función

No se permiten matrices o funciones. Use una matriz de punteros a funciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2092:

```
// C2092.cpp
typedef void (F) ();
typedef F AT[10];   // C2092
```

## <a name="example"></a>Ejemplo

Posible resolución:

```
// C2092b.cpp
// compile with: /c
typedef void (F) ();
typedef F * AT[10];
```