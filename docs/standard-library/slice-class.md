---
title: slice (Clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::slice
- valarray/std::slice::size
- valarray/std::slice::start
- valarray/std::slice::stride
helpviewer_keywords:
- std::slice [C++]
- std::slice [C++], size
- std::slice [C++], start
- std::slice [C++], stride
ms.assetid: 00f0b03d-d657-4b81-ba53-5a9034bb2bf2
ms.openlocfilehash: 05f87cbb6061e205f9731d2a903ce52a2482b214
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336715"
---
# <a name="slice-class"></a>slice (Clase)

Una clase de utilidad para valarray que se usa para definir subconjuntos unidimensionales de una valarray principal. Si una valarray se considera como una matriz bidimensional con todos los elementos de una matriz, el segmento extrae un vector en una dimensión de la matriz bidimensional.

## <a name="remarks"></a>Observaciones

La clase almacena los parámetros que caracterizan a un objeto de tipo [slice_array](../standard-library/slice-array-class.md). El subconjunto de una valarray se crea indirectamente cuando un objeto de clase slice aparece como argumento para un objeto de clase [valarray](../standard-library/valarray-class.md#op_at)**\<Type>**. Los valores almacenados que especifican el subconjunto seleccionado de la valarray primaria incluyen:

- Índice inicial de la valarray.

- Longitud total o número de elementos en el segmento.

- Un intervalo, o la distancia entre índices subsiguientes de los elementos de la valarray.

Si el conjunto definido por un segmento es el subconjunto de una valarray de constantes, el segmento es una nueva valarray. Si el conjunto definido por un segmento es el subconjunto de una valarray de no constantes, el segmento tiene semántica de referencia a la valarray original. El mecanismo de evaluación para valarrays de no constantes ahorra tiempo y memoria.

Las operaciones en valarrays solo se garantizan si los subconjuntos de origen y de destino definidos por los segmentos son distintos y todos los índices son válidos.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[Rebanada](#slice)|Define un subconjunto de un `valarray` que consta de un número de elementos equidistantes y que comienzan en un elemento especificado.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Tamaño](#size)|Busca el número de elementos de un segmento de una `valarray`.|
|[start](#start)|Busca el índice inicial de un segmento de una `valarray`.|
|[Paso](#stride)|Busca la distancia entre los elementos de un segmento de una `valarray`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="slicesize"></a><a name="size"></a>rebanada::tamaño

Busca el número de elementos de un segmento de una valarray.

```cpp
size_t size() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos de un segmento de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// slice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA, sizeVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   sizeVAR = vaSlice.size ( );
   cout << "The size of slice vaSlice is: "
        << sizeVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The size of the valarray is: 20.

The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The size of slice vaSlice is: 6.
```

## <a name="sliceslice"></a><a name="slice"></a>rebanada::slice

Define un subconjunto de una valarray que consta de un número de elementos equidistantes y que comienzan en un elemento especificado.

```cpp
slice();

slice(
    size_t _StartIndex,
    size_t _Len,
    size_t stride);
```

### <a name="parameters"></a>Parámetros

*_StartIndex*\
El índice de valarray del primer elemento del subconjunto.

*_Len*\
El número de elementos del subconjunto.

*Paso*\
La distancia entre los elementos del subconjunto.

### <a name="return-value"></a>Valor devuelto

El constructor predeterminado almacena ceros para el índice de inicio, la longitud total y el intervalo. El segundo constructor almacena *_StartIndex* para el índice inicial, *_Len* para la longitud total y *zancada* para la zancada.

### <a name="remarks"></a>Observaciones

El intervalo puede ser negativo.

### <a name="example"></a>Ejemplo

```cpp
// slice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  2 * (i + 1 );

   cout << "The operand valarray va is:\n( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 1 , 7 , 3 );
   vaResult = va [ vaSlice ];

   cout << "\nThe slice of valarray va is vaResult:"
        << "\nva[slice( 1, 7, 3)] = ( ";
      for ( i = 0 ; i < 7 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 ).

The slice of valarray va is vaResult:
va[slice( 1, 7, 3)] = ( 4 10 16 22 28 34 40 ).
```

## <a name="slicestart"></a><a name="start"></a>rebanada::start

Busca el índice inicial de un segmento de una valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Valor devuelto

El índice inicial de un segmento de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// slice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t startVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] = i+1;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 3 , 6 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 3, 6, 3)] =\n ( ";
      for ( i = 0 ; i < 6 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   startVAR = vaSlice.start ( );
   cout << "The start index of slice vaSlice is: "
        << startVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The slice of valarray va is vaResult = va[slice( 3, 6, 3)] =
( 4 7 10 13 16 19 ).
The start index of slice vaSlice is: 3.
```

## <a name="slicestride"></a><a name="stride"></a>rebanada::stride

Busca la distancia entre los elementos de un segmento de una valarray.

```cpp
size_t stride() const;
```

### <a name="return-value"></a>Valor devuelto

La distancia entre los elementos de un segmento de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// slice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t strideVAR;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i += 1 )
      va [ i ] =  3 * ( i + 1 );

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   slice vaSlice ( 4 , 5 , 3 );
   vaResult = va [ vaSlice ];

   cout << "The slice of valarray va is vaResult = "
        << "va[slice( 4, 5, 3)] =\n ( ";
      for ( i = 0 ; i < 5 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   strideVAR = vaSlice.stride ( );
   cout << "The stride of slice vaSlice is: "
        << strideVAR << "." << endl;
}
```

```Output
The operand valarray va is:
( 3 6 9 12 15 18 21 24 27 30 33 36 39 42 45 48 51 54 57 60 ).
The slice of valarray va is vaResult = va[slice( 4, 5, 3)] =
( 15 24 33 42 51 ).
The stride of slice vaSlice is: 3.
```

## <a name="see-also"></a>Consulte también

[Seguridad de roscas en la biblioteca estándar C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
