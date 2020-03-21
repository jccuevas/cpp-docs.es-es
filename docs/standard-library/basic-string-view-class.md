---
title: basic_string_view (clase)
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
ms.openlocfilehash: 8f6b1bdf5648298221a8b41de31ec49ae0c47513
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076710"
---
# <a name="basic_string_view-class"></a>basic_string_view (clase)

La plantilla de clase `basic_string_view<charT>` se agregó en C++ 17 para servir como una manera segura y eficaz de que una función acepte varios tipos de cadena no relacionados sin que la función tenga que ser hace plantilla en esos tipos. La clase contiene un puntero que no es propietario a una secuencia contigua de datos de caracteres y una longitud que especifica el número de caracteres de la secuencia. No se realiza ninguna suposición con respecto a si la secuencia está terminada en NULL.

La biblioteca estándar define varias especializaciones basadas en el tipo de los elementos:

-  `string_view`
-  `wstring_view`
-  `u16string_view`
-  `u32string_view`

En este documento, el término "string_view" se refiere generalmente a cualquiera de estas definiciones de de.

Un string_view describe la interfaz común mínima necesaria para leer los datos de cadena. Proporciona acceso const a los datos subyacentes. no realiza ninguna copia (excepto la función `copy`). Los datos pueden contener o no valores NULL (' \ 0 ') en cualquier posición. Un string_view no tiene ningún control sobre la duración del objeto. Es responsabilidad del autor de la llamada asegurarse de que los datos de cadena subyacentes son válidos.

Una función que acepta un parámetro de tipo string_view puede realizarse para trabajar con cualquier tipo de cadena, sin realizar la función en una plantilla o restringir la función a un subconjunto determinado de tipos de cadena. El único requisito es que exista una conversión implícita del tipo de cadena que se va a string_view. Todos los tipos de cadena estándar se pueden convertir implícitamente en una string_view que contiene el mismo tipo de elemento. En otras palabras, un `std::string` se pueden convertir en un `string_view` pero no en un `wstring_view`.

En el ejemplo siguiente se muestra una función que no es de plantilla `f` que toma un parámetro de tipo `wstring_view`. Se puede llamar con argumentos de tipo `std::wstring`, `wchar_t*`y `winrt::hstring`.

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

