---
title: ADVERTENCIA del compilador (nivel 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: 2136e94a261b2f767165e43acfd66583e8d15e9f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164591"
---
# <a name="compiler-warning-level-1-c4020"></a>ADVERTENCIA del compilador (nivel 1) C4020

' function ': hay demasiados parámetros reales

El número de parámetros reales en una llamada de función supera el número de parámetros formales en el prototipo o la definición de la función. El compilador pasa los parámetros reales adicionales según la Convención de llamada de la función.

En el ejemplo siguiente se genera C4020:

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

Solución posible:

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```
