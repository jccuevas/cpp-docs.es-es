---
title: "goto (Instrucci&#243;n) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "goto_cpp"
  - "goto"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "goto (palabra clave) [C++]"
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# goto (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La instrucción `goto` transfiere incondicionalmente el control a la instrucción etiquetada por el identificador especificado.  
  
## Sintaxis  
  
```  
goto identifier;  
```  
  
## Comentarios  
 La instrucción con etiqueta designada por `identifier` debe estar en la función actual.  Todos los nombres de `identifier` son miembros de un espacio de nombres interno y, por tanto, no interfieren con otros identificadores.  
  
 Una etiqueta de instrucción solo es significativa para una instrucción `goto`; de lo contrario, se omiten las etiquetas de instrucciones.  Las etiquetas no se pueden volver a declarar.  
  
 Un buen estilo de programación consiste en utilizar las instrucciones `break`, `continue` y `return` en lugar de la instrucción `goto` siempre que sea posible.  Sin embargo, puesto que la instrucción `break` sale de un solo nivel de un bucle, puede que tenga que utilizar una instrucción `goto` para salir de un bucle anidado profundamente.  
  
 Para obtener más información sobre las etiquetas y la instrucción `goto`, vea [Instrucciones con etiquetas](../cpp/labeled-statements.md) y [Usar etiquetas con la instrucción goto](http://msdn.microsoft.com/es-es/6cd7c31a-9822-4241-8566-f79f51be48fe).  
  
## Ejemplo  
 En este ejemplo, una instrucción `goto` transfiere el control al punto con la etiqueta `stop` cuando `i` es igual a 3.  
  
```  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
  **Outer loop executing.  i \= 0**  
 **Inner loop executing.  j \= 0**  
 **Inner loop executing.  j \= 1**  
**Outer loop executing.  i \= 1**  
 **Inner loop executing.  j \= 0**  
 **Inner loop executing.  j \= 1**  
**Outer loop executing.  i \= 2**  
 **Inner loop executing.  j \= 0**  
 **Inner loop executing.  j \= 1**  
**Outer loop executing.  i \= 3**  
 **Inner loop executing.  j \= 0**  
**Jumped to stop.  i \= 3**    
## Vea también  
 [Instrucciones de salto](../cpp/jump-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)