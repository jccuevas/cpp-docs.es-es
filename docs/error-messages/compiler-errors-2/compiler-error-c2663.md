---
title: Error del compilador C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756037"
---
# <a name="compiler-error-c2663"></a>Error del compilador C2663

' función ': las sobrecargas de número no tienen conversiones válidas para el puntero ' this '

El compilador no pudo convertir `this` en ninguna de las versiones sobrecargadas de la función miembro.

Este error puede deberse a la invocación de una función miembro no`const` en un objeto `const`.  Soluciones posibles:

1. Quite la `const` de la declaración del objeto.

1. Agregue `const` a una de las sobrecargas de función miembro.

En el ejemplo siguiente se genera C2663:

```cpp
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```
