---
title: Error del compilador C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 44f7988f9fedb882972b2823f2fe70d9512d4e87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484791"
---
# <a name="compiler-error-c2801"></a>Error del compilador C2801

'operator operator' debe ser un miembro no estático

Únicamente como miembros no estáticos se pueden sobrecargar los operadores siguientes:

- Asignación `=`

- Acceso a miembros de clase `->`

- Subíndices `[]`

- Llamada de función `()`

Posibles causas de C2801:

- Operador sobrecargado no es una clase, estructura o miembro de unión.

- Operador sobrecargado se declara `static`.

- El ejemplo siguiente genera C2801:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```