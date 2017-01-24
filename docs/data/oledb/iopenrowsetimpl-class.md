---
title: "IOpenRowsetImpl (Clase) | Microsoft Docs"
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
  - "IOpenRowsetImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IOpenRowsetImpl (clase)"
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IOpenRowsetImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la implementación de la interfaz de `IOpenRowset` .  
  
## Sintaxis  
  
```  
template <class SessionClass>  
class IOpenRowsetImpl : public IOpenRowset  
```  
  
#### Parámetros  
 `SessionClass`  
 La clase, derivada de `IOpenRowsetImpl`.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CreateRowset](../../data/oledb/iopenrowsetimpl-createrowset.md)|Crea un objeto de conjunto de filas.  No denominado directamente por el usuario.|  
|[OpenRowset](../../data/oledb/iopenrowsetimpl-openrowset.md)|Abre y devuelve un conjunto de filas que incluya todas las filas de una sola tabla o índice. \(No en ATLDB.H\)|  
  
## Comentarios  
 La interfaz de [IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx) es obligatoria para un objeto de sesión.  Abre y devuelve un conjunto de filas que incluya todas las filas de una sola tabla o índice.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)