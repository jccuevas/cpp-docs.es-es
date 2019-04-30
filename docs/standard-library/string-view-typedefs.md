---
title: '&lt;string_view&gt; typedefs'
ms.date: 04/19/2019
f1_keywords:
- xstring/std::string_view
- xstring/std::u16string_view
- xstring/std::u32string_view
- xstring/std::wstring_view
ms.openlocfilehash: 16d7ba49facf24dcffb7df444e445d83d92255e0
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346973"
---
# <a name="ltstringviewgt-typedefs"></a>&lt;string_view&gt; typedefs

||||
|-|-|-|
|[string_view](#string_view)|[u16string_view](#u16string_view)|[u32string_view](#u32string_view)|
|[wstring_view](#wstring_view)|

## <a name="string_view"></a> string_view

Un tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo **char**.

```cpp
typedef basic_string_view<char, char_traits<char>> string_view;
```

### <a name="remarks"></a>Comentarios

Las declaraciones siguientes son equivalentes:

```cpp
string_view str("Hello");

basic_string_view<char> str("Hello");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u16string_view"></a> u16string_view

Un tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo `char16_t`.

```cpp
typedef basic_string_view<char16_t, char_traits<char16_t>> u16string_view;
```

### <a name="remarks"></a>Comentarios

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="u32string_view"></a> u32string_view

Un tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo `char32_t`.

```cpp
typedef basic_string_view<char32_t, char_traits<char32_t>> u32string_view;
```

### <a name="remarks"></a>Comentarios

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

## <a name="wstring_view"></a>  wstring_view

Un tipo que describe una especialización de la plantilla de clase [basic_string_view](../standard-library/basic-string-view-class.md) con elementos de tipo **wchar_t**.

```cpp
typedef basic_string_view<wchar_t, char_traits<wchar_t>> wstring_view;
```

### <a name="remarks"></a>Comentarios

Las declaraciones siguientes son equivalentes:

```cpp
wstring_view wstr(L"Hello");

basic_string_view<wchar_t> wstr(L"Hello");
```

Para obtener una lista de los constructores de cadena, vea [basic_string::basic_string](../standard-library/basic-string-class.md#basic_string).

> [!NOTE]
> El tamaño de **wchar_t** es de dos bytes en Windows, pero esto no es necesariamente el caso de todas las plataformas. Si necesita un tipo de carácter ancho string_view con un ancho que se garantiza que siguen siendo los mismos en todas las plataformas, utilice [u16string_view](../standard-library/string-view-typedefs.md#u16string_view) o [u32string_view](../standard-library/string-view-typedefs.md#u32string_view).

## <a name="see-also"></a>Vea también

[\<string_view>](../standard-library/string-view.md)<br/>
