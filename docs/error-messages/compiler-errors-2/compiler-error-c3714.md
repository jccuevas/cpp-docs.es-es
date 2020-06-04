---
title: Error del compilador C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 1078bf8a97f6cb7afeaf7046489fe262c0bb0199
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753333"
---
# <a name="compiler-error-c3714"></a>Error del compilador C3714

' Method ': un método de controlador de eventos debe tener la misma Convención de llamada que el ' método ' de origen

Definió un método de controlador de eventos que no utilizaba la misma Convención de llamada que el método de evento de origen. Para corregir este error, asigne al método de controlador de eventos las mismas convenciones de llamada que las del método de evento de origen. Por ejemplo, en el código siguiente, haga que las convenciones de llamada de `handler1` y `event1` coincidan ([__cdecl](../../cpp/cdecl.md) o [__stdcall](../../cpp/stdcall.md) , etc.). Quitar las palabras clave de Convención de llamada de ambas declaraciones también resolverá el problema y provocará que `event1` y `handler1` tengan como valor predeterminado la Convención de llamada [thiscall](../../cpp/thiscall.md) . Vea [convenciones de llamada](../../cpp/calling-conventions.md) para obtener más información.

En el ejemplo siguiente se genera C3714:

```cpp
// C3714.cpp
// compile with: /c
// processor: x86
[event_source(native)]
class CEventSrc {
public:
   __event void __cdecl event1();
   // try the following line instead
   // __event void __stdcall event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void __stdcall handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714
   }
};
```
