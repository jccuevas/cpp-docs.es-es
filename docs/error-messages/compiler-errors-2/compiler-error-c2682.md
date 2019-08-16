---
title: Error del compilador C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266275"
---
# <a name="compiler-error-c2682"></a>Error del compilador C2682

no se puede usar operador_de_conversión para convertir de 'tipo1' a 'tipo2'

Un operador de conversión intentó convertir entre tipos incompatibles. Por ejemplo, no se puede usar el [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir un puntero a una referencia. El `dynamic_cast` operador no se puede usar para desechar los calificadores. Deben coincidir con todos los calificadores de los tipos.

Puede usar el `const_cast` operador para quitar atributos, como `const`, `volatile`, o `__unaligned`.

El ejemplo siguiente genera C2682:

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

El ejemplo siguiente genera C2682:

```
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