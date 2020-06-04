---
title: Error del compilador C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: cc871467e1e3fb23edc6231c3adb182f5e26c0d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760249"
---
# <a name="compiler-error-c2688"></a>Error del compilador C2688

' C2:: fgrv ': las devoluciones covariantes con Multiple o la herencia virtual no se admiten para las funciones varargs

Los tipos de valor devueltos covariantes no se admiten en Visual C++ cuando una función contiene argumentos variables.

Para resolver este error, defina las funciones de modo que no usen argumentos de variable o que los valores devueltos sean los mismos para todas las funciones virtuales.

En el ejemplo siguiente se genera C2688:

```cpp
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```
