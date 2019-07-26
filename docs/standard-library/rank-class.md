---
title: rank (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::rank
helpviewer_keywords:
- rank class
- rank
ms.assetid: bc9f1b8f-800f-46ca-b6f4-d8579ed5406a
ms.openlocfilehash: cab8d4bb782c7e02df62874a40db14479558da99
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458176"
---
# <a name="rank-class"></a>rank (Clase)

Obtiene el número de dimensiones de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct rank;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

La consulta de tipo contiene el valor del número de dimensiones del tipo de matriz *Ty*o 0 si *Ty* no es un tipo de matriz.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__rank.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "rank<int> == "
        << std::rank<int>::value << std::endl;
    std::cout << "rank<int[5]> == "
        << std::rank<int[5]>::value << std::endl;
    std::cout << "rank<int[5][10]> == "
        << std::rank<int[5][10]>::value << std::endl;

    return (0);
    }
```

```Output
rank<int> == 0
rank<int[5]> == 1
rank<int[5][10]> == 2
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[extent (Clase)](../standard-library/extent-class.md)
