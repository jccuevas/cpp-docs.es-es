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
ms.openlocfilehash: 63bf0a9e3f458b35421ca53d32a2d6be4b701e58
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687243"
---
# <a name="ostream_iterator-class"></a>ostream_iterator (Clase)

La plantilla de clase ostream_iterator describe un objeto de iterador de salida que escribe elementos sucesivos en el flujo de salida con la `operator <<` de extracción.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type class CharType = char class Traits = char_traits <CharType>>
class ostream_iterator
```

### <a name="parameters"></a>Parámetros

*Escribir* \
Tipo de objeto que se va a insertar en el flujo de salida.

@No__t_1 *CharType*
Tipo que representa el tipo de caracteres para `ostream_iterator`. Este argumento es opcional y el valor predeterminado es **Char**.

*Rasgos* \
Tipo que representa el tipo de caracteres para `ostream_iterator`. Este argumento es opcional y el valor predeterminado es `char_traits`\< *CharType>.*

La clase ostream_iterator debe satisfacer los requisitos de un iterador de salida. Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostream_iterator`.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ostream_iterator](#ostream_iterator)|Construye una clase `ostream_iterator` que se inicializa y delimita para escribir caracteres en el flujo de salida.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que proporciona el tipo de los caracteres de `ostream_iterator`.|
|[ostream_type](#ostream_type)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|
|[traits_type](#traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator*](#op_star)|Operador de desreferencia usado para implementar la expresión de iterador de salida \* `i`  =  `x`.|
|[operator++](#op_add_add)|Operador de incremento no funcional que devuelve un objeto `ostream_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|
|[operator=](#op_eq)|Operador de asignación usado para implementar la expresión de iterador de salida \* `i`  =  `x` para escribir en un flujo de salida.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="char_type"></a> ostream_iterator::char_type

Un tipo que proporciona el tipo de caracteres del iterador.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Comentarios

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

## <a name="op_star"></a> ostream_iterator::operator*

Desreferencia el operador usado para implementar la expresión de iterador de salida \* *ii* = *x*.

```cpp
ostream_iterator<Type, CharType, Traits>& operator*();
```

### <a name="return-value"></a>Valor devuelto

Una referencia a `ostream_iterator`.

### <a name="remarks"></a>Comentarios

Los requisitos para un iterador de salida que `ostream_iterator` debe satisfacer solo requieren que la expresión \* *ii* = *t* sea válida y no indique nada sobre **operator** o `operator=` por cuenta propia. El operador miembro en esta implementación devuelve **\*this**.

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

## <a name="op_add_add"></a> ostream_iterator::operator++

Operador de incremento no funcional que devuelve un objeto `ostream_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.

```cpp
ostream_iterator<Type, CharType, Traits>& operator++();
ostream_iterator<Type, CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

Una referencia a `ostream_iterator`.

### <a name="remarks"></a>Comentarios

Estos operadores miembro devuelven **\*this**.

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

## <a name="op_eq"></a> ostream_iterator::operator=

Operador de asignación usado para implementar la expresión output_iterator \* `i`  =  `x` para escribir en un flujo de salida.

```cpp
ostream_iterator<Type, CharType, Traits>& operator=(const Type& val);
```

### <a name="parameters"></a>Parámetros

\ *Val*
El valor del objeto de tipo `Type` que se va a insertar en el flujo de salida.

### <a name="return-value"></a>Valor devuelto

El operador inserta *Val* en el flujo de salida asociado al objeto, seguido del delimitador especificado en el [constructor ostream_iterator](#ostream_iterator) (si existe) y, a continuación, devuelve una referencia a la `ostream_iterator`.

### <a name="remarks"></a>Comentarios

Los requisitos para un iterador de salida que el `ostream_iterator` debe cumplir requiere solo la expresión \* `ii`  =  `t` ser válida y no indica nada sobre el operador o el operador = por su cuenta. Este operador miembro devuelve `*this`.

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

## <a name="ostream_iterator"></a> ostream_iterator::ostream_iterator

Construye una clase `ostream_iterator` que se inicializa y delimita para escribir caracteres en el flujo de salida.

```cpp
ostream_iterator(
    ostream_type& _Ostr);

ostream_iterator(
    ostream_type& _Ostr,
    const CharType* _Delimiter);
```

### <a name="parameters"></a>Parámetros

@No__t_1 *_Ostr*
El flujo de salida de tipo [ostream_iterator::ostream_type](#ostream_type) que se va a repetir.

@No__t_1 *_Delimiter*
El delimitador que se inserta en el flujo de salida entre valores.

### <a name="remarks"></a>Comentarios

El primer constructor inicializa el puntero del flujo de salida con `&_Ostr`. El puntero de la cadena de delimitador designa una cadena vacía.

El segundo constructor inicializa el puntero del flujo de salida con `&_Ostr` y el puntero de la cadena de delimitador con *_Delimiter*.

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

## <a name="ostream_type"></a> ostream_iterator::ostream_type

Un tipo que proporciona el tipo de secuencia del iterador.

```cpp
typedef basic_ostream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de [basic_ostream](../standard-library/basic-ostream-class.md)< `CharType`, `Traits`>, una clase de secuencia de la jerarquía iostream que define objetos que pueden usarse para escribir.

### <a name="example"></a>Ejemplo

Vea [ostream_iterator](#ostream_iterator) para obtener un ejemplo de cómo declarar y usar `ostream_type`.

## <a name="traits_type"></a> ostream_iterator::traits_type

Un tipo que proporciona el tipo de rasgos de los caracteres del iterador.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Comentarios

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

## <a name="see-also"></a>Vea también

[\<iterator>](../standard-library/iterator.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
