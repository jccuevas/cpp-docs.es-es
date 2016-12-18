---
title: "Declarador de referencia a un valor L: &amp; | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& (operador), operador de referencia"
  - "operador de referencia"
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Declarador de referencia a un valor L: &amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.  
  
## Sintaxis  
  
```  
  
type-id & cast-expression  
```  
  
## Comentarios  
 Una referencia de valor L se puede considerar otro nombre para un objeto.  Una declaración de referencia de valor L está formada por una lista opcional de especificadores seguida de un declarador de referencia.  Una referencia debe inicializarse y no se puede cambiar.  
  
 Cualquier objeto cuya dirección se pueda convertir a un tipo de puntero especificado también se puede convertir a un tipo de referencia similar.  Por ejemplo, cualquier objeto cuya dirección se pueda convertir al tipo `char *` también se puede convertir al tipo `char &`.  
  
 No confunda las declaraciones de referencia con el uso del [operador address\-of](../cpp/address-of-operator-amp.md).  Cuando el *identificador* `&` va precedido de un tipo como, por ejemplo, `int` o `char`, el *identificador* se declara como una referencia al tipo.  Cuando el *identificador* `&` no va precedido de un tipo, el uso es el del operador address\-of.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra el declarador de referencia mediante la declaración de un objeto `Person` y una referencia a ese objeto.  Dado que `rFriend` es una referencia a `myFriend`, actualizar una de las variables cambia el mismo objeto.  
  
```  
// reference_declarator.cpp  
// compile with: /EHsc  
// Demonstrates the reference declarator.  
#include <iostream>  
using namespace std;  
  
struct Person  
{  
    char* Name;  
    short Age;  
};  
  
int main()  
{  
   // Declare a Person object.  
   Person myFriend;  
  
   // Declare a reference to the Person object.  
   Person& rFriend = myFriend;  
  
   // Set the fields of the Person object.  
   // Updating either variable changes the same object.  
   myFriend.Name = "Bill";  
   rFriend.Age = 40;  
  
   // Print the fields of the Person object to the console.  
   cout << rFriend.Name << " is " << myFriend.Age << endl;  
}  
```  
  
  **Bill tiene 40 años**   
## Vea también  
 [Referencias](../cpp/references-cpp.md)   
 [Argumentos de función de tipo de referencia](../cpp/reference-type-function-arguments.md)   
 [Valores devueltos de las funciones de tipo de referencia](../cpp/reference-type-function-returns.md)   
 [Referencias a punteros](../cpp/references-to-pointers.md)