---
title: tuple_size (Clase);
ms.date: 11/04/2016
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
ms.openlocfilehash: 361545bee020d6c3624d1d45743abcb9c2b4ac85
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688857"
---
# <a name="tuple_size-class"></a>tuple_size (Clase);

Informa el número de elementos que contiene una `tuple` .

## <a name="syntax"></a>Sintaxis

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

```cpp
template <class T> inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```

### <a name="parameters"></a>Parámetros

@No__t_1 de *tupla*
El tipo de tupla.

@No__t_1 *Elem*
El tipo de los elementos de la matriz.

*Tamaño* \
Se refiere al tamaño de la matriz.

@No__t_1 *T1*
El tipo del primer miembro del par.

@No__t_1 *T2*
El tipo del segundo miembro del par.

*Types*\ (Tipos [Referencia de C#])
Los tipos de los elementos de tupla.

## <a name="remarks"></a>Comentarios

La plantilla de clase tiene un miembro `value` que es una expresión constante entera cuyo valor es la extensión de la *tupla*de tipo de tupla.

La especialización de plantilla para matrices tiene un miembro `value` que es una expresión constante entera cuyo valor es *size*, que es el tamaño de la matriz.

La especialización de plantilla para pares tiene un miembro `value` que es una expresión constante entera cuyo valor es 2.

## <a name="example"></a>Ejemplo

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents "0 1 2 3"
    cout << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size "4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
0 1.5 2 3.7
4
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<tuple>

**Encabezado:** \<array> (para la especialización de matrices)

**Encabezado:** \<utility> (para la especialización de pares)

**Espacio de nombres:** std
