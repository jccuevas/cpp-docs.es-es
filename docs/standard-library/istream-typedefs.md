---
title: Definiciones de tipo &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: e9228bddcc3b99503b6b5f0e93b5ed6eeed773d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363093"
---
# <a name="ltistreamgt-typedefs"></a>Definiciones de tipo &lt;istream&gt;

||||
|-|-|-|
|[iostream](#iostream)|[Istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a><a name="iostream"></a>Iostream

Un `basic_iostream` tipo especializado en **char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_iostream](../standard-library/basic-iostream-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="istream"></a><a name="istream"></a>Istream

Un `basic_istream` tipo especializado en **char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_istream](../standard-library/basic-istream-class.md), especializada para elementos de tipo **char** con rasgos de carácter predeterminados.

## <a name="wiostream"></a><a name="wiostream"></a>wiostream

Un `basic_iostream` tipo especializado en **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_iostream](../standard-library/basic-iostream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="wistream"></a><a name="wistream"></a>wistream

Un `basic_istream` tipo especializado en **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Observaciones

El tipo es un sinónimo de plantilla de clase [basic_istream](../standard-library/basic-istream-class.md), especializada para elementos de tipo **wchar_t** con rasgos de carácter predeterminados.

## <a name="see-also"></a>Consulte también

[\<>istream](../standard-library/istream.md)
