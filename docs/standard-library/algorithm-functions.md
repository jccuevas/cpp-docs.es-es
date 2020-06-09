---
title: Funciones &lt;algorithm&gt;
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: c8c550be87eacf81fab994239e07ed2358fad39b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617663"
---
# <a name="ltalgorithmgt-functions"></a>Funciones &lt;algorithm&gt;

## <a name="adjacent_find"></a><a name="adjacent_find"></a>adjacent_find

Busca dos elementos adyacentes que son iguales o cumplen una condición especificada.

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*pronostica*\
El predicado binario que da la condición que deben cumplir los valores de los elementos adyacentes en el intervalo en el que se buscará.

### <a name="return-value"></a>Valor devuelto

Un iterador hacia delante al primero de los elementos adyacentes que son iguales entre sí (en la primera versión) o que satisfacen la condición dada por el predicado binario (en la segunda versión), siempre que se encuentre un par de elementos. De lo contrario, se devuelve un iterador que apunta a *Last* .

### <a name="remarks"></a>Observaciones

El algoritmo `adjacent_find` es un algoritmo de secuencia no cambiante. El intervalo en el que se buscará debe ser válido: todos los punteros deben poder desreferenciarse y se debe poder acceder a la última posición desde la primera con incrementos. La complejidad temporal del algoritmo es lineal en el número de elementos incluidos en el intervalo.

El `operator==` utilizado para determinar la coincidencia entre los elementos debe imponer una relación de equivalencia entre sus operandos.

### <a name="example"></a>Ejemplo

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return elem1 * 2 == elem2;
}

