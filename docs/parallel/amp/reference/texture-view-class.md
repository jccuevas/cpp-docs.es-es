---
title: texture_view (clase) | Documentos de Microsoft
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
ms.openlocfilehash: 3db02d9cafb87c0f173546687ad01390e09b9f68
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="textureview-class"></a>texture_view (Clase)
Proporciona acceso de lectura y escritura en una textura. `texture_view` solo puede usarse para leer las texturas cuyo tipo de valor es `int`, `unsigned int`, o `float` que tienen bpse de 32 bits de forma predeterminada. Para leer otros formatos de textura, utilice `texture_view<const value_type, _Rank>`.  
  
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
 `value_type`  
 El tipo de los elementos en el agregado de textura.  
  
 `_Rank`  
 El rango de la `texture_view`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`value_type`|El tipo de los elementos de los agregados de textura.|  
|`coordinates_type`|El tipo de la coordenada se utiliza para especificar un elemento de textura en el `texture_view`, es decir, un `short_vector` que tienen la misma clasificación como la textura asociada que tiene un tipo de valor de `float`.|  
|`gather_return_type`|El tipo de valor devuelto que se usa para recopilar las operaciones, es decir, un rango 4 `short_vector` que contiene los cuatro componentes de color homogéneo recopila a partir de los cuatro valores de textura muestreados.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[texture_view Constructor](#ctor)|Sobrecargado. Construye un `texture_view` instancia.|  
|[~ texture_view (destructor)](#ctor)|Destruye el `texture_view` instancia.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura muestreadas.|  
|[gather_blue](#gather_blue)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de azul (z) de los cuatro elementos de textura muestreadas.|  
|[gather_green](#gather_green)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de color verde (y) de los cuatro elementos de textura muestreadas.|  
|[gather_red](#gather_red)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura muestreadas.|  
|[get](#get)|Sobrecargado. Obtiene el valor del elemento por índice.|  
|[Ejemplo](#sample)|Sobrecargado. Ejemplos de la textura en el nivel de detalle y las coordenadas especificadas mediante la configuración de muestreo especificada.|  
|[set](#set)|Establece el valor de un elemento por su índice.|  
  
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
 `_Src`  
 [1, 2] Constructor  
 El `texture` en el que la escritura `texture_view` se crea.  
  
 [3, 4] Constructor  
 El `texture` en el que el no modificable `texture_view` se crea.  
  
 `_Other`  
 [5] Constructor de copias  
 El origen de escritura `texture_view`.  
  
 [6, 7] Constructor de copias  
 El origen no se puede escribir `texture_view`.  
  
 `_Mipmap_level`  
 El nivel de asignación de MIP específico en el origen de `texture` grabable que este `texture_view` se enlaza a. El valor predeterminado es 0, que representa el nivel de mip de nivel superior (más detallado).  
  
 `_Most_detailed_mip`  
 Nivel de mip nivel (más detallado) para la vista, en relación con lo especificado superior `texture_view` objeto.  
  
 `_Mip_levels`  
 El número de niveles de asignación MIP accesibles a través de la `texture_view`.  
  
##  <a name="gather_red"></a> gather_red 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura muestreadas.  
  
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
 `_Address_mode`  
 El modo de dirección que se utiliza al ejemplo la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para usar al ejemplo la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se usan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente de color rojo (x) de 4 muestrea valores de textura.  
  
##  <a name="gather_green"></a> gather_green 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de color verde (y) de los cuatro elementos de textura muestreadas.  
  
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
 `_Address_mode`  
 El modo de dirección que se utiliza al ejemplo la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para usar al ejemplo la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se usan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente verde (y) de 4 muestrea valores de textura.  
  
##  <a name="gather_blue"></a> gather_blue 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de azul (z) de los cuatro elementos de textura muestreadas.  
  
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
 `_Address_mode`  
 El modo de dirección que se utiliza al ejemplo la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para usar al ejemplo la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se usan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente de color rojo (x) de 4 muestrea valores de textura.  
  
##  <a name="gather_alpha"></a> gather_alpha 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura muestreadas.  
  
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
 `_Address_mode`  
 El modo de dirección que se utiliza al ejemplo la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para usar al ejemplo la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se usan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un rango 4 corto vector que contiene el componente de 4 muestrea valores de textura (w) alfa.  
  
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
 `_Index`  
 Índice del elemento que se va a obtener, posiblemente multidimensionales.  
  
 `_Mip_level`  
 El nivel de asignación MIP desde el que se debe obtener el valor. El valor predeterminado 0 representa el nivel de asignación MIP más detallado.  
  
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
 `_Other`  
 [1, 2] Constructor de copias  
 Admite escritura `texture_view` objeto.  
  
 [3] Constructor de copias de  
 No modificable `texture_view` objeto.  
  
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
 `_Index`  
 El índice, posiblemente multidimensional.  
  
 `_I0`  
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
 `_Index`  
 El índice, posiblemente multidimensional.  
  
 `_I0`  
 El componente más significativo del índice.  
  
 `_I1`  
 El componente siguiente-a-más significativo del índice.  
  
 `_I2`  
 El componente menos significativos del índice.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor del elemento indizado por `_Index`.  
  
##  <a name="sample"></a> Ejemplo 

 Ejemplos de la textura en el nivel de detalle y las coordenadas especificadas mediante la configuración de muestreo especificada.  
  
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
 `_Filter_mode`  
 El modo de filtro se utiliza para la texture_view de ejemplo. El modo de filtro es el mismo para la minimización, maximización y filtros de asignación MIP.  
  
 `_Address_mode`  
 El modo de dirección debe utilizar para el texture_view de ejemplo. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para usarla en el texture_view de ejemplo.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se usan para interpolará entre los valores de textura.  
  
 `_Level_of_detail`  
 El valor especifica el nivel de asignación MIP de muestra de. Los valores fraccionarios se usan para interpolar entre dos niveles de asignación MIP. El nivel de detalle predeterminado es 0, que representa el nivel de mip más detallado.  
  
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
 `_Index`  
 Índice del elemento que se va a establecer, posiblemente multidimensionales.  
  
 `value`  
 El valor que se establecerá el elemento.  
  
##  <a name="value_type"></a> value_type 

 El tipo de valor de los elementos de la texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
