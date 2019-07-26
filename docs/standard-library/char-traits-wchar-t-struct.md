---
title: char_traits&lt;wchar_t&gt; (Struct)
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: a2f8a882020ddb3d87436d08b3d85ea9407b1c08
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458976"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; (Struct)

Una clase que es una especialización del struct de plantilla **char_traits\<CharType >** a un elemento de tipo **wchar_t**.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Comentarios

La especialización permite que el struct aproveche las funciones de biblioteca que manipulan objetos de este tipo **wchar_t**.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<string>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[char_traits (Struct)](../standard-library/char-traits-struct.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
