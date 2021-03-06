---
title: Funciones &lt;numeric&gt;
description: Describe las plantillas de función proporcionadas por el &lt;encabezado numérico&gt;C++ en la biblioteca estándar.
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425368"
---
# <a name="ltnumericgt-functions"></a>Funciones &lt;numeric&gt;

## <a name="accumulate"></a>acumular

Calcula la suma de todos los elementos de un intervalo especificado, incluido algún valor inicial, mediante el cálculo de sumas parciales sucesivas. O calcula el resultado de los resultados parciales sucesivos de una operación binaria especificada.

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

### <a name="return-value"></a>Valor devuelto

La suma de *init* y todos los elementos del intervalo especificado para la primera función de plantilla, o, para la segunda función de plantilla, el resultado de aplicar la operación binaria *binary_op* en lugar de la operación SUM, a (* PartialResult, *in_iter*), donde *PartialResult* es el resultado de las aplicaciones anteriores de la operación y *in_iter* es un iterador que apunta al siguiente elemento del intervalo.

### <a name="remarks"></a>Observaciones

El valor inicial garantiza que haya un resultado bien definido cuando el intervalo esté vacío, en cuyo caso se devuelve *init* . No es necesario que la operación binaria sea asociativa o conmutativa. El resultado se inicializa en el valor inicial *init* y, a continuación, el *resultado* = *binary_op*(*result*, *in_iter*) se calcula de forma iterativa a través del intervalo, donde *in_iter* es un iterador que apunta a cada elemento sucesivo del intervalo. El intervalo debe ser válido y la complejidad es lineal con el tamaño del intervalo. El tipo devuelto del operador binario debe ser convertible a **Type** para garantizar el cierre durante la iteración.

### <a name="example"></a>Ejemplo

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada. Envía los resultados a un intervalo de destino. O calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.

*última*\
Iterador de entrada que direcciona el último elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de diferencias o los resultados de la operación especificada.

*binary_op*\
Operación binaria que se va a aplicar en la operación generalizada, reemplazando la operación de resta en el procedimiento de diferenciación.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona el final del intervalo de destino: `result` + (`last` - `first`).

### <a name="remarks"></a>Observaciones

El *resultado* del iterador de salida puede ser el mismo iterador que el iterador de entrada en *primer lugar*, de modo que los valores de `adjacent_difference` se puedan calcular en contexto.

Para una secuencia de valores *a*1, *a*2, *a*3, en un intervalo de entrada, la primera función de plantilla almacena los valores de `adjacent_difference` sucesivos *a*1, *a*2- *a*1, a3- *a*2, en el intervalo de destino.

En el caso de una secuencia de valores *a*1, *a*2, *a*3, en un intervalo de entrada, la segunda función de plantilla almacena los valores *de*`adjacent_difference` sucesivos 1, *a*2 *binary_op* *a*1, *a*3 *binary_op* *2,* en el intervalo de destino.

No es necesario que la operación binaria *binary_op* sea asociativa o conmutativa, ya que se especifica el orden de las operaciones aplicadas.

### <a name="example"></a>Ejemplo

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

Calcula una operación de suma de prefijo exclusiva mediante `std::plus<>()` o un operador binario especificado en un intervalo, dado un valor inicial. Escribe los resultados en el intervalo que comienza en el destino especificado. Una suma de *prefijo exclusiva* significa que el elemento de entrada *n*no se incluye en la suma *n*. Las sobrecargas que incluyen un argumento de directiva de ejecución se ejecutan de acuerdo con la Directiva especificada.

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona el final del intervalo de destino: *result* + (*último* - *primero*).

## <a name="gcd"></a>d

Calcula el máximo común divisor de los enteros m y n.

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>Parámetros

*m*, *n*\
Valores de tipo entero.

### <a name="return-value"></a>Valor devuelto

Devuelve el máximo común divisor de los valores absolutos de *m* y *n*, o cero si *m* y *n* son cero. Los resultados son indefinidos si los valores absolutos de *m* o *n* no se pueden representar como valores de tipo `common_type_t<M,N>`.

## <a name="inclusive_scan"></a>inclusive_scan

Calcula una operación de suma de prefijo inclusiva utilizando `std::plus<>()` o un operador binario especificado en un intervalo, dado un valor inicial. Escribe los resultados en el intervalo que comienza en el destino especificado. Una suma de *prefijo inclusiva* significa que el elemento de entrada *n*se incluye en la suma *n*. Las sobrecargas que incluyen un argumento de directiva de ejecución se ejecutan de acuerdo con la Directiva especificada.

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona el final del intervalo de destino: *result* + (*último* - *primero*).

