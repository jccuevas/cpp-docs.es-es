---
title: "do-while (instrucci&#243;n de C++) | Microsoft Docs"
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
  - "do-while_cpp"
  - "do-while"
  - "do"
  - "while_cpp"
  - "do_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "do (palabra clave) [C++]"
  - "do (palabra clave) [C++], do-while"
  - "do-while (palabra clave) [C++]"
  - "while (palabra clave) [C++], do-while"
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# do-while (instrucci&#243;n de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ejecuta un elemento *statement* repetidamente veces hasta que la condición de finalización \(*expression*\) se evalúa como cero.  
  
## Sintaxis  
  
```  
  
      do  
   statement  
   while ( expression ) ;  
```  
  
## Comentarios  
 La prueba de la condición de finalización se realiza después de cada ejecución del bucle; por consiguiente, un bucle `do-while` se ejecuta una o más veces, dependiendo del valor de la expresión de finalización.  La instrucción `do-while` también puede finalizar cuando se ejecuta una instrucción [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) o [return](../cpp/return-statement-cpp.md) dentro del cuerpo de la instrucción.  
  
 *expression* debe tener un tipo aritmético o de puntero.  La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta el cuerpo de instrucción.  
  
2.  A continuación, se evalúa *expression*.  Si *expression* es false, la instrucción `do-while` finaliza y el control pasa a la siguiente instrucción del programa.  Si *expression* es true \(distinta de cero\), el proceso se repite a partir del paso 1.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra la instrucción `do-while`:  
  
```  
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## Vea también  
 [Instrucciones de iteración](../cpp/iteration-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [while \(Instrucción\) \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [for \(Instrucción\) \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)