---
title: tiled_index (Clase)
ms.date: 03/27/2019
f1_keywords:
- tiled_index
- AMP/tiled_index
- AMP/Concurrency::tiled_index::tiled_index
- AMP/Concurrency::tiled_index::get_tile_extent
- AMP/Concurrency::tiled_index::barrier
- AMP/Concurrency::tiled_index::global
- AMP/Concurrency::tiled_index::local
- AMP/Concurrency::tiled_index::rank
- AMP/Concurrency::tiled_index::tile
- AMP/Concurrency::tiled_index::tile_dim0
- AMP/Concurrency::tiled_index::tile_dim1
- AMP/Concurrency::tiled_index::tile_dim2
- AMP/Concurrency::tiled_index::tile_origin
- AMP/Concurrency::tiled_index::tile_extent
helpviewer_keywords:
- tiled_index class
ms.assetid: 0ce2ae26-f1bb-4436-b473-a9e1b619bb38
ms.openlocfilehash: 46a6b3548526f0917c4e022a12bf859242e70b20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375480"
---
# <a name="tiled_index-class"></a>tiled_index (Clase)

Proporciona un índice en un [objeto tiled_extent.](tiled-extent-class.md) Esta clase tiene propiedades para tener acceso a elementos relativos al origen de teselas local y en relación con el origen global. Para obtener más información acerca de los espacios en mosaico, consulte [Uso de mosaicos](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <
    int _Dim0,
    int _Dim1 = 0,
    int _Dim2 = 0
>
class tiled_index : public _Tiled_index_base<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_index<_Dim0, _Dim1, 0> : public _Tiled_index_base<2>;

template <
    int _Dim0
>
class tiled_index<_Dim0, 0, 0> : public _Tiled_index_base<1>;
```

### <a name="parameters"></a>Parámetros

*_Dim0*<br/>
La longitud de la dimensión más significativa.

*_Dim1*<br/>
La longitud de la dimensión próxima a la más significativa.

*_Dim2*<br/>
La longitud de la dimensión menos significativa.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor tiled_index](#ctor)|Inicializa una nueva instancia de la clase `tile_index`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Devuelve un objeto [extent](extent-class.md) que `tiled_index` tiene los `_Dim0` `_Dim1`valores `_Dim2`de los argumentos de plantilla , , y .|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[barrera Constante](#tiled_index__barrier)|Almacena un [objeto tile_barrier](tile-barrier-class.md) que representa una barrera en el mosaico actual de subprocesos.|
|||
|[Constant global](#tiled_index__global)|Almacena un objeto de [índice](index-class.md) de rango 1, 2 o 3 que representa el índice global en un objeto de cuadrícula.|
|[local (Constante)](#tiled_index__local)|Almacena `index` un objeto de rango 1, 2 o 3 que representa el índice relativo en el icono actual de un [objeto tiled_extent.](tiled-extent-class.md)|
|[rango Constante](#tiled_index__rank)|Almacena el rango `tiled_index` del objeto.|
|[azulejo Constante](#tiled_index__tile)|Almacena `index` un objeto de rango 1, 2 o 3 que representa `tiled_extent` las coordenadas del mosaico actual de un objeto.|
|[tile_dim0 Constante](#tiled_index__tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 Constante](#tiled_index__tile_dim1)|Almacena la longitud de la dimensión próxima a la más significativa.|
|[tile_dim2 Constante](#tiled_index__tile_dim2)|Almacena la longitud de la dimensión menos significativa.|
|[tile_origin Constante](#tiled_index__tile_origin)|Almacena `index` un objeto de rango 1, 2 o 3 que representa las coordenadas `tiled_extent` globales del origen del mosaico actual en un objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un objeto [extent](extent-class.md) que tiene `tiled_index` los `tiled_index` valores de `_Dim0` `_Dim1`los `_Dim2`argumentos de plantilla de argumentos de plantilla , , y .|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrencia

## <a name="tiled_index-constructor"></a><a name="ctor"></a>Constructor tiled_index

Inicializa una nueva instancia de la clase `tiled_index`.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Global*<br/>
El [índice](index-class.md) global del `tiled_index`archivo .

*_Local*<br/>
El [índice](index-class.md) local de la construcción`tiled_index`

*_Tile*<br/>
El [índice](index-class.md) de teselas de la`tiled_index`

*_Tile_origin*<br/>
El [índice](index-class.md) de origen de teselas de la`tiled_index`

*_Barrier*<br/>
El objeto [tile_barrier](tile-barrier-class.md) del `tiled_index`archivo .

*_Other*<br/>
Objeto `tile_index` que se va a `tiled_index`copiar en el archivo .

### <a name="overloads"></a>Overloads

|||
|-|-|
|Nombre|Descripción|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa una nueva instancia `tile_index` de la clase desde el índice del icono en coordenadas globales y la posición relativa en el icono en coordenadas locales. Se `_Global` `_Tile_origin` calculan los parámetros y.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa una nueva instancia `tile_index` de la clase `tiled_index` copiando el objeto especificado.|

## <a name="get_tile_extent"></a><a name="tiled_index__get_tile_extent"></a>get_tile_extent

Devuelve un objeto [extent](extent-class.md) que `tiled_index` tiene los `_Dim0` `_Dim1`valores `_Dim2`de los argumentos de plantilla , , y .

### <a name="syntax"></a>Sintaxis

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Objeto `extent` que tiene los `tiled_index` valores de `_Dim0` `_Dim1`los `_Dim2`argumentos de plantilla , , y .

## <a name="barrier"></a><a name="tiled_index__barrier"></a>Barrera

Almacena un [objeto tile_barrier](tile-barrier-class.md) que representa una barrera en el mosaico actual de subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
const tile_barrier barrier;
```

## <a name="global"></a><a name="tiled_index__global"></a>Global

Almacena un objeto de [índice](index-class.md) de rango 1, 2 o 3 que representa el índice global de un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> global;
```

## <a name="local"></a><a name="tiled_index__local"></a>Local

Almacena un objeto de [índice](index-class.md) de rango 1, 2 o 3 que representa el índice relativo en el icono actual de un objeto [tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> local;
```

## <a name="rank"></a><a name="tiled_index__rank"></a>rango

Almacena el rango `tiled_index` del objeto.

### <a name="syntax"></a>Sintaxis

```cpp
static const int rank = _Rank;
```

## <a name="tile"></a><a name="tiled_index__tile"></a>Azulejo

Almacena un objeto de [índice](index-class.md) de rango 1, 2 o 3 que representa las coordenadas del icono actual de un objeto [tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> tile;
```

## <a name="tile_dim0"></a><a name="tiled_index__tile_dim0"></a>tile_dim0

Almacena la longitud de la dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tiled_index__tile_dim1"></a>tile_dim1

Almacena la longitud de la dimensión próxima a la más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tiled_index__tile_dim2"></a>tile_dim2

Almacena la longitud de la dimensión menos significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_origin"></a><a name="tiled_index__tile_origin"></a>tile_origin

Almacena un objeto de [índice](index-class.md) de rango 1, 2 o 3 que representa las coordenadas globales del origen del mosaico actual dentro de un objeto [tiled_extent.](tiled-extent-class.md)

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a><a name="tile_extent"></a>tile_extent

Obtiene un objeto [extent](extent-class.md) que tiene `tiled_index` los `tiled_index` valores de `_Dim0` `_Dim1`los `_Dim2`argumentos de plantilla de argumentos de plantilla , , y .

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
