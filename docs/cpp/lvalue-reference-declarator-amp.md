---
title: 'Declarador de referencia lvalue: &amp; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d16ed882b1037123963f105b1a78bf8e1023d332
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944799"
---
# <a name="lvalue-reference-declarator-amp"></a>Declarador de referencia lvalue: &amp;
Contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
type-id & cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 Una referencia de valor L se puede considerar otro nombre para un objeto. Una declaración de referencia de valor L está formada por una lista opcional de especificadores seguida de un declarador de referencia. Una referencia debe inicializarse y no se puede cambiar.  
  
 Cualquier objeto cuya dirección se pueda convertir a un tipo de puntero especificado también se puede convertir a un tipo de referencia similar. Por ejemplo, cualquier objeto cuya dirección se pueda convertir al tipo `char *` también se puede convertir al tipo `char &`.  
  
 No confunda las declaraciones de referencia con el uso de la [operador address-of](../cpp/address-of-operator-amp.md). Cuando el `&` *identificador* está precedido por un tipo, como **int** o **char**, *identificador* se declara como una referencia a el tipo. Cuando `&` *identificador* no va precedido por un tipo, el uso es que el operador address-of.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el declarador de referencia mediante la declaración de un objeto `Person` y una referencia a ese objeto. Dado que `rFriend` es una referencia a `myFriend`, actualizar una de las variables cambia el mismo objeto.  
  
```cpp 
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
 [Argumentos de función del tipo de referencia](../cpp/reference-type-function-arguments.md)   
 [Tipo de referencia de función devuelve](../cpp/reference-type-function-returns.md)   
 [Referencias a punteros](../cpp/references-to-pointers.md)