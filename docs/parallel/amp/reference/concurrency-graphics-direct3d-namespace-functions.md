---
title: Concurrency::graphics::direct3d (Funciones del espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d::get_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_sampler
- amp_graphics/Concurrency::graphics::direct3d::make_texture
ms.assetid: 11ee1d42-333e-4ae9-95ac-4cf68c06d13d
ms.openlocfilehash: 665732700ee6b85425f332a0eb96a5b75864a74e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126973"
---
# <a name="concurrencygraphicsdirect3d-namespace-functions"></a>Concurrency::graphics::direct3d (Funciones del espacio de nombres)

||||
|-|-|-|
|[get_sampler](#get_sampler)|[get_texture](#get_texture)|[make_sampler](#make_sampler)|
|[make_texture](#make_texture)|[msad4](#msad4)|

## <a name="get_sampler"></a>get_sampler

Obtiene la interfaz de estado de muestra de D3D en la vista de acelerador proporcionada que representa el objeto de muestra especificado.

```cpp
IUnknown* get_sampler(
    const Concurrency::accelerator_view& _Av,
    const sampler& _Sampler) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Av*<br/>
Una vista de acelerador D3D en la que se va a crear el estado de muestra D3D.

*_Sampler*<br/>
Objeto de muestra para el que se crea la interfaz de estado de muestra D3D subyacente.

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz IUnknown correspondiente al estado de muestra D3D que representa la muestra especificada.

## <a name="get_texture"></a>get_texture

Obtiene la interfaz de textura de Direct3D subyacente al objeto de [textura](texture-class.md) especificado.

```cpp
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
Tipo de elemento de la textura.

*_Rank*<br/>
Rango de la textura.

*_Texture*<br/>
Una vista de textura o textura asociada al accelerator_view para el que se devuelve la interfaz de textura de Direct3D subyacente.

### <a name="return-value"></a>Valor devuelto

Puntero de interfaz IUnknown que corresponde a la textura de Direct3D que subyace a la textura.

## <a name="make_sampler"></a>make_sampler

Cree una muestra a partir de un puntero de interfaz de estado de muestra D3D.

```cpp
sampler make_sampler(_In_ IUnknown* _D3D_sampler) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_D3D_sampler*<br/>
Puntero de interfaz IUnknown del estado de muestra D3D del que se va a crear la muestra.

### <a name="return-value"></a>Valor devuelto

Una muestra representa el estado de muestra D3D proporcionado.

## <a name="make_texture"></a>make_texture

Crea un objeto de [textura](texture-class.md) con los parámetros especificados.

```cpp
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
Tipo de los elementos de la textura.

*_Rank*<br/>
Rango de la textura.

*_Av*<br/>
Una vista de acelerador D3D en la que se va a crear la textura.

*_D3D_texture*<br/>
Puntero de interfaz IUnknown de la textura D3D de la que se va a crear la textura.

*_View_format*<br/>
El formato de DXGI que se va a usar para las vistas creadas a partir de esta textura. Pase DXGI_FORMAT_UNKNOWN (valor predeterminado) para derivar el formato del formato subyacente de _D3D_texture y el value_type de esta plantilla. El formato proporcionado debe ser compatible con el formato subyacente de _D3D_texture.

### <a name="return-value"></a>Valor devuelto

Textura con la textura D3D proporcionada.

## <a name="msad4"></a>msad4

Compara un valor de referencia de 4 bytes y un valor de origen de 8 bytes y acumula un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de diferentes alineaciones de bytes entre el valor de referencia y el valor de origen.

```cpp
inline uint4 msad4(
    uint _Reference,
    uint2 _Source,
    uint4 _Accum) restrict(amp);
```

### <a name="parameters"></a>Parámetros

*_Reference*<br/>
Matriz de referencia de 4 bytes en un valor uint

*_Source*<br/>
Matriz de origen de 8 bytes en un vector de dos valores uint.

*_Accum*<br/>
Vector de 4 valores que se va a agregar a la suma enmascarada de diferencias absolutas de las diferentes alineaciones de bytes entre el valor de referencia y el valor de origen.

### <a name="return-value"></a>Valor devuelto

Devuelve un vector de 4 sumas. Cada suma corresponde a la suma enmascarada de diferencias absolutas de diferentes alineaciones de bytes entre el valor de referencia y el valor de origen.

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency:: Graphics::d irect3d

## <a name="see-also"></a>Consulte también

[Concurrency::graphics::direct3d (espacio de nombres)](concurrency-graphics-direct3d-namespace.md)
