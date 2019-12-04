---
title: Error del compilador C3910
ms.date: 11/04/2016
f1_keywords:
- C3910
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
ms.openlocfilehash: ef63b8f5d1ee4b3f094bed3549eec8157a950e91
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748884"
---
# <a name="compiler-error-c3910"></a>Error del compilador C3910

' evento ': debe definir el miembro ' Method '

Se definió un evento, pero no contenía el método de descriptor de acceso necesario especificado.

Para obtener más información, vea [Event](../../extensions/event-cpp-component-extensions.md).

En el ejemplo siguiente se genera C3910:

```cpp
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
