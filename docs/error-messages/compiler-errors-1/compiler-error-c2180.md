---
title: Error del compilador C2180 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2180
dev_langs:
- C++
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c74912b92162cbfcada3630ed6a6845b67045d0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084151"
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