---
title: Error del compilador C2509
ms.date: 11/04/2016
f1_keywords:
- C2509
helpviewer_keywords:
- C2509
ms.assetid: 339c1fcd-ec4a-456c-9f18-a9b24d9921af
ms.openlocfilehash: f0322c1d6f80f26b81ac0e93b944a2f3277026ce
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746817"
---
# <a name="compiler-error-c2509"></a>Error del compilador C2509

' Identifier ': función miembro no declarada en ' clase '

La función no se declara en la clase especificada.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2509.

```cpp
// C2509.cpp
// compile with: /c
struct A {
   virtual int vfunc() = 0;
   virtual int vfunc2() = 0;
};

struct B : private A {
   using A::vfunc;
   virtual int vfunc2();
};

int B::vfunc() { return 1; }   // C2509
int B::vfunc2() { return 1; }   // OK
```
