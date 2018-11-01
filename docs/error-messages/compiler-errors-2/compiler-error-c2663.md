---
title: Error del compilador C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644345"
---
# <a name="compiler-error-c2663"></a>Error del compilador C2663

'function': número sobrecargas no tienen ninguna conversión válida para el puntero 'this'

No se pudo convertir el compilador `this` a cualquiera de las versiones sobrecargadas de la función miembro.

Este error puede deberse a invocar no`const` función miembro en un `const` objeto.  Soluciones posibles:

1. Quitar el `const` de la declaración del objeto.

1. Agregar `const` a una de las sobrecargas de función miembro.

El ejemplo siguiente genera C2663:

```
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