---
title: 'Operadores relacionales: &lt;, &gt;, &lt;=, y &gt;='
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
ms.openlocfilehash: 52a3c10e6da42f6c181d3f93de13168e22141bec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458960"
---
# <a name="relational-operators-lt-gt-lt-and-gt"></a>Operadores relacionales: &lt;, &gt;, &lt;=, y &gt;=

## <a name="syntax"></a>Sintaxis

```
expression < expression
expression > expression
expression <= expression
expression >= expression
```

## <a name="remarks"></a>Comentarios

Los operadores relacionales binarios determinan las relaciones siguientes:

- Menor que (**\<**)

- Mayor que (**>**)

- Menor o igual a (**\<=**)

- Mayor o igual a (**>=**)

Los operadores relacionales tienen asociatividad de izquierda a derecha. Ambos operandos de los operadores relacionales deben ser de tipo aritmética o puntero. Producen valores de tipo **bool**. El valor devuelto es **false** (0) si la relación en la expresión es false; en caso contrario, el valor devuelto es **true** (1).

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

Las expresiones en el ejemplo anterior deben incluirse entre paréntesis porque el operador de inserción de secuencia (**<<**) tiene mayor prioridad que los operadores relacionales. Por consiguiente, la primera expresión sin paréntesis se evaluaría como:

```cpp
(cout << "The true expression 3 > 2 yields: " << 3) < (2 << "\n");
```

Tratan las conversiones aritméticas habituales en [conversiones estándar](standard-conversions.md) se aplican a los operandos de tipos aritméticos.

## <a name="comparing-pointers"></a>Comparar punteros

Cuando se comparan dos punteros a objetos del mismo tipo, el resultado está determinado por la ubicación de los objetos a los que se señala en el espacio de direcciones del programa. También se pueden comparar punteros en una expresión constante que se evalúa como 0 o a un puntero de tipo `void *`. Si se realiza una comparación de punteros de un puntero de tipo `void *`, el otro puntero se convierte implícitamente al tipo `void *`. A continuación, se realiza la comparación.

Dos punteros de tipos diferentes no pueden compararse a menos que:

- Un tipo sea un tipo de clase derivado del otro tipo.

- Al menos uno de los punteros se convierta explícitamente (conversión) al tipo `void *`. (El otro puntero se convierte implícitamente al tipo `void *` para la conversión.)

Se garantiza que dos punteros del mismo tipo que señalan al mismo objeto realizan una comparación igual. Si se comparan dos punteros a miembros no estáticos de un objeto, se aplican las reglas siguientes:

- Si el tipo de clase no es un **unión**, y si los dos miembros no están separados por un *access-specifier*, tales como **pública**, **protegido**, o **privada**, el puntero al miembro declarado por última vez realizará una comparación mayor que el puntero al miembro declarado anteriormente.

- Si los dos miembros están separados por un *access-specifier*, los resultados son indefinidos.

- Si el tipo de clase es un **unión**, punteros a miembros de datos diferentes en que **unión** comparan igual.

Si dos punteros señalan a elementos de la misma matriz o al elemento uno situado más allá del final de la matriz, el puntero al objeto con el subíndice más alto realiza una comparación superior. Se garantiza que la comparación de punteros es válida solo cuando los punteros hacen referencia a objetos de la misma matriz o a la ubicación uno superado el final de la matriz.

## <a name="see-also"></a>Vea también

[Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Operadores relacionales y de igualdad de C](../c-language/c-relational-and-equality-operators.md)