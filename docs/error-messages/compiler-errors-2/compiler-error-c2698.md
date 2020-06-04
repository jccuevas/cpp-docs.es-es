---
title: Error del compilador C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755192"
---
# <a name="compiler-error-c2698"></a>Error del compilador C2698

la declaración Using de ' declaration 1 ' no puede coexistir con la declaración Using existente para ' declaration 2 '

Una vez que tenga una [declaración Using](../../cpp/using-declaration.md) para un miembro de datos, no se permite ninguna declaración Using en el mismo ámbito que use el mismo nombre, ya que solo se pueden sobrecargar las funciones.

En el ejemplo siguiente se genera C2698:

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