int main()
{
    using namespace std;
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

    L.push_back( 50 );
    L.push_back( 40 );
    L.push_back( 10 );
    L.push_back( 20 );
    L.push_back( 20 );

    cout << "L = ( " ;
    for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
        cout << *Iter << " ";
    cout << ")" << endl;

    result1 = adjacent_find( L.begin( ), L.end( ) );
    if ( result1 == L.end( ) )
        cout << "There are not two adjacent elements that are equal."
            << endl;
    else
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a><a name="all_of"></a>all_of

Devuelve **verdadero** cuando una condición está presente en cada elemento del intervalo especificado.

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica dónde comenzar a comprobar una condición. El iterador marca el comienzo de un intervalo de elementos.

*guardado*\
Iterador de entrada que indica el final del intervalo de elementos en el que se va a comprobar una condición.

*pronostica*\
Condición que se va a probar. Es un objeto de función de predicado definido por el usuario que define la condición que debe cumplir el elemento que se está comprobando. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si la condición se detecta en cada elemento del intervalo indicado o si el intervalo está vacío y **false** en caso contrario.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve **true** solo si, para cada del `N` intervalo `[0, last - first)` , el predicado `pred(*(first + N))` es **true**.

### <a name="example"></a>Ejemplo

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a><a name="any_of"></a>any_of

Devuelve **verdadero** cuando una condición está presente al menos una vez en el intervalo de elementos especificado.

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica dónde comenzar a comprobar una condición en un intervalo de elementos.

*guardado*\
Iterador de entrada que indica el final del intervalo de elementos en el que se va a comprobar una condición.

*pronostica*\
Condición que se va a probar. La proporciona un objeto de función de predicado definido por el usuario. El predicado define la condición que debe cumplir el elemento que se está probando. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si la condición se detecta al menos una vez en el intervalo indicado, **false** si la condición nunca se detecta.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve **true** solo si, para algunos `N` en el intervalo

`[0, last - first)`, el predicado `pred(*(first + N))` es True.

### <a name="example"></a>Ejemplo

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a><a name="binary_search"></a>binary_search

Comprueba si hay un elemento en un intervalo ordenado que sea igual a un valor especificado o equivalente a este del modo especificado por un predicado binario.

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*valor*\
Valor que debe coincidir con el valor del elemento o que debe cumplir la condición con el valor del elemento especificado por el predicado binario.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

**true** si un elemento se encuentra en el intervalo igual o equivalente al valor especificado; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

El intervalo de origen ordenado al que se hace referencia debe ser válido; todos los punteros deben poder desreferenciarse y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo ordenado debe estar organizado como condición previa a la aplicación del algoritmo `binary_search` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

`binary_search` no modifica los intervalos de origen.

Los tipos de valor de los iteradores hacia delante tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes.

La complejidad del algoritmo es logarítmica para los iteradores de acceso aleatorio y lineal en caso contrario, con el número de pasos proporcionales a ( `last`  -  `first` ).

### <a name="example"></a>Ejemplo

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list<int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a><a name="clamp"></a>Sujet

Compara un valor con un límite superior e inferior, y devuelve una referencia al valor si está entre los límites, o una referencia al límite superior o inferior si el valor está por encima o por debajo de ellos, respectivamente.

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*valor*\
Valor que se va a comparar con el nivel *superior* e *inferior*.

*inferiores*\
Límite inferior de valores al que se va a fijar el *valor* .

*esquina superior*\
Límite superior de valores a los que se va a fijar el *valor* .

*pronostica*\
Predicado que se usa para comparar el *valor* con el *inferior* o el *superior*. Un predicado de comparación toma dos argumentos y devuelve **true** si el primero es en cierto sentido menor que el segundo; de lo contrario, es **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a *Lower* si `value < lower` , o una referencia a *Upper* si `upper < value` . De lo contrario, devuelve una referencia a *Value*.

### <a name="remarks"></a>Observaciones

El comportamiento es indefinido si *Upper* es *menor que el menor.*

## <a name="copy"></a><a name="copy"></a>copiar

Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia delante.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que direcciona la posición del primer elemento del intervalo de origen.

*guardado*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento del intervalo de origen.

*destBeg*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino, es decir, el iterador direcciona `result` + (*último*  -  *primero*).

### <a name="remarks"></a>Observaciones

El intervalo de origen debe ser válido y debe haber suficiente espacio en el destino para contener todos los elementos que se van a copiar.

Dado que el algoritmo copia los elementos de origen por orden a partir del primer elemento, el intervalo de destino puede superponerse al intervalo de origen siempre que la *última* posición del intervalo de origen no esté contenida en el intervalo de destino. `copy`se puede usar para desplazar elementos hacia la izquierda pero no a la derecha, a menos que no haya superposición entre los intervalos de origen y de destino. Para desplazar a la derecha cualquier número de posiciones, use el algoritmo [copy_backward](algorithm-functions.md#copy_backward).

El algoritmo `copy` solo modifica los valores a los que apuntan los iteradores, asignando nuevos valores a los elementos del intervalo de destino. No se puede utilizar para crear elementos nuevos y no puede insertar elementos en un contenedor vacío directamente.

### <a name="example"></a>Ejemplo

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ii++ )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy the first 3 elements of v1 into the middle of v2
    copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the left
    copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a><a name="copy_backward"></a>copy_backward

Asigna los valores de elementos de un intervalo de origen a un intervalo de destino, recorriendo en iteración la secuencia de origen de elementos y asignándoles nuevas posiciones en una dirección hacia atrás.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador bidireccional que direcciona la posición del primer elemento del intervalo de origen.

*guardado*\
Iterador bidireccional que direcciona la posición situada un elemento más allá del último elemento del intervalo de origen.

*desofertas*\
Iterador bidireccional que direcciona la posición de un elemento más allá del último elemento del intervalo de destino.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino, es decir, el iterador se *dirige a la* promediación: (*último*  -  *primero*).

### <a name="remarks"></a>Observaciones

El intervalo de origen debe ser válido y debe haber suficiente espacio en el destino para contener todos los elementos que se van a copiar.

El `copy_backward` algoritmo impone requisitos más estrictos que el `copy` algoritmo. Tanto sus iteradores de entrada como de salida deben ser bidireccionales.

Los algoritmos `copy_backward` y [move_backward](algorithm-functions.md#move_backward) son los únicos algoritmos de la Biblioteca estándar de C++ que designan el intervalo de salida con un iterador que apunta al final del intervalo de destino.

Dado que el algoritmo copia los elementos de origen por orden a partir del último elemento, el intervalo de destino puede superponerse al intervalo de origen siempre que la *primera* posición del intervalo de origen no esté contenida en el intervalo de destino. Se puede utilizar `copy_backward` para desplazar elementos hacia la derecha pero no hacia la izquierda, a menos que no haya superposición entre los intervalos de origen y de destino. Para desplazar a la izquierda cualquier número de posiciones, use el algoritmo [copy](algorithm-functions.md#copy).

El algoritmo `copy_backward` solo modifica los valores a los que apuntan los iteradores, asignando nuevos valores a los elementos del intervalo de destino. No se puede utilizar para crear elementos nuevos y no puede insertar elementos en un contenedor vacío directamente.

### <a name="example"></a>Ejemplo

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; ++i )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ++ii )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy_backward the first 3 elements of v1 into the middle of v2
    copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the right
    copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a><a name="copy_if"></a>copy_if

En un intervalo de elementos, copia los elementos que son **true** para la condición especificada.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica el inicio de un intervalo en el que se va a comprobar la condición.

*guardado*\
Iterador de entrada que indica el final del intervalo.

*dest*\
Iterador de salida que indica el destino de los elementos copiados.

*pronostica*\
Condición con la que se comprueba cada elemento del intervalo. La proporciona un objeto de función de predicado definido por el usuario. Un predicado unario toma un argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que es igual a *dest* incrementada una vez para cada elemento que cumple la condición. En otras palabras, el valor devuelto menos *dest* es igual al número de elementos copiados.

### <a name="remarks"></a>Observaciones

La función de plantilla evalúa

`if (pred(*first + N)) * dest++ = *(first + N))`

una vez por cada `N` del intervalo `[0, last - first)`, con los valores de `N` incrementados de forma estricta empezando por el valor inferior. Si *dest* y *First* designan regiones de almacenamiento, *dest* no debe estar en el intervalo `[ first, last )` .

### <a name="example"></a>Ejemplo

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a><a name="copy_n"></a>copy_n

Copia un número especificado de elementos.

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica de dónde se copiarán los elementos.

*contabiliza*\
Tipo entero con o sin signo que especifica el número de elementos que se copiarán.

*dest*\
Iterador de salida que indica adónde se copiarán los elementos.

### <a name="return-value"></a>Valor devuelto

Devuelve un iterador de salida de la ubicación a la que se copiaron los elementos. Es el mismo que el valor devuelto del parámetro *dest* .

### <a name="remarks"></a>Observaciones

La función de plantilla evalúa `*(dest + N) = *(first + N))` una vez por cada `N` del intervalo `[0, count)`, con los valores de `N` incrementados de forma estricta empezando por el valor inferior. Después, devuelve `dest + N`. Si *dest* y *First* designan regiones de almacenamiento, *dest* no debe estar en el intervalo `[first, last)` .

### <a name="example"></a>Ejemplo

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a><a name="count"></a>contabiliza

Devuelve el número de elementos de un intervalo cuyos valores coinciden con un valor especificado.

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que dirige a la posición del primer elemento del intervalo que se va a atravesar.

*guardado*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo que se va a atravesar.

*valor*\
Valor de los elementos que se van a contar.

### <a name="return-value"></a>Valor devuelto

El tipo de diferencia de `InputIterator` que cuenta el número de elementos del intervalo [*First*, *Last*) que tienen *valor*de valor.

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

Este algoritmo se generaliza para contar los elementos que satisfacen cualquier predicado con la función de plantilla [count_if](algorithm-functions.md#count_if).

### <a name="example"></a>Ejemplo

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a><a name="count_if"></a>count_if

Devuelve el número de elementos de un intervalo cuyos valores satisfacen una condición especificada.

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que debe cumplir el elemento para que se cuente. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Número de elementos que satisfacen la condición especificada por el predicado.

### <a name="remarks"></a>Observaciones

Esta función de plantilla es una generalización del algoritmo [count](algorithm-functions.md#count) donde el predicado "es igual a un valor específico" se sustituye por cualquier predicado.

### <a name="example"></a>Ejemplo

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a><a name="equal"></a>sea

Compara dos intervalos elemento a elemento para ver si son iguales o equivalentes según lo especificado por un predicado binario.

Use `std::equal` al comparar elementos de diferentes tipos de contenedor (por ejemplo, `vector` y `list`) o al comparar diferentes tipos de elemento, o cuando sea necesario comparar subintervalos de contenedores. Por otra parte, al comparar elementos de igual tipo en el mismo tipo de contenedor, use `operator==` no miembro que se proporciona para cada contenedor.

Use las sobrecargas de dos intervalos en código C ++ 14 porque las sobrecargas que toman un único iterador para el segundo intervalo no detectan las diferencias si el segundo intervalo es más largo que el primero y esto provoca un comportamiento indefinido si el segundo intervalo es más corto que el primero.

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Un iterador de entrada que dirige a la posición del primer elemento en el primer intervalo que se va a probar.

*last1*\
Un iterador de entrada que dirige a la posición situada una posición después del último elemento en el primer intervalo que se va a probar.

*first2*\
Un iterador de entrada que dirige a la posición del primer elemento en el segundo intervalo que se va a probar.

*last2*\
Un iterador de entrada que dirige a la posición situada una posición después del último elemento en el segundo intervalo que se va a probar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

**True** únicamente si los intervalos son idénticos o equivalentes en el predicado binario cuando se compara elemento a elemento; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

El intervalo en el que se va a buscar debe ser válido: todos los iteradores deben poder desreferenciarse y se debe poder acceder a la última posición desde la primera con incrementos.

Si los dos intervalos tienen la misma duración, la complejidad temporal del algoritmo es lineal en el número de elementos incluidos en el intervalo. En caso contrario, la función devuelve el **valor false**inmediatamente.

No es necesario que `operator==` o el predicado definido por el usuario impongan una relación de equivalencia que sea simétrica, reflexiva y transitiva entre sus operandos.

### <a name="example"></a>Ejemplo

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}
```

## <a name="equal_range"></a><a name="equal_range"></a>equal_range

En un intervalo ordenado, busca el subintervalo en el que todos los elementos son equivalentes a un valor determinado.

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*valor*\
Valor que se va a buscar en el intervalo ordenado.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="return-value"></a>Valor devuelto

Par de iteradores hacia delante que especifican un subintervalo, incluido en el intervalo buscado, en el que todos los elementos son equivalentes al *valor* en el sentido definido por el predicado binario usado ( *Pred* o el valor predeterminado, menor que).

Si ningún elemento del intervalo es equivalente a *Value*, los iteradores hacia delante del par devuelto son iguales y especifican el punto en el que se podría insertar el *valor* sin alterar el orden del intervalo.

### <a name="remarks"></a>Observaciones

El primer iterador del par devuelto por el algoritmo es [lower_bound](algorithm-functions.md#lower_bound) y el segundo es [upper_bound](algorithm-functions.md#upper_bound).

El intervalo debe estar ordenado según el predicado proporcionado para `equal_range`. Por ejemplo, si va a usar el predicado mayor que, el intervalo debe ordenarse en orden descendente.

Los elementos del subintervalo posiblemente vacío definido por el par de iteradores devueltos por serán `equal_range` equivalentes a *Value* en el sentido definido por el predicado utilizado.

La complejidad del algoritmo es logarítmica para los iteradores de acceso aleatorio y lineal en caso contrario, con el número de pasos proporcionales a (*último*  -  *primero*).

### <a name="example"></a>Ejemplo

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}
```

## <a name="fill"></a><a name="fill"></a>relleno

Asigna el mismo valor nuevo a cada elemento de un intervalo especificado.

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo que se va a atravesar.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo que se va a atravesar.

*valor*\
Valor que se va a asignar a los elementos del intervalo [*First*, *Last*).

### <a name="remarks"></a>Observaciones

El intervalo de destino debe ser válido; todos los punteros deben poder desreferenciarse y se debe poder acceder a la última posición desde la primera con incrementos. La complejidad es lineal con el tamaño del intervalo.

### <a name="example"></a>Ejemplo

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Fill the last 5 positions with a value of 2
    fill( v1.begin( ) + 5, v1.end( ), 2 );

    cout << "Modified v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a><a name="fill_n"></a>fill_n

Asigna un nuevo valor a un número especificado de elementos de un intervalo a partir de un elemento determinado.

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de salida que dirige a la posición del primer elemento del intervalo al que se va a asignar el *valor*de valor.

*contabiliza*\
Tipo entero con o sin signo que especifica el número de elementos que se van a asignar al valor.

*valor*\
Valor que se va a asignar a los elementos del intervalo [*First*, *First + Count*).

### <a name="return-value"></a>Valor devuelto

Un iterador al elemento que sigue al último elemento rellenado si *count* > cero; de lo contrario, el primer elemento.

### <a name="remarks"></a>Observaciones

El intervalo de destino debe ser válido; todos los punteros deben poder desreferenciarse y se debe poder acceder a la última posición desde la primera con incrementos. La complejidad es lineal con el tamaño del intervalo.

### <a name="example"></a>Ejemplo

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}
```

## <a name="find"></a><a name="find"></a>localización

Busca la posición de la primera aparición de un elemento en un intervalo que tiene un valor especificado.

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que direcciona la posición del primer elemento del intervalo en el que se va a buscar el valor especificado.

*guardado*\
Iterador de entrada que direcciona la posición de un elemento más allá del último elemento del intervalo en el que se va a buscar el valor especificado.

*valor*\
Valor que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Iterador de entrada que direcciona la primera aparición del valor especificado en el intervalo en el que se está buscando. Si no se encuentra ningún elemento con un valor equivalente, devuelve *Last*.

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

Para obtener un ejemplo de código con `find()`, vea [find_if](algorithm-functions.md#find_if).

## <a name="find_end"></a><a name="find_end"></a>find_end

Busca en un intervalo la última subsecuencia que es idéntica a una secuencia especificada o que es equivalente según lo especificado por un predicado binario.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*first1*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*last1*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*first2*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*last2*\
Iterador hacia delante que dirige a la posición del último elemento del intervalo en el que se buscará.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la posición del primer elemento de la última subsecuencia dentro de [first1, last1) que coincide con la secuencia especificada [first2, last2).

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

Los intervalos a los que se hace referencia deben ser válidos: todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, se debe poder acceder a la última posición desde la primera con incrementos.

### <a name="example"></a>Ejemplo

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for a match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent to those\n in v2 under the binary "
            << "predicate twice and that begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a><a name="find_first_of"></a>find_first_of

Busca la primera aparición de cualquiera de varios valores dentro de un intervalo de destino o la primera aparición de cualquiera de varios elementos que son equivalentes según lo especificado por un predicado binario en un conjunto especificado de los elementos.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*first1*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*last1*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*first2*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo con el que se establecerá la coincidencia.

*last2*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo con el que se establecerá la coincidencia.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la posición del primer elemento de la primera subsecuencia que coincide con la secuencia especificada o que es equivalente en un sentido especificado por un predicado binario.

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

Los intervalos a los que se hace referencia deben ser válidos: todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, se debe poder acceder a la última posición desde la primera con incrementos.

### <a name="example"></a>Ejemplo

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 3 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a><a name="find_if"></a>find_if

Busca la posición de la primera aparición de un elemento en un intervalo que cumple una condición especificada.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de entrada que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*pronostica*\
Objeto de función de predicado definido por el usuario o [expresión lambda](../cpp/lambda-expressions-in-cpp.md) que define la condición que debe cumplir el elemento que se va a buscar. Un predicado unario toma un solo argumento y devuelve **true** si se cumple, o **false** si no se cumple. La firma de *Pred* debe ser efectiva `bool pred(const T& arg);` , donde `T` es un tipo al que se `InputIterator` puede convertir implícitamente al desreferenciarse. La palabra clave **const** solo se muestra para ilustrar que el objeto de función o la expresión lambda no deben modificar el argumento.

### <a name="return-value"></a>Valor devuelto

Iterador de entrada que hace referencia al primer elemento del intervalo que cumple la condición especificada por el predicado (el predicado devuelve **true**). Si no se encuentra ningún elemento que cumpla el predicado, devuelve *Last*.

### <a name="remarks"></a>Observaciones

Esta función de plantilla es una generalización del algoritmo [find](algorithm-functions.md#find) donde el predicado "es igual a un valor específico" se sustituye por cualquier predicado. Para ver información sobre la operación lógica opuesta (buscar el primer elemento que no cumple el predicado), vea [find_if_not](algorithm-functions.md#find_if_not).

### <a name="example"></a>Ejemplo

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}
```

## <a name="find_if_not"></a><a name="find_if_not"></a>find_if_not

Devuelve el primer elemento del intervalo indicado que no satisface una condición.

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de entrada que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*pronostica*\
Objeto de función de predicado definido por el usuario o [expresión lambda](../cpp/lambda-expressions-in-cpp.md) que define la condición que no debe cumplir el elemento que se va a buscar. Un predicado unario toma un solo argumento y devuelve **true** si se cumple, o **false** si no se cumple. La firma de *Pred* debe ser efectiva `bool pred(const T& arg);` , donde `T` es un tipo al que se `InputIterator` puede convertir implícitamente al desreferenciarse. La palabra clave **const** solo se muestra para ilustrar que el objeto de función o la expresión lambda no deben modificar el argumento.

### <a name="return-value"></a>Valor devuelto

Iterador de entrada que hace referencia al primer elemento del intervalo que no cumple la condición especificada por el predicado (el predicado devuelve **false**). Si todos los elementos cumplen el predicado (el predicado da como resultado **true** para cada elemento), devuelve *Last*.

### <a name="remarks"></a>Observaciones

Esta función de plantilla es una generalización del algoritmo [find](algorithm-functions.md#find) donde el predicado "es igual a un valor específico" se sustituye por cualquier predicado. Para ver información sobre la operación lógica opuesta (buscar el primer elemento que sí cumple el predicado), vea [find_if](algorithm-functions.md#find_if).

Para obtener un ejemplo de código que se adapta fácilmente a `find_if_not()`, vea [find_if](algorithm-functions.md#find_if).

## <a name="for_each"></a><a name="for_each"></a>for_each

Aplica un objeto de función especificado a cada elemento en un orden hacia delante dentro de un intervalo y devuelve el objeto de función.

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de entrada que dirige a la posición del primer elemento del intervalo en el que se va a operar.

*guardado*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo en el que se va a operar.

*funciones*\
Objeto de función definido por el usuario que se aplica a cada elemento del intervalo.

### <a name="return-value"></a>Valor devuelto

Copia del objeto de función una vez aplicado a todos los elementos del intervalo.

### <a name="remarks"></a>Observaciones

El algoritmo `for_each` es muy flexible, lo que permite la modificación de cada elemento de un intervalo de formas distintas especificadas por el usuario. Las funciones de plantilla se pueden volver a usar en un formato modificado si se pasan parámetros diferentes. Las funciones definidas por el usuario pueden acumular información dentro de un estado interno que el algoritmo puede devolver después de procesar todos los elementos del intervalo.

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal con, como máximo, las comparaciones (*último*  -  *primero*).

### <a name="example"></a>Ejemplo

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) {
    }

    // The function call for the element to be multiplied
    void operator( ) ( Type& elem ) const
    {
        elem *= Factor;
    }
};

// The function object to determine the average
class Average
{
private:
    long num;      // The number of elements
    long sum;      // The sum of the elements
public:
    // Constructor initializes the value to multiply by
    Average( ) : num ( 0 ) , sum ( 0 )
    {
    }

    // The function call to process the next elment
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The local state of a function object can accumulate
    // information about a sequence of actions that the
    // return value can make available, here the Average
    double avemod2 = for_each ( v1.begin( ), v1.end( ),
        Average( ) );
    cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
            << avemod2 << "." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a><a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a><a name="generate"></a>crear

Asigna los valores generados por un objeto de función a cada elemento de un intervalo.

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo al que se van a asignar valores.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo al que se van a asignar valores.

*Group*\
Objeto de función al que se llama sin argumentos que se usa para generar los valores que se van a asignar a cada uno de los elementos del intervalo.

### <a name="remarks"></a>Observaciones

El objeto de función se invoca por cada elemento en el intervalo y no es necesario que el valor devuelto sea el mismo cada vez que se llama. Así, por ejemplo, puede leer de un archivo o hacer referencia a un estado local y modificarlo. El tipo de resultado del generador debe poder convertirse en el tipo de valor de los iteradores hacia delante del intervalo.

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal, y las llamadas exactamente ( `last`  -  `first` ) al generador son necesarias.

### <a name="example"></a>Ejemplo

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
    using namespace std;

    // Assigning random values to vector integer elements
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

    generate ( v1.begin( ), v1.end( ), rand );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Assigning random values to deque integer elements
    generate ( deq1.begin( ), deq1.end( ), rand );

    cout << "Deque deq1 is ( " ;
    for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
        cout << *d1_Iter << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a><a name="generate_n"></a>generate_n

Asigna los valores generados por un objeto de función a un número especificado de elementos de un intervalo y vuelve a la posición situada una más allá del último valor asignado.

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de salida que direcciona la posición del primer elemento del intervalo al que se van a asignar valores.

*contabiliza*\
Tipo de entero con signo o sin signo que especifica el número de elementos a los que la función de generador va a asignar un valor.

*Group*\
Objeto de función al que se llama sin argumentos que se usa para generar los valores que se van a asignar a cada uno de los elementos del intervalo.

### <a name="remarks"></a>Observaciones

El objeto de función se invoca por cada elemento en el intervalo y no es necesario que el valor devuelto sea el mismo cada vez que se llama. Así, por ejemplo, puede leer de un archivo o hacer referencia a un estado local y modificarlo. El tipo de resultado del generador debe poder convertirse en el tipo de valor de los iteradores hacia delante del intervalo.

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal, siendo necesarias exactamente `count` llamadas al generador.

### <a name="example"></a>Ejemplo

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}
```

## <a name="includes"></a><a name="includes"></a>presenta

Prueba si un intervalo ordenado contiene todos los elementos incluidos en un segundo intervalo ordenado, donde el criterio de ordenación o equivalencia entre los elementos se pueden especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que dirige a la posición del primer elemento del primero de dos intervalos de origen ordenados donde se va a comprobar que todos los elementos del segundo estén incluidos en el primero.

*last1*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del primero de dos intervalos de origen ordenados donde se va a comprobar que todos los elementos del segundo estén incluidos en el primero.

*first2*\
Iterador de entrada que dirige a la posición del primer elemento del segundo de dos intervalos de origen ordenados consecutivos donde se va a comprobar que todos los elementos del segundo estén incluidos en el primero.

*last2*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del segundo de dos intervalos de origen ordenados consecutivos donde se va a comprobar que todos los elementos del segundo estén incluidos en el primero.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="return-value"></a>Valor devuelto

**True** si el primer intervalo ordenado contiene todos los elementos del segundo intervalo ordenado; de lo contrario, **False**.

### <a name="remarks"></a>Observaciones

Otra utilidad de esta prueba es que permite determinar si el segundo intervalo de origen es un subconjunto del primero.

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo includes según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

El algoritmo no modifica los intervalos de origen `merge` .

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. Más concretamente, el algoritmo comprueba si todos los elementos del primer intervalo ordenado de un predicado binario especificado tienen una ordenación equivalente a los del segundo intervalo ordenado.

La complejidad del algoritmo es lineal con, a lo sumo, `2 * ((last1 - first1) - (last2 - first2)) - 1` comparaciones para intervalos de origen no vacíos.

### <a name="example"></a>Ejemplo

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
    bool Result1;
    Result1 = includes ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ) );
    if ( Result1 )
        cout << "All the elements in vector v1b are "
            << "contained in vector v1a." << endl;
    else
        cout << "At least one of the elements in vector v1b "
            << "is not contained in vector v1a." << endl;

    // To test for inclusion under descending
    // order specify binary predicate greater<int>( )
    bool Result2;
    Result2 = includes ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ), greater<int>( ) );
    if ( Result2 )
        cout << "All the elements in vector v2b are "
            << "contained in vector v2a." << endl;
    else
        cout << "At least one of the elements in vector v2b "
            << "is not contained in vector v2a." << endl;

    // To test for inclusion under a user
    // defined binary predicate mod_lesser
    bool Result3;
    Result3 = includes ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), mod_lesser );
    if ( Result3 )
        cout << "All the elements in vector v3b are "
            << "contained under mod_lesser in vector v3a."
            << endl;
    else
        cout << "At least one of the elements in vector v3b is "
            << " not contained under mod_lesser in vector v3a."
            << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a><a name="inplace_merge"></a>inplace_merge

Combina los elementos de dos intervalos ordenados consecutivos en un único intervalo ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que dirige a la posición del primer elemento del primero de dos intervalos ordenados consecutivos que se van a combinar y ordenar en un solo intervalo.

*Apellido*\
Iterador bidireccional que dirige a la posición del primer elemento del segundo de dos intervalos ordenados consecutivos que se van a combinar y ordenar en un solo intervalo.

*guardado*\
Iterador bidireccional que dirige a la posición situada una posición después del último elemento del segundo de dos intervalos ordenados consecutivos que se van a combinar y ordenar en un solo intervalo.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado de comparación toma dos argumentos y debe devolver **true** si el primer elemento es menor que el segundo elemento y **false** en caso contrario.

### <a name="remarks"></a>Observaciones

Los intervalos consecutivos ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

Los intervalos consecutivos ordenados deben estar organizados como condición previa a la aplicación del algoritmo `inplace_merge` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados. La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo en el intervalo combinado.

La complejidad depende de la memoria disponible, ya que el algoritmo asigna memoria a un búfer temporal. Si hay suficiente memoria disponible, el mejor caso es lineal con `(last - first) - 1` comparaciones; si no hay memoria auxiliar disponible, el peor de los casos es `N log(N)` , donde *N*es la  =  *last*  -  *primera*vez.

### <a name="example"></a>Ejemplo

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
    break1 = find (v1.begin( ), v1.end( ), -5 );
    inplace_merge ( v1.begin( ), break1, v1.end( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Applying a user defined (UD) binary predicate mod_lesser
    inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a><a name="is_heap"></a>is_heap

Devuelve **true** si los elementos del intervalo especificado forman un montón.

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de acceso aleatorio que indica el inicio de un intervalo en el que se va a buscar un montón.

*guardado*\
Iterador de acceso aleatorio que indica el final de un intervalo.

*pronostica*\
Condición que se va a probar para ordenar los elementos. Un predicado de comparación toma dos argumentos y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si los elementos del intervalo especificado forman un montón, **false** si no lo son.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve [is_heap_until](algorithm-functions.md#is_heap_until) `(first , last) == last` .

La segunda función de plantilla devuelve

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a><a name="is_heap_until"></a>is_heap_until

Devuelve un iterador colocado en el primer elemento del intervalo [ `first` , `last` ) que no satisface la condición de ordenación del montón, o *End* si el intervalo forma un montón.

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de acceso aleatorio que especifica el primer elemento de un intervalo para comprobar si hay un montón.

*guardado*\
Iterador de acceso aleatorio que especifica el final del intervalo para comprobar si hay un montón.

*pronostica*\
Predicado binario que especifica la condición de ordenación débil estricta que define un montón. El predicado predeterminado es `std::less<>` cuando no se especifica *Pred* .

### <a name="return-value"></a>Valor devuelto

Devuelve *Last* si el intervalo especificado forma un montón o contiene uno o menos elementos. De lo contrario, devuelve un iterador para el primer elemento encontrado que no satisface la condición de montón.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve el último iterador `next` de `[first, last)` donde `[first, next)` es un montón ordenado por el objeto de función `std::less<>`. Si la distancia `last - first` es menor que 2, la función devuelve *Last*.

La segunda función de plantilla se comporta igual que la primera, salvo que usa el predicado *Pred* en lugar de `std::less<>` como condición de ordenación del montón.

## <a name="is_partitioned"></a><a name="is_partitioned"></a>is_partitioned

Devuelve **true** si todos los elementos del intervalo especificado que prueban **true** para una condición van antes que los elementos que prueban **false**.

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica dónde comienza a comprobar una condición un intervalo.

*guardado*\
Iterador de entrada que indica el final de un intervalo.

*pronostica*\
Condición que se va a comprobar. La proporciona un objeto de función de predicado definido por el usuario que define la condición que debe cumplir el elemento que se está buscando. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** cuando todos los elementos del intervalo especificado que prueban **true** para una condición se encuentran antes que los elementos que prueban **false**, y en caso contrario, devuelve **false**.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve **true** solo si todos los elementos de `[first, last)` están particionados por *Pred*; es decir, todos los elementos `X` de `[first, last)` para los que `pred (X)` es true se producen antes de todos los elementos `Y` para los que `pred (Y)` es **false**.

## <a name="is_permutation"></a><a name="is_permutation"></a>is_permutation

Devuelve true si ambos intervalos contienen los mismos elementos, independientemente de si los elementos están en el mismo orden. Use las sobrecargas de dos intervalos en código C ++ 14 porque las sobrecargas que toman un único iterador para el segundo intervalo no detectan las diferencias si el segundo intervalo es más largo que el primero y esto provoca un comportamiento indefinido si el segundo intervalo es más corto que el primero.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*first1*\
Iterador hacia delante que hace referencia al primer elemento del intervalo.

*last1*\
Iterador hacia delante que hace referencia a un elemento más allá del último elemento del intervalo.

*first2*\
Iterador hacia delante que hace referencia al primer elemento de un segundo intervalo, usado para la comparación.

*last2*\
Iterador hacia delante que hace referencia a un elemento más allá del último elemento de un segundo intervalo, usado para la comparación.

*pronostica*\
Predicado que comprueba la equivalencia y devuelve un **booleano**.

### <a name="return-value"></a>Valor devuelto

**true** cuando los intervalos se pueden reorganizar de manera que sean idénticos según el predicado de comparación; en caso contrario, **false**.

### <a name="remarks"></a>Observaciones

En el peor de los casos, `is_permutation` tiene complejidad cuadrática.

La primera función de plantilla asume que hay tantos elementos en el intervalo a partir de *first2* , como en el intervalo designado por `[first1, last1)` . Si hay más elementos en el segundo intervalo, se ignoran; si hay menos, se producirá un comportamiento indefinido. La tercera función de plantilla (C++14 y versiones posteriores) no hace esta suposición. Ambos devuelven **true** solo si, para cada elemento X del intervalo designado por, hay tantos `[first1, last1)` elementos Y en el mismo intervalo para los cuales X = = Y en el intervalo que empieza en *first2* o `[first2, last2)` . Aquí, `operator==` debe realizar una comparación en pares entre sus operandos.

La segunda y la cuarta funciones de plantilla se comportan de la misma forma, salvo que reemplazan `operator==(X, Y)` con `Pred(X, Y)`. Para que se comporten correctamente, el predicado debe ser simétrico, reflexivo y transitivo.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar `is_permutation`:

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}
```

## <a name="is_sorted"></a><a name="is_sorted"></a>is_sorted

Devuelve **true** si los elementos del intervalo especificado están ordenados.

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que indica dónde empieza el intervalo que se va a comprobar.

*guardado*\
Iterador hacia delante que indica el final de un intervalo.

*pronostica*\
Condición que se va a probar para determinar un orden entre dos elementos. Un predicado de comparación toma dos argumentos y devuelve **true** o **false**. Realiza la misma tarea que `operator<`.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve [is_sorted_until](#is_sorted_until) `( first, last ) == last` . La `operator<` función realiza la comparación de orden.

La segunda función de plantilla devuelve `is_sorted_until( first, last , pred ) == last`. La función de predicado *Pred* realiza la comparación de orden.

## <a name="is_sorted_until"></a><a name="is_sorted_until"></a>is_sorted_until

Devuelve un `ForwardIterator` que se establece en el último elemento que está en el criterio de ordenación de un intervalo especificado.

La segunda versión permite proporcionar un objeto de función de comparación que devuelve **true** cuando dos elementos determinados están ordenados y **false** en caso contrario.

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que indica dónde se inicia el intervalo que se va a comprobar.

*guardado*\
Iterador hacia delante que indica el final de un intervalo.

*pronostica*\
Condición que se va a probar para determinar un orden entre dos elementos. Un predicado de comparación toma dos argumentos y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve un `ForwardIterator` establecido en el último elemento en el criterio de ordenación. La secuencia ordenada comienza en *primer lugar*.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve el último iterador `next` de `[first, last]` de modo que `[first, next)` es una secuencia ordenada por `operator<`. Si `distance()` es menor que 2, la función devuelve *Last*.

La segunda función de plantilla se comporta igual, salvo que sustituye `operator<(X, Y)` por `pred(X, Y)`.

## <a name="iter_swap"></a><a name="iter_swap"></a>iter_swap

Intercambia dos valores a los que se hace referencia mediante un par de iteradores especificados.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>Parámetros

*salido*\
Uno de los iteradores hacia delante cuyo valor se va a intercambiar.

*correcta*\
Segundo de los iteradores hacia delante cuyo valor se va a intercambiar.

### <a name="remarks"></a>Observaciones

`swap`debe usarse en preferencia a **iter_swap**, que se incluyó en el estándar de C++ para la compatibilidad con versiones anteriores. Si `Fit1` y `Fit2` son iteradores hacia delante, `iter_swap( Fit1, Fit2 )` es equivalente a `swap( *Fit1, *Fit2 )` .

Los tipos de valor de los iteradores hacia delante de entrada deben tener el mismo valor.

### <a name="example"></a>Ejemplo

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) { m_nVal =
    rhs.m_nVal; return *this; }
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt(" << rhs.m_nVal << ")";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    CInt c1 = 5, c2 = 1, c3 = 10;
    deque<CInt> deq1;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Exchanging first and last elements with iter_swap
    iter_swap ( deq1.begin( ), --deq1.end( ) );

    cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping back first and last elements with swap
    swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

    cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping a vector element with a deque element
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        deq2.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque deq2 is ( " ;
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;

    iter_swap ( v1.begin( ), deq2.begin( ) );

    cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a><a name="lexicographical_compare"></a>lexicographical_compare

Compara dos secuencias elemento a elemento para determinar cuál es menor de los dos.

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que dirige a la posición del primer elemento del primer intervalo que se va a comparar.

*last1*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del primer intervalo que se va a comparar.

*first2*\
Iterador de entrada que dirige a la posición del primer elemento del segundo intervalo que se va a comparar.

*last2*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del segundo intervalo que se va a comparar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="return-value"></a>Valor devuelto

**True** si el primer intervalo es lexicográficamente menor que el segundo; en caso contrario, **False**.

### <a name="remarks"></a>Observaciones

Una comparación lexicográfica entre secuencias las compara elemento a elemento hasta que:

- Encuentra dos elementos correspondientes distintos y el resultado de la comparación se toma como resultado de la comparación entre secuencias.

- No se encuentra ninguna desigualdad, pero una secuencia tiene más elementos que la otra y la secuencia más corta se considera menor que la más larga.

- No se encuentran desigualdades y las secuencias tienen el mismo número de elementos, por lo que las secuencias son iguales y el resultado de la comparación es **false**.

### <a name="example"></a>Ejemplo

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    int ii;
    for ( ii = 0 ; ii <= 6 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Self lexicographical_comparison of v1 under identity
    bool result1;
    result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v1.begin( ), v1.end( ) );
    if ( result1 )
        cout << "Vector v1 is lexicographically_less than v1." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v1." << endl;

    // lexicographical_comparison of v1 and L2 under identity
    bool result2;
    result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                    L1.begin( ), L1.end( ) );
    if ( result2 )
        cout << "Vector v1 is lexicographically_less than L1." << endl;
    else
        cout << "Vector v1 is lexicographically_less than L1." << endl;

    bool result3;
    result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v2.begin( ), v2.end( ), twice );
    if ( result3 )
        cout << "Vector v1 is lexicographically_less than v2 "
            << "under twice." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v2 "
            << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a><a name="lower_bound"></a>lower_bound

