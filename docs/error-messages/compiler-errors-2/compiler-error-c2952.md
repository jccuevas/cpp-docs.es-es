---
title: Error del compilador C2952
ms.date: 11/04/2016
f1_keywords:
- C2952
helpviewer_keywords:
- C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
ms.openlocfilehash: 9a76fc1718941ec5043f14064fa8c2609829ede3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755972"
---
# <a name="compiler-error-c2952"></a>Error del compilador C2952

'declaration': falta la lista de parámetros de la declaración de tipo

Una declaración de plantilla está mal formada.

El ejemplo siguiente genera la advertencia C2952:

```cpp
// C2952.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1 {
      void f();
   };
};

template <class T> void S<T>::S1<T>::f() {}   // C2952

// OK
template <class T>
template <class T1>
void S<T>::S1<T1>::f() {}
```

También se puede producir el error C2952 al usar genéricos:

```cpp
// C2952b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC {
   generic <class T1>
   ref struct GC1 {
      void f();
   };
};

generic <class T> void GC<T>::GC1<T>::f() {}   // C2952

// OK
generic <class T>
generic <class T1>
void GC<T>::GC1<T1>::f() {}
```
