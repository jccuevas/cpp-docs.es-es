---
title: Funciones globales del punto de conexión
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 6474297f8b9adf04541f7d232fb88d5e52d4e88c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331530"
---
# <a name="connection-point-global-functions"></a>Funciones globales del punto de conexión

Estas funciones proporcionan compatibilidad con puntos de conexión y mapas de receptores.

> [!IMPORTANT]
> Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.|
|[AtlUnadvise](#atlunadvise)|Termina la conexión `AtlAdvise`establecida a través de .|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Aconseja o desaconseja entradas en un mapa de receptores de eventos.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atladvise"></a><a name="atladvise"></a>AtlAdvise

Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*<br/>
[en] Un puntero `IUnknown` al objeto con el que el cliente desea conectarse.

*Punk*<br/>
[en] Un puntero a la `IUnknown`.

*Iid*<br/>
[en] El GUID del punto de conexión. Normalmente, esto es lo mismo que la interfaz saliente administrada por el punto de conexión.

*Pdw*<br/>
[fuera] Puntero a la cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El receptor implementa la interfaz saliente admitida por el punto de conexión. El cliente utiliza la cookie *pdw* para eliminar la conexión pasándola a [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

## <a name="atlunadvise"></a><a name="atlunadvise"></a>AtlUnadvise

Termina la conexión establecida a través de [AtlAdvise](#atladvise).

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*<br/>
[en] Puntero al `IUnknown` objeto con el que está conectado el cliente.

*Iid*<br/>
[en] El GUID del punto de conexión. Normalmente, esto es lo mismo que la interfaz saliente administrada por el punto de conexión.

*dw*<br/>
[en] La cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

## <a name="atladvisesinkmap"></a><a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Llame a esta función para notificar o no notificar todas las entradas del mapa de eventos del receptor del objeto.

> [!IMPORTANT]
> Esta función no se puede utilizar en aplicaciones que se ejecutan en Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
[en] Puntero al objeto que contiene el mapa de receptores.

*bAdvise*<br/>
[en] TRUESi se deben avisar a todas las entradas del receptor; FALSE si se deben desaconsejar todas las entradas del receptor.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)<br/>
[Macros de punto de conexión](../../atl/reference/connection-point-macros.md)
