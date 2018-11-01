---
title: Error del compilador C2556
ms.date: 11/04/2016
f1_keywords:
- C2556
helpviewer_keywords:
- C2556
ms.assetid: fc4399ad-45b3-49fd-be1f-0b13956a595a
ms.openlocfilehash: 4a2b4dc9dcd71d518845651dee97c566b778eb0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484154"
---
# <a name="compiler-error-c2556"></a>Error del compilador C2556

'identifier': las funciones sobrecargadas sólo se diferencian por el tipo de valor devuelto

Las funciones sobrecargadas tienen distintos tipos de valor devueltos, pero la misma lista de parámetros. Cada función sobrecargada debe tener una lista de parámetros formales distinta.

El ejemplo siguiente genera C2556:

```
// C2556.cpp
// compile with: /c
class C {
   int func();
   double func();   // C2556
   int func(int i);   // ok parameter lists differ
};
```