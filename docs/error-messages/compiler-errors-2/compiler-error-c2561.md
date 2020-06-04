---
title: Error del compilador C2561
ms.date: 11/04/2016
f1_keywords:
- C2561
helpviewer_keywords:
- C2561
ms.assetid: 0abe955b-53a6-4a3c-8362-b1a8eb40e8d1
ms.openlocfilehash: b4a14be9cd32c752e2ab889417494e80b935e31b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755569"
---
# <a name="compiler-error-c2561"></a>Error del compilador C2561

' Identifier ': la función debe devolver un valor

La función se declaró como si devolviera un valor, pero la definición de función no contiene una instrucción `return`.

Este error puede deberse a un prototipo de función incorrecto:

1. Si la función no devuelve un valor, declare la función con el tipo de valor devuelto [void](../../cpp/void-cpp.md).

1. Compruebe que todas las ramas posibles de la función devuelven un valor del tipo declarado en el prototipo.

1. C++las funciones que contienen rutinas de ensamblado en línea que almacenan el valor devuelto en el registro de `AX` pueden necesitar una instrucción return. Copie el valor de `AX` en una variable temporal y devuelva esa variable desde la función.

En el ejemplo siguiente se genera C2561:

```cpp
// C2561.cpp
int Test(int x) {
   if (x) {
      return;   // C2561
      // try the following line instead
      // return 1;
   }
   return 0;
}

int main() {
   Test(1);
}
```
