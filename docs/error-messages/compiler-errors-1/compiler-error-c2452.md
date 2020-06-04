---
title: Error del compilador C2452
ms.date: 11/04/2016
f1_keywords:
- C2452
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
ms.openlocfilehash: 7e8173c2697a931e5b292dc974b6d1b22f376794
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744113"
---
# <a name="compiler-error-c2452"></a>Error del compilador C2452

' type ': tipo de origen no válido para safe_cast

El tipo de origen de [safe_cast](../../extensions/safe-cast-cpp-component-extensions.md) no era válido.  Por ejemplo, todos los tipos de una operación de `safe_cast` deben ser tipos CLR.

En el ejemplo siguiente se genera C2452:

```cpp
// C2452.cpp
// compile with: /clr

struct A {};
struct B : public A {};

ref struct C {};
ref struct D : public C{};

int main() {
   A a;
   safe_cast<B*>(&a);   // C2452

   // OK
   C ^ c = gcnew C;
   safe_cast<D^>(c);
}
```
