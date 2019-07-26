---
title: remove_cv (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_cv
helpviewer_keywords:
- remove_cv class
- remove_cv
ms.assetid: 8502602a-1c80-479c-84e0-33bd1d6496d6
ms.openlocfilehash: dbe21d8e9f0ed0dc7c72a19584f24ee1bce0803c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451323"
---
# <a name="removecv-class"></a>remove_cv (Clase)

Crea un tipo no cons/volatile a partir de un tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct remove_cv;

template <class T>
using remove_cv_t = typename remove_cv<T>::type;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_cv<T>` contiene un tipo modificado que es `T1` cuando *T* tiene `const T1`el formato, `volatile T1`o `const volatile T1`, de lo contrario, es.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    int *p = (std::remove_cv_t<const volatile int> *)0;

    p = p;  // to quiet "unused" warning
    std::cout << "remove_cv_t<const volatile int> == "
        << typeid(*p).name() << std::endl;

    return (0);
    }
```

```Output
remove_cv_t<const volatile int> == int
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[remove_const (Clase)](../standard-library/remove-const-class.md)\
[remove_volatile (Clase)](../standard-library/remove-volatile-class.md)
