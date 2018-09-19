---
title: Funciones de C que realiza la llamada en el ensamblado alineado | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a080c05aee58a2e6ffae17d14e99c66922aa1f17
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686692"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C en el ensamblado alineado

**Específicos de Microsoft**

Un bloque `__asm` puede llamar a las funciones de C, incluidas las rutinas de la biblioteca de C. El ejemplo siguiente llama a la rutina de biblioteca `printf`:

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

Dado que los argumentos de la función se pasan en la pila, inserte simplemente los argumentos necesarios (los punteros de cadena en el ejemplo anterior) antes de llamar a la función. Los argumentos se insertan en el orden inverso, de modo que dejan la pila en el orden deseado. Para emular la instrucción de C

```cpp
printf( format, hello, world );
```

el ejemplo inserta punteros a `world`, `hello` y `format`, en ese orden, y después llama a `printf`.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Ensamblador insertado](../../assembler/inline/inline-assembler.md)<br/>