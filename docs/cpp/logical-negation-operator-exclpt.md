---
title: "Operador l&#243;gico de negaci&#243;n: ! | Microsoft Docs"
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
  - "!"
  - "Not"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "! (operador)"
  - "negación lógica"
  - "NOT (operador)"
ms.assetid: 650add9f-a7bc-426c-b01d-5fc6a81c8b62
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador l&#243;gico de negaci&#243;n: !
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
! cast-expression  
```  
  
## Comentarios  
 El operador de negación lógico \(**\!**\) invierte el significado del operando.  El operando debe ser de tipo aritmético o de puntero \(o una expresión que se evalúe como un tipo aritmético o de puntero\).  El operando se convierte implícitamente al tipo `bool`.  El resultado es **true** si el operando convertido es **false**; el resultado es **false** si el operando convertido es **true**.  El resultado es de tipo `bool`.  
  
 Para una expresión *e*, la expresión unaria **\!***e* es equivalente a la expresión **\(***e* `==` 0\), excepto si intervienen operadores sobrecargados.  
  
## Palabra clave del operador para \!  
 El operador **not** es el equivalente de texto de **\!** Hay dos maneras de acceder al operador **not** en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Logical_NOT_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
int main() {  
   int i = 0;  
   if (!i)  
      cout << "i is zero" << endl;  
}  
```  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores aritméticos unarios](../c-language/unary-arithmetic-operators.md)