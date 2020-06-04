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
ms.openlocfilehash: 4b630a9728770a5e35e6d6300cf465b90238350c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209810"
---
# <a name="receiving-notifications"></a>Recibir notificaciones

OLE DB proporciona interfaces para recibir notificaciones cuando se producen eventos. Se describen en [OLE DB notificaciones de objeto](/previous-versions/windows/desktop/ms725406(v=vs.85)) en la **Referencia del programador de OLE DB**. La instalación de estos eventos utiliza el mecanismo de punto de conexión COM estándar. Por ejemplo, un objeto ATL que desea recuperar eventos a través de `IRowsetNotify` implementa la interfaz `IRowsetNotify` agregando `IRowsetNotify` a la lista derivada de la clase y exponiéndolo a través de una macro COM_INTERFACE_ENTRY.

`IRowsetNotify` tiene tres métodos, a los que se puede llamar en diversos momentos. Si desea responder solo a uno de estos métodos, puede usar la clase [irowsetnotifyimpl (](../../data/oledb/irowsetnotifyimpl-class.md) , que devuelve E_NOTIMPL para los métodos que no le interesan.

Al crear el conjunto de filas, debe indicar al proveedor que desea que el objeto de conjunto de filas devuelto admita `IConnectionPointContainer`, que es necesario para configurar la notificación.

En el código siguiente se muestra cómo abrir el conjunto de filas desde un objeto ATL y utilizar la función `AtlAdvise` para configurar el receptor de notificaciones. `AtlAdvise` devuelve una cookie que se usa al llamar a `AtlUnadvise`.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_IConnectionPointContainer, true);
```

A continuación, utilizado por el código siguiente:

```cpp
product.Open(session, _T("Products"), &propset);

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);
```

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
