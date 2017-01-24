---
title: "Llamar a funciones de C en ensamblados alineados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], llamar a funciones"
  - "llamadas a funciones, funciones de C"
  - "llamadas a funciones, en ensamblado alineado"
  - "funciones [C], llamar en ensamblado alineado"
  - "ensamblado en línea, llamar a funciones"
  - "Visual C, funciones"
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Llamar a funciones de C en ensamblados alineados
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Un bloque `__asm` puede llamar a las funciones de C, incluidas las rutinas de la biblioteca de C.  El ejemplo siguiente llama a la rutina de biblioteca `printf`:  
  
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
  
 Dado que los argumentos de la función se pasan en la pila, inserte simplemente los argumentos necesarios \(los punteros de cadena en el ejemplo anterior\) antes de llamar a la función.  Los argumentos se insertan en el orden inverso, de modo que dejan la pila en el orden deseado.  Para emular la instrucción de C  
  
```  
printf( format, hello, world );  
```  
  
 el ejemplo inserta punteros a `world`, `hello` y `format`, en ese orden, y después llama a `printf`.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)