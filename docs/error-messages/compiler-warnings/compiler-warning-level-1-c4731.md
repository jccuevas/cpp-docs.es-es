---
title: ADVERTENCIA del compilador (nivel 1) C4731
ms.date: 11/04/2016
f1_keywords:
- C4731
helpviewer_keywords:
- C4731
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
ms.openlocfilehash: b2591756dfaa8887affbe4e470f1c98738b6b680
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052425"
---
# <a name="compiler-warning-level-1-c4731"></a>ADVERTENCIA del compilador (nivel 1) C4731

' Pointer ': el registro de puntero de marco ' Register ' modificado por el código de ensamblado alineado

Se modificó un registro de puntero de marco. Debe guardar y restaurar el registro en el bloque de ensamblado insertado o en la variable de marco (local o de parámetro, en función del registro modificado) o es posible que el código no funcione correctamente.

En el ejemplo siguiente se genera C4731:

```cpp
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

EBP es el puntero de marco (no se permite el FPO) y se está modificando. Cuando se hace referencia a `p` posteriormente, se hace referencia a él en relación con `EBP`. Pero el código ha sobrescrito `EBP`, por lo que el programa no funcionará correctamente y puede incluso que se produzca un error.