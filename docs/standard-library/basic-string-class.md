---
title: basic_string (Clase)
ms.date: 11/12/2019
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::swap
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 08620e0ae6b54b106daba8e0b0a392ceb1a6577d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821914"
---
# <a name="basic_string-class"></a>basic_string (Clase)

Las secuencias controladas por un objeto de tipo `basic_string` son la C++ clase de cadena estándar y se suelen denominar cadenas, pero no se deben confundir con las cadenas de estilo C terminadas en NULL C++ que se usan en la biblioteca estándar. La cadena de C++ estándar es un contenedor que permite usar cadenas como tipos normales, por ejemplo, operaciones de comparación y concatenación, iteradores, algoritmos de la biblioteca estándar de C++, y copiar y asignar con la memoria administrada del asignador de clases. Si necesita convertir una cadena de C++ estándar en una cadena de estilo C terminada en null, use el miembro [basic_string::c_str](#c_str).

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>Parameters

\ *CharType*
El tipo de datos de un carácter único que se almacenará en la cadena. La C++ biblioteca estándar proporciona especializaciones de esta plantilla de clase, con la [cadena](../standard-library/string-typedefs.md#string) de definiciones de tipo para elementos de tipo **char**, [wstring](../standard-library/string-typedefs.md#wstring), para **wchar_t**, [u16string](../standard-library/string-typedefs.md#u16string) para `char16_t`y [u32string](../standard-library/string-typedefs.md#u32string) para `char32_t`.

*Rasgos*\
La clase `Traits`describe diversas propiedades importantes de los elementos `CharType` de una especialización basic_string. El valor predeterminado es `char_traits`< `CharType`>.

\ de *asignador*
El tipo que representa el objeto asignador almacenado que encapsula los detalles sobre la asignación y la desasignación de memoria de la cadena. El valor predeterminado es **allocator**< `CharType`>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_string](#basic_string)|Crea una cadena que está vacía, que inicializan caracteres específicos o que es una copia total o parcial de algún otro objeto de cadena o alguna otra cadena de C.|

### <a name="typedefs"></a>Definiciones de tipo

|Nombre de tipo|Descripción|
|-|-|
|[allocator_type](#allocator_type)|Tipo que representa la clase `allocator` para un objeto de cadena.|
|[const_iterator](#const_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede acceder a un elemento **const** de la cadena y leerlo.|
|[const_pointer](#const_pointer)|Tipo que proporciona un puntero a un elemento **const** en una cadena.|
|[const_reference](#const_reference)|Tipo que proporciona una referencia a un elemento **const** almacenado en una cadena para leer operaciones **const** y ejecutarlas.|
|[const_reverse_iterator](#const_reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento **const** en la cadena.|
|[difference_type](#difference_type)|Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma cadena.|
|[iterator](#iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar cualquier elemento de una cadena.|
|[npos](#npos)|Un valor entero sin signo inicializado en-1 que indica "no se encontró" o "todos los caracteres restantes" cuando se produce un error en una función de búsqueda.|
|[pointer](#pointer)|Tipo que proporciona un puntero a un elemento de carácter de una cadena o una matriz de caracteres.|
|[reference](#reference)|Tipo que proporciona una referencia a un elemento almacenado en una cadena.|
|[reverse_iterator](#reverse_iterator)|Tipo que proporciona un iterador de acceso aleatorio que puede leer o modificar un elemento de una cadena invertida.|
|[size_type](#size_type)|Tipo entero sin signo para el número de elementos de una cadena.|
|[traits_type](#traits_type)|Tipo de los rasgos de carácter de los elementos almacenados en una cadena.|
|[value_type](#value_type)|Tipo que representa el tipo de caracteres que se almacenan en una cadena.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[append](#append)|Agrega caracteres al final de una cadena.|
|[assign](#assign)|Asigna nuevos valores de caracteres al contenido de una cadena.|
|[at](#at)|Devuelve una referencia al elemento situado en una ubicación especificada de la cadena.|
|[back](#back)||
|[begin](#begin)|Devuelve un iterador que dirige al primer elemento de la cadena.|
|[c_str](#c_str)|Convierte el contenido de una cadena en una cadena de estilo C terminada en null.|
|[capacity](#capacity)|Devuelve el número máximo de elementos que podrían almacenarse en una cadena sin aumentar la asignación de memoria de la cadena.|
|[cbegin](#cbegin)|Devuelve un iterador constante que dirige al primer elemento de la cadena.|
|[cend](#cend)|Devuelve un iterador constante que dirige a la ubicación que sigue al último elemento de una cadena.|
|[clear](#clear)|Borra todos los elementos de una cadena.|
|[compare](#compare)|Compara una cadena con una cadena especificada para determinar si las dos cadenas son iguales o si una es lexicográficamente menor que la otra.|
|[copy](#copy)|Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino. Opción obsoleta. Use [basic_string::_Copy_s](#copy_s) en su lugar.|
|[crbegin](#crbegin)|Devuelve un iterador constante que dirige al primer elemento de una cadena invertida.|
|[crend](#crend)|Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una cadena invertida.|
|[_Copy_s](#copy_s)|Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino.|
|[data](#data)|Convierte el contenido de una cadena en una matriz de caracteres.|
|[empty](#empty)|Comprueba si la cadena contiene caracteres.|
|[end](#end)|Devuelve un iterador que dirige a la ubicación siguiente al último elemento de una cadena.|
|[erase](#erase)|Quita un elemento o un intervalo de elementos de una cadena de una posición especificada.|
|[find](#find)|Busca hacia delante en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.|
|[find_first_not_of](#find_first_not_of)|Busca en una cadena el primer carácter que no es ningún elemento de una cadena especificada.|
|[find_first_of](#find_first_of)|Busca en una cadena el primer carácter que coincide con algún elemento de una cadena especificada.|
|[find_last_not_of](#find_last_not_of)|Busca en una cadena el último carácter que no es ningún elemento de una cadena especificada.|
|[find_last_of](#find_last_of)|Busca en una cadena el último carácter que es un elemento de una cadena especificada.|
|[front](#front)|Devuelve una referencia al primer elemento de una cadena.|
|[get_allocator](#get_allocator)|Devuelve una copia del objeto `allocator` que se usa para construir la cadena.|
|[insert](#insert)|Inserta un elemento, varios elementos o un intervalo de elementos en la cadena en una posición especificada.|
|[length](#length)|Devuelve el número actual de elementos de una cadena.|
|[max_size](#max_size)|Devuelve el número máximo de caracteres que puede contener una cadena.|
|[pop_back](#pop_back)|Borra el último elemento de la cadena.|
|[push_back](#push_back)|Agrega un elemento al final de la cadena.|
|[rbegin](#rbegin)|Devuelve un iterador al primer elemento de una cadena invertida.|
|[rend](#rend)|Devuelve un iterador que apunta al lugar inmediatamente posterior al último elemento de una cadena invertida.|
|[replace](#replace)|Reemplaza los elementos de una cadena situados en la posición especificada por los caracteres especificados o los caracteres copiados de otros intervalos, cadenas o cadenas de C.|
|[reserve](#reserve)|Configura la capacidad de la cadena con un número que es, al menos, tan alto como un número especificado.|
|[resize](#resize)|Especifica un nuevo tamaño para una cadena y anexa o borra elementos según sea necesario.|
|[rfind](#rfind)|Busca hacia atrás en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.|
|[shrink_to_fit](#shrink_to_fit)|Descarta el exceso de capacidad de la cadena.|
|[size](#size)|Devuelve el número actual de elementos de una cadena.|
|[substr](#substr)|Copia una subcadena de, como máximo, un número de caracteres de una cadena, empezando desde la posición especificada.|
|[swap](#swap)|Intercambie el contenido de dos cadenas.|

### <a name="operators"></a>Operadores

|"??"|Descripción|
|-|-|
|[operator+=](#op_add_eq)|Anexa caracteres a una cadena.|
|[operator=](#op_eq)|Asigna nuevos valores de caracteres al contenido de una cadena.|
|[operator&#91;&#93;](#op_at)|Proporciona una referencia al carácter de una cadena que tiene el índice especificado.|

## <a name="remarks"></a>Notas

Si se pide a una función que genere una secuencia de más de [max_size](#max_size) elementos, la función notifica un error de longitud al iniciar un objeto de tipo [length_error](../standard-library/length-error-class.md).

Las referencias, los punteros y los iteradores que designan elementos de la secuencia controlada pueden perder su validez después de que se realice cualquier llamada a una función que modifique la secuencia controlada o después de la primera llamada a una función miembro no **const**.

## <a name="requirements"></a>Requisitos de

**Encabezado:** \<cadena >

**Espacio de nombres:** std

## <a name="allocator_type"></a>  basic_string::allocator_type

Tipo que representa la clase de asignador de un objeto de cadena.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Notas

El tipo es un sinónimo del parámetro de plantilla `Allocator`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="append"></a>  basic_string::append

Agrega caracteres al final de una cadena.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameters

\ *ptr*
Cadena de C que se va a anexar.

\ *Str*
Cadena cuyos caracteres se van a anexar.

\ de *desplazamiento*
Índice de la parte de la cadena de origen que proporciona los caracteres que se va a anexar.

*recuento*\
Número máximo de caracteres que se van a anexar desde la cadena de origen.

*char_value*\
Valor de carácter que se va a anexar.

*primer*\
Iterador de entrada que dirige al primer elemento del intervalo que se va a anexar.

*última*\
Iterador de entrada, const_pointer o const_iterator que dirige a la posición situada una posición después del último elemento del intervalo que se va a anexar.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena que se está anexando con los caracteres pasados por la función miembro.

### <a name="remarks"></a>Notas

Los caracteres se pueden anexar a una cadena mediante [Operator + =](#op_add_eq) o las funciones miembro `append` o [push_back](#push_back). `operator+=` anexa valores de un solo argumento, mientras que la función miembro de varios argumentos `append` permite especificar una parte específica de una cadena para agregarla.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="assign"></a>  basic_string::assign

Asigna nuevos valores de caracteres al contenido de una cadena.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameters

\ *ptr*
Puntero a los caracteres de la cadena de C que se va a asignar a la cadena de destino.

*recuento*\
Número de caracteres que se van a asignar a partir de la cadena de origen.

\ *Str*
Cadena de origen cuyos caracteres se van a asignar a la cadena de destino.

*char_value*\
Valor de carácter que se va a asignar.

*primer*\
Iterador de entrada, const_pointer o const_iterator que dirige al primer carácter del intervalo de la cadena de origen que se va a asignar al intervalo de destino.

*última*\
Iterador de entrada, const_pointer o const_iterator que dirige al carácter situado un carácter después del último del intervalo de la cadena de origen que se va a asignar al intervalo de destino.

*desactivado*\
Posición en la que se va a empezar a asignar a los nuevos caracteres.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena al que la función miembro está asignando nuevos caracteres.

### <a name="remarks"></a>Notas

Es posible asignar nuevos valores de caracteres a las cadenas. El nuevo valor puede ser una cadena y una cadena de C o un solo carácter. Se puede usar el [operador =](#op_eq) si el nuevo valor se puede describir mediante un solo parámetro; de lo contrario, se puede usar la función miembro `assign`, que tiene varios parámetros, para especificar qué parte de la cadena se va a asignar a una cadena de destino.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="at"></a>  basic_string::at

Proporciona una referencia al carácter de una cadena que tiene el índice especificado.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>Parameters

\ de *desplazamiento*
Índice de la posición del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Referencia al carácter de la cadena en la posición especificada por el índice de parámetro.

### <a name="remarks"></a>Notas

El primer elemento de la cadena tiene un índice de cero y los enteros positivos indizan de forma consecutiva los siguientes elementos, de modo que una cadena de longitud *n* *tenga un elemento enésimo*indizado por el número *n-* 1.

El [operador&#91; ](#op_at) miembro es más rápido que la función miembro `at` para proporcionar acceso de lectura y escritura a los elementos de una cadena.

El `operator[]` miembro no comprueba si el índice pasado como parámetro es válido, pero la función miembro `at` realiza y, por lo tanto, debe usarse si la validez no es cierta. Índice no válido, que es un índice menor que cero o mayor o igual que el tamaño de la cadena, que se pasa a la función miembro `at` produce una excepción de [clase out_of_range](../standard-library/out-of-range-class.md) . Un índice no válido pasado a `operator[]` tiene como resultado un comportamiento indefinido, pero el índice igual a la longitud de la cadena es un índice válido para cadenas const y el operador devuelve el carácter nulo cuando se ha pasado este índice.

La referencia devuelta puede ser anulada por las reasignaciones de cadena o las modificaciones de las cadenas no **const**.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="back"></a>  basic_string::back

Devuelve una referencia al último elemento de la cadena.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>Valor devuelto

Referencia al último elemento de la cadena, que no debe estar vacío.

### <a name="remarks"></a>Notas

## <a name="basic_string"></a>  basic_string::basic_string

Crea una cadena que está vacía, que inicializan caracteres específicos o que es una copia total o parcial de algún otro objeto de cadena o alguna otra cadena (terminada en null) de C.

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameters

\ *ptr*
Cadena de C cuyos caracteres se van a usar para inicializar el `string` que se crea. Este valor no puede ser un puntero nulo.

*alloc_type*\
Clase de asignador de almacenamiento para el objeto de cadena que se crea.

*recuento*\
Número de caracteres que se van a inicializar.

\ *derecha*
Cadena que inicializa la cadena que se crea.

*right_offset*\
Índice de un carácter en una cadena que es el primero que se utilizará para inicializar los valores de caracteres para la cadena que se crea.

*char_value*\
Valor de carácter que se copia en la cadena que se crea.

*primer*\
Iterador de entrada, const_pointer o const_iterator, que dirige el primer elemento del intervalo de origen que se va a insertar.

*última*\
Iterador de entrada, const_pointer o const_iterator, que dirige la posición que está más allá del último elemento del intervalo de origen que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena que se crea con los constructores.

### <a name="remarks"></a>Notas

Todos los constructores almacenan [basic_string::allocator_type](#allocator_type) e inicializan la secuencia controlada. El objeto de asignador es el argumento `al`, si existe. Para el constructor de copias, es `right.`[basic_string:: get_allocator](#get_allocator)`()`. De lo contrario, se `Alloc()`el asignador.

La secuencia controlada se inicializa con una copia de la secuencia de operandos especificada por los operandos restantes. Un constructor sin una secuencia de operandos especifica una secuencia controlada inicial vacía. Si `InputIterator` es un tipo entero en un constructor de plantilla, la secuencia de operandos `first,  last` se comporta igual que `(size_type) first, (value_type) last`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="begin"></a>  basic_string::begin

Devuelve un iterador que dirige al primer elemento de la cadena.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio que dirige al primer elemento de la secuencia o justo después del final de una secuencia vacía.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="c_str"></a>  basic_string::c_str

Convierte el contenido de una cadena en una cadena de estilo C terminada en null.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la versión de estilo C de la cadena que llama.  El valor de puntero no es válido después de llamar a una función no const, incluido el destructor, en la clase basic_string en el objeto.

### <a name="remarks"></a>Notas

Los objetos de tipo String que pertenecen a la plantilla de clase basic_string\<char > no tienen por qué terminar con NULL. El carácter nulo '\0' se usa como un carácter especial en una cadena de C para marcar el final de la cadena, pero no tiene ningún significado especial en un objeto de cadena de tipo y puede ser una parte de la cadena igual que cualquier otro carácter. Hay una conversión automática de **const char** <strong>\*</strong> en cadenas, pero la clase String no proporciona conversiones automáticas de cadenas de estilo C a objetos de tipo **basic_string\<char >** .

No se debe modificar la cadena de estilo C devuelta, ya que esto podría invalidar el puntero a la cadena, o eliminar, ya que la cadena tiene una duración limitada y es propiedad de la cadena de clase.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="capacity"></a>  basic_string::capacity

Devuelve el número máximo de elementos que podrían almacenarse en una cadena sin aumentar la asignación de memoria de la cadena.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño de almacenamiento asignado actualmente en memoria para conservar la cadena.

### <a name="remarks"></a>Notas

La función miembro devuelve el almacenamiento asignado actualmente para conservar la secuencia controlada, un valor al menos tan grande como [size](#size).

### <a name="example"></a>Ejemplo

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="cbegin"></a>  basic_string::cbegin

Devuelve un iterador **const** que direcciona el primer elemento del intervalo.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador **const** de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

### <a name="remarks"></a>Notas

Con el valor devuelto de `cbegin`, los elementos del intervalo no se pueden modificar.

Se puede usar esta función miembro en lugar de la función miembro `begin()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere `Container` ser un contenedor modificable (no **const**) de cualquier tipo que admita `begin()` y `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  basic_string::cend

Devuelve un iterador **const** que direcciona la ubicación situada más allá del último elemento de un intervalo.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Valor devuelto

Un iterador **const** de acceso aleatorio que apunta justo después del final del intervalo.

### <a name="remarks"></a>Notas

`cend` se usa para probar si un iterador ha sobrepasado el final de su intervalo.

Se puede usar esta función miembro en lugar de la función miembro `end()` para garantizar que el valor devuelto es `const_iterator`. Normalmente, se usa junto con la palabra clave de deducción de tipos [auto](../cpp/auto-cpp.md), como se muestra en el ejemplo siguiente. En el ejemplo, considere `Container` ser un contenedor modificable (no **const**) de cualquier tipo que admita `end()` y `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

No se debe desreferenciar el valor devuelto por `cend`.

## <a name="clear"></a>  basic_string::clear

Borra todos los elementos de una cadena.

```cpp
void clear();
```

### <a name="remarks"></a>Notas

La cadena en la que se llama a la función miembro estará vacía.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="compare"></a>  basic_string::compare

Realiza una comparación que distingue entre mayúsculas y minúsculas con una cadena especificada para determinar si las dos cadenas son iguales o si una es lexicográficamente menor que la otra.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>Parameters

\ *Str*
Cadena que se va a comparar con la cadena de operando.

*position_1*\
Índice de la cadena de operando en la que comienza la comparación.

*number_1*\
Número máximo de caracteres de la cadena de operando que se va a comparar.

*number_2*\
Número máximo de caracteres de la cadena de parámetro que se va a comparar.

\ de *desplazamiento*
Índice de la cadena de parámetro en la que comienza la comparación.

*recuento*\
Número máximo de caracteres de la cadena de parámetro que se va a comparar.

\ *ptr*
Cadena de C que se va a comparar con la cadena de operando.

### <a name="return-value"></a>Valor devuelto

Valor negativo si la cadena de operando es menor que la cadena de parámetro; cero si las dos cadenas son iguales; o un valor positivo si la cadena de operando es mayor que la cadena de parámetro.

### <a name="remarks"></a>Notas

Las funciones miembro `compare` comparan la totalidad o parte de las cadenas de parámetro y de operando en función de las que se utilizan en.

La comparación realizada distingue entre mayúsculas y minúsculas.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="const_iterator"></a>  basic_string::const_iterator

Tipo que proporciona un iterador de acceso aleatorio que puede acceder a un elemento **const** de la cadena y leerlo.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Notas

Un tipo `const_iterator` no se puede usar para modificar el valor de un carácter y se usa para iterar una cadena hacia delante.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar `const_iterator`.

## <a name="const_pointer"></a>  basic_string::const_pointer

Tipo que proporciona un puntero a un elemento **const** en una cadena.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Notas

El tipo es un sinónimo de `allocator_type::const_pointer`.

Para el tipo `string`, es equivalente a `char*`.

Los punteros declarados const se deben inicializar al declararse. Los punteros const siempre apuntan a la misma ubicación de memoria y pueden apuntar a datos const o no const.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="const_reference"></a>  basic_string::const_reference

Tipo que proporciona una referencia a un elemento **const** almacenado en una cadena para leer operaciones **const** y ejecutarlas.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>Notas

Un tipo `const_reference` no se puede utilizar para modificar el valor de un elemento.

El tipo es un sinónimo de `allocator_type::const_reference`. En el caso de `type`de cadena, es equivalente a const `char&`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [at](#at) para obtener un ejemplo de cómo declarar y usar `const_reference`.

## <a name="const_reverse_iterator"></a>  basic_string::const_reverse_iterator

Tipo que proporciona un iterador de acceso aleatorio que puede leer cualquier elemento **const** en la cadena.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Notas

Un tipo `const_reverse_iterator` no puede modificar el valor de un carácter. Se usa para iterar una cadena en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `const_reverse_iterator`.

## <a name="copy"></a>  basic_string::copy

Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino.

Este método es potencialmente inseguro, ya que se basa en el llamador para comprobar que los valores pasados son correctos. Plantéese usar [basic_string::_Copy_s](#copy_s) en su lugar.

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parameters

\ *ptr*
Matriz de caracteres de destino en la que van a copiarse los elementos.

*recuento* Número de caracteres que se va a copiar, como máximo, de la cadena de origen.

\ de *desplazamiento*
Posición inicial de la cadena de origen a partir de la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Notas

Un carácter nulo no se anexa al final de la copia.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="crbegin"></a>  basic_string::crbegin

Devuelve un iterador constante que dirige al primer elemento de una cadena invertida.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador inverso que apunta a la posición que se encuentra justo después del final de la cadena. La posición designa el principio de la cadena inversa.

## <a name="crend"></a>  basic_string::crend

Devuelve un iterador constante que dirige a la ubicación siguiente al último elemento de una cadena invertida.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Valor devuelto

Iterador constante inverso que dirige a la ubicación siguiente al último elemento de una cadena invertida (la ubicación que había precedido al primer elemento de la cadena sin invertir).

### <a name="remarks"></a>Notas

## <a name="copy_s"></a>  basic_string::_Copy_s

Copia, como máximo, un número especificado de caracteres de una posición indexada de una cadena de origen a una matriz de caracteres de destino.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parameters

\ de *destino*
Matriz de caracteres de destino en la que van a copiarse los elementos.

*dest_size*\
Tamaño del *destino*.

*recuento* Número de caracteres que se va a copiar, como máximo, de la cadena de origen.

\ de *desplazamiento*
Posición inicial de la cadena de origen a partir de la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Notas

Un carácter nulo no se anexa al final de la copia.

### <a name="example"></a>Ejemplo

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="data"></a>  basic_string::data

Convierte el contenido de una cadena en una matriz de caracteres terminada en NULL.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero al primer elemento de la matriz terminada en null que contiene el contenido de la cadena. En el caso de una cadena vacía, el puntero apunta a un único carácter nulo igual a `value_type()`.

### <a name="remarks"></a>Notas

El puntero devuelto por `data` puntos en un intervalo válido `[data(), data() + size()]`. Cada elemento del intervalo corresponde a los datos actuales de la cadena. Es decir, para cada desplazamiento válido *n* en el intervalo, `data() + n == addressof(operator[](n))`.

Si modifica el contenido de la cadena devuelta por la sobrecarga **const** de `data`, el comportamiento es indefinido. También obtiene un comportamiento indefinido si el carácter nulo del terminal se cambia a cualquier otro valor. El puntero devuelto se puede invalidar si se pasa una referencia no const a la cadena a una función de biblioteca estándar. También se puede invalidar mediante una llamada a una función miembro no const. Las llamadas a miembros `at`, `back`, `begin`, `end`, `front`, `rbegin`, `rend`y `operator[]` no invalidan el puntero. 

Antes de C++ 11, `data` no garantizaba que la cadena devuelta finalizaba en NULL. Dado que C++ 11, `data` y `c_str` devuelven una cadena terminada en NULL y, de hecho, son iguales.

La sobrecarga no const es nueva en C++ 17. Para usarlo, especifique la opción del compilador **/STD: c++ 17** o **/STD: c + + latest** .

### <a name="example"></a>Ejemplo

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="difference_type"></a>  basic_string::difference_type

Tipo que proporciona la diferencia entre dos iteradores que hacen referencia a elementos de la misma cadena.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Notas

El tipo de entero con signo describe un objeto que puede representar la diferencia entre las direcciones de dos elementos cualesquiera de la secuencia controlada.

Para el tipo `string`, es equivalente a `ptrdiff_t`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="empty"></a>  basic_string::empty

Comprueba si la cadena contiene caracteres o no.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto de cadena no contiene caracteres; **False** si tiene al menos un carácter.

### <a name="remarks"></a>Notas

La función miembro es equivalente a [size](#size) == 0.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="end"></a>  basic_string::end

Devuelve un iterador que dirige a la ubicación siguiente al último elemento de una cadena.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de acceso aleatorio que dirige a la ubicación que sigue al último elemento de una cadena.

### <a name="remarks"></a>Notas

`end` se usa a menudo para comprobar si un iterador ha llegado al final de su cadena. No se debe desreferenciar el valor devuelto por `end`.

Si el valor devuelto de `end` se asigna a `const_iterator`, el objeto de cadena no se puede modificar. Si el valor devuelto de `end` se asigna a un `iterator`, el objeto de cadena se puede modificar.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="erase"></a>  basic_string::erase

Quita un elemento o un intervalo de elementos de una cadena de una posición especificada.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>Parameters

*primer*\
Iterador que dirige a la posición del primer elemento del intervalo que se va a borrar.

*última*\
Iterador que dirige a la posición situada una posición después del último elemento del intervalo que se va a borrar.

\ *ITER*
Iterador que dirige a la posición del elemento de la cadena que se va a borrar.

\ de *desplazamiento*
Índice del primer carácter de la cadena que se va a quitar.

*recuento*\
El número de elementos que se quitarán si hay tantos en el intervalo de la cadena que comienza con *offset*.

### <a name="return-value"></a>Valor devuelto

En el caso de las dos primeras funciones miembro, iterador que dirige al primer carácter situado después del último carácter quitado por la función miembro. En el caso de la tercera función miembro, referencia al objeto de cadena desde el que se han borrado los elementos.

### <a name="remarks"></a>Notas

La tercera función miembro devuelve **\*this**.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="find"></a>  basic_string::find

Busca hacia delante en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde se va a iniciar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'perfect' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="find_first_not_of"></a>  basic_string::find_first_not_of

Busca en una cadena el primer carácter que no es un elemento de una cadena especificada.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde se va a iniciar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="find_first_of"></a>  basic_string::find_first_of

Busca en una cadena el primer carácter que coincide con algún elemento de una cadena especificada.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde se va a iniciar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="find_last_not_of"></a>  basic_string::find_last_not_of

Busca en una cadena el último carácter que no es ningún elemento de una cadena especificada.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde va a terminar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="find_last_of"></a>  basic_string::find_last_of

Busca en una cadena el último carácter que coincide con algún elemento de una cadena especificada.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde va a terminar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="front"></a>  basic_string::front

Devuelve una referencia al primer elemento de una cadena.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>Valor devuelto

Referencia al primer elemento de la cadena, que no debe estar vacío.

### <a name="remarks"></a>Notas

## <a name="get_allocator"></a>  basic_string::get_allocator

Devuelve una copia del objeto de asignador usado para construir la cadena.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Valor devuelto

Asignador usado por la cadena.

### <a name="remarks"></a>Notas

La función miembro devuelve el objeto de asignador almacenado.

Los asignadores de la clase string especifican cómo administra el almacenamiento la clase. Los asignadores predeterminados proporcionados con las clases de contenedor son suficientes para la mayoría de las necesidades de programación. La escritura y el uso de sus propias clases de asignador son temas avanzados de C++.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="insert"></a>  basic_string::insert

Inserta un elemento, varios elementos o un intervalo de elementos en la cadena en una posición especificada.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameters

*posición*\
Índice de la posición detrás del punto de inserción de los nuevos caracteres.

\ *ptr*
Cadena de C que se va a insertar total o parcialmente en la cadena.

*recuento*\
Número de caracteres que se van a insertar.

\ *Str*
Cadena que se va a insertar total o parcialmente en la cadena de destino.

\ de *desplazamiento*
Índice de la parte de la cadena de origen que proporciona los caracteres que se va a anexar.

*char_value*\
Valor de carácter de los elementos que se van a insertar.

\ *ITER*
Iterador que direcciona la posición detrás de la cual se va a insertar un carácter.

*primer*\
Iterador de entrada, const_pointer o const_iterator, que dirige el primer elemento del intervalo de origen que se va a insertar.

*última*\
Iterador de entrada, const_pointer o const_iterator, que dirige la posición que está más allá del último elemento del intervalo de origen que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena al que la función de miembro está asignando nuevos caracteres o, en el caso de inserciones de caracteres individuales, iterador que direcciona la posición del carácter insertado, o ninguno, dependiendo de la función miembro concreta.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="iterator"></a>  basic_string::iterator

Tipo que proporciona un iterador de acceso aleatorio que puede acceder a un elemento **const** de la cadena y leerlo.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Notas

Un tipo `iterator` se puede usar para modificar el valor de un carácter y se usa para recorrer en iteración una cadena en una dirección hacia delante.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [begin](#begin) para obtener un ejemplo de cómo declarar y usar `iterator`.

## <a name="length"></a>  basic_string::length

Devuelve el número actual de elementos de una cadena.

```cpp
size_type length() const;
```

### <a name="remarks"></a>Notas

La función miembro es igual que [size](#size).

### <a name="example"></a>Ejemplo

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="max_size"></a>  basic_string::max_size

Devuelve el número máximo de caracteres que puede contener una cadena.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Valor devuelto

Número máximo de caracteres que puede contener una cadena.

### <a name="remarks"></a>Notas

Una excepción de tipo [length_error (Clase)](../standard-library/length-error-class.md) se inicia cuando una operación genera una cadena con una longitud mayor que el tamaño máximo.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="npos"></a>  basic_string::npos

Un valor entero sin signo inicializado en-1 que indica "no se encontró" o "todos los caracteres restantes" cuando se produce un error en una función de búsqueda.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>Notas

Cuando se va a comprobar el valor devuelto para el valor `npos`, es posible que no funcione a menos que el valor devuelto sea de tipo [size_type](#size_type) y no sea **int** o **sin signo**.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [find](#find) para obtener un ejemplo de cómo declarar y usar `npos`.

## <a name="op_add_eq"></a>  basic_string::operator+=

Anexa caracteres a una cadena.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameters

*char_value*\
Carácter que se va a anexar.

\ *ptr*
Caracteres de la cadena de C que se van a anexar.

\ *derecha*
Caracteres de la cadena que se van a anexar.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena que se está anexando con los caracteres pasados por la función miembro.

### <a name="remarks"></a>Notas

Se pueden anexar caracteres a una cadena mediante `operator+=` o las funciones miembro [append](#append) o [push_back](#push_back). `operator+=` anexa valores de un solo argumento, mientras que la función miembro de varios argumentos append permite especificar una parte concreta de una cadena para agregar.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="op_eq"></a>  basic_string::operator=

Asigna nuevos valores de caracteres al contenido de una cadena.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que se va a asignar.

\ *ptr*
Puntero a los caracteres de la cadena de C que se va a asignar a la cadena de destino.

\ *derecha*
Cadena de origen cuyos caracteres se van a asignar a la cadena de destino.

### <a name="return-value"></a>Valor devuelto

Referencia al objeto de cadena al que la función miembro está asignando nuevos caracteres.

### <a name="remarks"></a>Notas

Es posible asignar nuevos valores de caracteres a las cadenas. El nuevo valor puede ser una cadena y una cadena de C o un solo carácter. Se puede usar `operator=` si el nuevo valor puede ser descrito mediante un solo parámetro; en caso contrario, se puede usar la función miembro [assign](#assign), que tiene varios parámetros, para especificar qué parte de la cadena se va a asignar a una cadena de destino.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="op_at"></a>  basic_string::operator[]

Proporciona una referencia al carácter de una cadena que tiene el índice especificado.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>Parameters

\ de *desplazamiento*
Índice de la posición del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Referencia al carácter de la cadena en la posición especificada por el índice de parámetro.

### <a name="remarks"></a>Notas

El primer elemento de la cadena tiene un índice de cero y los enteros positivos indizan de forma consecutiva los siguientes elementos para que una cadena de longitud *n* tenga un elemento *enésimo* indizado por el número *n* - 1.

`operator[]` es más rápido que la función miembro [at](#at) a la hora de proporcionar acceso de lectura y escritura a los elementos de una cadena.

`operator[]` no comprueba si el índice pasado como parámetro es válido, pero la función miembro `at` realiza y, por lo tanto, se debe usar en la validez no es cierto. Un índice no válido (un índice menor que cero o mayor o igual que el tamaño de la cadena) que se pasa a la función miembro `at` produce una excepción de [clase out_of_range](../standard-library/out-of-range-class.md) . Un índice no válido pasado a `operator[]` tiene como resultado un comportamiento indefinido, pero el índice igual a la longitud de la cadena es un índice válido para cadenas const y el operador devuelve el carácter nulo cuando se ha pasado este índice.

La referencia devuelta puede ser anulada por las reasignaciones de cadena o las modificaciones de las cadenas no **const**.

Al compilar con [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento fuera de los límites de la cadena. Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="pointer"></a>  basic_string::pointer

Tipo que proporciona un puntero a un elemento de carácter de una cadena o una matriz de caracteres.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Notas

El tipo es un sinónimo de `allocator_type::pointer`.

Para el tipo `string`, es equivalente a **char** <strong>\*</strong>.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="pop_back"></a>  basic_string::pop_back

Borra el último elemento de la cadena.

```cpp
void pop_back();
```

### <a name="remarks"></a>Notas

Esta función miembro llama eficazmente a `erase(size() - 1)` para borrar el último elemento de la secuencia, que no debe estar vacío.

## <a name="push_back"></a>  basic_string::push_back

Agrega un elemento al final de la cadena.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>Parameters

*char_value*\
Carácter que se va a agregar al final de la cadena.

### <a name="remarks"></a>Notas

La función miembro llama eficazmente a [Insert](#insert)( [End](#end), *char_value* ).

### <a name="example"></a>Ejemplo

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="rbegin"></a>  basic_string::rbegin

Devuelve un iterador al primer elemento de una cadena invertida.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de acceso aleatorio al primer elemento de una cadena invertida que se dirige a lo que sería el último elemento de la cadena no invertida correspondiente.

### <a name="remarks"></a>Notas

`rbegin` se usa con una cadena invertida igual que [begin](#begin) se usa con una cadena.

Si el valor devuelto de `rbegin` se asigna a `const_reverse_iterator`, el objeto de cadena no se puede modificar. Si el valor devuelto de `rbegin` se asigna a `reverse_iterator`, el objeto de cadena se puede modificar.

`rbegin` puede usarse para inicializar una iteración a través de una cadena hacia atrás.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="reference"></a>  basic_string::reference

Tipo que proporciona una referencia a un elemento almacenado en una cadena.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>Notas

Se puede utilizar un tipo `reference` para modificar el valor de un elemento.

El tipo es un sinónimo de `allocator_type::reference`.

Para el tipo `string`, es equivalente a `chr&`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [at](#at) para obtener un ejemplo de cómo declarar y usar `reference`.

## <a name="rend"></a>  basic_string::rend

Devuelve un iterador que dirige a la ubicación que sigue al último elemento de una cadena invertida.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio que dirige a la ubicación que sigue al último elemento de una cadena invertida.

### <a name="remarks"></a>Notas

`rend` se usa con una cadena invertida igual que [end](#end) se usa con una cadena.

Si el valor devuelto de `rend` se asigna a `const_reverse_iterator`, el objeto de cadena no se puede modificar. Si el valor devuelto de `rend` se asigna a `reverse_iterator`, el objeto de cadena se puede modificar.

Se puede usar `rend` para comprobar si un iterador inverso ha llegado al final de su cadena.

No se debe desreferenciar el valor devuelto por `rend`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
*str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="replace"></a>  basic_string::replace

Reemplaza los elementos de una cadena situados en la posición especificada por los caracteres especificados o los caracteres copiados de otros intervalos, cadenas o cadenas de C.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Parameters

\ *Str*
Cadena que va a ser un origen de caracteres para la cadena de operando.

*position_1*\
Índice de la cadena de operando en la que comienza la sustitución.

*number_1*\
Número máximo de caracteres de la cadena de operando que se van a sustituir.

*position_2*\
Índice de la cadena de parámetro en la que comienza la copia.

*number_2*\
Número máximo de caracteres de la cadena de C de parámetro que se van a usar.

\ *ptr*
Cadena de C que va a ser un origen de caracteres para la cadena de operando.

*char_value*\
Carácter que se va a copiar en la cadena de operando.

\ *first0*
Iterador que dirige al primer carácter de la cadena de operando que se va a quitar.

\ *last0*
Iterador que dirige al último carácter de la cadena de operando que se va a quitar.

*primer*\
Iterador, const_pointer o const_iterator que dirige al primer carácter de la cadena de parámetro que se va a copiar.

*última*\
Iterador, const_pointer o const_iterator que dirige al último carácter de la cadena de parámetro que se va a copiar.

*recuento*\
El número de veces que *char_value* se copia en la cadena de operando.

### <a name="return-value"></a>Valor devuelto

Cadena de operando con la sustitución realizada.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="reserve"></a>  basic_string::reserve

Configura la capacidad de la cadena con un número que es, al menos, tan alto como un número especificado.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>Parameters

*recuento*\
Número de caracteres para los que se va a reservar memoria.

### <a name="remarks"></a>Notas

Es importante tener suficiente capacidad porque las reasignaciones son procesos lentos que anulan todas las referencias, los punteros y los iteradores que hacen referencia a caracteres de una cadena.

El concepto de capacidad para los objetos de cadenas de tipo es igual que para los objetos de vector de tipo. A diferencia de Vector, se puede llamar a la función miembro `reserve` para reducir la capacidad de un objeto. La solicitud no es vinculante y puede producirse o no. Dado que el valor predeterminado del parámetro es cero, una llamada a `reserve` es una solicitud que no es de enlace para reducir la capacidad de la cadena para ajustarse al número de caracteres que hay actualmente en la cadena. La capacidad nunca se reduce por debajo del número actual de caracteres.

Una llamada a `reserve` es la única forma posible de reducir la capacidad de una cadena. Pero como se ha indicado arriba, esta solicitud no es vinculante y podría no producirse.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="resize"></a>  basic_string::resize

Especifica un nuevo tamaño para una cadena y anexa o borra elementos según sea necesario.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>Parameters

*recuento*\
El nuevo tamaño de la cadena.

*char_value*\
Valor con el que se inicializan los caracteres anexados si se necesitan elementos adicionales.

### <a name="remarks"></a>Notas

Si el tamaño resultante supera el número máximo de caracteres, la fórmula inicia `length_error`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="reverse_iterator"></a>  basic_string::reverse_iterator

Tipo que proporciona una referencia a un elemento almacenado en una cadena.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Notas

Un tipo `reverse_iterator` se puede usar para modificar el valor de un carácter. Se usa para iterar una cadena en orden inverso.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [rbegin](#rbegin) para obtener un ejemplo de cómo declarar y usar `reverse_iterator`.

## <a name="rfind"></a>  basic_string::rfind

Busca hacia atrás en una cadena la primera aparición de una subcadena que coincide con una secuencia especificada de caracteres.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Parameters

*char_value*\
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice de la posición donde se va a iniciar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
Cadena que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice de la última aparición al buscar hacia atrás del primer carácter de la subcadena cuando la operación se realiza correctamente; de lo contrario, `npos`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="shrink_to_fit"></a>  basic_string::shrink_to_fit

Descarta el exceso de capacidad de la cadena.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Notas

Esta función miembro elimina cualquier almacenamiento innecesario en el contenedor.

## <a name="size"></a>  basic_string::size

Devuelve el número actual de elementos de una cadena.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="size_type"></a>  basic_string::size_type

Tipo entero sin signo que puede representar el número de elementos e índices de una cadena.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>Notas

es equivalente a `allocator_type::size_type`.

Para el tipo `string`, es equivalente a `size_t`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="substr"></a>  basic_string::substr

Copia una subcadena de, como máximo, un número de caracteres de una cadena, empezando desde la posición especificada.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>Parameters

\ de *desplazamiento*
Índice que localiza el elemento en la posición a partir de la que se realiza la copia de la cadena, con un valor predeterminado de 0.

*recuento*\
Número de caracteres que se van a copiar si están presentes.

### <a name="return-value"></a>Valor devuelto

Objeto de subcadena que es una copia de elementos del operando de cadena a partir de la posición especificada por el primer argumento.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="swap"></a>  basic_string::swap

Intercambie el contenido de dos cadenas.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Parameters

\ *Str*
Cadena de origen cuyos elementos se van a intercambiar con los de la cadena de destino.

### <a name="remarks"></a>Notas

Si las cadenas que se van a intercambiar tienen el mismo objeto de asignador, la función miembro `swap`:

- Se ejecuta en tiempo constante.

- No inicia excepciones.

- No anula ninguna referencia, puntero ni iterador que designe elementos de las dos cadenas.

De lo contrario, realiza varias asignaciones de elementos y llamadas de constructor proporcionales al número de elementos de ambas secuencias controladas.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="traits_type"></a>  basic_string::traits_type

Tipo de los rasgos de carácter de los elementos almacenados en una cadena.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Notas

El tipo es un sinónimo del segundo parámetro de plantilla `Traits`.

Para el tipo `string`, es equivalente a **char_traits\<char >** .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [copy](../standard-library/char-traits-struct.md#copy) para obtener un ejemplo de cómo declarar y usar `traits_type`.

## <a name="value_type"></a>  basic_string::value_type

Tipo que representa el tipo de caracteres que se almacenan en una cadena.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>Notas

Es equivalente a `traits_type::char_type` y es equivalente a **Char** para los objetos de tipo `string`.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>Vea también

[\<string>](../standard-library/string.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
