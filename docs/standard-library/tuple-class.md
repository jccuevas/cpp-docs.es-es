---
title: tupla (Clase)
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 9890a6a9dea1671f14b66897a80f4b49861dff2b
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257109"
---
# <a name="tuple-class"></a>tupla (Clase)

Ajusta una secuencia de elementos de longitud fija.

## <a name="syntax"></a>Sintaxis

```cpp
class tuple {
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
};
```

### <a name="parameters"></a>Parámetros

\ de *TN*
Tipo del enésimo elemento de la tupla.

## <a name="remarks"></a>Observaciones

La plantilla de clase describe un objeto que almacena N objetos de tipos `T1`, `T2`,..., `TN`, respectivamente, donde `0 <= N <= Nmax`. La extensión de una instancia de tupla `tuple<T1, T2, ..., TN>` es el número `N` de sus argumentos de plantilla. El índice del argumento de plantilla `Ti` y del valor almacenado correspondiente de ese tipo es `i - 1`. Por lo tanto, aunque se numeran los tipos de 1 a N en esta documentación, los valores de índice correspondientes van de 0 a N-1.

## <a name="example"></a>Ejemplo

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="op_eq"></a>operador =

Asigna un objeto `tuple`.

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>Parámetros

*UN*\
Tipo del enésimo elemento copiado de la tupla.

\ *derecha*
Tupla de la que se va a copiar.

### <a name="remarks"></a>Observaciones

Los dos primeros operadores miembro asignan los elementos de la *derecha* a los elementos correspondientes de `*this`. El tercer operador miembro asigna `right.first` al elemento en el índice 0 de `*this` y `right.second` al elemento en el índice 1. Los tres operadores miembro devuelven `*this`.

Los operadores miembro restantes son análogos a los anteriores, pero con [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Ejemplo

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="tuple_swap"></a>pasar

Intercambia los elementos de dos tuplas.

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>Parámetros

\ *izquierda*
Tupla cuyos elementos se van a intercambiar con los del *derecho*de la tupla.

\ *derecha*
Tupla cuyos elementos se van a intercambiar con los de la tupla *izquierda*.

### <a name="remarks"></a>Observaciones

La función ejecuta `left.swap(right)`.

## <a name="tuple"></a>organizar

Construye un objeto `tuple`.

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>Parámetros

*UN*\
Tipo del enésimo elemento copiado de la tupla.

\ *derecha*
Tupla de la que se va a copiar.

### <a name="remarks"></a>Observaciones

El primer constructor crea un objeto cuyos elementos se han construido de forma predeterminada.

El segundo constructor crea un objeto cuyos elementos se han creado a partir de los argumentos `P1`, `P2`, ..., `PN` con cada `Pi` inicializando el elemento en el índice `i - 1`.

El tercer y cuarto constructores crean un objeto cuyos elementos se construyen a partir del elemento correspondiente de la *derecha*.

El quinto constructor crea un objeto cuyo elemento en el índice 0 se ha copiado a partir de `right.first` y cuyo elemento en el índice 1 se ha copiado a partir de `right.second`.

Los constructores restantes son análogos a los anteriores, pero con [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Ejemplo

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
{
    Mytuple c0(0, 1, 2, 3);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c1) << " ";
    std::cout << std::get<1>(c1) << " ";
    std::cout << std::get<2>(c1) << " ";
    std::cout << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

    // display contents "x 4"
    std::cout << std::get<0>(c2) << " ";
    std::cout << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c3) << " ";
    std::cout << std::get<1>(c3) << " ";
    std::cout << std::get<2>(c3) << " ";
    std::cout << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

    // display contents "4 5 6 7"
    std::cout << std::get<0>(c4) << " ";
    std::cout << std::get<1>(c4) << " ";
    std::cout << std::get<2>(c4) << " ";
    std::cout << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
0 1 2 3
4 5 6 7
```
