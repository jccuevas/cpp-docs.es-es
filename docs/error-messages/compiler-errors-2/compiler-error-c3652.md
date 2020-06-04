---
title: Error del compilador C3652
ms.date: 11/04/2016
f1_keywords:
- C3652
helpviewer_keywords:
- C3652
ms.assetid: 15d68737-177e-41f1-80e0-7c3e2afdf0fc
ms.openlocfilehash: 3290b1e4b40a63a69911452b845bf1ea0ddf3223
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756349"
---
# <a name="compiler-error-c3652"></a>Error del compilador C3652

' override ': una función que invalida explícitamente debe ser virtual

Una función que realiza una invalidación explícita debe ser virtual. Para obtener más información, vea [invalidaciones explícitas](../../extensions/explicit-overrides-cpp-component-extensions.md).

En el ejemplo siguiente se genera C3652:

```cpp
// C3652.cpp
// compile with: /clr /c
public interface class I {
   void f();
};

public ref struct R : I {
   void f() = I::f {}   // C3652
   // try the following line instead
   // virtual void f() = I::f {}
};
```
