---
title: aligned_storage (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_storage
helpviewer_keywords:
- aligned_storage class
- aligned_storage
ms.assetid: f255e345-1f05-4d07-81e4-017f420839fb
ms.openlocfilehash: 0da2b206cd40f84ac33860c84bbb6a86f6f47fc0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477290"
---
# <a name="alignedstorage-class"></a>aligned_storage (Clase)

Crea un tipo alineado como corresponda.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Len, std::size_t Align>
struct aligned_storage;

template <std::size_t Len, std::size_t Align = alignment_of<max_align_t>::value>
using aligned_storage_t = typename aligned_storage<Len, Align>::type;
```

### <a name="parameters"></a>Parámetros

*Len*<br/>
Tamaño del objeto.

*Alinear*<br/>
Alineación del objeto.

## <a name="remarks"></a>Comentarios

El typedef de miembro de plantilla `type` es un sinónimo de un tipo POD con alineación *alinear* y tamaño *Len*. *Alinear* debe ser igual a `alignment_of<T>::value` para algún tipo `T`, o para la alineación predeterminada.

## <a name="example"></a>Ejemplo

```cpp
#include <type_traits>
#include <iostream>

typedef std::aligned_storage<sizeof (int),
    std::alignment_of<double>::value>::type New_type;
int main()
    {
    std::cout << "alignment_of<int> == "
        << std::alignment_of<int>::value << std::endl;
    std::cout << "aligned to double == "
        << std::alignment_of<New_type>::value << std::endl;

    return (0);
    }

```

```Output
alignment_of<int> == 4
aligned to double == 8
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[alignment_of (Clase)](../standard-library/alignment-of-class.md)<br/>
