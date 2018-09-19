---
title: Error del compilador C3717 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3717
dev_langs:
- C++
helpviewer_keywords:
- C3717
ms.assetid: ae4fceb1-2583-4577-b2f1-40971a017055
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75c770ecfc914c033c1db71578cda137d632e363
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086702"
---
# <a name="compiler-error-c3717"></a>Error del compilador C3717

'method': no se puede definir un método que desencadena eventos

Se ha declarado un método de evento que incluye una implementación. Un [__event](../../cpp/event.md) declaración de método no puede tener una definición. Para corregir este error, asegúrese de que no hay declaraciones de método de evento tienen definiciones. Por ejemplo, en el código siguiente, quite el cuerpo de la función de la `event1` declaración como se indica en los comentarios.

El ejemplo siguiente genera C3717:

```
// C3717.cpp
[event_source(native)]
class CEventSrc {
public:
   __event void event1() {   // C3717
   }

   // remove definition for event1 and substitute following declaration
   // __event void event1();
};

[event_receiver(native)]
class CEventRec {
public:
   void handler1() {
   }

   void HookEvents(CEventSrc* pSrc) {
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }

   void UnhookEvents(CEventSrc* pSrc) {
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);
   }
};

int main() {
}
```