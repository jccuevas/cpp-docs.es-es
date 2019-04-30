---
title: Error del compilador C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: b7bdd10ebd70eb61746690958532854dd98c6429
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228595"
---
# <a name="compiler-error-c2597"></a>Error del compilador C2597

referencia no válida a miembro no estático 'identifier'

Causas posibles:

1. Se especifica un miembro no estático en una función de miembro estático. Para tener acceso al miembro no estático, debe pasar o crear una instancia local de la clase y usar un operador de acceso a miembros (`.` o `->`).

1. El identificador especificado no es miembro de una clase, estructura o unión. Revisar la ortografía del identificador.

1. Un operador de acceso a miembros hace referencia a una función no miembro.

1. El ejemplo siguiente genera el error C2597 y muestra cómo corregirlo:

```
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```