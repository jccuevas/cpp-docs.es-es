---
title: is_base_of (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_base_of
helpviewer_keywords:
- is_base_of class
- is_base_of
ms.assetid: 436f6213-1d4c-4ffc-a588-fc7c4887dd86
ms.openlocfilehash: 345301b5eeed7b66f18a54e56b9bee6346078634
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647881"
---
# <a name="isbaseof-class"></a>is_base_of (Clase)

Comprueba si un tipo es la base de otro.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Base, class Derived>
struct is_base_of;
```

### <a name="parameters"></a>Parámetros

*base*<br/>
Clase base que se va a comprobar.

*Derivados*<br/>
Tipo derivado que se va a comprobar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Base* es una clase base del tipo *Derived*, en caso contrario, es false.

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

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_convertible (Clase)](../standard-library/is-convertible-class.md)<br/>
