---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 0ec278484b7c1c9887771f6cbe7e5d0b05205dd7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376673"
---
# <a name="ltstring_viewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a><a name="string_view"></a>string_view

Tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Observaciones

Las declaraciones siguientes son equivalentes:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a><a name="u16string_view"></a>u16string_view

Tipo que describe una especialización [basic_string_view](../standard-library/basic-string-view-class.md) de la plantilla `char16_t`de clase basic_string_view con elementos de tipo .

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Observaciones

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a><a name="u32string_view"></a>u32string_view

Tipo que describe una especialización [basic_string_view](../standard-library/basic-string-view-class.md) de la plantilla `char32_t`de clase basic_string_view con elementos de tipo .

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Observaciones

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a><a name="wstring_view"></a>wstring_view

Un tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Observaciones

Las declaraciones siguientes son equivalentes:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> El tamaño de **wchar_t** es de dos bytes en Windows, pero esto no es necesariamente el caso para todas las plataformas. Si necesita un tipo de carácter string_view ancho con un ancho que se garantiza que seguirá siendo el mismo en todas las plataformas, utilice [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) o [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Consulte también

[\<string_view>](../standard-library/string-view.md)
