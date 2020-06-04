---
title: Error del compilador C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7dd47ffbd9481f69f3799a94a17a53ccdffb2a84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745023"
---
# <a name="compiler-error-c2391"></a>Error del compilador C2391

' Identifier ': ' Friend ' no se puede usar durante la definición de tipo

La declaración de `friend` incluye una declaración de clase completa. Una declaración de `friend` puede especificar una función miembro o un especificador de tipo elaborado, pero no una declaración de clase completa.

El ejemplo siguiente genera la advertencia C2326:

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
