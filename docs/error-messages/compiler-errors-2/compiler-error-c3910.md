---
title: Error del compilador C3910
ms.date: 11/04/2016
f1_keywords:
- C3910
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
ms.openlocfilehash: b9194149c532044f6c8a1eab84729f7896f1352b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568550"
---
# <a name="compiler-error-c3910"></a>Error del compilador C3910

'evento': debe definir el miembro 'método'

Se definió un evento, pero no contiene el método de descriptor de acceso especificada, se requiere.

Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).

El ejemplo siguiente genera C3910:

```
// C3910.cpp
// compile with: /clr /c
delegate void H();
ref class X {
   event H^ E {
      // uncomment the following lines
      // void add(H^) {}
      // void remove( H^ h ) {}
      // void raise( ) {}
   };   // C3910

   event H^ E2; // OK data member
};
```