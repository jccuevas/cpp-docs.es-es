---
title: istream_iterator (Clase)
ms.date: 11/04/2016
f1_keywords:
- iterator/std::istream_iterator
- iterator/std::istream_iterator::char_type
- iterator/std::istream_iterator::istream_type
- iterator/std::istream_iterator::traits_type
helpviewer_keywords:
- std::istream_iterator [C++]
- std::istream_iterator [C++], char_type
- std::istream_iterator [C++], istream_type
- std::istream_iterator [C++], traits_type
ms.assetid: fb52a8cd-7f71-48d1-b73e-4b064e2a8d16
ms.openlocfilehash: 3766a93d7cba9096ce3ff775d94c17a85456fb00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363102"
---
# <a name="istream_iterator-class"></a>istream_iterator (Clase)

Describe un objeto iterador de entrada. Extrae objetos de clase `Type` de un flujo de entrada al que tiene acceso a través de un objeto que almacena, de tipo `pointer` en `basic_istream`< `CharType`, `Traits`>.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type, class CharType = char, class Traits = char_traits<CharType>, class Distance = ptrdiff_t,>
class istream_iterator
: public iterator<
    input_iterator_tag, Type, Distance,
    const Type *,
    const Type&>;
```

### <a name="parameters"></a>Parámetros

*Tipo*\
Tipo de objeto que se extraerá del flujo de entrada.

*CharType*\
Tipo que representa el tipo de caracteres para `istream_iterator`. Este argumento es opcional y el valor predeterminado es **char**.

*Rasgos*\
Tipo que representa el tipo de caracteres para `istream_iterator`. Este argumento es opcional y el valor predeterminado es `char_traits`< `CharType`>.

*Distancia*\
Tipo entero con signo que representa el tipo de diferencia para `istream_iterator`. Este argumento es opcional y el valor predeterminado es `ptrdiff_t`.

Después de crear o incrementar un objeto de clase istream_iterator con un puntero almacenado no null, el objeto intenta extraer y almacenar un objeto de tipo `Type` del flujo de entrada asociado. Si se produce un error en la extracción, el objeto reemplaza el puntero almacenado con un puntero NULL, creando de esta forma un indicador de fin de secuencia.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[istream_iterator](#istream_iterator)|Construye un iterador de fin de secuencia como `istream_iterator` predeterminado, o bien un `istream_iterator` inicializado en el tipo de flujo del iterador del que lee.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que proporciona el tipo de los caracteres de `istream_iterator`.|
|[istream_type](#istream_type)|Tipo que proporciona el tipo de flujo de `istream_iterator`.|
|[traits_type](#traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|El operador de desreferencia devuelve el objeto almacenado de tipo `Type` señalado por `istream_iterator`.|
|[>operador](#op_arrow)|Devuelve el valor de un miembro, si existe.|
|[operador++](#op_add_add)|Extrae un objeto incrementado del flujo de entrada o copia el objeto antes de aumentarlo y devuelve la copia.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="istream_iteratorchar_type"></a><a name="char_type"></a>istream_iterator::char_type

Tipo que proporciona el tipo de los caracteres de `istream_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Chartype`.

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '2 4 f' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoristream_iterator"></a><a name="istream_iterator"></a>istream_iterator::istream_iterator

Construye un iterador de fin de secuencia como `istream_iterator` predeterminado, o bien un `istream_iterator` inicializado en el tipo de flujo del iterador del que lee.

```cpp
istream_iterator();

istream_iterator(istream_type& _Istr);
```

### <a name="parameters"></a>Parámetros

*_Istr*\
Flujo de entrada que se va a leer usado para inicializar `istream_iterator`.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el puntero del flujo de entrada con un puntero null y crea un iterador de fin de flujo. El segundo constructor inicializa el *&_Istr*puntero de secuencia de entrada con `Type`&_Istr y, a continuación, intenta extraer y almacenar un objeto de tipo .

El iterador de fin de flujo se puede usar para probar si `istream_iterator` ha llegado al final de un flujo.

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_istream_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   // Used in conjunction with copy algorithm
   // to put elements into a vector read from cin
   vector<int> vec ( 4 );
   vector <int>::iterator Iter;

   cout << "Enter 4 integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";
   istream_iterator<int> intvecRead ( cin );

   // Default constructor will test equal to end of stream
   // for delimiting source range of vecor
   copy ( intvecRead , istream_iterator<int>( ) , vec.begin ( ) );
   cin.clear ( );

   cout << "vec = ";
   for ( Iter = vec.begin( ) ; Iter != vec.end( ) ; Iter++ )
      cout << *Iter << " "; cout << endl;
}
```

