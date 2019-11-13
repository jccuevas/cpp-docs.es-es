---
title: ADVERTENCIA del compilador (nivel 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 8402c6a2d0fcbb4704b833ac7ae2b070c7af3a48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051587"
---
# <a name="compiler-warning-level-3-c4390"></a>ADVERTENCIA del compilador (nivel 3) C4390

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