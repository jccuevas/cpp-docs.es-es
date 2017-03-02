---
title: Funciones del espacio de nombres Concurrency::Graphics::Direct3D | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: aa7e91237eaa9ced297e2c5748359c23bb436df8
ms.lasthandoff: 02/24/2017

---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funciones del espacio de nombres Concurrency::Graphics::Direct3D
||||  
|-|-|-|  
|[get_sampler (función)](#get_sampler)|[get_texture (función)](#get_texture)|[make_sampler (función)](#make_sampler)|  
|[make_texture (función)](#make_texture)|[msad4 (función)](#msad4)|  
  
##  <a name="a-namegetsamplera--getsampler-function"></a><a name="get_sampler"></a>get_sampler (función)  
 Obtener la interfaz de estado de muestrario de D3D en el Acelerador determinado ver que representa el objeto de muestra especificado.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 Vista de aceleradores de D3D en los que es necesario crear el estado de muestrario de D3D.  
  
 `_Sampler`  
 Un objeto de muestra para el que se crea la interfaz de estado de muestrario de D3D subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero de interfaz IUnknown corresponde al estado de muestrario de D3D que representa la muestra determinada.  
  
##  <a name="a-namegettexturea--gettexture-function"></a><a name="get_texture"></a>get_texture (función)  
 Obtiene la interfaz de textura Direct3D subyacente especificado [textura](texture-class.md) objeto.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const writeonly_texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
template<
    typename value_type,  
    int _Rank  
>  
_Ret_ IUnknown *get_texture(
    const texture_view<value_type, _Rank>& _Texture) restrict(cpu);

 
```  
  
### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de elemento de la textura.  
  
 `_Rank`  
 El rango de la textura.  
  
 `_Texture`  
 Una textura o una vista de textura asociados a la accelerator_view para el que se devuelve la interfaz de textura Direct3D subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
 El puntero de interfaz IUnknown correspondiente a la textura Direct3D subyacente de la textura.  
  
##  <a name="a-namemakesamplera--makesampler-function"></a><a name="make_sampler"></a>make_sampler (función)  
 Crear una muestra de un puntero de interfaz de estado de muestrario de D3D.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_D3D_sampler`  
 Puntero de interfaz IUnknown del estado de muestrario de D3D para crear la muestra de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una muestra de representa el estado de muestra proporcionado de D3D.  
  
##  <a name="a-namemaketexturea--maketexture-function"></a><a name="make_texture"></a>make_texture (función)  
 Crea un [textura](texture-class.md) objeto utilizando los parámetros especificados.  
  
```  
template<
    typename value_type,  
    int _Rank  
>  
texture<value_type, _Rank> make_texture(
    const Concurrency::accelerator_view& _Av,  
    _In_ IUnknown* _D3D_texture,  
    DXGI_FORMAT _View_format = DXGI_FORMAT_UNKNOWN) restrict(cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `value_type`  
 El tipo de los elementos de la textura.  
  
 `_Rank`  
 El rango de la textura.  
  
 `_Av`  
 Vista de aceleradores de D3D en los que es necesario crear la textura.  
  
 `_D3D_texture`  
 Puntero de interfaz IUnknown para crear la textura de la textura de D3D.  
  
 `_View_format`  
 El formato DXGI utilizado para las vistas creadas de esta textura. Pasar DXGI_FORMAT_UNKNOWN (predeterminado) para derivar el formato desde el formato subyacente de _D3D_texture y la value_type de esta plantilla. El formato proporcionado debe ser compatible con el formato subyacente de _D3D_texture.  
  
### <a name="return-value"></a>Valor devuelto  
 Una textura con la textura de D3D proporcionada.  
  
##  <a name="a-namemsad4a--msad4-function"></a><a name="msad4"></a>msad4 (función)  
 Compara un valor de referencia de 4 bytes y un valor de origen de 8 bytes y acumula un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de alineaciones de byte diferentes entre el valor de referencia y el valor de origen.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Reference`  
 La matriz de referencia de 4 bytes en un valor uint  
  
 `_Source`  
 La matriz de origen de 8 bytes en un vector de dos valores uint.  
  
 `_Accum`  
 Un vector de 4 valores que se agregarán a la suma de las diferencias absolutas de las alineaciones de byte diferentes entre el valor de referencia y el valor de origen enmascarada.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de alineaciones de byte diferentes entre el valor de referencia y el valor de origen.  
  
## <a name="see-also"></a>Vea también  
 [Namespace Concurrency::Graphics::Direct3D](concurrency-graphics-direct3d-namespace.md)

