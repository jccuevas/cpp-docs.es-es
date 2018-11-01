---
title: Error del compilador C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 435288ba657bd22ba29c6681014ae15baa051cec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636467"
---
# <a name="compiler-error-c3909"></a>Error del compilador C3909

aWinRT o declaración de evento administrado debe aparecer en un tipo administrado o WinRT

Se declaró un evento de Windows Runtime o administrado en un tipo nativo. Para corregir este error, declare los eventos en tipos de Windows Runtime o en tipos administrados.

Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).

El ejemplo siguiente genera el error C3909 y muestra cómo corregirlo:

```
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```