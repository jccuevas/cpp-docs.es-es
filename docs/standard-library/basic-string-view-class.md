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
ms.openlocfilehash: ac65dca931f821c717e9c081c8d3479fd0b3bb0e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364890"
---
# <a name="basic_string_view-class"></a>Clase basic_string_view

La plantilla `basic_string_view<charT>` de clase se agregó en C++17 para servir como una manera segura y eficiente para que una función acepte varios tipos de cadena no relacionados sin que la función tenga que ser plantillas en esos tipos. La clase contiene un puntero no propietario a una secuencia contigua de datos de caracteres y una longitud que especifica el número de caracteres de la secuencia. No se asume con respecto a si la secuencia está terminada en null.

La biblioteca estándar define varias especializaciones en función del tipo de elementos:

- `string_view`
- `wstring_view`
- `u16string_view`
- `u32string_view`

En este documento, el término "string_view" se refiere generalmente a cualquiera de estas typedefs.

Un string_view describe la interfaz común mínima necesaria para leer datos de cadena. Proporciona acceso const a los datos subyacentes; no hace copias (excepto `copy` para la función). Los datos pueden o no contener valores nulos ('-0') en cualquier posición. Un string_view no tiene control sobre la duración del objeto. Es responsabilidad del autor de la llamada asegurarse de que los datos de cadena subyacentes son válidos.

Una función que acepta un parámetro de tipo string_view se puede hacer para trabajar con cualquier tipo de cadena, sin convertir la función en una plantilla, o restringir la función a un subconjunto determinado de tipos de cadena. El único requisito es que existe una conversión implícita del tipo de cadena a string_view. Todos los tipos de cadena estándar son implícitamente convertibles a un string_view que contiene el mismo tipo de elemento. En otras palabras, `std::string` a `string_view` es convertible `wstring_view`a un pero no a un archivo .

En el ejemplo siguiente se `f` muestra una función que no es de plantilla que toma un parámetro de tipo `wstring_view`. Se puede llamar con argumentos `wchar_t*`de `winrt::hstring`tipo `std::wstring`, , y .

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

*CharType*\
El tipo de los caracteres que se almacenan en el string_view. La biblioteca estándar C++ proporciona las siguientes desflas de tipo para las especializaciones de esta plantilla.

