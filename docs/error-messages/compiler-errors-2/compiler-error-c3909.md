---
title: Error del compilador C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749001"
---
# <a name="compiler-error-c3909"></a>Error del compilador C3909

la declaración de eventos aWinRT o Managed debe aparecer en un tipo WinRT o administrado

Se declaró un evento de Windows en tiempo de ejecución o administrado en un tipo nativo. Para corregir este error, declare los eventos en tipos de Windows Runtime o en tipos administrados.

Para obtener más información, vea [Event](../../extensions/event-cpp-component-extensions.md).

El ejemplo siguiente genera el error C3909 y muestra cómo corregirlo:

```cpp
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
