---
title: Error del compilador C2876
ms.date: 11/04/2016
f1_keywords:
- C2876
helpviewer_keywords:
- C2876
ms.assetid: 8b674bf1-f9f4-4a8e-8127-e884c1d1708f
ms.openlocfilehash: bb242c889d924612b5349ea06c19db954261b245
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736352"
---
# <a name="compiler-error-c2876"></a>Error del compilador C2876

' Class:: Symbol ': no se puede tener acceso a todas las sobrecargas

Todas las formas sobrecargadas de una función de una clase base deben ser accesibles para la clase derivada.

En el ejemplo siguiente se genera C2876:

```cpp
// C2876.cpp
// compile with: /c
class A {
public:
   double a(double);
private:
   int a(int);
};

class B : public A {
   using A::a;   // C2876 one overload is private in base class
};
```
