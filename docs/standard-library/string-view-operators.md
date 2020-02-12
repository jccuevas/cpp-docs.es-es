---
title: operadores de&gt; de string_view de &lt;
ms.date: 04/19/2019
f1_keywords:
- xstring/basic_string_view::operator!=
- xstring/basic_string_view::operator&gt;
- xstring/basic_string_view::operator&gt;=
- xstring/basic_string_view::operator&lt;
- xstring/basic_string_view::operator&lt;&lt;
- xstring/basic_string_view::operator&lt;=
- xstring/basic_string_view::operator+
- xstring/basic_string_view::operator==
helpviewer_keywords:
- std::basic_string_view::operator!=
- std::basic_string_view::operator&gt;
- std::basic_string_view::operator&gt;=
- std::basic_string_view::operator&lt;
- std::basic_string_view::operator&lt;&lt;
- std::basic_string_view::operator&lt;=, std::basic_string_view::operator==
ms.openlocfilehash: 699b1f1bddeb71ecbf03297d162a7e45ebd39609
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127743"
---
# <a name="ltstring_viewgt-operators"></a>operadores de&gt; de string_view de &lt;

Utilice estos operadores para comparar dos objetos string_view, o un string_view y algún otro objeto de cadena (por ejemplo, [STD:: String](basic-string-class.md)o **Char\*** ) para el que se proporciona una conversión implícita. 

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operador "" VP](#op_sv)|

## <a name="op_neq"></a>operador! =

Comprueba si el objeto en el lado izquierdo del operador no es igual al objeto del lado derecho.

```cpp
template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator!=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator!=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador no es lexicográficamente igual que el objeto del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Debe existir una conversión implícita de *convertible_string_type* al string_view en el otro lado. 

La comparación se basa en una comparación lexicográfica en pares de las secuencias de caracteres. Si tienen el mismo número de elementos y los elementos son iguales, los dos objetos son iguales. Si no se cumplen estas condiciones, significa que son distintas.

## <a name="op_eq_eq"></a>operador = =

Comprueba si el objeto en el lado izquierdo del operador es igual al objeto del lado derecho.

```cpp
template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator==(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator==(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador es lexicográficamente igual que el objeto del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Debe existir una conversión implícita de *convertible_string_type* al string_view en el otro lado. 

La comparación se basa en una comparación lexicográfica en pares de las secuencias de caracteres. Si tienen el mismo número de elementos y los elementos son iguales, los dos objetos son iguales.


## <a name="op_lt"></a> operator&lt;

Comprueba si el objeto en el lado izquierdo del operador es menor que el objeto de la derecha sidestring_view
```cpp
template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador es lexicográficamente menor que el objeto del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Debe existir una conversión implícita de *convertible_string_type* al string_view en el otro lado. 

La comparación se basa en una comparación lexicográfica en pares de las secuencias de caracteres. Cuando se encuentra el primer par de caracteres distinto de, se devuelve el resultado de la comparación. Si no se encuentran caracteres desiguales, pero una secuencia es más corta, la secuencia más corta es menor que la más larga. En otras palabras, "cat" es menor que "gatos".

### <a name="example"></a>Ejemplo

```cpp
#include <string>
#include <string_view>

using namespace std;

int main()
{
    string_view sv1 { "ABA" };
    string_view sv2{ "ABAC" };
    string_view sv3{ "ABAD" };
    string_view sv4{ "ABACE" };

    bool result = sv2 > sv1; // true
    result = sv3 > sv2; // true
    result = sv3 != sv1; // true
    result = sv4 < sv3; // true because `C` < `D`
}
```

## <a name="op_lt_eq"></a>operador&lt;=

Comprueba si el objeto en el lado izquierdo del operador es menor o igual que el objeto del lado derecho.

```cpp
template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator<=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator<=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador es lexicográficamente menor o igual que el objeto del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Vea [operador&lt;](#op_lt).

## <a name="op_lt_lt"></a>operador&lt;&lt;

Escribe una string_view en un flujo de salida.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parámetros

\ *ostr*
flujo de salida en el que se escribe.

\ *Str*
String_view que se va a escribir en un flujo de salida.

### <a name="return-value"></a>Valor devuelto

flujo de salida en el que se escribe.

### <a name="remarks"></a>Observaciones

Utilice este operador para insertar el contenido de una string_view en un flujo de salida, por ejemplo, mediante [STD:: cout](iostream.md#cout).

## <a name="op_gt"></a> operator&gt;

Comprueba si el objeto en el lado izquierdo del operador es mayor que el objeto del lado derecho.

```cpp
template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador es lexicográficamente mayor que el objeto de string_view del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Vea [operador&lt;](#op_lt).

## <a name="op_gt_eq"></a>operador&gt;=

Comprueba si el objeto en el lado izquierdo del operador es mayor o igual que el objeto del lado derecho.

```cpp
template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    const basic_string_view<CharType, Traits>& right);

template <class CharType, class Traits>
bool operator>=(
    const basic_string_view<CharType, Traits>& left,
    convertible_string_type right);

template <class CharType, class Traits>
bool operator>=(
    convertible_string_type left,
    const basic_string_view<CharType, Traits>& right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

\ *derecha*
Cualquier tipo de cadena convertible o un objeto de tipo `basic_string_view` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**true** si el objeto en el lado izquierdo del operador es lexicográficamente mayor o igual que el objeto del lado derecho; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

Vea [operador&lt;](#op_lt).

## <a name="op_sv"></a>operador "" VP (string_view literal)

Construye una string_view a partir de un literal de cadena. Requiere `std::literals::string_view_literals`de espacio de nombres. 

### <a name="example"></a>Ejemplo

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Consulte también

[\<string_view >](../standard-library/string-view.md)
