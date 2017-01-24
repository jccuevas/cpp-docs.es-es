---
title: "IDBCreateSessionImpl (Clase) | Microsoft Docs"
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
  - "IDBCreateSessionImpl"
  - "ATL.IDBCreateSessionImpl"
  - "ATL::IDBCreateSessionImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBCreateSessionImpl (clase)"
ms.assetid: 48c02c5c-8362-45ac-af8e-bb119cf8c5c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateSessionImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [IDBCreateSession](https://msdn.microsoft.com/en-us/library/ms724076.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class SessionClass>  
class ATL_NO_VTABLE IDBCreateSessionImpl   
   : public IDBCreateSession  
```  
  
#### Parámetros  
 `T`  
 SU CLASS, DERIVADA OF  
  
 `SessionClass`  
 Objeto de sesión.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[CreateSession](../../data/oledb/idbcreatesessionimpl-createsession.md)|Crea una nueva sesión del objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.|  
  
## Comentarios  
 Una interfaz de enlace en objetos de origen de datos.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)