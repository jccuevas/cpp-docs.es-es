---
title: Definiciones de tipo de &lt;streambuf&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 1c9850ad7d7ec9b9c3554e6806f4790ef3613b08
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866217"
---
# <a name="ltstreambufgt-typedefs"></a>Definiciones de tipo de &lt;streambuf&gt;

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Una especialización de `basic_streambuf` que usa **Char** como parámetros de plantilla.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="wstreambuf"></a>  wstreambuf

Una especialización de `basic_streambuf` que usa **wchar_t** como parámetros de plantilla.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Consulte también

[\<streambuf>](../standard-library/streambuf.md)
