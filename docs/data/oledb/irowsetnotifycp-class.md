---
title: "IRowsetNotifyCP (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IRowsetNotifyCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyCP (clase)"
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IRowsetNotifyCP (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa el sitio del proveedor para la interfaz [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)de punto de conexión.  
  
## Sintaxis  
  
```  
template <  
   class T,   
   class ReentrantEventSync = CComSharedMutex   
>  
class IRowsetNotifyCP :   
   public IConnectionPointImpl<  
      T,   
      piid = &__uuidof(IRowsetNotify),   
      CComDynamicUnkArray DynamicUnkArray  
   >,  
   public ReentrantEventSync  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de `IRowsetNotifyCP`.  
  
 `ReentrantEventSync`  
 Una clase mutex que admite el entrar \(el valor predeterminado es **CComSharedMutex**\).  Una exclusión mutua es un objeto de sincronización que permite que un subproceso tenga \- acceso exclusivo a un recurso.  
  
 `piid`  
 Un puntero de identificador de interfaz \(**IID\***\) para una interfaz de puntos de conexión de **IRowsetNotify** .  El valor predeterminado es **&\_\_uuidof\(IRowsetNotify\)**.  
  
 `DynamicUnkArray`  
 Una matriz de [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)escrito, que es una matriz dinámicamente asignado de punteros de **IUnknown** a las interfaces de receptor de cliente.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Fire\_OnFieldChange](../../data/oledb/irowsetnotifycp-fire-onfieldchange.md)|Notifica al consumidor de un cambio del valor de una columna.|  
|[Fire\_OnRowChange](../../data/oledb/irowsetnotifycp-fire-onrowchange.md)|Notifica al consumidor de un cambio que afecta a las filas.|  
|[Fire\_OnRowsetChange](../../data/oledb/irowsetnotifycp-fire-onrowsetchange.md)|Notifica al consumidor de un cambio que afecta al conjunto de filas completo.|  
  
## Comentarios  
 `IRowsetNotifyCP` implementa funciones de difusión para advertir a los agentes de escucha del punto de conexión **IID\_IRowsetNotify** sobre cambios en el contenido del conjunto de filas.  
  
 Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor \(también conocido como “receptor”\) mediante [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) de modo que el consumidor pueda controlar notificaciones.  Vea [Recibir notificaciones](../../data/oledb/receiving-notifications.md) sobre la implementación de la interfaz de punto de conexión en el consumidor.  
  
 Para obtener información detallada sobre cómo implementar notificaciones, vea “admitir notificaciones” en [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Notifications \(COM\)](http://msdn.microsoft.com/library/windows/desktop/ms678433)   
 [Overview of Notifications \(OLE DB\)](https://msdn.microsoft.com/en-us/library/ms725406.aspx)   
 [BEGIN\_CONNECTION\_POINT\_MAP](../Topic/BEGIN_CONNECTION_POINT_MAP.md)   
 [END\_CONNECTION\_POINT\_MAP](../Topic/END_CONNECTION_POINT_MAP.md)   
 [CONNECTION\_POINT\_ENTRY](../Topic/CONNECTION_POINT_ENTRY.md)   
 [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)