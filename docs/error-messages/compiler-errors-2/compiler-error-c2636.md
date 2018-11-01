---
title: Error del compilador C2636
ms.date: 11/04/2016
f1_keywords:
- C2636
helpviewer_keywords:
- C2636
ms.assetid: 379873ec-8d05-49f8-adf1-b067bc07bdb8
ms.openlocfilehash: f196058bf458cf0732e3a19b98df366eb046e93a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644887"
---
# <a name="compiler-error-c2636"></a>Error del compilador C2636

'identifier': puntero a miembro de referencia no es válido

Se ha declarado un puntero a un miembro de referencia.

El ejemplo siguiente genera C2636:

```
// C2636.cpp
struct S {};
int main() {
   int &S::*prs;   // C2636
   int S::*prs1;   // OK
   int *S::*prs2;   // OK
}
```