---
title: Error del compilador C2153
ms.date: 11/04/2016
f1_keywords:
- C2153
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
ms.openlocfilehash: eeb7da509ffb1b8c408763c79d471586eb94f383
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605938"
---
# <a name="compiler-error-c2153"></a>Error del compilador C2153

las constantes hexadecimales deben tener al menos un dígito hexadecimal

Las constantes hexadecimales 0 x, 0 X y \x no son válidos. Debe seguir al menos un dígito hexadecimal x o X.

El ejemplo siguiente genera C2153:

```
// C2153.cpp
int main() {
   int a= 0x;    // C2153
   int b= 0xA;   // OK
}
```