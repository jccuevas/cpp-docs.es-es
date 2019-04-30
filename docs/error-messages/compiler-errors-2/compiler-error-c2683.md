---
title: Error del compilador C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 49e4897ad5db866aa1ca42589859bedff12718df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266873"
---
# <a name="compiler-error-c2683"></a>Error del compilador C2683

'cast': 'type' no es un tipo polimórfico

No puede usar [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir de una clase que no es polimórfico (una clase sin funciones virtuales).

Puede usar [static_cast](../../cpp/static-cast-operator.md) para realizar las conversiones de tipos no polimórficos. Sin embargo, `static_cast` no lleva a cabo una comprobación en tiempo de ejecución.

El ejemplo siguiente genera C2683:

```
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```