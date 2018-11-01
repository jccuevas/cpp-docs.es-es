---
title: Advertencia del compilador (nivel 1) C4549
ms.date: 11/04/2016
f1_keywords:
- C4549
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
ms.openlocfilehash: 5732b2f963be52512d5d80f2552af4a80acb3372
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657241"
---
# <a name="compiler-warning-level-1-c4549"></a>Advertencia del compilador (nivel 1) C4549

'operador': operador antes de una coma no tiene ningún efecto; ¿ha pensado en 'operador'?

El compilador detectó una expresión de coma mal formada.

De forma predeterminada, esta advertencia está desactivada. Para obtener más información, consulte [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

El ejemplo siguiente genera C4549:

```
// C4549.cpp
// compile with: /W1
#pragma warning (default : 4549)

int main() {
   int i = 0, k = 0;

   if ( i == 0, k )   // C4549
   // try the following line instead
   // if ( i == 0 )
      i++;
}
```