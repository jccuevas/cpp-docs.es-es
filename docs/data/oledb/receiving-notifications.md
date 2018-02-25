---
title: Recibir notificaciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 50911440acbc7514b091a439d42bf73ee60353f9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="receiving-notifications"></a>Recibir notificaciones
OLE DB proporciona interfaces para recibir notificaciones cuando se producen eventos. Se describen en [notificaciones de objetos OLE DB](https://msdn.microsoft.com/en-us/library/ms725406.aspx) en el *referencia del programador de OLE DB*. El programa de instalación de estos eventos usa el mecanismo de punto de conexión COM estándar. Por ejemplo, un objeto ATL que desea recuperar eventos a través de `IRowsetNotify` implementa la `IRowsetNotify` interfaz agregando `IRowsetNotify` a la lista de la clase derivada y exponerlo a través de un **COM_INTERFACE_ENTRY** macro.  
  
 `IRowsetNotify` tiene tres métodos, que se pueden llamar varias veces. Si desea responder a solo uno de estos métodos, puede usar el [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) de la clase, que devuelve **E_NOTIMPL** para los métodos que no le interesa.  
  
 Cuando se crea el conjunto de filas, se debe indicar al proveedor que desea que el objeto de conjunto de filas devuelto para admitir **IConnectionPointContainer**, que es necesario para configurar la notificación.  
  
 El código siguiente muestra cómo abrir el conjunto de filas desde un objeto ATL y utilizar el `AtlAdvise` función para configurar el receptor de notificación. `AtlAdvise` Devuelve una cookie que se utiliza cuando se llama a `AtlUnadvise`.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  

propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  

product.Open(session, _T("Products"), &propset);  
  

AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)