Busca la posición del primer elemento en un intervalo ordenado que tiene un valor mayor o equivalente a un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*valor*\
Valor en cuya primera posición o posible primera posición se busca en el intervalo ordenado.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante en la posición del primer elemento de un intervalo ordenado con un valor mayor que un valor especificado o equivalente a este, donde la equivalencia se especifica con un predicado binario.

### <a name="remarks"></a>Observaciones

El intervalo de origen ordenado al que se hace referencia debe ser válido; todos los iteradores deben poder desreferenciarse y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

Un intervalo ordenado es una condición previa al uso de `lower_bound`; en él el orden es el mismo que el especificado por el predicado binario.

El algoritmo `lower_bound` no modifica el intervalo.

Los tipos de valor de los iteradores hacia delante tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes.

La complejidad del algoritmo es logarítmica para los iteradores de acceso aleatorio y lineal en caso contrario, con el número de pasos proporcionales a ( `last - first` ).

### <a name="example"></a>Ejemplo

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a><a name="make_heap"></a>make_heap

Convierte elementos de un intervalo especificado en un montón en el que el primer elemento es el mayor y para el que se puede especificar un criterio de ordenación con un predicado binario.

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred );
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a convertir en un montón.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a convertir en un montón.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="remarks"></a>Observaciones

