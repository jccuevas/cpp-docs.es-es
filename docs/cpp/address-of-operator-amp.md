---
title: 'Operador Address-of: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: 4c9ae9aedaec202c8798ab454ee5df1a68278a6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181608"
---
# <a name="address-of-operator-amp"></a>Operador Address-of: &amp;

## <a name="syntax"></a>Sintaxis

```
& cast-expression
```

## <a name="remarks"></a>Observaciones

El operador unario Address-of ( **&** ) toma la dirección de su operando. El operando del operador Address-of puede ser un designador de función o un valor l que designe un objeto que no sea un campo de bits.

El operador address-of solo se puede aplicar a variables con tipos fundamentales, de estructura, de clase o de unión que se declaren en el nivel de ámbito de archivo o para referencias de matriz de subíndice. En estas expresiones, se puede agregar o quitar de la expresión address-of una expresión constante que no incluya el operador address-of.

Cuando se aplica a funciones o valores L, el resultado de la expresión es un tipo de puntero (un valor R) derivado del tipo del operando. Por ejemplo, si el operando es de tipo **Char**, el resultado de la expresión es de tipo Pointer a **Char**. El operador Address-of, aplicado a objetos **const** o **volatile** , se evalúa como `const type *` o `volatile type *`, donde **Type** es el tipo del objeto original.

Cuando el operador Address-of se aplica a un nombre completo, el resultado depende de si el *nombre completo* especifica un miembro estático. En ese caso, el resultado es un puntero al tipo especificado en la declaración del miembro. Si el miembro no es estático, el resultado es un puntero al *nombre* de miembro de la clase indicada por *el nombre de clase calificado*. (Vea [expresiones primarias](../cpp/primary-expressions.md) para obtener más información sobre *Qualified-Class-Name*). En el fragmento de código siguiente se muestra cómo difiere el resultado, en función de si el miembro es estático:

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

En este ejemplo, la expresión `&PTM::fValue` proporciona el tipo `float *` en lugar de `float PTM::*`, porque `fValue` es un miembro estático.

La dirección de una función sobrecargada se puede tomar solo cuando está claro a qué versión de la función se hace referencia. Vea [sobrecarga de funciones](function-overloading.md) para obtener información sobre cómo obtener la dirección de una función sobrecargada determinada.

Al aplicar el operator address-of a un tipo de referencia se obtiene el mismo resultado que al aplicar el operador al objeto al que se enlaza la referencia. Por ejemplo:

## <a name="example"></a>Ejemplo

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>Output

```Output
&d equals &rd
```

En el ejemplo siguiente se usa el operator address-of para pasar un argumento de puntero a una función:

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>Output

```Output
25
```

## <a name="see-also"></a>Consulte también

[Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[Operadores de direccionamiento indirecto y address-of](../c-language/indirection-and-address-of-operators.md)
