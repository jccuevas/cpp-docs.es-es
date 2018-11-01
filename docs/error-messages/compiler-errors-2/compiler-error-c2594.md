---
title: Error del compilador C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428290"
---
# <a name="compiler-error-c2594"></a>Error del compilador C2594

'operador': conversiones ambiguas de 'tipo1' a 'tipo2'

No hay conversión de *type1* a *type2* es más directa que cualquier otro. Se recomienda dos posibles soluciones para convertir de *type1* a *type2*. La primera opción consiste en definir una conversión directa de *type1* a *type2*, y la segunda opción consiste en especificar una secuencia de conversiones de *type1* a  *tipo2*.

El ejemplo siguiente genera C2594. La solución sugerida para el error es una secuencia de conversiones:

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```