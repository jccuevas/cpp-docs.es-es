---
title: ostreambuf_iterator
ms.date: 11/04/2016
f1_keywords:
- streambuf/std::ostreambuf_iterator
- iterator/std::ostreambuf_iterator::char_type
- iterator/std::ostreambuf_iterator::ostream_type
- iterator/std::ostreambuf_iterator::streambuf_type
- iterator/std::ostreambuf_iterator::traits_type
- iterator/std::ostreambuf_iterator::failed
helpviewer_keywords:
- std::ostreambuf_iterator [C++]
- std::ostreambuf_iterator [C++], char_type
- std::ostreambuf_iterator [C++], ostream_type
- std::ostreambuf_iterator [C++], streambuf_type
- std::ostreambuf_iterator [C++], traits_type
- std::ostreambuf_iterator [C++], failed
ms.assetid: dad1e624-2f45-4e94-8887-a885e95f9071
ms.openlocfilehash: 8e9fa10888b511ad2a500f64faf610dc7dd5ba03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373561"
---
# <a name="ostreambuf_iterator-class"></a>ostreambuf_iterator

La plantilla de clase ostreambuf_iterator describe un objeto de iterador de salida que escribe elementos de carácter sucesivos en la secuencia de salida con el operador de extracción **>>**. Los objetos `ostreambuf_iterator`s se diferencian de los de la [clase ostream_iterator](../standard-library/ostream-iterator-class.md) en que tienen caracteres en lugar de un tipo genérico en el tipo de objeto que se inserta en el flujo de salida.

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType = char class Traits = char_traits <CharType>>
```

### <a name="parameters"></a>Parámetros

*CharType*\
Tipo que representa el tipo de caracteres para ostreambuf_iterator. Este argumento es opcional y el valor predeterminado es **char**.

*Rasgos*\
Tipo que representa el tipo de caracteres para ostreambuf_iterator. Este argumento es opcional y el valor predeterminado es `char_traits`\< *CharType>.*

## <a name="remarks"></a>Observaciones

La clase ostreambuf_iterator debe satisfacer los requisitos de un iterador de salida. Los algoritmos se pueden escribir directamente en el flujo de salida mediante `ostreambuf_iterator`. La clase proporciona un iterador de flujo de bajo nivel que permite acceso al flujo raw (sin formato) de E/S en forma de caracteres y la capacidad de omitir las traslaciones de caracteres y el almacenamiento en búfer asociados a los iteradores de flujo de alto nivel.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator)|Construye un objeto `ostreambuf_iterator` que se inicializa para escribir caracteres en el flujo de salida.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|[char_type](#char_type)|Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.|
|[ostream_type](#ostreambuf_iterator_ostream_type)|Tipo que proporciona el tipo de flujo de `ostream_iterator`.|
|[streambuf_type](#streambuf_type)|Tipo que proporciona el tipo de flujo de `ostreambuf_iterator`.|
|[traits_type](#traits_type)|Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Fallado](#failed)|Comprueba si hay errores en una inserción en el búfer del flujo de salida.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador*](#op_star)|Operador de desreferenciación utilizado \* `i`  =  `x`para implementar la expresión de iterador de salida.|
|[operador++](#op_add_add)|Operador de incremento no funcional que devuelve un objeto `ostreambuf_iterator` al mismo objeto que señalaba antes de que se llamara a la operación.|
|[operador](#op_eq)|El operador inserta un carácter en el búfer del flujo asociado.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<iterator>

**Espacio de nombres:** std

## <a name="ostreambuf_iteratorchar_type"></a><a name="char_type"></a>ostreambuf_iterator::char_type

Tipo que proporciona el tipo de los caracteres de `ostreambuf_iterator`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `CharType`.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_char_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="ostreambuf_iteratorfailed"></a><a name="failed"></a>ostreambuf_iterator::falló

Comprueba si hay errores en una inserción en el búfer del flujo de salida.

```cpp
bool failed() const throw();
```

### <a name="return-value"></a>Valor devuelto

**True** si no se han producido errores anteriormente en ninguna inserción del búfer del flujo de salida; de otro modo **False**.

### <a name="remarks"></a>Observaciones

La función miembro devuelve **True** si, en algún uso anterior del miembro `operator=`, la llamada a **subf**_-> `sputc` ha devuelto **eof**.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_failed.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'a';
   charOut ++;
*charOut  = 'b';
   charOut ++;
*charOut = 'c';
   cout << " are characters output individually." << endl;

   bool b1 = charOut.failed ( );
   if (b1)
       cout << "At least one insertion failed." << endl;
   else
       cout << "No insertions failed." << endl;
}
/* Output:
abc are characters output individually.
No insertions failed.
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_star"></a>ostreambuf_iterator::operador\*

Un operador de desreferenciación no funcional \* utilizado para implementar la expresión de iterador de salida *i* = *x*.

```cpp
ostreambuf_iterator<CharType, Traits>& operator*();
```

### <a name="return-value"></a>Valor devuelto

El objeto de iterador ostreambuf.

### <a name="remarks"></a>Observaciones

Este operador solo funciona en \* la expresión de iterador de salida *i* = *x* para generar caracteres en el búfer de secuencia. Aplicado a un iterador ostreambuf, devuelve el iterador; iter devuelve **iter**, ** \***

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_op_deref.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;   // no effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_add_add"></a>ostreambuf_iterator::operador++

Un operador de incremento no funcional que devuelve un iterador ostream al mismo carácter que señalaba antes de que se llamara a la operación.

```cpp
ostreambuf_iterator<CharType, Traits>& operator++();
ostreambuf_iterator<CharType, Traits>& operator++(int);
```

### <a name="return-value"></a>Valor devuelto

Una referencia al carácter que se ha direccionado originalmente o a un objeto definido por una implementación que puede convertirse en `ostreambuf_iterator`\< **CharType**, **Traits**>.

### <a name="remarks"></a>Observaciones

El operador se utiliza para \* implementar la expresión de iterador de salida *i* = *x*.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_op_incr.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratoroperator"></a><a name="op_eq"></a>ostreambuf_iterator::operador ?

El operador inserta un carácter en el búfer del flujo asociado.

```cpp
ostreambuf_iterator<CharType, Traits>& operator=(CharType _Char);
```

### <a name="parameters"></a>Parámetros

*_Char*\
El carácter que se va a insertar en el búfer de secuencia.

### <a name="return-value"></a>Valor devuelto

Una referencia al carácter insertado en el búfer de secuencia.

### <a name="remarks"></a>Observaciones

Operador de asignación utilizado \* para implementar la expresión de iterador de salida *i* = *x* para escribir en una secuencia de salida.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_op_assign.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   // with new line delimiter
   ostreambuf_iterator<char> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output stream
   cout << "Elements written to output stream:" << endl;
*charOutBuf = 'O';
   charOutBuf++;      // No effect on iterator position
*charOutBuf = 'U';
*charOutBuf = 'T';
}
/* Output:
Elements written to output stream:
OUT
*/
```

