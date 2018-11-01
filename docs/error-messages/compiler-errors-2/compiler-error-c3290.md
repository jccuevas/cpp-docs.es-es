---
title: Error del compilador C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: d82d3272563f7a5af5de399a2f7fff621500e612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490486"
---
# <a name="compiler-error-c3290"></a>Error del compilador C3290

'type': una propiedad trivial no puede tener tipo de referencia

Se ha declarado incorrectamente una propiedad. Cuando se declara una propiedad trivial, el compilador crea una variable que actualizará la propiedad y no es posible tener una variable de referencia de seguimiento en una clase.

Consulte [propiedad](../../windows/property-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3290.

```
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```