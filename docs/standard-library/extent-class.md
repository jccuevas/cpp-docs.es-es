---
title: extent (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 0cd53ba8537e706a68ffdcf08df998108266ad20
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457788"
---
# <a name="extent-class"></a>extent (Clase)

Obtiene una dimensión de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

*CONFIGUR*\
La matriz que se enlaza a la consulta.

## <a name="remarks"></a>Comentarios

Si *Ty* es un tipo de matriz que tiene al menos *I* dimensiones, la consulta de tipo contiene el número de elementos de la dimensión especificada por *I*. Si *Ty* no es un tipo de matriz o su rango es menor que *I*, o si *I* es cero y *Ty* es de tipo "matriz de límite desconocido `U`de", la consulta de tipo contiene el valor 0.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }
```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[remove_all_extents (Clase)](../standard-library/remove-all-extents-class.md)\
[remove_extent (Clase)](../standard-library/remove-extent-class.md)
