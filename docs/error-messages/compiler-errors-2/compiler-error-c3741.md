---
title: Error del compilador C3741
ms.date: 11/04/2016
f1_keywords:
- C3741
helpviewer_keywords:
- C3741
ms.assetid: ed311315-cc32-49c9-97fa-01b293d81526
ms.openlocfilehash: d207c87c7b3f75ac939c155da127720562973160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569265"
---
# <a name="compiler-error-c3741"></a>Error del compilador C3741

'class': debe ser una coclase cuando el parámetro 'layout_dependent' de event_receiver = true

Cuando `layout_dependent=true` para un [event_receiver](../../windows/event-receiver.md) clase y, a continuación, la clase también debe tener la [coclase](../../windows/coclass.md) atributo.

El ejemplo siguiente genera C3741

```
// C3741.cpp
// compile with: /c
// C3741 expected
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
[module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I{ HRESULT f(); };

// Delete the following line to resolve.
[ event_receiver(com, layout_dependent=true)]

// class or struct must be declared with coclass
// Uncomment the following line to resolve.
// [ event_receiver(com, layout_dependent=true), coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct R : I {
   HRESULT f(){ return 0; }
   R(){}
   R(I* a){ __hook(I, a); }
};
```