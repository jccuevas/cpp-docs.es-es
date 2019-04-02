---
title: Error del compilador C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: f2a346354d8da7d78c5517b01b4438bfb8af50ad
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774846"
---
# <a name="compiler-error-c3290"></a>Error del compilador C3290

'type': una propiedad trivial no puede tener tipo de referencia

Se ha declarado incorrectamente una propiedad. Cuando se declara una propiedad trivial, el compilador crea una variable que actualizará la propiedad y no es posible tener una variable de referencia de seguimiento en una clase.

Consulte [propiedad](../../extensions/property-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../extensions/tracking-reference-operator-cpp-component-extensions.md) para obtener más información.

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