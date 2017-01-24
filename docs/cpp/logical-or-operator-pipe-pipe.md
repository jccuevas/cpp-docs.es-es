---
title: "Operador OR l&#243;gico: || | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "|| (operador)"
  - "OR lógico (operador)"
  - "OR (operador)"
  - "OR (operador), lógico"
ms.assetid: 31837c99-2655-4bf3-8ded-f13b7a9dc533
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador OR l&#243;gico: ||
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
logical-or-expression   
||  
 logical-and-expression  
  
```  
  
## Comentarios  
 El operador OR lógico \(`||`\) devuelve el valor booleano **true** si uno o los dos operandos son **true**; en caso contrario, devuelve **false**.  Los operandos se convierten implícitamente al tipo `bool` antes de evaluación, y el resultado es de tipo `bool`.  El operador OR lógico tiene asociatividad de izquierda a derecha.  
  
 Los operandos del operador OR lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero.  Los operandos son normalmente expresiones relacionales o de igualdad.  
  
 El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión OR lógica, se aplican todos los efectos secundarios.  
  
 El segundo operando se evalúa solo si el primero se evalúa como false \(0\).  Esto elimina la evaluación innecesaria del segundo operando cuando la expresión OR lógica es true.  
  
```  
printf( "%d" , (x == w || x == y || x == z) );  
```  
  
 En el ejemplo anterior, si `x` es igual a `w`, `y` o `z`, el segundo argumento de la función `printf` se evalúa como true y se imprime el valor 1.  De lo contrario, se evalúa como false y se imprime el valor 0.  En cuanto una de las condiciones se evalúe como true, se interrumpe la evaluación.  
  
## Palabra clave del operador para &#124;&#124;  
 El operador **or** es el equivalente de texto de `||`.  Hay dos maneras de acceder al operador **or** en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Logical_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical OR  
#include <iostream>  
using namespace std;  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b || b > c yields "  
         << (a < b || b > c) << endl  
         << "The false expression "  
         << "a > b || b > c yields "  
         << (a > b || b > c) << endl;  
}  
```  
  
## Vea también  
 [Operadores lógicos](../misc/logical-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores lógicos de C](../c-language/c-logical-operators.md)