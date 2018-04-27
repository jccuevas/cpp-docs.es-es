---
title: Clase is_integral | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_integral
dev_langs:
- C++
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4681bff0e989eebe7c52106eab17cdd59789981
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="isintegral-class"></a>is_integral (Clase)

Comprueba si el tipo es entero.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `Ty` es uno de los tipos enteros o un formulario `cv-qualified` de uno de ellos; en caso contrario, es false.

Un tipo entero es uno de `bool`, `char`, `unsigned char`, `signed char`, `wchar_t`, `short`, `unsigned short`, `int`, `unsigned int`, `long` y `unsigned long`. Además, con los compiladores que los proporcionan, un tipo entero puede ser uno de `long long`, `unsigned long long`, `__int64` y `unsigned __int64`.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }

```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum (Clase)](../standard-library/is-enum-class.md)<br/>
[is_floating_point (Clase)](../standard-library/is-floating-point-class.md)<br/>
