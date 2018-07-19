---
title: valarray (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- valarray/std::valarray
- valarray/std::valarray::value_type
- valarray/std::valarray::apply
- valarray/std::valarray::cshift
- valarray/std::valarray::free
- valarray/std::valarray::max
- valarray/std::valarray::min
- valarray/std::valarray::resize
- valarray/std::valarray::shift
- valarray/std::valarray::size
- valarray/std::valarray::sum
- valarray/std::valarray::swap
dev_langs:
- C++
helpviewer_keywords:
- std::valarray [C++]
- std::valarray [C++], value_type
- std::valarray [C++], apply
- std::valarray [C++], cshift
- std::valarray [C++], free
- std::valarray [C++], max
- std::valarray [C++], min
- std::valarray [C++], resize
- std::valarray [C++], shift
- std::valarray [C++], size
- std::valarray [C++], sum
- std::valarray [C++], swap
ms.assetid: 19b862f9-5d09-4003-8844-6ddd02c1a3a7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0521d09f4f96c73c20022d88621671564e7ada78
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965531"
---
# <a name="valarray-class"></a>valarray (Clase)

La clase de plantilla describe un objeto que controla una secuencia de elementos de tipo `Type` que se almacenan como una matriz, diseñado para realizar operaciones matemáticas de alta velocidad y optimizado para ofrecer un alto rendimiento.

## <a name="remarks"></a>Comentarios

La clase es una representación del concepto matemático de un conjunto ordenado de valores y los elementos se numeran secuencialmente a partir de cero. La clase se describe como un pseudocontenedor porque es compatible con algunas de las funciones que admiten los contenedores de secuencias de primera clase, como [vector](../standard-library/vector-class.md), pero no con todas ellas. Difiere del vector de clase de plantilla en dos aspectos importantes:

- Define muchas operaciones aritméticas entre los elementos correspondientes de `valarray<Type>` objetos del mismo tipo y longitud, como *xarr* = cos ( *yarr*) + sin ( *zarr*).

- Define una variedad de formas interesantes de subíndice un `valarray<Type>` objeto mediante la sobrecarga de [operador&#91;&#93;](#op_at).

Un objeto de clase `Type`:

- Tiene un constructor público predeterminado, un destructor, un constructor de copias y un operador de asignación, con un comportamiento convencional.

- Define, en la medida que sean necesarios, los operadores aritméticos y las funciones matemáticas que se definen para los tipos de punto flotante con un comportamiento convencional.

En concreto, no pueden existir diferencias sutiles entre la construcción de la copia y la construcción predeterminada seguida por una asignación. Ninguna de las operaciones en objetos de clase `Type` pueden producir excepciones.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[valarray](#valarray)|Construye una `valarray` de un tamaño específico o con elementos de un valor determinado, o como una copia de otra `valarray` o un subconjunto de otra `valarray`.|

### <a name="typedefs"></a>Typedefs

|Nombre de tipo|Descripción|
|-|-|
|[value_type](#value_type)|Tipo que representa el tipo de elemento almacenado en una `valarray`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[apply](#apply)|Aplica una función especificada a cada elemento de una `valarray`.|
|[cshift](#cshift)|Desplaza de forma cíclica todos los elementos de una `valarray` un número especificado de posiciones.|
|[free](#free)|Libera la memoria usada por la `valarray`.|
|[max](#max)|Busca el elemento más grande en una `valarray`.|
|[min](#min)|Busca el elemento más pequeño en una `valarray`.|
|[resize](#resize)|Cambia el número de elementos de una `valarray` por un número especificado, agregando o quitando elementos según sea necesario.|
|[shift](#shift)|Desplaza todos los elementos de una `valarray` un número especificado de posiciones.|
|[size](#size)|Busca el número de elementos de una `valarray`.|
|[sum](#sum)|Determina la suma de todos los elementos de una `valarray` de longitud distinta de cero.|
|[swap](#swap)||

### <a name="operators"></a>Operadores

|Operador|Descripción|
|-|-|
|[operator!](#op_not)|Operador unario que obtiene los valores `NOT` lógicos de cada elemento de una `valarray`.|
|[operator%=](#op_mod_eq)|Obtiene el resto de la división de los elementos de una matriz uno a uno por una `valarray` especificada o por un valor del tipo de elemento.|
|[operator&=](#op_amp_eq)|Obtiene el `AND` bit a bit de los elementos de una matriz con los elementos correspondientes de una `valarray` especificada o con un valor del tipo de elemento.|
|[operator>>=](#op_gt_gt_eq)|Desplaza hacia la derecha los bits de cada elemento de un operando `valarray` un número especificado de posiciones o una cantidad de elementos especificada por una segunda `valarray`.|
|[operator<<=](#op_lt_lt_eq)|Desplaza hacia la izquierda los bits de cada elemento de un operando `valarray` un número especificado de posiciones o una cantidad de elementos especificada por una segunda `valarray`.|
|[operator*=](#op_star_eq)|Multiplica los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, por un operando `valarray`.|
|[operator+](#op_add)|Operador unario que aplica un signo más a cada elemento de una `valarray`.|
|[operator+=](#op_add_eq)|Suma los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, a un operando `valarray`.|
|[operator-](#operator-)|Operador unario que aplica un signo menos a cada elemento de una `valarray`.|
|[operator-=](#operator-_eq)|Resta los elementos de una `valarray` especificada o un valor del tipo de elemento, uno a uno, de un operando `valarray`.|
|[operator/=](#op_div_eq)|Divide un operando `valarray` elemento a elemento por los elementos de una `valarray` especificada o un valor del tipo de elemento.|
|[operator=](#op_eq)|Asigna los elementos a una `valarray` cuyos valores se especifican directamente o como parte de otra `valarray` o mediante una `slice_array`, `gslice_array`, `mask_array` o `indirect_array`.|
|[operator&#91;&#93;](#op_at)|Devuelve una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.|
|[operator^=](#op_xor_eq)|Obtiene el operador OR exclusivo lógico ( `XOR`) por elemento de una matriz con una valarray especificada o un valor del tipo de elemento.|
|[operator&#124;=](#op_or_eq)|Obtiene el `OR` bit a bit de los elementos de una matriz con los elementos correspondientes de una `valarray` especificada o con un valor del tipo de elemento.|
|[operator~](#op_dtor)|Operador unario que obtiene los valores `NOT` bit a bit de cada elemento de una `valarray`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="apply"></a>  valarray::apply

Aplica una función especificada a cada elemento de una valarray.

```cpp
valarray<Type> apply(Type _Func(Type)) const;

valarray<Type> apply(Type _Func(constType&)) const;
```

### <a name="parameters"></a>Parámetros

*_Func(Type)* el objeto de función que se aplicará a cada elemento de la valarray de operando.

*_Func(const Type&)* el objeto de función para const que se aplicará a cada elemento de la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray a cuyos elementos se ha aplicado `_Func` por elemento a los elementos de la valarray de operando.

### <a name="remarks"></a>Comentarios

La función miembro devuelve un objeto de la clase [valarray](../standard-library/valarray-class.md)**\<Type>** de longitud [size](#size), cuyos elementos `I` son **func**(( **\*this**)[ `I`]).

### <a name="example"></a>Ejemplo

```cpp
// valarray_apply.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

using namespace std;

int __cdecl MyApplyFunc( int n )
{
   return n*2;
}

int main( int argc, char* argv[] )
{
   valarray<int> vaR(10), vaApplied(10);
   int i;

   for ( i = 0; i < 10; i += 3 )
      vaR[i] = i;

   for ( i = 1; i < 10; i += 3 )
      vaR[i] = 0;

   for ( i = 2; i < 10; i += 3 )
      vaR[i] = -i;

   cout << "The initial Right valarray is: (";
   for   ( i=0; i < 10; ++i )
      cout << " " << vaR[i];
   cout << " )" << endl;

   vaApplied = vaR.apply( MyApplyFunc );

   cout << "The element-by-element result of "
       << "applying MyApplyFunc to vaR is the\nvalarray: ( ";
   for ( i = 0; i < 10; ++i )
      cout << " " << vaApplied[i];
   cout << " )" << endl;
}
\* Output:
The initial Right valarray is: ( 0 0 -2 3 0 -5 6 0 -8 9 )
The element-by-element result of applying MyApplyFunc to vaR is the
valarray: (  0 0 -4 6 0 -10 12 0 -16 18 )
*\
```

## <a name="cshift"></a>  valarray::cshift

Desplaza de forma cíclica todos los elementos de una valarray en un número especificado de posiciones.

```cpp
valarray<Type> cshift(int count) const;
```

### <a name="parameters"></a>Parámetros

*count*  
 El número de posiciones que se van a desplazar hacia adelante los elementos.

### <a name="return-value"></a>Valor devuelto

Una nueva valarray en la que todos los elementos se han movido *recuento* posiciones cíclicamente hacia la parte delantera de la valarray, a la izquierda con respecto a sus posiciones en la valarray de operando.

### <a name="remarks"></a>Comentarios

Un valor positivo de *recuento* desplaza los elementos cíclicamente a la izquierda *recuento* coloca.

Un valor negativo de *recuento* desplaza los elementos cíclicamente a la derecha *recuento* coloca.

### <a name="example"></a>Ejemplo

```cpp
// valarray_cshift.cpp
// compile with: /EHsc

#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    valarray<int> va1(10), va2(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;
    for (i = 0; i < 10; i+=1)
        va2[i] = 10 - i;

    cout << "The operand valarray va1 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    // A positive parameter shifts elements right
    va1 = va1.cshift(4);
    cout << "The cyclically shifted valarray va1 is:\nva1.cshift (4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va1[i];
    cout << ")" << endl;

    cout << "The operand valarray va2 is: (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;

    // A negative parameter shifts elements left
    va2 = va2.cshift(-4);
    cout << "The cyclically shifted valarray va2 is:\nva2.shift (-4) = (";
    for (i = 0; i < 10; i++)
        cout << " " << va2[i];
    cout << ")" << endl;
}
\* Output:
The operand valarray va1 is: ( 0 1 2 3 4 5 6 7 8 9)
The cyclically shifted valarray va1 is:
va1.cshift (4) = ( 4 5 6 7 8 9 0 1 2 3)
The operand valarray va2 is: ( 10 9 8 7 6 5 4 3 2 1)
The cyclically shifted valarray va2 is:
va2.shift (-4) = ( 4 3 2 1 10 9 8 7 6 5)
*\
```

## <a name="free"></a>  valarray::free

Libera la memoria usada por la valarray.

```cpp
void free();
```

### <a name="remarks"></a>Comentarios

Esta función no estándar es equivalente a asignar una valarray vacía. Por ejemplo:

```cpp
valarray<T> v;
v = valarray<T>();

// equivalent to v.free()
```

## <a name="max"></a>  valarray::max

Busca el elemento más grande en una valarray.

```cpp
Type max() const;
```

### <a name="return-value"></a>Valor devuelto

El valor máximo de los elementos de la valarray de operando.

### <a name="remarks"></a>Comentarios

La función miembro compara valores aplicando **operador\<**  o **operador >** entre pares de elementos de la clase `Type`, para qué operadores se deben proporcionar para el elemento `Type`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_max.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MaxValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i - 1;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  10 - i;

   cout << "The operand valarray is: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MaxValue = vaR.max (  );
   cout << "The largest element in the valarray is: "
        << MaxValue  << "." << endl;
}
\* Output:
The operand valarray is: ( 0 1 8 3 7 5 6 13 2 9 ).
The largest element in the valarray is: 13.
*\
```

## <a name="min"></a>  valarray::min

Busca el elemento más pequeño en una valarray.

```cpp
Type min() const;
```

### <a name="return-value"></a>Valor devuelto

El valor mínimo de los elementos de la valarray de operando.

### <a name="remarks"></a>Comentarios

La función miembro compara valores aplicando **operador\<**  o **operador >** entre pares de elementos de la clase `Type`, para qué operadores se deben proporcionar para el elemento `Type`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_min.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i, MinValue;

   valarray<int> vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 3 )
      vaR [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 3 )
      vaR [ i ] =  2*i;
   for ( i = 2 ; i < 10 ; i += 3 )
      vaR [ i ] =  5 - i;

   cout << "The operand valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   MinValue = vaR.min ( );
   cout << "The smallest element in the valarray is: "
        << MinValue  << "." << endl;
}
\* Output:
The operand valarray is: ( 0 2 3 -3 8 0 -6 14 -3 -9 ).
The smallest element in the valarray is: -9.
*\
```

## <a name="op_not"></a>  valarray::operator!

Un operador unario que obtiene los valores **NOT** lógicos de cada elemento de una valarray.

```cpp
valarray<bool> operator!() const;
```

### <a name="return-value"></a>Valor devuelto

La valarray de valores booleanos que son la negación de los valores de elemento de la valarray de operando.

### <a name="remarks"></a>Comentarios

La operación lógica **NOT** niega los elementos dado que convierte todos los ceros en unos, considera todos los valores distintos de cero como unos y los convierte en ceros. La valarray devuelta de valores booleanos es del mismo tamaño que la valarray de operando.

También hay un bit a bit **no**[valarray:: operator ~](#op_dtor) que niega en el nivel de bits individuales dentro de la representación binaria de **char** y **int**  elementos de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_lognot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<bool> vaNOT ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaNOT = !vaL;
   cout << "The element-by-element result of "
        << "the logical NOT operator! is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The element-by-element result of the logical NOT operator! is the
 valarray: ( 1 1 1 0 1 0 1 0 1 0 ).
*\
```

## <a name="op_mod_eq"></a>  valarray::operator%=

Obtiene el resto de la división de los elementos de una matriz uno a uno por una valarray especificada o por un valor del tipo de elemento.

```cpp
valarray<Type>& operator%=(const valarray<Type>& right);

valarray<Type>& operator%=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que consiste en dividir, por elemento, la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el resto de la división por elemento de la valarray de operando por *derecha*

### <a name="example"></a>Ejemplo

```cpp
// valarray_class_op_rem.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  53;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -67;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  3*i+1;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL %= vaR;
   cout << "The remainders from the element-by-element "
        << "division is the\n valarray: ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 53 -67 53 -67 53 -67 ).
The initial  right valarray is: ( 1 4 7 10 13 16 ).
The remainders from the element-by-element division is the
 valarray: ( 0 -3 4 -7 1 -3 ).
*\
```

## <a name="and_eq"></a>  valarray::operator&amp;=

Obtiene el **AND** bit a bit de los elementos de una matriz con los elementos correspondientes de una valarray especificada o con un valor del tipo de elemento.

```cpp
valarray<Type>& operator&=(const valarray<Type>& right);

valarray<Type>& operator&=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico de la valarray de operando que se va a combinar, por elemento, mediante la operación lógica `AND` con la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son los elementos lógicos `AND` de la valarray de operando por *derecha*

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **longdouble**, **void**, **bool**, u otros tipos de datos más complejos.

La operación AND bit a bit tiene la misma tabla de verdad que la operación lógica `AND` pero se aplica al tipo de datos en el nivel de los bits individuales. Dados los bits *b*1 y *b*2, *b*1 `AND` *b*2 es **true** si ambos bits son true; **false** si al menos uno es false.

### <a name="example"></a>Ejemplo

```cpp
// valarray_class_op_bitand.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;
   for ( i = 0 ; i < 10 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL &= vaR;
   cout << "The element-by-element result of "
        << "the logical AND operator&= is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 0 2 0 4 0 6 0 8 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 8 9 ).
The element-by-element result of the logical AND operator&= is the
 valarray: ( 0 0 0 2 0 4 0 6 0 8 ).
*\
```

## <a name="op_gt_gt_eq"></a>  valarray::operator&gt;&gt;=

Desplaza hacia la derecha los bits de cada elemento de un operando de valarray en un número especificado de posiciones o una cantidad por elemento especificada por una segunda valarray.

```cpp
valarray<Type>& operator>>=(const valarray<Type>& right);

valarray<Type>& operator>>=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 El valor que indica la cantidad de desplazamiento a la derecha o la valarray cuyos elementos indican la cantidad de desplazamiento a la derecha por elemento.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos se han desplazado a la derecha la cantidad especificada en *derecho*.

### <a name="remarks"></a>Comentarios

Los números con signo conservan sus signos.

### <a name="example"></a>Ejemplo

```cpp
// valarray_class_op_rs.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  64;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -64;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL >>= vaR;
   cout << "The element-by-element result of "
        << "the right shift is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is: ( 64 -64 64 -64 64 -64 64 -64 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the right shift is the
 valarray: ( 64 -32 16 -8 4 -2 1 -1 ).
*\
```

## <a name="op_lt_lt_eq"></a>  valarray::operator&lt;&lt;=

Desplaza hacia la izquierda los bits de cada elemento de un operando de valarray un número especificado de posiciones o una cantidad por elemento especificada por una segunda valarray.

```cpp
valarray<Type>& operator<<=(const valarray<Type>& right);

valarray<Type>& operator<<=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 El valor que indica la cantidad de desplazamiento a la izquierda o la valarray cuyos elementos indican la cantidad de desplazamiento a la izquierda por elemento.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos se ha desplazado izquierda la cantidad especificada en *derecho*.

### <a name="remarks"></a>Comentarios

Los números con signo conservan sus signos.

### <a name="example"></a>Ejemplo

```cpp
// valarray_class_op_ls.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  1;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial operand valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL <<= vaR;
   cout << "The element-by-element result of "
        << "the left shift\n on the operand array is the valarray:\n ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is: ( 1 -1 1 -1 1 -1 1 -1 ).
The  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the left shift
 on the operand array is the valarray:
 ( 1 -2 4 -8 16 -32 64 -128 ).
*\
```

## <a name="op_star_eq"></a>  valarray::operator*=

Multiplica los elementos de una valarray especificada o un valor del tipo de elemento, uno a uno, por una valarray de operando.

```cpp
valarray<Type>& operator*=(const valarray<Type>& right);

valarray<Type>& operator*=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que va a multiplicar, por elemento, la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el producto por elemento de la valarray de operando y *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_emult.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL *= vaR;
   cout << "The element-by-element result of "
        << "the multiplication is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial Right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the multiplication is the
 valarray: ( 0 -1 4 -3 8 -5 12 -7 ).
*\
```

## <a name="op_add"></a>  valarray::operator+

Un operador unario que aplica un signo más a cada elemento de una valarray.

```cpp
valarray<Type> operator+() const;
```

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son más que los de la matriz de operando.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_eplus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaPLUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaPLUS = +vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaPLUS [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
*\
```

## <a name="op_add_eq"></a>  valarray::operator+=

Suma los elementos de una valarray especificada o un valor del tipo de elemento, uno a uno, por una valarray de operando.

```cpp
valarray<Type>& operator+=(const valarray<Type>& right);

valarray<Type>& operator+=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que se va a sumar, por elemento, a la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la suma por elemento de la valarray de operando y *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_eadd.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  2;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  -1;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL += vaR;
   cout << "The element-by-element result of "
        << "the sum is the\n valarray: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 2 -1 2 -1 2 -1 2 -1 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the sum is the
 valarray: ( 2 0 4 2 6 4 8 6 ).
*\
```

## <a name="valarray__operator-"></a>  valarray::operator-

Un operador unario que aplica un signo menos a cada elemento de una valarray.

```cpp
valarray<Type> operator-() const;
```

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son menos que los de la matriz de operando.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_eminus.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 );
   valarray<int> vaMINUS ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL [ i ] =  -i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL [ i ] =  i-1;

   cout << "The initial valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   vaMINUS = -vaL;
   cout << "The element-by-element result of "
        << "the operator+ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaMINUS [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is:  ( 0 0 -2 2 -4 4 -6 6 -8 8 ).
The element-by-element result of the operator+ is the
 valarray: ( 0 0 2 -2 4 -4 6 -6 8 -8 ).
*\
```

## <a name="valarray__operator-_eq"></a>  valarray::operator-=

Resta los elementos de una valarray especificada o un valor del tipo de elemento, uno a uno, de una valarray de operando.

```cpp
valarray<Type>& operator-=(const valarray<Type>& right);

valarray<Type>& operator-=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que se va a restar, por elemento, de la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son la diferencia por elemento de la valarray de operando y *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_esub.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 8 ), vaR ( 8 );
   for ( i = 0 ; i < 8 ; i += 2 )
      vaL [ i ] =  10;
   for ( i = 1 ; i < 8 ; i += 2 )
      vaL [ i ] =  0;
   for ( i = 0 ; i < 8 ; i++ )
      vaR [ i ] =  i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial  right valarray is: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL -= vaR;
   cout << "The element-by-element result of "
        << "the difference is the\n valarray: ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 10 0 10 0 10 0 10 0 ).
The initial  right valarray is: ( 0 1 2 3 4 5 6 7 ).
The element-by-element result of the difference is the
 valarray: ( 10 -1 8 -3 6 -5 4 -7 ).
*\
```

## <a name="op_div_eq"></a>  valarray::operator/=

Divide una valarray de operando, por elemento, por los elementos de una valarray especificada o un valor del tipo de elemento.

```cpp
valarray<Type>& operator/=(const valarray<Type>& right);

valarray<Type>& operator/=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que se va a dividir, por elemento, en la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el cociente por elemento de la valarray de operando dividida por *derecho*.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_ediv.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<double> vaL ( 6 ), vaR ( 6 );
   for ( i = 0 ; i < 6 ; i += 2 )
      vaL [ i ] =  100;
   for ( i = 1 ; i < 6 ; i += 2 )
      vaL [ i ] =  -100;
   for ( i = 0 ; i < 6 ; i++ )
      vaR [ i ] =  2*i;

   cout << "The initial valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The initial Right valarray is: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL /= vaR;
   cout << "The element-by-element result of "
        << "the quotient is the\n valarray: ( ";
      for (i = 0 ; i < 6 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray is: ( 100 -100 100 -100 100 -100 ).
The initial Right valarray is: ( 0 2 4 6 8 10 ).
The element-by-element result of the quotient is the
 valarray: ( inf -50 25 -16.6667 12.5 -10 ).
*\
```

## <a name="op_eq"></a>  valarray::operator=

Asigna elementos a una valarray cuyos valores se especifican directamente o como parte de alguna otra valarray o por una slice_array, gslice_array, mask_array o indirect_array.

```cpp
valarray<Type>& operator=(const valarray<Type>& right);

valarray<Type>& operator=(valarray<Type>&& right);

valarray<Type>& operator=(const Type& val);

valarray<Type>& operator=(const slice_array<Type>& _Slicearray);

valarray<Type>& operator=(const gslice_array<Type>& _Gslicearray);

valarray<Type>& operator=(const mask_array<Type>& _Maskarray);

valarray<Type>& operator=(const indirect_array<Type>& _Indarray);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray que se va a copiar en la valarray de operando.

*Val*  
 El valor que se va a asignar a los elementos de la valarray de operando.

*_Slicearray*  
 La slice_array que se va a copiar en la valarray de operando.

*_Gslicearray*  
 La gslice_array que se va a copiar en la valarray de operando.

*_Maskarray*  
 La mask_array que se va a copiar en la valarray de operando.

*_Indarray*  
 La indirect_array que se va a copiar en la valarray de operando.

### <a name="return-value"></a>Valor devuelto

El primer operador miembro reemplaza la secuencia controlada por una copia de la secuencia controlada por *derecho*.

El segundo operador miembro es igual que el primero, pero con un [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

El tercer operador miembro reemplaza cada elemento de la secuencia controlada por una copia de *val*.

Los operadores miembro restantes reemplazan los elementos de la secuencia controlada seleccionados por sus argumentos, que se generan únicamente por el [operator&#91;&#93;](#op_at).

Si el valor de un miembro en la secuencia controlada de reemplazo depende de un miembro de la secuencia controlada inicial, el resultado es indefinido.

### <a name="remarks"></a>Comentarios

Si cambia la longitud de la secuencia controlada, el resultado es generalmente indefinido. Pero en esta implementación, el efecto es simplemente invalidar los punteros o referencias a los elementos de la secuencia controlada.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_assign.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 10 ), vaR ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va [ i ] = i;
   for ( i = 0 ; i < 10 ; i+=1 )
      vaR [ i ] = 10 -  i;

   cout << "The operand valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   cout << "The operand valarray vaR is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << vaR [ i ];
   cout << endl;

   // Assigning vaR to va with the first member functon
   va = vaR;
   cout << "The reassigned valarray va is:";
   for ( i = 0 ; i < 10 ; i++ )
      cout << " " << va [ i ];
   cout << endl;

   // Assigning elements of value 10 to va
   // with the second member functon
   va = 10;
   cout << "The reassigned valarray va is:";
      for ( i = 0 ; i < 10 ; i++ )
         cout << " " << va [ i ];
   cout << endl;
}
\* Output:
The operand valarray va is: 0 1 2 3 4 5 6 7 8 9
The operand valarray vaR is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 9 8 7 6 5 4 3 2 1
The reassigned valarray va is: 10 10 10 10 10 10 10 10 10 10
*\
```

## <a name="op_at"></a>  valarray::operator[]

Devuelve una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.

```cpp
Type& operator[](size_t _Off);

slice_array<Type> operator[](slice _Slicearray);

gslice_array<Type> operator[](const gslice& _Gslicearray);

mask_array<Type> operator[](const valarray<bool>& _Boolarray);

indirect_array<Type> operator[](const valarray<size_t>& _Indarray);

Type operator[](size_t _Off) const;


valarray<Type> operator[](slice _Slice) const;


valarray<Type> operator[](const gslice& _Gslicearray) const;


valarray<Type> operator[](const valarray<bool>& _Boolarray) const;


valarray<Type> operator[](const valarray<size_t>& _Indarray) const;
```

### <a name="parameters"></a>Parámetros

*_Off*  
 El índice del elemento al que se va a asignar un valor.

*_Slicearray*  
 Una slice_array de una valarray que especifica un subconjunto que se va a seleccionar o devolver a una nueva valarray.

*_Gslicearray*  
 Una gslice_array de una valarray que especifica un subconjunto que se va a seleccionar o devolver a una nueva valarray.

*_Boolarray*  
 Una bool_array de una valarray que especifica un subconjunto que se va a seleccionar o devolver a una nueva valarray.

*_Indarray*  
 Una indirect_array de una valarray que especifica un subconjunto que se va a seleccionar o devolver a una nueva valarray.

### <a name="return-value"></a>Valor devuelto

Una referencia a un elemento o su valor en el índice especificado o un subconjunto especificado.

### <a name="remarks"></a>Comentarios

El operador de miembro se sobrecarga para proporcionar varias maneras de seleccionar secuencias de elementos entre las controla **\****esto**. El primer grupo de cinco operadores miembro funcionan en conjunción con varias sobrecargas de [operador=](#op_eq) (y otros operadores de asignación) para permitir el reemplazo selectivo (segmentación) de la secuencia controlada. Los elementos seleccionados deben existir.

Al compilar con [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) definido como 1 o 2, se produce un error de tiempo de ejecución si intenta tener acceso a un elemento fuera de los límites de la valarray.  Para más información, vea [Iteradores activados](../standard-library/checked-iterators.md).

### <a name="example"></a>Ejemplo

Vea los ejemplos de [slice::slice](../standard-library/slice-class.md#slice) y [gslice::gslice](../standard-library/gslice-class.md#gslice) para obtener un ejemplo de cómo declarar y usar el operador.

## <a name="op_xor_eq"></a>  valarray::operator^=

Obtiene el operador OR lógico exclusivo ( **XOR**) por elemento de una matriz con una valarray especificada o un valor del tipo de elemento.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que se va a combinar, por elemento, mediante el **XOR** lógico exclusivo con la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son el lógico exclusivo por elemento, **XOR** de la valarray de operando y *derecho*.

### <a name="remarks"></a>Comentarios

El OR lógico exclusivo, que se conoce como **XOR**, tiene la semántica siguiente: dados los elementos *e*1 y *e*2, *e*1 **XOR** *e*2 es **true** si exactamente uno de los elementos es true. Es **false** si ambos elementos son false o si ambos elementos son true.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_exor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
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

   cout << "The initial operand valarray is:  ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL ^= vaR;
   cout << "The element-by-element result of "
        << "the bitwise XOR operator^= is the\n valarray: ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is:  ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is: ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the bitwise XOR operator^= is the
 valarray: ( 1 0 0 3 2 4 7 6 6 9 ).
*\
```

## <a name="op_or_eq"></a>  valarray::operator&#124;=

Obtiene el `OR` bit a bit de los elementos de una matriz con los elementos correspondientes de una valarray especificada o con un valor del tipo de elemento.

```cpp
valarray<Type>& operator|=(const valarray<Type>& right);

valarray<Type>& operator|=(const Type& right);
```

### <a name="parameters"></a>Parámetros

*right*  
 La valarray o el valor de un tipo de elemento idéntico al de la valarray de operando que se va a combinar, por elemento, mediante el `OR` bit a bit con la valarray de operando.

### <a name="return-value"></a>Valor devuelto

Una valarray cuyos elementos son los elementos de bit a bit `OR` de la valarray de operando por *derecho*.

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **longdouble**, **void**, **bool**, u otros tipos de datos más complejos.

El `OR` bit a bit tiene la misma tabla de verdad que el `OR` lógico pero se aplica al tipo de datos en el nivel de los bits individuales. Dados los bits *b*1 y *b*2, *b*1 `OR` *b*2 es **true** si al menos uno de los bits es true o **false** si los dos bits son false.

### <a name="example"></a>Ejemplo

```cpp
// valarray_class_op_bitor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> vaL ( 10 ), vaR ( 10 );
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

   cout << "The initial operand valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;

   cout << "The  right valarray is:\n ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaR [ i ] << " ";
   cout << ")." << endl;

   vaL |= vaR;
   cout << "The element-by-element result of "
        << "the logical OR\n operator|= is the valarray:\n ( ";
      for (i = 0 ; i < 10 ; i++ )
         cout << vaL [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is:
 ( 1 0 1 0 1 0 1 0 1 0 ).
The  right valarray is:
 ( 0 0 1 3 3 4 6 6 7 9 ).
The element-by-element result of the logical OR
 operator|= is the valarray:
 ( 1 0 1 3 3 4 7 6 7 9 ).
*\
```

## <a name="op_dtor"></a>  valarray::operator~

Un operador unario que obtiene el bit a bit `NOT` valores de cada elemento de una valarray.

```cpp
valarray<Type> operator~() const;
```

### <a name="return-value"></a>Valor devuelto

La valarray de valores booleanos que son el bit a bit `NOT` de los valores de elemento de la valarray de operando.

### <a name="remarks"></a>Comentarios

Una operación bit a bit solo puede usarse para manipular los bits de **char** y **int** variantes y tipos de datos y no en **float**, **doble**, **longdouble**, **void**, **bool** u otros tipos de datos más complejos.

El `NOT` bit a bit tiene la misma tabla de verdad que el `NOT` lógico pero se aplica al tipo de datos en el nivel de los bits individuales. Dado el bit *b*, ~ *b* es true si *b* es false y es false si *b* es true. El [operador!](#op_not)**NOT** lógico se aplica en el nivel de elemento, contando todos los valores distintos de cero como **true**, y el resultado es una valarray de valores booleanos. Bit a bit `NOToperator~`, por el contrario, puede dar lugar a una valarray de valores distintos de 0 o 1, dependiendo del resultado de la operación bit a bit.

### <a name="example"></a>Ejemplo

```cpp
// valarray_op_bitnot.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<unsigned short int> vaL1 ( 10 );
   valarray<unsigned short int> vaNOT1 ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL1 [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL1 [ i ] =  5*i;

   cout << "The initial valarray <unsigned short int> is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL1 [ i ] << " ";
   cout << ")." << endl;

   vaNOT1 = ~vaL1;
   cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT1 [ i ] << " ";
   cout << ")." << endl << endl;

   valarray<int> vaL2 ( 10 );
   valarray<int> vaNOT2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      vaL2 [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      vaL2 [ i ] =  -2 * i;

   cout << "The initial valarray <int> is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaL2 [ i ] << " ";
   cout << ")." << endl;

   vaNOT2 = ~vaL2;
   cout << "The element-by-element result of "
        << "the bitwise NOT operator~ is the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;

   // The negative numbers are represented using
   // the two's complement approach, so adding one
   // to the flipped bits returns the negative elements
   vaNOT2 = vaNOT2 + 1;
   cout << "The element-by-element result of "
        << "adding one\n is the negative of the "
        << "original elements the\n valarray: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << vaNOT2 [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial valarray <unsigned short int> is:  ( 0 5 2 15 4 25 6 35 8 45 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( 65535 65530 65533 65520 65531 65510 65529 65500 65527 65490 ).

The initial valarray <int> is:  ( 0 -2 2 -6 4 -10 6 -14 8 -18 ).
The element-by-element result of the bitwise NOT operator~ is the
 valarray: ( -1 1 -3 5 -5 9 -7 13 -9 17 ).
The element-by-element result of adding one
 is the negative of the original elements the
 valarray: ( 0 2 -2 6 -4 10 -6 14 -8 18 ).
*\
```

## <a name="resize"></a>  valarray::resize

Cambia el número de elementos de una valarray a un número especificado.

```cpp
void resize(
    size_t _Newsize);

void resize(
    size_t _Newsize,
    const Type val);
```

### <a name="parameters"></a>Parámetros

*_Newsize*  
 Número de elementos de la valarray cuyo tamaño se cambió.

*Val*  
 Valor que se asignará a los elementos de la valarray cuyo tamaño se cambió.

### <a name="remarks"></a>Comentarios

La primera función miembro inicializa los elementos con su constructor predeterminado.

Se invalidan los punteros o referencias a elementos de la secuencia controlada.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo debe usarse la función miembro valarray::resize.

```cpp
// valarray_resize.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, sizeNew;

    valarray<int> va1(10);
    for (i = 0; i < 10; i+=1)
        va1[i] = i;

    cout << "The valarray contains ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray is: "
         << size1  << "." <<endl << endl;

    va1.resize(15, 10);

    cout << "The valarray contains ( ";
        for (i = 0; i < 15; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;
    sizeNew = va1.size();
    cout << "The number of elements in the resized valarray is: "
         << sizeNew  << "." <<endl << endl;
}
```

```Output
The valarray contains ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray is: 10.

The valarray contains ( 10 10 10 10 10 10 10 10 10 10 10 10 10 10 10 ).
The number of elements in the resized valarray is: 15.
```

## <a name="shift"></a>  valarray::shift

Desplaza todos los elementos de una valarray un número especificado de posiciones.

```cpp
valarray<Type> shift(int count) const;
```

### <a name="parameters"></a>Parámetros

*count*  
 El número de posiciones que se van a desplazar hacia adelante los elementos.

### <a name="return-value"></a>Valor devuelto

Una nueva valarray en la que todos los elementos se han movido *recuento* posiciones hacia la parte delantera de la valarray, a la izquierda con respecto a sus posiciones en la valarray de operando.

### <a name="remarks"></a>Comentarios

Un valor positivo de *recuento* desplaza los elementos a la izquierda *recuento* posiciones, con relleno cero.

Un valor negativo de *recuento* desplaza los elementos a la derecha *recuento* posiciones, con relleno cero.

### <a name="example"></a>Ejemplo

```cpp
// valarray_shift.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va1 ( 10 ), va2 ( 10 );
   for ( i = 0 ; i < 10 ; i += 1 )
      va1 [ i ] =  i;
   for ( i = 0 ; i < 10 ; i += 1 )
      va2 [ i ] = 10 -  i;

   cout << "The operand valarray va1(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   // A positive parameter shifts elements left
   va1 = va1.shift ( 4 );
   cout << "The shifted valarray va1 is: va1.shift (4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va1 [ i ] << " ";
   cout << ")." << endl;

   cout << "The operand valarray va2(10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;

   // A negative parameter shifts elements right
   va2 = va2.shift ( - 4 );
   cout << "The shifted valarray va2 is: va2.shift (-4) = ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va2 [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The shifted valarray va1 is: va1.shift (4) = ( 4 5 6 7 8 9 0 0 0 0 ).
The operand valarray va2(10) is: ( 10 9 8 7 6 5 4 3 2 1 ).
The shifted valarray va2 is: va2.shift (-4) = ( 0 0 0 0 10 9 8 7 6 5 ).
*\
```

## <a name="size"></a>  valarray::size

Busca el número de elementos de una valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de la valarray de operando.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo debe usarse la función miembro valarray::size.

```cpp
// valarray_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;
    size_t size1, size2;

    valarray<int> va1(10), va2(12);
    for (i = 0; i < 10; i += 1)
        va1[i] =  i;
    for (i = 0; i < 10; i += 1)
        va2[i] =  i;

    cout << "The operand valarray va1(10) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va1[i] << " ";
    cout << ")." << endl;

    size1 = va1.size();
    cout << "The number of elements in the valarray va1 is: va1.size = "
         << size1  << "." <<endl << endl;

    cout << "The operand valarray va2(12) is: ( ";
        for (i = 0; i < 10; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;

    size2 = va2.size();
    cout << "The number of elements in the valarray va2 is: va2.size = "
         << size2  << "." << endl << endl;

    // Initializing two more elements to va2
    va2[10] = 10;
    va2[11] = 11;
    cout << "After initializing two more elements,\n "
         << "the operand valarray va2(12) is now: ( ";
        for (i = 0; i < 12; i++)
            cout << va2[i] << " ";
    cout << ")." << endl;
    cout << "The number of elements in the valarray va2 is still: "
         << size2  << "." << endl;
}
```

```Output
The operand valarray va1(10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va1 is: va1.size = 10.

The operand valarray va2(12) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The number of elements in the valarray va2 is: va2.size = 12.

After initializing two more elements,
 the operand valarray va2(12) is now: ( 0 1 2 3 4 5 6 7 8 9 10 11 ).
The number of elements in the valarray va2 is still: 12.
```

## <a name="sum"></a>  valarray::sum

Determina la suma de todos los elementos de una valarray de longitud distinta de cero.

```cpp
Type sum() const;
```

### <a name="return-value"></a>Valor devuelto

La suma de los elementos de la valarray de operando.

### <a name="remarks"></a>Comentarios

Si la longitud es mayor que uno, la función miembro agrega valores a la suma aplicando `operator+=` entre pares de elementos de la clase `Type`, cuyo operador, por lo tanto, debe proporcionarse para elementos de tipo `Type`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_sum.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   int sumva = 0;

   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va (10) is: ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sumva = va.sum ( );
   cout << "The sum of elements in the valarray is: "
        << sumva  << "." <<endl;
}
\* Output:
The operand valarray va (10) is: ( 0 1 2 3 4 5 6 7 8 9 ).
The sum of elements in the valarray is: 45.
*\
```

## <a name="swap"></a>  valarray::swap

Intercambia los elementos de dos `valarray`.

```cpp
void swap(valarray& right);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*right*|`valarray` que proporciona los elementos que se van a intercambiar.|

### <a name="remarks"></a>Comentarios

La función miembro intercambia las secuencias controladas entre `*this` y *derecho*. Lo hace en tiempo constante, no inicia ninguna excepción y no invalida ninguna referencia, puntero o iterador que designen elementos en las dos secuencias controladas.

## <a name="valarray"></a>  valarray::valarray

Construye una valarray de un tamaño específico o con elementos de un valor determinado, o como una copia de otra valarray o un subconjunto de otra valarray.

```cpp
valarray();

explicit valarray(
    size_t Count);

valarray(
    const Type& Val,
    size_t Count);

valarray(
    const Type* Ptr,
    size_t Count);

valarray(
    const valarray<Type>& Right);

valarray(
    const slice_array<Type>& SliceArray);

valarray(
    const gslice_array<Type>& GsliceArray);

valarray(
    const mask_array<Type>& MaskArray);

valarray(
    const indirect_array<Type>& IndArray);

valarray(
    valarray<Type>&& Right);

valarray(
    initializer_list<Type> IList);
```

### <a name="parameters"></a>Parámetros

*Recuento*  
 Número de elementos que va a haber en la valarray.

*Val*  
 Valor que se utilizará al inicializar los elementos de la valarray.

*PTR*  
 Puntero a los valores que se usarán para inicializar los elementos de la valarray.

*Derecha*  
 Valarray existente para inicializar la nueva valarray.

*SliceArray*  
 slice_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.

*GsliceArray*  
 gslice_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.

*MaskArray*  
 mask_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.

*IndArray*  
 indirect_array cuyos valores de elemento se van a utilizar al inicializar los elementos de la valarray que se va a construir.

*IList*  
 initializer_list que contiene los elementos que se van a copiar.

### <a name="remarks"></a>Comentarios

El primer constructor (predeterminado) inicializa el objeto en una matriz vacía. Los siguientes tres constructores inicializan el objeto en una matriz de *recuento* elementos como sigue:

- En el caso de `valarray(size_t Count)` explícito, cada elemento se inicializa con el constructor predeterminado.

- Para `valarray(const Type& Val, Count)`, cada elemento se inicializa con *Val*.

- En `valarray(const Type* Ptr, Count)`, el elemento situado en la posición `I` se inicializa con `Ptr`[ `I`].

Cada constructor restante inicializa el objeto en un objeto valarray\<Type> determinado por el subconjunto especificado en el argumento.

El último constructor es igual que el penúltimo, pero con un [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).

### <a name="example"></a>Ejemplo

```cpp
// valarray_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main()
{
    using namespace std;
    int i;

    // The second member function
    valarray<int> va(10);
    for (auto i : va){
        va[i] = 2 * (i + 1);
    }

    cout << "The operand valarray va is:\n(";
    for (auto i : va) {
        cout << " " << va[i];
    }
    cout << " )" << endl;

    slice Slice(2, 4, 3);

    // The fifth member function
    valarray<int> vaSlice = va[Slice];

    cout << "The new valarray initialized from the slice is vaSlice ="
        << "\nva[slice( 2, 4, 3)] = (";
    for (int i = 0; i < 3; i++) {
        cout << " " << vaSlice[i];
    }
    cout << " )" << endl;

    valarray<int> va2{{ 1, 2, 3, 4 }};
    for (auto& v : va2){
        cout << v << " ";
    }
    cout << endl;
}

```

```Output
The operand valarray va is:( 0 2 2 2 2 2 2 2 2 2 )The new valarray initialized from the slice is vaSlice =va[slice( 2, 4, 3)] = ( 0 0 0 )1 2 3 4
```

## <a name="value_type"></a>  valarray::value_type

Un tipo que representa el tipo de elemento almacenado en una valarray.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Comentarios

El tipo es un sinónimo del parámetro de plantilla `Type`.

### <a name="example"></a>Ejemplo

```cpp
// valarray_value_type.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   valarray<int> va ( 10 );
   for ( i = 0 ; i < 10 ; i += 2 )
      va [ i ] =  i;
   for ( i = 1 ; i < 10 ; i += 2 )
      va [ i ] =  -1;

   cout << "The initial operand valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   // value_type declaration and initialization:
   valarray<int>::value_type Right = 10;

   cout << "The decalared value_type Right is: "
           << Right << endl;
   va *= Right;
   cout << "The resulting valarray is:  ( ";
      for ( i = 0 ; i < 10 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;
}
\* Output:
The initial operand valarray is:  ( 0 -1 2 -1 4 -1 6 -1 8 -1 ).
The decalared value_type Right is: 10
The resulting valarray is:  ( 0 -10 20 -10 40 -10 60 -10 80 -10 ).
*\
```

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
