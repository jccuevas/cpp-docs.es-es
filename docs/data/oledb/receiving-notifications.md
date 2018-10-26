---
title: Recepción de notificaciones | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- receiving notifications in OLE DB
- events [C++], notifications in OLE DB
- notifications [C++], events
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB providers, notifications
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 244ebbfdb1ca706550fa26acd29e0af067cb1a7a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079719"
---
# <a name="receiving-notifications"></a>Recibir notificaciones

OLE DB proporciona interfaces para recibir notificaciones cuando se producen eventos. Estos métodos se describen en [notificaciones de objetos OLE DB](/previous-versions/windows/desktop/ms725406) en el **referencia del programador de OLE DB**. En la instalación de estos eventos se utiliza el mecanismo de punto de conexión COM estándar. Por ejemplo, un objeto ATL que desea recuperar eventos a través de `IRowsetNotify` implementa el `IRowsetNotify` interfaz agregando `IRowsetNotify` a la lista de clase derivada y exponerlo a través de una macro COM_INTERFACE_ENTRY.

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