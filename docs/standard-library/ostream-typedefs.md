---
title: Definiciones de tipo &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: d0ceae12069712c7a124990d0f81968c21bc683a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856614"
---
# <a name="ltostreamgt-typedefs"></a>Definiciones de tipo &lt;ostream&gt;

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a> ostream

Crea un tipo a partir de basic_ostream especializado en **Char** y `char_traits` Specialized en **Char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="wostream"></a> wostream

Crea un tipo a partir de basic_ostream especializado en **wchar_t** y `char_traits` especializados en **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de la plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Consulte también

[\<ostream>](../standard-library/ostream.md)
