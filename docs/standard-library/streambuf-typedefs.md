---
title: Definiciones de tipo de &lt;streambuf&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::streambuf
- iosfwd/std::wstreambuf
ms.assetid: 2678e18f-f0f0-4995-bc53-f1bc7dfc4ec6
ms.openlocfilehash: 8fb1713dfbc2d9766c488f21d324d801a4886d68
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
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
