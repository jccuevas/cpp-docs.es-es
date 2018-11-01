---
title: Error del compilador C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d920629dc0697d0f2fdd05ac5aca6118b89b88cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489732"
---
# <a name="compiler-error-c2884"></a>Error del compilador C2884

'name': introducido por la declaración using entra en conflicto con la función local 'function'

Ha intentado definir una función varias veces. La primera definición es una definición local. El segundo es de un espacio de nombres con un `using` declaración.

El ejemplo siguiente genera C2884:

```
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```