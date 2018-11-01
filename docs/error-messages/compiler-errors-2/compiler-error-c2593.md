---
title: Error del compilador C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: c358553a36104b5c389076f5a5ce02f94f85e85a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667316"
---
# <a name="compiler-error-c2593"></a>Error del compilador C2593

'operador identificador' es ambiguo

Se define más de un operador para posibles para un operador sobrecargado.

Este error puede corregirse si usa una conversión explícita en uno o varios parámetros reales.

El ejemplo siguiente genera C2593:

```
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

Este error puede deberse a un punto flotante por medio de serializar un `CArchive` objeto. El compilador identifica la `<<` operador como ambigua. Tipos de C++ solo primitivos que `CArchive` puede serializar son los tipos de tamaño fijo `BYTE`, `WORD`, `DWORD`, y `LONG`. Todos los tipos de entero deben convertirse en uno de estos tipos para la serialización. Tipos de punto flotante pueden almacenarse utilizando el `CArchive::Write()` función miembro.

El ejemplo siguiente muestra cómo almacenar una variable de punto flotante (`f`) al archivo `ar`:

```
ar.Write(&f, sizeof( float ));
```