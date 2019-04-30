---
title: Clase basic_string_view
ms.date: 04/20/2019
f1_keywords:
- xstring/std::basic_string_view
- xstring/std::basic_string_view::allocator_type
- xstring/std::basic_string_view::const_iterator
- xstring/std::basic_string_view::const_pointer
- xstring/std::basic_string_view::const_reference
- xstring/std::basic_string_view::const_reverse_iterator
- xstring/std::basic_string_view::difference_type
- xstring/std::basic_string_view::iterator
- xstring/std::basic_string_view::npos
- xstring/std::basic_string_view::pointer
- xstring/std::basic_string_view::reference
- xstring/std::basic_string_view::reverse_iterator
- xstring/std::basic_string_view::size_type
- xstring/std::basic_string_view::traits_type
- xstring/std::basic_string_view::value_type
- xstring/std::basic_string_view::append
- xstring/std::basic_string_view::assign
- xstring/std::basic_string_view::at
- xstring/std::basic_string_view::back
- xstring/std::basic_string_view::begin
- xstring/std::basic_string_view::c_str
- xstring/std::basic_string_view::capacity
- xstring/std::basic_string_view::cbegin
- xstring/std::basic_string_view::cend
- xstring/std::basic_string_view::clear
- xstring/std::basic_string_view::compare
- xstring/std::basic_string_view::copy
- xstring/std::basic_string_view::_Copy_s
- xstring/std::basic_string_view::crbegin
- xstring/std::basic_string_view::crend
- xstring/std::basic_string_view::data
- xstring/std::basic_string_view::empty
- xstring/std::basic_string_view::end
- xstring/std::basic_string_view::erase
- xstring/std::basic_string_view::find
- xstring/std::basic_string_view::find_first_not_of
- xstring/std::basic_string_view::find_first_of
- xstring/std::basic_string_view::find_last_not_of
- xstring/std::basic_string_view::find_last_of
- xstring/std::basic_string_view::front
- xstring/std::basic_string_view::get_allocator
- xstring/std::basic_string_view::insert
- xstring/std::basic_string_view::length
- xstring/std::basic_string_view::max_size
- xstring/std::basic_string_view::pop_back
- xstring/std::basic_string_view::push_back
- xstring/std::basic_string_view::rbegin
- xstring/std::basic_string_view::rend
- xstring/std::basic_string_view::remove_prefix
- xstring/std::basic_string_view::remove_suffix
- xstring/std::basic_string_view::replace
- xstring/std::basic_string_view::reserve
- xstring/std::basic_string_view::resize
- xstring/std::basic_string_view::rfind
- xstring/std::basic_string_view::shrink_to_fit
- xstring/std::basic_string_view::size
- xstring/std::basic_string_view::substr
- xstring/std::basic_string_view::swap
helpviewer_keywords:
- std::basic_string_view
- std::basic_string_view, allocator_type
- std::basic_string_view, const_iterator
- std::basic_string_view, const_pointer
- std::basic_string_view, const_reference
- std::basic_string_view, const_reverse_iterator
- std::basic_string_view, difference_type
- std::basic_string_view, iterator
- std::basic_string_view, npos
- std::basic_string_view, pointer
- std::basic_string_view, reference
- std::basic_string_view, reverse_iterator
- std::basic_string_view, size_type
- std::basic_string_view, traits_type
- std::basic_string_view, value_type
- std::basic_string_view, append
- std::basic_string_view, assign
- std::basic_string_view, at
- std::basic_string_view, back
- std::basic_string_view, begin
- std::basic_string_view, c_str
- std::basic_string_view, capacity
- std::basic_string_view, cbegin
- std::basic_string_view, cend
- std::basic_string_view, clear
- std::basic_string_view, compare
- std::basic_string_view, copy
- std::basic_string_view, crbegin
- std::basic_string_view, crend
- std::basic_string_view, data
- std::basic_string_view, empty
- std::basic_string_view, end
- std::basic_string_view, erase
- std::basic_string_view, find
- std::basic_string_view, find_first_not_of
- std::basic_string_view, find_first_of
- std::basic_string_view, find_last_not_of
- std::basic_string_view, find_last_of
- std::basic_string_view, front
- std::basic_string_view, get_allocator
- std::basic_string_view, insert
- std::basic_string_view, length
- std::basic_string_view, max_size
- std::basic_string_view, pop_back
- std::basic_string_view, push_back
- std::basic_string_view, rbegin
- std::basic_string_view, rend
- std::basic_string_view, remove_prefix
- std::basic_string_view, remove_suffix
- std::basic_string_view, replace
- std::basic_string_view, reserve
- std::basic_string_view, resize
- std::basic_string_view, rfind
- std::basic_string_view, shrink_to_fit
- std::basic_string_view, size
- std::basic_string_view, substr
- std::basic_string_view, swap
ms.assetid: a9c3e0a2-39bf-4c8a-b093-9abe30839591
ms.openlocfilehash: 0ac5e3d528881f7b1caa0a1dcdae0161a6777e57
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346943"
---
# <a name="basicstringview-class"></a>Clase basic_string_view

