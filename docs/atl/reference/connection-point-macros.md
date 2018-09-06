---
title: Macros de punto de conexión | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::BEGIN_CONNECTION_POINT_MAP
- atlcom/ATL::END_CONNECTION_POINT_MAP
dev_langs:
- C++
helpviewer_keywords:
- connection points [C++], macros
ms.assetid: cc3a6dd3-5538-45df-b027-1f34963c31e5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 226c0b0d0f1fc316d5b78884a4d6e260296c52f9
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43752198"
---
# <a name="connection-point-macros"></a>Macros de punto de conexión

Estas macros definen asignaciones de punto de conexión y las entradas.

|||
|-|-|
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marca el principio de las entradas de asignación de punto de conexión.|
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Escribe los puntos de conexión en el mapa.|
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (Visual Studio 2017) Pero, de forma similar al CONNECTION_POINT_ENTRY toma un puntero a iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marca el final de las entradas de asignación de punto de conexión.|  

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP

Marca el principio de las entradas de asignación de punto de conexión.

```
BEGIN_CONNECTION_POINT_MAP(x)
```

### <a name="parameters"></a>Parámetros

*x*  
[in] El nombre de la clase que contiene los puntos de conexión.

### <a name="remarks"></a>Comentarios

Iniciar la asignación de punto de conexión con la macro BEGIN_CONNECTION_POINT_MAP, agregar entradas para cada uno de los puntos de conexión con el [CONNECTION_POINT_ENTRY](#connection_point_entry) macro y complete el mapa con el [END_CONNECTION_ POINT_MAP](#end_connection_point_map) macro.

Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]

##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY y CONNECTION_POINT_ENTRY_P

Escribe un punto de conexión para la interfaz especificada en el mapa de puntos de conexión para que se puede acceder.

```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parámetros

*IID*  
[in] El GUID de la interfaz que se va a agregar a la asignación de punto de conexión. 

*piid*  
[in] Puntero al GUID de la interfaz que se está activado.

### <a name="remarks"></a>Comentarios

Las entradas de punto de conexión en el mapa se utilizan por [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La clase que contiene la asignación de punto de conexión debe heredar de `IConnectionPointContainerImpl`.

Iniciar la asignación de punto de conexión con el [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) macro, agregar entradas para cada uno de los puntos de conexión con la macro CONNECTION_POINT_ENTRY y completar la asignación con el [END_CONNECTION_ POINT_MAP](#end_connection_point_map) macro.

Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]

##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP

Marca el final de las entradas de asignación de punto de conexión.

```
END_CONNECTION_POINT_MAP()
```

### <a name="remarks"></a>Comentarios

Iniciar la asignación de punto de conexión con el [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) macro, agregar entradas para cada uno de los puntos de conexión con el [CONNECTION_POINT_ENTRY](#connection_point_entry) macro y complete el mapa con el END_ Macro CONNECTION_POINT_MAP.

Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)   
[Funciones globales de punto de conexión](../../atl/reference/connection-point-global-functions.md)
