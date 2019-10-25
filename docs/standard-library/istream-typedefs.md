---
title: Definiciones de tipo &lt;istream&gt;
ms.date: 11/04/2016
f1_keywords:
- istream/std::iostream
- istream/std::istream
- istream/std::wiostream
- istream/std::wistream
ms.assetid: 55bc1f84-53a7-46ca-a36f-ac6ef75d0374
ms.openlocfilehash: 9a25e4aa9ee42ea36d1bb8d6b196b36ff5c97758
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689479"
---
# <a name="ltistreamgt-typedefs"></a>Definiciones de tipo &lt;istream&gt;

||||
|-|-|-|
|[iostream](#iostream)|[istream](#istream)|[wiostream](#wiostream)|
|[wistream](#wistream)|

## <a name="iostream"></a>  iostream

Tipo `basic_iostream` especializado en **Char**.

```cpp
typedef basic_iostream<char, char_traits<char>> iostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la plantilla de clase [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="istream"></a>  istream

Tipo `basic_istream` especializado en **Char**.

```cpp
typedef basic_istream<char, char_traits<char>> istream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la plantilla de clase [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos de tipo **Char** con rasgos de caracteres predeterminados.

## <a name="wiostream"></a>  wiostream

Tipo `basic_iostream` especializado en **wchar_t**.

```cpp
typedef basic_iostream<wchar_t, char_traits<wchar_t>> wiostream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la plantilla de clase [basic_iostream](../standard-library/basic-iostream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="wistream"></a>  wistream

Tipo `basic_istream` especializado en **wchar_t**.

```cpp
typedef basic_istream<wchar_t, char_traits<wchar_t>> wistream;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo de la plantilla de clase [basic_istream](../standard-library/basic-istream-class.md), especializada en elementos de tipo **wchar_t** con rasgos de caracteres predeterminados.

## <a name="see-also"></a>Vea también

[\<istream>](../standard-library/istream.md)
