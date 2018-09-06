---
title: Funciones globales de punto de conexión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlAdvise
- atlbase/ATL::AtlUnadvise
- atlbase/ATL::AtlAdviseSinkMap
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], global functions
ms.assetid: bcb4bf50-2155-4e20-b8bb-f2908b03a6e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68c22ff88ac92357dabfef8076c160271a76378
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756495"
---
# <a name="connection-point-global-functions"></a>Funciones globales de punto de conexión

Estas funciones proporcionan compatibilidad para puntos de conexión y mapas de receptor.

> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

|||
|-|-|
|[AtlAdvise](#atladvise)|Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.|
|[AtlUnadvise](#atlunadvise)|Finaliza la conexión establecida mediante `AtlAdvise`.|
|[AtlAdviseSinkMap](#atladvisesinkmap)|Aconseja o no notifica las entradas de un mapa de receptores de eventos.|  

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atladvise"></a>  AtlAdvise

Crea una conexión entre el punto de conexión de un objeto y el receptor de un cliente.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
HRESULT    AtlAdvise(
    IUnknown* pUnkCP,
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*  
[in] Un puntero a la `IUnknown` del objeto desea conectar con el cliente.

*pUnk*  
[in] Un puntero para el cliente `IUnknown`.

*IID*  
[in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.

*PDW*  
[out] Un puntero a la cookie que identifica la conexión.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="remarks"></a>Comentarios

El receptor implementa la interfaz de salida admitida por el punto de conexión. El cliente usa la *pdw* cookie para quitar la conexión pasándolo a [AtlUnadvise](#atlunadvise).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#91](../../atl/codesnippet/cpp/connection-point-global-functions_1.cpp)]

##  <a name="atlunadvise"></a>  AtlUnadvise

Finaliza la conexión establecida mediante [AtlAdvise](#atladvise).

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
HRESULT    AtlUnadvise(
    IUnknown* pUnkCP,
    const IID& iid,
    DWORD dw);
```

### <a name="parameters"></a>Parámetros

*pUnkCP*  
[in] Un puntero a la `IUnknown` del objeto que el cliente está conectado con.

*IID*  
[in] El GUID del punto de conexión. Normalmente, esto es igual que la interfaz de salida administrada por el punto de conexión.

*almacenamiento de datos*  
[in] La cookie que identifica la conexión.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#96](../../atl/codesnippet/cpp/connection-point-global-functions_2.cpp)]

##  <a name="atladvisesinkmap"></a>  AtlAdviseSinkMap

Llame a esta función para notificar o no notificar todas las entradas del mapa de eventos del receptor del objeto.

> [!IMPORTANT]
>  Esta función no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

```
HRESULT AtlAdviseSinkMap(T* pT, bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*pT*  
[in] Un puntero al objeto que contiene el mapa de receptores.

*bAdvise*  
[in] Es TRUE si todas las entradas de receptor se informamos; FALSE si se deben notificar todas las entradas de receptor.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT estándar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#92](../../atl/codesnippet/cpp/connection-point-global-functions_3.h)]

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)   
[Macros de punto de conexión](../../atl/reference/connection-point-macros.md)
