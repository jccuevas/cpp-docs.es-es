---
title: Error del compilador C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: c1ce0132ed0db418359effe60f59e1eb2d3cc221
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760288"
---
# <a name="compiler-error-c2682"></a>Error del compilador C2682

no se puede usar casting_operator para convertir de ' tipo1 ' a ' tipo2 '

Un operador de conversión intentó realizar una conversión entre tipos incompatibles. Por ejemplo, no puede utilizar el operador [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir un puntero a una referencia. No se puede usar el operador `dynamic_cast` para convertir calificadores. Todos los calificadores de los tipos deben coincidir.

Puede usar el operador `const_cast` para quitar atributos como `const`, `volatile`o `__unaligned`.

En el ejemplo siguiente se genera C2682:

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

En el ejemplo siguiente se genera C2682:

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
