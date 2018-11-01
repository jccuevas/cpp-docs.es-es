---
title: Error del compilador C2164
ms.date: 11/04/2016
f1_keywords:
- C2164
helpviewer_keywords:
- C2164
ms.assetid: 55df5024-68a8-45a8-ae6c-e6dba35318a2
ms.openlocfilehash: 3b1c7a94dfca1c2767e14f96204ecda670c8a586
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460819"
---
# <a name="compiler-error-c2164"></a>Error del compilador C2164

'function': función intrínseca no declarada

Un `intrinsic` pragma utiliza una función sin declarar (sólo se produce con **/Oi**). O bien, uno de los intrínsecos del compilador se utilizó sin incluir su archivo de encabezado.

El ejemplo siguiente genera C2164:

```
// C2164.c
// compile with: /c
// processor: x86
// Uncomment the following line to resolve.
// #include "xmmintrin.h"
void b(float *p) {
   _mm_load_ss(p);   // C2164
}
```