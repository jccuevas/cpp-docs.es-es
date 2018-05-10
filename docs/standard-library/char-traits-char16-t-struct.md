---
title: char_traits&lt;char16_t&gt; (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- char_traits<char16_t>
- iosfwd/std::char_traits<char16_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char16_t> class
ms.assetid: 5daf3b62-dd6e-451f-b189-0350a04ff966
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24d6c3d5dd11290ce4151b5d54885ba492b8ee45
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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

[\<string>](../standard-library/string.md)<br/>
[char_traits (Struct)](../standard-library/char-traits-struct.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
