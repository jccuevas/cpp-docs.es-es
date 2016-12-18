---
title: "Operador de direccionamiento indirecto: * | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "* (operador)"
  - "operador de direccionamiento indirecto"
  - "operador de direccionamiento indirecto, sintaxis"
  - "operadores [C++], direccionamiento indirecto"
ms.assetid: c50309e1-6c02-4184-9fcb-2e13c1f4ac03
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador de direccionamiento indirecto: *
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
* cast-expression  
```  
  
## Comentarios  
 El operador de direccionamiento indirecto unario \(**\***\) desreferencia un puntero; es decir, convierte un valor de puntero en un valor L.  El operando del operador de direccionamiento indirecto debe ser un puntero a un tipo.  El resultado de la expresión de direccionamiento indirecto es el tipo del que se deriva el tipo de puntero.  El uso del operador **\*** en este contexto es diferente de su significado como operador binario, que es multiplicación.  
  
 Si el operando señala a una función, el resultado es un designador de función.  Si señala a una ubicación de almacenamiento, el resultado es un valor L que designa la ubicación de almacenamiento.  
  
 El operador de direccionamiento indirecto se puede utilizar de manera acumulativa para desreferenciar punteros a punteros.  Por ejemplo:  
  
```  
// expre_Indirection_Operator.cpp  
// compile with: /EHsc  
// Demonstrate indirection operator  
#include <iostream>  
using namespace std;  
int main() {  
   int n = 5;  
   int *pn = &n;  
   int **ppn = &pn;  
  
   cout  << "Value of n:\n"  
         << "direct value: " << n << endl  
         << "indirect value: " << *pn << endl  
         << "doubly indirect value: " << **ppn << endl  
         << "address of n: " << pn << endl  
         << "address of n via indirection: " << *ppn << endl;  
}  
```  
  
 Si el valor de puntero no es válido, el resultado es indefinido.  La lista siguiente incluye algunas de las condiciones más comunes que invalidan un valor de puntero.  
  
-   El puntero es un puntero null.  
  
-   El puntero especifica la dirección de un elemento local que no está visible en el momento de la referencia.  
  
-   El puntero especifica una dirección que está alineada de una forma no adecuada para el tipo de objeto al que se señala.  
  
-   El puntero especifica una dirección no utilizada por el programa que se ejecuta.  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operador address\-of: &](../cpp/address-of-operator-amp.md)   
 [Operadores de direccionamiento indirecto y address\-of](../c-language/indirection-and-address-of-operators.md)