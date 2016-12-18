---
title: "Operador coma: , | Microsoft Docs"
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
  - "%2C"
  - ","
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "coma (operador)"
ms.assetid: 38e0238e-19da-42ba-ae62-277bfdab6090
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador coma: ,
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Permite agrupar dos instrucciones donde se espera una.  
  
## Sintaxis  
  
```  
  
expression , expression  
```  
  
## Comentarios  
 El operador de comas tiene asociatividad de izquierda a derecha.  Dos expresiones separadas por una coma se evalúan de izquierda a derecha.  El operando izquierdo se evalúa siempre, y todos los efectos secundarios se completan antes de que se evalúe el operando derecho.  
  
 Las comas se pueden utilizar como separadores en algunos contextos, como las listas de argumentos de función.  No confunda el uso de la coma como separador y como operador; los dos usos son completamente diferentes.  
  
 Considere la expresión  
  
 *e1* , *e2*  
  
 El tipo y el valor de la expresión son el tipo y el valor de *e2*; el resultado de evaluar *e1* se descarta.  El resultado es un valor L si el operando derecho es un valor L.  
  
 En los contextos en los que normalmente se utiliza la coma como separador \(por ejemplo, en argumentos reales para funciones o inicializadores de agregado\), el operador de la coma y sus operandos deben incluirse entre paréntesis.  Por ejemplo:  
  
```  
func_one( x, y + 2, z );  
func_two( (x--, y + 2), z );  
```  
  
 En la llamada de función a `func_one` de la parte superior, se pasan tres argumentos separados por comas: `x`, `y + 2` y `z`.  En la llamada de función a `func_two`, los paréntesis hacen que el compilador interprete la primera coma como el operador de evaluación secuencial.  Esta llamada a función pasa dos argumentos a `func_two`.  El primer argumento es el resultado de la operación de evaluación secuencial `(x--, y + 2)`, que tiene el valor y tipo de la expresión `y + 2`; el segundo argumento es `z`.  
  
## Ejemplo  
  
```  
// cpp_comma_operator.cpp  
#include <stdio.h>  
int main () {  
   int i = 10, b = 20, c= 30;  
   i = b, c;  
   printf("%i\n", i);  
  
   i = (b, c);  
   printf("%i\n", i);  
}  
```  
  
  **20**  
**30**   
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operador de evaluación secuencial](../c-language/sequential-evaluation-operator.md)