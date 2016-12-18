---
title: "CArrayRowset (Clase) | Microsoft Docs"
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
  - "ATL.CArrayRowset<TAccessor>"
  - "ATL.CArrayRowset"
  - "CArrayRowset"
  - "ATL::CArrayRowset"
  - "ATL::CArrayRowset<TAccessor>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CArrayRowset (clase)"
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CArrayRowset (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Tiene acceso a los elementos de un conjunto de filas con sintaxis de matriz.  
  
## Sintaxis  
  
```  
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### Parámetros  
 `TAccessor`  
 El tipo de clase de descriptor de acceso que desea que el conjunto de filas para utilizar.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|Constructor.|  
|[Instantánea](../../data/oledb/carrayrowset-snapshot.md)|Lee el conjunto de filas completo en memoria.|  
  
### Operadores  
  
|||  
|-|-|  
|[Operador &#91;&#93;](../../data/oledb/carrayrowset-operator.md)|Tiene acceso a un elemento de conjunto de filas.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[CArrayRowset::m\_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|El número de filas lee ya.|  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)