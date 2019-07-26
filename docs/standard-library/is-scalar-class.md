---
title: is_scalar (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_scalar
helpviewer_keywords:
- is_scalar class
- is_scalar
ms.assetid: a0cdfc9a-f27e-4808-890f-6ed7942db60c
ms.openlocfilehash: d562ba4beb037d547846f57e7b40eaceb409a358
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449812"
---
# <a name="isscalar-class"></a>is_scalar (Clase)

Comprueba si el tipo es escalar.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_scalar;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es un tipo entero, un tipo de punto flotante, un tipo de enumeración, un tipo de puntero o un puntero a un `cv-qualified` tipo de miembro, o bien un formulario de uno de ellos; en caso contrario, contiene false.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_scalar.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_scalar<trivial> == " << std::boolalpha
        << std::is_scalar<trivial>::value << std::endl;
    std::cout << "is_scalar<trivial *> == " << std::boolalpha
        << std::is_scalar<trivial *>::value << std::endl;
    std::cout << "is_scalar<int> == " << std::boolalpha
        << std::is_scalar<int>::value << std::endl;
    std::cout << "is_scalar<float> == " << std::boolalpha
        << std::is_scalar<float>::value << std::endl;

    return (0);
    }
```

```Output
is_scalar<trivial> == false
is_scalar<trivial *> == true
is_scalar<int> == true
is_scalar<float> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[Clase is_compound](../standard-library/is-compound-class.md)
