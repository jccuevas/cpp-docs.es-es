---
title: "IRowsetNotifyImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IRowsetNotifyImpl"
  - "ATL::IRowsetNotifyImpl"
  - "IRowsetNotifyImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetNotifyImpl (clase)"
ms.assetid: fbfd0cb2-38ff-4b42-899a-8de902f834b8
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# IRowsetNotifyImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa y registra [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) en el consumidor \(también conocido como “receptor”\) para que pueda controlar notificaciones.  
  
## Sintaxis  
  
```  
class ATL_NO_VTABLE IRowsetNotifyImpl : public IRowsetNotify  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[OnFieldChange](../../data/oledb/irowsetnotifyimpl-onfieldchange.md)|Notifica al consumidor cualquier cambio en el valor de una columna.|  
|[OnRowChange](../../data/oledb/irowsetnotifyimpl-onrowchange.md)|Notifica al consumidor el primer cambio en una fila o cualquier cambio que afecte a la fila completa.|  
|[OnRowsetChange](../../data/oledb/irowsetnotifyimpl-onrowsetchange.md)|Notifica al consumidor cualquier cambio que afecte al conjunto de filas completo.|  
  
## Comentarios  
 Vea [Recibir notificaciones](../../data/oledb/receiving-notifications.md) sobre la implementación de la interfaz de punto de conexión en el consumidor.  
  
 `IRowsetNotifyImpl` proporciona una implementación ficticia para `IRowsetNotify`, con las funciones vacías para los métodos [OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx), [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx), y [OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)de `IRowsetNotify` .  Si hereda de esta clase cuando implementa una interfaz de `IRowsetNotify` , puede implementar los métodos que necesita.  También necesita proporcionar implementaciones vacías para los otros métodos usted mismo.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx)   
 [IRowsetNotifyCP \(Clase\)](../../data/oledb/irowsetnotifycp-class.md)