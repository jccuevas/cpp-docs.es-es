---
title: extent (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::extent
dev_langs:
- C++
helpviewer_keywords:
- extent class
- extent
ms.assetid: 6d16263d-90b2-4330-9ec7-b59ed898792d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fb721b23f473c59051e72edc969e5de38f1c984
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843254"
---
# <a name="extent-class"></a>extent (Clase)

Obtiene una dimensión de matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty, unsigned I = 0>
struct extent;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

`I` La matriz se enlaza a la consulta.

## <a name="remarks"></a>Comentarios

Si `Ty` es un tipo de matriz con `I` dimensiones como mínimo, la consulta de tipo contiene el número de elementos de la dimensión que especifica `I`. Si `Ty` no es un tipo de matriz o el rango es menor que `I`, o si `I` es cero y `Ty` es de tipo "matriz de límite desconocido de `U`", la consulta de tipo contiene el valor 0.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__extent.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "extent 0 == "
        << std::extent<int[5][10]>::value << std::endl;
    std::cout << "extent 1 == "
        << std::extent<int[5][10], 1>::value << std::endl;

    return (0);
    }

```

```Output
extent 0 == 5
extent 1 == 10
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents (Clase)](../standard-library/remove-all-extents-class.md)<br/>
[remove_extent (Clase)](../standard-library/remove-extent-class.md)<br/>