## <a name="istream_iteratoristream_type"></a><a name="istream_type"></a>istream_iterator::istream_type

Tipo que proporciona el tipo de flujo de `istream_iterator`.

```cpp
typedef basic_istream<CharType, Traits> istream_type;
```

### <a name="remarks"></a>Observaciones

El tipo es `basic_istream` \< un sinónimo de **CharType**, **Traits**>.

### <a name="example"></a>Ejemplo

Vea [istream_iterator](#istream_iterator) para obtener un ejemplo de cómo declarar y usar `istream_type`.

## <a name="istream_iteratoroperator"></a><a name="op_star"></a>istream_iterator::operador*

El operador de desreferencia devuelve el objeto almacenado de tipo `Type` señalado por `istream_iterator`.

```cpp
const Type& operator*() const;
```

### <a name="return-value"></a>Valor devuelto

El objeto almacenado `Type`de tipo .

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_operator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoroperator-gt"></a><a name="op_arrow"></a>istream_iterator::operador-&gt;

Devuelve el valor de un miembro, si existe.

```cpp
const Type* operator->() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de un miembro, si existe.

### <a name="remarks"></a>Observaciones

`i->m` equivale a `(*i).m`.

El operador devuelve `&*this`.

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_operator_vm.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>
#include <complex>

using namespace std;

int main( )
{
   cout << "Enter complex numbers separated by spaces & then\n"
        << " a character pair ( try example: '(1,2) (3,4) (a,b)' ): ";

   // istream_iterator from stream cin
   istream_iterator< complex<double> > intRead ( cin );

   // End-of-stream iterator
   istream_iterator<complex<double> > EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading the real part: " << intRead ->real( ) << endl;
      cout << "Reading the imaginary part: " << intRead ->imag( ) << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratoroperator"></a><a name="op_add_add"></a>istream_iterator::operador++

Extrae un objeto incrementado del flujo de entrada o copia el objeto antes de aumentarlo y devuelve la copia.

```cpp
istream_iterator<Type, CharType, Traits, Distance>& operator++();

istream_iterator<Type, CharType, Traits, Distance> operator++(int);
```

### <a name="return-value"></a>Valor devuelto

El primer operador miembro devuelve una referencia `Type` al objeto incrementado de tipo extraído de la secuencia de entrada y la segunda función miembro devuelve una copia del objeto.

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_operator_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <algorithm>
#include <iostream>

int main( )
{
   using namespace std;

   cout << "Enter integers separated by spaces & then\n"
        << " a character ( try example: '2 4 6 8 a' ): ";

   // istream_iterator from stream cin
   istream_iterator<int> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="istream_iteratortraits_type"></a><a name="traits_type"></a>istream_iterator::traits_type

Tipo que proporciona el tipo de rasgos de los caracteres de `istream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla *Traits*.

### <a name="example"></a>Ejemplo

```cpp
// istream_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <iostream>

int main( )
{
   using namespace std;

   typedef istream_iterator<int>::char_type CHT1;
   typedef istream_iterator<int>::traits_type CHTR1;

   // Standard iterator interface for reading
   // elements from the input stream:
   cout << "Enter integers separated by spaces & then\n"
        << " any character ( try example: '10 20 a' ): ";

   // istream_iterator for reading int stream
   istream_iterator<int, CHT1, CHTR1> intRead ( cin );

   // End-of-stream iterator
   istream_iterator<int, CHT1, CHTR1> EOFintRead;

   while ( intRead != EOFintRead )
   {
      cout << "Reading:  " << *intRead << endl;
      ++intRead;
   }
   cout << endl;
}
```

## <a name="see-also"></a>Consulte también

[input_iterator_tag Struct](../standard-library/input-iterator-tag-struct.md)\
[iterador Struct](../standard-library/iterator-struct.md)\
[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
