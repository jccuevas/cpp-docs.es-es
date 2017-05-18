---
title: texture_view (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 4896b3ee55a5955c33e1c2652eb73851e4ec5a64
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="textureview-class"></a>texture_view (Clase)
Proporciona acceso de lectura y escritura para una textura. `texture_view`sólo puede utilizarse para leer las texturas cuyo tipo de valor es `int`, `unsigned int`, o `float` que tienen bpse de 32 bits de forma predeterminada. Para leer otros formatos de textura, utilice `texture_view<const value_type, _Rank>`.  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|`value_type`|El tipo de los elementos de los agregados de textura.|  
|`coordinates_type`|El tipo de la coordenada se utiliza para especificar un elemento de textura en el `texture_view`, es decir, un `short_vector` que tiene la misma jerarquía como la textura asociada que tiene un tipo de valor de `float`.|  
|`gather_return_type`|El tipo de valor devuelto que se usa para recopilar las operaciones, es decir, un rango 4 `short_vector` que contiene los cuatro componentes de color homogéneo recopilados de los cuatro valores de textura a muestrear.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[texture_view (Constructor)](#ctor)|Sobrecargado. Construye un `texture_view` instancia.|  
|[~ texture_view (destructor)](#ctor)|Destruye el `texture_view` instancia.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[gather_alpha](#gather_alpha)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura de muestreadas.|  
|[gather_blue](#gather_blue)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de azul (z) de los cuatro elementos de textura de muestreadas.|  
|[gather_green](#gather_green)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de color verde (y) de los cuatro elementos de textura de muestreadas.|  
|[gather_red](#gather_red)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura de muestreadas.|  
|[get](#get)|Sobrecargado. Obtiene el valor del elemento por índice.|  
|[ejemplo](#sample)|Sobrecargado. Ejemplos de la textura en las coordenadas especificadas y el nivel de detalle con la configuración de muestreo especificada.|  
|[set](#set)|Establece el valor de un elemento por índice.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Operator()](#operator_call)|Sobrecargado. Obtiene el valor del elemento por índice.|  
|[operator]](#operator_at)|Sobrecargado. Obtiene el valor del elemento por índice.|  
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[value_type](#value_type)|El tipo de valor de los elementos de la `texture_view`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `_Texture_base`  
  
 `texture_view`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Graphics  
  
##  <a name="dtor"></a>~ texture_view 

 Destruye el `texture_view` instancia.  
  
```  
~texture_view() restrict(amp, cpu);
```  
  
##  <a name="ctor"></a>texture_view 

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
 El `texture` en el que el no modificables `texture_view` se crea.  
  
 `_Other`  
 [5] Constructor de copias  
 El origen puede escribir `texture_view`.  
  
 [6, 7] Copy (Constructor)  
 El origen no se puede escribir `texture_view`.  
  
 `_Mipmap_level`  
 El nivel de asignación de MIP específico en el origen de `texture` grabable que este `texture_view` se enlaza. El valor predeterminado es 0, que representa el nivel de mip de nivel superior (más detallado).  
  
 `_Most_detailed_mip`  
 Principales de nivel de mip nivel (más detallado) para la vista, en relación con el especificado `texture_view` objeto.  
  
 `_Mip_levels`  
 El número de niveles de mipmap accesibles a través de la `texture_view`.  
  
##  <a name="gather_red"></a>gather_red 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes rojo (x) de los cuatro elementos de textura de muestreadas.  
  
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
 Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para utilizar al ejemplo de la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente rojo (x) de 4 muestrea valores de textura.  
  
##  <a name="gather_green"></a>gather_green 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de color verde (y) de los cuatro elementos de textura de muestreadas.  
  
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
 Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para utilizar al ejemplo de la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente verde (y) de 4 muestrea valores de textura.  
  
##  <a name="gather_blue"></a>gather_blue 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes de azul (z) de los cuatro elementos de textura de muestreadas.  
  
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
 Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para utilizar al ejemplo de la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un vector corto de rango 4 que contiene el componente rojo (x) de 4 muestrea valores de textura.  
  
##  <a name="gather_alpha"></a>gather_alpha 

 Ejemplos de la textura en las coordenadas especificadas mediante la configuración de muestreo especificada y devuelve los componentes alfa (w) de los cuatro elementos de textura de muestreadas.  
  
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
 Para usar el modo de direccionamiento a muestra la `texture_view`. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra para utilizar al ejemplo de la `texture_view`.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se utilizan para interpolar entre elementos de textura de ejemplo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un rango corto 4 vector que contiene la versión alfa de componente de 4 muestra los valores de textura (w).  
  
##  <a name="get"></a>Obtener 

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
 El nivel de asignación MIP desde el que obtendremos el valor. El valor predeterminado 0 representa el nivel de asignación MIP más detallado.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del elemento.  
  
##  <a name="operator_eq"></a>operador = 

 Asigna una vista de la misma textura especificado `texture_view` a esta `texture_view` instancia.  
  
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
 [1, 2] Copy (Constructor)  
 Escritura `texture_view` objeto.  
  
 [3] Constructor de copias de  
 No modificables `texture_view` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `texture_view` instancia.  
  
##  <a name="operator_at"></a>operator] 

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
  
##  <a name="operator_call"></a>Operator() 

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
  
##  <a name="sample"></a>ejemplo 

 Ejemplos de la textura en las coordenadas especificadas y el nivel de detalle con la configuración de muestreo especificada.  
  
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
 El modo de filtro se utiliza para la texture_view de ejemplo. El modo de filtro es la misma para la minimización, maximización y filtros de mipmap.  
  
 `_Address_mode`  
 El modo de dirección se utiliza para la texture_view de ejemplo. El modo de dirección es el mismo para todas las dimensiones.  
  
 `_Sampler`  
 La configuración de muestra se utiliza para la texture_view de ejemplo.  
  
 `_Coord`  
 Las coordenadas para tomar la muestra de. Los valores de coordenadas fraccionarios se utilizan para interpolar entre valores de textura.  
  
 `_Level_of_detail`  
 El valor especifica el nivel de asignación MIP muestrear. Los valores fraccionarios se utilizan para interpolar entre dos niveles de mipmap. El nivel de detalle predeterminado es 0, que representa el nivel de mip más detallado.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de interpolación de ejemplo.  
  
##  <a name="set"></a>conjunto 

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
 El valor para establecer el elemento.  
  
##  <a name="value_type"></a>value_type 

 El tipo de valor de los elementos de la texture_view.  
  
```  
typedef typename const value_type value_type;  
```  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)

