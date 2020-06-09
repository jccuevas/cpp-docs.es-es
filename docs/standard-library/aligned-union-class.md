---
title: Clase aligned_union
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: ae6ef629535238b9406216afd9f680a5c1e1afe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623799"
---
# <a name="aligned_union-class"></a>Clase aligned_union

Proporciona un tipo POD lo suficientemente grande y convenientemente alineado para almacenar un tipo de unión y el tamaño necesario.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Len, class... Types>
struct aligned_union;

template <std::size_t Len, class... Types>
using aligned_union_t = typename aligned_union<Len, Types...>::type;
```

### <a name="parameters"></a>Parámetros

*Terminado*\
El valor de alineación para el tipo más grande de la unión.

*Distintos*\
Los distintos tipos de la unión subyacente.

## <a name="remarks"></a>Observaciones

Use la plantilla de clase para obtener la alineación y el tamaño necesarios para almacenar una Unión en almacenamiento no inicializado. El typedef de miembro `type` nombra un tipo Pod adecuado para el almacenamiento de cualquier tipo enumerado en *tipos*; el tamaño mínimo es *Len*. El miembro estático `alignment_value` de tipo `std::size_t` contiene la alineación más estricta necesaria para todos los tipos enumerados en *tipos*.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo usar `aligned_union` para asignar un búfer de pila alineada para colocar una unión.

```cpp
// std__type_traits__aligned_union.cpp
#include <iostream>
#include <type_traits>

union U_type
{
    int i;
    float f;
    double d;
    U_type(float e) : f(e) {}
};

typedef std::aligned_union<16, int, float, double>::type aligned_U_type;

int main()
{
    // allocate memory for a U_type aligned on a 16-byte boundary
    aligned_U_type au;
    // do placement new in the aligned memory on the stack
    U_type* u = new (&au) U_type(1.0f);
    if (nullptr != u)
    {
        std::cout << "value of u->i is " << u->i << std::endl;
        // must clean up placement objects manually!
        u->~U_type();
    }
}
```

```Output
value of u->i is 1065353216
```

## <a name="requirements"></a>Requisitos

**Encabezado:**\<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](type-traits.md)\
[alignment_of (clase)](alignment-of-class.md)
