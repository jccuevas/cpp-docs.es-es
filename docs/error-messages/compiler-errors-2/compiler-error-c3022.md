---
title: Error del compilador C3022
ms.date: 11/04/2016
f1_keywords:
- C3022
helpviewer_keywords:
- C3022
ms.assetid: 9f1d444c-6c6e-48d9-9346-69128390aa33
ms.openlocfilehash: 187db5a7150ee0956258e83596966e269e5e50c7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651599"
---
# <a name="compiler-error-c3022"></a>Error del compilador C3022

'clause': tipo de programación no válida de 'value' en la directiva de OpenMP 'directive'

Se pasó un valor no admitido a una cláusula.

El ejemplo siguiente genera la advertencia C3022:

```
// C3022.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(10)   // C3022
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(x)   // C3022
   for (i = 0; i < 10; ++i) ;

   // OK
   #pragma omp parallel for schedule(runtime)
   for (i = 0; i < 10; ++i)
   ;
}
```