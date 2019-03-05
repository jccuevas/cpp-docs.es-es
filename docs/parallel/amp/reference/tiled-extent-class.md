---
title: tiled_extent (Clase)
ms.date: 11/04/2016
f1_keywords:
- tiled_extent
- AMP/tiled_extent
- AMP/Concurrency::tiled_extent::tiled_extent
- AMP/Concurrency::tiled_extent::get_tile_extent
- AMP/Concurrency::tiled_extent::pad
- AMP/Concurrency::tiled_extent::truncate
- AMP/Concurrency::tiled_extent::tile_dim0
- AMP/Concurrency::tiled_extent::tile_dim1
- AMP/Concurrency::tiled_extent::tile_dim2
- AMP/Concurrency::tiled_extent::tile_extent
ms.assetid: 671ecaf8-c7b0-4ac8-bbdc-e30bd92da7c0
ms.openlocfilehash: 51e7696b8103e81d42beec0987a49f26fe041643
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264340"
---
# <a name="tiledextent-class"></a>tiled_extent (Clase)

Un `tiled_extent` objeto es un `extent` objeto de uno a tres dimensiones que divide el espacio de la extensión en una, dos o iconos tridimensionales.

### <a name="syntax"></a>Sintaxis

```
template <
    int _Dim0,
    int _Dim1,
    int _Dim2
>
class tiled_extent : public Concurrency::extent<3>;

template <
    int _Dim0,
    int _Dim1
>
class tiled_extent<_Dim0, _Dim1, 0> : public Concurrency::extent<2>;

template <
    int _Dim0
>
class tiled_extent<_Dim0, 0, 0> : public Concurrency::extent<1>;
```

### <a name="parameters"></a>Parámetros

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
|[tiled_extent (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `tiled_extent`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Devuelve un `extent` objeto que captura los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|
|[pad](#pad)|Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas para ser divisible por las dimensiones del mosaico.|
|[truncate](#truncate)|Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas a la baja para ser equitativamente divisibles por las dimensiones del icono.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `tiled_index` objeto en este.|

### <a name="public-constants"></a>Constantes públicas

|nombre|Descripción|
|----------|-----------------|
|[tile_dim0 (constante)](#tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 (constante)](#tile_dim1)|Almacena la longitud de la dimensión significativa más próxima.|
|[tile_dim2 (constante)](#tile_dim2)|Almacena la longitud de la dimensión menos significativa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un `extent` objeto que captura los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`extent`

`tiled_extent`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres**: simultaneidad

## <a name="ctor"> </a>  tiled_extent (Constructor)

Inicializa una nueva instancia de la clase `tiled_extent`.

### <a name="syntax"></a>Sintaxis

```
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El `extent` o `tiled_extent` objeto que se va a copiar.

## <a name="get_tile_extent"> </a>  get_tile_extent

Devuelve un `extent` objeto que captura los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Un `extent` objeto que captura las dimensiones de esta `tiled_extent` instancia.

## <a name="pad"> </a>  panel

Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas para ser divisible por las dimensiones del mosaico.

### <a name="syntax"></a>Sintaxis

```
tiled_extent pad() const;
```

### <a name="return-value"></a>Valor devuelto

El nuevo `tiled_extent` objeto por valor.
## <a name="truncate"> </a>  truncate

Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas a la baja para ser equitativamente divisibles por las dimensiones del icono.

### <a name="syntax"></a>Sintaxis

```
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un nuevo `tiled_extent` objeto con extensiones ajustadas a la baja para ser equitativamente divisibles por las dimensiones del icono.

## <a name="operator_eq"> </a>  operator=

Copia el contenido del elemento especificado `tiled_index` objeto en este.

### <a name="syntax"></a>Sintaxis

```
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
La `tiled_index` objeto que se va a copiar desde.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `tiled_index` instancia.

## <a name="tile_dim0"> </a>  tile_dim0

Almacena la longitud de la dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"> </a>  tile_dim1

Almacena la longitud de la dimensión significativa más próxima.

### <a name="syntax"></a>Sintaxis

```
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"> </a>  tile_dim2

Almacena la longitud de la dimensión menos significativa.

### <a name="syntax"></a>Sintaxis

```
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"> </a>  tile_extent
  Obtiene un `extent` objeto que captura los valores de la `tiled_extent` argumentos de plantilla `_Dim0`, `_Dim1`, y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
