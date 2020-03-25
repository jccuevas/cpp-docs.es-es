---
title: Admitir notificaciones
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: d29f84a0a5b33d55c0a04a4c758050cf9746f72a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209563"
---
# <a name="supporting-notifications"></a>Admitir notificaciones

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Implementar interfaces de punto de conexión en el proveedor y el consumidor

Para implementar notificaciones, una clase de proveedor debe heredar de [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) y [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` implementa el sitio del proveedor para la interfaz de punto de conexión [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` implementa funciones de difusión para informar a los agentes de escucha en el punto de conexión `IID_IRowsetNotify` de los cambios en el contenido del conjunto de filas.

También debe implementar y registrar `IRowsetNotify` en el consumidor (también conocido como receptor) con [irowsetnotifyimpl (](../../data/oledb/irowsetnotifyimpl-class.md) para que el consumidor pueda controlar las notificaciones. Para obtener información sobre cómo implementar la interfaz de punto de conexión en el consumidor, consulte [recibir notificaciones](../../data/oledb/receiving-notifications.md).

Además, la clase debe tener una asignación que defina la entrada del punto de conexión, como se indica a continuación:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Agregar IRowsetNotify

Para agregar `IRowsetNotify`, debe agregar `IConnectionPointContainerImpl<rowset-name>` y `IRowsetNotifyCP<rowset-name>` a la cadena de herencia.

Por ejemplo, esta es la cadena de herencia para `RUpdateRowset` en [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> El código de ejemplo puede diferir de lo que se muestra aquí; se debe considerar como la versión más actualizada.

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

### <a name="setting-com-map-entries"></a>Establecer entradas de asignación COM

También debe agregar lo siguiente al mapa COM del conjunto de filas:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Estas macros permiten a cualquier persona que llame a `QueryInterface` para el contenedor de puntos de conexión (la base de `IRowsetNotify`) buscar la interfaz solicitada en el proveedor. Para obtener un ejemplo de cómo usar puntos de conexión, vea el ejemplo de polígono de ATL y el tutorial.

### <a name="setting-connection-point-map-entries"></a>Establecer entradas de asignación de puntos de conexión

También debe agregar una asignación de punto de conexión. Debe tener un aspecto similar al siguiente:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Esta asignación de puntos de conexión permite a un componente buscar la interfaz `IRowsetNotify` para encontrarla en el proveedor.

### <a name="setting-properties"></a>Establecer propiedades

También debe agregar las siguientes propiedades al proveedor. Solo tiene que agregar propiedades basadas en las interfaces que admita.

|Propiedad|Agregar si se admite|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Siempre|
|DBPROP_NOTIFICATIONGRANULARITY|Siempre|
|DBPROP_NOTIFICATIONPHASES|Siempre|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Siempre|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Siempre|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

La mayor parte de la implementación de las notificaciones ya está incrustada en las plantillas de proveedor de OLE DB. Si no agrega `IRowsetNotifyCP` a la cadena de herencia, el compilador quita todo ese código del flujo de compilación, lo que hace que el tamaño del código sea menor.

## <a name="see-also"></a>Consulte también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
