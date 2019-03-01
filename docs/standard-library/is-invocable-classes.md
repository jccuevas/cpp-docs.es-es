---
title: is_invocable, is_invocable_r, is_nothrow_invocable, clases is_nothrow_invocable_r
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
ms.openlocfilehash: bb5e75a897029ded2e00e491d93d2df41a3e115b
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006866"
---
# <a name="isinvocable-isinvocabler-isnothrowinvocable-isnothrowinvocabler-classes"></a>is_invocable, is_invocable_r, is_nothrow_invocable, clases is_nothrow_invocable_r

Estas plantillas determinan si un tipo se puede invocar con los tipos de argumento especificados. `is_invocable_r` y `is_nothrow_invocable_r` también determinan si el resultado de la invocación es convertible a un tipo específico. `is_nothrow_invocable` y `is_nothrow_invocable_r` también determinan si la invocación se sabe que no producen excepciones. Agregado en C ++ 17.

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

*Callable*<br/>
El tipo que se puede llamar para la consulta.

*Args*<br/>
Para consultar los tipos de argumento.

*Convertibles*<br/>
El tipo de resultado de *Callable* debe ser convertible a.

## <a name="remarks"></a>Comentarios

El `is_invocable` predicado de tipo contiene true si el tipo que se puede llamar *Callable* puede invocarse utilizando los argumentos *Args* en un contexto no evaluado.

El `is_invocable_r` predicado de tipo contiene true si el tipo que se puede llamar *Callable* puede invocarse utilizando los argumentos *Args* en un contexto no evaluado para generar un tipo convertible de resultado en  *Convertible*.

El `is_nothrow_invocable` predicado de tipo contiene true si el tipo que se puede llamar *Callable* puede invocarse utilizando los argumentos *Args* en un contexto no evaluado y que se conoce esta llamada no se inicia una excepción.

El `is_nothrow_invocable_r` predicado de tipo contiene true si el tipo que se puede llamar *Callable* puede invocarse utilizando los argumentos *Args* en un contexto no evaluado para generar un tipo convertible de resultado en  *Convertible*, y que se conoce esta llamada no se inicia una excepción.

Cada uno de los tipos *Convertible*, *Callable*y los tipos en el paquete de parámetros *Args* debe ser un tipo completo, una matriz de límite desconocido o una posiblementecalificadoparacv**void**. En caso contrario, el comportamiento del predicado es indefinido.

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

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[invoke](functional-functions.md#invoke)<br/>
