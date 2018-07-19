---
title: Definiciones de tipo &lt;ostream&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 3f5511cfbf73ddf74fa12954e1a108d8accf875e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852584"
---
# <a name="ltostreamgt-typedefs"></a>Definiciones de tipo &lt;ostream&gt;

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a> ostream

Crea un tipo de basic_ostream que está especializado en `char` y `char_traits` especializado en `char`.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `char` con rasgos de caracteres predeterminados.

## <a name="wostream"></a> wostream

Crea un tipo de basic_ostream que está especializado en `wchar_t` y `char_traits` especializado en `wchar_t`.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la clase de plantilla [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo `wchar_t` con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<ostream>](../standard-library/ostream.md)<br/>
