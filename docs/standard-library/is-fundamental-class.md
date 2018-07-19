---
title: Clase is_fundamental | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_fundamental
dev_langs:
- C++
helpviewer_keywords:
- is_fundamental class
- is_fundamental
ms.assetid: b84eee84-2fb2-4611-beaf-b384074d8b6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63b2c11b7a5a8d48e3fe068807b641489c6aa323
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957365"
---
# <a name="isfundamental-class"></a>is_fundamental (Clase)

Prueba si el tipo es nulo o aritmético

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_fundamental;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es un tipo fundamental, es decir, **void**, un tipo entero, un flotante, tipo de punto o un `cv-qualified` formulario de uno de ellos; en caso contrario, contiene false.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_fundamental.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_fundamental<trivial> == " << std::boolalpha
        << std::is_fundamental<trivial>::value << std::endl;
    std::cout << "is_fundamental<int> == " << std::boolalpha
        << std::is_fundamental<int>::value << std::endl;
    std::cout << "is_fundamental<const float> == " << std::boolalpha
        << std::is_fundamental<const float>::value << std::endl;
    std::cout << "is_fundamental<void> == " << std::boolalpha
        << std::is_fundamental<void>::value << std::endl;

    return (0);
    }

```

```Output
is_fundamental<trivial> == false
is_fundamental<int> == true
is_fundamental<const float> == true
is_fundamental<void> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_compound (Clase)](../standard-library/is-compound-class.md)<br/>
