---
title: Definiciones de tipo &lt;ostream&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
ms.openlocfilehash: 82539a3fdadf10d340ca957756e235e8ae00b267
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373585"
---
# <a name="ltostreamgt-typedefs"></a>Definiciones de tipo &lt;ostream&gt;

|||
|-|-|
|[ostream](#ostream)|[wostream](#wostream)|

## <a name="ostream"></a><a name="ostream"></a>ostream

Crea un tipo a partir de `char_traits` basic_ostream especializado en **char** y especializado en **char**.

```cpp
typedef basic_ostream<char, char_traits<char>> ostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="wostream"></a><a name="wostream"></a>wostream

Crea un tipo a partir de `char_traits` basic_ostream especializado en **wchar_t** y especializado en **wchar_t**.

```cpp
typedef basic_ostream<wchar_t, char_traits<wchar_t>> wostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_ostream](../standard-library/basic-ostream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="see-also"></a>Consulte también

[\<>ostream](../standard-library/ostream.md)
