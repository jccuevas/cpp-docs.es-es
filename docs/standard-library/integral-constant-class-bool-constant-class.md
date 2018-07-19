---
title: integral_constant (Clase), bool_constant (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
dev_langs:
- C++
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bff57549307eeaa9245c0bb4083b206471fe726
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962538"
---
# <a name="integralconstant-class-boolconstant-class"></a>Clase integral_constant, clase bool_constant

Crea una constante entera a partir de un tipo y un valor.

## <a name="syntax"></a>Sintaxis

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>Parámetros

*T* el tipo de la constante.

*v* el valor de la constante.

## <a name="remarks"></a>Comentarios

La clase de plantilla `integral_constant`, si está especializada con un tipo entero *T* y un valor *v* de ese tipo, representa un objeto que contiene una constante de ese tipo entero con el valor especificado. El miembro denominado `type` es un alias para el tipo de especialización de la plantilla generada y el miembro `value` contiene el valor *v* usado para crear la especialización.

El `bool_constant` clase de plantilla es una especialización parcial explícita de `integral_constant` que usa **bool** como el *T* argumento.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }

```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[false_type](../standard-library/type-traits-typedefs.md#false_type)<br/>
[true_type](../standard-library/type-traits-typedefs.md#true_type)<br/>
