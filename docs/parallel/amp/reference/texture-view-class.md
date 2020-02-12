---
title: texture_view (Clase)
ms.date: 11/04/2016
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
ms.assetid: 6ec2e289-1626-4727-9592-07981cf1d27d
ms.openlocfilehash: 6bf4b9666d746199cea92fa2bd52b691c67e4a5b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126359"
---
# <a name="texture_view-class"></a>texture_view (Clase)

Proporciona acceso de lectura y acceso de escritura a una textura. `texture_view` solo se puede usar para leer texturas cuyo tipo de valor sea `int`, `unsigned int`o `float` que tengan valores de bpse de 32 bits predeterminados. Para leer otros formatos de textura, use `texture_view<const value_type, _Rank>`.

## <a name="syntax"></a>Sintaxis

```cpp
template<typename value_type,int _Rank>
class texture_view;

template<typename value_type, int _Rank>
class texture_view
   : public details::_Texture_base<value_type, _Rank>;

template<typename value_type, int _Rank>
class texture_view<const value_type, _Rank>
   : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>Parámetros

*value_type*<br/>
Tipo de los elementos del agregado de textura.

*_Rank*<br/>
Rango del `texture_view`.

## <a name="members"></a>Members

### <a name="public-typedefs"></a>Typedefs públicos

|Nombre|Descripción|
|----------|-----------------|
|`value_type`|Tipo de los elementos de los agregados de textura.|
|`coordinates_type`|El tipo de la coordenada que se usa para especificar un textura en el `texture_view`, es decir, un `short_vector` que tiene el mismo rango que la textura asociada que tiene un tipo de valor de `float`.|
|`gather_return_type`|El tipo de valor devuelto que se usa para las operaciones de recopilación, es decir, una `short_vector` de rango 4 que contiene los cuatro componentes de color homogéneos que se recopilan de los cuatro valores de textura muestreados.|

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de texture_view](#ctor)|Sobrecargado. Crea una instancia de `texture_view`.|
|[~ texture_view destructor](#ctor)|Destruye la instancia de `texture_view`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[gather_alpha](#gather_alpha)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro textura muestreados.|
|[gather_blue](#gather_blue)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes azules (z) de los cuatro textura muestreados.|
|[gather_green](#gather_green)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes verdes (y) de los cuatro textura muestreados.|
|[gather_red](#gather_red)|Sobrecargado. Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro textura muestreados.|
|[get](#get)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[sample](#sample)|Sobrecargado. Muestrea la textura en las coordenadas especificadas y el nivel de detalle mediante la configuración de muestreo especificada.|
|[set](#set)|Establece el valor de un elemento por índice.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator()](#operator_call)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[operator\[\]](#operator_at)|Sobrecargado. Obtiene el valor del elemento por índice.|
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[value_type](#value_type)|Tipo de valor de los elementos de la `texture_view`.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`_Texture_base`

`texture_view`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="dtor"></a>~ texture_view

Destruye la instancia de `texture_view`.

```cpp
~texture_view() restrict(amp, cpu);
```

## <a name="ctor"></a>texture_view

Crea una instancia de `texture_view`.

```cpp
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
[1,2] Constructor el `texture` en el que se crea el `texture_view` grabable.

[3,4] Constructor el `texture` en el que se crea el `texture_view` no grabable.

*_Other*<br/>
[5] constructor de copia el `texture_view`de escritura de origen.

[6, 7] Constructor de copias el `texture_view`de origen no grabable.

*_Mipmap_level*<br/>
Nivel de mipmap específico en el `texture` de origen al que se enlaza este `texture_view` grabable. El valor predeterminado es 0, que representa el nivel de MIP de nivel superior (más detallado).

*_Most_detailed_mip*<br/>
Nivel de MIP de nivel superior (más detallado) de la vista, en relación con el objeto de `texture_view` especificado.

*_Mip_levels*<br/>
El número de niveles de mipmap accesibles a través de la `texture_view`.

## <a name="gather_red"></a>gather_red

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro textura muestreados.

```cpp
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
Modo de dirección que se va a utilizar para muestrear el `texture_view`. El modo de dirección es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra que se va a usar para muestrear el `texture_view`.

*_Coord*<br/>
Coordenadas de las que se va a tomar la muestra. Los valores de coordenadas fraccionarios se utilizan para interpolar entre textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente rojo (x) de los 4 valores de textura muestreados.

## <a name="gather_green"></a>gather_green

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes verdes (y) de los cuatro textura muestreados.

```cpp
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
Modo de dirección que se va a utilizar para muestrear el `texture_view`. El modo de dirección es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra que se va a usar para muestrear el `texture_view`.

