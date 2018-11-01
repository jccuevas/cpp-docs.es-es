---
title: Error del compilador C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: 5355abc603726eb1bacb7a22fa1095bf2d81c538
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588557"
---
# <a name="compiler-error-c2688"></a>Error del compilador C2688

'C2:: fgrv': con varios valores devueltos de covariante o herencia virtual no es compatible con funciones varargs

No se admiten los tipos de valor devuelto covariante en Visual C++ cuando una función contiene argumentos de variable.

Para resolver este error, defina las funciones para que no utilizan argumentos de variable o hacer que los valores devueltos el mismo para todas las funciones virtuales.

El ejemplo siguiente genera C2688:

```
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