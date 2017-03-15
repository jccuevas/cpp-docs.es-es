---
title: "Operador AND l&#243;gico: &amp;&amp; | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "&amp;&amp; (operador)"
  - "AND (operador)"
  - "AND lógico (operador)"
ms.assetid: 50cfa664-a8c4-4b31-9bab-2f80d7cd2d1f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador AND l&#243;gico: &amp;&amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
expression   
&&  
 expression  
  
```  
  
## Comentarios  
 El operador AND lógico \(**&&**\) devuelve el valor booleano **true** si ambos operandos son **true**; en caso contrario, devuelve **false**.  Los operandos se convierten implícitamente al tipo `bool` antes de evaluación, y el resultado es de tipo `bool`.  El operador AND lógico tiene asociatividad de izquierda a derecha.  
  
 Los operandos del operador AND lógico no tienen por qué ser del mismo tipo, pero deben ser de tipo entero o puntero.  Los operandos son normalmente expresiones relacionales o de igualdad.  
  
 El primer operando se evalúa en su totalidad y, antes de proseguir con la evaluación de la expresión AND lógica, se aplican todos los efectos secundarios.  
  
 El segundo operando solo se evalúa si el primero se evalúa como true \(distinto de cero\).  Esta evaluación elimina la evaluación innecesaria del segundo operando cuando la expresión lógica AND es false.  Puede utilizar esta evaluación de cortocircuito para evitar la desreferencia de punteros null, como se muestra en el ejemplo siguiente:  
  
```  
char *pch = 0;  
...  
(pch) && (*pch = 'a');  
```  
  
 Si `pch` es null \(0\), el lado derecho de la expresión no se evalúa.  Por consiguiente, la asignación a través de un puntero null es imposible.  
  
## Palabra clave del operador para &&  
 El operador **and** es el equivalente de texto de **&&**.  Hay dos maneras de acceder al operador **and** en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Logical_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate logical AND  
#include <iostream>  
  
using namespace std;  
  
int main() {  
   int a = 5, b = 10, c = 15;  
   cout  << boolalpha  
         << "The true expression "  
         << "a < b && b < c yields "  
         << (a < b && b < c) << endl  
         << "The false expression "  
         << "a > b && b < c yields "  
         << (a > b && b < c) << endl;  
}  
```  
  
## Vea también  
 [Operadores lógicos](../misc/logical-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores lógicos de C](../c-language/c-logical-operators.md)