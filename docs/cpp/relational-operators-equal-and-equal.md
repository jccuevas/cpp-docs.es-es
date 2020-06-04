---
title: 'Operadores relacionales: &lt;, &gt;, &lt;= y &gt;='
ms.date: 11/04/2016
f1_keywords:
- <
- '>'
helpviewer_keywords:
- '> operator'
- less than operator
- relational operators [C++], syntax
- '>= operator'
- greater than or equal to operators [C++]
- greater than operators [C++]
- < operator
- less than or equal to operator
- <= operator
ms.assetid: d346b53d-f14d-4962-984f-89d39a17ca0f
ms.openlocfilehash: 38e05b78d334ca690d9523797f7ca1813834c5d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179125"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operadores relacionales: &lt;, &gt;, &lt;= y &gt;=

## <a name="syntax"></a>Sintaxis

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Observaciones

Los operadores relacionales binarios determinan las relaciones siguientes:

- Menor que ( **\<** )

- Mayor que ( **>** )

- Menor o igual que ( **\<=** )

- Mayor o igual que ( **>=** )

Los operadores relacionales tienen asociatividad de izquierda a derecha. Ambos operandos de los operadores relacionales deben ser de tipo aritmética o puntero. Producen valores de tipo **bool**. El valor devuelto es **false** (0) si la relación de la expresión es false; de lo contrario, el valor devuelto es **true** (1).

## <a name="example"></a>Ejemplo

```cpp
// expre_Relational_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << "The true expression 3 > 2 yields: "
         << (3 > 2) << endl
         << "The false expression 20 < 10 yields: "
         << (20 < 10) << endl;
}
```

Las expresiones del ejemplo anterior se deben incluir entre paréntesis porque el operador de inserción de secuencias ( **<<** ) tiene mayor precedencia que los operadores relacionales. Por consiguiente, la primera expresión sin paréntesis se evaluaría como:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Las conversiones aritméticas habituales descritas en [conversiones estándar](standard-conversions.md) se aplican a los operandos de tipos aritméticos.

## <a name="comparing-pointers"></a>Comparar punteros

Cuando se comparan dos punteros a objetos del mismo tipo, el resultado está determinado por la ubicación de los objetos a los que se señala en el espacio de direcciones del programa. Los punteros también se pueden comparar con una expresión constante que se evalúa como 0 o con un puntero de tipo `void *`. Si se realiza una comparación de puntero en un puntero de tipo `void *`, el otro puntero se convierte implícitamente al tipo `void *`. A continuación, se realiza la comparación.

Dos punteros de tipos diferentes no pueden compararse a menos que:

- Un tipo sea un tipo de clase derivado del otro tipo.

- Al menos uno de los punteros se convierte explícitamente (Cast) al tipo `void *`. (El otro puntero se convierte implícitamente al tipo `void *` para la conversión).

Se garantiza que dos punteros del mismo tipo que señalan al mismo objeto realizan una comparación igual. Si se comparan dos punteros a miembros no estáticos de un objeto, se aplican las reglas siguientes:

- Si el tipo de clase no es una **Unión**y los dos miembros no están separados por un *especificador de acceso*, como **Public**, **Protected**o **Private**, el puntero al miembro declarado Last se comparará más que el puntero al miembro declarado anteriormente.

- Si los dos miembros están separados por un *especificador de acceso*, los resultados son indefinidos.

- Si el tipo de clase es una **Unión**, los punteros a distintos miembros de datos de esa **Unión** comparan igual.

Si dos punteros señalan a elementos de la misma matriz o al elemento uno situado más allá del final de la matriz, el puntero al objeto con el subíndice más alto realiza una comparación superior. Se garantiza que la comparación de punteros es válida solo cuando los punteros hacen referencia a objetos de la misma matriz o a la ubicación uno superado el final de la matriz.

## <a name="see-also"></a>Consulte también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores relacionales y de igualdad de C](../c-language/c-relational-and-equality-operators.md)
