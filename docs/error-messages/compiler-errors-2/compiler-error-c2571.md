---
title: Error del compilador C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 7bd87f0732e1a632b8c86cc57fab1a0f104b2c77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755504"
---
# <a name="compiler-error-c2571"></a>Error del compilador C2571

' función ': la función virtual no puede estar en la Unión ' Union '

Una Unión se declara con una función virtual. Solo puede declarar una función virtual en una clase o estructura.  Soluciones posibles:

1. Cambie la Unión a una clase o estructura.

1. Haga que la función no sea virtual.

En el ejemplo siguiente se genera C2571:

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
