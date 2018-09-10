---
title: remove_extent (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::remove_extent
dev_langs:
- C++
helpviewer_keywords:
- remove_extent class
- remove_extent
ms.assetid: b9320862-3891-49fc-80bc-571eb2c035cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcd99de00e7cc5bf2689476df03c5d97d65e2be5
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107402"
---
# <a name="removeextent-class"></a>remove_extent (Clase)

Crea un tipo de elemento a partir de un tipo de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct remove_extent;

template <class T>
using remove_extent_t = typename remove_extent<T>::type;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

Una instancia de `remove_extent<T>` contiene un tipo modificado que es `T1` cuando *T* tiene el formato `T1[N]`en caso contrario, *T*.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_extent_t<int> == "
        << typeid(std::remove_extent_t<int>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5]> == "
        << typeid(std::remove_extent_t<int[5]>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5][10]> == "
        << typeid(std::remove_extent_t<int[5][10]>).name()
        << std::endl;
    return (0);
    }
```

```Output
remove_extent_t<int> == int
remove_extent_t<int[5]> == int
remove_extent_t<int[5][10]> == int [10]
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents (Clase)](../standard-library/remove-all-extents-class.md)<br/>
