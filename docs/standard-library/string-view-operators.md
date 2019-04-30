---
title: '&lt;string_view&gt; operators'
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
ms.openlocfilehash: 1fbb7faf7d6fc92a053c0f4d47575c5c53c7968e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346923"
---
# <a name="ltstringviewgt-operators"></a>&lt;string_view&gt; operators

Use estos operadores para comparar dos objetos string_view, o un string_view y algún otro objeto de cadena (por ejemplo [std:: String](basic-string-class.md), o **char\***) para que se proporciona una conversión implícita. 

||||
|-|-|-|
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[operator==](#op_eq_eq)|[operator""sv](#op_sv)|

## <a name="op_neq"></a> operator!=

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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador no es lexicográficamente igual que el objeto en el lado derecho; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Debe existir una conversión implícita de *convertible_string_type* a la string_view en el otro lado. 

La comparación se basa en una pareja comparación lexicográfica de las secuencias de caracteres. Si tienen el mismo número de elementos y los elementos son iguales, los dos objetos son iguales. Si no se cumplen estas condiciones, significa que son distintas.

## <a name="op_eq_eq"></a> operador ==

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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador es lexicográficamente igual que el objeto en el lado derecho; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Debe existir una conversión implícita de *convertible_string_type* a la string_view en el otro lado. 

La comparación se basa en una pareja comparación lexicográfica de las secuencias de caracteres. Si tienen el mismo número de elementos y los elementos son iguales, los dos objetos son iguales.


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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador es lexicográficamente menor que el objeto en el lado derecho; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Debe existir una conversión implícita de *convertible_string_type* a la string_view en el otro lado. 

La comparación se basa en una pareja comparación lexicográfica de las secuencias de caracteres. Cuando se encuentra el primer par desigual de caracteres, se devuelve el resultado de esa comparación. Si no se encuentran caracteres distintos, pero una secuencia es más corta, la secuencia más corta es menor que la más larga. En otras palabras, "cat" es menor que "cats".

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

## <a name="op_lt_eq"></a> Operador&lt;=

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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador es lexicográficamente menor o igual que el objeto en el lado derecho; en caso contrario **false**.

### <a name="remarks"></a>Comentarios

Consulte [operador&lt;](#op_lt).

## <a name="op_lt_lt"></a> Operador&lt;&lt;

Escribe un string_view en un flujo de salida.

```cpp
template <class CharType, class Traits>
inline basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& Ostr, const basic_string_view<CharType, Traits> Str);
```

### <a name="parameters"></a>Parámetros

*Ostr*<br/>
que se escriben en un flujo de salida.

*Str*<br/>
String_view debe especificarse en un flujo de salida.

### <a name="return-value"></a>Valor devuelto

que se escriben en un flujo de salida.

### <a name="remarks"></a>Comentarios

Utilice este operador para insertar el contenido de un string_view en un flujo de salida, por ejemplo mediante [std:: cout](iostream.md#cout).

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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador es lexicográficamente mayor que el objeto string_view en el lado derecho; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Consulte [operador&lt;](#op_lt).

## <a name="op_gt_eq"></a> Operador&gt;=

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

*left*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

*right*<br/>
Un objeto de tipo o de cualquier tipo de cadenas que puedan convertirse `basic_string_view` va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si el objeto en el lado izquierdo del operador es lexicográficamente mayor o igual que el objeto en el lado derecho; de lo contrario **false**.

### <a name="remarks"></a>Comentarios

Consulte [operador&lt;](#op_lt).

## <a name="op_sv"></a> operador"" sv (string_view literal)

Construye un string_view desde un literal de cadena. Requiere el espacio de nombres `std::literals::string_view_literals`. 

### <a name="example"></a>Ejemplo

```cpp

using namespace std;
using namespace literals::string_view_literals;

    string_view sv{ "Hello"sv };
    wstring_view wsv{ L"Hello"sv };
    u16string_view sv16{ u"Hello"sv };
    u32string_view sv32{ U"Hello"sv };
```

## <a name="see-also"></a>Vea también

[\<string_view>](../standard-library/string-view.md)<br/>