La plantilla de clase `basic_string_view<charT>` se agregó en C ++ 17 que sirva como una forma eficaz y segura para una función que acepte varios no relacionados con los tipos de cadena sin la necesidad de ser de plantilla en esos tipos de función. La clase contiene un puntero que no es propietario a una secuencia contigua de datos de caracteres y una longitud que especifica el número de caracteres en la secuencia. No se realiza ninguna suposición con respecto a si la secuencia está terminada en null.

La biblioteca estándar define varias especializaciones según el tipo de los elementos:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

En este documento, el término "string_view" hace referencia generalmente a cualquiera de estas definiciones de tipos.

Un string_view describe la interfaz común mínima necesaria leer datos de cadena. Proporciona acceso constante a los datos subyacentes; no realiza ninguna copia (excepto para el `copy` función). Los datos pueden o no pueden contener valores null ('\0') en cualquier posición. Un string_view ejerce ningún control sobre la duración del objeto. Es responsabilidad del llamador asegurarse de que los datos subyacentes de la cadena están válidos.

Una función que acepta un parámetro de tipo string_view puede realizarse para que funcione con cualquier tipo de cadena, sin necesidad de realizar la función en una plantilla o restringir la función a un determinado subconjunto de tipos de cadena. El único requisito es que existe una conversión implícita desde el tipo de cadena para string_view. Todos los tipos de cadena estándar son implícitamente convertibles a un string_view que contiene el mismo tipo de elemento. En otras palabras, un `std::string` puede convertirse en un `string_view` pero no a un `wstring_view`.

El ejemplo siguiente muestra una función que no son de plantilla `f` que toma un parámetro de tipo `wstring_view`. Se puede llamar con argumentos de tipo `std::wstring`, `wchar_t*`, y `winrt::hstring`.

```cpp
// compile with: /std:c++17
// string_view that uses elements of wchar_t
void f(wstring_view);

// pass a std::wstring:
const std::wstring& s { L"Hello" };
f(s);

// pass a C-style null-terminated string (string_view is not null-terminated):
const wchar_t* ns = L"Hello";
f(ns);

// pass a C-style character array of len characters (excluding null terminator):
const wchar_t* cs { L"Hello" };
size_t len { 5 };
f({cs,len});

// pass a WinRT string
winrt::hstring hs { L"Hello" };
f(hs);
```

## <a name="syntax"></a>Sintaxis

```cpp
template <class CharType, class Traits = char_traits<CharType>>
class basic_string_view;
```

### <a name="parameters"></a>Parámetros

