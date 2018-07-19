---
title: Definiciones de tipo de &lt;streambuf&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 81c7cd875c6083ee77701116f6b1179760373ec0
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953997"
---
# <a name="ltstreambufgt-typedefs"></a>Definiciones de tipo de &lt;streambuf&gt;

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Una especialización de `basic_streambuf` que usa **char** como los parámetros de plantilla.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos del tipo **char** con rasgos de caracteres predeterminados.

## <a name="wstreambuf"></a>  wstreambuf

Una especialización de `basic_streambuf` que usa **wchar_t** como los parámetros de plantilla.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos del tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<streambuf>](../standard-library/streambuf.md)<br/>
