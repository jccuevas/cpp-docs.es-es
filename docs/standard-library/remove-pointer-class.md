---
title: remove_pointer (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_pointer
helpviewer_keywords:
- remove_pointer class
- remove_pointer
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
ms.openlocfilehash: 786a1cba5fc35014e33e3e19245271adefec1372
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451255"
---
# <a name="removepointer-class"></a>remove_pointer (Clase)

Convierte un tipo de puntero en un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct remove_pointer;

template <class T>
using remove_pointer_t = typename remove_pointer<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_pointer<T>` contiene un tipo modificado que es `T1` cuando *T* tiene el formato `T1*`, `T1* const`, `T1* volatile`o `T1* const volatile`, de lo contrario, *t*.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_pointer_t<int *> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_pointer_t<int *> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_pointer_t<int *> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[add_pointer (Clase)](../standard-library/add-pointer-class.md)
