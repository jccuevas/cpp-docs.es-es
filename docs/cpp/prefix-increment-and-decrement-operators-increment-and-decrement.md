---
title: "Operadores de incremento y decremento prefijos: ++ y -- | Microsoft Docs"
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
  - "-- (operador), operadores de decremento prefijos"
  - "++ (operador), operadores de incremento prefijos"
  - "operadores de decremento"
  - "operadores de decremento, sintaxis"
  - "operadores de incremento, sintaxis"
  - "operadores [C++], decremento"
  - "operadores [C++], incremento"
ms.assetid: 45ea7fc7-f279-4be9-a216-1d9a0ef9eb7b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de incremento y decremento prefijos: ++ y --
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
++ unary-expression –– unary-expression  
```  
  
## Comentarios  
 El operador de incremento de prefijo \(`++`\) suma uno a su operando; este valor incrementado es el resultado de la expresión.  El operando debe ser un valor L distinto del tipo **const**.  El resultado es un valor L del mismo tipo que el operando.  
  
 El operador de decremento de prefijo \(**––**\) es similar al operador de incremento de prefijo, solo que el operando se reduce en uno y el resultado es este valor disminuido.  
  
 Los operadores de incremento y decremento de prefijo y postfijo afectan a sus operandos.  La principal diferencia entre ellos es el orden en que se realiza el incremento o el decremento al evaluar una expresión.  \(Para obtener más información, vea [Operadores de incremento y decremento postfijos](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)\). En la forma de prefijo, el incremento o decremento tiene lugar antes de que el valor se use en la evaluación de la expresión, por lo que el valor de la expresión es diferente del valor del operando.  En la forma de postfijo, el incremento o decremento tiene lugar después de que el valor se use en la evaluación de la expresión, por lo que el valor de la expresión es el mismo que el valor del operando.  Por ejemplo, el siguiente programa imprime “`++i = 6`”:  
  
```  
// expre_Increment_and_Decrement_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int i = 5;  
   cout << "++i = " << ++i << endl;  
}  
```  
  
 Un operando de tipo entero o flotante aumenta o disminuye en el valor entero 1.  El tipo del resultado es el mismo que el tipo del operando.  Un operando de tipo de puntero aumenta o disminuye en el tamaño del objeto al que apunta.  Un puntero incrementado apunta al siguiente objeto; un puntero disminuido apunta al objeto anterior.  
  
 Como los operadores de incremento y decremento tienen efectos secundarios, el uso de expresiones con operadores de incremento y decremento en una [macro de preprocesador](../preprocessor/macros-c-cpp.md) puede producir resultados no deseados.  Considere este ejemplo:  
  
```  
// expre_Increment_and_Decrement_Operators2.cpp  
#define max(a,b) ((a)<(b))?(b):(a)  
  
int main()  
{  
   int i = 0, j = 0, k;  
   k = max( ++i, j );  
}  
```  
  
 La macro se expande en:  
  
```  
k = ((++i)<(j))?(j):(++i);  
```  
  
 Si `i` es mayor o igual que `j` o es menor que `j` en 1, aumentará dos veces.  
  
> [!NOTE]
>  Las funciones insertadas de C\+\+ son preferibles a las macros en muchos casos porque eliminan los efectos secundarios como los que se describen aquí, y permiten que el lenguaje realice una comprobación de tipos más completa.  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores de incremento y decremento prefijos](../c-language/prefix-increment-and-decrement-operators.md)