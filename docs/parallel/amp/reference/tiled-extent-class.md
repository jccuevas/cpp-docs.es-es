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
ms.openlocfilehash: ce2710da1a745efedcd6e9e524355eda41e26de2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374710"
---
# <a name="tiled_extent-class"></a>tiled_extent (Clase)

Un `tiled_extent` objeto `extent` es un objeto de una a tres dimensiones que subdivide el espacio de extensión en teselas de una, dos o tres dimensiones.

## <a name="syntax"></a>Sintaxis

```cpp
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
La longitud de la dimensión próxima a la más significativa.

*_Dim2*<br/>
La longitud de la dimensión menos significativa.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor tiled_extent](#ctor)|Inicializa una nueva instancia de la clase `tiled_extent`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Devuelve `extent` un objeto que captura `tiled_extent` los valores `_Dim0` `_Dim1`de `_Dim2`los argumentos de plantilla , , y .|
|[Almohadilla](#pad)|Devuelve un `tiled_extent` nuevo objeto con extensiones ajustadas para que sean uniformemente divisibles por las dimensiones de teselas.|
|[Truncar](#truncate)|Devuelve un `tiled_extent` nuevo objeto con extensiones ajustadas para que sean uniformemente divisibles por las cotas de teselas.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador](#operator_eq)|Copia el contenido del `tiled_index` objeto especificado en éste.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[tile_dim0 Constante](#tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 Constante](#tile_dim1)|Almacena la longitud de la dimensión próxima a la más significativa.|
|[tile_dim2 Constante](#tile_dim2)|Almacena la longitud de la dimensión menos significativa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un `extent` objeto que captura los `tiled_extent` valores `_Dim0`de `_Dim1`los `_Dim2`argumentos de plantilla , , y .|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`extent`

`tiled_extent`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrencia

## <a name="tiled_extent-constructor"></a><a name="ctor"> </a> Constructor tiled_extent

Inicializa una nueva instancia de la clase `tiled_extent`.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent();

tiled_extent(
    const Concurrency::extent<rank>& _Other );

tiled_extent(
    const tiled_extent& _Other );
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El `extent` `tiled_extent` objeto u que se va a copiar.

## <a name="get_tile_extent"></a><a name="get_tile_extent"> </a> get_tile_extent

Devuelve `extent` un objeto que captura `tiled_extent` los valores `_Dim0` `_Dim1`de `_Dim2`los argumentos de plantilla , , y .

### <a name="syntax"></a>Sintaxis

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Objeto `extent` que captura las dimensiones de esta `tiled_extent` instancia.

## <a name="pad"></a><a name="pad"> </a> almohadilla

Devuelve un `tiled_extent` nuevo objeto con extensiones ajustadas para que sean uniformemente divisibles por las dimensiones de teselas.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Valor devuelto

El `tiled_extent` nuevo objeto, por valor.

## <a name="truncate"></a><a name="truncate"> </a> truncar

Devuelve un `tiled_extent` nuevo objeto con extensiones ajustadas para que sean uniformemente divisibles por las cotas de teselas.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `tiled_extent` nuevo objeto con extensiones ajustadas para que sean uniformemente divisibles por las cotas de teselas.

## <a name="operator"></a><a name="operator_eq"> </a> operador

Copia el contenido del `tiled_index` objeto especificado en éste.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto `tiled_index` desde el que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Una referencia `tiled_index` a esta instancia.

## <a name="tile_dim0"></a><a name="tile_dim0"> </a> tile_dim0

Almacena la longitud de la dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a><a name="tile_dim1"> </a> tile_dim1

Almacena la longitud de la dimensión próxima a la más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a><a name="tile_dim2"> </a> tile_dim2

Almacena la longitud de la dimensión menos significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a><a name="tile_extent"> </a> tile_extent

Obtiene un `extent` objeto que captura los `tiled_extent` valores `_Dim0`de `_Dim1`los `_Dim2`argumentos de plantilla , , y .

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
