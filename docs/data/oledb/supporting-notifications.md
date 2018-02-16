---
title: Admitir notificaciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cbdb3b7faaec99f9893df29e8d368fd05c8fd111
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="supporting-notifications"></a>Admitir notificaciones
## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementar Interfaces de punto de conexión en el proveedor y el consumidor  
 Para implementar notificaciones, una clase de proveedor debe heredar de [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) y [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).  
  
 `IRowsetNotifyCP` implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx). `IRowsetNotifyCP` implementa las funciones para indicar que los agentes de escucha en el punto de conexión de difusión **IID_IRowsetNotify** de los cambios en el contenido del conjunto de filas.  
  
 Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor (también conocido como el receptor) mediante [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) para que el consumidor pueda controlar las notificaciones. Para obtener información sobre cómo implementar la interfaz de punto de conexión en el consumidor, consulte [recibir notificaciones](../../data/oledb/receiving-notifications.md).  
  
 Además, la clase también debe contener un mapa que define la entrada de punto de conexión, similar al siguiente:  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## <a name="adding-irowsetnotify"></a>Agregar IRowsetNotify  
 Para agregar `IRowsetNotify`, debe agregar `IConnectionPointContainerImpl<rowset-name>` y `IRowsetNotifyCP<rowset-name>` a la cadena de herencia.  
  
 Por ejemplo, esta es la cadena de herencia para `RUpdateRowset` en [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  El código de ejemplo puede diferir de lo que se muestre aquí; el ejemplo de código se debe considerar como la versión más actualizada.  
  
```cpp
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### <a name="setting-com-map-entries"></a>Establecer entradas del mapa COM  
 También debe agregar lo siguiente a la asignación de COM en el conjunto de filas:  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 Estas macros permiten llamar a `QueryInterface` para el contenedor de punto de conexión (la base de `IRowsetNotify`) para buscar la interfaz solicitada en el proveedor. Para obtener un ejemplo de cómo usar puntos de conexión, vea el ejemplo ATL POLYGON y el tutorial.  
  
### <a name="setting-connection-point-map-entries"></a>Entradas de mapa de puntos de conexión de configuración  
 También debe agregar un mapa de puntos de conexión. Debería ser similar:  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 Este mapa de puntos de conexión permite a los componentes buscando el `IRowsetNotify` interfaz encontrarla en el proveedor.  
  
### <a name="setting-properties"></a>Establecer las propiedades  
 También debe agregar las siguientes propiedades al proveedor. Basta con agregar propiedades en función de las interfaces que se admiten.  
  
|Property|Debe agregarla si admite|  
|--------------|------------------------|  
|**DBPROP_IConnectionPointContainer**|Always|  
|**DBPROP_NOTIFICATIONGRANULARITY**|Always|  
|**DBPROP_NOTIFICATIONPHASES**|Always|  
|**DBPROP_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE**|Always|  
|**DBPROP_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWSETRELEASE**|Always|  
|**DBPROP_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUNDOINSERT**|`IRowsetUpdate`|  
|**DBPROP_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 La mayor parte de la implementación para las notificaciones ya está incrustada en las plantillas de proveedor OLE DB. Si no se agrega `IRowsetNotifyCP` a la cadena de herencia, el compilador quita todo el código de la secuencia de compilación, lo que hace que el tamaño del código sea más pequeño.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)