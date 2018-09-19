---
title: Error del compilador C2231 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2231
dev_langs:
- C++
helpviewer_keywords:
- C2231
ms.assetid: 677c5c66-d30f-4c3b-bbb9-760858d56477
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd6cd35d20f4ce0377aa5ae5cd66cd8c08004fb8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021686"
---
# <a name="compiler-error-c2231"></a>Error del compilador C2231

'.': operando izquierdo señala a 'class-key', use '->'

El operando situado a la izquierda de la operación de selección de miembro (.) es un puntero en lugar de una clase, estructura o unión.

El ejemplo siguiente genera la advertencia C2231:

```
// C2231.c
struct S {
   int member;
} s, *ps = &s;
int main() {
   ps.member = 0;   // C2231

   // OK
   ps->member = 0;   // crash
   s.member = 0;
}
```