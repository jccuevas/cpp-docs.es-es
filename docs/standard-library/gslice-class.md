---
title: gslice (Clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice
- valarray/std::gslice::size
- valarray/std::gslice::start
- valarray/std::gslice::stride
helpviewer_keywords:
- std::gslice [C++]
- std::gslice [C++], size
- std::gslice [C++], start
- std::gslice [C++], stride
ms.assetid: f47cffd0-ea59-4b13-848b-7a5ce1d7e2a3
ms.openlocfilehash: 9290fabc86ffbdb051b7c61fe1600cd2f7f17dca
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866261"
---
# <a name="gslice-class"></a>gslice (Clase)

Clase de utilidad para valarray que se usa para definir subconjuntos multidimensionales de una valarray. Si una valarray se considera como una matriz multidimensional con todos los elementos de una matriz, el segmento extrae un vector de la matriz multidimensional.

## <a name="remarks"></a>Observaciones

La clase almacena los parámetros que caracterizan a un objeto de tipo [gslice_array](../standard-library/gslice-array-class.md). El subconjunto de una valarray se crea indirectamente cuando un objeto de clase gslice aparece como argumento de un objeto de clase [valarray](../standard-library/valarray-class.md#op_at) **\<Type>** . Los valores almacenados que especifican el subconjunto seleccionado de la valarray primaria incluyen:

- Un índice de inicio.

- Vector de longitud de la clase `valarray<size_t>`.

- Un vector de paso de `valarray<size_t>`de clase.

Los dos vectores deben tener la misma longitud.

Si el conjunto definido por un gslice es el subconjunto de una valarray de constantes, el gslice es una nueva valarray. Si el conjunto definido por un gslice es el subconjunto de una valarray de no constantes, el gslice tiene semántica de referencia a la valarray original. El mecanismo de evaluación para valarrays de no constantes ahorra tiempo y memoria.

Las operaciones en valarrays solo se garantizan si los subconjuntos de origen y de destino definidos por los gslices son distintos y todos los índices son válidos.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[gslice](#gslice)|Define un subconjunto de un `valarray` que consta de varios segmentos de la `valarray` que todas comienzan a partir de un elemento especificado.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[size](#size)|Busca los valores de la matriz especificando el número de elementos en un segmento general de un `valarray`.|
|[start](#start)|Busca el índice inicial de un segmento general de un `valarray`.|
|[stride](#stride)|Busca la distancia entre los elementos de un segmento general de un `valarray`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray >

**Espacio de nombres:** std

## <a name="gslice"></a>  gslice::gslice

Clase de utilidad para valarray que se usa para definir segmentos multidimensionales de una valarray.

```cpp
gslice();

gslice(
    size_t _StartIndex,
    const valarray<size_t>& _LenArray,
    const valarray<size_t>& _IncArray);
```

### <a name="parameters"></a>Parámetros

*_StartIndex*\
El índice de valarray del primer elemento del subconjunto.

*_LenArray*\
Una matriz que especifica el número de elementos de cada segmento.

*_IncArray*\
Una matriz que especifica el intervalo de cada segmento.

### <a name="return-value"></a>Valor devuelto

El constructor predeterminado almacena cero para el índice de inicio y vectores de longitud cero para los vectores de longitud e intervalo. El segundo constructor almacena *_StartIndex* para el índice de inicio, *_LenArray* para la matriz de longitud y *_IncArray* para la matriz de STRIDE.

### <a name="remarks"></a>Observaciones

**gslice** define un subconjunto de una valarray que consta de varios segmentos de la valarray que empiezan en el mismo elemento especificado. La capacidad de usar matrices para definir varios segmentos es la única diferencia entre `gslice` y [slice::slice](../standard-library/slice-class.md#slice). El primer segmento tiene un primer elemento con un índice de *_StartIndex*, un número de elementos especificado por el primer elemento de *_LenArray*y un intervalo proporcionado por el primer elemento de *_IncArray*. El siguiente conjunto de segmentos ortogonales tiene primeros elementos proporcionados por el primer segmento. El segundo elemento de *_LenArray* especifica el número de elementos. El intervalo lo proporciona el segundo elemento de *_IncArray*. Una tercera dimensión de segmentos podría tomar los elementos de la matriz bidimensional como los elementos de inicio y continuar de forma análoga

### <a name="example"></a>Ejemplo

```cpp
// gslice_ctor.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:" << endl << "(";
   for ( i = 0 ; i < 20 ; i++ )
      cout << " " << va [ i ];
   cout << " )" << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];

   cout << "The valarray for vaGSlice is vaResult:" << endl
        << "va[vaGSlice] = (";

   for ( i = 0 ; i < 8 ; i++ )
      cout << " " << vaResult [ i ];
   cout << ")" << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 )
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19)
```

## <a name="size"></a>  gslice::size

Busca los valores de la matriz al especificar el número de elementos de un segmento general de una valarray.

```cpp
valarray<size_t> size() const;
```

### <a name="return-value"></a>Valor devuelto

Valarray que especifica el número de elementos de cada segmento de un segmento general de una valarray.

### <a name="remarks"></a>Observaciones

La función miembro devuelve las longitudes almacenadas de los segmentos.

### <a name="example"></a>Ejemplo

```cpp
// gslice_size.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;
   size_t sizeVA;

   valarray<int> va ( 20 ), vaResult;
   for ( i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   sizeVA = va.size ( );
   cout << "The size of the valarray is: "
        << sizeVA << "." << endl << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> sizeGS = vaGSlice.size ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The size of vaResult is:"
        << "\n vaGSlice.size ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << sizeGS[ i ] << " ";
   cout << ")." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The size of the valarray is: 20.

The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The size of vaResult is:
vaGSlice.size ( ) = ( 4 4 ).
```

## <a name="start"></a>  gslice::start

Busca el índice inicial de un segmento general de una valarray.

```cpp
size_t start() const;
```

### <a name="return-value"></a>Valor devuelto

El índice inicial de un segmento general de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// gslice_start.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for ( i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   size_t vaGSstart = vaGSlice.start ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for (i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The index of the first element of vaResult is: "
        << vaGSstart << "." << endl;
}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The index of the first element of vaResult is: 0.
```

## <a name="stride"></a>  gslice::stride

Busca la distancia entre los elementos de un segmento general de una valarray.

```cpp
valarray<size_t> stride() const;
```

### <a name="return-value"></a>Valor devuelto

Valarray que especifica las distancias entre elementos de cada segmento de un segmento general de una valarray.

### <a name="example"></a>Ejemplo

```cpp
// gslice_stride.cpp
// compile with: /EHsc
#include <valarray>
#include <iostream>

int main( )
{
   using namespace std;
   int i;

   valarray<int> va ( 20 ), vaResult;
   for (i = 0 ; i < 20 ; i+=1 )
      va [ i ] =  i;

   cout << "The operand valarray va is:\n ( ";
      for (i = 0 ; i < 20 ; i++ )
         cout << va [ i ] << " ";
   cout << ")." << endl;

   valarray<size_t> Len ( 2 ), Stride ( 2 );
   Len [0] = 4;
   Len [1] = 4;
   Stride [0] = 7;
   Stride [1] = 4;

   gslice vaGSlice ( 0, Len, Stride );
   vaResult = va [ vaGSlice ];
   const valarray <size_t> strideGS = vaGSlice.stride ( );

   cout << "The valarray for vaGSlice is vaResult:"
        << "\n va[vaGSlice] = ( ";
      for ( i = 0 ; i < 8 ; i++ )
         cout << vaResult [ i ] << " ";
   cout << ")." << endl;

   cout << "The strides of vaResult are:"
        << "\n vaGSlice.stride ( ) = ( ";
      for ( i = 0 ; i < 2 ; i++ )
         cout << strideGS[ i ] << " ";
   cout << ")." << endl;

}
```

```Output
The operand valarray va is:
( 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ).
The valarray for vaGSlice is vaResult:
va[vaGSlice] = ( 0 4 8 12 7 11 15 19 ).
The strides of vaResult are:
vaGSlice.stride ( ) = ( 7 4 ).
```

## <a name="see-also"></a>Consulte también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
