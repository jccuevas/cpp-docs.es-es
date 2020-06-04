---
title: 'Declarador de referencia lvalue: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 595f2b683d2abb4cdc8a328dc6e86338ab90f214
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178072"
---
# <a name="lvalue-reference-declarator-amp"></a>Declarador de referencia lvalue: &amp;

Contiene la dirección de un objeto, pero se comporta sintácticamente como un objeto.

## <a name="syntax"></a>Sintaxis

```
type-id & cast-expression
```

## <a name="remarks"></a>Observaciones

Una referencia de valor L se puede considerar otro nombre para un objeto. Una declaración de referencia de valor L está formada por una lista opcional de especificadores seguida de un declarador de referencia. Una referencia debe inicializarse y no se puede cambiar.

Cualquier objeto cuya dirección se pueda convertir a un tipo de puntero especificado también se puede convertir a un tipo de referencia similar. Por ejemplo, cualquier objeto cuya dirección se pueda convertir al tipo `char *` también se puede convertir al tipo `char &`.

No confunda las declaraciones de referencia con el uso del [operador Address-of](../cpp/address-of-operator-amp.md). Cuando el *identificador* de `&`está precedido por un tipo, como **int** o **Char**, el *identificador* se declara como una referencia al tipo. Cuando `&`*identificador* no va precedido de un tipo, el uso es el del operador Address-of.

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

## <a name="see-also"></a>Consulte también

[Referencias](../cpp/references-cpp.md)<br/>
[Argumentos de función de tipo de referencia](../cpp/reference-type-function-arguments.md)<br/>
[Valores devueltos de función de tipo de referencia](../cpp/reference-type-function-returns.md)<br/>
[Referencias a punteros](../cpp/references-to-pointers.md)
