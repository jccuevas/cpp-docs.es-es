---
title: "Admitir notificaciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "eventos [C++], notificaciones en OLE DB"
  - "notificaciones [C++], consumidores OLE DB"
  - "consumidores OLE DB, notificaciones"
  - "plantillas del proveedor OLE DB, notificaciones"
  - "proveedores OLE DB, notificaciones"
  - "conjuntos de filas, notificaciones de eventos"
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Admitir notificaciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Implementar interfaces de punto de conexión en el proveedor y en el consumidor  
 Para implementar notificaciones, una clase de proveedor debe heredar de [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) y [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).  
  
 `IRowsetNotifyCP` implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx).  `IRowsetNotifyCP` implementa funciones de difusión para advertir a los agentes de escucha del punto de conexión **IID\_IRowsetNotify** sobre cambios en el contenido del conjunto de filas.  
  
 Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor \(conocido también como el receptor\) mediante [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md), de forma que el consumidor pueda controlar las notificaciones.  Para obtener información sobre la implementación de la interfaz de punto de conexión en el consumidor, vea [Recibir notificaciones](../../data/oledb/receiving-notifications.md).  
  
 Además, la clase también debe contener un mapa que defina la entrada del punto de conexión, de la manera siguiente:  
  
```  
BEGIN_CONNECTION_POINT_MAP  
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)  
END_CONNECTION_POINT_MAP  
```  
  
## Agregar IRowsetNotify  
 Para agregar `IRowsetNotify`, debe agregar `IConnectionPointContainerImpl<rowset-name>` y `IRowsetNotifyCP<rowset-name>` a la cadena de herencia.  
  
 Por ejemplo, a continuación se muestra la cadena de herencia para `RUpdateRowset` en [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f):  
  
> [!NOTE]
>  El código del ejemplo puede ser diferente del mostrado aquí; debe considerar el código del ejemplo como la versión más actualizada.  
  
```  
///////////////////////////////////////////////////////////////////////////  
// class RUpdateRowset (in rowset.h)  
  
class RUpdateRowset :   
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,   
         CAtlArray< CAgentMan, CAtlArray<CAgentMan> >, CSimpleRow,   
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll > >,  
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,  
      public IConnectionPointContainerImpl<RUpdateRowset>,  
      public IRowsetNotifyCP<RUpdateRowset>  
```  
  
### Establecer entradas del mapa COM  
 También debe agregar las líneas siguientes al mapa COM del conjunto de filas:  
  
```  
COM_INTERFACE_ENTRY(IConnectionPointContainer)  
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)  
```  
  
 Estas macros permiten encontrar en el proveedor la interfaz solicitada llamando a `QueryInterface` para obtener el contenedor de punto de conexión \(la base de `IRowsetNotify`\).  Para consultar un ejemplo del uso de los puntos de conexión, vea el ejemplo ATL POLYGON y el tutorial.  
  
### Establecer entradas del mapa de puntos de conexión  
 También debe agregar un mapa de puntos de conexión.  Debe ser parecido al siguiente:  
  
```  
BEGIN_CONNECTION_POINT_MAP(rowset-name)  
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))  
END_CONNECTION_POINT_MAP()  
```  
  
 Este mapa de puntos de conexión permite a los componentes que busquen la interfaz `IRowsetNotify` encontrarla en el proveedor.  
  
### Establecer propiedades  
 También deberá agregar las siguientes propiedades al proveedor.  Sólo tendrá que agregar propiedades en función de las interfaces que admita.  
  
|Propiedad|Debe agregarla si admite|  
|---------------|------------------------------|  
|**DBPROP\_IConnectionPointContainer**|Siempre|  
|**DBPROP\_NOTIFICATIONGRANULARITY**|Siempre|  
|**DBPROP\_NOTIFICATIONPHASES**|Siempre|  
|**DBPROP\_NOTIFYCOLUMNSET**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWDELETE**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWINSERT**|`IRowsetChange`|  
|**DBPROP\_NOTIFYROWSETFETCHPOSITIONCHANGE**|Siempre|  
|**DBPROP\_NOTIFYROWFIRSTCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWSETRELEASE**|Siempre|  
|**DBPROP\_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDODELETE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUNDOCHANGE**|`IRowsetUpdate`|  
|**DBPROP\_NOTIFYROWUPDATE**|`IRowsetUpdate`|  
  
 La mayor parte de la implementación para las notificaciones ya está incrustada en las Plantillas de proveedor OLE DB.  Debido a una característica del compilador de Visual C\+\+ .NET, si no agrega `IRowsetNotifyCP` a la cadena de herencia, el compilador quita todo el código de la secuencia de compilación, con lo que se reduce el tamaño del código.  
  
## Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)