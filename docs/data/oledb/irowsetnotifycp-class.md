---
title: IRowsetNotifyCP (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetNotifyCP
dev_langs:
- C++
helpviewer_keywords:
- IRowsetNotifyCP class
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19147710ce8965222eed998e1a7ab4baa1e32caf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetnotifycp-class"></a>IRowsetNotifyCP (Clase)
Implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx).  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray>,  
   public ReentrantEventSync  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de `IRowsetNotifyCP`.  
  
 `ReentrantEventSync`  
 Una clase de exclusión mutua que admite la reentrada (el valor predeterminado es **CComSharedMutex**). Una exclusión mutua es un objeto de sincronización que permite que un subproceso tenga acceso mutuamente exclusivo a un recurso.  
  
 `piid`  
 Un puntero de identificador de interfaz (**IID\***) para un **IRowsetNotify** interfaz puntos de conexión. El valor predeterminado es **& __uuidof(IRowsetNotify)**.  
  
 `DynamicUnkArray`  
 Una matriz de tipo [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que es una matriz asignada dinámicamente de **IUnknown** interfaces de receptor de punteros al cliente.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Fire_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|Notifica al consumidor de un cambio en el valor de una columna.|  
|[Fire_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|Notifica al consumidor de un cambio que afecta a las filas.|  
|[Fire_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|Notifica al consumidor de un cambio que afecta a todo el conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 `IRowsetNotifyCP` implementa las funciones para indicar que los agentes de escucha en el punto de conexión de difusión **IID_IRowsetNotify** de los cambios en el contenido del conjunto de filas.  
  
 Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor (también conocido como el "receptor") mediante [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) para que el consumidor pueda controlar las notificaciones. Vea [recibir notificaciones](../../data/oledb/receiving-notifications.md) acerca de cómo implementar la interfaz de punto de conexión en el consumidor.  
  
 Para obtener información detallada sobre la implementación de las notificaciones, vea "Compatibilidad con notificaciones" en [crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Notificaciones (COM)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)   
 [END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)   
 [CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)   
 [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)