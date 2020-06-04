---
title: istreambuf_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::istreambuf_iterator
- iterator/std::istreambuf_iterator::char_type
- iterator/std::istreambuf_iterator::int_type
- iterator/std::istreambuf_iterator::istream_type
- iterator/std::istreambuf_iterator::streambuf_type
- iterator/std::istreambuf_iterator::traits_type
- iterator/std::istreambuf_iterator::equal
helpviewer_keywords:
- std::istreambuf_iterator [C++]
- std::istreambuf_iterator [C++], char_type
- std::istreambuf_iterator [C++], int_type
- std::istreambuf_iterator [C++], istream_type
- std::istreambuf_iterator [C++], streambuf_type
- std::istreambuf_iterator [C++], traits_type
- std::istreambuf_iterator [C++], equal
ms.assetid: 39002da2-61a6-48a5-9d0c-5df8271f6038
ms.openlocfilehash: 80bca2160f2e60938e9d0c85557b11a273c23264
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363061"
---
# <a name="istreambuf_iterator-class"></a>istreambuf_iterator (Clase)

La plantilla de clase istreambuf_iterator describe un objeto de iterador de entrada que extrae elementos de `basic_streambuf` \< caracteres de un búfer de secuencia de entrada, al que tiene acceso a través de un objeto que almacena, de tipo puntero a **CharType**, **Traits**>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType class Traits = char_traits <CharType>>
class istreambuf_iterator
: public iterator<input_iterator_tag, CharType, typename Traits ::off_type, CharType*, CharType&>
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo que representa el tipo de caracteres para istreambuf_iterator.

*Rasgos*\
Tipo que representa el tipo de caracteres para istreambuf_iterator. Este argumento es opcional y el valor predeterminado es `char_traits`\< *CharType>.*

## <a name="remarks"></a>Observaciones

La clase istreambuf_iterator debe satisfacer los requisitos de un iterador de entrada.

