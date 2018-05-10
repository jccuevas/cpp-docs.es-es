---
title: Clase is_convertible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_convertible
dev_langs:
- C++
helpviewer_keywords:
- is_convertible class
- is_convertible
ms.assetid: 75614008-1894-42ea-bd57-974399628536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fbc0003db72d6a72e31a7d79de786476c946188
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="isconvertible-class"></a>is_convertible (Clase)

Comprueba si un tipo es convertible a otro.

## <a name="syntax"></a>Sintaxis

```cpp
template <class From, class To>
struct is_convertible;
```

### <a name="parameters"></a>Parámetros

`From` El tipo de conversión de.

`Ty` Tipo que se debe convertir a.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si la expresión `To to = from;`, donde `from` es un objeto de tipo `From`, tiene un formato correcto.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_convertible.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_convertible<trivial, int> == " << std::boolalpha
        << std::is_convertible<trivial, int>::value << std::endl;
    std::cout << "is_convertible<trivial, trivial> == " << std::boolalpha
        << std::is_convertible<trivial, trivial>::value << std::endl;
    std::cout << "is_convertible<char, int> == " << std::boolalpha
        << std::is_convertible<char, int>::value << std::endl;

    return (0);
    }

```

```Output
is_convertible<trivial, int> == false
is_convertible<trivial, trivial> == true
is_convertible<char, int> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_base_of (Clase)](../standard-library/is-base-of-class.md)<br/>
