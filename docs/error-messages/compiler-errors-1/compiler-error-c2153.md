---
title: Error del compilador C2153 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2153
dev_langs:
- C++
helpviewer_keywords:
- C2153
ms.assetid: cfc50cb7-9a0f-4b5b-879a-d419c99f7be1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbb3283ff4d27b6c939434ac3df8f8c1febf0eb3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051430"
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