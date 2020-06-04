---
title: Definiciones de tipo de &lt;streambuf&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8eb058f161a9f30ccf5e9d49307b50c215f79c22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376689"
---
# <a name="ltstreambufgt-typedefs"></a>Definiciones de tipo de &lt;streambuf&gt;

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a><a name="streambuf"></a>streambuf

Una especialización de `basic_streambuf` que utiliza **char** como los parámetros de plantilla.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="wstreambuf"></a><a name="wstreambuf"></a>wstreambuf

Una especialización que utiliza `basic_streambuf` **wchar_t** como parámetros de plantilla.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="see-also"></a>Consulte también

[\<>streambuf](../standard-library/streambuf.md)
