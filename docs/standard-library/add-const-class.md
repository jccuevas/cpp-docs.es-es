---
title: add_const (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_const
helpviewer_keywords:
- add_const class
- add_const
ms.assetid: 1262a1eb-8c9c-4dd6-9f43-88ba280182f1
ms.openlocfilehash: 6f27a8e4bc0bea3a469d46a56e8885dabe5894df
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456581"
---
# <a name="addconst-class"></a>add_const (Clase)

Crea un tipo const a partir de un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct add_const;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia del modificador de tipo contiene un tipo modificado que es *Ty* si *Ty* es una referencia, una función o un tipo calificado como const; de lo contrario `const Ty`,.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__add_const.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
{
    std::add_const<int>::type *p = (const int *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_const<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_const<int> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[remove_const (Clase)](../standard-library/remove-const-class.md)
