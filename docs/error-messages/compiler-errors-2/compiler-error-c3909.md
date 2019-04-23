---
title: Error del compilador C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 95de97a27fc42e98247675b1b48325593ff3c21e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779380"
---
# <a name="compiler-error-c3909"></a>Error del compilador C3909

aWinRT o declaración de evento administrado debe aparecer en un tipo administrado o WinRT

Se declaró un evento de Windows en tiempo de ejecución o administrado en un tipo nativo. Para corregir este error, declare los eventos en tipos de Windows Runtime o en tipos administrados.

Para obtener más información, consulte [eventos](../../extensions/event-cpp-component-extensions.md).

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