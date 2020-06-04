---
title: Error del compilador C3865
ms.date: 11/04/2016
f1_keywords:
- C3865
helpviewer_keywords:
- C3865
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
ms.openlocfilehash: 960c795fe934433e4e3cf79e4c01c49d00205b9b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761496"
---
# <a name="compiler-error-c3865"></a>Error del compilador C3865

' calling_convention ': solo se puede usar en funciones miembro nativas

Se utilizó una Convención de llamada en una función que era una función global o una función miembro administrada. La Convención de llamada solo se puede usar en una función miembro nativa (no administrada).

Para obtener más información, vea [convenciones de llamada](../../cpp/calling-conventions.md).

En el ejemplo siguiente se genera C3865:

```cpp
// C3865.cpp
// compile with: /clr
// processor: x86
void __thiscall Func(){}   // C3865

// OK
struct MyType {
   void __thiscall Func(){}
};
```
