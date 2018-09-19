---
title: Error del compilador C2597 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9f8deb325ae54393518698263f3ca93ca88ca48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114454"
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