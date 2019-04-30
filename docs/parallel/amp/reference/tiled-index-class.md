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
ms.openlocfilehash: dd8b6d7a0e174c88ad229da2d08a9ec8a11fb0aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352195"
---
# <a name="tiledindex-class"></a>tiled_index (Clase)

Proporciona un índice en una [tiled_extent](tiled-extent-class.md) objeto. Esta clase tiene propiedades para tener acceso a elementos relacionados con el origen local del mosaico y con el origen global. Para obtener más información sobre los espacios de mosaico, vea [usando iconos](../../../parallel/amp/using-tiles.md).

## <a name="syntax"></a>Sintaxis

```
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

#### <a name="parameters"></a>Parámetros

*_Dim0*<br/>
La longitud de la dimensión más significativa.

*_Dim1*<br/>
La longitud de la dimensión significativa más próxima.

*_Dim2*<br/>
La longitud de la dimensión menos significativa.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[tiled_index (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `tile_index`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Devuelve un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|

### <a name="public-constants"></a>Constantes públicas

|Name|Descripción|
|----------|-----------------|
|[Constante de barrera](#tiled_index__barrier)|Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.|
|||
|[Constante global](#tiled_index__global)|Almacena un [índice](index-class.md) objeto del rango 1, 2 o 3 que representa el índice global en un objeto de cuadrícula.|
|[Constante local](#tiled_index__local)|Almacena un `index` objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.|
|[rank Constant](#tiled_index__rank)|Almacena el rango de la `tiled_index` objeto.|
|[Tile (constante)](#tiled_index__tile)|Almacena un `index` objeto del rango 1, 2 ó 3 que representa las coordenadas del mosaico actual de un `tiled_extent` objeto.|
|[tile_dim0 (constante)](#tiled_index__tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 (constante)](#tiled_index__tile_dim1)|Almacena la longitud de la dimensión significativa más próxima.|
|[tile_dim2 (constante)](#tiled_index__tile_dim2)|Almacena la longitud de la dimensión menos significativa.|
|[tile_origin (constante)](#tiled_index__tile_origin)|Almacena un `index` objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen del mosaico actual en un `tiled_extent` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres**: simultaneidad

## <a name="ctor"></a>  tiled_index (Constructor)

Inicializa una nueva instancia de la clase `tiled_index`.

## <a name="syntax"></a>Sintaxis

```
tiled_index(
    const index<rank>& _Global,
    const index<rank>& _Local,
    const index<rank>& _Tile,
    const index<rank>& _Tile_origin,
    const tile_barrier& _Barrier ) restrict(amp,cpu);

tiled_index(
    const tiled_index& _Other ) restrict(amp,cpu);
```

#### <a name="parameters"></a>Parámetros

*_Global*<br/>
Global [índice](index-class.md) de construido `tiled_index`.

*_Local*<br/>
Local [índice](index-class.md) de construido `tiled_index`

*_Tile*<br/>
El icono de [índice](index-class.md) de construido `tiled_index`

*_Tile_origin*<br/>
El origen del mosaico [índice](index-class.md) de construido `tiled_index`

*_Barrier*<br/>
El [tile_barrier](tile-barrier-class.md) objeto de construido `tiled_index`.

*_Other*<br/>
El `tile_index` objeto va a copiar a construido `tiled_index`.

## <a name="overloads"></a>Overloads

|||
|-|-|
|Name|Descripción|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase desde el índice de mosaico en coordenadas globales y la posición relativa en el mosaico en coordenadas locales. El `_Global` y `_Tile_origin` se calculan los parámetros.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa una nueva instancia de la `tile_index` clase copiando especificado `tiled_index` objeto.|

## <a name="tiled_index__get_tile_extent"></a>  get_tile_extent

Devuelve un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.

## <a name="syntax"></a>Sintaxis

```
extent<rank> get_tile_extent()restrict(amp,cpu);
```

## <a name="return-value"></a>Valor devuelto

Un `extent` objeto que tiene los valores de la `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.

## <a name="tiled_index__barrier"></a>  barrier

Almacena un [tile_barrier](tile-barrier-class.md) objeto que representa una barrera en el mosaico actual de subprocesos.

## <a name="syntax"></a>Sintaxis

```
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>  global

Almacena un [índice](index-class.md) objeto del rango 1, 2 o 3 que representa el índice de un objeto global.

## <a name="syntax"></a>Sintaxis

```
const index<rank> global;
```

## <a name="tiled_index__local"></a>  local

Almacena un [índice](index-class.md) objeto de índice de rango 1, 2 o 3 que representa la relación en el mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```
const index<rank> local;
```

## <a name="tiled_index__rank"></a>  rank

Almacena el rango de la `tiled_index` objeto.

## <a name="syntax"></a>Sintaxis

```
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>  icono

Almacena un [índice](index-class.md) objeto del rango 1, 2 ó 3 que representa las coordenadas del mosaico actual de un [tiled_extent](tiled-extent-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>  tile_dim0

Almacena la longitud de la dimensión más significativa.

## <a name="syntax"></a>Sintaxis

```
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>  tile_dim1

Almacena la longitud de la dimensión significativa más próxima.

## <a name="syntax"></a>Sintaxis

```
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>  tile_dim2

Almacena la longitud de la dimensión menos significativa.

## <a name="syntax"></a>Sintaxis

```
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>  tile_origin

Almacena un [índice](index-class.md) objeto de coordenadas de rango 1, 2 o 3 que representa la información global del origen del mosaico actual dentro de un [tiled_extent](tiled-extent-class.md) objeto.

## <a name="syntax"></a>Sintaxis

```
const index<rank> tile_origin
```

## <a name="tile_extent"></a>  tile_extent
  Obtiene un [extensión](extent-class.md) objeto que tiene los valores de la `tiled_index` argumentos de plantilla `tiled_index` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.

## <a name="syntax"></a>Sintaxis

```
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
