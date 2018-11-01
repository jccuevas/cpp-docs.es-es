---
title: Error del compilador C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553327"
---
# <a name="compiler-error-c2180"></a>Error del compilador C2180

la expresión de control es del tipo 'type'

La expresión de control es `if`, `while` o `for`, o la instrucción `do` es una expresión convertida en `void`. Para corregir este problema, cambie la expresión de control por otra que produzca `bool` o un tipo que se pueda convertir en `bool`.

El ejemplo siguiente genera el error C2180:

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```