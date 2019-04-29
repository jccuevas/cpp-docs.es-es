---
title: is_compound (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_compound
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
ms.openlocfilehash: f270a1a58bb8023d91d84b0d1ca3395d36298c95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62337107"
---
# <a name="iscompound-class"></a>is_compound (Clase)

Comprueba si el tipo especificado no es fundamental.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene **false** si el tipo de *Ty* es un tipo fundamental (es decir, si [is_fundamental](../standard-library/is-fundamental-class.md)\<Ty > contiene  **True**); en caso contrario, contiene **true**. Por lo tanto, el predicado se aplica **true** si *Ty* es un tipo de matriz, un tipo de función, un puntero a **void** o un objeto o una función, una referencia, una clase, una unión, enumeración o un puntero a miembro de clase no estática, o un *calificado para cv* formulario de uno de ellos.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }
```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class (Clase)](../standard-library/is-class-class.md)<br/>
