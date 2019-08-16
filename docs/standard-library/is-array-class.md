---
title: is_array (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_array
helpviewer_keywords:
- is_array class
- is_array
ms.assetid: 61fb2201-8de3-4746-9721-617f02df170f
ms.openlocfilehash: c54664ed5f56411929c60a0f15ae3c4f0e4581ce
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456657"
---
# <a name="isarray-class"></a>is_array (Clase)

Comprueba si el tipo es array.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_array;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es un tipo de matriz; en caso contrario, contiene false.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_array.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_array<trivial> == " << std::boolalpha
        << std::is_array<trivial>::value << std::endl;
    std::cout << "is_array<int> == " << std::boolalpha
        << std::is_array<int>::value << std::endl;
    std::cout << "is_array<int[5]> == " << std::boolalpha
        << std::is_array<int[5]>::value << std::endl;

    return (0);
    }
```

```Output
is_array<trivial> == false
is_array<int> == false
is_array<int[5]> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[Clase extent](../standard-library/extent-class.md)\
[Clase rank](../standard-library/rank-class.md)
