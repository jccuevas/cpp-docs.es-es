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
ms.openlocfilehash: eda01667a6b239284c682ba6ae3f9b857c713447
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142423"
---
# <a name="tiled_index-class"></a>tiled_index (Clase)

Proporciona un índice en un objeto [tiled_extent](tiled-extent-class.md) . Esta clase tiene propiedades para tener acceso a los elementos relacionados con el origen del mosaico local y con respecto al origen global. Para obtener más información sobre los espacios en mosaico, vea [usar iconos](../../../parallel/amp/using-tiles.md).

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
La longitud de la dimensión siguiente a la más significativa.

*_Dim2*<br/>
La longitud de la dimensión menos significativa.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de tiled_index](#ctor)|Inicializa una nueva instancia de la clase `tile_index`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_tile_extent](#tiled_index__get_tile_extent)|Devuelve un objeto de [extensión](extent-class.md) que tiene los valores de los argumentos de plantilla `tiled_index` `_Dim0`, `_Dim1`y `_Dim2`.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[Constante de barrera](#tiled_index__barrier)|Almacena un objeto [tile_barrier](tile-barrier-class.md) que representa una barrera en el mosaico actual de subprocesos.|
|||
|[Constante global](#tiled_index__global)|Almacena un objeto de [Índice](index-class.md) de rango 1, 2 ó 3 que representa el índice global de un objeto Grid.|
|[Constante local](#tiled_index__local)|Almacena un objeto `index` de los rangos 1, 2 o 3 que representa el Índice relativo en el mosaico actual de un objeto [tiled_extent](tiled-extent-class.md) .|
|[Rank (constante)](#tiled_index__rank)|Almacena el rango del objeto `tiled_index`.|
|[Tile (constante)](#tiled_index__tile)|Almacena un objeto `index` de los rangos 1, 2 o 3 que representa las coordenadas del mosaico actual de un objeto `tiled_extent`.|
|[tile_dim0 constante)](#tiled_index__tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 constante)](#tiled_index__tile_dim1)|Almacena la longitud de la siguiente dimensión más significativa.|
|[tile_dim2 constante)](#tiled_index__tile_dim2)|Almacena la longitud de la dimensión menos significativa.|
|[tile_origin constante)](#tiled_index__tile_origin)|Almacena un objeto `index` de los rangos 1, 2 o 3 que representa las coordenadas globales del origen del mosaico actual en un objeto `tiled_extent`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un objeto de [extensión](extent-class.md) que tiene los valores de los argumentos de plantilla `tiled_index` `tiled_index` los argumentos de plantilla `_Dim0`, `_Dim1`y `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Tiled_index_base`

`tiled_index`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="ctor"></a>Constructor de tiled_index

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
[Índice](index-class.md) global del `tiled_index`construido.

*_Local*<br/>
[Índice](index-class.md) local del `tiled_index` construido.

*_Tile*<br/>
[Índice](index-class.md) del mosaico del `tiled_index` construido.

*_Tile_origin*<br/>
[Índice](index-class.md) de origen del mosaico del `tiled_index` construido

*_Barrier*<br/>
Objeto [tile_barrier](tile-barrier-class.md) del `tiled_index`construido.

*_Other*<br/>
Objeto `tile_index` que se va a copiar en el `tiled_index`construido.

### <a name="overloads"></a>Overloads

|||
|-|-|
|Nombre|Descripción|
|`tiled_index(const index<rank>& _Global, const index<rank>& _Local, const index<rank>& _Tile, const index<rank>& _Tile_origin, const tile_barrier& _Barrier restrict(amp,cpu);`|Inicializa una nueva instancia de la clase `tile_index` a partir del índice del mosaico en coordenadas globales y la posición relativa en el mosaico en coordenadas locales. Se calculan los parámetros `_Global` y `_Tile_origin`.|
|`tiled_index(    const tiled_index& _Other) restrict(amp,cpu);`|Inicializa una nueva instancia de la clase `tile_index` copiando el objeto `tiled_index` especificado.|

## <a name="tiled_index__get_tile_extent"></a>get_tile_extent

Devuelve un objeto de [extensión](extent-class.md) que tiene los valores de los argumentos de plantilla `tiled_index` `_Dim0`, `_Dim1`y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```cpp
extent<rank> get_tile_extent()restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Objeto `extent` que tiene los valores de los argumentos de plantilla `tiled_index` `_Dim0`, `_Dim1`y `_Dim2`.

## <a name="tiled_index__barrier"></a>barreras

Almacena un objeto [tile_barrier](tile-barrier-class.md) que representa una barrera en el mosaico actual de subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
const tile_barrier barrier;
```

## <a name="tiled_index__global"></a>global

Almacena un objeto de [Índice](index-class.md) de rango 1, 2 ó 3 que representa el índice global de un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> global;
```

## <a name="tiled_index__local"></a>localizar

Almacena un objeto de [Índice](index-class.md) de rango 1, 2 ó 3 que representa el Índice relativo en el mosaico actual de un objeto [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> local;
```

## <a name="tiled_index__rank"></a>criterios

Almacena el rango del objeto `tiled_index`.

### <a name="syntax"></a>Sintaxis

```cpp
static const int rank = _Rank;
```

## <a name="tiled_index__tile"></a>posición

Almacena un objeto de [Índice](index-class.md) de rango 1, 2 ó 3 que representa las coordenadas del mosaico actual de un objeto [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> tile;
```

## <a name="tiled_index__tile_dim0"></a>tile_dim0

Almacena la longitud de la dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tiled_index__tile_dim1"></a>tile_dim1

Almacena la longitud de la siguiente dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tiled_index__tile_dim2"></a>tile_dim2

Almacena la longitud de la dimensión menos significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tiled_index__tile_origin"></a>tile_origin

Almacena un objeto de [Índice](index-class.md) de rango 1, 2 ó 3 que representa las coordenadas globales del origen del mosaico actual dentro de un objeto [tiled_extent](tiled-extent-class.md) .

### <a name="syntax"></a>Sintaxis

```cpp
const index<rank> tile_origin
```

## <a name="tile_extent"></a>tile_extent

Obtiene un objeto de [extensión](extent-class.md) que tiene los valores de los argumentos de plantilla `tiled_index` `tiled_index` los argumentos de plantilla `_Dim0`, `_Dim1`y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_tile_extent)) extent<rank> tile_extent;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