Los montones tienen dos propiedades:

- El primer elemento siempre es el mayor.

- Se pueden agregar o quitar elementos en tiempo logarítmico.

Los montones son una forma ideal de implementar colas de prioridad y se usan en la implementación del adaptador de contenedor de la biblioteca estándar de C++ [priority_queue (Clase)](priority-queue-class.md).

La complejidad es lineal, lo que requiere `3 * (last - first)` comparaciones.

### <a name="example"></a>Ejemplo

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="max"></a><a name="max"></a>máx.

Compara dos objetos y devuelve el mayor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*salido*\
Primero de los dos objetos que se van a comparar.

*correcta*\
Segundo de los dos objetos que se van a comparar.

*pronostica*\
Predicado binario utilizado para comparar los dos objetos.

*represente*\
Lista de inicializadores que contiene los objetos que se van a comparar.

### <a name="return-value"></a>Valor devuelto

El mayor de los dos objetos, a menos que ninguno sea mayor; en ese caso, devuelve el primero de los dos objetos. En el caso de una initializer_list, devuelve el mayor de los objetos de la lista.

### <a name="remarks"></a>Observaciones

Es poco habitual que el algoritmo `max` tenga objetos que se pasan como parámetros. La mayoría de los algoritmos de la biblioteca estándar de C++ actúan sobre un intervalo de elementos cuya posición se especifica mediante iteradores pasados como parámetros. Si necesita una función que actúe sobre un intervalo de elementos, use [max_element](algorithm-functions.md#max_element) en su lugar. Visual Studio 2017 habilita **constexpr** en las sobrecargas que toman una initializer_list.

### <a name="example"></a>Ejemplo

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = -elem1;
    if ( elem2 < 0 )
        elem2 = -elem2;
    return elem1 < elem2;
};

int main()
{
    int a = 6, b = -7;
    // Return the integer with the larger absolute value
    const int& result1 = max(a, b, abs_greater);
    // Return the larger integer
    const int& result2 = max(a, b);

    cout << "Using integers 6 and -7..." << endl;
    cout << "The integer with the greater absolute value is: "
            << result1 << "." << endl;
    cout << "The integer with the greater value is: "
            << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = max({ a, b });
    const int& result4 = max({ a, b }, abs_greater);

    cout << "Comparing the members of an initializer_list..." << endl;
    cout << "The member with the greater value is: " << result3 << endl;
    cout << "The integer with the greater absolute value is: " << result4 << endl;

    // Comparing set containers with elements of type CInt
    // using the max algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = max ( s1, s2 );
    cout << "s3 = max ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using the max algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = max ( v1, v2 );
    v5 = max ( v1, v3 );

    cout << "Vector v4 = max (v1,v2) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = max (v1,v3) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer with the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a><a name="max_element"></a>max_element

Busca la primera aparición del elemento mayor en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que direcciona la posición del primer elemento del intervalo en el que se va a buscar el elemento mayor.

*guardado*\
Iterador hacia delante que direcciona la posición de un elemento más allá del último elemento del intervalo en el que se va a buscar el elemento mayor.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado de comparación toma dos argumentos y debe devolver **true** si el primer elemento es menor que el segundo elemento y **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la posición de la primera aparición del elemento mayor en el intervalo buscado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de cada secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal: `(last - first) - 1` se necesitan comparaciones para un intervalo no vacío.

### <a name="example"></a>Ejemplo

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the maximum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

    cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The largest element in v1 under the mod_lesser"
            << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a><a name="merge"></a>sin

Combina todos los elementos de dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que direcciona la posición del primer elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo.

*last1*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo.

*first2*\
Iterador de entrada que direcciona la posición del primer elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo.

*last2*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino donde los dos intervalos de origen se van a combinar en un solo intervalo ordenado.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado de comparación toma dos argumentos y debe devolver **true** si el primer elemento es menor que el segundo elemento y **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona la posición situada una posición después del último elemento del intervalo de destino ordenado.

### <a name="remarks"></a>Observaciones

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo de destino no debe superponerse a ninguno de los intervalos de origen y debe ser lo suficientemente grande como para contener el intervalo de destino.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo `merge` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo en el intervalo de destino. El algoritmo no modifica los intervalos de origen `merge` .

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo intervalo de origen en el intervalo de destino.

La complejidad del algoritmo es lineal con, a lo sumo, `(last1 - first1) - (last2 - first2) - 1` comparaciones.

La [clase list ](list-class.md) proporciona una función miembro "merge" para combinar los elementos de dos listas.

### <a name="example"></a>Ejemplo

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main() {
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a><a name="min"></a> min

Compara dos objetos y devuelve el menor de los dos, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);

template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*salido*\
Primero de los dos objetos que se van a comparar.

*correcta*\
Segundo de los dos objetos que se van a comparar.

*pronostica*\
Predicado binario utilizado para comparar los dos objetos.

*represente*\
`initializer_list`Que contiene los miembros que se van a comparar.

### <a name="return-value"></a>Valor devuelto

El menor de los dos objetos, a menos que ninguno sea menor; en ese caso, devuelve el primero de los dos objetos. En el caso de `initializer_list` , devuelve el menor de los objetos de la lista.

### <a name="remarks"></a>Observaciones

Es poco habitual que el algoritmo `min` tenga objetos que se pasan como parámetros. La mayoría de los algoritmos de la biblioteca estándar de C++ actúan sobre un intervalo de elementos cuya posición se especifica mediante iteradores pasados como parámetros. Si necesita una función que emplee un intervalo de elementos, use [min_element](algorithm-functions.md#min_element). [constexpr](../cpp/constexpr-cpp.md) se habilitó en las `initializer_list` sobrecargas de Visual Studio 2017.

### <a name="example"></a>Ejemplo

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
    // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a><a name="min_element"></a>min_element

Busca la primera aparición del menor elemento en un intervalo especificado donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se va a buscar el elemento menor.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se va a buscar el elemento menor.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado de comparación toma dos argumentos y debe devolver **true** si el primer elemento es menor que el segundo elemento y **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la posición de la primera aparición del elemento menor en el intervalo en el que se busca.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de cada secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal: `(last - first) - 1` se necesitan comparaciones para un intervalo no vacío.

### <a name="example"></a>Ejemplo

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the minimum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

    cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a><a name="minmax_element"></a>minmax_element

Realiza el trabajo efectuado por `min_element` y `max_element` en una llamada.

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que indica el principio de un intervalo.

*guardado*\
Iterador hacia delante que indica el final de un intervalo.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado de comparación toma dos argumentos y debe devolver **true** cuando el primero es menor que el segundo y **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Devuelve

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

La segunda función de plantilla se comporta igual, salvo que sustituye `operator<(X, Y)` por `pred(X, Y)`.

Si la secuencia no está vacía, la función realiza a lo sumo `3 * (last - first - 1) / 2` comparaciones.

## <a name="minmax"></a><a name="minmax"></a>MinMax

Compara dos parámetros de entrada y los devuelve como un par, de menor a mayor.

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*salido*\
Primero de los dos objetos que se van a comparar.

*correcta*\
Segundo de los dos objetos que se van a comparar.

*pronostica*\
Predicado binario utilizado para comparar los dos objetos.

*represente*\
`initializer_list`Que contiene los miembros que se van a comparar.

### <a name="remarks"></a>Observaciones

La primera función de plantilla devuelve `pair<const Type&, const Type&>( right, left )` si *right* es menor que *left*. De lo contrario, devuelve `pair<const Type&, const Type&>( left, right )`.

La segunda función miembro devuelve un par donde el primer elemento es el menor y el segundo es el mayor cuando se comparan mediante el predicado *Pred*.

Las funciones de plantilla restantes se comportan de la misma manera, salvo que reemplazan los parámetros *izquierdo* y *derecho* por *inlist*.

La función realiza exactamente una comparación.

## <a name="mismatch"></a><a name="mismatch"></a>versiones

Compara dos intervalos elemento a elemento y localiza la primera posición en la que se produce una diferencia.

Use las sobrecargas de dos intervalos en código C ++ 14 porque las sobrecargas que toman un único iterador para el segundo intervalo no detectan las diferencias si el segundo intervalo es más largo que el primero y esto provoca un comportamiento indefinido si el segundo intervalo es más corto que el primero.

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Un iterador de entrada que dirige a la posición del primer elemento en el primer intervalo que se va a probar.

*last1*\
Un iterador de entrada que dirige a la posición situada una posición después del último elemento en el primer intervalo que se va a probar.

*first2*\
Un iterador de entrada que dirige a la posición del primer elemento en el segundo intervalo que se va a probar.

*last2*\
Un iterador de entrada que dirige a la posición situada una posición después del último elemento en el segundo intervalo que se va a probar.

*pronostica*\
Objeto de función de predicado definido por el usuario que compara los elementos actuales de cada intervalo y determina si son equivalentes. Devuelve **True** si se cumple y **False** si no.

### <a name="return-value"></a>Valor devuelto

Un par de iteradores que dirigen a las posiciones no coincidentes en los dos intervalos, el primer iterador del componente a la posición del primer intervalo y el segundo iterador del componente a la posición del segundo intervalo. Si no hay ninguna diferencia entre los elementos de los intervalos comparados o si todos los pares de elemento de los dos rangos satisfacen el predicado binario en la segunda versión, el primer iterador componente apunta a la posición uno pasado el elemento final en el primer intervalo y el segundo iterador del componente, a la posición uno pasado el último elemento probado en el segundo intervalo.

### <a name="remarks"></a>Observaciones

La primera función de plantilla asume que hay tantos elementos en el intervalo que empieza en first2 como en el intervalo designado mediante por [first1, last1). Si hay más en el segundo intervalo, se omiten; Si hay menos, se producirá un comportamiento indefinido.

El intervalo en el que se va a buscar debe ser válido: todos los iteradores deben poder desreferenciarse y se debe poder acceder a la última posición desde la primera con incrementos.

La complejidad temporal del algoritmo es lineal en el número de elementos incluidos en el intervalo más corto.

No es necesario que el predicado definido por el usuario imponga una relación de equivalencia que sea simétrica, reflexiva y transitiva entre sus operandos.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar la no coincidencia. La sobrecarga C++03 solo se muestra para demostrar cómo puede producir un resultado inesperado.

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="ltalggt-move"></a><a name="alg_move"></a> &lt;alg&gt; move

Mueve los elementos asociados a un intervalo especificado.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica dónde comienza el intervalo de elementos que se moverán.

*guardado*\
Iterador de entrada que indica el final de un intervalo de elementos que se moverán.

*dest*\
Iterador de salida que contendrá los elementos movidos.

### <a name="remarks"></a>Observaciones

La función de plantilla evalúa `*(dest + N) = move(*(first + N))` una vez por cada `N` del intervalo `[0, last - first)`, con los valores de `N` incrementados de forma estricta empezando por el valor inferior. Después, devuelve `dest + N`. Si `dest` y *primero* designan regiones de almacenamiento, *dest* no debe estar en el intervalo `[first, last)` .

## <a name="move_backward"></a><a name="move_backward"></a>move_backward

Mover los elementos de un iterador a otro. El movimiento comienza con el último elemento de un intervalo especificado y termina con el primer elemento de ese intervalo.

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador que indica el inicio de un intervalo del que se van a mover elementos.

*guardado*\
Iterador que indica el final de un intervalo del que se van a mover elementos. Este elemento no se mueve.

*desofertas*\
Iterador bidireccional que direcciona la posición de un elemento más allá del último elemento del intervalo de destino.

### <a name="remarks"></a>Observaciones

La función de plantilla evalúa `*(destEnd - N - 1) = move(*(last - N - 1))` una vez por cada `N` del intervalo `[0, last - first)`, con los valores de `N` incrementados de forma estricta empezando por el valor inferior. Después, devuelve `destEnd - (last - first)`. Si no se *propone* y *primero* se designan regiones de *almacenamiento, no* debe estar en el intervalo `[first, last)` .

`move` y `move_backward` son funcionalmente equivalentes a utilizar `copy` y `copy_backward` con un iterador de movimiento.

## <a name="next_permutation"></a><a name="next_permutation"></a>next_permutation

Reorganiza los elementos de un intervalo de modo que la ordenación original se reemplaza con la mayor permutación lexicográficamente siguiente si existe, donde el sentido de siguiente se puede especificar con un predicado binario.

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador bidireccional que apunta a la posición del primer elemento del intervalo que se va a permutar.

*guardado*\
Iterador bidireccional que apunta a la posición situada una posición después del último elemento del intervalo que se va a permutar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

**True** si la permutación lexicográficamente siguiente existe y ha sustituido a la ordenación original del intervalo; de lo contrario, **False**, en cuyo caso la ordenación se transforma en la permutación lexicográficamente menor.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El predicado binario predeterminado es menor que y los elementos del intervalo deben ser comparables con menor que para asegurarse de que la permutación siguiente está bien definida.

La complejidad es lineal con, a lo sumo, `(last - first) / 2` intercambios.

### <a name="example"></a>Ejemplo

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 5, c2 = 1, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically next permutation "
            << "exists and has\nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically next permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of next_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permuting vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a><a name="nth_element"></a>nth_element

Divide un intervalo de elementos, localizando correctamente el elemento *n*de la secuencia en el intervalo de modo que todos los elementos de delante sean menores o iguales que él y todos los elementos que lo siguen en la secuencia sean mayores o iguales que él.

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a dividir.

*enésimo*\
Iterador de acceso aleatorio que dirige a la posición del elemento que se va a ordenar correctamente en el límite de la partición.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a dividir.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El `nth_element` algoritmo no garantiza que se ordenen los elementos de los subrangos que estén en el lado del elemento *n*. Por eso ofrece menos garantías que `partial_sort`, que ordena los elementos del intervalo bajo algún elemento seleccionado y se puede usar como una alternativa más rápida a `partial_sort` cuando no se necesita la ordenación del intervalo inferior.

Los elementos son equivalentes, pero no necesariamente iguales, si ninguno es menor que el otro.

El promedio de una complejidad de ordenación es lineal con respecto al *último primero*.

### <a name="example"></a>Ejemplo

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
    return elem1 > elem2;
}

int main() {
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 3 * i );

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
        v1.push_back( 3 * ii + 1 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 3 * iii +2 );

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
    cout << "Position 3 partitioned vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
            greater<int>( ) );
    cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    random_shuffle( v1.begin( ), v1.end( ) );
    cout << "Shuffled vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
    cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

