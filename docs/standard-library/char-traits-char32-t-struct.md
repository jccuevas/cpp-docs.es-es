---
title: char_traits&lt;char32_t&gt; (Struct) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iosfwd/std::char_traits<char_32t>
- char_traits<char32_t>
dev_langs:
- C++
helpviewer_keywords:
- char_traits<char32_t> class
ms.assetid: c0315466-45d0-4a99-b83e-3b1dbfbfbbc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6caffb278fbcb94eff1042716adc384b56ae6050
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="chartraitsltchar32tgt-struct"></a>char_traits&lt;char32_t&gt; (Struct)

Un struct que es una especialización del struct de plantilla **char_traits\<CharType>** para un elemento de tipo `char32_t`.

## <a name="syntax"></a>Sintaxis

```cpp
template <>
struct char_traits<char32_t>;
```

## <a name="remarks"></a>Comentarios

La especialización permite que struct aproveche las funciones de biblioteca que manipulan objetos de este tipo `char32_t`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<string>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<string>](../standard-library/string.md)<br/>
[char_traits (Struct)](../standard-library/char-traits-struct.md)<br/>
