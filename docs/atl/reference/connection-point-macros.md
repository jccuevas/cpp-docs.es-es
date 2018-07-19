---
title: Macros de punto de conexión | Documentos de Microsoft
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
ms.openlocfilehash: e50a868dd87628873b2a43f0ace55690b0583fd5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32362935"
---
# <a name="connection-point-macros"></a>Macros de punto de conexión
Estas macros definen asignaciones de punto de conexión y las entradas.  
  
|||  
|-|-|  
|[BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map)|Marca el principio de las entradas del mapa de punto de conexión.|  
|[CONNECTION_POINT_ENTRY](#connection_point_entry)|Entra en puntos de conexión en el mapa.|  
|[CONNECTION_POINT_ENTRY_P](#connection_point_entry)| (2017 de visual Studio) Similar a CONNECTION_POINT_ENTRY pero toma un puntero a iid.|
|[END_CONNECTION_POINT_MAP](#end_connection_point_map)|Marca el final de las entradas del mapa de punto de conexión.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcom.h 
   
##  <a name="begin_connection_point_map"></a>  BEGIN_CONNECTION_POINT_MAP  
 Marca el principio de las entradas del mapa de punto de conexión.  
  
```
BEGIN_CONNECTION_POINT_MAP(x)
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de la clase que contiene los puntos de conexión.  
  
### <a name="remarks"></a>Comentarios  
 Iniciar la asignación de punto de conexión con el `BEGIN_CONNECTION_POINT_MAP` macro, agregue entradas para cada uno de los puntos de conexión con el [CONNECTION_POINT_ENTRY](#connection_point_entry) (macro) y complete el mapa con la [END_CONNECTION_POINT_MAP](#end_connection_point_map) macro.  
  
 Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#101](../../atl/codesnippet/cpp/connection-point-macros_1.h)]  
  
##  <a name="connection_point_entry"></a>  CONNECTION_POINT_ENTRY y CONNECTION_POINT_ENTRY_P  
 Especifica un punto de conexión para la interfaz especificada en la asignación de punto de conexión para que se puede tener acceso.  
  
```
CONNECTION_POINT_ENTRY(iid)
CONNECTION_POINT_ENTRY_P(piid) // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parámetros  
 `iid`  
 [in] El GUID de la interfaz que se agrega a la asignación de punto de conexión. 
 
 `piid`  
 [in] Puntero al GUID de la interfaz está activado.   
  
### <a name="remarks"></a>Comentarios  
 Las entradas de punto de conexión en el mapa se utilizan por [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md). La clase que contiene la asignación de punto de conexión debe heredar de `IConnectionPointContainerImpl`.  
  
 Iniciar la asignación de punto de conexión con el [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) macro, agregue entradas para cada uno de los puntos de conexión con el `CONNECTION_POINT_ENTRY` (macro) y complete el mapa con la [END_CONNECTION_POINT_MAP ](#end_connection_point_map) (macro).  
  
 Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#120](../../atl/codesnippet/cpp/connection-point-macros_2.h)]  
  
##  <a name="end_connection_point_map"></a>  END_CONNECTION_POINT_MAP  
 Marca el final de las entradas del mapa de punto de conexión.  
  
```
END_CONNECTION_POINT_MAP()
```  
  
### <a name="remarks"></a>Comentarios  
 Iniciar la asignación de punto de conexión con el [BEGIN_CONNECTION_POINT_MAP](#begin_connection_point_map) macro, agregue entradas para cada uno de los puntos de conexión con el [CONNECTION_POINT_ENTRY](#connection_point_entry) (macro) y complete el mapa con la `END_CONNECTION_POINT_MAP` macro.  
  
 Para obtener más información acerca de los puntos de conexión en ATL, vea el artículo [puntos de conexión](../../atl/atl-connection-points.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Windowing#128](../../atl/codesnippet/cpp/connection-point-macros_3.h)]  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [Funciones globales de punto de conexión](../../atl/reference/connection-point-global-functions.md)
