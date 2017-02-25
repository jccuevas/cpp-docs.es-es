---
title: "CAccessorRowset (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAccessorRowset"
  - "ATL.CAccessorRowset"
  - "ATL::CAccessorRowset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorRowset (clase)"
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CAccessorRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula un conjunto de filas y sus descriptores de acceso asociados en una sola clase.  
  
## Sintaxis  
  
```  
template <   
   class TAccessor = CNoAccessor,    
   template <typename T> class TRowset = CRowset    
>  
class CAccessorRowset :   
   public TAccessor,    
   public TRowset<TAccessor>  
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
|[Bind](../../data/oledb/caccessorrowset-bind.md)|Crea los enlaces \(utilizados cuando **bBind** se especifica como false en [CCommand::Open](../../data/oledb/ccommand-open.md)\).|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|Constructor.|  
|[Cerrar](../../data/oledb/caccessorrowset-close.md)|Cierre el conjunto de filas y los descriptores de acceso.|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|Libera cualquier columna del registro actual que necesita ser liberado.|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|Implementa [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx).|  
  
## Comentarios  
 La clase `TAccessor` administra el descriptor de acceso.  La clase *TRowset* administra el conjunto de filas.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)