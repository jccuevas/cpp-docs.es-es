---
title: Error del compilador C3765
ms.date: 11/04/2016
f1_keywords:
- C3765
helpviewer_keywords:
- C3765
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
ms.openlocfilehash: 8a12bdfaf0931fb0a94dafc289f9ae39aef61f23
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757245"
---
# <a name="compiler-error-c3765"></a>Error del compilador C3765

' evento ': no se puede definir un evento en una clase o estructura ' type ' marcada como event_receiver

Si una clase está marcada con el atributo [event_receiver](../../windows/event-receiver.md) , la clase no puede contener una declaración [__event](../../cpp/event.md) .

En el ejemplo siguiente se genera C3765:

```cpp
// C3765.cpp
[event_receiver(native)]
struct ER2 {
   __event void f();   // C3765
   __event void b(int);   // C3765
};
```
