---
title: Admitir notificaciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 984f1bf9e716c94885df62d91f670627e89b7aab
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075013"
---
# <a name="supporting-notifications"></a>Admitir notificaciones

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementar Interfaces de punto de conexión en el proveedor y consumidor

Para implementar notificaciones, una clase de proveedor debe heredar de [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) y [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](/previous-versions/windows/desktop/ms712959). `IRowsetNotifyCP` implementa funciones aconsejar a los agentes de escucha en el punto de conexión de difusión `IID_IRowsetNotify` de los cambios en el contenido del conjunto de filas.

Tenga en cuenta que también debe implementar y registrar `IRowsetNotify` en el consumidor (también conocido como el receptor) mediante [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) para que el consumidor puede controlar las notificaciones. Para obtener información acerca de cómo implementar la interfaz de punto de conexión del consumidor, consulte [recibir notificaciones](../../data/oledb/receiving-notifications.md).

Además, la clase también debe contener una asignación que define la entrada de punto de conexión, similar al siguiente:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Agregar IRowsetNotify

Para agregar `IRowsetNotify`, deberá agregar `IConnectionPointContainerImpl<rowset-name>` y `IRowsetNotifyCP<rowset-name>` a la cadena de herencia.

Por ejemplo, esta es la cadena de herencia para `RUpdateRowset` en [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> El código de ejemplo puede diferir de lo que se muestra aquí. el código de ejemplo se debe considerar como la versión más actualizada.

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

### <a name="setting-com-map-entries"></a>Configuración de las entradas de mapa COM

También debe agregar lo siguiente al mapa COM en el conjunto de filas:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Estas macros que nadie llame a `QueryInterface` para el contenedor de punto de conexión (la base de `IRowsetNotify`) para buscar en el proveedor de la interfaz solicitada. Para obtener un ejemplo de cómo usar puntos de conexión, vea el ejemplo ATL POLYGON y el tutorial.

### <a name="setting-connection-point-map-entries"></a>Entradas de mapa de puntos de conexión de configuración

También deberá agregar un mapa de puntos de conexión. Debe ser similar:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Este mapa de puntos de conexión permite a los componentes buscando el `IRowsetNotify` interfaz encontrarla en el proveedor.

### <a name="setting-properties"></a>Establecer las propiedades

También deberá agregar las siguientes propiedades para el proveedor. Solo deberá agregar propiedades en función de las interfaces que proporciona soporte técnico.

|Property|Agregar si admite|
|--------------|------------------------|
|`DBPROP_IConnectionPointContainer`|Always|
|`DBPROP_NOTIFICATIONGRANULARITY`|Always|
|`DBPROP_NOTIFICATIONPHASES`|Always|
|`DBPROP_NOTIFYCOLUMNSET`|`IRowsetChange`|
|`DBPROP_NOTIFYROWDELETE`|`IRowsetChange`|
|`DBPROP_NOTIFYROWINSERT`|`IRowsetChange`|
|`DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE`|Always|
|`DBPROP_NOTIFYROWFIRSTCHANGE`|`IRowsetUpdate`|
|`DBPROP_NOTIFYROWSETRELEASE`|Always|
|`DBPROP_NOTIFYROWUNDOCHANGE`|`IRowsetUpdate`|
|`DBPROP_NOTIFYROWUNDODELETE`|`IRowsetUpdate`|
|`DBPROP_NOTIFYROWUNDOINSERT`|`IRowsetUpdate`|
|`DBPROP_NOTIFYROWUPDATE`|`IRowsetUpdate`|

La mayoría de la implementación para las notificaciones ya está incrustada en las plantillas de proveedor OLE DB. Si no agrega `IRowsetNotifyCP` a la cadena de herencia, el compilador quita todo el código de la secuencia de compilación, lo que hace que el tamaño del código sea más pequeño.

## <a name="see-also"></a>Vea también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)