## <a name="none_of"></a><a name="none_of"></a>none_of

Devuelve **verdadero** cuando una condición nunca está presente entre los elementos del intervalo especificado.

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica dónde comenzar a comprobar una condición en un intervalo de elementos.

*guardado*\
Iterador de entrada que indica el final de un intervalo de elementos.

*pronostica*\
Condición que se va a comprobar. La proporciona y la define un objeto de función de predicado definido por el usuario. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si la condición no se detecta al menos una vez en el intervalo indicado, y **false** si se detecta la condición.

### <a name="remarks"></a>Observaciones

La función de plantilla devuelve **true** solo si, para algunos `N` en el intervalo `[0, last - first)` , el predicado `pred(*(first + N))` es siempre **false**.

## <a name="partial_sort"></a><a name="partial_sort"></a>partial_sort

Organiza un número especificado de los elementos menores de un intervalo en un orden no descendente, o de acuerdo con un criterio de ordenación especificado por un predicado binario.

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*sortEnd*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del subintervalo que se va a ordenar.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar de forma parcial.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los elementos son equivalentes, pero no necesariamente iguales, si ninguno es menor que el otro. El `sort` algoritmo no es estable y no garantiza que se conserve la ordenación relativa de los elementos equivalentes. El algoritmo `stable_sort` conserva esta ordenación original.

La complejidad media de ordenación parcial es *O*(( `last` -  `first` ) registro ( `sortEnd` -  `first` )).

### <a name="example"></a>Ejemplo

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii +1 );
    }

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
    cout << "Partially sorted vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To partially sort in descending order, specify binary predicate
    partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
    cout << "Partially resorted (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
    cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a><a name="partial_sort_copy"></a>partial_sort_copy

Copia los elementos de un intervalo de origen a un intervalo de destino donde los elementos de origen están ordenados por menor que u otro predicado binario especificado.

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que direcciona la posición del primer elemento del intervalo de origen.

*last1*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del intervalo de origen.

*first2*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo de destino ordenado.

*last2*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo de destino ordenado.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador de acceso aleatorio que dirige al elemento del intervalo de destino situado una posición después del último elemento del intervalo de origen.

### <a name="remarks"></a>Observaciones

Los intervalos de origen y destino no deben superponerse y deben ser válidos; todos los punteros se deben poder desreferenciar y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El predicado binario debe proporcionar una ordenación débil estricta para que se ordenen los elementos que no son equivalentes, pero no los que sí son equivalentes. Dos elementos son equivalentes según menor que, pero no necesariamente iguales, si ninguno es menor que el otro.

### <a name="example"></a>Ejemplo

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a><a name="partition"></a>divide

Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que dirige a la posición del primer elemento del intervalo que se va a dividir.

*guardado*\
Iterador bidireccional que dirige a la posición situada una posición después del último elemento del intervalo que se va a dividir.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que debe cumplir un elemento para ser clasificado. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que dirige a la posición del primer elemento del intervalo que no cumple la condición del predicado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los elementos *a* y *b* son equivalentes, pero no necesariamente iguales, si ambos `pred( a, b )` son false y `pred( b, a )` es false, donde *Pred* es el predicado especificado por el parámetro. El `partition` algoritmo no es estable y no garantiza que se conserve la ordenación relativa de los elementos equivalentes. El algoritmo `stable_partition` conserva esta ordenación original.

La complejidad es lineal: hay aplicaciones preparadas `(last - first)` y, a lo sumo, *pred* `(last - first)/2` intercambios.

