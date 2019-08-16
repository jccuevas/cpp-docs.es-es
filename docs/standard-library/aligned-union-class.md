---
title: Clase aligned_union
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::aligned_union
helpviewer_keywords:
- aligned_union
ms.assetid: 9931a44d-3a67-4f29-a0f6-d47a7cf560ac
ms.openlocfilehash: b9ffb4aff4d4d5667ab8d626ea13a21da94ca0c1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456462"
---
# <a name="alignedunion-class"></a>Clase aligned_union

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

*Types*\ (Tipos [Referencia de C#])
Los distintos tipos de la unión subyacente.

## <a name="remarks"></a>Comentarios

Use la clase de plantilla para obtener la alineación y el tamaño necesarios para almacenar una unión en el almacenamiento sin inicializar. El typedef `type` de miembro nombra un tipo Pod adecuado para el almacenamiento de cualquier tipo enumerado en *tipos*; el tamaño mínimo es *Len*. El miembro `alignment_value` estático de tipo `std::size_t` contiene la alineación más estricta necesaria para todos los tipos enumerados en *tipos*.

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

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[alignment_of (Clase)](../standard-library/alignment-of-class.md)
