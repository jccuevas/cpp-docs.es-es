---
title: is_base_of (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: d56222f218033d00583e5e3def9790720ef7bb94
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456616"
---
# <a name="isbaseof-class"></a>is_base_of (Clase)

Comprueba si un tipo es la base de otro.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>Parámetros

*Básica*\
Clase base que se va a comprobar.

*Obtienen*\
Tipo derivado que se va a comprobar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *base* es una clase base del tipo *derivado*; en caso contrario, contiene false.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

struct base
    {
    int val;
    };

struct derived
    : public base
    {
    };

int main()
    {
    std::cout << "is_base_of<base, base> == " << std::boolalpha
        << std::is_base_of<base, base>::value << std::endl;
    std::cout << "is_base_of<base, derived> == " << std::boolalpha
        << std::is_base_of<base, derived>::value << std::endl;
    std::cout << "is_base_of<derived, base> == " << std::boolalpha
        << std::is_base_of<derived, base>::value << std::endl;

    return (0);
    }
```

```Output
is_base_of<base, base> == true
is_base_of<base, derived> == true
is_base_of<derived, base> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[Clase is_convertible](../standard-library/is-convertible-class.md)
