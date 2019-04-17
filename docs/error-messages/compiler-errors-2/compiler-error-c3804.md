---
title: Error del compilador C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: c3c00d1d07306a9e8dc67d3f75a5cb25d8f03aee
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770297"
---
# <a name="compiler-error-c3804"></a>Error del compilador C3804

'property_accessor': los métodos de descriptor de acceso de una propiedad debe ser estáticos o no estáticos

Al definir una propiedad no trivial, las funciones de descriptor de acceso pueden ser estáticas o instancia, pero no ambos.

Vea [property](../../extensions/property-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3804.

```
// C3804.cpp
// compile with: /c /clr
ref struct A {

   property int i {
      static int get() {}
      void set(int i) {}
   }   // C3804 error

   // OK
   property int j {
      int get() { return 0; }
      void set(int i) {}
   }

   property int k {
      static int get() { return 0; }
      static void set(int i) {}
   }
};
```