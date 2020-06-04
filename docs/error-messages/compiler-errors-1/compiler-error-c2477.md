---
title: Error del compilador C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743658"
---
# <a name="compiler-error-c2477"></a>Error del compilador C2477

' Member ': no se puede inicializar un miembro de datos estático mediante una clase derivada

Un miembro de datos estático de una clase de plantilla se inicializó incorrectamente. Se trata de un cambio importante con las versiones del C++ compilador de Microsoft anteriores a Visual Studio .NET 2003, con el fin C++ de ajustarse al estándar ISO.

En el ejemplo siguiente se genera C2477:

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
