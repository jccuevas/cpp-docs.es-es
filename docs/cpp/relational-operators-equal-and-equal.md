---
title: "Operadores relacionales: &lt;, &gt;, &lt;= y &gt;= | Microsoft Docs"
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
  - "<"
  - ">"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "< (operador)"
  - "<= (operador)"
  - "> (operador)"
  - ">= (operador)"
  - "operadores mayor que"
  - "operadores mayor o igual que"
  - "operador menor que"
  - "operador menor o igual que"
  - "operadores relacionales, sintaxis"
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores relacionales: &lt;, &gt;, &lt;= y &gt;=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
        expression < expression  
expression > expression  
expression <= expression  
expression >= expression  
```  
  
## Comentarios  
 Los operadores relacionales binarios determinan las relaciones siguientes:  
  
-   Menor que \(**\<**\)  
  
-   Mayor que \(**\>**\)  
  
-   Menor o igual que \(**\<\=**\)  
  
-   Mayor o igual que \(**\>\=**\)  
  
 Los operadores relacionales tienen asociatividad de izquierda a derecha.  Ambos operandos de los operadores relacionales deben ser de tipo aritmética o puntero.  Producen valores de tipo `bool`.  El valor devuelto es **false** \(0\) si la relación de la expresión es falsa; si no, el valor devuelto es **true** \(1\).  
  
## Ejemplo  
  
```  
// expre_Relational_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << "The true expression 3 > 2 yields: "  
         << (3 > 2) << endl  
         << "The false expression 20 < 10 yields: "  
         << (20 < 10) << endl;  
}  
```  
  
 Las expresiones del ejemplo anterior se deben incluir entre paréntesis porque el operador de inserción de la secuencia \(**\<\<**\) tiene mayor prioridad que los operadores relacionales.  Por consiguiente, la primera expresión sin paréntesis se evaluaría como:  
  
```  
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");  
```  
  
 Las conversiones aritméticas habituales tratadas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos de tipos aritméticos.  
  
## Comparar punteros  
 Cuando se comparan dos punteros a objetos del mismo tipo, el resultado está determinado por la ubicación de los objetos a los que se señala en el espacio de direcciones del programa.  Los punteros también se pueden comparar con una expresión de constante que se evalúa como 0 o con un puntero de tipo void \*.  Si una comparación de puntero se realiza frente a un puntero de tipo void \*, el otro puntero se convierte implícitamente al tipo void \*.  A continuación, se realiza la comparación.  
  
 Dos punteros de tipos diferentes no pueden compararse a menos que:  
  
-   Un tipo sea un tipo de clase derivado del otro tipo.  
  
-   Al menos uno de los punteros se convierta explícitamente \(conversión\) al tipo void \*.  \(El otro puntero se convierte implícitamente al tipo void \* para la conversión\).  
  
 Se garantiza que dos punteros del mismo tipo que señalan al mismo objeto realizan una comparación igual.  Si se comparan dos punteros a miembros no estáticos de un objeto, se aplican las reglas siguientes:  
  
-   Si el tipo de clase no es una unión y si los dos miembros no se separan mediante un especificador de acceso \(*access\-specifier*\), como public, protected o private, el puntero al miembro declarado en último lugar realizará una comparación mayor que el puntero al miembro declarado anteriormente.  \(Para obtener información sobre un especificador de acceso \(*access\-specifier*\), vea la sección Sintaxis en [Especificadores de acceso](../misc/access-specifiers.md)\).  
  
-   Si los dos miembros están separados por un especificador de acceso \(*access\-specifier*\), los resultados son indefinidos.  
  
-   Si el tipo de clase es una unión, los punteros a miembros de datos diferentes en esa unión realizan una comparación igual.  
  
 Si dos punteros señalan a elementos de la misma matriz o al elemento uno situado más allá del final de la matriz, el puntero al objeto con el subíndice más alto realiza una comparación superior.  Se garantiza que la comparación de punteros es válida solo cuando los punteros hacen referencia a objetos de la misma matriz o a la ubicación uno superado el final de la matriz.  
  
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores relacionales y de igualdad de C](../c-language/c-relational-and-equality-operators.md)