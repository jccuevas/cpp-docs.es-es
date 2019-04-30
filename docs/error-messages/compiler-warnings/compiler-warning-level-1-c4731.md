---
title: Advertencia del compilador (nivel 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: af091d1d35fff955afcc5af3da48b80416e79f36
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385438"
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