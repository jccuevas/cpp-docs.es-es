---
title: "CBulkRowset (Clase) | Microsoft Docs"
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
  - "ATL::CBulkRowset"
  - "ATL.CBulkRowset"
  - "ATL::CBulkRowset<TAccessor>"
  - "CBulkRowset"
  - "ATL.CBulkRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBulkRowset (clase)"
ms.assetid: c6bde426-c543-4022-a98a-9519d9e2ae59
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBulkRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las búsquedas y manipular filas para trabajar con datos de forma masiva recuperar múltiples identificadores de fila con una única llamada.  
  
## Sintaxis  
  
```  
template <class TAccessor>  
class CBulkRowset : public CRowset<TAccessor>  
```  
  
#### Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[AddRefRows](../../data/oledb/cbulkrowset-addrefrows.md)|Incrementa el recuento de referencias.|  
|[CBulkRowset](../../data/oledb/cbulkrowset-cbulkrowset.md)|Constructor.|  
|[MoveFirst](../../data/oledb/cbulkrowset-movefirst.md)|Recupera la primera fila de datos, realice una nueva búsqueda masivas en caso necesario.|  
|[MoveLast](../../data/oledb/cbulkrowset-movelast.md)|Se desplaza a la última fila.|  
|[MoveNext](../../data/oledb/cbulkrowset-movenext.md)|Recupera la fila siguiente de datos.|  
|[MovePrev](../../data/oledb/cbulkrowset-moveprev.md)|Se desplaza a la fila anterior.|  
|[MoveToBookmark](../../data/oledb/cbulkrowset-movetobookmark.md)|Captura la fila marcada por un marcador o una fila de un desplazamiento especificado del marcador.|  
|[MoveToRatio](../../data/oledb/cbulkrowset-movetoratio.md)|Captura filas de una posición fraccionarios en el conjunto de filas.|  
|[ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)|Establece la fila actual \(**m\_nCurrentRow**\) a cero y a libera todas las filas.|  
|[SetRows](../../data/oledb/cbulkrowset-setrows.md)|Establece el número de identificadores de fila que se recuperarán por una llamada.|  
  
## Ejemplo  
 El ejemplo siguiente se muestra el uso de la clase de `CBulkRowset` .  
  
 [!code-cpp[NVC_OLEDB_Consumer#1](../../data/oledb/codesnippet/CPP/cbulkrowset-class_1.cpp)]  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)