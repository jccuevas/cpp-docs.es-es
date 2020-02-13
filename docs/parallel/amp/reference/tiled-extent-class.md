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
ms.openlocfilehash: e2248c770c7eedde59d1cb592f7d5d7c1bfbde9a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126427"
---
# <a name="tiled_extent-class"></a>tiled_extent (Clase)

Un objeto `tiled_extent` es un objeto `extent` de una a tres dimensiones que divide el espacio de la extensión en mosaicos de una, dos o tres dimensiones.

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
La longitud de la dimensión siguiente a la más significativa.

*_Dim2*<br/>
La longitud de la dimensión menos significativa.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de tiled_extent](#ctor)|Inicializa una nueva instancia de la clase `tiled_extent`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[get_tile_extent](#get_tile_extent)|Devuelve un objeto `extent` que captura los valores de los argumentos de plantilla `tiled_extent` `_Dim0`, `_Dim1`y `_Dim2`.|
|[plataforma](#pad)|Devuelve un nuevo objeto de `tiled_extent` con extensiones ajustadas para que las dimensiones del mosaico sean divisible uniformemente.|
|[truncate](#truncate)|Devuelve un nuevo objeto de `tiled_extent` con extensiones ajustadas hacia abajo para que las dimensiones del mosaico sean divisible uniformemente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Copia el contenido del objeto `tiled_index` especificado en este.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[tile_dim0 constante)](#tile_dim0)|Almacena la longitud de la dimensión más significativa.|
|[tile_dim1 constante)](#tile_dim1)|Almacena la longitud de la siguiente dimensión más significativa.|
|[tile_dim2 constante)](#tile_dim2)|Almacena la longitud de la dimensión menos significativa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[tile_extent](#tile_extent)|Obtiene un objeto `extent` que captura los valores de los argumentos de plantilla `tiled_extent` `_Dim0`, `_Dim1`y `_Dim2`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`extent`

`tiled_extent`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="ctor"></a> Constructor de tiled_extent

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
`extent` o `tiled_extent` objeto que se va a copiar.

## <a name="get_tile_extent"></a> get_tile_extent

Devuelve un objeto `extent` que captura los valores de los argumentos de plantilla `tiled_extent` `_Dim0`, `_Dim1`y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```cpp
Concurrency::extent<rank> get_tile_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>Valor devuelto

Objeto `extent` que captura las dimensiones de esta instancia de `tiled_extent`.

## <a name="pad"></a> panel de control

Devuelve un nuevo objeto de `tiled_extent` con extensiones ajustadas para que las dimensiones del mosaico sean divisible uniformemente.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent pad() const;
```

### <a name="return-value"></a>Valor devuelto

Nuevo objeto de `tiled_extent`, por valor.
## <a name="truncate"></a> truncar

Devuelve un nuevo objeto de `tiled_extent` con extensiones ajustadas hacia abajo para que las dimensiones del mosaico sean divisible uniformemente.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent truncate() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve un nuevo objeto de `tiled_extent` con extensiones ajustadas hacia abajo para que las dimensiones del mosaico sean divisible uniformemente.

## <a name="operator_eq"></a> operador =

Copia el contenido del objeto `tiled_index` especificado en este.

### <a name="syntax"></a>Sintaxis

```cpp
tiled_extent&  operator= (
    const tiled_extent& _Other ) restrict (amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
Objeto de `tiled_index` del que se va a copiar.

### <a name="return-value"></a>Valor devuelto

Referencia a esta instancia de `tiled_index`.

## <a name="tile_dim0"></a> tile_dim0

Almacena la longitud de la dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim0 = _Dim0;
```

## <a name="tile_dim1"></a> tile_dim1

Almacena la longitud de la siguiente dimensión más significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim1 = _Dim1;
```

## <a name="tile_dim2"></a> tile_dim2

Almacena la longitud de la dimensión menos significativa.

### <a name="syntax"></a>Sintaxis

```cpp
static const int tile_dim2 = _Dim2;
```

## <a name="tile_extent"></a> tile_extent
  Obtiene un objeto `extent` que captura los valores de los argumentos de plantilla `tiled_extent` `_Dim0`, `_Dim1`y `_Dim2`.

### <a name="syntax"></a>Sintaxis

```cpp
__declspec(property(get= get_tile_extent)) Concurrency::extent<rank> tile_extent;
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
