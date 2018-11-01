---
title: Error del compilador C3804
ms.date: 11/04/2016
f1_keywords:
- C3804
helpviewer_keywords:
- C3804
ms.assetid: 7c4cda28-ec96-4d04-937b-36dbd9944722
ms.openlocfilehash: e83380696aca3d6d45c235925b830bef9e3061a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544591"
---
# <a name="compiler-error-c3804"></a>Error del compilador C3804

'property_accessor': los métodos de descriptor de acceso de una propiedad debe ser estáticos o no estáticos

Al definir una propiedad no trivial, las funciones de descriptor de acceso pueden ser estáticas o instancia, pero no ambos.

Vea [property](../../windows/property-cpp-component-extensions.md) para obtener más información.

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