### <a name="example"></a>Ejemplo

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }
    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    partition ( v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="partition_copy"></a><a name="partition_copy"></a>partition_copy

Copia los elementos para los que una condición es **verdadera** para un destino y cuya condición es **falsa** en otro. Los elementos deben proceder de un intervalo especificado.

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que indica el inicio de un intervalo en el que se va a comprobar una condición.

*guardado*\
Iterador de entrada que indica el final de un intervalo.

*dest1*\
Iterador de salida usado para copiar elementos que devuelven TRUE para una condición probada mediante *Pred*.

*dest2*\
Iterador de salida usado para copiar elementos que devuelven false para una condición probada mediante *Pred*.

*pronostica*\
Condición que se va a comprobar. La proporciona y la define un objeto de función de predicado definido por el usuario. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="remarks"></a>Observaciones

La función de plantilla copia cada elemento `X` de en `[first,last)` `*dest1++` si `pred(X)` es true, o en `*dest2++` si no lo está. Devuelve `pair<OutputIterator1, OutputIterator2>(dest1, dest2)`.

## <a name="partition_point"></a><a name="partition_point"></a>partition_point

Devuelve el primer elemento del intervalo especificado que no satisface la condición. Los elementos se ordenan de forma que aquellos que satisfacen la condición están antes que los que no lo hacen.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
`ForwardIterator` que indica el inicio de un intervalo en el que se va a comprobar una condición.

*guardado*\
`ForwardIterator` que indica el final de un intervalo.

*pronostica*\
Condición que se va a comprobar. La proporciona un objeto de función de predicado definido por el usuario que define la condición que debe cumplir el elemento que se está buscando. Un predicado unario toma un solo argumento y devuelve **true** o **false**.

### <a name="return-value"></a>Valor devuelto

Devuelve un `ForwardIterator` que hace referencia al primer elemento que no cumple la condición comprobada por *Pred*o devuelve *Last* si no se encuentra ninguno.

### <a name="remarks"></a>Observaciones

La función de plantilla encuentra el primer iterador `it` de `[first, last)` para el que `pred(*it)` es **false**. La secuencia se debe ordenar por *Pred*.

## <a name="pop_heap"></a><a name="pop_heap"></a>pop_heap

Quita el elemento mayor del principio de un montón hasta la penúltima posición del intervalo y después forma un nuevo montón con los elementos restantes.

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del montón.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del montón.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="remarks"></a>Observaciones

El algoritmo `pop_heap` es el inverso de la operación realizada por el algoritmo push_heap, que agrega un elemento en la posición siguiente a la última de un intervalo a un montón que se compone de los elementos anteriores del intervalo, en el caso de que el elemento que se va a agregar al montón sea mayor que cualquiera de los elementos ya presentes en este.

Los montones tienen dos propiedades:

- El primer elemento siempre es el mayor.

- Se pueden agregar o quitar elementos en tiempo logarítmico.

Los montones son una forma ideal de implementar colas de prioridad y se usan en la implementación del adaptador de contenedor de la biblioteca estándar de C++ [priority_queue (Clase)](priority-queue-class.md).

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El intervalo que excluye al elemento recién agregado al final debe ser un montón.

La complejidad es logarítmica, que requiere como máximo `log (last - first)` comparaciones.

### <a name="example"></a>Ejemplo

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    // Make v1 a heap with default less than ordering
    random_shuffle( v1.begin( ), v1.end( ) );
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the back of the heap
    v1.push_back( 10 );
    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove the largest element from the heap
    pop_heap( v1.begin( ), v1.end( ) );
    cout << "The heap v1 with 10 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater-than ordering with a 0 element
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    v1.push_back( 0 );
    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Application of pop_heap to remove the smallest element
    pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="prev_permutation"></a><a name="prev_permutation"></a>prev_permutation

Reorganiza los elementos de un intervalo de modo que la ordenación original se sustituya por la mayor permutación lexicográficamente anterior, si existe, donde el sentido de anterior se puede especificar con un predicado binario.

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador bidireccional que apunta a la posición del primer elemento del intervalo que se va a permutar.

*guardado*\
Iterador bidireccional que apunta a la posición situada una posición después del último elemento del intervalo que se va a permutar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

**true** si existe la permutación anterior lexicográficamente y se ha reemplazado la ordenación original del intervalo; de lo contrario, es **false**, en cuyo caso la ordenación se transforma en la permutación más grande de lexicográficamente.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El predicado binario predeterminado es menor que y los elementos del intervalo deben ser comparables con menor que para asegurarse de que la permutación anterior está bien definida.

La complejidad es lineal, con un máximo de ( `last`  -  `first` )/2 intercambios.

### <a name="example"></a>Ejemplo

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 1, c2 = 5, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically previous permutation "
            << "exists and has \nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically previous permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of prev_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permutating vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
        v1.push_back( i );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a><a name="push_heap"></a>push_heap

Agrega un elemento que está al final de un intervalo a un montón existente que se compone de los elementos anteriores del intervalo.

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del montón.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a convertir en un montón.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="remarks"></a>Observaciones

El elemento primero debe moverse al final de un montón existente y luego se usa el algoritmo para agregarlo al montón existente.

Los montones tienen dos propiedades:

- El primer elemento siempre es el mayor.

- Se pueden agregar o quitar elementos en tiempo logarítmico.

Los montones son una forma ideal de implementar colas de prioridad y se usan en la implementación del adaptador de contenedor de la biblioteca estándar de C++ [priority_queue (Clase)](priority-queue-class.md).

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El intervalo que excluye al elemento recién agregado al final debe ser un montón.

La complejidad es logarítmica, que requiere como máximo `log(last - first)` comparaciones.

### <a name="example"></a>Ejemplo

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the heap
    v1.push_back( 10 );
    cout << "The heap v1 with 10 pushed back is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    v1.push_back(0);
    cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater than reheaped v1 with 11 added is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="random_shuffle"></a><a name="random_shuffle"></a>random_shuffle

La función STD:: random_shuffle () está en desuso y se reemplaza por [STD:: orden aleatorio](algorithm-functions.md#shuffle). Para obtener un ejemplo de código y más información, vea [\<random>](random.md) y el stack Overflow post [¿por qué los métodos STD:: random_shuffle están en desuso en c++ 14?](https://go.microsoft.com/fwlink/p/?linkid=397954).

## <a name="remove"></a><a name="remove"></a>retirar

Elimina un valor especificado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que direcciona la posición del primer elemento del intervalo del que se quitan los elementos.

*guardado*\
Iterador hacia delante que direcciona la posición uno después del elemento final del intervalo del que se quitan los elementos.

*valor*\
El valor que debe quitarse del intervalo.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la nueva posición final del intervalo modificado, una después del elemento final del resto de la secuencia sin el valor especificado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El orden de los elementos no quitados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal; hay `last`  -  `first` comparaciones de igualdad ().

La [clase List](list-class.md) tiene una versión de función miembro más eficaz de `remove` , que también revincula punteros.

### <a name="example"></a>Ejemplo

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove ( v1.begin( ), v1.end( ), 7 );

    cout << "Vector v1 with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy"></a><a name="remove_copy"></a>remove_copy

Copia elementos de un intervalo de origen a un intervalo de destino, excepto que los elementos de un valor especificado no se copian, sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo de destino.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que direcciona la posición del primer elemento del intervalo del que se quitan los elementos.

*guardado*\
Iterador de entrada que direcciona la posición situada una posición después del elemento final del intervalo del que se quitan los elementos.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino del que se quitan los elementos.

*valor*\
El valor que debe quitarse del intervalo.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la nueva posición final del intervalo de destino, situada una posición después del elemento final de la copia de la secuencia restante sin el valor especificado.

### <a name="remarks"></a>Observaciones

Los intervalos de origen y destino a los que se hace referencia deben ser válidos; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

Debe haber suficiente espacio en el intervalo de destino para incluir los elementos restantes que se copiarán después de quitar elementos del valor especificado.

El orden de los elementos no quitados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal; hay `last`  -  `first` comparaciones de igualdad y, a lo sumo, ( `last`  -  `first` ).

### <a name="example"></a>Ejemplo

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:     ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

    cout << "Vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a><a name="remove_copy_if"></a>remove_copy_if

Copia elementos de un intervalo de origen a un intervalo de destino, excepto los elementos que cumplen un predicado. Los elementos se copian sin alterar el orden de los elementos restantes. Devuelve el final de un nuevo intervalo de destino.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que direcciona la posición del primer elemento del intervalo del que se quitan los elementos.

*guardado*\
Iterador de entrada que direcciona la posición situada una posición después del elemento final del intervalo del que se quitan los elementos.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino del que se quitan los elementos.

*pronostica*\
El predicado unario que debe cumplirse es el valor de un elemento que se va a reemplazar.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la nueva posición final del intervalo de destino, situada una posición después del elemento final de la secuencia restante sin los elementos que cumplen el predicado.

### <a name="remarks"></a>Observaciones

El intervalo de origen al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Debe haber suficiente espacio en el intervalo de destino para incluir los elementos restantes que se copiarán después de quitar elementos del valor especificado.

El orden de los elementos no quitados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal: hay ( `last`  -  `first` ) comparaciones para igualdad y, a lo sumo, ( `last`  -  `first` ) asignaciones.

Para más información sobre el comportamiento de estas funciones, vea [Iteradores activados](checked-iterators.md).

### <a name="example"></a>Ejemplo

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:      ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value greater than 6
    new_end = remove_copy_if ( v1.begin( ), v1.end( ),
        v2.begin( ), greater6 );

    cout << "After the appliation of remove_copy_if to v1,\n "
         << "vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with values greater "
         << "than 6 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_if"></a><a name="remove_if"></a>remove_if

Elimina los elementos que cumplen un predicado de un intervalo determinado sin alterar el orden de los elementos restantes y devolver el final de un nuevo intervalo libre del valor especificado.

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que apunta a la posición del primer elemento del intervalo del que se van a quitar elementos.

*guardado*\
Iterador hacia delante que apunta a la posición situada una posición después del último elemento del intervalo del que se van a quitar elementos.

*pronostica*\
El predicado unario que debe cumplirse es el valor de un elemento que se va a reemplazar.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que direcciona la nueva posición final del intervalo modificado, una después del elemento final del resto de la secuencia sin el valor especificado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El orden de los elementos no quitados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal: hay ( `last`  -  `first` ) comparaciones para igualdad.

List tiene una versión de función miembro más eficaz de remove, que vuelve a vincular los punteros.

### <a name="example"></a>Ejemplo

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements satisfying predicate greater6
    new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

    cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace"></a><a name="replace"></a>Reemplace

Examina cada elemento de un intervalo y lo reemplaza si coincide con un valor especificado.

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que apunta a la posición del primer elemento del intervalo en el que se van a sustituir elementos.

*guardado*\
Iterador hacia delante que apunta a la posición situada una posición después del último elemento del intervalo en el que se van a sustituir elementos.

*oldVal*\
Valor anterior de los elementos que se van a reemplazar.

*newVal*\
Nuevo valor que se va a asignar a los elementos con el valor anterior.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El orden de los elementos no reemplazados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal; hay ( `last`  -  `first` ) comparaciones para igualdad y, a lo sumo, ( `last`  -  `first` ) asignaciones de nuevos valores.

### <a name="example"></a>Ejemplo

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 with a value of 700
    replace (v1.begin( ), v1.end( ), 7 , 700);

    cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy"></a><a name="replace_copy"></a>replace_copy

Examina cada elemento de un intervalo de origen y lo reemplaza si coincide con un valor especificado y copia el resultado a un nuevo intervalo de destino.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que apunta a la posición del primer elemento del intervalo cuyos elementos se reemplazan.

*guardado*\
Iterador de entrada que apunta a la posición situada una posición después del último elemento del intervalo cuyos elementos se reemplazan.

*da*\
Iterador de salida que apunta al primer elemento del intervalo de destino en el que se va a copiar la secuencia de elementos modificada.

*oldVal*\
Valor anterior de los elementos que se van a reemplazar.

*newVal*\
Nuevo valor que se va a asignar a los elementos con el valor anterior.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que apunta a la posición situada una posición después del último elemento del intervalo de destino en el que se copia la secuencia de elementos modificada.

### <a name="remarks"></a>Observaciones

Los intervalos de origen y destino a los que se hace referencia no deben superponerse y deben ser válidos: todos los punteros se deben poder desreferenciar y, dentro de las secuencias, la última posición debe ser accesible desde la primera mediante incrementos.

El orden de los elementos no reemplazados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal: hay ( `last`  -  `first` ) comparaciones para igualdad y, a lo sumo, ( `last`  -  `first` ) asignaciones de nuevos valores.

### <a name="example"></a>Ejemplo

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 15 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in one part of a vector with a value of 7
    // with a value of 70 and copy into another part of the vector
    replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

    cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

    cout << "The list copy L1 of v1 with the value 0 replacing "
            << "that of 7 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a><a name="replace_copy_if"></a>replace_copy_if

Examina cada elemento de un intervalo de origen y lo reemplaza si satisface un predicado especificado y copia el resultado a un nuevo intervalo de destino.

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de entrada que apunta a la posición del primer elemento del intervalo cuyos elementos se reemplazan.

*guardado*\
Iterador de entrada que apunta a la posición situada una posición después del último elemento del intervalo cuyos elementos se reemplazan.

*da*\
Iterador de salida que apunta a la posición del primer elemento del intervalo de destino en el que se copian los elementos.

*pronostica*\
El predicado unario que debe cumplirse es el valor de un elemento que se va a reemplazar.

*valor*\
Nuevo valor que se asigna a los elementos cuyo valor antiguo cumple el predicado.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que apunta a la posición situada una posición después del último elemento del intervalo de destino en el que se copia la secuencia de elementos modificada.

### <a name="remarks"></a>Observaciones

Los intervalos de origen y destino a los que se hace referencia no deben superponerse y deben ser válidos: todos los punteros se deben poder desreferenciar y, dentro de las secuencias, la última posición debe ser accesible desde la primera mediante incrementos.

El orden de los elementos no reemplazados no se ve afectado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal; hay ( `last`  -  `first` ) comparaciones para igualdad y, a lo sumo, ( `last`  -  `first` ) asignaciones de nuevos valores.

### <a name="example"></a>Ejemplo

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 13 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 in the 1st half of a vector
    // with a value of 70 and copy it into the 2nd half of the vector
    replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
        greater6 , 70);

    cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
        greater6 , -1 );

    cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_if"></a><a name="replace_if"></a>replace_if

Examina cada elemento de un intervalo y lo reemplaza si satisface un predicado especificado.

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que apunta a la posición del primer elemento del intervalo en el que se van a sustituir elementos.

*guardado*\
Iterador que apunta a la posición situada una posición después del último elemento del intervalo en el que se van a sustituir elementos.

*pronostica*\
El predicado unario que debe cumplirse es el valor de un elemento que se va a reemplazar.

*valor*\
Nuevo valor que se asigna a los elementos cuyo valor antiguo cumple el predicado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

El orden de los elementos no reemplazados no se ve afectado.

El algoritmo `replace_if` es una generalización del algoritmo `replace` , lo que permite especificar cualquier predicado, en lugar de igualdad a un valor constante especificado.

El `operator==` utilizado para determinar la igualdad entre elementos debe imponer una relación de equivalencia entre sus operandos.

La complejidad es lineal: hay ( `last`  -  `first` ) comparaciones para igualdad y, a lo sumo, ( `last`  -  `first` ) asignaciones de nuevos valores.

### <a name="example"></a>Ejemplo

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements satisfying the predicate greater6
    // with a value of 70
    replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

    cout << "The vector v1 with a value 70 replacing those\n "
         << "elements satisfying the greater6 predicate is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="reverse"></a><a name="reverse"></a>viceversa

Invierte el orden de los elementos dentro de un intervalo.

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que apunta a la posición del primer elemento del intervalo en el que se van a permutar los elementos.

*guardado*\
Iterador bidireccional que apunta a la posición situada una posición después del último elemento del intervalo en el que se van a permutar los elementos.

### <a name="remarks"></a>Observaciones

El intervalo de origen al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

### <a name="example"></a>Ejemplo

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse (v1.begin( ), v1.end( ) );

    cout << "The modified vector v1 with values reversed is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a><a name="reverse_copy"></a>reverse_copy

Invierte el orden de los elementos dentro de un intervalo de origen mientras los copia a un intervalo de destino

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que apunta a la posición del primer elemento del intervalo de origen en el que se permutan los elementos.

*guardado*\
Iterador bidireccional que apunta a la posición situada una posición después del último elemento del intervalo de origen en el que se permutan los elementos.

*da*\
Iterador de salida que apunta a la posición del primer elemento del intervalo de destino en el que se copian los elementos.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que apunta a la posición situada una posición después del último elemento del intervalo de destino en el que se copia la secuencia de elementos modificada.

### <a name="remarks"></a>Observaciones

Los intervalos de origen y destino a los que se hace referencia deben ser válidos; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

### <a name="example"></a>Ejemplo

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

    cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "The original vector v1 remains unmodified as:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="rotate"></a><a name="rotate"></a>rota

Intercambia los elementos de dos intervalos adyacentes.

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que direcciona la posición del primer elemento del intervalo que se va a intercambiar.

*Apellido*\
Iterador hacia delante que define el límite dentro del intervalo que direcciona la posición del primer elemento de la segunda parte del intervalo cuyos elementos se van a intercambiar con los de la primera parte del intervalo.

*guardado*\
Iterador hacia delante que direcciona la posición situada una posición después del último elemento del intervalo que se va a intercambiar.

### <a name="remarks"></a>Observaciones

Los intervalos a los que se hace referencia deben ser válidos; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

La complejidad es lineal con, a lo sumo, ( `last`  -  `first` ) swaps.

