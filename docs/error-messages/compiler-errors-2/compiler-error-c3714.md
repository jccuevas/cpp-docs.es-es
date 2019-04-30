---
title: Error del compilador C3714
ms.date: 11/04/2016
f1_keywords:
- C3714
helpviewer_keywords:
- C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
ms.openlocfilehash: 9bfdf8b26ab599ef1a28483af7ebc28f0dbc1912
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328346"
---
# <a name="compiler-error-c3714"></a>Error del compilador C3714

'method': un método de controlador de eventos debe tener la misma convención de llamada que el origen 'método'

Define un método de controlador de eventos que no utiliza la misma convención de llamada que el método de evento de origen. Para corregir este error, dé al método de controlador de eventos las mismas convenciones de llamada que los del método del evento de origen. Por ejemplo, en el código siguiente, realice las convenciones de llamada de `handler1` y `event1` coinciden ([__cdecl](../../cpp/cdecl.md) o [__stdcall](../../cpp/stdcall.md) u otros). Eliminación de palabras clave de convención de llamada de ambas declaraciones también solucionar el problema y provocar `event1` y `handler1` al valor predeterminado para el [thiscall](../../cpp/thiscall.md) convención de llamada. Consulte [convenciones de llamada](../../cpp/calling-conventions.md) para obtener más información.

El ejemplo siguiente genera C3714:

```
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