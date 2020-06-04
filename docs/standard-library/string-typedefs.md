---
title: Definiciones de tipo de &lt;string&gt;
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 1ee36d67d137c74e17fff845f9d412b2673f311e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376638"
---
# <a name="ltstringgt-typedefs"></a>Definiciones de tipo de &lt;string&gt;

||||
|-|-|-|
|[string](#string)|[u16string](#u16string)|[u32string](#u32string)|
|[wstring](#wstring)|

## <a name="string"></a>Cadena de <a name="string"></a>

Tipo que describe una especialización de la plantilla de clase [basic_string](../standard-library/basic-string-class.md) con elementos de tipo **char**.

Otras definiciones de tipo que especializan `basic_string` incluyen [wstring](../standard-library/string-typedefs.md#wstring), [u16string](../standard-library/string-typedefs.md#u16string) y [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Observaciones

Las declaraciones siguientes son equivalentes:

```cpp
string str("");

basic_string<char> str("");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string"></a><a name="u16string"></a>u16string

Tipo que describe una especialización [basic_string](../standard-library/basic-string-class.md) de la plantilla `char16_t`de clase basic_string con elementos de tipo .

Hay otras definiciones de tipo que especializan `basic_string` entre las que se incluyen [wstring](../standard-library/string-typedefs.md#wstring), [string](../standard-library/string-typedefs.md#string) y [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Observaciones

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string"></a><a name="u32string"></a>u32string

Tipo que describe una especialización [basic_string](../standard-library/basic-string-class.md) de la plantilla `char32_t`de clase basic_string con elementos de tipo .

Hay otras definiciones de tipo que especializan `basic_string`, entre las que se incluyen [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) y [wstring](../standard-library/string-typedefs.md#wstring).

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Observaciones

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring"></a><a name="wstring"></a>wstring

Tipo que describe una especialización de la plantilla de clase [basic_string](../standard-library/basic-string-class.md) con elementos de tipo **wchar_t**.

Hay otras definiciones de tipo que especializan `basic_string`, entre las que se incluyen [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) y [u32string](../standard-library/string-typedefs.md#u32string).

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Observaciones

Las declaraciones siguientes son equivalentes:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> El tamaño de **wchar_t** está definido por la implementación. Si el código depende **de wchar_t** a un tamaño determinado, compruebe `sizeof(wchar_t)`la implementación de la plataforma (por ejemplo, con ). Si necesita un tipo de carácter de cadena con una anchura garantizada de modo que se mantenga igual en todas las plataformas, use [string](../standard-library/string-typedefs.md#string), [u16string](../standard-library/string-typedefs.md#u16string) o [u32string](../standard-library/string-typedefs.md#u32string).

## <a name="see-also"></a>Consulte también

[\<>de cuerda](../standard-library/string.md)