### <a name="example"></a>Ejemplo

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
    {
        d1.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a><a name="rotate_copy"></a>rotate_copy

Intercambia los elementos de dos intervalos adyacentes dentro de un intervalo de origen y copia el resultado a un intervalo de destino.

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que direcciona la posición del primer elemento del intervalo que se va a intercambiar.

*Apellido*\
Iterador hacia delante que define el límite dentro del intervalo que direcciona la posición del primer elemento de la segunda parte del intervalo cuyos elementos se van a intercambiar con los de la primera parte del intervalo.

*guardado*\
Iterador hacia delante que direcciona la posición situada una posición después del último elemento del intervalo que se va a intercambiar.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona la posición situada una posición después del último elemento del intervalo de destino.

### <a name="remarks"></a>Observaciones

Los intervalos a los que se hace referencia deben ser válidos; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

La complejidad es lineal con, a lo sumo, ( `last`  -  `first` ) swaps.

### <a name="example"></a>Ejemplo

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a><a name="sample"></a>AdventureWorks

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a><a name="search"></a>buscan

Busca la primera aparición de una secuencia dentro de un intervalo de destino cuyos elementos son iguales que los de una secuencia determinada de elementos o cuyos elementos son equivalentes según lo especificado por un predicado binario a los elementos de la secuencia especificada.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*last1*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*first2*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo con el que se establecerá la coincidencia.

*last2*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo con el que se establecerá la coincidencia.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

*buscador*\
El buscador que encapsula el patrón que se va a buscar y el algoritmo de búsqueda que se va a usar. Para obtener más información sobre los buscadores, vea [default_searcher clase](default-searcher-class.md), [boyer_moore_horspool_searcher clase](boyer-moore-horspool-searcher-class.md)y [boyer_moore_searcher clase](boyer-moore-searcher-class.md).

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la posición del primer elemento de la primera subsecuencia que coincide con la secuencia especificada o que es equivalente en un sentido especificado por un predicado binario.

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

Los intervalos a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, se debe poder acceder a la última posición desde la primera mediante incrementos.

La complejidad del promedio es lineal con respecto al tamaño del intervalo en el que se busca; el peor escenario de complejidad también es lineal con respecto al tamaño de la secuencia que se está buscando.

### <a name="example"></a>Ejemplo

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a><a name="search_n"></a>search_n

Busca la primera subsecuencia de un intervalo en la que un número especificado de elementos tienen un valor determinado o una relación con ese valor según lo especificado por un predicado binario.

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo en el que se buscará.

*last1*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo en el que se buscará.

*contabiliza*\
Tamaño de la subsecuencia que se está buscando.

*valor*\
Valor de los elementos de la secuencia que se está buscando.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que dirige a la posición del primer elemento de la primera subsecuencia que coincide con la secuencia especificada o que es equivalente en un sentido especificado por un predicado binario.

### <a name="remarks"></a>Observaciones

El `operator==` que se usa para determinar la coincidencia entre un elemento y el valor especificado debe imponer una relación de equivalencia entre sus operandos.

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es lineal con respecto al tamaño de lo buscado.

### <a name="example"></a>Ejemplo

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
    return elem1 == 2 * elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
    result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

    if ( result2 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1"
            << " under the equivalence predicate one_half." << endl;
    else
        cout << "There is a match of a sequence ( 5 5 5 ) "
            << "under the equivalence\n predicate one_half "
            << "in v1 and the first one begins at "
            << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a><a name="set_difference"></a>set_difference

Agrupa todos los elementos que pertenecen a un intervalo de origen ordenado, pero no a un segundo intervalo de origen ordenado, en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que dirige a la posición del primer elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la diferencia de los dos intervalos de origen.

*last1*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la diferencia de los dos intervalos de origen.

*first2*\
Iterador de entrada que dirige a la posición del primer elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la diferencia de los dos intervalos de origen.

*last2*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la diferencia de los dos intervalos de origen.

*da*\
Iterador de salida que dirige a la posición del primer elemento del intervalo de destino donde los dos intervalos de origen se van a combinar en un solo intervalo ordenado que representa la diferencia de los dos intervalos de origen.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado binario toma dos argumentos y debe devolver el valor **true** si el primer elemento es menor que el segundo elemento y el valor **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino ordenado que representa la diferencia de los dos intervalos de origen.

### <a name="remarks"></a>Observaciones

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo de destino no debe superponerse a ninguno de los intervalos de origen y debe ser lo suficientemente grande como para contener el intervalo del primer origen.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo `set_difference` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo en el intervalo de destino. El algoritmo merge no modifica los intervalos de origen.

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro). Esto produce una ordenación entre los elementos no equivalentes. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo intervalo de origen en el intervalo de destino. Si los intervalos de origen contienen duplicados de un elemento, de forma que hay más en el primer intervalo de origen que en el segundo, el intervalo de destino contendrá el número por el que las apariciones de esos elementos en el primer intervalo de origen supera a las apariciones de esos elementos en el segundo intervalo de origen.

La complejidad del algoritmo es lineal con, a lo sumo, `2 * ((last1 - first1) - (last2 - first2)) - 1` comparaciones para intervalos de origen no vacíos.

### <a name="example"></a>Ejemplo

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a><a name="set_intersection"></a>set_intersection

Agrupa todos los elementos que pertenecen a ambos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que direcciona la posición del primer elemento en el primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la intersección de los dos intervalos de origen.

*last1*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento en el primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la intersección de los dos intervalos de origen.

*first2*\
Iterador de entrada que direcciona la posición del primer elemento en el segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la intersección de los dos intervalos de origen.

*last2*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento en el segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la intersección de los dos intervalos de origen.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino donde los dos intervalos de origen se van a combinar en un solo intervalo ordenado que representa la intersección de los dos intervalos de origen.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado binario toma dos argumentos y debe devolver el valor **true** si el primer elemento es menor que el segundo elemento y el valor **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona la posición situada una posición después del último elemento del intervalo de destino ordenado que representa la intersección de los dos intervalos de origen.

### <a name="remarks"></a>Observaciones

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo de destino no debe superponerse a ninguno de los intervalos de origen y debe ser lo suficientemente grande como para contener el intervalo de destino.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo merge según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo en el intervalo de destino. El algoritmo no modifica los intervalos de origen.

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo intervalo de origen en el intervalo de destino. Si los intervalos de origen contienen duplicados de un elemento, el intervalo de destino contendrá el número máximo de los elementos que aparecen en ambos intervalos de origen.

La complejidad del algoritmo es lineal con, a lo sumo, `2 * ((last1 - first1) + (last2 - first2)) - 1` comparaciones para intervalos de origen no vacíos.

### <a name="example"></a>Ejemplo

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a><a name="set_symmetric_difference"></a>set_symmetric_difference

Agrupa todos los elementos que pertenecen a uno, pero no a ambos, de los intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que direcciona la posición del primer elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la diferencia simétrica de los dos intervalos de origen.

*last1*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento del primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la diferencia simétrica de los dos intervalos de origen.

*first2*\
Iterador de entrada que direcciona la posición del primer elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la diferencia simétrica de los dos intervalos de origen.

*last2*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento del segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la diferencia simétrica de los dos intervalos de origen.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino donde los dos intervalos de origen se van a combinar en un solo intervalo ordenado que representa la diferencia simétrica de los dos intervalos de origen.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado binario toma dos argumentos y debe devolver el valor **true** si el primer elemento es menor que el segundo elemento y el valor **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona la posición situada una posición después del último elemento del intervalo de destino ordenado que representa la diferencia simétrica de los dos intervalos de origen.

### <a name="remarks"></a>Observaciones

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo de destino no debe superponerse a ninguno de los intervalos de origen y debe ser lo suficientemente grande como para contener el intervalo de destino.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo `merge*` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo en el intervalo de destino. El algoritmo merge no modifica los intervalos de origen.

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo intervalo de origen en el intervalo de destino. Si los intervalos de origen contienen duplicados de un elemento, el intervalo de destino contendrá el valor absoluto del número por el que las apariciones de esos elementos en uno de los intervalos de origen supera a las apariciones de esos elementos en el segundo intervalo de origen.

La complejidad del algoritmo es lineal con, a lo sumo, `2 * ((last1 - first1) - (last2 - first2)) - 1` comparaciones para intervalos de origen no vacíos.

### <a name="example"></a>Ejemplo

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a><a name="set_union"></a>set_union

Agrupa todos los elementos que pertenecen al menos a uno de los dos intervalos de origen ordenados en un único intervalo de destino ordenado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que direcciona la posición del primer elemento en el primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la unión de los dos intervalos de origen.

*last1*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento en el primero de dos intervalos de origen ordenados que se van a combinar y ordenar en un solo intervalo que representa la unión de los dos intervalos de origen.

*first2*\
Iterador de entrada que direcciona la posición del primer elemento en el segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la unión de los dos intervalos de origen.

*last2*\
Iterador de entrada que direcciona la posición situada una posición después del último elemento en el segundo de dos intervalos de origen ordenados consecutivos que se van a combinar y ordenar en un solo intervalo que representa la unión de los dos intervalos de origen.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino donde los dos intervalos de origen se van a combinar en un solo intervalo ordenado que representa la unión de los dos intervalos de origen.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. El predicado binario toma dos argumentos y debe devolver el valor **true** si el primer elemento es menor que el segundo elemento y el valor **false** en caso contrario.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona la posición situada una posición después del último elemento del intervalo de destino ordenado que representa la unión de los dos intervalos de origen.

### <a name="remarks"></a>Observaciones

Los intervalos de origen ordenados a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

El intervalo de destino no debe superponerse a ninguno de los intervalos de origen y debe ser lo suficientemente grande como para contener el intervalo de destino.

Los intervalos de origen ordenados deben estar organizados como condición previa a la aplicación del algoritmo `merge` según el mismo orden que va a usar el algoritmo para ordenar los intervalos combinados.

La operación es estable, ya que se conserva el orden relativo de los elementos de cada intervalo en el intervalo de destino. El algoritmo no modifica los intervalos de origen `merge` .

Los tipos de valor de los iteradores de entrada tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes. Cuando hay elementos equivalentes en ambos intervalos de origen, los elementos del primer intervalo preceden a los del segundo intervalo de origen en el intervalo de destino. Si los intervalos de origen contienen duplicados de un elemento, el intervalo de destino contendrá el número máximo de los elementos que aparecen en ambos intervalos de origen.

La complejidad del algoritmo es lineal con, a lo sumo, `2 * ((last1 - first1) - (last2 - first2)) - 1` comparaciones.

### <a name="example"></a>Ejemplo

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a><a name="shuffle"></a>aleatoria

Ordena (reorganiza) elementos para un intervalo determinado utilizando un generador de números aleatorio.

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Un iterador del primer elemento del intervalo que debe ordenarse, incluido. Debe cumplir los requisitos de `RandomAccessIterator` y `ValueSwappable`.

*guardado*\
Un iterador del último elemento del intervalo que debe ordenarse, excluido. Debe cumplir los requisitos de `RandomAccessIterator` y `ValueSwappable`.

*Group*\
El generador de números aleatorios que la función `shuffle()` utilizará para la operación. Debe cumplir los requisitos de un `UniformRandomNumberGenerator`.

### <a name="remarks"></a>Observaciones

Para obtener más información y un ejemplo de código que utiliza `shuffle()` , vea [\<random>](random.md) .

## <a name="sort"></a><a name="sort"></a>clasificación

Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario.

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Este predicado binario toma dos argumentos y devuelve **true** si los dos argumentos están en orden y **false** en caso contrario. Esta función de comparador debe imponer una ordenación débil estricta en los pares de elementos de la secuencia. Para más información, vea [Algoritmos](algorithms.md).

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los elementos son equivalentes, pero no necesariamente iguales, si ninguno es menor que el otro. El algoritmo `sort` no es estable ni garantiza la conservación de la ordenación relativa de los elementos equivalentes. El algoritmo `stable_sort` conserva esta ordenación original.

El promedio de una complejidad de ordenación es `O( N log N )` , donde *N*  =  *last*  -  *primero*.

### <a name="example"></a>Ejemplo

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii + 1 );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    sort( v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order. specify binary predicate
    sort( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    sort( v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a><a name="sort_heap"></a>sort_heap

Convierte un montón en un intervalo ordenado.

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Iterador de acceso aleatorio que dirige a la posición del primer elemento del montón de destino.

*guardado*\
Iterador de acceso aleatorio que dirige a la posición situada una posición después del último elemento del montón de destino.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="remarks"></a>Observaciones

Los montones tienen dos propiedades:

- El primer elemento siempre es el mayor.

- Se pueden agregar o quitar elementos en tiempo logarítmico.

Después de la aplicación de este algoritmo, el intervalo al que se ha aplicado ya no es un montón.

No es un orden estable, porque no se conserva necesariamente el orden relativo de los elementos equivalentes.

Los montones son una forma ideal de implementar colas de prioridad y se usan en la implementación del adaptador de contenedor de la biblioteca estándar de C++ [priority_queue (Clase)](priority-queue-class.md).

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

La complejidad es como máximo `N log N` , donde *N*  =  *last*  -  *primero*.

### <a name="example"></a>Ejemplo

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a><a name="stable_partition"></a>stable_partition

Clasifica los elementos de un intervalo en dos conjuntos disjuntos, donde los elementos que satisfacen un predicado unario preceden a los que no lo satisfacen, conservando el orden relativo de los elementos equivalentes.

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que dirige a la posición del primer elemento del intervalo que se va a dividir.

*guardado*\
Iterador bidireccional que dirige a la posición situada una posición después del último elemento del intervalo que se va a dividir.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que debe cumplir un elemento para ser clasificado. Un predicado unario toma un solo argumento y devuelve **true** si se cumple, o **false** si no se cumple.

### <a name="return-value"></a>Valor devuelto

Iterador bidireccional que dirige a la posición del primer elemento del intervalo que no cumple la condición del predicado.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los elementos *a* y *b* son equivalentes, pero no necesariamente iguales, si ambos `pred( a, b )` son false y `pred( b, a )` es false, donde *Pred* es el predicado especificado por el parámetro. El `stable_partition` algoritmo es estable y garantiza que se conservará el orden relativo de los elementos equivalentes. El algoritmo `partition` no conserva necesariamente este orden original.

### <a name="example"></a>Ejemplo

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 4 ; ii++ )
        v1.push_back( 5 );

    random_shuffle(v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    result = stable_partition (v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "The first element in v1 to fail to satisfy the"
         << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a><a name="stable_sort"></a>stable_sort

Organiza los elementos de un intervalo especificado en un orden no descendente o de acuerdo con un criterio de ordenación especificado por un predicado binario y conserva el orden relativo de los elementos equivalentes.

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador bidireccional que dirige a la posición del primer elemento del intervalo que se va a ordenar.

*guardado*\
Iterador bidireccional que dirige a la posición situada una posición después del último elemento del intervalo que se va a ordenar.

*pronostica*\
Objeto de función de predicado definido por el usuario que define el criterio de comparación que deben cumplir los elementos sucesivos de la ordenación. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="remarks"></a>Observaciones

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos.

Los elementos son equivalentes, pero no necesariamente iguales, si ninguno es menor que el otro. El `sort` algoritmo es estable y garantiza que se conservará el orden relativo de los elementos equivalentes.

La complejidad en tiempo de ejecución de `stable_sort` depende de la cantidad de memoria disponible, pero el mejor caso (dado la memoria suficiente) es `O(N log N)` y el peor de los casos es `O(N (log N)^2)` , donde *N*en  =  *último*  -  *lugar*. Normalmente, el `sort` algoritmo es significativamente más rápido que `stable_sort` .

### <a name="example"></a>Ejemplo

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    stable_sort(v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    stable_sort(v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a><a name="swap"></a>pasar

El primer reemplazo intercambia los valores de dos objetos. El segundo reemplazo intercambia los valores entre dos matrices de objetos.

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>Parámetros

*salido*\
En el primer reemplazo, primer objeto cuyo contenido se intercambia. En el segundo reemplazo, primera matriz de objetos cuyo contenido se intercambia.

*correcta*\
En el primer reemplazo, segundo objeto cuyo contenido se intercambia. En el segundo reemplazo, segunda matriz de objetos cuyo contenido se intercambia.

### <a name="remarks"></a>Observaciones

La primera sobrecarga está diseñada para actuar sobre objetos individuales. La segunda sobrecarga intercambia el contenido de objetos entre dos matrices.

### <a name="example"></a>Ejemplo

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    for ( int i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }

    for ( int ii = 0 ; ii <= 4 ; ii++ )
    {
        v2.push_back( 5 );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    swap( v1, v2 );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a><a name="swap_ranges"></a>swap_ranges

Intercambia los elementos de un intervalo con los elementos de otro intervalo del mismo tamaño.

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador hacia delante que apunta a la primera posición del primer intervalo cuyos elementos se van a intercambiar.

*last1*\
Iterador hacia delante que apunta a la posición situada una posición después del último elemento del primer intervalo cuyos elementos se van a intercambiar.

*first2*\
Iterador hacia delante que apunta a la primera posición del segundo intervalo cuyos elementos se van a intercambiar.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante que apunta a la posición situada una posición después del último elemento del segundo intervalo cuyos elementos se van a intercambiar.

### <a name="remarks"></a>Observaciones

Los intervalos a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, se debe poder acceder a la última posición desde la primera mediante incrementos. El segundo intervalo tiene que ser tan grande como el primero.

La complejidad es lineal con los intercambios de *last1*  -  *first1* realizados. Si se intercambian elementos de contenedores del mismo tipo, se debería usar la función miembro `swap` de ese contenedor, porque esta normalmente tiene complejidad constante.

### <a name="example"></a>Ejemplo

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =4 ; ii <= 9 ; ii++ )
    {
        d1.push_back( 6 );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

    cout << "After the swap_range, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "After the swap_range deque d1 is   ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a><a name="transform"></a>transformación

Aplica un objeto de función especificado a cada elemento de un intervalo de origen o a un par de elementos de dos intervalos de origen y copia los valores devueltos del objeto de función a un intervalo de destino.

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*first1*\
Iterador de entrada que dirige a la posición del primer elemento del primer intervalo de origen en el que se va a operar.

*last1*\
Iterador de entrada que dirige a la posición situada una posición después del último elemento del primer intervalo de origen en el que se va a operar.

*first2*\
Iterador de entrada que dirige a la posición del primer elemento del segundo intervalo de origen en el que se va a operar.

*da*\
Iterador de salida que direcciona la posición del primer elemento del intervalo de destino.

*funciones*\
Objeto de función unario definido por el usuario empleado en la primera versión del algoritmo que se aplica a cada elemento del primer intervalo de origen u objeto de función binario definido por el usuario empleado en la segunda versión del algoritmo que se aplica en pares, en un orden hacia delante, a los dos intervalos de origen.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino que va a recibir los elementos de salida transformados por el objeto de función.

### <a name="remarks"></a>Observaciones

Los intervalos a los que se hace referencia deben ser válidos; todos los punteros deben poder desreferenciarse y, dentro de cada secuencia, se debe poder acceder a la última posición desde la primera mediante incrementos. El intervalo de destino debe ser lo suficientemente grande como para contener el intervalo de origen transformado.

Si el *resultado* se establece en *first1* en la primera versión del algoritmo, los intervalos de origen y de destino serán iguales y la secuencia se modificará en su lugar. Pero es posible que el *resultado* no se ponga en una posición dentro del intervalo [ `first1` + 1, `last1` ).

La complejidad es lineal con, a lo sumo, ( `last1`  -  `first1` ) comparaciones.

### <a name="example"></a>Ejemplo

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Modifying the vector v1 in place
    transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
    cout << "The elements of the vector v1 multiplied by 2 in place gives:"
            << "\n v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using transform to multiply each element by a factor of 5
    transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a><a name="unique"></a>espeficarse

Quita los elementos duplicados adyacentes entre sí en un intervalo especificado.

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo que se va a examinar para la eliminación de duplicados.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo que se va a examinar para la eliminación de duplicados.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante al nuevo final de la secuencia modificada que no contiene duplicados consecutivos, que se dirige a la posición situada una posición después del último elemento no eliminado.

### <a name="remarks"></a>Observaciones

Ambas formas del algoritmo quitan el segundo duplicado de un par consecutivo de elementos iguales.

La operación de algoritmo es estable, de forma que no se altera el orden relativo de los elementos no borrados.

El intervalo al que se hace referencia debe ser válido; todos los punteros se deben poder desreferenciar y, dentro de la secuencia, se debe poder llegar a la última posición desde la primera mediante incrementos. el algoritmo no cambia el número de elementos de la secuencia `unique` y los elementos que van más allá del final de la secuencia modificada son desreferenciables pero no se especifican.

La complejidad es lineal, lo que requiere `(last - first) - 1` comparaciones.

List proporciona una función miembro "unique" más eficaz que puede funcionar mejor.

Estos algoritmos no se puede usar en un contenedor asociativo.

### <a name="example"></a>Ejemplo

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main()
{
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
            v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
    {
        v1.push_back( 4 );
    }
    v1.push_back( 7 );

    cout << "Vector v1 is ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates
    v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

    cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

    cout << "Removing adjacent duplicates from vector v1 under the\n "
            << " binary predicate mod_equal gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;

    // Remove elements if preceded by an element that was greater
    v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

    cout << "Removing adjacent elements satisfying the binary\n "
            << " predicate mod_equal from vector v1 gives ( " ;
    for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
        cout << *v1_Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a><a name="unique_copy"></a>unique_copy

Copia los elementos de un intervalo de origen a un intervalo de destino salvo los elementos duplicados que son adyacentes entre sí.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>Parámetros

*ejec*\
Directiva de ejecución que se va a usar.

*lugar*\
Iterador hacia delante que dirige a la posición del primer elemento del intervalo de origen que se va a copiar.

*guardado*\
Iterador hacia delante que dirige a la posición situada una posición después del último elemento del intervalo de origen que se va a copiar.

*da*\
Iterador de salida que dirige a la posición del primer elemento del intervalo de destino que recibe la copia con duplicados consecutivos quitados.

*pronostica*\
Objeto de función de predicado definido por el usuario que define la condición que se debe cumplir si dos elementos se van a tomar como equivalentes. Un predicado binario toma dos argumentos y devuelve **true** si se cumplen y **false** si no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que dirige a la posición situada una posición después del último elemento del intervalo de destino que va a recibir la copia con duplicados consecutivos quitados.

### <a name="remarks"></a>Observaciones

Ambas formas del algoritmo quitan el segundo duplicado de un par consecutivo de elementos iguales.

La operación de algoritmo es estable, de forma que no se altera el orden relativo de los elementos no borrados.

Los intervalos a los que se hace referencia deben ser válidos: todos los punteros deben poder desreferenciarse y, dentro de una secuencia, se debe poder tener acceso a la última posición desde la primera con incrementos.

La complejidad es lineal, lo que requiere `last`  -  `first` comparaciones ().

### <a name="example"></a>Ejemplo

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main() {
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
            v1_NewEnd1, v1_NewEnd2;

    int i;
    for ( i = 0 ; i <= 1 ; i++ ) {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
        v1.push_back( 4 );
    v1.push_back( 7 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 10 );

    cout << "Vector v1 is\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Copy first half to second, removing consecutive duplicates
    v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

    cout << "Copying the first half of the vector to the second half\n "
            << "while removing adjacent duplicates gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    int iv;
    for ( iv = 0 ; iv <= 7 ; iv++ )
        v1.push_back( 10 );

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
        v1.begin( ) + 14 , mod_equal );

    cout << "Copying the first half of the vector to the second half\n "
            << " removing adjacent duplicates under mod_equals gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="upper_bound"></a><a name="upper_bound"></a>upper_bound

Busca la posición del primer elemento de un intervalo ordenado que tiene un valor mayor que un valor especificado, donde el criterio de ordenación se puede especificar mediante un predicado binario.

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>Parámetros

*lugar*\
Posición del primer elemento del intervalo en el que se va a buscar.

*guardado*\
Posición situada una posición después del último elemento del intervalo en el que se va a buscar.

*valor*\
Valor del intervalo ordenado que debe ser superado por el valor del elemento al que se dirige el iterador devuelto.

*pronostica*\
Objeto de función de predicado de comparación definido por el usuario que define el sentido en el que un elemento es menor que otro. Un predicado de comparación toma dos argumentos y devuelve **true** si se cumplen y **false** cuando no se cumplen.

### <a name="return-value"></a>Valor devuelto

Iterador hacia delante a la posición del primer elemento que tiene un valor mayor que uno especificado.

### <a name="remarks"></a>Observaciones

El intervalo de origen ordenado al que se hace referencia debe ser válido; todos los iteradores deben poder desreferenciarse y, dentro de la secuencia, la última posición debe ser accesible desde la primera mediante incrementos.

Un intervalo ordenado es una condición previa al uso de `upper_bound` y donde el criterio de ordenación es el mismo que el especificado por el predicado de comparación.

`upper_bound` no modifica el intervalo.

Los tipos de valor de los iteradores hacia delante tienen que ser comparables con menor que para poder ordenarse, de modo que, dados dos elementos, se pueda determinar que son equivalentes (en el sentido de que ninguno es menor que el otro) o que uno es menor que el otro. Esto produce una ordenación entre los elementos no equivalentes.

La complejidad del algoritmo es logarítmica para los iteradores de acceso aleatorio y lineal en caso contrario, con el número de pasos proporcionales a ( `last - first` ).

### <a name="example"></a>Ejemplo

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
