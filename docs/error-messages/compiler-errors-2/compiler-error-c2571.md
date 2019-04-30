---
title: Error del compilador C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: d7d4898e5f0b55c50a4c18cef053cc150394d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408587"
---
# <a name="compiler-error-c2571"></a>Error del compilador C2571

'function': función virtual no puede estar en la unión "union"

Se declara una unión con una función virtual. Puede declarar una función virtual solo en una clase o estructura.  Soluciones posibles:

1. Cambie la unión a una clase o estructura.

1. Hacer que la función no virtual.

El ejemplo siguiente genera C2571:

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```