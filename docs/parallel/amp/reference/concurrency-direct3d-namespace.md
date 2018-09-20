---
title: 'Concurrency:: Direct3D Namespace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
dev_langs:
- C++
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb7f03add1340c77d64c76abf811dfde49e1d57b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404251"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d (Espacio de nombres)

El `direct3d` espacio de nombres proporciona funciones que admiten interoperabilidad de D3D. Permite utilizar sin problemas de recursos de D3D para calcular en código AMP así como permitir el uso de los recursos creados en AMP con código D3D, sin necesidad de crear copias intermedias redundantes. Puede acelerar las secciones de cálculo intensivo de las aplicaciones DirectX mediante C++ AMP y utilizar la API D3D en los datos producidos por los cálculos de AMP de incrementalmente.

## <a name="syntax"></a>Sintaxis

```
namespace direct3d;
```

## <a name="members"></a>Miembros

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[scoped_d3d_access_lock (clase)](scoped-d3d-access-lock-class.md)|Un contenedor RAII para un bloqueo de acceso de D3D en un `accelerator_view` objeto.|

### <a name="structures"></a>Estructuras

|Name|Descripción|
|----------|-----------------|
|[adopt_d3d_access_lock_t (estructura)](adopt-d3d-access-lock-t-structure.md)|Tipo de etiqueta para indicar el bloqueo de acceso de D3D debe adoptar en lugar adquirido.|

### <a name="functions"></a>Funciones

|Name|Descripción|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Devuelve el valor absoluto del argumento.|
|[clamp](concurrency-direct3d-namespace-functions-amp.md#clamp)|Sobrecargado. Ajusta _X al intervalo _Min y _Max especificado|
|[countbits](concurrency-direct3d-namespace-functions-amp.md#countbits)|Cuenta el número de bits establecidos en _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crea un [accelerator_view (clase)](accelerator-view-class.md) de un puntero a una interfaz de dispositivo Direct3D|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Adquiere un bloqueo en un accelerator_view para realizar operaciones D3D en recursos compartidos con el accelerator_view de forma segura con|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Intento de adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloquearse.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Libere el bloqueo de acceso de D3D en el objeto accelerator_view especificado.|
|[firstbithigh](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden más alto y trabajar hacia abajo|
|[firstbitlow](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden más bajo y trabajar hacia arriba|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtener la interfaz del búfer D3D subyacente de una matriz.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Compara dos valores, devolviendo el valor que sea mayor.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Compara dos valores, devolviendo el valor que sea menor.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Devuelve una marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado.|
|[mad](concurrency-direct3d-namespace-functions-amp.md#mad)|Sobrecargado. Realiza una operación aritmética en tres argumentos: _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Crear una matriz de un puntero de interfaz del búfer D3D.|
|[ruido](concurrency-direct3d-namespace-functions-amp.md#noise)|Genera un valor aleatorio mediante el algoritmo de ruido de Perlin|
|[radianes](concurrency-direct3d-namespace-functions-amp.md#radians)|Convierte _X de grados en radianes.|
|[rcp](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcula un recíproco rápido, aproximado del argumento.|
|[reversebits](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Invierte el orden de los bits en _X|
|[saturate](concurrency-direct3d-namespace-functions-amp.md#saturate)|Ajusta _X dentro del intervalo de 0 a 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Sobrecargado. Devuelve el signo del argumento.|
|[smoothstep](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Devuelve una interpolación suavizada de Hermite entre 0 y 1, si _X está en el intervalo de [_Min, _Max].|
|[step](concurrency-direct3d-namespace-functions-amp.md#step)|Compara dos valores, devolviendo 0 o 1 según el valor que es mayor|
|[umax](concurrency-direct3d-namespace-functions-amp.md#umax)|Compara dos valores sin signo, devolviendo el valor que sea mayor.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Compara dos valores sin signo, devolviendo el valor que sea menor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
