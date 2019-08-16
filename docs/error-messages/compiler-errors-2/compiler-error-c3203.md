---
title: Error del compilador C3203
ms.date: 11/04/2016
f1_keywords:
- C3203
helpviewer_keywords:
- C3203
ms.assetid: 6356770e-22c1-434c-91fe-f60b0aa23b91
ms.openlocfilehash: c55160c855a6188a616f957acee43e409b751b62
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447799"
---
# <a name="compiler-error-c3203"></a>Error del compilador C3203

'tipo' : una plantilla de clase no especializada o un genérico no pueden usarse como plantilla o argumento genérico para el parámetro genérico o plantilla 'param'; se esperaba un tipo real.

Se pasó un argumento no válido a una plantilla de clase o genérico. La plantilla de clase o el genérico esperan un tipo como parámetro.

Este error puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio 2005: una plantilla de clase no especializada no puede usarse como un argumento de plantilla en una lista de clases base. Para evitar el error C3203, agregue explícitamente los parámetros de tipo de plantilla al nombre de clase de plantilla cuando lo use como parámetro de plantilla en una lista de clases base.

```
// C3203.cpp
template< typename T >
struct X {
   void f(X) {}
};

template< typename T >
struct Y : public X<Y> {   // C3203
// try the following line instead
// struct Y : public X<Y<T> > {
   void f(Y) {}
};

int main() {
   Y<int> y;
}
```

En el siguiente ejemplo se genera el error C3203 y se muestra cómo corregirlo:

```
// C3203_b.cpp
// compile with: /c
template <class T>
struct S1 {};

template <class T>
class C1 {};

typedef C1<S1> MyC1;   // C3203

// OK
template <template <class> class T>
class C2 {};

typedef C2<S1> MyC1;

template <class T>
class C3 {};

typedef C3<S1<int> > MyC12;
```

El error C3203 también puede producirse al usar genéricos:

```
// C3203_c.cpp
// compile with: /clr /c
generic <class T>
value struct GS1 {};

generic <class T>
value struct GC1 {};

typedef GC1<GS1> MyGC1;   // C3203
typedef GC1<GS1<int> > MyGC2;   // OK
```