---
title: texture_view (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- texture_view
- AMP_GRAPHICS/texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::texture_view
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_alpha
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_blue
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_green
- AMP_GRAPHICS/Concurrency::graphics::texture_view::gather_red
- AMP_GRAPHICS/Concurrency::graphics::texture_view::get
- AMP_GRAPHICS/Concurrency::graphics::texture_view::sample
- AMP_GRAPHICS/Concurrency::graphics::texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::texture_view::value_type
dev_langs:
- C++
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8a87c303d4527f89a7d7f59b69b3cc8572e0e7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387412"
---
# <a name="textureview-class"></a>texture_view (Clase)

Proporciona acceso de lectura y escritura a una textura. `texture_view` solo puede usarse para leer texturas cuyo tipo de valor es `int`, `unsigned int`, o `float` que tienen bpse de 32 bits de forma predeterminada. Para leer otros formatos de textura, utilice `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Sintaxis

```
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

#### <a name="parameters"></a>Parámetros

*value_type*<br/>
El tipo de los elementos del agregado de texturas.

*_Rank*<br/>
El rango de la `texture_view`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`value_type`|El tipo de los elementos de los agregados de texturas.|
|`coordinates_type`|El tipo de la coordenada utilizado para especificar un texel en la `texture_view`, es decir, un `short_vector` que tiene el mismo rango que la textura asociada que tiene un tipo de valor de `float`.|
|`gather_return_type`|El tipo de valor devuelto se utiliza para operaciones de recopilación, es decir, un rango 4 `short_vector` que contiene los cuatro componentes de color homogéneos recopilados desde los cuatro valores de texel muestreados.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[texture_view (Constructor)](#ctor)|Sobrecargado. Construye un `texture_view` instancia.|
|[~ texture_view (destructor)](#ctor)|Destruye el `texture_view` instancia.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura muestreados.|
|[gather_blue](#gather_blue)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes azul (z) de los cuatro elementos de textura muestreados.|
|[gather_green](#gather_green)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes verde (y) de los cuatro elementos de textura muestreados.|
|[gather_red](#gather_red)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura muestreados.|
|[get](#get)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[Ejemplo](#sample)|Sobrecargado. Muestrea la textura en el nivel de detalle y las coordenadas especificadas mediante la configuración de muestreo especificada.|
|[set](#set)|Establece el valor de un elemento por índice.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[Operator()](#operator_call)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[operator[]](#operator_at)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[value_type](#value_type)|El tipo de valor de los elementos de la `texture_view`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Namespace:** Concurrency:: Graphics

##  <a name="dtor"></a> ~ texture_view

Destruye el `texture_view` instancia.

```
~texture_view() restrict(amp, cpu);
```

##  <a name="ctor"></a> texture_view

Construye un `texture_view` instancia.

```
texture_view(// [1] constructor
    texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [2] constructor
    texture<value_type, _Rank>& _Src,
    unsigned int _Mipmap_level = 0) restrict(cpu);

texture_view(// [3] constructor
    const texture<value_type, _Rank>& _Src) restrict(amp);

texture_view(// [4] constructor
    const texture<value_type, _Rank>& _Src,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);

texture_view(// [5] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [6] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view(// [7] copy constructor
    const texture_view<const value_type, _Rank>& _Other,
    unsigned int _Most_detailed_mip,
    unsigned int _Mip_levels) restrict(cpu);
```

### <a name="parameters"></a>Parámetros

*_Src*<br/>
[1, 2] Constructor la `texture` en el que la escritura `texture_view` se crea.

[3, 4] Constructor la `texture` en el que el no modificable `texture_view` se crea.

*_Otro*<br/>
[5] Constructor de copia el origen de escritura `texture_view`.

[6, 7] El origen no modificable del Constructor de copias `texture_view`.

*_Mipmap_level*<br/>
El nivel del mipmap concreto en el origen de `texture` grabable que este `texture_view` se enlaza. El valor predeterminado es 0, que representa el nivel de mip (más detallado) de nivel superior.

*_Most_detailed_mip*<br/>
Top (más detallado) nivel de mip para la vista, en relación con el especificado `texture_view` objeto.

*_Mip_levels*<br/>
El número de niveles de mipmap accesibles a través de la `texture_view`.

##  <a name="gather_red"></a> gather_red

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura muestreados.

```
const gather_return_type gather_red(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_red(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Address_mode*<br/>
Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de direccionamiento es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra para usar a muestra la `texture_view`.

*_Coord*<br/>
Las coordenadas para la toma el ejemplo. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente rojo (x) de los 4 valores de texel muestreados.

##  <a name="gather_green"></a> gather_green

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes verde (y) de los cuatro elementos de textura muestreados.

```
const gather_return_type gather_green(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_green(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Address_mode*<br/>
Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de direccionamiento es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra para usar a muestra la `texture_view`.

*_Coord*<br/>
Las coordenadas para la toma el ejemplo. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente verde (y) de los 4 valores de texel muestreados.

##  <a name="gather_blue"></a> gather_blue

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes azul (z) de los cuatro elementos de textura muestreados.

```
const gather_return_type gather_blue(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_blue(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Address_mode*<br/>
Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de direccionamiento es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra para usar a muestra la `texture_view`.

*_Coord*<br/>
Las coordenadas para la toma el ejemplo. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente rojo (x) de los 4 valores de texel muestreados.

##  <a name="gather_alpha"></a> gather_alpha

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura muestreados.

```
const gather_return_type gather_alpha(
    const sampler& _Sampler,
    const coordinates_type& _Coord) const restrict(amp);

template<
    address_mode _Address_mode = address_clamp
>
const gather_return_type gather_alpha(
    const coordinates_type& _Coord) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Address_mode*<br/>
Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de direccionamiento es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra para usar a muestra la `texture_view`.

*_Coord*<br/>
Las coordenadas para la toma el ejemplo. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un corto de rango 4 vector que contiene la versión alfa (w) componente de los 4 valores de texel muestreados.

##  <a name="get"></a> Obtener

Obtiene el valor del elemento en el índice especificado.

```
const value_type get(
    const index<_Rank>& _Index) const restrict(amp);

value_type get(
    const index<_Rank>& _Index,
    unsigned int _Mip_level = 0) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento que se va a obtener, posiblemente multidimensional.

*_Mip_level*<br/>
El nivel del mipmap desde el que debemos obtener el valor. El valor predeterminado 0 representa el nivel del mipmap más detallado.

### <a name="return-value"></a>Valor devuelto

Valor del elemento.

##  <a name="operator_eq"></a> operator=

Asigna una vista de la misma textura especificado `texture_view` a este `texture_view` instancia.

```
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Otro*<br/>
[1, 2] Constructor de copias de una escritura `texture_view` objeto.

[3] Constructor de copia A no modificable `texture_view` objeto.

### <a name="return-value"></a>Valor devuelto

Una referencia a este `texture_view` instancia.

##  <a name="operator_at"></a> operator]

Devuelve el valor del elemento por índice.

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice, posiblemente multidimensional.

*_I0*<br/>
El índice unidimensional.

### <a name="return-value"></a>Valor devuelto

El valor del elemento indizado por `_Index`.

##  <a name="operator_call"></a> Operator()

Devuelve el valor del elemento por índice.

```
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,   int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);

value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

value_type operator() (
    int _I0) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
El índice, posiblemente multidimensional.

*_I0*<br/>
El componente más significativo del índice.

*_I1*<br/>
El siguiente-a-componente más significativo del índice.

*_I2*<br/>
El componente menos significativo del índice.

### <a name="return-value"></a>Valor devuelto

El valor del elemento indizado por `_Index`.

##  <a name="sample"></a> Ejemplo

Muestrea la textura en el nivel de detalle y las coordenadas especificadas mediante la configuración de muestreo especificada.

```
value_type sample(
    const sampler& _Sampler,
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);

template<
    filter_mode _Filter_mode = filter_linear,
    address_mode _Address_mode = address_clamp
>
value_type sample(
    const coordinates_type& _Coord,
    float _Level_of_detail = 0.0f) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Filter_mode*<br/>
Modo de filtro que se va a usar para el muestreo de texture_view. El modo de filtro es el mismo para la minimización, maximización y los filtros de mipmap.

*_Address_mode*<br/>
El modo de direccionamiento a usar para el muestreo de texture_view. El modo de direccionamiento es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra se utiliza para el muestreo de texture_view.

*_Coord*<br/>
Las coordenadas para la toma el ejemplo. Los valores de coordenadas fraccionarios se utilizan para interpolar entre valores de texel.

*_Level_of_detail*<br/>
El valor especifica el nivel del mipmap de muestra de. Los valores fraccionarios se utilizan para interpolar entre dos niveles de mipmap. El nivel de detalle predeterminado es 0, que representa el nivel de mip más detallado.

### <a name="return-value"></a>Valor devuelto

El valor de ejemplo interpolado.

##  <a name="set"></a> Conjunto

Establece el valor del elemento en el índice especificado en el valor especificado.

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento que se va a establecer, posiblemente multidimensional.

*valor*<br/>
Valor que se establecerá el elemento.

##  <a name="value_type"></a> value_type

El tipo de valor de los elementos de texture_view.

```
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
