---
title: Advertencia del compilador (nivel 4) C4740
ms.date: 11/04/2016
f1_keywords:
- C4740
helpviewer_keywords:
- C4740
ms.assetid: 85528969-966a-44b4-8a2f-971704c64477
ms.openlocfilehash: 936dfb5464eabe7b1ac44df24445224fb9e204a0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457890"
---
# <a name="compiler-warning-level-4-c4740"></a>Advertencia del compilador (nivel 4) C4740

flujo dentro o fuera del código inline asm suprime la optimización global

Cuando hay un salto en a o fuera de un `asm` bloque, se deshabilitan las optimizaciones globales para esa función.

El ejemplo siguiente genera C4740:

```
// C4740.cpp
// compile with: /O2 /W4
// processor: x86
int main() {
   __asm jmp tester
   tester:;
}
```