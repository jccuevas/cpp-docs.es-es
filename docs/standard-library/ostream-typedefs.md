---
title: Definiciones de tipo &lt;ostream&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::ostream
- iosfwd/std::wostream
ms.assetid: 2ec4dc52-a01f-4654-bd65-dd5288777c48
caps.latest.revision: 11
manager: ghogen
ms.openlocfilehash: 8c451b16a581ab13f87c7bcca793efe3a0f07bf5
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
