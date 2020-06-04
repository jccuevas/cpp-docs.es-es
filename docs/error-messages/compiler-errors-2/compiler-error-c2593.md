---
title: Error del compilador C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759352"
---
# <a name="compiler-error-c2593"></a>Error del compilador C2593

' operator Identifier ' es ambiguo

Se ha definido más de un operador posible para un operador sobrecargado.

Este error puede corregirse si se usa una conversión explícita en uno o más parámetros reales.

En el ejemplo siguiente se genera C2593:

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

Este error puede deberse a la serialización de una variable de punto flotante mediante un objeto `CArchive`. El compilador identifica el operador de `<<` como ambiguo. Los únicos tipos C++ primitivos que `CArchive` pueden serializar son los tipos de tamaño fijo `BYTE`, `WORD`, `DWORD`y `LONG`. Todos los tipos enteros deben convertirse en uno de estos tipos para la serialización. Los tipos de punto flotante se deben archivar mediante la función miembro `CArchive::Write()`.

En el ejemplo siguiente se muestra cómo archivar una variable de punto flotante (`f`) para archivar `ar`:

```
ar.Write(&f, sizeof( float ));
```
