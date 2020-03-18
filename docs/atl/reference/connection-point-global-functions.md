---
title: Funciones globales de punto de conexión
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
ms.openlocfilehash: 0313e93ee82bb96f3bfe08e45f70ccfee30dbee6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423181"
---
# <a name="connection-point-global-functions"></a>Funciones globales de punto de conexión

Estas funciones proporcionan compatibilidad con los puntos de conexión y las asignaciones de receptor.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.|
|[AtlUnadvise](#atlunadvise)|Finaliza la conexión establecida a través de `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Aconseja o desaconseja entradas en una asignación de receptor de eventos.|

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

##  <a name="atladvise"></a>AtlAdvise

Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*<br/>
de Puntero al `IUnknown` del objeto con el que el cliente desea conectarse.

*pUnk*<br/>
de Puntero a la `IUnknown`del cliente.

*suscripto*<br/>
de GUID del punto de conexión. Normalmente, es igual que la interfaz de salida administrada por el punto de conexión.

*estudio*<br/>
enuncia Puntero a la cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="remarks"></a>Observaciones

El receptor implementa la interfaz de salida compatible con el punto de conexión. El cliente usa la cookie de *PDW* para quitar la conexión pasándola a [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>AtlUnadvise

Finaliza la conexión establecida a través de [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*<br/>
de Puntero al `IUnknown` del objeto con el que está conectado el cliente.

*suscripto*<br/>
de GUID del punto de conexión. Normalmente, es igual que la interfaz de salida administrada por el punto de conexión.

*dw*<br/>
de Cookie que identifica de forma única la conexión.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>AtlAdviseSinkMap

Llame a esta función para notificar o no notificar todas las entradas del mapa de eventos del receptor del objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el Windows Runtime.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*Ptos*<br/>
de Puntero al objeto que contiene la asignación de receptor.

*bAdvise*<br/>
de TRUE si se van a notificar todas las entradas de receptor; FALSE si se van a desaconsejar todas las entradas del receptor.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Consulte también

[Funciones](../../atl/reference/atl-functions.md)<br/>
[Macros de punto de conexión](../../atl/reference/connection-point-macros.md)
