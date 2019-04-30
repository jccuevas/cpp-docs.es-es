---
title: Advertencia del compilador (nivel 3) C4390
ms.date: 11/04/2016
f1_keywords:
- C4390
helpviewer_keywords:
- C4390
ms.assetid: c95c2f1b-9bce-4b1f-a80c-565d4cde0b1e
ms.openlocfilehash: 4ca00f892adc8fe3ac1bffb59a27ea1744249dea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401987"
---
# <a name="compiler-warning-level-3-c4390"></a>Advertencia del compilador (nivel 3) C4390

';': una se encuentra; de instrucción controlada vacía ¿Esto es la intención?

Se encontró un punto y coma después de una instrucción de control que no contiene instrucciones.

Si obtiene C4390 debido a una macro, debe usar el [advertencia](../../preprocessor/warning.md) pragma para deshabilitar C4390 en el módulo que contiene la macro.

El ejemplo siguiente genera C4390:

```
// C4390.cpp
// compile with: /W3
int main() {
   int i = 0;
   if (i);   // C4390
      i++;
}
```