---
title: "Operadores de igualdad: == y != | Microsoft Docs"
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
  - "not_eq"
  - "!="
  - "=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "!= (operador)"
  - "== (operador)"
  - "igual que (operador)"
  - "operador de igualdad"
  - "operador de igualdad, sintaxis"
  - "distinto de (operador de comparación)"
  - "not_eq (operador)"
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de igualdad: == y !=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
      expression == expression  
expression != expression  
```  
  
## Comentarios  
 Los operadores de igualdad binarios comparan la igualdad o desigualdad estricta de sus operandos.  
  
 Los operadores de igualdad, igual a \(`==`\) y no igual a \(`!=`\), tienen prioridad inferior que los operadores relacionales, pero se comportan de igual forma.  El tipo de resultado de estos operadores es `bool`.  
  
 El operador igual a \(`==`\) devuelve **true** \(1\) si ambos operandos tienen el mismo valor; de lo contrario, devuelve **false** \(0\).  El operador no es igual a \(`!=`\) devuelve **true** si los operandos no tienen el mismo valor; de lo contrario, devuelve **false**.  
  
## Palabra clave del operador para \!\=  
 El operador `not_eq` es el equivalente de texto de `!=`.  Hay dos maneras de obtener acceso al operador `not_eq` en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Equality_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   cout  << boolalpha  
         << "The true expression 3 != 2 yields: "  
         << (3 != 2) << endl  
         << "The false expression 20 == 10 yields: "  
         << (20 == 10) << endl;  
}  
```  
  
 Los operadores de igualdad puede comparar punteros a miembros del mismo tipo.  En esta comparación, se realizan conversiones de puntero a miembro, como se describe en [Conversiones de puntero a miembro](../misc/pointer-to-member-conversions.md).  Los punteros a miembros también se pueden comparar con una expresión constante que se evalúa como 0.  
  
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores relacionales y de igualdad de C](../c-language/c-relational-and-equality-operators.md)