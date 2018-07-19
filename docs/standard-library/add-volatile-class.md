---
title: add_volatile (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_volatile
dev_langs:
- C++
helpviewer_keywords:
- add_volatile class
- add_volatile
ms.assetid: cde57277-d764-402d-841e-97611ebaab14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf15ef0b5134af7831cf2e71b4235df9534f3425
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841302"
---
# <a name="addvolatile-class"></a>add_volatile (Clase)

Crea un tipo volátil a partir del tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct add_volatile;

template <class T>
using add_volatile_t = typename add_volatile<T>::type;
```

### <a name="parameters"></a>Parámetros

*T* el tipo para modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `add_volatile<T>` tiene un typedef de miembro `type` que es *T* si *T* es una referencia, una función o un tipo calificado como volátil; si no, es `volatile` *T*. El alias `add_volatile_t` es un acceso directo para acceder al typedef de miembro `type`.

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
