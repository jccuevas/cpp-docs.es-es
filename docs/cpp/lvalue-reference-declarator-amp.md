---
title: 'Declarador de referencia lvalue: &amp; | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6aa0c0a18d77f685369681c0d0400ada6f879e9d
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="lvalue-reference-declarator-amp"></a>Declarador de referencia lvalue:&amp;
Contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
type-id & cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 Una referencia de valor L se puede considerar otro nombre para un objeto. Una declaración de referencia de valor L está formada por una lista opcional de especificadores seguida de un declarador de referencia. Una referencia debe inicializarse y no se puede cambiar.  
  
 Cualquier objeto cuya dirección se pueda convertir a un tipo de puntero especificado también se puede convertir a un tipo de referencia similar. Por ejemplo, cualquier objeto cuya dirección se pueda convertir al tipo `char *` también se puede convertir al tipo `char &`.  
  
 No confunda las declaraciones de referencia con el uso de la [operador address-of](../cpp/address-of-operator-amp.md). Cuando el `&` *identificador* está precedido por un tipo, como `int` o `char`, *identificador* se declara como una referencia al tipo. Cuando `&` *identificador* no está precedido por un tipo, el uso es que el operador address-of.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el declarador de referencia mediante la declaración de un objeto `Person` y una referencia a ese objeto. Dado que `rFriend` es una referencia a `myFriend`, actualizar una de las variables cambia el mismo objeto.  
  
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
  
```Output  
Bill is 40  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencias](../cpp/references-cpp.md)   
 [Argumentos de función de tipo de referencia](../cpp/reference-type-function-arguments.md)   
 [Devueltos de función de tipo de referencia](../cpp/reference-type-function-returns.md)   
 [Referencias a punteros](../cpp/references-to-pointers.md)
