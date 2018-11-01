---
title: Error del compilador C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: f643b7d8c035b4d1d7d8806feb5b121cf76d7796
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651920"
---
# <a name="compiler-error-c2698"></a>Error del compilador C2698

la declaración using para ' declaración 1' no puede coexistir con la declaración using existente de ' declaración 2'

Una vez que tenga un [mediante declaración](../../cpp/using-declaration.md) para un miembro de datos, cualquier uso no se permite la declaración en el mismo ámbito que utiliza el mismo nombre, como funciones solo se pueden sobrecargar.

El ejemplo siguiente genera C2698:

```
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