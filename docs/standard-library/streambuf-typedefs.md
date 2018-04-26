---
title: Definiciones de tipo de &lt;streambuf&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: a9629bd9721d1e6089352cfb7fa8c2b40cbc00b7
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ltstreambufgt-typedefs"></a>Definiciones de tipo de &lt;streambuf&gt;

|||
|-|-|
|[streambuf](#streambuf)|[wstreambuf](#wstreambuf)|

## <a name="streambuf"></a>  streambuf

Una especialización de `basic_streambuf` que usa `char` como los parámetros de plantilla.

```cpp
typedef basic_streambuf<char, char_traits<char>> streambuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos del tipo `char` con rasgos de caracteres predeterminados.

## <a name="wstreambuf"></a>  wstreambuf

Una especialización de `basic_streambuf` que usa `wchar_t` como los parámetros de plantilla.

```cpp
typedef basic_streambuf<wchar_t, char_traits<wchar_t>> wstreambuf;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_streambuf](../standard-library/basic-streambuf-class.md), especializada en elementos del tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<streambuf>](../standard-library/streambuf.md)<br/>
