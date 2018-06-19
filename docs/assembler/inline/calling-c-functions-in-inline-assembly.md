---
title: Las funciones que realiza la llamada C en código ensamblador en línea | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c3f6d03ba77c7a4cdb3478a1bfe8729019dea002
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32049523"
---
# <a name="calling-c-functions-in-inline-assembly"></a>Llamada a funciones C en el ensamblado alineado
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Un bloque `__asm` puede llamar a las funciones de C, incluidas las rutinas de la biblioteca de C. El ejemplo siguiente llama a la rutina de biblioteca `printf`:  
  
```  
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
  
```  
printf( format, hello, world );  
```  
  
 el ejemplo inserta punteros a `world`, `hello` y `format`, en ese orden, y después llama a `printf`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Ensamblador insertado](../../assembler/inline/inline-assembler.md)