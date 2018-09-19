---
title: Error del compilador C3160 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf3ecc18e1afc9b13e47ad8b20bb92f7686d0cfc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042278"
---
# <a name="compiler-error-c3160"></a>Error del compilador C3160

'pointer': un miembro de datos de una clase administrada o WinRT no puede ser de este tipo

Los punteros interiores de recolección de elementos no utilizados pueden apuntar al interior de una clase administrada o WinRT. Ya que son más lentos que los punteros de objetos completos y requieren un tratamiento especial por parte del recolector de elementos no utilizados, no puede declarar punteros interiores administrados como miembros de una clase.

El ejemplo siguiente genera el error C3160:

```
// C3160.cpp
// compile with: /clr
ref struct A {
   // cannot create interior pointers inside a class
   interior_ptr<int> pg;   // C3160
   int g;   // OK
   int* pg2;   // OK
};

int main() {
   interior_ptr<int> pg2;   // OK
}
```
