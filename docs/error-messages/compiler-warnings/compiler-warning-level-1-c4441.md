---
title: Advertencia del compilador (nivel 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 45d7a6af09677c1e63dab5ffcc55c35d8203b40b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50539703"
---
# <a name="compiler-warning-level-1-c4441"></a>Advertencia del compilador (nivel 1) C4441

convención de llamada de 'cc1' omitida; en su lugar, usó 'cc2'

Las funciones miembro de tipos administrados definidos por el usuario y tipos genéricos de la función global deben usar el [__clrcall](../../cpp/clrcall.md) convención de llamada.  El compilador usa `__clrcall`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4441.

```
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```