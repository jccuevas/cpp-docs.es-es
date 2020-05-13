---
title: Advertencia del compilador (nivel 2) C4356
ms.date: 11/04/2016
f1_keywords:
- C4356
helpviewer_keywords:
- C4356
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
ms.openlocfilehash: ffcf0098799b893f83e331b3b4cc602e1b538b1c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161833"
---
# <a name="compiler-warning-level-2-c4356"></a>Advertencia del compilador (nivel 2) C4356

' Member ': no se puede inicializar un miembro de datos estático mediante una clase derivada

La inicialización de un miembro de datos estático tenía un formato incorrecto. El compilador aceptó la inicialización. Para evitar la advertencia, inicialice el miembro a través de la clase base.

Use la pragma [Warning](../../preprocessor/warning.md) para suprimir esta advertencia.

En el ejemplo siguiente se genera C4356:

```cpp
// C4356.cpp
// compile with: /W2 /EHsc
#include <iostream>

template <class T>
class C {
   static int n;
};

class D : C<int> {};

int D::n = 0; // C4356
// try the following line instead
// int C<int>::n = 0;

class A {
public:
   static int n;
};

class B : public A {};

int B::n = 10;   // C4356
// try the following line instead
// int A::n = 99;

int main() {
   using namespace std;
   cout << B::n << endl;
}
```