## <a name="inner_product"></a>inner_product

Calcula la suma del producto de elementos de dos intervalos y la agrega a un valor inicial especificado, o calcula el resultado de un procedimiento general donde las operaciones binarias de suma y de producto se reemplazan por otras operaciones binarias especificadas.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>Parámetros

\ *first1*
Un iterador de entrada que direcciona el primer elemento del primer intervalo cuyo producto interno o producto interno generalizado debe calcularse con el segundo intervalo.

\ *last1*
Un iterador de entrada que direcciona el último elemento del primer intervalo cuyo producto interno o producto interno generalizado con el segundo intervalo debe calcularse.

\ *first2*
Un iterador de entrada que direcciona el primer elemento del segundo intervalo cuyo producto interno o producto interno generalizado con el primer intervalo debe calcularse.

\ *init*
Un valor inicial al que se va a agregar el producto interno o el producto interno generalizado entre los intervalos.

*binary_op1*\
La operación binaria que reemplaza la operación de producto interno de suma que se aplica a los productos de elementos en la generalización del producto interno.

*binary_op2*\
La operación binaria que reemplaza la operación de elementos de producto interno de multiplicar en la generalización del producto interno.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la suma de los productos de elementos y la agrega al valor inicial especificado. Por lo que para los intervalos de valores *a*i y *b*i, devuelve:

*init* + (*a*1 \* *b*1) + (*a*2 \* *b*2) +... + (*a*n \* *b*n)

reemplazando de forma iterativa *init* por *init* + (*a*i \* *b*i).

La segunda función miembro devuelve:

*init* *binary_op1* init (*a*1 *binary_op2* *b*1) *binary_op1* (*a*2 *binary_op2* *b*2) *binary_op1* ... *binary_op1* (*a*n *binary_op2* *b*n)

reemplazando de forma iterativa *init* por *init* *binary_op1* (*a*i *binary_op2* *b*i).

### <a name="remarks"></a>Observaciones

El valor inicial garantiza que hay un resultado bien definido cuando el intervalo está vacío. En ese caso, se devuelve *init* . No es necesario que las operaciones binarias sean asociativas o conmutativas. El intervalo debe ser válido y la complejidad es lineal con el tamaño del intervalo. El tipo devuelto del operador binario debe ser convertible a **Type** para garantizar el cierre durante la iteración.

### <a name="example"></a>Ejemplo

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>Iota

