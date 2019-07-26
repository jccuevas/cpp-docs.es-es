---
title: is_void (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_void
helpviewer_keywords:
- is_void class
- is_void
ms.assetid: 99b0de3b-1b38-4949-b053-080e5363174e
ms.openlocfilehash: 28c162f6a868c8d6640ba17af875d84fef78c79a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458873"
---
# <a name="isvoid-class"></a>is_void (Clase)

Comprueba si el tipo es void.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_void;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es **void** o una forma con el valor CV completo de **void**; en caso contrario, contiene false.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_void.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_void<trivial> == " << std::boolalpha
        << std::is_void<trivial>::value << std::endl;
    std::cout << "is_void<void()> == " << std::boolalpha
        << std::is_void<void()>::value << std::endl;
    std::cout << "is_void<void> == " << std::boolalpha
        << std::is_void<void>::value << std::endl;

    return (0);
    }
```

```Output
is_void<trivial> == false
is_void<void()> == false
is_void<void> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
