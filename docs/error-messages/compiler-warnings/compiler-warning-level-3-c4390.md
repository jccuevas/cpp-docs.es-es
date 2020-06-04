---
title: Advertencia del compilador (nivel 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 63150f4ca801d3c377c7bc09b58a778bebf02b46
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198684"
---
# <a name="compiler-warning-level-3-c4390"></a>Advertencia del compilador (nivel 3) C4390

'; ': se encontró una instrucción controlada vacía; ¿es esta la intención?

Se encontró un punto y coma después de una instrucción de control que no contiene instrucciones.

Si obtiene C4390 debido a una macro, debe usar la pragma [Warning](../../preprocessor/warning.md) para deshabilitar C4390 en el módulo que contiene la macro.

En el ejemplo siguiente se genera C4390:

```cpp
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```