Almacena un valor inicial, empezando por el primer elemento y rellenando con incrementos sucesivos de ese valor (`value++`) en cada uno de los elementos del intervalo `[first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Parámetros

*primer*\
Un iterador de entrada que direcciona el primer elemento del intervalo que se va a rellenar.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo que se va a rellenar.

*value*\
Valor inicial que se va a almacenar en el primer elemento y que se va a incrementar sucesivamente para los elementos posteriores.

### <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestran algunos usos de la función `iota` rellenando una [lista](../standard-library/list.md) de enteros y, después, rellenando un [vector](../standard-library/vector.md) con `list`, de manera que pueda usarse la función [random_shuffle](../standard-library/algorithm-functions.md#random_shuffle).

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>LCM

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

Calcula una serie de sumas en un intervalo de entrada desde el primer elemento hasta el elemento *n*y almacena el resultado de cada una de esas sumas en el elemento *n*de un intervalo de destino. O calcula el resultado de un procedimiento generalizado donde la operación de suma se reemplaza por otra operación binaria especificada.

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo que se va a sumar parcialmente o combinar según una operación binaria especificada.

*última*\
Iterador de entrada que direcciona el último elemento del intervalo que se va a sumar parcialmente o combinar según una operación binaria especificada que está una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino para almacenar la serie de sumas parciales o los resultados sucesivos de la operación binaria especificada.

*binary_op*\
Operación binaria que se va a aplicar en la operación generalizada, reemplazando la operación de Sum en el procedimiento de suma parcial.

### <a name="return-value"></a>Valor devuelto

Iterador de salida que direcciona el final del intervalo de destino: *result* + (*último* - *primero*).

### <a name="remarks"></a>Observaciones

El *resultado* del iterador de salida puede ser el mismo que *el iterador de entrada, por*lo que se pueden calcular sumas parciales en contexto.

Para una secuencia de valores *a*1, *a*2,... *una*x, en un intervalo de entrada, la primera función de plantilla almacena sumas parciales sucesivas en el intervalo de destino. El elemento *n*viene dado por (*a*1 + *a*2 + *a*3 +... + *a*n).

En el caso de una secuencia de valores *a*1, *a*2, *a*3, en un intervalo de entrada, la segunda función de plantilla almacena los resultados parciales sucesivos en el intervalo de destino. El elemento *n*viene dado por ((... *((1* *binary_op* *a*2) *binary_op* *3)* *binary_op* ...) *binary_op* *n)* .

No es necesario que la operación binaria *binary_op* sea asociativa o conmutativa, ya que se especifica el orden de las operaciones aplicadas.

### <a name="example"></a>Ejemplo

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>reducen

Reduce todos los elementos de un intervalo especificado, posiblemente incluyendo algún valor inicial, calculando las sumas en un orden arbitrario y posiblemente permutado. O bien, reduce el cálculo de los resultados de una operación binaria especificada. Las sobrecargas que incluyen un argumento de directiva de ejecución se ejecutan de acuerdo con la Directiva especificada.

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

### <a name="return-value"></a>Valor devuelto

El resultado de aplicar *binary_op* o `std::plus<>()` a *init* y todos los elementos del intervalo especificado a (* PartialResult, *in_iter*), donde *PartialResult* es el resultado de las aplicaciones anteriores de la operación, y *in_iter* es un iterador que apunta a algún elemento del intervalo. En las sobrecargas que no especifican *init*, el valor *init* utilizado es equivalente a `typename iterator_traits<InputIterator>::value_type{}`.

### <a name="remarks"></a>Observaciones

`reduce` comportamiento no es determinista a menos que *binary_op* sea asociativo y conmutativa. El comportamiento es indefinido si *binary_op* modifica algún elemento o invalida cualquier iterador en el intervalo \[*primero*, *último*], ambos inclusive.

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

Transforma los elementos de un intervalo con un operador unario especificado y, a continuación, calcula una operación de suma de prefijo exclusiva mediante `std::plus<>()` o un operador binario especificado sobre el intervalo, dado un valor inicial. Escribe los resultados en el intervalo que comienza en el destino especificado. Una suma de *prefijo exclusiva* significa que el elemento de entrada *n*no se incluye en la suma *n*. Las sobrecargas que incluyen un argumento de directiva de ejecución se ejecutan de acuerdo con la Directiva especificada. La suma se puede realizar en un orden arbitrario.

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

*unary_op*\
Operación unaria que se va a aplicar a cada elemento del intervalo especificado.

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

Transforma los elementos de un intervalo con un operador unario especificado y, a continuación, calcula una operación de suma de prefijo inclusiva utilizando `std::plus<>()` o un operador binario especificado en el intervalo, dado un valor inicial. Escribe los resultados en el intervalo que comienza en el destino especificado. Una suma de *prefijo inclusiva* significa que el elemento de entrada *n*se incluye en la suma *n*. Las sobrecargas que incluyen un argumento de directiva de ejecución se ejecutan de acuerdo con la Directiva especificada. La suma se puede realizar en un orden arbitrario.

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

*unary_op*\
Operación unaria que se va a aplicar a cada elemento del intervalo especificado.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

## <a name="transform_reduce"></a>transform_reduce

Transforma un intervalo de elementos y, a continuación, aplica un functor que reduce los elementos transformados en orden arbitrario. De hecho, un `transform` seguido de un `reduce`.

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>Parámetros

\ *exec*
Una directiva de ejecución.

*primer*\
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op*.

\ *first1*
Iterador de entrada que direcciona el primer elemento del intervalo a SUM o combine mediante *binary_op1*.

*última*\
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ *last1*
Un iterador de entrada que direcciona el último elemento del intervalo a SUM o combine mediante *binary_op1*, es una posición más allá del último elemento incluido realmente en la acumulación iterada.

\ de *resultados*
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas o los resultados de la operación especificada.

\ *init*
Valor inicial al que cada elemento se agrega o combina mediante *binary_op*.

*binary_op*\
Operación binaria que se va a aplicar a cada elemento del intervalo especificado y al resultado de sus aplicaciones anteriores.

*unary_op*\
Operación unaria que se va a aplicar a cada elemento del intervalo especificado.

### <a name="return-value"></a>Valor devuelto

Resultado transformado y reducido.
