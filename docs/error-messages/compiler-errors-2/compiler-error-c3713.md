---
title: Error del compilador C3713
ms.date: 11/04/2016
f1_keywords:
- C3713
helpviewer_keywords:
- C3713
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
ms.openlocfilehash: 8c8c3b5e6016c7f4af471a163463c91d478fea91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444569"
---
# <a name="compiler-error-c3713"></a>Error del compilador C3713

'method': un método de controlador de eventos debe tener los mismos parámetros de función que el origen 'método'

Define un método de controlador de eventos que no utiliza los mismos parámetros que el método de evento de origen. Para corregir este error, dé al método de controlador de eventos los mismos parámetros que los del método del evento de origen.

El ejemplo siguiente genera C3713:

```
// C3713.cpp
// compile with: /c
[event_source(native)]
class CEventSrc {
public:
   __event void event1(int nValue);
   // try the following line instead
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {}

   void HookEvents(CEventSrc* pSrc) {
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713
   }
};
```