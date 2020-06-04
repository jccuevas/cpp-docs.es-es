---
title: Macros de punto de conexión
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: 361cf6ab2c7af142c1d57c002681ccf6e4a87bda
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331498"
---
# <a name="connection-point-macros"></a>Macros de punto de conexión

Estas macros definen las entradas y los mapas de puntos de conexión.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marca el principio de las entradas de mapa de punto de conexión.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Introduce puntos de conexión en el mapa.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Similar a CONNECTION_POINT_ENTRY pero toma un puntero a iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marca el final de las entradas del mapa del punto de conexión.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_connection_point_map"></a><a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Marca el principio de las entradas de mapa de punto de conexión.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] El nombre de la clase que contiene los puntos de conexión.

### <a name="remarks"></a>Observaciones

Inicie el mapa de puntos de conexión con la macro BEGIN_CONNECTION_POINT_MAP, agregue entradas para cada uno de los puntos de conexión con la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) y complete el mapa con la macro [END_CONNECTION_POINT_MAP.](#end_connection_point_map)

Para obtener más información acerca de los puntos de conexión en ATL, consulte el artículo [Puntos](../../atl/atl-connection-points.md)de conexión .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

## <a name="connection_point_entry-and-connection_point_entry_p"></a><a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY y CONNECTION_POINT_ENTRY_P

Ingresa un punto de conexión para la interfaz especificada en el mapa del punto de conexión para que se pueda acceder a ella.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*Iid*<br/>
[en] GUID de la interfaz que se agrega a la asignación de punto de conexión.

*piid*<br/>
[en] Puntero al GUID de la interfaz que se va a dar.

### <a name="remarks"></a>Observaciones

Las entradas de punto de conexión en el mapa las usa [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La clase que contiene la `IConnectionPointContainerImpl`asignación de puntode de conexión debe heredar de .

Inicie el mapa de puntos de conexión con la macro [BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) agregue entradas para cada uno de los puntos de conexión con la macro CONNECTION_POINT_ENTRY y complete el mapa con la macro [END_CONNECTION_POINT_MAP.](#end_connection_point_map)

Para obtener más información acerca de los puntos de conexión en ATL, consulte el artículo [Puntos](../../atl/atl-connection-points.md)de conexión .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

## <a name="end_connection_point_map"></a><a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Marca el final de las entradas del mapa del punto de conexión.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Observaciones

Inicie el mapa de puntos de conexión con la macro [BEGIN_CONNECTION_POINT_MAP,](#begin_connection_point_map) agregue entradas para cada uno de los puntos de conexión con la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) y complete el mapa con la macro END_CONNECTION_POINT_MAP.

Para obtener más información acerca de los puntos de conexión en ATL, consulte el artículo [Puntos](../../atl/atl-connection-points.md)de conexión .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales del punto de conexión](../../atl/reference/connection-point-global-functions.md)
