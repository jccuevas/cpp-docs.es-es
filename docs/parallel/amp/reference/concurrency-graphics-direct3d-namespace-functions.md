---
title: Las funciones del espacio de nombres de Concurrency::Graphics::Direct3D | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
dev_langs: C++
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 97f03dbf71c0f8b97b750532279e4cc76d01fb64
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funciones del espacio de nombres de Concurrency::Graphics::Direct3D
||||  
|-|-|-|  
|[get_sampler)](#get_sampler)|[get_texture)](#get_texture)|[make_sampler](#make_sampler)|  
|[make_texture](#make_texture)|[msad4](#msad4)|  

 
##  <a name="get_sampler"></a>get_sampler)  
 Obtener la interfaz de estado de la muestra de D3D en el Acelerador determinado ver que representa el objeto de muestra especificado.  
  
```  
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,  
    const sampler& _Sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Av`  
 Vista de aceleradores de D3D en el que el estado de la muestra de D3D consiste en crear.  
  
 `_Sampler`  
 Un objeto de muestra para el que se crea la interfaz de estado de muestra de D3D subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero de interfaz IUnknown que se corresponde con el estado de la muestra de D3D que representa la muestra de determinado.  
  
##  <a name="get_texture"></a>get_texture)  
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
  
##  <a name="make_sampler"></a>make_sampler  
 Crear una muestra de un puntero de interfaz de estado de muestra de D3D.  
  
```  
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_D3D_sampler`  
 Puntero de interfaz IUnknown del estado de muestra de D3D para crear la muestra de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una muestra de representa el estado de muestra de D3D proporcionado.  
  
##  <a name="make_texture"></a>make_texture  
 Crea un [textura](texture-class.md) objeto mediante el uso de los parámetros especificados.  
  
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
 Puntero de interfaz IUnknown de la textura de D3D para crear la textura de.  
  
 `_View_format`  
 El formato DXGI a usar para las vistas creadas de esta textura. Pasar DXGI_FORMAT_UNKNOWN (valor predeterminado) para derivar el formato desde el formato subyacente del _D3D_texture y la value_type de esta plantilla. El formato proporcionado debe ser compatible con el formato subyacente de _D3D_texture.  
  
### <a name="return-value"></a>Valor devuelto  
 Una textura mediante la textura de D3D proporcionada.  
  
##  <a name="msad4"></a>msad4  
 Compara un valor de referencia de 4 bytes y un valor de origen de 8 bytes y se acumula un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de la diferencia absoluta de alineaciones que sean diferentes de byte entre el valor de referencia y el valor de origen.  
  
```  
inline uint4 msad4(
    uint _Reference,  
    uint2 _Source,  
    uint4 _Accum) restrict(amp);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Reference`  
 La matriz de referencia de 4 bytes en un valor de uint  
  
 `_Source`  
 La matriz de origen de 8 bytes en un vector de dos valores de uint.  
  
 `_Accum`  
 Un vector de 4 valores va a agregar a la suma enmascarada de absoluta las diferencias entre las alineaciones de bytes diferentes entre el valor de referencia y el valor de origen.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de la diferencia absoluta de alineaciones que sean diferentes de byte entre el valor de referencia y el valor de origen.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Concurrency::graphics::direct3d 

## <a name="see-also"></a>Vea también  
 [Concurrency::graphics::direct3d (espacio de nombres)](concurrency-graphics-direct3d-namespace.md)
