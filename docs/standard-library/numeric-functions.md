---
title: Funciones &lt;numeric&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::partial_sum
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::partial_sum [C++]
ms.openlocfilehash: ae1c3e043d35ba91813fb5288e100610986dbd76
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100188"
---
# <a name="ltnumericgt-functions"></a>Funciones &lt;numeric&gt;

||||
|-|-|-|
|[accumulate](#accumulate)|[adjacent_difference](#adjacent_difference)|[inner_product](#inner_product)|
|[iota](#iota)|[partial_sum](#partial_sum)|

## <a name="accumulate"></a> accumulate

Calcula la suma de todos los elementos en un intervalo especificado incluidos algunos valores iniciales mediante el cálculo de sumas parciales sucesivas, o calcula el resultado de los resultados parciales sucesivos obtenidos de manera similar mediante el uso de una operación binaria determinada distinta de la suma.

```cpp
template <class InputIterator, class Type>
Type accumulate(InputIterator first, InputIterator last, Type val);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type val,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Un iterador de entrada que direcciona el primer elemento del intervalo que se va a sumar o combinar según una operación binaria especificada.

*Último*<br/>
Un iterador de entrada que direcciona el último elemento del intervalo que se va a sumar o combinar según una operación binaria especificada que está una posición más allá del último elemento incluido realmente en la acumulación iterada.

*Val*<br/>
Un valor inicial al que, a su vez, cada elemento se agrega o combina según una operación binaria específica.

*binary_op*<br/>
La operación binaria que se va a aplicar en cada elemento del intervalo especificado y el resultado de sus aplicaciones anteriores.

### <a name="return-value"></a>Valor devuelto

La suma de *val* y todos los elementos del intervalo especificado para la primera función de plantilla, o bien, para la segunda función de plantilla, el resultado de aplicar la operación binaria especificada, en lugar de la operación de suma para (  *PartialResult, \*Iter*), donde *PartialResult* es el resultado de las aplicaciones de la operación anteriores y `Iter` es un iterador que apunta a un elemento del intervalo.

### <a name="remarks"></a>Comentarios

El valor inicial garantiza que habrá un resultado bien definido cuando el intervalo está vacío, en cuyo caso *val* se devuelve. La operación binaria no necesita ser asociativa o conmutativa. El resultado se inicializa en el valor inicial *val* y, a continuación, *resultado*  =  `binary_op` ( *resultado*, <strong>\*</strong> `Iter`) se calcula de forma iterativa mediante el rango, donde `Iter` es un iterador que apunta al elemento sucesivo del intervalo. El intervalo debe ser válido y la complejidad es lineal con el tamaño del intervalo. El tipo devuelto del operador binario debe ser convertible a **Type** para garantizar el cierre durante la iteración.

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

## <a name="adjacent_difference"></a> adjacent_difference

Calcula las diferencias sucesivas entre cada elemento y su predecesor en un intervalo de entrada, y pone los resultados en un intervalo de destino; o calcula el resultado de un procedimiento generalizado donde la operación de diferencia se reemplaza por otra operación binaria especificada.

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
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Iterador de entrada que direcciona el primer elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.

*Último*<br/>
Iterador de entrada que direcciona el último elemento del intervalo de entrada cuyos elementos se van a diferenciar con sus predecesores respectivos o donde se va a actuar sobre el par de valores mediante otra operación binaria especificada.

*Resultado*<br/>
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de diferencias o los resultados de la operación especificada.

*binary_op*<br/>
Operación binaria que se va a aplicar en la operación generalizada reemplazando la operación de resta en el procedimiento de diferenciación.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que direcciona al final del intervalo de destino: `result` + ( `last` - `first`).

### <a name="remarks"></a>Comentarios

El iterador de salida _ *resultado* se permite que sea el mismo que el iterador de entrada * primero, * para que `adjacent_difference`s se puedan calcular en su lugar.

Para una secuencia de valores *un*1, *un*2, *un*3, en un intervalo de entrada, la primera función de plantilla almacena sucesivas `partial_difference`s *un*1 , *un*2 - *un*1, a3 - *un*2, en el intervalo de destino.

Para una secuencia de valores *un*1, *un*2, *un*3, en un intervalo de entrada, la segunda función de plantilla almacena sucesivas `partial_difference`s *un* 1, *un*2 `binary_op` *un*1, *un*3 `binary_op` *un*2, en el intervalo de destino.

No es necesario que la operación binaria `binary_op` sea asociativa o conmutativa, ya que el orden en que se aplican las operaciones se especifica completamente.

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

## <a name="inner_product"></a> inner_product

Calcula la suma del producto de elementos de dos intervalos y la agrega a un valor inicial especificado, o calcula el resultado de un procedimiento general donde las operaciones binarias de suma y de producto se reemplazan por otras operaciones binarias especificadas.

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             val,
    BinaryOperation1  binary_op1,
    BinaryOperation2  binary_op2);
```

### <a name="parameters"></a>Parámetros

*first1*<br/>
Un iterador de entrada que direcciona el primer elemento del primer intervalo cuyo producto interno o producto interno generalizado debe calcularse con el segundo intervalo.

*last1*<br/>
Un iterador de entrada que direcciona el último elemento del primer intervalo cuyo producto interno o producto interno generalizado con el segundo intervalo debe calcularse.

*first2*<br/>
Un iterador de entrada que direcciona el primer elemento del segundo intervalo cuyo producto interno o producto interno generalizado con el primer intervalo debe calcularse.

*Val*<br/>
Un valor inicial al que se va a agregar el producto interno o el producto interno generalizado entre los intervalos.

*binary_op1*<br/>
La operación binaria que reemplaza la operación de producto interno de suma que se aplica a los productos de elementos en la generalización del producto interno.

*binary_op2*<br/>
La operación binaria que reemplaza la operación de elementos de producto interno de multiplicar en la generalización del producto interno.

### <a name="return-value"></a>Valor devuelto

La primera función miembro devuelve la suma de los productos de elementos y la agrega al valor inicial especificado. Por lo que para los intervalos de valores *a*i y *b*i, devuelve:

`val` + ( *un*1 \* *b*1) + ( *un*2 \* *b*2) +... + ( *un*n \* *b*n)

reemplazando de manera iterativa *val* con `val` + ( *un* \* *b*).

La segunda función miembro devuelve:

`val` *binary_op1* ( *un*1 *binary_op2* *b*1) *binary_op1* ( *un*2 *binary_op2* *b*2) *binary_op1* ... *binary_op1* ( *un*n *binary_op2* *b*n)

reemplazando de manera iterativa *val* con `val` *binary_op1* ( *un* *binary_op2* *b* i).

### <a name="remarks"></a>Comentarios

El valor inicial garantiza que habrá un resultado bien definido cuando el intervalo está vacío, en cuyo caso *val* se devuelve. Las operaciones binarias no necesitan ser asociativas ni conmutativas. El intervalo debe ser válido y la complejidad es lineal con el tamaño del intervalo. El tipo devuelto del operador binario debe ser convertible a **Type** para garantizar el cierre durante la iteración.

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

## <a name="iota"></a> iota

Almacena un valor inicial, empezando por el primer elemento y rellenando con incrementos sucesivos de ese valor (` value++`) en cada uno de los elementos en el intervalo `[ first,  last)`.

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>Parámetros

*first*<br/>
Un iterador de entrada que direcciona el primer elemento del intervalo que se va a rellenar.

*Último*<br/>
Un iterador de entrada que direcciona el último elemento del intervalo que se va a rellenar.

*valor*<br/>
El valor inicial para almacenar en el primer elemento y para incrementar sucesivamente los elementos posteriores.

### <a name="remarks"></a>Comentarios

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

## <a name="partial_sum"></a> partial_sum

Calcula una serie de sumas en un intervalo de entrada desde el primer elemento hasta el elemento *i*-ésimo y almacena el resultado de cada una de esas sumas en el elemento *i*-ésimo de un intervalo de destino o calcula el resultado de un procedimiento generalizado donde la operación de suma se reemplaza por otra operación binaria especificada.

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

*first*<br/>
Iterador de entrada que direcciona el primer elemento del intervalo que se va a sumar parcialmente o combinar según una operación binaria especificada.

*Último*<br/>
Iterador de entrada que direcciona el último elemento del intervalo que se va a sumar parcialmente o combinar según una operación binaria especificada que está una posición más allá del último elemento incluido realmente en la acumulación iterada.

*Resultado*<br/>
Iterador de salida que direcciona el primer elemento de un intervalo de destino donde se va a almacenar la serie de sumas parciales o los resultados de la operación especificada.

*binary_op*<br/>
Operación binaria que se va a aplicar en la operación generalizada reemplazando la operación de suma en el procedimiento de suma parcial.

### <a name="return-value"></a>Valor devuelto

Un iterador de salida que direcciona al final del intervalo de destino: `result` + (`last` - `first`),

### <a name="remarks"></a>Comentarios

El iterador de salida *resultado* se permite que sea el mismo que el iterador de entrada *primera*, de modo que se puedan calcular sumas parciales en su lugar.

Para una secuencia de valores *a*1, *a*2, *a*3 de un intervalo de entrada, la primera función de plantilla almacena sumas parciales sucesivas en el intervalo de destino, donde el elemento *i*-ésimo viene dado por (  ( ( *a*1 + *a*2) + *a*3) *a*i).

Para una secuencia de valores *un*1, *un*2, *un*3, en un intervalo de entrada, la segunda función de plantilla almacena sumas parciales sucesivas en el intervalo de destino, donde el elemento i-ésimo es determinado por ((( *un*1 `binary_op` *un* (2)`binary_op` *un* (3)*un*).

La operación binaria *binary_op* no debe ser asociativa o conmutativa, ya que se aplica el orden de las operaciones se especifica completamente.

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

## <a name="see-also"></a>Vea también

[\<numeric>](../standard-library/numeric.md)<br/>
