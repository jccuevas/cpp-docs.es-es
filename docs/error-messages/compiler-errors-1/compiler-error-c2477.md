---
title: Error del compilador C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: 27db194cb308d711a259127b628c60b4d10b94ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383235"
---
# <a name="compiler-error-c2477"></a>Error del compilador C2477

'member': no se puede inicializar el miembro de datos estático mediante una clase derivada

Un miembro de datos estático de una clase de plantilla se inicializó incorrectamente. Esto es un cambio importante con versiones del compilador de Visual C++ anteriores a Visual Studio .NET 2003, con el fin de cumplir el estándar ISO C++.

El ejemplo siguiente genera C2477:

```
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