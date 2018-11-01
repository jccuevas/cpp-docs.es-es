---
title: Error del compilador C2090
ms.date: 11/04/2016
f1_keywords:
- C2090
helpviewer_keywords:
- C2090
ms.assetid: e8176e55-382b-453d-aa27-6597f0274afd
ms.openlocfilehash: d805a4d6e0da0e94288ac36c6680a952b7633b86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469399"
---
# <a name="compiler-error-c2090"></a>Error del compilador C2090

Devuelve una matriz (función)

Una función no puede devolver una matriz. Devolver un puntero a una matriz en su lugar.

El ejemplo siguiente genera C2090:

```
// C2090.cpp
int func1(void)[] {}   // C2090
```

Posible resolución:

```
// C2090b.cpp
// compile with: /c
int* func2(int * i) {
   return i;
}
```