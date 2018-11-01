---
title: Error del compilador C3059
ms.date: 11/04/2016
f1_keywords:
- C3059
helpviewer_keywords:
- C3059
ms.assetid: 57220324-8286-4cab-a1ab-45385eb1eae0
ms.openlocfilehash: df1f65f231f72f2efa90458fe9b21339dda80080
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668434"
---
# <a name="compiler-error-c3059"></a>Error del compilador C3059

'var': el símbolo 'threadprivate' no se puede usar en la cláusula 'cláusula'.

Se usó un símbolo [threadprivate](../../parallel/openmp/reference/threadprivate.md) en una cláusula.

El ejemplo siguiente genera la advertencia C3059:

```
// C3059.cpp
// compile with: /openmp
#include "omp.h"
int x, y;
#pragma omp threadprivate(x, y)

int main() {
   #pragma omp parallel private(x, y)   // C3059
   {
      x = y;
   }
}
```

Posible resolución:

```
// C3059b.cpp
// compile with: /openmp
#include "omp.h"
int x = 0, y = 0;

int main() {
   #pragma omp parallel firstprivate(y) private(x)
   {
      x = y;
   }
}
```