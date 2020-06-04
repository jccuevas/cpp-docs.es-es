---
title: Error del compilador C3703
ms.date: 11/04/2016
f1_keywords:
- C3703
helpviewer_keywords:
- C3703
ms.assetid: 7e3677d9-f2be-4c26-998f-423564e9023c
ms.openlocfilehash: 1071623c8dbaef52a6a391d8858e7502de9c74b4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758000"
---
# <a name="compiler-error-c3703"></a>Error del compilador C3703

' controlador de eventos ': un método de controlador de eventos debe tener la misma clase de almacenamiento que el ' evento ' de origen

Un [evento](../../cpp/event-handling.md) tiene una clase de almacenamiento diferente que el controlador de eventos al que se enlaza. Por ejemplo, este error se produce si el controlador de eventos es una función miembro estática y el evento no es estático. Para corregir este error, asigne el mismo tipo de almacenamiento al evento y al controlador de eventos.

En el ejemplo siguiente se genera C3703:

```cpp
// C3703.cpp
// C3703 expected
#include <stdio.h>

[event_source(type=native)]
class CEventSrc {
public:
   __event static void MyEvent();
};

[event_receiver(type=native)]
class CEventHandler {
public:
   // delete the following line to resolve
   void MyHandler() {}

   // try the following line instead
   // static void MyHandler() {}

   void HookIt(CEventSrc* pSource) {
      __hook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }

   void UnhookIt(CEventSrc* pSource) {
      __unhook(CEventSrc::MyEvent, pSource, &CEventHandler::MyHandler);
   }
};

int main() {
   CEventSrc src;
   CEventHandler hnd;

   hnd.HookIt(&src);
   __raise src.MyEvent();
   hnd.UnhookIt(&src);
}
```
