---
title: "while (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "while_cpp"
  - "while"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "while (palabra clave) [C++]"
  - "while (palabra clave) [C++], sintaxis"
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# while (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ejecuta *statement* repetidamente hasta que *expression* se evalúa como cero.  
  
## Sintaxis  
  
```  
  
      while ( expression )  
   statement  
```  
  
## Comentarios  
 La comprobación de *expression* tiene lugar antes de cada ejecución del bucle; por tanto, un bucle `while` se ejecuta cero o más veces.  *expression* debe ser de tipo entero, un tipo de puntero o un tipo de clase con una conversión no ambigua a un tipo entero o de puntero.  
  
 Un bucle `while` también puede finalizar cuando se ejecuta [break](../cpp/break-statement-cpp.md), [goto](../cpp/goto-statement-cpp.md) o [return](../cpp/return-statement-cpp.md) dentro del cuerpo de instrucción.  Utilice [continue](../cpp/continue-statement-cpp.md) para finalizar la iteración actual sin salir del bucle `while`.  **continue** pasa el control a la siguiente iteración del bucle `while`.  
  
 En el código siguiente se utiliza un bucle `while` para recortar los caracteres de subrayado finales de una cadena:  
  
```  
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 La condición de finalización se evalúa al principio del bucle.  Si no hay ningún carácter de subrayado final, el bucle nunca se ejecuta.  
  
## Vea también  
 [Instrucciones de iteración](../cpp/iteration-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [do\-while \(instrucción de C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [for \(Instrucción\) \(C\+\+\)](../cpp/for-statement-cpp.md)   
 [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)