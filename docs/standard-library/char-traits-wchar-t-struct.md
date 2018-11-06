---
title: char_traits&lt;wchar_t&gt; (Struct)
ms.date: 11/04/2016
f1_keywords:
- char_traits<wchar_t>
- iosfwd/std::char_traits<wchar_t>
helpviewer_keywords:
- char_traits<wchar_t> class
ms.assetid: 31f34072-04d6-4871-88fe-48e17d473484
ms.openlocfilehash: ef40a34b5aa874c8bdf48aeb7657ae3496160eec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584748"
---
# <a name="chartraitsltwchartgt-struct"></a>char_traits&lt;wchar_t&gt; (Struct)

Una clase que es una especialización del struct de plantilla **char_traits\<CharType >** a un elemento de tipo **wchar_t**.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct char_traits<wchar_t>;
```

## <a name="remarks"></a>Comentarios

La especialización permite aprovechar las funciones de biblioteca que manipulan objetos de este tipo de struct **wchar_t**.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<string>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[char_traits (Struct)](../standard-library/char-traits-struct.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
