---
title: Recibir notificaciones
ms.date: 10/24/2018
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
ms.openlocfilehash: 67f7eb5f77dc68b57f04ab4d016680255cb1ae86
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416025"
---
# <a name="receiving-notifications"></a>Recibir notificaciones

OLE DB proporciona interfaces para recibir notificaciones cuando se producen eventos. Estos métodos se describen en [notificaciones de objetos OLE DB](/previous-versions/windows/desktop/ms725406(v=vs.85)) en el **referencia del programador de OLE DB**. En la instalación de estos eventos se utiliza el mecanismo de punto de conexión COM estándar. Por ejemplo, un objeto ATL que desea recuperar eventos a través de `IRowsetNotify` implementa el `IRowsetNotify` interfaz agregando `IRowsetNotify` a la lista de clase derivada y exponerlo a través de una macro COM_INTERFACE_ENTRY.

`IRowsetNotify` tiene tres métodos, que se pueden llamar varias veces. Si desea responder sólo a uno de estos métodos, puede usar el [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) (clase), que devuelve E_NOTIMPL para los métodos que no le interesan.

Cuando se crea el conjunto de filas, se debe indicar al proveedor que desea que el objeto de conjunto de filas devuelto para admitir `IConnectionPointContainer`, que es necesario para configurar la notificación.

El código siguiente muestra cómo abrir el conjunto de filas de un objeto ATL y utilizar el `AtlAdvise` función para configurar el receptor de notificaciones. `AtlAdvise` Devuelve una cookie que se usa al llamar a `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

A continuación, usa el código siguiente:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)