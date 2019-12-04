---
title: Error del compilador C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d0e283c7cd6116655a56f8df67ab4eecf9923b68
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760946"
---
# <a name="compiler-error-c2884"></a>Error del compilador C2884

' name ': la introducción por la declaración Using entra en conflicto con la función local ' function '

Intentó definir una función más de una vez. La primera definición es una definición local. La segunda es de un espacio de nombres con una declaración `using`.

En el ejemplo siguiente se genera C2884:

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
