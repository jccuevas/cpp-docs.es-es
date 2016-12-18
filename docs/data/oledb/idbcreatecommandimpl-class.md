---
title: "IDBCreateCommandImpl (Clase) | Microsoft Docs"
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
  - "ATL::IDBCreateCommandImpl"
  - "IDBCreateCommandImpl"
  - "ATL.IDBCreateCommandImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBCreateCommandImpl (clase)"
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBCreateCommandImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class CommandClass >  
class ATL_NO_VTABLE IDBCreateCommandImpl   
   : public IDBCreateCommand  
```  
  
#### Parámetros  
 `T`  
 El objeto de sesión derivado de `IDBCreateCommandImpl`.  
  
 `CommandClass`  
 La clase de comando.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[CreateCommand](../../data/oledb/idbcreatecommandimpl-createcommand.md)|Crea un nuevo comando.|  
  
## Comentarios  
 Una interfaz opcional en el objeto de sesión para obtener un nuevo comando.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)