---
title: extent (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::extent
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
ms.openlocfilehash: 7463b424d15ee86f851b7d81953abf3fe1c98fee
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519089"
---
# <a name="extent-class"></a>extent (Clase)

Obtiene una dimensión de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

*I*<br/>
La matriz que se enlaza a la consulta.

## <a name="remarks"></a>Comentarios

Si *Ty* es un tipo de matriz que tiene al menos *me* dimensiones, la consulta de tipo contiene el número de elementos de la dimensión especificada por *me*. Si *Ty* no es un tipo de matriz o el rango es menor que *me*, o si *me* es cero y *Ty* es de tipo "matriz de límite desconocido de `U` ", la consulta de tipo contiene el valor 0.

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

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents (Clase)](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent (Clase)](../standard-library/remove-extent-class.md)<br/>