*CharType*<br/>
El tipo de los caracteres que se almacenan en el string_view. El C++ biblioteca estándar proporciona los siguientes TypeDef para especializaciones de esta plantilla.
- [string_view](../standard-library/string-view-typedefs.md#string_view) elementos del tipo **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), para **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) para **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) para **char32_t**.

*Rasgos*<br/>
El valor predeterminado es [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_string_view](#basic_string_view)|Construye un string_view que está vacía, o bien apunta a todos o parte de datos de algún otro objeto de cadena, o a una matriz de caracteres de estilo C.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|**const_iterator**|Iterador de acceso aleatorio que puede leer **const** elementos.|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**iterator**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**pointer**|`using pointer = value_type*;`|
|**reference**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operadores de miembro

|Operador|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna un objeto de cadena string_view o convertible a otro string_view.|
|[operator\[\]](#op_at)|Devuelve el elemento que se encuentra en el índice especificado.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[at](#at)|Devuelve un const_reference al elemento en una ubicación especificada.|
|[back](#back)|Devuelve un const_reference al último elemento.|
|[begin](#begin)|Devuelve un iterador const que direcciona el primer elemento. (string_views son inmutables).|
|[cbegin](#cbegin)|Igual que [comenzar](#begin).|
|[cend](#cend)|Devuelve un iterador constante que apunta a uno más allá del último elemento.|
|[copy](#copy)|Copia a lo sumo un número especificado de caracteres de una posición indexada en un origen de string_view en una matriz de caracteres de destino. (No recomendado. Use _Copy_s en su lugar.)|
|[_Copy_s](#_copy_s)|Función de copia de CRT segura.|
|[compare](#compare)|Compara un string_view con un string_view especificado para determinar si son iguales o si una es lexicográficamente menor que el otro.|
|[crbegin](#crbegin)|Igual que [rbegin](#rbegin).|
|[crend](#crend)|Igual que [rend](#rend).|
|[data](#data)|Devuelve un puntero sin formato que no es propietario a la secuencia de caracteres.|
|[empty](#empty)|Comprueba si el string_view contiene caracteres.|
|[end](#end)|Igual que [cend](#cend).|
|[find](#find)|Busca hacia delante de la primera aparición de una subcadena que coincide con una secuencia de caracteres especificada.|
|[find_first_not_of](#find_first_not_of)|Busca el primer carácter que no es ningún elemento de un objeto de cadenas que puedan convertirse o string_view especificado.|
|[find_first_of](#find_first_of)|Busca el primer carácter que coincide con cualquier elemento de un objeto de cadenas que puedan convertirse o string_view especificado.|
|[find_last_not_of](#find_last_not_of)|Busca el último carácter que no es ningún elemento de un objeto de cadenas que puedan convertirse o string_view especificado.|
|[find_last_of](#find_last_of)|Busca el último carácter que es un elemento de un objeto de cadenas que puedan convertirse o string_view especificado.|
|[front](#front)|Devuelve un const_reference al primer elemento.|
|[length](#length)|Devuelve el número actual de elementos.|
|[max_size](#max_size)|Devuelve el número máximo de caracteres que puede contener un string_view.|
|[rbegin](#rbegin)|Devuelve un iterador const que direcciona el primer elemento en un string_view invertido.|
|[remove_prefix](#remove_prefix)|Mueve el puntero hacia delante el número especificado de elementos.|
|[remove_suffix](#remove_suffix)|Reduce el tamaño de la vista por el número especificado de elementos a partir de la parte posterior.|
|[rend](#rend)|Devuelve un iterador constante que apunta a uno más allá del último elemento de un string_view invertido.|
|[rfind](#rfind)|Busca un string_view en orden inverso para la primera aparición de una subcadena que coincide con una secuencia de caracteres especificada.|
|[size](#size)|Devuelve el número actual de elementos.|
|[substr](#substr)|Devuelve una subcadena de una longitud especificada, empezando por un índice especificado.|
|[swap](#swap)|Intercambia el contenido de dos string_views.|

## <a name="remarks"></a>Comentarios

Si se pide a una función que genere una secuencia de más de [max_size](#max_size) elementos, la función notifica un error de longitud al iniciar un objeto de tipo [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Requisitos

[std: c ++ 17](../build/reference/std-specify-language-standard-version.md) o posterior

**Encabezado:** \<string_view >

**Espacio de nombres:** std

## <a name="at"></a>  basic_string_view::at

Devuelve un const_reference al carácter en el índice especificado basado en 0.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El índice del elemento que se hace referencia.

### <a name="return-value"></a>Valor devuelto

Un const_reference para el carácter que ocupa la posición especificada por el índice del parámetro.

### <a name="remarks"></a>Comentarios

El primer elemento tiene un índice de cero y los siguientes elementos se indizan de forma consecutiva enteros positivos, por lo que un string_view de longitud *n* tiene un *n*elemento indizado por el número *n -* 1. **en** produce una excepción para los índices no válidos, a diferencia de [operador\[\]](#op_at). 

En general, recomendamos que **en** para las secuencias como `std::vector` y string_view nunca debe utilizarse. Un índice no válido pasado a una secuencia es un error de lógica que se debe detectar y fija durante el desarrollo. Si un programa no está completamente seguro de que sus índices son válidos, debe probarlos, no llame a at() y dependen de excepciones para defenderse contra descuidada programación.

Consulte [basic_string_view::operator\[ \] ](#op_at) para obtener más información.

### <a name="example"></a>Ejemplo

```cpp
// basic_string_view_at.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>

int main()
{
    using namespace std;

    const string_view  str1("Hello world");
    string_view::const_reference refStr2 = str1.at(8); // 'r'
}
```

## <a name="back"></a>  basic_string_view::back

Devuelve un const_reference al último elemento.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

Un const_reference hasta el último elemento en el string_view.

### <a name="remarks"></a>Comentarios

Produce una excepción si el string_view está vacía.

Tenga en cuenta que después de modificar un string_view, por ejemplo mediante una llamada a `remove_suffix`, a continuación, el elemento devuelto por esta función ya no es el último elemento en los datos subyacentes.

### <a name="example"></a>Ejemplo

Un string_view construido con un literal de cadena de C no incluye el carácter nulo final y, por tanto, en el ejemplo siguiente `back` devuelve "p" y no '\0'.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p 
```

Los valores null incrustados se tratan como cualquier otro carácter:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_view"></a>  basic_string_view::basic_string_view

Construye un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Puntero a los valores de caracteres.

*len*<br/>
El número de caracteres que se va a incluir en la vista.

## <a name="remarks"></a>Comentarios

Los constructores con un parámetro de gráfico * se suponen que la entrada está terminada en null, pero no se incluye el carácter nulo en el string_view.

También se puede construir un string_view con un literal. Consulte [operador "" sv](string-view-operators.md#op_sv).

## <a name="begin"></a>  basic_string_view::begin

Igual que [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto
Devuelve un const_iterator que dirige al primer elemento.

## <a name="cbegin"></a>  basic_string_view::cbegin

Devuelve un const_iterator que dirige al primer elemento del intervalo.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

## <a name="cend"></a>  basic_string_view::cend

Devuelve un const_iterator que dirige a la ubicación situada más allá del último elemento de un intervalo.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un **const** iterador de acceso aleatorio que apunta justo después del final del intervalo.

### <a name="remarks"></a>Comentarios

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="compare"></a> basic_string_view::compare

Realiza una comparación distingue mayúsculas de minúsculas, con un string_view especificado (o un tipo de cadenas que puedan convertirse) para determinar si los dos objetos son iguales o si una es lexicográficamente menor que el otro. El [ \<string_view > operadores](string-view-operators.md) utilizar esta función miembro para realizar comparaciones.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parámetros

*strv*<br/>
String_view en el que se va a compararse con este string_view.

*pos*<br/>
El índice de este string_view en el que comienza la comparación.

*num*<br/>
El número máximo de caracteres de este string_view va a comparar.

*num2*<br/>
El número máximo de caracteres de *strv* va a comparar.

*offset*<br/>
El índice de *strv* en el que comienza la comparación.

*ptr*<br/>
La cadena de C que va a compararse con este string_view.

### <a name="return-value"></a>Valor devuelto

Un valor negativo si esta string_view es menor que *strv* o *ptr*; es cero si las secuencias de caracteres de dos son iguales; o un valor positivo si es mayor que este string_view *strv*o *ptr*.

### <a name="remarks"></a>Comentarios

El `compare` funciones miembro realizan una comparación entre mayúsculas y minúsculas de la totalidad o parte de cada secuencia de caracteres. 

### <a name="example"></a>Ejemplo

```cpp
// basic_string_view_compare.cpp
// compile with: /EHsc
#include <string_view>
#include <iostream>
#include <string>

using namespace std;

string to_alpha(int result)
{
   if (result < 0) return " less than ";
   else if (result == 0) return " equal to ";
   else return " greater than ";
}

int main()
{
   // The first member function compares
   // two string_views
   string_view sv_A("CAB");
   string_view sv_B("CAB");
   cout << "sv_A is " << sv_A << endl;
   cout << "sv_B is " << sv_B << endl;
   int comp1 = sv_A.compare(sv_B);
   cout << "sv_A is" << to_alpha(comp1) << "sv_B.\n";

   // The second member function compares part of
   // an operand string_view to another string_view
   string_view sv_C("AACAB");
   string_view sv_D("CAB");
   cout << "sv_C is: " << sv_C << endl;
   cout << "sv_D is: " << sv_D << endl;
   int comp2a = sv_C.compare(2, 3, sv_D);
   cout << "The last three characters of sv_C are" 
       << to_alpha(comp2a) << "sv_D.\n";

   int comp2b = sv_C.compare(0, 3, sv_D);
   cout << "The first three characters of sv_C are" 
       << to_alpha(comp2b) << "sv_D.\n";

   // The third member function compares part of
   // an operand string_view to part of another string_view
   string_view sv_E("AACAB");
   string_view sv_F("DCABD");
   cout << "sv_E: " << sv_E << endl;
   cout << "sv_F is: " << sv_F << endl;
   int comp3a = sv_E.compare(2, 3, sv_F, 1, 3);
   cout << "The three characters from position 2 of sv_E are"
       << to_alpha(comp3a) 
       << "the 3 characters of sv_F from position 1.\n";

   // The fourth member function compares
   // an operand string_view to a C string
   string_view sv_G("ABC");
   const char* cs_A = "DEF";
   cout << "sv_G is: " << sv_G << endl;
   cout << "cs_A is: " << cs_A << endl;
   int comp4a = sv_G.compare(cs_A);
   cout << "sv_G is" << to_alpha(comp4a) << "cs_A.\n";

   // The fifth member function compares part of
   // an operand string_view to a C string
   string_view sv_H("AACAB");
   const char* cs_B = "CAB";
   cout << "sv_H is: " << sv_H << endl;
   cout << "cs_B is: " << cs_B << endl;
   int comp5a = sv_H.compare(2, 3, cs_B);
   cout << "The last three characters of sv_H are"
      << to_alpha(comp5a) << "cs_B.\n";

   // The sixth member function compares part of
   // an operand string_view to part of an equal length of
   // a C string
   string_view sv_I("AACAB");
   const char* cs_C = "ACAB";
   cout << "sv_I is: " << sv_I << endl;
   cout << "cs_C: " << cs_C << endl;
   int comp6a = sv_I.compare(1, 3, cs_C, 3);
   cout << "The 3 characters from position 1 of sv_I are"
      << to_alpha(comp6a) << "the first 3 characters of cs_C.\n";
}
```

```Output
sv_A is CAB
sv_B is CAB
sv_A is equal to sv_B.
sv_C is: AACAB
sv_D is: CAB
The last three characters of sv_C are equal to sv_D.
The first three characters of sv_C are less than sv_D.
sv_E: AACAB
sv_F is: DCABD
The three characters from position 2 of sv_E are equal to the 3 characters of sv_F from position 1.
sv_G is: ABC
cs_A is: DEF
sv_G is less than cs_A.
sv_H is: AACAB
cs_B is: CAB
The last three characters of sv_H are equal to cs_B.
sv_I is: AACAB
cs_C: ACAB
The 3 characters from position 1 of sv_I are equal to the first 3 characters of cs_C.
```

## <a name="copy"></a>  basic_string_view::copy

Copia a lo sumo un número especificado de caracteres de una posición indexada en un origen de string_view en una matriz de caracteres de destino. Le recomendamos que use la función segura [basic_string_view::_Copy_s](#_copy_s) en su lugar.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*ptr*<br/>
Matriz de caracteres de destino en la que van a copiarse los elementos.

*count*<br/>
El número de caracteres que se copian, a lo sumo, desde el origen string_view.

*offset*<br/>
Posición inicial en el string_view de origen desde el que copias se van a estar.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Comentarios

Un carácter nulo no se anexa al final de la copia.

## <a name="_copy_s"></a>  basic_string_view::_Copy_s

Proteger la función de copia de CRT que se utilizará en lugar de [copia](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parámetros

*dest*<br/>
Matriz de caracteres de destino en la que van a copiarse los elementos.

*dest_size*<br/>
El tamaño de *dest*.

_ *Recuento* el número de caracteres que se copian, como máximo, de la cadena de origen.

*_Off*<br/>
Posición inicial de la cadena de origen a partir de la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Comentarios

Un carácter nulo no se anexa al final de la copia.

 Para obtener más información, consulte [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="crbegin"></a>  basic_string_view::crbegin

Devuelve un const_reverse_iterator que direcciona el primer elemento en un string_view invertido.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un const_reverse_iterator que direcciona el primer elemento en un string_view invertido. 

## <a name="crend"></a>  basic_string_view::crend

Igual que [rend](#rend). 

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_reverse_iterator que soluciona una más allá del final de un string_view invertido.

## <a name="data"></a>  basic_string_view::data

Devuelve un puntero sin formato que no es propietario a la secuencia de caracteres const del objeto que fue utilizado para construir el string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a-const al primer elemento de la secuencia de caracteres.

### <a name="remarks"></a>Comentarios

El puntero no puede modificar los caracteres.

Una secuencia de caracteres de string_view no es necesariamente terminada en null. El tipo de valor devuelto para `data` no es una cadena de C válida, porque no se anexa ningún carácter nulo. El carácter nulo '\0' no tiene ningún significado especial en un objeto de tipo string_view y puede ser una parte del objeto string_view igual que cualquier otro carácter.

## <a name="empty"></a>  basic_string_view::empty

Comprueba si el string_view contiene caracteres o no.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**True** si el objeto string_view no contiene ningún carácter; **false** si tiene al menos un carácter.

### <a name="remarks"></a>Comentarios

La función miembro es equivalente a [tamaño](#size)() == 0.

## <a name="end"></a>  basic_string_view::end

Devuelve un const_iterator acceso aleatorio que apunta a uno más allá del último elemento.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_iterator acceso aleatorio que apunta a uno más allá del último elemento.

### <a name="remarks"></a>Comentarios

`end` se usa para comprobar si un const_iterator ha llegado al final de su string_view. El valor devuelto por `end` no se debe desreferenciar.

## <a name="find"></a>  basic_string_view::find

Busca un string_view hacia delante de la primera aparición de un carácter o subcadena que coincide con una secuencia de caracteres especificada.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que es comenzar la búsqueda.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres en *ptr*, contando hacia delante desde el primer carácter.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="find_first_not_of"></a>  basic_string_view::find_first_not_of

Busca el primer carácter que no es un elemento de un objeto de cadenas que puedan convertirse o string_view especificado.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que es comenzar la búsqueda.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres, contando hacia delante desde el primer carácter en la cadena de C para el que la función miembro consiste en Buscar.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="find_first_of"></a>  basic_string_view::find_first_of

Busca el primer carácter que coincide con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que es comenzar la búsqueda.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres, contando hacia delante desde el primer carácter en la cadena de C para el que la función miembro consiste en Buscar.

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="find_last_not_of"></a>  basic_string_view::find_last_not_of

Busca el último carácter que no es ningún elemento de un string_view especificado.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que la búsqueda va a finalizar.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres, contando hacia delante desde el primer carácter, en *ptr*.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `string_view::npos`.

## <a name="find_last_of"></a>  basic_string_view::find_last_of

Busca el último carácter que coincide con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que la búsqueda va a finalizar.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres, contando hacia delante desde el primer carácter en la cadena de C para el que la función miembro consiste en Buscar.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="front"></a>  basic_string_view::front

Devuelve un const_reference al primer elemento.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Un const_reference al primer elemento.

### <a name="remarks"></a>Comentarios

Produce una excepción si el string_view está vacía.

## <a name="length"></a> basic_string_view::length

Devuelve el número actual de elementos.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Comentarios

La función miembro es igual que [size](#size).

## <a name="max_size"></a>  basic_string_view::max_size

Devuelve el número máximo de caracteres que puede contener un string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de caracteres que puede contener un string_view.

### <a name="remarks"></a>Comentarios

Una excepción de tipo [length_error](../standard-library/length-error-class.md) se produce cuando una operación genera un string_view con una longitud mayor que `max_size()`.

## <a name="op_eq"></a>  basic_string_view::operator=

Asigna un objeto de cadena string_view o convertible a otro string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```
### <a name="example"></a>Ejemplo

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```
## <a name="op_at"></a>  basic_string_view::operator[]

Proporciona un const_reference al carácter con un índice especificado.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
El índice del elemento que se hace referencia.

### <a name="return-value"></a>Valor devuelto

Un const_reference para el carácter que ocupa la posición especificada por el índice del parámetro.

### <a name="remarks"></a>Comentarios

El primer elemento tiene un índice de cero y los siguientes elementos se indizan de forma consecutiva enteros positivos, por lo que un string_view de longitud *n* tiene un *n*elemento indizado por el número *n* - 1.

`operator[]` es más rápido que la función miembro [en](#at) para proporcionar acceso de lectura a los elementos de un string_view.

`operator[]` no comprueba si el índice pasado como un argumento es válido. Un índice no válido pasado a `operator[]` da como resultado un comportamiento indefinido.

La referencia devuelta se puede invalidar si los datos de cadena subyacente se modifica o elimina el objeto propietario.

Cuando se compila con [ \_ITERADOR\_depurar\_nivel](../standard-library/iterator-debug-level.md) establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta acceder a un elemento fuera de los límites de la string_view. Para obtener más información, consulta [Checked Iterators](../standard-library/checked-iterators.md).

## <a name="rbegin"></a>  basic_string_view::rbegin

Devuelve un iterador constante al primer elemento en un string_view invertido.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de acceso aleatorio al primer elemento en un string_view invertido, dirige a lo que sería el último elemento en el correspondiente string_view sin invertir.

### <a name="remarks"></a>Comentarios

`rbegin` se usa con un string_view invertido igual que [comenzar](#begin) se usa con un string_view. `rbegin` puede usarse para inicializar una iteración con versiones anteriores.

## <a name="remove_prefix"></a> basic_string_view::remove_prefix

Mueve el puntero hacia delante el número especificado de elementos.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Comentarios

Deja los datos subyacentes sin cambios. Mueve el puntero de string_view hacia delante por n elementos y establece la privada `size` n - tamaño del miembro de datos.

## <a name="remove_suffix"></a> basic_string_view::remove_suffix

Reduce el tamaño de la vista por el número especificado de elementos a partir de la parte posterior.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Comentarios

Deja los datos subyacentes y el puntero a sin cambios. Establece la privada `size` n - tamaño del miembro de datos.

## <a name="rend"></a>  basic_string_view::rend

Devuelve un iterador constante que apunta a uno más allá del último elemento de un string_view invertido.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Una constante inverso iterador de acceso aleatorio que apunta a uno más allá del último elemento de un string_view invertido.

### <a name="remarks"></a>Comentarios

`rend` se usa con un string_view invertido igual que [final](#end) se usa con un string_view. `rend` puede usarse para comprobar si un iterador inverso ha llegado al final de su string_view. El valor devuelto por `rend` no se debe desreferenciar.

## <a name="rfind"></a>  basic_string_view::rfind

Busca un string_view en orden inverso una subcadena que coincide con una secuencia de caracteres especificada.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*chVal*<br/>
Valor de carácter que va a buscar la función miembro.

*offset*<br/>
Índice en el que es comenzar la búsqueda.

*ptr*<br/>
La cadena de C para el que la función miembro consiste en Buscar.

*count*<br/>
El número de caracteres, contando hacia delante desde el primer carácter en la cadena de C para el que la función miembro consiste en Buscar.

*str*<br/>
El string_view para que la función miembro consiste en Buscar.

### <a name="return-value"></a>Valor devuelto

El índice del primer carácter de la subcadena cuando se realiza correctamente; en caso contrario `npos`.

## <a name="size"></a>  basic_string_view::size

Devuelve el número de elementos en el string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

La longitud de la string_view.

### <a name="remarks"></a>Comentarios

Un string_view puede modificar su longitud, por ejemplo si `remove_prefix` y `remove_suffix`. Dado que esto no modifica los datos de cadena subyacente, el tamaño de un string_view no es necesariamente el tamaño de los datos subyacentes.

## <a name="substr"></a>  basic_string_view::substr

Devuelve un string_view que representa el número especificado de caracteres (como máximo) de una posición especificada.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parámetros

*offset*<br/>
Índice que localiza el elemento en la posición desde la que se realiza la copia, con un valor predeterminado de 0.

*count*<br/>
El número de caracteres que se va a incluir en la subcadena, si están presentes.

### <a name="return-value"></a>Valor devuelto

Un objeto string_view que representa la secuencia de elementos secundarios especificada.

## <a name="swap"></a>  basic_string_view::swap

Intercambia dos string_views, en otras palabras, los punteros a los datos de cadena subyacente y los valores de tamaño.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parámetros

*sv*<br/>
El origen string_view cuyos valores de puntero y el tamaño son van a intercambiar con el de la string_view de destino.

## <a name="see-also"></a>Vea también

[\<string_view>](../standard-library/string-view.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
