---
title: Advertencia del compilador (nivel 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: 4de80a9b7ad5601d9f8760d7c55a64a8631307a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162379"
---
# <a name="compiler-warning-level-1-c4441"></a>Advertencia del compilador (nivel 1) C4441

se omitió la Convención de llamada de ' CC1 '; se usó ' CC2 ' en su lugar

Las funciones miembro en los tipos administrados definidos por el usuario y los genéricos de funciones globales deben usar la Convención de llamada de [__clrcall](../../cpp/clrcall.md) .  El compilador usó `__clrcall`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4441.

```cpp
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
