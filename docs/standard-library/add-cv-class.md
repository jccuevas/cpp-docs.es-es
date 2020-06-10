---
title: add_cv (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::add_cv
helpviewer_keywords:
- add_cv class
- add_cv
ms.assetid: a5572c78-a097-45d7-b476-ed4876889dea
ms.openlocfilehash: 412dc8426112e65d00b572a65f064667d2709a0d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620782"
---
# <a name="add_cv-class"></a>add_cv (Clase)

Crea un tipo **const volatile** a partir de un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_cv;

template <class T>
using add_cv_t = typename add_cv<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Observaciones

Una instancia del tipo modificado `add_cv<T>` tiene una definición de tipo de `type` miembro equivalente a *T* **typedef** modificada por [Add_volatile](add-volatile-class.md) y [add_const](add-const-class.md), a menos que *T* ya tenga los calificadores CV, sea una referencia o sea una función.

El tipo del asistente `add_cv_t<T>` es un acceso directo para acceder al typedef de miembro `add_cv<T>``type`.

## <a name="example"></a>Ejemplo

```cpp
// add_cv.cpp
// compile by using: cl /EHsc /W4 add_cv.cpp
#include <type_traits>
#include <iostream>

struct S {
    void f() {
        std::cout << "invoked non-cv-qualified S.f()" << std::endl;
    }
    void f() const {
        std::cout << "invoked const S.f()" << std::endl;
    }
    void f() volatile {
        std::cout << "invoked volatile S.f()" << std::endl;
    }
    void f() const volatile {
        std::cout << "invoked const volatile S.f()" << std::endl;
    }
};

template <class T>
void invoke() {
    T t;
    ((T *)&t)->f();
}

int main()
{
    invoke<S>();
    invoke<std::add_const<S>::type>();
    invoke<std::add_volatile<S>::type>();
    invoke<std::add_cv<S>::type>();
}
```

```Output
invoked non-cv-qualified S.f()
invoked const S.f()
invoked volatile S.f()
invoked const volatile S.f()
```

## <a name="requirements"></a>Requisitos

**Encabezado:**\<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[remove_const (clase)](remove-const-class.md)\
[remove_volatile (clase)](remove-volatile-class.md)
