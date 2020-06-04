---
title: Error del compilador C3029
ms.date: 11/04/2016
f1_keywords:
- C3029
helpviewer_keywords:
- C3029
ms.assetid: 655eb04d-504a-468d-8c0c-bda1e5f297b7
ms.openlocfilehash: 12c06757ed6ec7560f7dd647e241ddd08a0484d5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736755"
---
# <a name="compiler-error-c3029"></a>Error del compilador C3029

'symbol': solamente puede aparecer una vez en cláusulas de uso compartido de datos de una directiva de OpenMP

Se utilizó un símbolo más de una vez en una o varias cláusulas de una directiva. El símbolo solo puede utilizarse una vez en la directiva.

El ejemplo siguiente genera la advertencia C3029:

```cpp
// C3029.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

int g_i;

int main() {
   int i, x;

   #pragma omp parallel reduction(+ : x, x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;

   #pragma omp parallel private(x) reduction(+ : x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;
}
```
