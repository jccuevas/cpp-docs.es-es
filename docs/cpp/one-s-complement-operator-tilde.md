---
title: "Operador de complemento de uno: ~ | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~ (operador), sintaxis"
  - "bit a bit (operador de complemento)"
  - "compl (operador)"
  - "operador de complemento de uno"
  - "tilde (~) (operador de complemento de uno)"
ms.assetid: 4bf81967-34f7-4b4b-aade-fd03d5da0174
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador de complemento de uno: ~
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
~ cast-expression  
```  
  
## Comentarios  
 El operador de complemento de uno \(`~`\), denominado a veces operador de “complemento bit a bit”, produce un complemento de uno bit a bit de su operando.  Es decir, cada bit que es 1 en el operando es 0 en el resultado.  Y a la inversa: cada bit que es 0 en el operando es 1 en el resultado.  El operando del operador de complemento de uno debe ser de tipo entero.  
  
## Palabra clave del operador para ~  
 El operador `compl` es el equivalente de texto de `~`.  Hay dos maneras de tener acceso al operador `compl` en los programas: incluir el archivo de encabezado `iso646.h` o compilar con [\/Za](../build/reference/za-ze-disable-language-extensions.md).  
  
## Ejemplo  
  
```  
// expre_One_Complement_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main () {  
   unsigned short y = 0xFFFF;  
   cout << hex << y << endl;  
   y = ~y;   // Take one's complement  
   cout << hex << y << endl;  
}  
```  
  
 En este ejemplo, el nuevo valor asignado a `y` es el complemento de uno del valor sin signo 0xFFFF, or 0x0000.  
  
 La promoción de entero se realiza en operandos enteros y el tipo resultante es el tipo al que se promueve el operando.  Vea [Promociones de entero](../misc/integral-promotions.md) para obtener más información sobre cómo se realiza la promoción.  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)