*_Coord*<br/>
Coordenadas de las que se va a tomar la muestra. Los valores de coordenadas fraccionarios se utilizan para interpolar entre textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente verde (y) de los 4 valores de textura muestreados.

## <a name="gather_blue"></a>gather_blue

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes azules (z) de los cuatro textura muestreados.

```cpp
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
Modo de dirección que se va a utilizar para muestrear el `texture_view`. El modo de dirección es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra que se va a usar para muestrear el `texture_view`.

*_Coord*<br/>
Coordenadas de las que se va a tomar la muestra. Los valores de coordenadas fraccionarios se utilizan para interpolar entre textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente rojo (x) de los 4 valores de textura muestreados.

## <a name="gather_alpha"></a>gather_alpha

Muestrea la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro textura muestreados.

```cpp
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
Modo de dirección que se va a utilizar para muestrear el `texture_view`. El modo de dirección es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra que se va a usar para muestrear el `texture_view`.

*_Coord*<br/>
Coordenadas de las que se va a tomar la muestra. Los valores de coordenadas fraccionarios se utilizan para interpolar entre textura de ejemplo.

### <a name="return-value"></a>Valor devuelto

Un vector corto de rango 4 que contiene el componente alfa (w) de los 4 valores de textura muestreados.

## <a name="get"></a>Obtener

Obtiene el valor del elemento en el índice especificado.

```cpp
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
Nivel de mipmap del que se debe obtener el valor. El valor predeterminado 0 representa el nivel de mipmap más detallado.

### <a name="return-value"></a>Valor devuelto

El valor del elemento.

## <a name="operator_eq"></a>operador =

Asigna a esta instancia de `texture_view` una vista de la misma textura que el `texture_view` especificado.

```cpp
texture_view<value_type, _Rank>& operator= (// [1] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(amp, cpu);

texture_view<const value_type, _Rank>& operator= (// [2] copy constructor
    const texture_view<value_type, _Rank>& _Other) restrict(cpu);

texture_view<const value_type, _Rank>& operator= (// [3] copy constructor
    const texture_view<const value_type, _Rank>& _Other) restrict(amp, cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
[1,2] El constructor de copia es un objeto de `texture_view` grabable.

[3] constructor de copias de un objeto de `texture_view` no grabable.

### <a name="return-value"></a>Valor devuelto

Referencia a esta instancia de `texture_view`.

## <a name="operator_at"></a>operador []

Devuelve el valor del elemento por índice.

```cpp
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);

value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice, posiblemente multidimensional.

*_I0*<br/>
Índice unidimensional.

### <a name="return-value"></a>Valor devuelto

Valor del elemento indizado por `_Index`.

## <a name="operator_call"></a>operador ()

Devuelve el valor del elemento por índice.

```cpp
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
Índice, posiblemente multidimensional.

*_I0*<br/>
Componente más significativo del índice.

*_I1*<br/>
El siguiente componente más significativo del índice.

*_I2*<br/>
El componente menos significativo del índice.

### <a name="return-value"></a>Valor devuelto

Valor del elemento indizado por `_Index`.

## <a name="sample"></a>AdventureWorks

Muestrea la textura en las coordenadas especificadas y el nivel de detalle mediante la configuración de muestreo especificada.

```cpp
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
Modo de filtro que se va a utilizar para muestrear el texture_view. El modo de filtro es el mismo para los filtros de minimización, maximización y mipmap.

*_Address_mode*<br/>
Modo de dirección que se va a utilizar para muestrear el texture_view. El modo de dirección es el mismo para todas las dimensiones.

*_Sampler*<br/>
La configuración de muestra que se va a usar para muestrear el texture_view.

*_Coord*<br/>
Coordenadas de las que se va a tomar la muestra. Los valores de coordenadas fraccionarios se utilizan para interpolar entre los valores de textura.

*_Level_of_detail*<br/>
El valor especifica el nivel de mipmap del que se va a muestrear. Los valores fraccionarios se utilizan para interpolar entre dos niveles de mipmap. El nivel de detalle predeterminado es 0, que representa el nivel de MIP más detallado.

### <a name="return-value"></a>Valor devuelto

Valor de ejemplo interpolado.

## <a name="set"></a>conjunto

Establece el valor del elemento en el índice especificado en el valor especificado.

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Index*<br/>
Índice del elemento que se va a establecer, posiblemente multidimensional.

*value*<br/>
Valor en el que se va a establecer el elemento.

## <a name="value_type"></a>value_type

Tipo de valor de los elementos de la texture_view.

```cpp
typedef typename const value_type value_type;
```

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
