---
title: Clase is_pointer | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_pointer
dev_langs:
- C++
helpviewer_keywords:
- is_pointer class
- is_pointer
ms.assetid: 44e0a403-7241-4e0a-8922-32877bcb9a4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30234c932aad28d16830b80fd19e4ad334ba407c
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38962821"
---
# <a name="ispointer-class"></a>is_pointer (Clase)

Comprueba si el tipo es un puntero.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_pointer;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es un puntero a **void**, un puntero a un objeto, o un puntero a una función o una `cv-qualified` formulario de uno de ellos; en caso contrario, contiene false. Tenga en cuenta que `is_pointer` es false si *Ty* es un puntero a miembro o un puntero a función miembro.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_pointer.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_pointer<trivial> == " << std::boolalpha
        << std::is_pointer<trivial>::value << std::endl;
    std::cout << "is_pointer<int trivial::*> == " << std::boolalpha
        << std::is_pointer<int trivial::*>::value << std::endl;
    std::cout << "is_pointer<trivial *> == " << std::boolalpha
        << std::is_pointer<trivial *>::value << std::endl;
    std::cout << "is_pointer<int> == " << std::boolalpha
        << std::is_pointer<int>::value << std::endl;
    std::cout << "is_pointer<int *> == " << std::boolalpha
        << std::is_pointer<int *>::value << std::endl;

    return (0);
    }

```

```Output
is_pointer<trivial> == false
is_pointer<int trivial::*> == false
is_pointer<trivial *> == true
is_pointer<int> == false
is_pointer<int *> == true
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_member_pointer (Clase)](../standard-library/is-member-pointer-class.md)<br/>
[is_reference (Clase)](../standard-library/is-reference-class.md)<br/>
