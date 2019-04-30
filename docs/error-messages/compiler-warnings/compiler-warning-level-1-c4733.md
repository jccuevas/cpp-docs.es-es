---
title: Advertencia del compilador (nivel 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 0d0b0b912ef15294f9a4362a79dffd6d7eeabed8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221120"
---
# <a name="compiler-warning-level-1-c4733"></a>Advertencia del compilador (nivel 1) C4733

Inline asm que asigna a 'FS: 0': controlador no está registrado como controlador seguro

Una función que modifique el valor en FS: 0 para agregar un nuevo controlador de excepción puede no funcionar con las excepciones seguras, porque no se puede registrar el controlador como un controlador de excepciones válido (vea [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Para resolver esta advertencia, quite la definición FS: 0 o desactivar esta advertencia y usar [. SAFESEH](../../assembler/masm/dot-safeseh.md) para especificar los controladores de excepciones seguros.

El ejemplo siguiente genera C4733:

```
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```