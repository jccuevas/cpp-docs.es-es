---
title: Error del compilador C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 86c043889c5342ed4f3edfc4d8a298bcbd345b3b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456399"
---
# <a name="compiler-error-c3765"></a>Error del compilador C3765

'evento': no se puede definir un evento en una class/struct 'tipo' marcada como event_receiver

Si una clase está marcada con el [event_receiver](../../windows/event-receiver.md) atributo, la clase no puede contener un [__event](../../cpp/event.md) declaración.

El ejemplo siguiente genera C3765:

```
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```