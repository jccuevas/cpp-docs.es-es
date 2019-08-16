---
title: Operadores de &lt;valarray&gt;
ms.date: 03/27/2019
f1_keywords:
- valarray/std::operator!=
- valarray/std::operator%
- valarray/std::operator&amp;
- valarray/std::operator&amp;&amp;
- valarray/std::operator&gt;
- valarray/std::operator&gt;&gt;
- valarray/std::operator&gt;=
- valarray/std::operator&lt;
- valarray/std::operator&lt;&lt;
- valarray/std::operator&lt;=
- valarray/std::operator*
- valarray/std::operator+
- valarray/std::operator-
- valarray/std::operator/
- valarray/std::operator==
- valarray/std::operator^
- valarray/std::operator|
- valarray/std::operator||
ms.assetid: 8a53562c-90ab-4eb3-85d3-ada5259d90b0
helpviewer_keywords:
- std::operator!= (valarray), std::operator&amp; (valarray)
- std::operator&amp;&amp; (valarray)
- std::operator&gt; (valarray)
- std::operator&gt;&gt; (valarray)
- std::operator&gt;= (valarray)
- std::operator&lt; (valarray)
- std::operator&lt;&lt; (valarray)
- std::operator&lt;= (valarray), std::operator== (valarray)
ms.openlocfilehash: 231bad65e2af1ee2ab800890c83cc50e584a8c6a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246109"
---
# <a name="ltvalarraygt-operators"></a>Operadores de &lt;valarray&gt;

## <a name="op_neq"></a> operador! =

Comprueba si los elementos correspondientes de dos valarray de igual tamaño no son iguales o si todos los elementos de una valarray no son iguales a un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator!=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator!=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a probar para desigualdad.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a probar para desigualdad.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **true** si los elementos correspondientes no son iguales.

- **false** si los elementos correspondientes son iguales.

### <a name="remarks"></a>Comentarios

El primer operador de plantilla devuelve un objeto de clase [valarray\<bool >](../standard-library/valarray-bool-class.md), cuyos elementos `I` es `left[I] != right[I]`.

El segundo operador de plantilla almacena en el elemento `I` `left[I] != right`.

El tercer operador de plantilla almacena en el elemento `I` `left != right[I]`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_ne.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL != vaR );
   cout << "The element-by-element result of "
        << "the not equal comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the not equal comparison test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_mod"></a> operator %

Obtiene el resto de dividir los elementos correspondientes de dos valarray de igual tamaño o de dividir una valarray por un valor especificado o de dividir un valor especificado por una valarray.

```cpp
template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator%(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator%(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un valor o valarray que actúa como el dividendo en el que se va a dividir otro valor o valarray.

*Correcto*\
Un valor o valarray que actúa como el divisor y que divide otro valor o valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son los restos por elemento de *izquierdo* dividido por *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   valarray<int> vaREM ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaREM = ( vaL % vaR );
   cout << "The remainders from the element-by-element "
        << "division is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaREM [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 53 -67 53 -67 53 -67 ).
The initial Right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
valarray: ( 0 -3 4 -7 1 -3 ).
```

## <a name="op_amp"></a> operator&amp;

Obtiene el **AND** bit a bit entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.

```cpp
template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos respectivos van a combinarse con el `AND` bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos respectivos van a combinarse con el `AND` bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la combinación por elemento de la operación AND bit a bit de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **longdouble**, **void**, **bool** u otros tipos de datos más complejos.

El `AND` bit a bit tiene la misma tabla de verdad que el `AND` lógico pero se aplica al tipo de datos en el nivel de los bits individuales. El [operator&&](#op_amp_amp) se aplica en el nivel de elemento, contando todos los valores distintos de cero como true, y el resultado es una valarray de valores booleanos. Bit a bit `AND` [operador &](#op_amp), por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaBWA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i+1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaBWA = ( vaL & vaR );
   cout << "The element-by-element result of "
        << "the bitwise operator & is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaBWA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 2 0 4 0 6 0 8 0 10 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the bitwise operator & is the
valarray: ( 0 0 0 0 0 4 0 0 0 8 ).
```

## <a name="op_amp_amp"></a> Operador&amp;&amp;