Después de crear o de incrementar un objeto de clase istreambuf_iterator con un puntero almacenado no null, el objeto intenta extraer y almacenar un objeto de tipo *CharType* del flujo de entrada asociado. Sin embargo, la extracción se puede retrasar hasta que el objeto se desreferencia o se copia realmente. Si se produce un error en la extracción, el objeto reemplaza el puntero almacenado con un puntero NULL, creando de esta forma un indicador de fin de secuencia.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[istreambuf_iterator](#istreambuf_iterator)|Construye una clase `istreambuf_iterator` que se inicializa para leer caracteres del flujo de entrada.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.|
|[int_type](#int_type)|Tipo que proporciona un tipo entero para `istreambuf_iterator`.|
|[istream_type](#istream_type)|Tipo que proporciona el tipo de flujo de `istream_iterator`.|
|[streambuf_type](#streambuf_type)|Tipo que proporciona el tipo de flujo de `istreambuf_iterator`.|
|[traits_type](../standard-library/istream-iterator-class.md#traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Igual](#equal)|Comprueba si dos iteradores de búfer del flujo de entrada son iguales.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|El operador de desreferenciación devuelve el siguiente carácter del flujo.|
|[operador++](#op_add_add)|Devuelve el siguiente carácter del flujo de entrada o copia el objeto antes de incrementarlo y devuelve la copia.|
|[>operador](#op_arrow)|Devuelve el valor de un miembro, si existe.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="istreambuf_iteratorchar_type"></a><a name="char_type"></a>istreambuf_iterator::char_type

Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *CharType*.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="istreambuf_iteratorequal"></a><a name="equal"></a>istreambuf_iterator::igual

Comprueba si dos iteradores de búfer del flujo de entrada son equivalentes.

```cpp
bool equal(const istreambuf_iterator<CharType, Traits>& right) const;
```

### <a name="parameters"></a>Parámetros

*Correcto*\
Iterador con el que se va a comprobar la igualdad.

### <a name="return-value"></a>Valor devuelto

**True** si ambos `istreambuf_iterator` son iteradores de fin de flujo o si ninguno es un iterador de fin de flujo; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

Un intervalo se `istreambuf_iterator` define por el to la posición actual y el iterador de fin de `equal` secuencia, pero como todos los iteradores `istreambuf_iterator`que no son finales de secuencia son equivalentes en la función miembro, no es posible definir ningún subrango mediante s. Los operadores `==` y `!=` tienen la misma semántica.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_equal.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "(Try the example: 'Hello world!'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   istreambuf_iterator<char> charReadIn1 ( cin );
   istreambuf_iterator<char> charReadIn2 ( cin );

   bool b1 = charReadIn1.equal ( charReadIn2 );

   if (b1)
      cout << "The iterators are equal." << endl;
   else
      cout << "The iterators are not equal." << endl;
}
```

## <a name="istreambuf_iteratorint_type"></a><a name="int_type"></a>istreambuf_iterator::int_type

Tipo que proporciona un tipo entero para `istreambuf_iterator`.

```cpp
typedef typename traits_type::int_type int_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de `Traits::int_type`.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_int_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;
   istreambuf_iterator<char>::int_type inttype1 = 100;
   cout << "The inttype1 = " << inttype1 << "." << endl;
}
/* Output:
The inttype1 = 100.
*/
```

## <a name="istreambuf_iteratoristream_type"></a><a name="istream_type"></a>istreambuf_iterator::istream_type

Tipo que proporciona el tipo de flujo de `istreambuf_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Observaciones

El tipo es `basic_istream` \< un sinónimo de **CharType**, **Traits**>.

### <a name="example"></a>Ejemplo

Vea [istreambuf_iterator](#istreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `istream_type`.

## <a name="istreambuf_iteratoristreambuf_iterator"></a><a name="istreambuf_iterator"></a>istreambuf_iterator::istreambuf_iterator

Construye un istreambuf_iterator que se inicializa para leer caracteres del flujo de entrada.

```cpp
istreambuf_iterator(streambuf_type* strbuf = 0) throw();
istreambuf_iterator(istream_type& _Istr) throw();
```

### <a name="parameters"></a>Parámetros

*strbuf*\
Búfer de flujo de entrada al que se va a adjuntar `istreambuf_iterator`.

*_Istr*\
Flujo de entrada al que se va a adjuntar `istreambuf_iterator`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el puntero de búfer de secuencia de entrada con *strbuf*. El segundo constructor inicializa el puntero de búfer de secuencia de entrada con *_Istr*. `rdbuf`, y, finalmente, intenta extraer y `CharType`almacenar un objeto de tipo .

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_istreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Following declarations will not compile:
   istreambuf_iterator<char>::istream_type &istrm = cin;
   istreambuf_iterator<char>::streambuf_type *strmbf = cin.rdbuf( );

   cout << "(Try the example: 'Oh what a world!'\n"
      << " then an Enter key to insert into the output,\n"
      << " & use a ctrl-Z Enter key combination to exit): ";
   istreambuf_iterator<char> charReadIn ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with hyphen-separators
   replace_copy ( charReadIn , istreambuf_iterator<char>( ),
      charOut , ' ' , '-' );
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_star"></a>istreambuf_iterator::operador*

El operador de desreferenciación devuelve el siguiente carácter del flujo.

```cpp
CharType operator*() const;
```

### <a name="return-value"></a>Valor devuelto

Siguiente carácter del flujo.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_operator_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;   //Put value of outpos equal to inpos
      ++inpos;
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator"></a><a name="op_add_add"></a>istreambuf_iterator::operador++

Devuelve el siguiente carácter del flujo de entrada o copia el objeto antes de incrementarlo y devuelve la copia.

```cpp
istreambuf_iterator<CharType, Traits>& operator++();
istreambuf_iterator<CharType, Traits> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

`istreambuf_iterator` o referencia a `istreambuf_iterator`.

### <a name="remarks"></a>Observaciones

El primer operador finalmente intenta extraer y `CharType` almacenar un objeto de tipo de la secuencia de entrada asociada. El segundo operador realiza una copia del objeto, lo incrementa y, después, devuelve la copia.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Type string of characters & enter to output it,\n"
      << " with stream buffer iterators,(try: 'I'll be back.')\n"
      << " repeat as many times as desired,\n"
      << " then keystroke ctrl-Z Enter to exit program: ";
   istreambuf_iterator<char> inpos ( cin );
   istreambuf_iterator<char> endpos;
   ostreambuf_iterator<char> outpos ( cout );
   while ( inpos != endpos )
   {
*outpos = *inpos;
      ++inpos;   //Increment istreambuf_iterator
      ++outpos;
   }
}
```

## <a name="istreambuf_iteratoroperator-gt"></a><a name="op_arrow"></a>istreambuf_iterator::operador-&gt;

Devuelve el valor de un miembro, si existe.

```cpp
const Elem* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

El operador ** & \* \*** devuelve este archivo .

## <a name="istreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>istreambuf_iterator::streambuf_type

Tipo que proporciona el tipo de flujo de istreambuf_iterator.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Observaciones

El tipo es `basic_streambuf` \< un sinónimo de **CharType**, **Traits**>.

### <a name="example"></a>Ejemplo

Vea [istreambuf_iterator](#istreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `istreambuf_type`.

## <a name="istreambuf_iteratortraits_type"></a><a name="traits_type"></a>istreambuf_iterator::traits_type

Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Traits*.

### <a name="example"></a>Ejemplo

```cpp
// istreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>
#include <algorithm>

int main( )
{
   using namespace std;

   typedef istreambuf_iterator<char>::char_type CHT1;
   typedef istreambuf_iterator<char>::traits_type CHTR1;

   cout << "(Try the example: 'So many dots to be done'\n"
        << " then an Enter key to insert into the output,\n"
        << " & use a ctrl-Z Enter key combination to exit): ";

   // istreambuf_iterator for input stream
   istreambuf_iterator< CHT1, CHTR1> charInBuf ( cin );
   ostreambuf_iterator<char> charOut ( cout );

   // Used in conjunction with replace_copy algorithm
   // to insert into output stream and replace spaces
   // with dot-separators
   replace_copy ( charInBuf , istreambuf_iterator<char>( ),
        charOut , ' ' , '.' );
}
```

## <a name="see-also"></a>Consulte también

[iterador Struct](../standard-library/iterator-struct.md)\
[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
