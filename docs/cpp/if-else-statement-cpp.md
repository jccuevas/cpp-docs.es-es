---
title: "if-else (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "else_cpp"
  - "else"
  - "if_cpp"
  - "if"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "else (palabra clave) [C++]"
  - "if (palabra clave) [C++]"
  - "if (palabra clave) [C++], if-else"
ms.assetid: f8c45cde-6bce-42ae-81db-426b3dbd4caa
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# if-else (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Controla la bifurcación condicional.  
  
## Sintaxis  
  
```  
  
      if ( expression )  
   statement1  
[else  
   statement2]  
```  
  
## Comentarios  
 Si el valor de *expression* es distinto de cero, se ejecuta *statement1*.  Si la cláusula **else** opcional está presente, se ejecuta *statement2* si el valor de *expression* es cero.  *expression* debe ser de tipo aritmético o puntero, o debe ser de un tipo de clase que defina una conversión no ambigua a un tipo aritmético o puntero. \(Para obtener más información sobre las conversiones, vea [Conversiones estándar](../cpp/standard-conversions.md)\).  
  
 En ambos formatos de la instrucción **if**, se evalúa *expression*, que puede tener cualquier valor excepto una estructura, incluidos todos los efectos secundarios.  El control pasa de la instrucción **if** a la siguiente instrucción del programa a menos que una de las *statement* contenga [break](../cpp/break-statement-cpp.md), [continue](../cpp/continue-statement-cpp.md) o [goto](../cpp/goto-statement-cpp.md).  
  
 La cláusula **else** de una instrucción `if...else` está asociada a la instrucción **if** anterior más cercana del mismo ámbito que no tenga una instrucción **else** correspondiente.  
  
 Para que este ejemplo no sea ambiguo con respecto al emparejamiento de `if...else`, quite las marcas de comentario de las llaves.  
  
## Ejemplo  
  
```  
// if_else_statement.cpp  
#include <stdio.h>  
  
int main()   
{  
   int x = 0;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n");  
   }  
   else  
   {  
      printf_s("x is not 0!\n"); // this statement will not be executed  
   }  
  
   x = 1;  
   if (x == 0)  
   {  
      printf_s("x is 0!\n"); // this statement will not be executed  
   }  
   else  
   {  
      printf_s("x is not 0!\n");  
   }  
  
   return 0;  
}  
```  
  
  **x is 0\!**  
**x is not 0\!**   
## Vea también  
 [Instrucciones de selección](../cpp/selection-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [switch \(Instrucción\) \(C\+\+\)](../cpp/switch-statement-cpp.md)