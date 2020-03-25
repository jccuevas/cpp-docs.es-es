---
title: Advertencia del compilador (nivel 1) C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 39674c32deb506725aa5f7c1f5f875e771519938
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185677"
---
# <a name="compiler-warning-level-1-c4733"></a>Advertencia del compilador (nivel 1) C4733

Asignación de ASM en línea a ' FS: 0 ': el controlador no está registrado como controlador seguro

Función que modifica el valor en FS: 0 para agregar un nuevo controlador de excepciones, puede que no funcione con excepciones seguras, ya que el controlador no se puede registrar como un controlador de excepciones válido (vea [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)).

Para resolver esta advertencia, quite el FS: 0 definición o desactive esta advertencia y use [. SAFESEH](../../assembler/masm/dot-safeseh.md) para especificar los controladores de excepciones seguros.

En el ejemplo siguiente se genera C4733:

```cpp
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
