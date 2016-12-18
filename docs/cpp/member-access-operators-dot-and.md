---
title: "Operadores de acceso a miembros: . y -&gt; | Microsoft Docs"
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
  - "."
  - "->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ". (operador)"
  - "-> (operador)"
  - "operador de punto (.)"
  - "acceso a miembros"
  - "acceso a miembros, expresiones"
  - "acceso a miembros, operadores"
  - "operadores [C++], acceso a miembros"
  - "operadores postfijos"
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de acceso a miembros: . y -&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
      postfix-expression   
      . name  
postfix-expression –> name  
```  
  
## Comentarios  
 Los operadores de acceso a miembros **.** y **\-\>** se utilizan para hacer referencia a los miembros de estructuras, uniones y clases.  Las expresiones de acceso a miembros tienen el valor y el tipo del miembro seleccionado.  
  
 Hay dos formas de expresiones de acceso de miembro:  
  
1.  En la primera forma, *postfix\-expression* representa un valor de tipo de estructura, clase o unión, y *name* designa un miembro de la estructura, unión o clase especificadas.  El valor de la operación es el de *name* y es un valor L si *postfix\-expression* es un valor L.  
  
2.  En la segunda forma, *postfix\-expression* representa un puntero a una estructura, unión o clase, y *name* designa un miembro de la estructura, unión o clase especificadas.  El valor es el de *name* y es un valor L.  El operador **–\>** desreferencia el puntero.  Por consiguiente, las expresiones *e***–\>**`member` y **\(\****e***\)**.`member` \(donde *e* representa un puntero\) producen resultados idénticos \(excepto cuando se sobrecargan los operadores **–\>** o **\***\).  
  
## Ejemplo  
 En el ejemplo siguiente se muestran dos formas del operador de acceso a miembros.  
  
```  
// expre_Selection_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
struct Date {  
   Date(int i, int j, int k) : day(i), month(j), year(k){}  
   int month;  
   int day;  
   int year;  
};  
  
int main() {  
   Date mydate(1,1,1900);  
   mydate.month = 2;     
   cout  << mydate.month << "/" << mydate.day  
         << "/" << mydate.year << endl;  
  
   Date *mydate2 = new Date(1,1,2000);  
   mydate2->month = 2;  
   cout  << mydate2->month << "/" << mydate2->day  
         << "/" << mydate2->year << endl;  
   delete mydate2;  
}  
```  
  
  **2\/1\/1900**  
**2\/1\/2000**   
## Vea también  
 [Expresiones postfijas](../cpp/postfix-expressions.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Clases y structs](../cpp/classes-and-structs-cpp.md)   
 [Miembros de estructura y de unión](../c-language/structure-and-union-members.md)