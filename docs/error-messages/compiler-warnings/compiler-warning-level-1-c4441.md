---
title: Compilador advertencia (nivel 1) C4441 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4441
dev_langs:
- C++
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a505c47ea348175a16c91c309646428f1222d091
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033438"
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