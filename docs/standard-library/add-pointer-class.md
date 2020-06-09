---
title: add_pointer (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_pointer
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
ms.openlocfilehash: 8adeffd0352d04fe844b286ea7456c66e907a0a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619260"
---
# <a name="add_pointer-class"></a>add_pointer (Clase)

Crea un puntero-a-tipo a partir de un tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Observaciones

El **typedef** de miembro `type` nombra el mismo tipo que `remove_reference<T>::type*` . El alias `add_pointer_t` es un acceso directo para acceder al **typedef** de miembro `type` .

Como no es válido crear punteros a partir de referencias, `add_pointer` quita la referencia, si existe, del tipo especificado antes de crear un puntero-a-tipo. Por consiguiente, se puede usar un tipo con `add_pointer` sin que preocupe el hecho de si el tipo es una referencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra que `add_pointer` de un tipo es igual que un puntero a ese tipo.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Requisitos

**Encabezado:**\<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[remove_pointer (clase)](remove-pointer-class.md)
