---
title: Compilador advertencia (nivel 1) C4731 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4731
dev_langs:
- C++
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75117b34e63694cfa6aeec97abf178ff8e61a7da
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086491"
---
# <a name="compiler-warning-level-1-c4731"></a>Advertencia del compilador (nivel 1) C4731

'pointer': 'registro' modificado por código ensamblador en línea de registro de puntero de marco

Se modificó un registro de puntero de marco. Debe guardar y restaurar el registro en la variable en línea ensamblado bloque o de marco (local o un parámetro, según el registro modificado), o el código no funcionen correctamente.

El ejemplo siguiente genera C4731:

```
// C4731.cpp
// compile with: /W1 /LD
// processor: x86
// C4731 expected
void bad(int p) {
   __asm
   {
      mov ebp, 1
   }

   if (p == 1)
   {
      // ...
   }
}
```

EBP es el puntero de marco (FPO no permitido) y se está modificando. Cuando `p` es posterior al que hace referencia, se hace referencia relativa a `EBP`. Pero `EBP` se ha sobrescrito por el código, por lo que el programa no funcionará correctamente e incluso puede producir un error.