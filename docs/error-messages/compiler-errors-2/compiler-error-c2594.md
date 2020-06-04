---
title: Error del compilador C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759339"
---
# <a name="compiler-error-c2594"></a>Error del compilador C2594

' operador ': conversiones ambiguas de ' tipo1 ' a ' tipo2 '

Ninguna conversión de *Type1* a *tipo2* era más directa que otra. Sugerimos dos posibles soluciones para convertir de *Type1* a *tipo2*. La primera opción consiste en definir una conversión directa de *tipo1* a *tipo2*y la segunda opción consiste en especificar una secuencia de conversiones de *tipo1* a *tipo2*.

En el ejemplo siguiente se genera C2594. La resolución sugerida para el error es una secuencia de conversiones:

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
