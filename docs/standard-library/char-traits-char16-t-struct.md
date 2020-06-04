---
title: char_traits&lt;char16_t&gt; (Struct)
ms.date: 11/04/2016
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
ms.openlocfilehash: d83f5278c2c4f8344334bfce40946612e9ca3e56
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448966"
---
# <a name="chartraitsltchar16tgt-struct"></a>char_traits&lt;char16_t&gt; (Struct)

Un struct que es una especialización del struct de plantilla **char_traits\<CharType>** para un elemento de tipo `char16_t`.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct char_traits<char16_t>;
```

## <a name="remarks"></a>Comentarios

La especialización permite que struct aproveche las funciones de biblioteca que manipulan objetos del tipo `char16_t`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<string>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<string>](../standard-library/string.md)\
[char_traits (Struct)](../standard-library/char-traits-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
