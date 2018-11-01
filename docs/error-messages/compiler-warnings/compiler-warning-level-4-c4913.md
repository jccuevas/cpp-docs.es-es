---
title: Advertencia del compilador (nivel 4) C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: a06fda0999e5f164fca81917cecbb63312fea25d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613829"
---
# <a name="compiler-warning-level-4-c4913"></a>Advertencia del compilador (nivel 4) C4913

**el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado**

Se produjo una llamada al operador coma integrado en un programa que también tenía un operador coma sobrecargado; no se ejecutó una conversión que creía que se había producido.

El ejemplo siguiente genera la advertencia C4913:

```
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```