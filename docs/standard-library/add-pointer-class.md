---
title: add_pointer (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::add_pointer
dev_langs:
- C++
helpviewer_keywords:
- add_pointer class
- add_pointer
ms.assetid: d8095cb0-6578-4143-b78f-87f82485298c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c7a80ffbfbcfb8c350eecc54e87c4cadaaab0295
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841423"
---
# <a name="addpointer-class"></a>add_pointer (Clase)

Crea un puntero-a-tipo a partir de un tipo especificado.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct add_pointer;

template <class T>
using add_pointer_t = typename add_pointer<T>::type;
```

### <a name="parameters"></a>Parámetros

*T* el tipo para modificar.

## <a name="remarks"></a>Comentarios

El typedef de miembro `type` denomina al mismo tipo como `remove_reference<T>::type*`. El alias `add_pointer_t` es un acceso directo para acceder al typedef de miembro `type`.

Como no es válido crear punteros a partir de referencias, `add_pointer` quita la referencia, si existe, del tipo especificado antes de crear un puntero-a-tipo. Por consiguiente, se puede usar un tipo con `add_pointer` sin que preocupe el hecho de si el tipo es una referencia.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra que `add_pointer` de un tipo es igual que un puntero a ese tipo.

```cpp
#include <type_traits>
#include <iostream>

int main()
{
    std::add_pointer_t<int> *p = (int **)0;

    p = p;  // to quiet "unused" warning
    std::cout << "add_pointer_t<int> == "
        << typeid(*p).name() << std::endl;

    return (0);
}
```

```Output
add_pointer_t<int> == int *
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_pointer (Clase)](../standard-library/remove-pointer-class.md)<br/>
