---
title: Macros de punto de conexión
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
ms.openlocfilehash: cb8d6f696980ef91d7b43c960dc50289ea8500a6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423157"
---
# <a name="connection-point-macros"></a>Macros de punto de conexión

Estas macros definen las entradas y las asignaciones de puntos de conexión.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marca el principio de las entradas de la asignación de puntos de conexión.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Especifica los puntos de conexión en el mapa.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Similar a CONNECTION_POINT_ENTRY pero toma un puntero a IID.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marca el final de las entradas de la asignación de puntos de conexión.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_connection_point_map"></a>BEGIN_CONNECTION_POINT_MAP

Marca el principio de las entradas de la asignación de puntos de conexión.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de Nombre de la clase que contiene los puntos de conexión.

### <a name="remarks"></a>Observaciones

Inicie el mapa de puntos de conexión con la macro BEGIN_CONNECTION_POINT_MAP, agregue entradas para cada uno de los puntos de conexión con la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) y complete el mapa con la macro [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Para obtener más información sobre los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>CONNECTION_POINT_ENTRY y CONNECTION_POINT_ENTRY_P

Especifica un punto de conexión para la interfaz especificada en la asignación de punto de conexión para que se pueda tener acceso a ella.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*suscripto*<br/>
de GUID de la interfaz que se va a agregar a la asignación de puntos de conexión.

*piid*<br/>
de Puntero al GUID de la interfaz que se va agrega.

### <a name="remarks"></a>Observaciones

[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)usa las entradas de punto de conexión en el mapa. La clase que contiene la asignación de punto de conexión debe heredar de `IConnectionPointContainerImpl`.

Inicie el mapa de puntos de conexión con la macro [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , agregue entradas para cada uno de los puntos de conexión con la macro CONNECTION_POINT_ENTRY y complete el mapa con la macro [END_CONNECTION_POINT_MAP](#end_connection_point_map) .

Para obtener más información sobre los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>END_CONNECTION_POINT_MAP

Marca el final de las entradas de la asignación de puntos de conexión.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Observaciones

Inicie el mapa de puntos de conexión con la macro [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) , agregue entradas para cada uno de los puntos de conexión con la macro [CONNECTION_POINT_ENTRY](#connection_point_entry) y complete el mapa con la macro END_CONNECTION_POINT_MAP.

Para obtener más información sobre los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[Funciones globales de punto de conexión](../../atl/reference/connection-point-global-functions.md)
