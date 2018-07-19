---
title: remove_pointer (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::remove_pointer
dev_langs:
- C++
helpviewer_keywords:
- remove_pointer class
- remove_pointer
ms.assetid: 2cd4e417-32fb-4f53-bd16-4e8a98240832
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9c8ddf5941394a8979832a753ed73cfda5f0876
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959129"
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

*T* el tipo de modificación.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_pointer<T>` contiene un tipo modificado que es `T1` cuando *T* tiene el formato `T1*`, `T1* const`, `T1* volatile`, o `T1* const volatile`en caso contrario, *T*.

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

[<type_traits>](../standard-library/type-traits.md)<br/>
[add_pointer (Clase)](../standard-library/add-pointer-class.md)<br/>
