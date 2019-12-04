---
title: Error del compilador C2514
ms.date: 11/04/2016
f1_keywords:
- C2514
helpviewer_keywords:
- C2514
ms.assetid: 4b7085e5-6714-4261-80b7-bc72e64ab3e8
ms.openlocfilehash: e0153ec9d48225d153221f2192761da4023fab96
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746518"
---
# <a name="compiler-error-c2514"></a>Error del compilador C2514

' Class ': la clase no tiene constructores

La clase, estructura o Unión no tiene ningún constructor con una lista de parámetros que coincida con los parámetros que se usan para crear una instancia del mismo.

Una clase debe declararse por completo antes de que se puedan crear instancias de ella.

En el ejemplo siguiente se genera C2514:

```cpp
// C2514.cpp
// compile with: /c
class f;

class g {
public:
    g (int x);
};

class fmaker {
   f *func1() {
      return new f(2);   // C2514
   }

   g *func2() {
      return new g(2);   // OK
   }
};
```
