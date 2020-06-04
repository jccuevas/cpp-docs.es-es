---
title: remove_all_extents (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_all_extents
helpviewer_keywords:
- remove_all_extents class
- remove_all_extents
ms.assetid: 548dc536-82e7-423a-b8c1-443d66d9632e
ms.openlocfilehash: 0909da3f08cec62bcb915a65c353abdd33c96c9d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451409"
---
# <a name="removeallextents-class"></a>remove_all_extents (Clase)

Convierte un tipo de matriz en un tipo que no es de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct remove_all_extents;

template <class T>
using remove_all_extents_t = typename remove_all_extents<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_all_extents<T>` contiene un tipo modificado que es el tipo de elemento del tipo de matriz *T* con todas las dimensiones de matriz quitadas, o *t* si *t* no es un tipo de matriz.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_all_extents<int> == "
        << typeid(std::remove_all_extents_t<int>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5]> == "
        << typeid(std::remove_all_extents_t<int[5]>).name()
        << std::endl;
    std::cout << "remove_all_extents_t<int[5][10]> == "
        << typeid(std::remove_all_extents_t<int[5][10]>).name()
        << std::endl;

    return (0);
    }
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[remove_extent (Clase)](../standard-library/remove-extent-class.md)
