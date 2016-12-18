---
title: "Operador condicional: ? : | Microsoft Docs"
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
  - "?:"
  - "?"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "? : (operador)"
  - "operadores condicionales"
ms.assetid: 88643ee8-7100-4f86-880a-705ec22b6271
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador condicional: ? :
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
expression ? expression : expression  
```  
  
## Comentarios  
 El operador condicional \(**? :**\) es un operador ternario \(toma tres operandos\).  El operador condicional funciona del modo siguiente:  
  
-   El primer operando se convierte implícitamente a `bool`.  Se evalúa y todos los efectos secundarios se completan antes de continuar.  
  
-   Si el primer operando se evalúa como **true** \(1\), se evalúa el segundo operando.  
  
-   Si el primer operando se evalúa como **false** \(0\), se evalúa el tercer operando.  
  
 El resultado del operador condicional es el resultado de cualquier operando que se evalúe, el segundo o el tercero.  Solo uno de los dos últimos operandos se evalúa en una expresión condicional.  
  
 Las expresiones condicionales tienen asociatividad de derecha a izquierda.  El primer operando debe ser de tipo entero o de tipo de puntero.  Las reglas siguientes se aplican a los operandos segundo y tercero:  
  
-   Si ambos operandos son del mismo tipo, el resultado es de ese tipo.  
  
-   Si ambos operandos son de tipos de aritmética o de enumeración, se realizan las conversiones aritméticas habituales \(que se describen en [Conversiones aritméticas](../misc/arithmetic-conversions.md)\) para convertirlos a un tipo común.  
  
-   Si ambos operandos son de tipos de puntero o si uno es de un tipo de puntero y el otro es una expresión de constante que se evalúa como 0, las conversiones de puntero se realizan para convertirlos a un tipo común.  
  
-   Si ambos operandos son de tipos de referencia, las conversiones de referencia se realizan para convertirlos a un tipo común.  
  
-   Si ambos operandos son de tipo void, el tipo común es el tipo void.  
  
-   Si ambos operandos son del mismo tipo definido por el usuario, el tipo común es ese tipo.  
  
-   Si los operandos son de tipos diferentes y al menos uno de ellos tiene un tipo definido por el usuario, se usan reglas de lenguaje para determinar el tipo común.  \(Vea la advertencia más adelante\).  
  
 Las combinaciones de los operandos segundo y tercero no incluidos en la lista anterior no son válidas.  El tipo del resultado es el tipo común, y es un valor L si tanto el segundo como el tercer operando son del mismo tipo y ambos son valores l.  
  
> [!WARNING]
>  Si los tipos de los operandos segundo y tercero no son idénticos, se invocan reglas de conversión de tipo complejo, como se especifica en el estándar de C\+\+.  Estas conversiones pueden provocar un comportamiento inesperado, incluida la creación y destrucción de objetos temporales.  Por esta razón, recomendamos encarecidamente \(1\) evitar el uso de tipos definidos por el usuario como operandos con el operador condicional, o \(2\) si utiliza tipos definidos por el usuario, convertir explícitamente cada operando a un tipo común.  
  
## Ejemplo  
  
```  
// expre_Expressions_with_the_Conditional_Operator.cpp  
// compile with: /EHsc  
// Demonstrate conditional operator  
#include <iostream>  
using namespace std;  
int main() {  
   int i = 1, j = 2;  
   cout << ( i > j ? i : j ) << " is greater." << endl;  
}  
```  
  
## Vea también  
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operador de expresión condicional](../c-language/conditional-expression-operator.md)