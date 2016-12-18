---
title: "return (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "return"
  - "return_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "return (palabra clave) [C++]"
  - "return (palabra clave) [C++], sintaxis"
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# return (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Finaliza la ejecución de una función y devuelve el control a la función de llamada \(o al sistema operativo si se transfiere el control de la función `main`\).  La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada.  
  
## Sintaxis  
  
```  
return [expression];  
```  
  
## Comentarios  
 La cláusula `expression`, si está presente, se convierte al tipo especificado en la declaración de función, como si se realizara una inicialización.  La conversión del tipo de la expresión al tipo `return` de la función puede crear objetos temporales.  Para obtener más información sobre cómo y cuándo se crean los elementos temporales, vea [Objetos temporales](../cpp/temporary-objects.md).  
  
 El valor de la cláusula `expression` se devuelve a la función de llamada.  Si se omite la expresión, el valor devuelto de la función es indefinido.  Los constructores y destructores, y las funciones de tipo `void`, `` no pueden especificar una expresión en la instrucción `return`.  Las funciones de todos los demás tipos deben especificar una expresión en la instrucción `return`.  
  
 Cuando el flujo de control sale del bloque que incluye la definición de función, el resultado es el mismo que si se hubiera ejecutado una instrucción `return` sin una expresión.  Esto no es válido para las funciones que se declaran como si devolvieran un valor.  
  
 Una función puede tener cualquier número de instrucciones `return`.  
  
 En el ejemplo siguiente se utiliza una expresión con una instrucción `return` para obtener el mayor de dos enteros.  
  
## Ejemplo  
  
```  
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## Vea también  
 [Instrucciones de salto](../cpp/jump-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)