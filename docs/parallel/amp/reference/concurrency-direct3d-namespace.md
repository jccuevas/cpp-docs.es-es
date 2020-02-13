---
title: Concurrency::direct3d (Espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::direct3d
- amprt/Concurrency::direct3d
- amp_short_vectors/Concurrency::direct3d
- amp_graphics/Concurrency::direct3d
- amp_math/Concurrency::direct3d
helpviewer_keywords:
- direct3d namespace
ms.assetid: 9566a2f1-4d5f-43e4-a3ac-676643d38420
ms.openlocfilehash: e1374acbd7061afaba372100cf6e69d9d717da8a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127038"
---
# <a name="concurrencydirect3d-namespace"></a>Concurrency::direct3d (Espacio de nombres)

El espacio de nombres `direct3d` proporciona funciones que admiten la interoperabilidad de D3D. Permite usar recursos D3D para COMPUTE en código AMP. También permite el uso de recursos creados en AMP en código D3D, sin crear copias intermedias redundantes. Puede acelerar incrementalmente las secciones de proceso intensivo de las aplicaciones DirectX mediante C++ amp y usar la API D3D en los datos generados a partir de los cálculos de amp.

## <a name="syntax"></a>Sintaxis

```cpp
namespace direct3d;
```

## <a name="members"></a>Members

### <a name="classes"></a>Clases

|Nombre|Descripción|
|----------|-----------------|
|[scoped_d3d_access_lock (clase)](scoped-d3d-access-lock-class.md)|Un contenedor RAII para un bloqueo de acceso de D3D en un objeto `accelerator_view`.|

### <a name="structures"></a>Estructuras

|Nombre|Descripción|
|----------|-----------------|
|[adopt_d3d_access_lock_t (estructura)](adopt-d3d-access-lock-t-structure.md)|Tipo de etiqueta para indicar que se debe adoptar el bloqueo de acceso de D3D en lugar de adquirirse.|

### <a name="functions"></a>Functions

|Nombre|Descripción|
|----------|-----------------|
|[abs](concurrency-direct3d-namespace-functions-amp.md#abs)|Devuelve el valor absoluto del argumento.|
|[Sujet](concurrency-direct3d-namespace-functions-amp.md#clamp)|Sobrecargado. Las abrazaderas _Xn al _Min y al intervalo de _Max especificados|
|[countbits (](concurrency-direct3d-namespace-functions-amp.md#countbits)|Cuenta el número de bits establecidos en _X|
|[create_accelerator_view](concurrency-direct3d-namespace-functions-amp.md#create_accelerator_view)|Crea una [clase accelerator_view](accelerator-view-class.md) a partir de un puntero a una interfaz de dispositivo Direct3D.|
|[d3d_access_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_lock)|Adquiere un bloqueo en un accelerator_view para realizar operaciones D3D con seguridad en recursos compartidos con el accelerator_view|
|[d3d_access_try_lock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_try_lock)|Intento de adquirir el bloqueo de acceso de D3D en un accelerator_view sin bloqueos.|
|[d3d_access_unlock](concurrency-direct3d-namespace-functions-amp.md#d3d_access_unlock)|Libera el bloqueo de acceso de D3D en el accelerator_view especificado.|
|[firstbithigh (](concurrency-direct3d-namespace-functions-amp.md#firstbithigh)|Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de ordenación más alto y trabajando hacia abajo|
|[firstbitlow (](concurrency-direct3d-namespace-functions-amp.md#firstbitlow)|Obtiene la ubicación del primer bit establecido en _X, empezando por el bit de orden más bajo y trabajando hacia arriba|
|[get_buffer](concurrency-direct3d-namespace-functions-amp.md#get_buffer)|Obtiene la interfaz de búfer D3D subyacente a una matriz.|
|[imax](concurrency-direct3d-namespace-functions-amp.md#imax)|Compara dos valores, devolviendo el valor que sea mayor.|
|[imin](concurrency-direct3d-namespace-functions-amp.md#imin)|Compara dos valores y devuelve el valor más pequeño.|
|[is_timeout_disabled](concurrency-direct3d-namespace-functions-amp.md#is_timeout_disabled)|Devuelve una marca booleana que indica si el tiempo de espera está deshabilitado para el accelerator_view especificado.|
|[Mad](concurrency-direct3d-namespace-functions-amp.md#mad)|Sobrecargado. Realiza una operación aritmética de multiplicación/suma con tres argumentos: _X \* _Y + _Z|
|[make_array](concurrency-direct3d-namespace-functions-amp.md#make_array)|Cree una matriz a partir de un puntero de interfaz de búfer de D3D.|
|[producido](concurrency-direct3d-namespace-functions-amp.md#noise)|Genera un valor aleatorio mediante el algoritmo de ruido de Perlen.|
|[radianes](concurrency-direct3d-namespace-functions-amp.md#radians)|Convierte _X de grados a radianes.|
|[Rep](concurrency-direct3d-namespace-functions-amp.md#rcp)|Calcula un recíproco rápido y aproximado del argumento.|
|[reversebits (](concurrency-direct3d-namespace-functions-amp.md#reversebits)|Invierte el orden de los bits en _X|
|[saturar](concurrency-direct3d-namespace-functions-amp.md#saturate)|Las abrazaderas _X en el intervalo de 0 a 1|
|[sign](concurrency-direct3d-namespace-functions-amp.md#sign)|Sobrecargado. Devuelve el signo del argumento.|
|[smoothstep (](concurrency-direct3d-namespace-functions-amp.md#smoothstep)|Devuelve una interpolación Smooth Hermite entre 0 y 1, si _X está en el intervalo [_Min, _Max].|
|[pasar](concurrency-direct3d-namespace-functions-amp.md#step)|Compara dos valores y devuelve 0 o 1 según el valor que sea mayor.|
|[escáner](concurrency-direct3d-namespace-functions-amp.md#umax)|Compara dos valores sin signo, devolviendo el valor que sea mayor.|
|[umin](concurrency-direct3d-namespace-functions-amp.md#umin)|Compara dos valores sin signo, devolviendo el valor menor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