- [string_view](../standard-library/string-view-typedefs.md#string_view) para elementos de tipo **char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), por **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) para **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) para **char32_t**.

*Rasgos*\
El valor predeterminado [es char_traits](char-traits-struct.md)<>*CharType.*

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_string_view](#basic_string_view)|Construye un string_view que está vacío o que apunta a todos o parte de los datos de algún otro objeto de cadena, o a una matriz de caracteres de estilo C.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|**const_iterator**|Iterador de acceso aleatorio que puede leer **elementos const.**|
|**const_pointer**|`using const_pointer = const value_type*;`|
|**const_reference**|`using const_reference = const value_type&;`|
|**const_reverse_iterator**|`using const_reverse_iterator = std::reverse_iterator<const_iterator>;`|
|**difference_type**|`using difference_type = ptrdiff_t;`|
|**Iterador**|`using iterator = const_iterator;`|
|**npos**|`static constexpr size_type npos = size_type(-1);`|
|**puntero**|`using pointer = value_type*;`|
|**Referencia**|`using reference = value_type&;`|
|**reverse_iterator**|`using reverse_iterator = const_reverse_iterator;`|
|**size_type**|`using size_type = size_t;`|
|**traits_type**|`using traits_type = Traits;`|
|**value_type**|`using value_type = CharType;`|

### <a name="member-operators"></a>Operadores miembros

|Operator|Descripción|
|-|-|
|[operador](#op_eq)|Asigna un objeto de cadena string_view o convertible a otro string_view.|
|[Operador\[\]](#op_at)|Devuelve el elemento que se encuentra en el índice especificado.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[En](#at)|Devuelve un const_reference al elemento en una ubicación especificada.|
|[Atrás](#back)|Devuelve un const_reference al último elemento.|
|[Comenzar](#begin)|Devuelve un iterador const que direcciona el primer elemento. (string_views son inmutables.)|
|[cbegin](#cbegin)|Igual [que empezar](#begin).|
|[cend](#cend)|Devuelve un iterador const que apunta a uno más allá del último elemento.|
|[copy](#copy)|Copia como máximo un número especificado de caracteres desde una posición indizada en un origen string_view a una matriz de caracteres de destino. (No recomendado. Utilice _Copy_s en su lugar.)|
|[_Copy_s](#_copy_s)|Función de copia CRT segura.|
|[Comparar](#compare)|Compara un string_view con un string_view especificado para determinar si son iguales o si uno es lexicográficamente menor que el otro.|
|[crbegin](#crbegin)|Igual que [rbegin](#rbegin).|
|[crend](#crend)|Igual que [rend](#rend).|
|[datos](#data)|Devuelve un puntero sin propietario a la secuencia de caracteres.|
|[Vacío](#empty)|Comprueba si el string_view contiene caracteres.|
|[Final](#end)|Igual que [cend](#cend).|
|[find](#find)|Busca en una dirección hacia delante la primera aparición de una subcadena que coincida con una secuencia especificada de caracteres.|
|[find_first_not_of](#find_first_not_of)|Busca el primer carácter que no es ningún elemento de un objeto de cadena string_view o convertible especificado.|
|[find_first_of](#find_first_of)|Busca el primer carácter que coincide con cualquier elemento de un objeto de cadena string_view o convertible especificado.|
|[find_last_not_of](#find_last_not_of)|Busca el último carácter que no es ningún elemento de un objeto de cadena string_view o convertible especificado.|
|[find_last_of](#find_last_of)|Busca el último carácter que es un elemento de un objeto de cadena string_view o convertible especificado.|
|[Frente](#front)|Devuelve un const_reference al primer elemento.|
|[length](#length)|Devuelve el número actual de elementos.|
|[max_size](#max_size)|Devuelve el número máximo de caracteres que podría contener un string_view.|
|[rbegin](#rbegin)|Devuelve un iterador const que direcciona el primer elemento de un string_view invertido.|
|[remove_prefix](#remove_prefix)|Mueve el puntero hacia delante por el número especificado de elementos.|
|[remove_suffix](#remove_suffix)|Reduce el tamaño de la vista por el número especificado de elementos a partir de la parte posterior.|
|[rend](#rend)|Devuelve un iterador const que apunta a uno más allá del último elemento de un string_view invertido.|
|[rfind](#rfind)|Busca en un string_view inverso la primera aparición de una subcadena que coincida con una secuencia especificada de caracteres.|
|[Tamaño](#size)|Devuelve el número actual de elementos.|
|[substr](#substr)|Devuelve una subcadena de una longitud especificada que comienza en un índice especificado.|
|[swap](#swap)|Intercambie el contenido de dos string_views.|

## <a name="remarks"></a>Observaciones

Si se pide a una función que genere una secuencia de más de [max_size](#max_size) elementos, la función notifica un error de longitud al iniciar un objeto de tipo [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Requisitos

[std:c++17](../build/reference/std-specify-language-standard-version.md) o posterior

**Encabezado:** \<> string_view

**Espacio de nombres:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view::at

Devuelve un const_reference al carácter en el índice basado en 0 especificado.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parámetros

*Compensar*\
El índice del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Un const_reference al carácter en la posición especificada por el índice de parámetros.

### <a name="remarks"></a>Observaciones

El primer elemento tiene un índice de cero y los siguientes elementos se indizan consecutivamente por los enteros positivos, de modo que un string_view de longitud *n* tiene un *n*ésimo elemento indexado por el número *n -* 1. **en** produce una excepción para los índices no válidos, a diferencia de [operator\[](#op_at).

En general, se **at** recomienda que en `std::vector` para secuencias como y string_view nunca se debe utilizar. Un índice no válido pasado a una secuencia es un error lógico que se debe detectar y corregir durante el desarrollo. Si un programa no está absolutamente seguro de que sus índices son válidos, debe probarlos, no llamar a() y confiar en excepciones para defenderse de la programación descuidada.

Consulte [basic_string_view::operador\[ ](#op_at) para obtener más información.

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view::back

Devuelve un const_reference al último elemento.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

Un const_reference al último elemento de la string_view.

### <a name="remarks"></a>Observaciones

Produce una excepción si el string_view está vacío.

Tenga en cuenta que después de modificar `remove_suffix`un string_view, por ejemplo, llamando a , el elemento devuelto por esta función ya no es el último elemento de los datos subyacentes.

### <a name="example"></a>Ejemplo

Un string_view que se construye con un literal de cadena de C `back` no incluye el null de terminación y, por lo tanto, en el ejemplo siguiente devuelve 'p' y no '-0'.

```cpp
char c[] = "Help"; // char[5]
string_view sv{ c };
cout << sv.size(); // size() == 4
cout << sv.back() << endl; // p
```

Los valores NULL incrustados se tratan como cualquier otro carácter:

```cpp
string_view e = "embedded\0nulls"sv;
cout << boolalpha << (e.back() == 's'); // true
```

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view::basic_string_view

Construye un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parámetros

*Str*\
El puntero a los valores de carácter.

*Len*\
El número de caracteres que se incluirán en la vista.

## <a name="remarks"></a>Observaciones

Los constructores con un parámetro charT* suponen que la entrada está terminada en null, pero el null de terminación no se incluye en el string_view.

También puede construir un string_view con un literal. Ver [operador"""sv](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view::comenzar

Igual que [cbegin](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_iterator que direcciona el primer elemento.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view::cbegin

Devuelve un const_iterator que direcciona el primer elemento del intervalo.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio **const** que apunta al primer elemento del intervalo o a la ubicación `cbegin() == cend()`justo más allá del final de un intervalo vacío (para un intervalo vacío, ).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view::cend

Devuelve un const_iterator que direcciona la ubicación justo más allá del último elemento de un intervalo.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio **const** que apunta justo más allá del final del intervalo.

### <a name="remarks"></a>Observaciones

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view::comparar

Realiza una comparación con distinción entre mayúsculas y minúsculas con un string_view especificado (o un tipo de cadena convertible) para determinar si los dos objetos son iguales o si uno es lexicográficamente menor que el otro. El [ \<string_view> operadores](string-view-operators.md) utilizan esta función miembro para realizar comparaciones.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parámetros

*strv*\
El string_view que se va a comparar con este string_view.

*Pos*\
El índice de este string_view en el que comienza la comparación.

*Num*\
El número máximo de caracteres de este string_view a comparar.

*num2*\
El número máximo de caracteres de *strv* que se va a comparar.

*Compensar*\
El índice de *strv* en el que comienza la comparación.

*Ptr*\
La cadena C que se comparará con este string_view.

### <a name="return-value"></a>Valor devuelto

Un valor negativo si este string_view es menor que *strv* o *ptr*; cero si las dos secuencias de caracteres son iguales; o un valor positivo si este string_view es mayor que *strv* o *ptr*.

### <a name="remarks"></a>Observaciones

Las `compare` funciones miembro realizan una comparación que distingue mayúsculas de minúsculas de todas o parte de cada secuencia de caracteres.

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view::copia

Copia como máximo un número especificado de caracteres desde una posición indizada en un origen string_view a una matriz de caracteres de destino. Le recomendamos que utilice la función secure [basic_string_view::_Copy_s](#_copy_s) en su lugar.

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*Ptr*\
Matriz de caracteres de destino en la que van a copiarse los elementos.

*Contar*\
El número de caracteres que se van a copiar, como máximo, del origen string_view.

*Compensar*\
La posición inicial en la fuente string_view desde la que se deben realizar copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Observaciones

Un carácter nulo no se anexa al final de la copia.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view::_Copy_s

Función de copia CRT segura que se utilizará en lugar de [copiar](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parámetros

*Dest*\
Matriz de caracteres de destino en la que van a copiarse los elementos.

*dest_size*\
El tamaño de *dest*.

_ *Recuento* El número de caracteres que se van a copiar, como máximo, de la cadena de origen.

*_Off*\
Posición inicial de la cadena de origen a partir de la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Observaciones

Un carácter nulo no se anexa al final de la copia.

Para obtener más información, consulte [c-runtime-library/security-features-in-the-crt](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view::crbegin

Devuelve un const_reverse_iterator que direcciona el primer elemento de un string_view invertido.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un const_reverse_iterator que aborda el primer elemento de un string_view invertido.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view::crend

Igual que [rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_reverse_iterator que direcciona uno más allá del final de un string_view invertido.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::data

Devuelve un puntero sin propietario a la secuencia de caracteres const del objeto que se usó para construir el string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a-const al primer elemento de la secuencia de caracteres.

### <a name="remarks"></a>Observaciones

El puntero no puede modificar los caracteres.

Una secuencia de caracteres string_view no está necesariamente terminada en null. El tipo `data` de valor devuelto para no es una cadena C válida, porque no se anexa ningún carácter nulo. El carácter nulo '-0' no tiene ningún significado especial en un objeto de tipo string_view y puede ser una parte del objeto string_view al igual que cualquier otro carácter.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view::vacío

Comprueba si el string_view contiene caracteres o no.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto string_view no contiene caracteres; **falso** si tiene al menos un carácter.

### <a name="remarks"></a>Observaciones

La función miembro es equivalente a [tamaño](#size)() .

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view::fin

Devuelve un const_iterator de acceso aleatorio que apunta a uno más allá del último elemento.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_iterator de acceso aleatorio que apunta a uno más allá del último elemento.

### <a name="remarks"></a>Observaciones

`end`se utiliza para probar si un const_iterator ha llegado al final de su string_view. El valor devuelto por `end` no se debe desreferenciar.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view::encontrar

Busca en un string_view en una dirección hacia delante la primera aparición de un carácter o subcadena que coincida con una secuencia especificada de caracteres.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*Str*\
El string_view para el que se va a buscar la función miembro.

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que se va a iniciar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres en *ptr*, contando hacia delante desde el primer carácter.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view::find_first_not_of

Busca el primer carácter que no es un elemento de un objeto de cadena string_view o convertible especificado.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*Str*\
El string_view para el que se va a buscar la función miembro.

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que se va a iniciar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres, contando hacia delante desde el primer carácter, en la cadena C para la que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view::find_first_of

Busca el primer carácter que coincida con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que se va a iniciar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres, contando hacia delante desde el primer carácter, en la cadena C para la que se va a buscar la función miembro.

*Str*\
El string_view para el que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view::find_last_not_of

Busca el último carácter que no es ningún elemento de un string_view especificado.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*Str*\
El string_view para el que se va a buscar la función miembro.

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que debe finalizar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres, contando hacia delante desde el primer carácter, en *ptr*.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view::find_last_of

Busca el último carácter que coincida con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*Str*\
El string_view para el que se va a buscar la función miembro.

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que debe finalizar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres, contando hacia delante desde el primer carácter, en la cadena C para la que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view::front

Devuelve un const_reference al primer elemento.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Un const_reference al primer elemento.

### <a name="remarks"></a>Observaciones

Produce una excepción si el string_view está vacío.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view::longitud

Devuelve el número actual de elementos.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Observaciones

La función miembro es igual que [size](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view::max_size

Devuelve el número máximo de caracteres que puede contener un string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

El número máximo de caracteres que puede contener un string_view.

### <a name="remarks"></a>Observaciones

Se produce una excepción de tipo [length_error](../standard-library/length-error-class.md) cuando una operación produce un string_view con una longitud mayor que `max_size()`.

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view::operador

Asigna un objeto de cadena string_view o convertible a otro string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Ejemplo

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view::operador[]

Proporciona un const_reference al carácter con un índice especificado.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parámetros

*Compensar*\
El índice del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Un const_reference al carácter en la posición especificada por el índice de parámetros.

### <a name="remarks"></a>Observaciones

El primer elemento tiene un índice de cero, y los siguientes elementos se indizan consecutivamente por los enteros positivos, de modo que un string_view de longitud *n* tiene un *n*ésimo elemento indizado por el número *n* - 1.

`operator[]`es más rápido que la función miembro [para](#at) proporcionar acceso de lectura a los elementos de un string_view.

`operator[]`no comprueba si el índice pasado como argumento es válido. Un índice no `operator[]` válido pasado a da como resultado un comportamiento indefinido.

La referencia devuelta puede invalidarse si el objeto propietario modifica o elimina los datos de cadena subyacentes.

Al compilar [ \_con\_\_ITERATOR DEBUG LEVEL](../standard-library/iterator-debug-level.md) establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites del string_view. Para obtener más información, vea [Iteradores comprobados](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view::rbegin

Devuelve un iterador const al primer elemento de un string_view invertido.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de acceso aleatorio al primer elemento de un string_view invertido, direccionando cuál sería el último elemento de la string_view no revertida correspondiente.

### <a name="remarks"></a>Observaciones

`rbegin`se utiliza con una string_view invertida al igual que [el comienzo](#begin) se utiliza con una string_view. `rbegin`se puede utilizar para inicializar una iteración hacia atrás.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view::remove_prefix

Mueve el puntero hacia delante por el número especificado de elementos.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Observaciones

Deja los datos subyacentes sin cambios. Mueve el puntero string_view hacia delante `size` por n elementos y establece el miembro de datos privados en size - n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view::remove_suffix

Reduce el tamaño de la vista por el número especificado de elementos a partir de la parte posterior.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Observaciones

Deja los datos subyacentes y el puntero a ellos sin cambios. Establece el `size` miembro de datos privados en size - n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view::rend

Devuelve un iterador const que apunta a uno más allá del último elemento de un string_view invertido.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio inverso const que apunta a uno más allá del último elemento de una string_view invertida.

### <a name="remarks"></a>Observaciones

`rend`se utiliza con una string_view invertida al igual que el [extremo](#end) se utiliza con un string_view. `rend`se puede utilizar para probar si un iterador inverso ha llegado al final de su string_view. El valor devuelto por `rend` no se debe desreferenciar.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view::rfind

Busca en un string_view inverso una subcadena que coincida con una secuencia especificada de caracteres.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

*chVal*\
Valor de carácter que va a buscar la función miembro.

*Compensar*\
Indice en el que se va a iniciar la búsqueda.

*Ptr*\
Cadena C para la que se va a buscar la función miembro.

*Contar*\
El número de caracteres, contando hacia delante desde el primer carácter, en la cadena C para la que se va a buscar la función miembro.

*Str*\
El string_view para el que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

El índice del primer carácter de la subcadena cuando se realiza correctamente; de `npos`lo contrario .

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view::tamaño

Devuelve el número de elementos de la string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

La longitud del string_view.

### <a name="remarks"></a>Observaciones

Un string_view puede modificar su `remove_prefix` longitud, por ejemplo, por y `remove_suffix`. Dado que esto no modifica los datos de cadena subyacentes, el tamaño de un string_view no es necesariamente el tamaño de los datos subyacentes.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view::substr

Devuelve un string_view que representa (como máximo) el número especificado de caracteres desde una posición especificada.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parámetros

*Compensar*\
Un índice que ubica el elemento en la posición desde la que se realiza la copia, con un valor predeterminado de 0.

*Contar*\
El número de caracteres que se incluirán en la subcadena, si están presentes.

### <a name="return-value"></a>Valor devuelto

Un objeto string_view que representa la subsecuencia especificada de elementos.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view::swap

Intercambia dos string_views, en otras palabras, los punteros a los datos de cadena subyacentes y los valores de tamaño.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parámetros

*Sv*\
El origen string_view cuyos valores de puntero y tamaño se van a intercambiar con los del destino string_view.

## <a name="see-also"></a>Consulte también

[\<string_view>](../standard-library/string-view.md)\
[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
