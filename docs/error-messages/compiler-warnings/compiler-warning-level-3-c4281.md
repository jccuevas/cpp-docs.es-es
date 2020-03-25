---
title: Advertencia del compilador (nivel 3) C4281
ms.date: 11/04/2016
f1_keywords:
- C4281
helpviewer_keywords:
- C4281
ms.assetid: a9771261-5725-4fc6-87b6-16cf92113a25
ms.openlocfilehash: 31c389f4bc0546270240c9c701be7f1e9e620db1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174146"
---
# <a name="compiler-warning-level-3-c4281"></a>Advertencia del compilador (nivel 3) C4281

se ha producido una recursividad ' operator-> ' a través del tipo ' type '

El código permite a los **operadores >** llamarse a sí mismo.

En el ejemplo siguiente se genera C4281:

```cpp
// C4281.cpp
// compile with: /W3 /WX
struct A;
struct B;
struct C;

struct A
{
   int z;
   B& operator->();
};

struct B
{
   C& operator->();
};

struct C
{
   A& operator->();
};

void f(A p)
{
   int i = p->z; // C4281
}
```
