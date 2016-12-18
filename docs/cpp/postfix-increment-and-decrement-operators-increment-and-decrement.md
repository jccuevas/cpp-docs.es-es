---
title: "Operadores de incremento y decremento postfijos: ++ y -- | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "-- (operador), operadores de decremento postfijos"
  - "++ (operador), operadores de incremento postfijos"
  - "operadores de decremento"
  - "operadores de decremento, sintaxis"
  - "operadores de incremento, sintaxis"
  - "operadores de selección de miembros"
  - "operadores [C++], postfijo"
  - "operadores postfijos"
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de incremento y decremento postfijos: ++ y --
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
      postfix-expression   
      ++  
postfix-expression ––  
```  
  
## Comentarios  
 C\+\+ proporciona operadores de incremento y decremento tanto de prefijo como de postfijo. En esta sección, se describen solo los de postfijo. \(Para obtener más información, vea [Operadores de incremento y decremento de prefijo](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)\). La diferencia entre los dos es que, en la notación de postfijo, el operador aparece después de el elemento *postfix\-expression*, mientras que, en la notación de prefijo, el operador aparece antes de *expression*. En el ejemplo siguiente, se muestra un operador de incremento de postfijo:  
  
```  
i++;  
```  
  
 La aplicación del operador de incremento de postfijo \(`++`\) tiene como efecto que el valor del operando se incrementa en una unidad del tipo adecuado.  De forma similar, la aplicación del operador de decremento de postfijo \(**––**\) tiene como efecto que el valor del operando se reduce en una unidad del tipo adecuado.  
  
 Es importante tener en cuenta que una expresión de incremento o decremento de postfijo se evalúa como el valor de la expresión **antes** de aplicar el operador correspondiente.  La operación de incremento o decremento se produce **después** de que se evalúa el operando.  El problema surge solo cuando la operación de incremento o decremento de postfijo se da en el contexto de una expresión mayor.  
  
 Cuando se aplica un operador de postfijo a un argumento de función, no es seguro que el valor del argumento aumente o disminuya antes de que se pase a la función.  Para obtener más información, vea la sección 1.9.17 del estándar C\+\+.  
  
 Al aplicar el operador de incremento de postfijo a un puntero en una matriz de objetos de tipo **long**, en realidad se agregan cuatro a la representación interna del puntero.  Este comportamiento hace que el puntero, que antes hacía referencia al elemento *n* de la matriz, haga referencia al elemento \(*n*\+1\).  
  
 Los operandos de los operadores de decremento e incremento de postfijo deben ser valores L modificables \(no **const**\) de tipo aritmético o puntero.  El tipo del resultado es el mismo que el de *postfix\-expression*, pero ya no es un valor L.  
  
 El operando de un operador de incremento de postfijo también puede ser de tipo `bool`, en cuyo caso el operando se evalúa y después se establece en **true**.  El operando de un operador de decremento de postfijo no puede ser de tipo `bool`.  
  
 El código siguiente muestra el operador de incremento de postfijo:  
  
```  
// expre_Postfix_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 10;  
   cout << i++ << endl;  
   cout << i << endl;  
}  
```  
  
 No se admiten las operaciones de incremento y decremento de postfijo en los tipos enumerados:  
  
```  
enum Compass { North, South, East, West );  
Compass myCompass;  
for( myCompass = North; myCompass != West; myCompass++ ) // Error  
```  
  
## Vea también  
 [Expresiones postfijas](../cpp/postfix-expressions.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores de incremento y decremento postfijos de C](../c-language/c-postfix-increment-and-decrement-operators.md)