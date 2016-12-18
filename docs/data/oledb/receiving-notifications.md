---
title: "Recibir notificaciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "notificaciones [C++], eventos"
  - "notificaciones [C++], consumidores OLE DB"
  - "consumidores OLE DB, notificaciones"
  - "proveedores OLE DB, notificaciones"
  - "recibir notificaciones en OLE DB"
  - "conjuntos de filas, notificaciones de eventos"
ms.assetid: 305a1103-0c87-40c8-94bc-7fbbdd52ae32
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Recibir notificaciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE DB proporciona interfaces para recibir notificaciones cuando se producen eventos.  Éstas se describen en [Notificaciones de objetos OLE DB](https://msdn.microsoft.com/en-us/library/ms725406.aspx), en la *Referencia del programador de OLE DB*.  La configuración de estos eventos usa el mecanismo COM estándar de punto de conexión.  Por ejemplo, un objeto ATL que desea recuperar eventos por medio de `IRowsetNotify` implementa la interfaz `IRowsetNotify` agregando `IRowsetNotify` a la lista derivada de la clase y exponiéndola a través de una macro **COM\_INTERFACE\_ENTRY**.  
  
 `IRowsetNotify` tiene tres métodos, a los que se puede llamar en varios momentos.  Si sólo desea responder a uno de estos métodos, puede utilizar la clase [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md), que devuelve **E\_NOTIMPL** para los métodos en los que no se está interesado.  
  
 Al crear el conjunto de filas, se debe indicar al proveedor que se desea que el objeto de conjunto de filas devuelto sea compatible con **IConnectionPointContainer**, que es necesario para crear la notificación.  
  
 En el código siguiente se muestra cómo abrir el conjunto de filas de un objeto ATL y cómo usar la función `AtlAdvise` para configurar el receptor de notificación.  `AtlAdvise` devuelve una cookie que se usa cuando se llama a `AtlUnadvise`.  
  
```  
CDBPropSet propset(DBPROPSET_ROWSET);  
propset.AddProperty(DBPROP_IConnectionPointContainer, true);  
  
product.Open(session, _T("Products"), &propset);  
  
AtlAdvise(product.m_spRowset, GetUnknown(), IID_IRowsetNotify, &m_dwCookie);  
```  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)