\ *CharType*
Tipo de los caracteres que se almacenan en el string_view. La C++ biblioteca estándar proporciona las siguientes definiciones de tipo para las especializaciones de esta plantilla.
- [string_view](../standard-library/string-view-typedefs.md#string_view) para elementos de tipo **Char**
- [wstring_view](../standard-library/string-view-typedefs.md#wstring_view), para **wchar_t**
- [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) para **char16_t**
- [u32string_view](../standard-library/string-view-typedefs.md#u32string_view) para **char32_t**.

*Rasgos*\
Tiene como valor predeterminado [char_traits](char-traits-struct.md)<*CharType*>.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[basic_string_view](#basic_string_view)|Construye una string_view que está vacía, o bien apunta a todos los datos de un objeto de cadena o a parte de ellos, o a una matriz de caracteres de estilo C.|

### <a name="typedefs"></a>Typedefs

|Nombre del tipo|Descripción|
|-|-|
|**const_iterator**|Iterador de acceso aleatorio que puede leer elementos **const** .|
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

|Operator|Descripción|
|-|-|
|[operator=](#op_eq)|Asigna un string_view o un objeto de cadena convertible a otro string_view.|
|[operator\[\]](#op_at)|Devuelve el elemento que se encuentra en el índice especificado.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[at](#at)|Devuelve un const_reference al elemento en una ubicación especificada.|
|[back](#back)|Devuelve un const_reference al último elemento.|
|[begin](#begin)|Devuelve un iterador const que direcciona el primer elemento. (string_views son inmutables).|
|[cbegin](#cbegin)|Igual que [Begin](#begin).|
|[cend](#cend)|Devuelve un iterador constante que apunta a uno más allá del último elemento.|
|[copy](#copy)|Copia como máximo un número especificado de caracteres de una posición indizada en un string_view de origen a una matriz de caracteres de destino. (No se recomienda. En su lugar, use _Copy_s).|
|[_Copy_s](#_copy_s)|Función de copia de CRT segura.|
|[compare](#compare)|Compara una string_view con una string_view especificada para determinar si son iguales o si una es lexicográficamente menor que la otra.|
|[crbegin](#crbegin)|Igual que [rbegin](#rbegin).|
|[crend](#crend)|Igual que [Rend](#rend).|
|[data](#data)|Devuelve un puntero no poseente no poseedor a la secuencia de caracteres.|
|[empty](#empty)|Comprueba si el string_view contiene caracteres.|
|[end](#end)|Igual que [cend](#cend).|
|[find](#find)|Busca en una dirección hacia delante la primera aparición de una subcadena que coincida con una secuencia especificada de caracteres.|
|[find_first_not_of](#find_first_not_of)|Busca el primer carácter que no es ningún elemento de un string_view especificado o un objeto de cadena convertible.|
|[find_first_of](#find_first_of)|Busca el primer carácter que coincide con cualquier elemento de un string_view especificado o un objeto de cadena convertible.|
|[find_last_not_of](#find_last_not_of)|Busca el último carácter que no es ningún elemento de un string_view especificado o un objeto de cadena convertible.|
|[find_last_of](#find_last_of)|Busca el último carácter que es un elemento de un string_view especificado o un objeto de cadena convertible.|
|[front](#front)|Devuelve un const_reference al primer elemento.|
|[length](#length)|Devuelve el número actual de elementos.|
|[max_size](#max_size)|Devuelve el número máximo de caracteres que puede contener un string_view.|
|[rbegin](#rbegin)|Devuelve un iterador const que direcciona el primer elemento de un string_view invertido.|
|[remove_prefix](#remove_prefix)|Mueve el puntero hacia delante el número de elementos especificado.|
|[remove_suffix](#remove_suffix)|Reduce el tamaño de la vista en el número especificado de elementos a partir de la parte posterior.|
|[rend](#rend)|Devuelve un iterador constante que apunta a uno más allá del último elemento de un string_view invertido.|
|[rfind](#rfind)|Busca una string_view en orden inverso para la primera aparición de una subcadena que coincida con una secuencia especificada de caracteres.|
|[size](#size)|Devuelve el número actual de elementos.|
|[substr](#substr)|Devuelve una subcadena de una longitud especificada a partir de un índice especificado.|
|[swap](#swap)|Intercambie el contenido de dos string_views.|

## <a name="remarks"></a>Observaciones

Si se pide a una función que genere una secuencia de más de [max_size](#max_size) elementos, la función notifica un error de longitud al iniciar un objeto de tipo [length_error](../standard-library/length-error-class.md).

## <a name="requirements"></a>Requisitos

[STD: c++ 17](../build/reference/std-specify-language-standard-version.md) o posterior

**Encabezado:** \<string_view >

**Espacio de nombres:** std

## <a name="basic_string_viewat"></a><a name="at"></a>basic_string_view:: at

Devuelve un const_reference al carácter que se encuentra en el índice de base 0 especificado.

```cpp
constexpr const_reference at(size_type offset) const;
```

### <a name="parameters"></a>Parámetros

\ de *desplazamiento*
Índice del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Const_reference al carácter situado en la posición especificada por el índice del parámetro.

### <a name="remarks"></a>Observaciones

El primer elemento tiene un índice de cero y los enteros positivos indizan de forma consecutiva los siguientes elementos, de modo que un string_view de longitud *n* tenga un elemento *n*-ésimo indizado por el número *n-* 1. **at** produce una excepción para los índices no válidos, a diferencia de los [\[de operador \]](#op_at).

En general, se recomienda que no se use **en** secuencias como `std::vector` y string_view. Un índice no válido que se pasa a una secuencia es un error lógico que debe detectarse y corregirse durante el desarrollo. Si un programa no está absolutamente seguro de que sus índices son válidos, debe probarlos, no llamar a () y basarse en las excepciones para defenderse de una programación descuidada.

Vea [basic_string_view:: operator\[\]](#op_at) para obtener más información.

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

## <a name="basic_string_viewback"></a><a name="back"></a>basic_string_view:: Back

Devuelve un const_reference al último elemento.

```cpp
constexpr const_reference back() const;
```

### <a name="return-value"></a>Valor devuelto

Const_reference al último elemento del string_view.

### <a name="remarks"></a>Observaciones

Produce una excepción si el string_view está vacío.

Tenga en cuenta que después de modificar un string_view, por ejemplo llamando a `remove_suffix`, el elemento devuelto por esta función ya no es el último elemento de los datos subyacentes.

### <a name="example"></a>Ejemplo

Un string_view que se construye con un literal de cadena de C no incluye el carácter null de terminación y, por lo tanto, en el ejemplo siguiente `back` devuelve ' p ' y no ' \ 0 '.

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

## <a name="basic_string_viewbasic_string_view"></a><a name="basic_string_view"></a>basic_string_view:: basic_string_view

Construye un string_view.

```cpp
constexpr basic_string_view() noexcept;
constexpr basic_string_view(const basic_string_view&) noexcept = default;
constexpr basic_string_view(const charT* str);
constexpr basic_string_view(const charT* str, size_type len);
```

### <a name="parameters"></a>Parámetros

\ *Str*
Puntero a los valores de carácter.

*len*\
Número de caracteres que se van a incluir en la vista.

## <a name="remarks"></a>Observaciones

Los constructores con un parámetro charT * suponen que la entrada termina en null, pero el valor null final no se incluye en el string_view.

También puede crear un string_view con un literal. Vea [operador "" VP](string-view-operators.md#op_sv).

## <a name="basic_string_viewbegin"></a><a name="begin"></a>basic_string_view:: Begin

Igual que [cbegin (](#cbegin).

```cpp
constexpr const_iterator begin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto
Devuelve un const_iterator que se dirige al primer elemento.

## <a name="basic_string_viewcbegin"></a><a name="cbegin"></a>basic_string_view:: cbegin (

Devuelve un const_iterator que se dirige al primer elemento del intervalo.

```cpp
constexpr const_iterator cbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un iterador **const** de acceso aleatorio que apunta al primer elemento del intervalo o la ubicación situada más allá del final de un intervalo vacío (para un intervalo vacío, `cbegin() == cend()`).

## <a name="basic_string_viewcend"></a><a name="cend"></a>basic_string_view:: cend

Devuelve un const_iterator que se dirige a la ubicación situada más allá del último elemento de un intervalo.

```cpp
constexpr const_iterator cend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un iterador **const** de acceso aleatorio que apunta justo después del final del intervalo.

### <a name="remarks"></a>Observaciones

El valor devuelto por `cend` no se debe desreferenciar.

## <a name="basic_string_viewcompare"></a><a name="compare"></a>basic_string_view:: Compare

Realiza una comparación con distinción entre mayúsculas y minúsculas con una string_view especificada (o un tipo de cadena convertible) para determinar si los dos objetos son iguales o si uno es lexicográficamente menor que el otro. Los [operadores\<string_view >](string-view-operators.md) utilizan esta función miembro para realizar comparaciones.

```cpp
constexpr int compare(basic_string_view strv) const noexcept;
constexpr int compare(size_type pos, size_type num, basic_string_view strv) const;
constexpr int compare(size_type pos, size_type num, basic_string_view strv, size_type offset, size_type num2) const;
constexpr int compare(const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr) const;
constexpr int compare(size_type pos, size_type num, const charT* ptr, size_type num2) const;
```

### <a name="parameters"></a>Parámetros

\ *strv*
String_view que se va a comparar con este string_view.

\ de *pos*
Índice de este string_view en el que comienza la comparación.

\ *NUM*
Número máximo de caracteres de este string_view que se van a comparar.

*num2*\
Número máximo de caracteres de *strv* que se van a comparar.

\ de *desplazamiento*
Índice de *strv* en el que comienza la comparación.

\ *ptr*
Cadena de C que se va a comparar con este string_view.

### <a name="return-value"></a>Valor devuelto

Un valor negativo si este string_view es menor que *strv* o *ptr*; cero si las dos secuencias de caracteres son iguales; o un valor positivo si este string_view es mayor que *strv* o *ptr*.

### <a name="remarks"></a>Observaciones

Las funciones miembro de `compare` realizan una comparación que distingue entre mayúsculas y minúsculas de toda o parte de cada secuencia de caracteres.

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

## <a name="basic_string_viewcopy"></a><a name="copy"></a>basic_string_view:: Copy

Copia como máximo un número especificado de caracteres de una posición indizada en un string_view de origen a una matriz de caracteres de destino. En su lugar, se recomienda usar la función Secure [basic_string_view:: _Copy_s](#_copy_s) .

```cpp
size_type copy(charT* ptr, size_type count, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

\ *ptr*
Matriz de caracteres de destino en la que van a copiarse los elementos.

*recuento*\
Número de caracteres que se van a copiar, como máximo, del string_view de origen.

\ de *desplazamiento*
Posición inicial de la string_view de origen desde la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Observaciones

Un carácter nulo no se anexa al final de la copia.

## <a name="basic_string_view_copy_s"></a><a name="_copy_s"></a>basic_string_view:: _Copy_s

Función de copia de CRT segura que se va a usar en lugar de [copiar](#copy).

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type _Off = 0) const;
```

### <a name="parameters"></a>Parámetros

\ de *destino*
Matriz de caracteres de destino en la que van a copiarse los elementos.

*dest_size*\
Tamaño del *destino*.

_ *Cuente* el número de caracteres que se copiarán, como máximo, de la cadena de origen.

*_Off*\
Posición inicial de la cadena de origen a partir de la que se van a realizar las copias.

### <a name="return-value"></a>Valor devuelto

Número de caracteres que realmente se va a copiar.

### <a name="remarks"></a>Observaciones

Un carácter nulo no se anexa al final de la copia.

Para obtener más información, vea [c-Runtime-Library/Security-Features-in-the-CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="basic_string_viewcrbegin"></a><a name="crbegin"></a>basic_string_view:: crbegin

Devuelve un const_reverse_iterator que se dirige al primer elemento de un string_view invertido.

```cpp
constexpr const_reverse_iterator crbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Const_reverse_iterator que se dirige al primer elemento de un string_view invertido.

## <a name="basic_string_viewcrend"></a><a name="crend"></a>basic_string_view:: crend

Igual que [Rend](#rend).

```cpp
constexpr const_reverse_iterator crend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_reverse_iterator que se dirige a una posición después del final de una string_view invertida.

## <a name="basic_string_viewdata"></a><a name="data"></a>basic_string_view::d ATA

Devuelve un puntero no poseente no poseedor a la secuencia de caracteres const del objeto que se usó para construir el string_view.

```cpp
constexpr value_type *data() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Puntero a const en el primer elemento de la secuencia de caracteres.

### <a name="remarks"></a>Observaciones

El puntero no puede modificar los caracteres.

Una secuencia de caracteres string_view no tiene necesariamente terminación nula. El tipo de valor devuelto para `data` no es una cadena de C válida, porque no se anexa ningún carácter nulo. El carácter nulo ' \ 0 ' no tiene ningún significado especial en un objeto de tipo string_view y puede ser una parte del objeto string_view como cualquier otro carácter.

## <a name="basic_string_viewempty"></a><a name="empty"></a>basic_string_view:: Empty

Comprueba si el string_view contiene caracteres o no.

```cpp
constexpr bool empty() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el objeto string_view no contiene ningún carácter; **false** si tiene al menos un carácter.

### <a name="remarks"></a>Observaciones

La función miembro es equivalente a [size](#size)() = = 0.

## <a name="basic_string_viewend"></a><a name="end"></a>basic_string_view:: end

Devuelve un const_iterator de acceso aleatorio que apunta a uno más allá del último elemento.

```cpp
constexpr const_iterator end() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un const_iterator de acceso aleatorio que apunta a uno más allá del último elemento.

### <a name="remarks"></a>Observaciones

`end` se usa para comprobar si un const_iterator ha alcanzado el final de su string_view. El valor devuelto por `end` no se debe desreferenciar.

## <a name="basic_string_viewfind"></a><a name="find"></a>basic_string_view:: Find

Busca una string_view en una dirección hacia delante para la primera aparición de un carácter o subcadena que coincida con una secuencia especificada de caracteres.

```cpp
constexpr size_type find(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

\ *Str*
String_view para el que se va a buscar la función miembro.

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que va a comenzar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres en *ptr*, contando hacia delante desde el primer carácter.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_first_not_of"></a><a name="find_first_not_of"></a>basic_string_view:: find_first_not_of

Busca el primer carácter que no es un elemento de un string_view especificado o un objeto de cadena convertible.

```cpp
constexpr size_type find_first_not_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_first_not_of(const charT* ptr, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

\ *Str*
String_view para el que se va a buscar la función miembro.

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que va a comenzar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_first_of"></a><a name="find_first_of"></a>basic_string_view:: find_first_of

Busca el primer carácter que coincide con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_first_of(basic_string_view str, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(charT chVal, size_type offset = 0) const noexcept;
constexpr size_type find_first_of(const charT* str, size_type offset, size_type count) const;
constexpr size_type find_first_of(const charT* str, size_type offset = 0) const;
```

### <a name="parameters"></a>Parámetros

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que va a comenzar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
String_view para el que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfind_last_not_of"></a><a name="find_last_not_of"></a>basic_string_view:: find_last_not_of

Busca el último carácter que no es ningún elemento de un string_view especificado.

```cpp
constexpr size_type find_last_not_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_not_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

\ *Str*
String_view para el que se va a buscar la función miembro.

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que se va a finalizar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, en *ptr*.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `string_view::npos`.

## <a name="basic_string_viewfind_last_of"></a><a name="find_last_of"></a>basic_string_view:: find_last_of

Busca el último carácter que coincide con cualquier elemento de un string_view especificado.

```cpp
constexpr size_type find_last_of(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type find_last_of(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type find_last_of(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

\ *Str*
String_view para el que se va a buscar la función miembro.

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que se va a finalizar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter de la subcadena buscada cuando la operación se realiza correctamente; de lo contrario, `npos`.

## <a name="basic_string_viewfront"></a><a name="front"></a>basic_string_view:: Front

Devuelve un const_reference al primer elemento.

```cpp
constexpr const_reference front() const;
```

### <a name="return-value"></a>Valor devuelto

Const_reference al primer elemento.

### <a name="remarks"></a>Observaciones

Produce una excepción si el string_view está vacío.

## <a name="basic_string_viewlength"></a><a name="length"></a>basic_string_view:: length

Devuelve el número actual de elementos.

```cpp
constexpr size_type length() const noexcept;
```

### <a name="remarks"></a>Observaciones

La función miembro es igual que [size](#size).

## <a name="basic_string_viewmax_size"></a><a name="max_size"></a>basic_string_view:: max_size

Devuelve el número máximo de caracteres que puede contener un string_view.

```cpp
constexpr size_type max_size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Número máximo de caracteres que puede contener un string_view.

### <a name="remarks"></a>Observaciones

Se produce una excepción de tipo [length_error](../standard-library/length-error-class.md) cuando una operación produce un string_view con una longitud mayor que `max_size()`.

## <a name="basic_string_viewoperator"></a><a name="op_eq"></a>basic_string_view:: Operator =

Asigna un string_view o un objeto de cadena convertible a otro string_view.

```cpp
constexpr basic_string_view& operator=(const basic_string_view&) noexcept = default;
```

### <a name="example"></a>Ejemplo

```cpp
   string_view s = "Hello";
   string_view s2 = s;
```

## <a name="basic_string_viewoperator"></a><a name="op_at"></a>basic_string_view:: Operator []

Proporciona un const_reference al carácter con un índice especificado.

```cpp
constexpr const_reference operator[](size_type offset) const;
```

### <a name="parameters"></a>Parámetros

\ de *desplazamiento*
Índice del elemento al que se va a hacer referencia.

### <a name="return-value"></a>Valor devuelto

Const_reference al carácter situado en la posición especificada por el índice del parámetro.

### <a name="remarks"></a>Observaciones

El primer elemento tiene un índice de cero y los enteros positivos indizan de forma consecutiva los siguientes elementos, de modo que una string_view de longitud *n* tenga un elemento *n*-ésimo indizado por el número *n* -1.

`operator[]` es más rápido que [la función miembro de para](#at) proporcionar acceso de lectura a los elementos de un string_view.

`operator[]` no comprueba si el índice pasado como argumento es válido. Un índice no válido pasado a `operator[]` produce un comportamiento indefinido.

La referencia devuelta se puede invalidar si el objeto propietario modifica o elimina los datos de cadena subyacentes.

Al compilar con [\_iterador\_DEpurar\_nivel](../standard-library/iterator-debug-level.md) establecido en 1 o 2, se producirá un error en tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites del string_view. Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).

## <a name="basic_string_viewrbegin"></a><a name="rbegin"></a>basic_string_view:: rbegin

Devuelve un iterador constante al primer elemento de un string_view invertido.

```cpp
constexpr const_reverse_iterator rbegin() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de acceso aleatorio al primer elemento de un string_view invertido, direccionando lo que sería el último elemento en el string_view sin invertir correspondiente.

### <a name="remarks"></a>Observaciones

`rbegin` se usa con un string_view invertido igual que [Begin](#begin) se usa con una string_view. `rbegin` puede usarse para inicializar una iteración hacia atrás.

## <a name="basic_string_viewremove_prefix"></a><a name="remove_prefix"></a>basic_string_view:: remove_prefix

Mueve el puntero hacia delante el número de elementos especificado.

```cpp
constexpr void remove_prefix(size_type n);
```

### <a name="remarks"></a>Observaciones

Deja los datos subyacentes sin modificar. Mueve el puntero de string_view hacia delante por n elementos y establece el miembro de datos de `size` privado en size-n.

## <a name="basic_string_viewremove_suffix"></a><a name="remove_suffix"></a>basic_string_view:: remove_suffix

Reduce el tamaño de la vista en el número especificado de elementos a partir de la parte posterior.

```cpp
constexpr void remove_suffix(size_type n);
```

### <a name="remarks"></a>Observaciones

Deja los datos subyacentes y el puntero en él sin modificar. Establece el miembro de datos `size` privado en size-n.

## <a name="basic_string_viewrend"></a><a name="rend"></a>basic_string_view:: Rend

Devuelve un iterador constante que apunta a uno más allá del último elemento de un string_view invertido.

```cpp
constexpr reverse_iterator rend() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Iterador Const inverso de acceso aleatorio que apunta a uno más allá del último elemento de un string_view invertido.

### <a name="remarks"></a>Observaciones

`rend` se utiliza con un string_view invertido igual que [End](#end) se usa con una string_view. `rend` se puede usar para comprobar si un iterador inverso ha alcanzado el final de su string_view. El valor devuelto por `rend` no se debe desreferenciar.

## <a name="basic_string_viewrfind"></a><a name="rfind"></a>basic_string_view:: rfind

Busca una subcadena que coincida con una secuencia especificada de caracteres en una string_view en orden inverso.

```cpp
constexpr size_type rfind(basic_string_view str, size_type offset = npos) const noexcept;
constexpr size_type rfind(charT chVal, size_type offset = npos) const noexcept;
constexpr size_type rfind(const charT* ptr, size_type offset, size_type count) const;
constexpr size_type rfind(const charT* ptr, size_type offset = npos) const;
```

### <a name="parameters"></a>Parámetros

\ *chVal*
Valor de carácter que va a buscar la función miembro.

\ de *desplazamiento*
Índice en el que va a comenzar la búsqueda.

\ *ptr*
Cadena de C que va a buscar la función miembro.

*recuento*\
Número de caracteres, contando hacia delante desde el primer carácter, de la cadena de C que va a buscar la función miembro.

\ *Str*
String_view para el que se va a buscar la función miembro.

### <a name="return-value"></a>Valor devuelto

Índice del primer carácter de la subcadena cuando se realiza correctamente; de lo contrario `npos`.

## <a name="basic_string_viewsize"></a><a name="size"></a>basic_string_view:: Size

Devuelve el número de elementos de la string_view.

```cpp
constexpr size_type size() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

Longitud de la string_view.

### <a name="remarks"></a>Observaciones

Un string_view puede modificar su longitud, por ejemplo `remove_prefix` y `remove_suffix`. Dado que esto no modifica los datos de cadena subyacentes, el tamaño de una string_view no es necesariamente el tamaño de los datos subyacentes.

## <a name="basic_string_viewsubstr"></a><a name="substr"></a>basic_string_view:: substr

Devuelve un string_view que representa (como máximo) el número especificado de caracteres de una posición especificada.

```cpp
constexpr basic_string_view substr(size_type offset = 0, size_type count = npos) const;
```

### <a name="parameters"></a>Parámetros

\ de *desplazamiento*
Índice que ubica el elemento en la posición desde la que se realiza la copia, con un valor predeterminado de 0.

*recuento*\
Número de caracteres que se van a incluir en la subcadena, si están presentes.

### <a name="return-value"></a>Valor devuelto

Objeto string_view que representa la subsecuencia de elementos especificada.

## <a name="basic_string_viewswap"></a><a name="swap"></a>basic_string_view:: swap

Intercambia dos string_views, es decir, los punteros a los datos de cadena subyacentes y los valores de tamaño.

```cpp
constexpr void swap(basic_string_view& sv) noexcept;
```

### <a name="parameters"></a>Parámetros

\ *VP*
String_view de origen cuyos valores de puntero y tamaño se van a intercambiar con los de la string_view de destino.

## <a name="see-also"></a>Consulte también

[\<string_view >](../standard-library/string-view.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
