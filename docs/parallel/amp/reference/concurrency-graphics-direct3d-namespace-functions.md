---
title: Funciones del espacio de nombres Concurrency::Graphics::Direct3D
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 71ce23d1238d852d42687be725de8153e938d6cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464732"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Funciones del espacio de nombres Concurrency::Graphics::Direct3D

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

##  <a name="get_sampler"></a>  get_sampler

Obtenga la interfaz de estado de muestra de D3D en el Acelerador proporcionada vista que representa el objeto de muestra especificado.

```
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
Una vista del Acelerador D3D en el que el estado de la muestra de D3D consiste en crear.

*_Sampler*<br/>
Un objeto de muestra para el que se crea la interfaz de estado de muestra de D3D subyacente.

### <a name="return-value"></a>Valor devuelto

El puntero de interfaz IUnknown correspondiente al estado de muestrario de D3D que representa el muestrario especificado.

##  <a name="get_texture"></a>  get_texture

Obtiene la interfaz de textura de Direct3D subyacente especificado [textura](texture-class.md) objeto.

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

*value_type*<br/>
El tipo de elemento de la textura.

*_Rank*<br/>
El rango de la textura.

*_Texture*<br/>
Una textura o una vista de textura asociado al elemento accelerator_view para el que se devuelve la interfaz de textura de Direct3D subyacente.

### <a name="return-value"></a>Valor devuelto

El puntero de interfaz IUnknown correspondiente a la textura de Direct3D que subyace a la textura.

##  <a name="make_sampler"></a>  make_sampler

Cree una muestra de un puntero de interfaz de estado de muestra de D3D.

```
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_D3D_sampler*<br/>
Puntero de interfaz IUnknown del estado para crear el ejemplo de muestra D3D.

### <a name="return-value"></a>Valor devuelto

Una muestra representa el estado del muestrario de D3D proporcionado.

##  <a name="make_texture"></a>  make_texture

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

*value_type*<br/>
El tipo de los elementos de la textura.

*_Rank*<br/>
El rango de la textura.

*_Av*<br/>
Una vista del Acelerador D3D en el que es necesario crear la textura.

*_D3D_texture*<br/>
Puntero de interfaz IUnknown de la textura D3D para crear la textura de.

*_View_format*<br/>
El formato DXGI que se usará para las vistas creadas desde esta textura. Pase DXGI_FORMAT_UNKNOWN (el valor predeterminado) para derivar el formato del formato subyacente de _D3D_texture y la value_type de esta plantilla. El formato proporcionado debe ser compatible con el formato subyacente de _D3D_texture.

### <a name="return-value"></a>Valor devuelto

Una textura utilizando la textura D3D proporcionada.

##  <a name="msad4"></a>  msad4

Compara un valor de referencia de 4 bytes y un valor de origen de 8 bytes y acumula un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de distintas alineaciones de bytes entre el valor de referencia y el valor de origen.

```
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*R_eferencia*<br/>
La matriz de referencia de 4 bytes en un valor uint

*_Source*<br/>
La matriz de origen de 8 bytes en un vector de dos valores uint.

*_Accum*<br/>
Un vector de 4 valores que se agregarán a la suma enmascarada de diferencias absolutas de las distintas alineaciones de bytes entre el valor de referencia y el valor de origen.

### <a name="return-value"></a>Valor devuelto

Devuelve un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de distintas alineaciones de bytes entre el valor de referencia y el valor de origen.

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Namespace:** Concurrency::graphics::direct3d

## <a name="see-also"></a>Vea también

[Concurrency::graphics::direct3d (espacio de nombres)](concurrency-graphics-direct3d-namespace.md)
