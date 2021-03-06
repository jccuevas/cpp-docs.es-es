---
title: ostream_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- iterator/std::ostream_iterator
- iterator/std::ostream_iterator::char_type
- iterator/std::ostream_iterator::ostream_type
- iterator/std::ostream_iterator::traits_type
helpviewer_keywords:
- std::ostream_iterator [C++]
- std::ostream_iterator [C++], char_type
- std::ostream_iterator [C++], ostream_type
- std::ostream_iterator [C++], traits_type
ms.assetid: 24d842d3-9f45-4bf6-a697-62f5968f5a03
ms.openlocfilehash: a0c794fe2ff7897bcb6d6412613689100a977589
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373596"
---
# <a name="ostream_iterator-class"></a>ostream_iterator (Clase)

La plantilla de clase ostream_iterator describe un objeto de iterador de `operator <<`salida que escribe elementos sucesivos en la secuencia de salida con la extracción.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parámetros

*Tipo*\
Tipo de objeto que se va a insertar en el flujo de salida.

*CharType*\
Tipo que representa el tipo de caracteres para `ostream_iterator`. Este argumento es opcional y el valor predeterminado es **char**.

*Rasgos*\
Tipo que representa el tipo de caracteres para `ostream_iterator`. Este argumento es opcional y el valor predeterminado es `char_traits`\< *CharType>.*

La clase ostream_iterator debe satisfacer los requisitos de un iterador de salida. Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostream_iterator`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ostream_iterator](#ostream_iterator)|Construye una clase `ostream_iterator` que se inicializa y delimita para escribir caracteres en el flujo de salida.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que proporciona el tipo de los caracteres de `ostream_iterator`.|
|[ostream_type](#ostream_type)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|
|[traits_type](#traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|Operador de desreferenciación utilizado \* `i`  =  `x`para implementar la expresión de iterador de salida.|
|[operador++](#op_add_add)|Operador de incremento no funcional que devuelve un objeto `ostream_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|
|[operador](#op_eq)|Operador de asignación utilizado \* `i`  =  `x` para implementar la expresión de iterador de salida para escribir en una secuencia de salida.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="ostream_iteratorchar_type"></a><a name="char_type"></a>ostream_iterator::char_type

Un tipo que proporciona el tipo de caracteres del iterador.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `CharType`.

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to the output stream\n"
        << "by intOut are:" << endl;
*intOut = 10;
*intOut = 20;
*intOut = 30;
}
/* Output:
The integers written to the output stream
by intOut are:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_star"></a>ostream_iterator::operador*

Operador de desreferenciación utilizado \* para implementar la expresión de iterador de salida *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a `ostream_iterator`.

### <a name="remarks"></a>Observaciones

Los requisitos para un `ostream_iterator` iterador de \* salida que el debe satisfacer requieren `operator=` sólo la expresión *ii* = *t* ser válido y no dice nada sobre el **operador** o el por su cuenta. El operador miembro de ** \*** esta implementación devuelve este archivo .

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_add_add"></a>ostream_iterator::operador++

Operador de incremento no funcional que devuelve un objeto `ostream_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

Una referencia a `ostream_iterator`.

### <a name="remarks"></a>Observaciones

Estos operadores ** \*** miembro devuelven este archivo .

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratoroperator"></a><a name="op_eq"></a>ostream_iterator::operador ?

Operador de asignación utilizado \* `i`  =  `x` para implementar la expresión output_iterator para escribir en una secuencia de salida.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parámetros

*Val*\
El valor del objeto de tipo `Type` que se va a insertar en el flujo de salida.

### <a name="return-value"></a>Valor devuelto

El operador inserta *val* en la secuencia de salida asociada al objeto, seguido del delimitador especificado en el `ostream_iterator`constructor [ostream_iterator](#ostream_iterator) (si existe) y, a continuación, devuelve una referencia a la extensión .

### <a name="remarks"></a>Observaciones

Los requisitos para un `ostream_iterator` iterador de \* `ii`  =  `t` salida que el debe satisfacer requieren que solo la expresión sea válida y no dice nada sobre el operador o el operador por sí solo. Este operador miembro devuelve `*this`.

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   // with new line delimiter
   ostream_iterator<int> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*intOut = 10;
   intOut++;      // No effect on iterator position
*intOut = 20;
*intOut = 30;
}
/* Output:
Elements written to output stream:
10
20
30
*/
```

## <a name="ostream_iteratorostream_iterator"></a><a name="ostream_iterator"></a>ostream_iterator::ostream_iterator

Construye una clase `ostream_iterator` que se inicializa y delimita para escribir caracteres en el flujo de salida.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parámetros

*_Ostr*\
El flujo de salida de tipo [ostream_iterator::ostream_type](#ostream_type) que se va a repetir.

*_Delimiter*\
El delimitador que se inserta en el flujo de salida entre valores.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el puntero del flujo de salida con `&_Ostr`. El puntero de la cadena de delimitador designa una cadena vacía.

El segundo constructor inicializa el `&_Ostr` puntero de secuencia de salida con y el puntero de cadena delimitador con *_Delimiter*.

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_ostream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostream_iterator for stream cout
   ostream_iterator<int> intOut ( cout , "\n" );
*intOut = 10;
   intOut++;
*intOut = 20;
   intOut++;

   int i;
   vector<int> vec;
   for ( i = 1 ; i < 7 ; ++i )
   {
      vec.push_back (  i );
   }

   // Write elements to standard output stream
   cout << "Elements output without delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout ) );
   cout << endl;

   // Write elements with delimiter " : " to output stream
   cout << "Elements output with delimiter: ";
   copy ( vec.begin ( ), vec.end ( ),
          ostream_iterator<int> ( cout, " : " ) );
   cout << endl;
}
/* Output:
10
20
Elements output without delimiter: 123456
Elements output with delimiter: 1 : 2 : 3 : 4 : 5 : 6 :
*/
```

## <a name="ostream_iteratorostream_type"></a><a name="ostream_type"></a>ostream_iterator::ostream_type

Un tipo que proporciona el tipo de secuencia del iterador.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Observaciones

El tipo es [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`un `Traits` sinónimo de basic_ostream ,>, una clase de secuencia de la jerarquía iostream que define los objetos que se pueden usar para escribir.

### <a name="example"></a>Ejemplo

Vea [ostream_iterator](#ostream_iterator) para obtener un ejemplo de cómo declarar y usar `ostream_type`.

## <a name="ostream_iteratortraits_type"></a><a name="traits_type"></a>ostream_iterator::traits_type

Un tipo que proporciona el tipo de rasgos de los caracteres del iterador.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Traits`.

### <a name="example"></a>Ejemplo

```cpp
// ostream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // The following not OK, but are just the default values:
   typedef ostream_iterator<int>::char_type CHT1;
   typedef ostream_iterator<int>::traits_type CHTR1;

   // ostream_iterator for stream cout
   // with new line delimiter:
    ostream_iterator<int, CHT1, CHTR1> intOut ( cout , "\n" );

   // Standard iterator interface for writing
   // elements to the output stream:
   cout << "The integers written to output stream\n"
        << "by intOut are:" << endl;
*intOut = 1;
*intOut = 10;
*intOut = 100;
}
/* Output:
The integers written to output stream
by intOut are:
1
10
100
*/
```

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