## <a name="ostreambuf_iteratorostreambuf_iterator"></a><a name="ostreambuf_iterator_ostreambuf_iterator"></a>ostreambuf_iterator::ostreambuf_iterator

Construye un objeto `ostreambuf_iterator` que se inicializa para escribir caracteres en el flujo de salida.

```cpp
ostreambuf_iterator(streambuf_type* strbuf) throw();
ostreambuf_iterator(ostream_type& Ostr) throw();
```

### <a name="parameters"></a>Parámetros

*strbuf*\
El objeto streambuf de salida que se ha usado para inicializar el puntero de búfer de flujo de salida.

*Ostr*\
El objeto de flujo de salida que se ha usado para inicializar el puntero de búfer de flujo de salida.

### <a name="remarks"></a>Observaciones

El primer constructor inicializa el puntero de búfer de secuencia de salida con *strbuf*.

El segundo constructor inicializa el puntero de búfer de flujo de salida con `Ostr`. `rdbuf`. El puntero almacenado no debe ser un puntero nulo.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iteratorOstreambuf_iterator.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   // ostreambuf_iterator for stream cout
   ostreambuf_iterator<char> charOut ( cout );

*charOut = 'O';
   charOut ++;
*charOut  = 'U';
   charOut ++;
*charOut = 'T';
   cout << " are characters output individually." << endl;

   ostreambuf_iterator<char> strOut ( cout );
   string str = "These characters are being written to the output stream.\n ";
   copy ( str.begin ( ), str. end ( ), strOut );
}
/* Output:
OUT are characters output individually.
These characters are being written to the output stream.
*/
```

## <a name="ostreambuf_iteratorostream_type"></a><a name="ostreambuf_iterator_ostream_type"></a>ostreambuf_iterator::ostream_type

Tipo que proporciona el tipo de flujo de `ostream_iterator`.

```cpp
typedef basicOstream<CharType, Traits> ostream_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo para `basicOstream`\< **CharType**, **Traits**>

### <a name="example"></a>Ejemplo

Vea [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `ostream_type`.

## <a name="ostreambuf_iteratorstreambuf_type"></a><a name="streambuf_type"></a>ostreambuf_iterator::streambuf_type

Tipo que proporciona el tipo de flujo de `ostreambuf_iterator`.

```cpp
typedef basic_streambuf<CharType, Traits> streambuf_type;
```

### <a name="remarks"></a>Observaciones

El tipo es `basic_streambuf` un sinónimo de \< **CharType**, **Traits**>, una `streambuf` clase de secuencia para búferes de E/S que se convierte en un sinónimo de tipo de carácter **char**.

### <a name="example"></a>Ejemplo

Vea [ostreambuf_iterator](#ostreambuf_iterator_ostreambuf_iterator) para obtener un ejemplo de cómo declarar y usar `streambuf_type`.

## <a name="ostreambuf_iteratortraits_type"></a><a name="traits_type"></a>ostreambuf_iterator::traits_type

Tipo que proporciona el tipo de rasgos de los caracteres de `ostream_iterator`.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo del parámetro de plantilla `Traits`.

### <a name="example"></a>Ejemplo

```cpp
// ostreambuf_iterator_traits_type.cpp
// compile with: /EHsc
#include <iterator>
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;

   typedef ostreambuf_iterator<char>::char_type CHT1;
   typedef ostreambuf_iterator<char>::traits_type CHTR1;

   // ostreambuf_iterator for stream cout
   // with new line delimiter:
    ostreambuf_iterator< CHT1, CHTR1> charOutBuf ( cout );

   // Standard iterator interface for writing
   // elements to the output streambuf:
   cout << "The characters written to the output stream\n"
        << " by charOutBuf are: ";
*charOutBuf = 'O';
   charOutBuf++;
*charOutBuf = 'U';
   charOutBuf++;
*charOutBuf = 'T';
   charOutBuf++;
   cout << "." << endl;
}
/* Output:
The characters written to the output stream
by charOutBuf are: OUT.
*/
```

## <a name="see-also"></a>Consulte también

[\<iterador>](../standard-library/iterator.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de la biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)