Obtiene el **AND** lógico entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.

```cpp
template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator&&(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator&&(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos respectivos van a combinarse con el `AND` lógico o un valor especificado del tipo de elemento que va a combinarse con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos respectivos van a combinarse con el `AND` lógico o un valor especificado del tipo de elemento que va a combinarse con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son de tipo bool y son la combinación por elemento de la operación lógica `AND` la operación de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

La operación lógica `ANDoperator&&` se aplica en el nivel de elemento, contando todos los valores distintos de cero como true y el resultado es una valarray de valores booleanos. La versión bit a bit de `AND`, [operador &,](#op_amp), por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_logand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL && vaR );
   cout << "The element-by-element result of "
        << "the logical AND operator&& is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&& is the
valarray: ( 0 0 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt"></a> operator&gt;

Comprueba si los elementos de una valarray son mayores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **True** si el *izquierdo* es mayor que el correspondiente elemento o valor *derecho* elemento o valor.

- **false** si el *izquierdo* elemento o valor no es mayor que el correspondiente *derecho* elemento o valor.

### <a name="remarks"></a>Comentarios

Si el número de elementos de dos valarray no es igual, el resultado es indefinido.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_gt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL > vaR );
   cout << "The element-by-element result of "
        << "the greater than comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_eq"></a> Operador&gt;=

Comprueba si los elementos de una valarray son mayores o iguales que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o iguales o menores que un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator>=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator>=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **True** si el *izquierdo* elemento o valor es mayor o igual que el correspondiente *derecho* elemento o valor.

- **false** si el *izquierdo* es menor que el correspondiente elemento o valor *derecho* elemento o valor.

### <a name="remarks"></a>Comentarios

Si el número de elementos de dos valarray no es igual, el resultado es indefinido.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_ge.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >= vaR );
   cout << "The element-by-element result of "
        << "the greater than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the greater than or equal test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_gt_gt"></a> Operador&gt;&gt;

Desplaza hacia la derecha los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.

```cpp
template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator>>(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator>>(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
El valor que se va a desplazar o la valarray cuyos elementos se van a desplazar.

*Correcto*\
El valor que indica la cantidad de desplazamiento a la derecha o la valarray cuyos elementos indican la cantidad de desplazamiento a la derecha por elemento.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos se han desplazado a la derecha la cantidad especificada.

### <a name="remarks"></a>Comentarios

Los números con signo conservan sus signos.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL >> vaR );
   cout << "The element-by-element result of "
        << "the right shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
```

## <a name="op_lt"></a> operator&lt;

Comprueba si los elementos de una valarray son menores que los elementos de una valarray de igual tamaño o si todos los elementos de una valarray son mayores o menores que un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **True** si el *izquierdo* es menor que el correspondiente elemento o valor *derecho* elemento o valor.

- **false** si el *izquierdo* elemento o valor no es menor que el correspondiente *derecho* elemento o valor.

### <a name="remarks"></a>Comentarios

Si el número de elementos de dos valarray no es igual, el resultado es indefinido.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_lt.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL < vaR );
   cout << "The element-by-element result of "
        << "the less-than comparson test is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the less-than comparson test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_eq"></a> Operador&lt;=

Comprueba si los elementos de una valarray son menores o iguales que los elementos de una valarray de igual tamaño, o si todos los elementos de una valarray son mayores, iguales o menores que un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator<=(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator<=(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a comparar o un valor especificado que se va a comparar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **True** si el *izquierdo* es menor o igual que el correspondiente elemento o valor *derecho* elemento o valor.

- **false** si el *izquierdo* es mayor que el correspondiente elemento o valor *derecho* elemento o valor.

### <a name="remarks"></a>Comentarios

Si el número de elementos de dos valarray no es igual, el resultado es indefinido.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_le.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i - 1;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL <= vaR );
   cout << "The element-by-element result of "
        << "the less than or equal test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( -1 0 1 2 3 4 5 6 7 8 ).
The element-by-element result of the less than or equal test is the
valarray: ( 0 0 1 0 1 0 1 0 1 0 ).
```

## <a name="op_lt_lt"></a> Operador&lt;&lt;

Desplaza hacia la izquierda los bits de cada elemento de una valarray un número especificado de posiciones o una cantidad de elementos especificada por una segunda valarray.

```cpp
template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator<<(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator<<(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
El valor que se va a desplazar o la valarray cuyos elementos se van a desplazar.

*Correcto*\
El valor que indica la cantidad de desplazamiento a la izquierda o la valarray cuyos elementos indican la cantidad de desplazamiento a la izquierda por elemento.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos se han desplazado a la izquierda la cantidad especificada.

### <a name="remarks"></a>Comentarios

Los números con signo conservan sus signos.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL << vaR );
   cout << "The element-by-element result of "
        << "the left shift is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift is the
valarray: ( 1 -2 4 -8 16 -32 64 -128 ).
```

## <a name="op_star"></a> operador *

Obtiene el producto por elemento entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado.

```cpp
template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator*(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator*(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a multiplicar o un valor especificado que se va a multiplicar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a multiplicar o un valor especificado que se va a multiplicar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el producto por elemento de *izquierdo* y *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_eprod.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL * vaR );
   cout << "The element-by-element result of "
        << "the multiplication is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
```

## <a name="op_add"></a> operator +

Obtiene la suma por elemento entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado.

```cpp
template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator+(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator+(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a sumar o un valor especificado que se va a sumar con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a sumar o un valor especificado que se va a sumar con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la suma por elemento de *izquierdo* y *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_esum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL + vaR );
   cout << "The element-by-element result of "
        << "the sum is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
valarray: ( 2 0 4 2 6 4 8 6 ).
```

## <a name="operator-"></a> operator-

Obtiene la diferencia por elemento entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado.

```cpp
template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator-(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator-(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un valor o valarray que actúa como el minuendo desde el que otros valores o valarray se van a restar para formar la diferencia.

*Correcto*\
Un valor o valarray que actúa como sustraendo que se va a restar de otros valores o valarray para formar la diferencia.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la diferencia por elemento de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

La terminología aritmética usada para describir una resta:

diferencia = minuendo - sustraendo

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_ediff.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   valarray<int> vaNE ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL - vaR );
   cout << "The element-by-element result of "
        << "the difference is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
```

## <a name="op_div"></a> operador /

Obtiene el cociente por elemento entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado.

```cpp
template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator/(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator/(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Un valor o valarray que actúa como el dividendo en el que se va a dividir otro valor o valarray para formar el cociente.

*Correcto*\
Un valor o valarray que actúa como el divisor y que divide otro valor o valarray para formar el cociente.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el cociente por elemento de *izquierdo* dividido por *derecho*.

### <a name="remarks"></a>Comentarios

La terminología aritmética usada para describir una división:

cociente = dividendo / divisor

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_equo.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   valarray<double> vaNE ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial Left valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL / vaR );
   cout << "The element-by-element result of "
        << "the quotient is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
valarray: ( inf -50 25 -16.6667 12.5 -10 ).
```

## <a name="op_eq_eq"></a> operador ==

Comprueba si los elementos correspondientes de dos valarray de igual tamaño son iguales o si todos los elementos de una valarray son iguales a un valor especificado.

```cpp
template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator==(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator==(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos se van a probar para igualdad.

*Correcto*\
La segunda de las dos valarray cuyos elementos se van a probar para igualdad.

### <a name="return-value"></a>Valor devuelto

Una valarray de valores booleanos, en la que cada uno es:

- **true** si los elementos correspondientes son iguales.

- **false** si los elementos correspondientes no son iguales.

### <a name="remarks"></a>Comentarios

El primer operador de plantilla devuelve un objeto de clase [valarray\<bool >](../standard-library/valarray-bool-class.md), cuyos elementos `I` es `left[I] == right[I]`. El segundo operador de plantilla almacena en el elemento `I` `left[I] == right`. El tercer operador de plantilla almacena en el elemento `I` `left == right[I]`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_eq.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaNE ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial Left valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaNE = ( vaL == vaR );
   cout << "The element-by-element result of "
        << "the equality comparison test is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNE [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is: ( 0 1 -2 3 -4 5 -6 7 -8 9 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the equality comparison test is the
valarray: ( 1 1 0 1 0 1 0 1 0 1 ).
```

## <a name="op_xor"></a> operador ^

Obtiene el `OR` exclusivo bit a bit ( **XOR**) entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.

```cpp
template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator^(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator^(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos respectivos van a combinarse con el **XOR** bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos respectivos van a combinarse con el **XOR** bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la combinación por elemento de bit a bit **XOR** la operación de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **long double**, **void**, **bool** u otros tipos de datos más complejos.

El exclusivo bit a bit `OR` ( **XOR**) tiene la semántica siguiente: Dados los bits *b*1 y *b*2, *b*1 **XOR** *b*2 es **true** si exactamente uno de los bits es true; **false** si ambos bits son falsas o si ambos bits son true.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_xor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL ^ vaR );
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^ is the\n"
        << "valarray: ( ";
           for ( i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^ is the
valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
```

## <a name="op_or"></a> operador&#124;

Obtiene el `OR` bit a bit entre los elementos correspondientes de dos valarrays de igual tamaño o entre una valarray y un valor especificado del tipo de elemento.

```cpp
template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<Type>
operator|(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<Type>
operator|(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos respectivos van a combinarse con el `OR` bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos respectivos van a combinarse con el `OR` bit a bit o un valor especificado del tipo de elemento que va a combinarse bit a bit con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la combinación por elemento de bit a bit `OR` la operación de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **longdouble**, **void**, **bool** u otros tipos de datos más complejos.

El OR bit a bit tiene la misma tabla de verdad que el `OR` lógico pero se aplica al tipo de datos en el nivel de los bits individuales. Dados los bits *b*1 y *b*2, *b*1 `OR` *b*2 es **true** si al menos uno de los bits es true o **false** si los dos bits son false. El `OR`[operador&#124;&#124;](../standard-library/valarray-operators.md#op_lor) lógico se aplica en el nivel de elemento, contando todos los valores distintos de cero como **true**, y el resultado es una valarray de valores booleanos. El `operator|` OR bit a bit, por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<int> vaLAA ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  i-1;

   cout << "The initial Left valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLAA = ( vaL | vaR );
   cout << "The element-by-element result of "
        << "the bitwise OR operator| is the\n"
        << "valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaLAA [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The initial Right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise OR operator| is the
valarray: ( 1 0 1 3 3 4 7 6 7 9 ).
```

## <a name="op_lor"></a> operador&#124;&#124;

Obtiene el `OR` lógico entre los elementos correspondientes de dos valarray de igual tamaño o entre una valarray y un valor especificado del tipo de elemento de valarray.

```cpp
template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const valarray<Type>& right);

template <class Type>
valarray<bool>
operator||(
    const valarray<Type>& left,
    const Type& right);

template <class Type>
valarray<bool>
operator||(
    const Type& left,
    const valarray<Type>& right);
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
La primera de las dos valarray cuyos elementos respectivos van a combinarse con el `OR` lógico o un valor especificado del tipo de elemento que va a combinarse con cada elemento de una valarray.

*Correcto*\
La segunda de las dos valarray cuyos elementos respectivos van a combinarse con el `OR` lógico o un valor especificado del tipo de elemento que va a combinarse con cada elemento de una valarray.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son de tipo **bool** y son la combinación por elemento de la operación OR lógica de *izquierdo* y *derecho*.

### <a name="remarks"></a>Comentarios

La operación lógica `OR` `operator||` se aplica en el nivel de elemento, contando todos los valores distintos de cero como **true**, y el resultado es una valarray de valores booleanos. La versión bit a bit de `OR`, [operator&#124;](../standard-library/valarray-operators.md#op_or), por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_logor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   valarray<bool> vaLOR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  0;

   cout << "The initial Left valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaLOR = ( vaL || vaR );
   cout << "The element-by-element result of "
        << "the logical OR operator|| is the\n"
        << "valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaLOR [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The initial Left valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 0 0 3 0 0 6 0 0 9 ).
The element-by-element result of the logical OR operator|| is the
valarray: ( 0 0 0 1 0 1 1 1 0 1 ).
```
