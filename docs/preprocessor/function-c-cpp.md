---
title: "function (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "function_CPP"
  - "vc-pragma.function"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "function (pragma)"
  - "pragma (directivas), función"
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# function (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que se generen llamadas a funciones especificadas en la lista de argumentos de pragma.  
  
## Sintaxis  
  
```  
  
#pragma function( function1 [, function2, ...] )  
```  
  
## Comentarios  
 Si utiliza la directiva pragma **intrinsic** \(u \/Oi\) para indicar al compilador que genere funciones intrínsecas \(las funciones intrínsecas se generan como código alineado, no como llamadas de función\), puede utilizar la directiva pragma **function** para forzar explícitamente una llamada de función.  Una vez vista una directiva pragma function, se aplica a la primera definición de función que contenga una función intrínseca especificada.  El efecto continúa hasta el final del archivo de código fuente o hasta la aparición de una directiva pragma **intrinsic** que especifique la misma función intrínseca.  La directiva pragma **function** solo se puede usar fuera de una función, en el nivel global.  
  
 Para ver listas de funciones que tienen formas intrínsecas, vea [\#pragma intrinsic](../preprocessor/intrinsic.md).  
  
## Ejemplo  
  
```  
// pragma_directive_function.cpp  
#include <ctype.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
  
// use intrinsic forms of memset and strlen  
#pragma intrinsic(memset, strlen)  
  
// Find first word break in string, and set remaining  
// chars in string to specified char value.  
char *set_str_after_word(char *string, char ch) {  
   int i;  
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */  
  
   for(i = 0; i < len; i++) {  
      if (isspace(*(string + i)))   
         break;  
   }  
  
   for(; i < len; i++)   
      *(string + i) = ch;  
  
   return string;  
}  
  
// do not use strlen intrinsic  
#pragma function(strlen)  
  
// Set all chars in string to specified char value.  
char *set_str(char *string, char ch) {  
   // Uses intrinsic for memset, but calls strlen library function  
   return (char *) memset(string, ch, strlen(string));  
}  
  
int main() {  
   char *str = (char *) malloc(20 * sizeof(char));  
  
   strcpy_s(str, sizeof("Now is the time"), "Now is the time");  
   printf("str is '%s'\n", set_str_after_word(str, '*'));  
   printf("str is '%s'\n", set_str(str, '!'));  
}  
```  
  
  **str es "Now\*\*\*\*\*\*\*\*\*\*\*\*"**  
**str es "\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!"**   
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)