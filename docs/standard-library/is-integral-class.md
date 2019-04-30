---
title: is_integral (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: c7d0d8b8572c26bfa75b9fab81900c0ae21fb932
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336500"
---
# <a name="isintegral-class"></a>is_integral (Clase)

Comprueba si el tipo es entero.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es uno de los tipos enteros, o un `cv-qualified` formulario de uno de los tipos enteros, en caso contrario, es false.

Un tipo entero es uno de **bool**, **char**, **unsigned char**, **firmado char**, **wchar_t**, **corto**, **entero corto sin signo**, **int**, **int sin signo**, **largo**y **unsigned long**. Además, los compiladores que proporcionarlas, un tipo entero puede ser uno de **long long**, **long long sin signo**, **__int64**, y **__int64 sin signo**.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum (Clase)](../standard-library/is-enum-class.md)<br/>
[is_floating_point (Clase)](../standard-library/is-floating-point-class.md)<br/>
