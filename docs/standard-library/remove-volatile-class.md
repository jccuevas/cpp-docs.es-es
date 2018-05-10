---
title: remove_volatile (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::remove_volatile
dev_langs:
- C++
helpviewer_keywords:
- remove_volatile class
- remove_volatile
ms.assetid: 8b87e2c2-a581-4eb3-8691-c5603910d61d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d1cd2b4882c4b5e62a2f6574b3011b74747e412b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="removevolatile-class"></a>remove_volatile (Clase)

Crea un tipo no volátil a partir de un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct remove_volatile;

template <class T>
using remove_volatile_t = typename remove_volatile<T>::type;
```

### <a name="parameters"></a>Parámetros

`T` Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_volatile<T>` contiene un tipo modificado que es `T1` cuando `T` tiene la forma `volatile T1`; si no es `T`.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_volatile_t<volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << " remove_volatile_t<volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_volatile_t<volatile int> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_volatile (Clase)](../standard-library/add-volatile-class.md)<br/>
