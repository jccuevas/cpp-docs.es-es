---
title: "CTable (Clase) | Microsoft Docs"
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
  - "ATL::CTable"
  - "ATL.CTable"
  - "CTable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTable (clase)"
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTable (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona significa obtener acceso directamente a un conjunto de filas \(uno sin parámetros\).  
  
## Sintaxis  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CTable :    
   public CAccessorRowset <   
      TAccessor,    
      TRowset    
   >  
```  
  
#### Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
 `TRowset`  
 Una clase de conjunto de filas.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Abrir](../../data/oledb/ctable-open.md)|Abra la tabla.|  
  
## Comentarios  
 Vea [CCommand](../../data/oledb/ccommand-class.md) para obtener información sobre cómo ejecutar un comando de tener acceso a un conjunto de filas.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)