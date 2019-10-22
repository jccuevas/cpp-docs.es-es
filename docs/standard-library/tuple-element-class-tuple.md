---
title: tuple_element (Clase)
ms.date: 11/04/2016
f1_keywords:
- utility/std::tuple_element
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
ms.openlocfilehash: 21efed39fdaabe0f95f83e9dc5cdfcc508a147c5
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684461"
---
# <a name="tuple_element-class"></a>tuple_element (Clase)

Contiene un elemento `tuple` . Las especializaciones contienen elementos `array` y elementos `pair`.

## <a name="syntax"></a>Sintaxis

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>Parámetros

*Índice* \
Índice del elemento designado.

@No__t_1 de *tupla*
El tipo de tupla.

@No__t_1 *Elem*
El tipo de un elemento de matriz.

*Tamaño* \
Se refiere al tamaño de la matriz.

@No__t_1 *T1*
Tipo del primer elemento de un par.

@No__t_1 *T2*
El tipo del segundo elemento de un par.

## <a name="remarks"></a>Comentarios

La plantilla de clase `tuple_element` tiene una definición de tipos anidada `type` que es un sinónimo del tipo en el *Índice* de índice de la *tupla*de tipo de tupla.

La definición de tipo `tuple_element_t` es un alias adecuado para `tuple_element<Index, Tuple>::type`.

La especialización de plantilla de clase para matrices proporciona una interfaz a un `array` como una tupla de `Size` elementos, cada uno de los cuales tiene el mismo tipo. Cada especialización tiene una definición de tipo anidada `type` que es un sinónimo del tipo del elemento *index* del `array`, con cualquier calificación const-volatile conservada.

Las especializaciones de plantilla para tipos `pair` tienen una definición de tipo de miembro único, `type`, que es un sinónimo del tipo del elemento en la posición especificada en el par, con cualquier calificador const o volatile conservado. La definición de tipo `tuple_element_t` es un alias adecuado para `tuple_element<N, pair<T1, T2>>::type`.

Utilice la [función get &lt;utility &gt;](../standard-library/utility-functions.md#get) para devolver el elemento en una posición especificada o de un tipo especificado.

## <a name="example"></a>Ejemplo

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>Ejemplo

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << e << " ";
    }
    cout << endl;

    // display first element "0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << val << endl;
}
```

```Output
0 1 2 3
0
```

## <a name="example"></a>Ejemplo

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents "0 1"
    cout << get<0>(c0) << " ";
    cout << get<1>(c0) << endl;

    // display first element "0 " by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << val << " ";

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << val2 << endl;
}
```

```Output
0 1.333
0 1.333
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<tuple>

**Encabezado:** \<array> (para la especialización de matrices)

**Encabezado:** \<utility > (para especializaciones de pares)

**Espacio de nombres:** std
