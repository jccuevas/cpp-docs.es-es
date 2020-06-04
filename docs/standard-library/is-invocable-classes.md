---
title: is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r clases
ms.date: 02/21/2019
f1_keywords:
- type_traits/std::is_invocable
- type_traits/std::is_invocable_r
- type_traits/std::is_nothrow_invocable
- type_traits/std::is_nothrow_invocable_r
helpviewer_keywords:
- is_invocable class
- is_invocable
- is_invocable_r class
- is_invocable_r
- is_nothrow_invocable class
- is_nothrow_invocable
- is_nothrow_invocable_r class
- is_nothrow_invocable_r
ms.openlocfilehash: 53394a10464e2688953cd1b5703530e2719b7593
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076453"
---
# <a name="is_invocable-is_invocable_r-is_nothrow_invocable-is_nothrow_invocable_r-classes"></a>is_invocable, is_invocable_r, is_nothrow_invocable, is_nothrow_invocable_r clases

Estas plantillas determinan si un tipo se puede invocar con los tipos de argumento especificados. `is_invocable_r` y `is_nothrow_invocable_r` también determinan si el resultado de la invocación se puede convertir en un tipo específico. `is_nothrow_invocable` y `is_nothrow_invocable_r` también determinan si se sabe que la invocación no inicia excepciones. Agregado en C++ 17.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Callable, class... Args>
struct is_invocable;

template <class Convertible, class Callable, class... Args>
struct is_invocable_r;

template <class Callable, class... Args>
struct is_nothrow_invocable;

template <class Convertible, class Callable, class... Args>
struct is_nothrow_invocable_r;

// Helper templates
template <class Callable, class... Args>
inline constexpr bool is_invocable_v =
    std::is_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_invocable_r_v =
    std::is_invocable_r<Convertible, Callable, Args...>::value;

template <class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_v =
    std::is_nothrow_invocable<Callable, Args...>::value;

template <class Convertible, class Callable, class... Args>
inline constexpr bool is_nothrow_invocable_r_v =
    std::is_nothrow_invocable_r<Convertible, Callable, Args...>::value;
```

### <a name="parameters"></a>Parámetros

\ *invocable*
El tipo que se puede llamar para la consulta.

\ *args*
Los tipos de argumento que se van a consultar.

\ *convertible*
El tipo al que se *puede llamar* se debe poder convertir a.

## <a name="remarks"></a>Observaciones

El predicado de tipo `is_invocable` contiene true si se puede invocar el tipo al que se *puede llamar mediante* los *argumentos arguments* en un contexto no evaluado.

El predicado de tipo `is_invocable_r` es true si se puede invocar el tipo al que se *puede llamar mediante* los *argumentos arguments* en un contexto no evaluado para generar un tipo de resultado convertible en *convertible*.

El predicado de tipo `is_nothrow_invocable` es true si se puede invocar el tipo al que se *puede llamar mediante* los *argumentos arguments* en un contexto no evaluado, y se sabe que dicha llamada no produce una excepción.

El predicado de tipo `is_nothrow_invocable_r` es true si se puede invocar el tipo al que se *puede llamar mediante* los *argumentos arguments* en un contexto no evaluado para generar un tipo de resultado que se pueda convertir en *convertible*y que se sepa que dicha llamada no produce una excepción.

Cada uno de los tipos *convertibles*, *Invocables*y los tipos en el paquete de parámetros *args* debe ser un tipo completo, una matriz de enlace desconocido o un **vacío**posiblemente calificado con la VC. De lo contrario, el comportamiento del predicado es undefined.

## <a name="example"></a>Ejemplo

```cpp
// std__type_traits__is_invocable.cpp
// compile using: cl /EHsc /std:c++17 std__type_traits__is_invocable.cpp
#include <type_traits>

auto test1(int) noexcept -> int (*)()
{
    return nullptr;
}

auto test2(int) -> int (*)()
{
    return nullptr;
}

int main()
{
    static_assert( std::is_invocable<decltype(test1), short>::value );

    static_assert( std::is_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_invocable_r<long(*)(), decltype(test1), int>::value ); // fails

    static_assert( std::is_nothrow_invocable<decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable<decltype(test2), int>::value ); // fails

    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test1), int>::value );
    static_assert( std::is_nothrow_invocable_r<int(*)(), decltype(test2), int>::value ); // fails
}
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits >

**Espacio de nombres:** std

## <a name="see-also"></a>Consulte también

[<type_traits>](../standard-library/type-traits.md)\
[invoke](functional-functions.md#invoke)
