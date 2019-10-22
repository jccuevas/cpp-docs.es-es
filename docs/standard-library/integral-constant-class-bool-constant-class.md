---
title: Clase integral_constant, clase bool_constant
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: 9577ce51d4b0773f7b309fe3dc6dcb5820693dcb
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689533"
---
# <a name="integral_constant-class-bool_constant-class"></a>Clase integral_constant, clase bool_constant

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

*T* \
Tipo de la constante.

*v* \
Valor de la constante.

## <a name="remarks"></a>Comentarios

La plantilla de clase `integral_constant`, cuando está especializada con un tipo entero *t* y un valor *v* de ese tipo, representa un objeto que contiene una constante de ese tipo entero con el valor especificado. El miembro denominado `type` es un alias para el tipo de especialización de la plantilla generada y el miembro `value` contiene el valor *v* usado para crear la especialización.

La plantilla de clase `bool_constant` es una especialización parcial explícita de `integral_constant` que usa **bool** como argumento *t* .

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

[<type_traits>](../standard-library/type-traits.md)\
\ [false_type](../standard-library/type-traits-typedefs.md#false_type)
[true_type](../standard-library/type-traits-typedefs.md#true_type)
