---
title: Error del compilador C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760678"
---
# <a name="compiler-error-c2801"></a>Error del compilador C2801

' operator Operator ' debe ser un miembro no estático

Los operadores siguientes solo se pueden sobrecargar como miembros no estáticos:

- `=` de asignación

- `->` de acceso a miembros de clase

- `[]` de subíndice

- `()` de llamada de función

Posibles causas de C2801:

- El operador sobrecargado no es un miembro de clase, estructura o Unión.

- El operador sobrecargado se declara `static`.

- En el ejemplo siguiente se genera C2801:

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
