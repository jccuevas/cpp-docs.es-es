---
title: add_volatile (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_volatile
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
ms.openlocfilehash: ff48b1848e2d7631d789621a5ef845d04d8e8821
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495945"
---
# <a name="addvolatile-class"></a>add_volatile (Clase)

Realiza una **volátil** tipo a partir del tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `add_volatile<T>` tiene un miembro **typedef** `type` decir *T* si *T* es una referencia, una función o un tipo calificado como volátil, en caso contrario **volátil** *T*. El alias `add_volatile_t` es un acceso directo para tener acceso al miembro **typedef** `type`.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_volatile_t<int> *p = (volatile int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_volatile<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_volatile<int> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_volatile (Clase)](../standard-library/remove-volatile-class.md)<br/>
