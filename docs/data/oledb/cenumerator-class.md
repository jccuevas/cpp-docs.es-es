---
title: "CEnumerator (Clase) | Microsoft Docs"
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
  - "CEnumerator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumerator (clase)"
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEnumerator (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utiliza un objeto de enumerador OLE DB, que expone la interfaz de [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) para devolver un conjunto de filas que describe todos los orígenes de datos y enumeradores.  
  
## Sintaxis  
  
```  
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Find](../../data/oledb/cenumerator-find.md)|Buscar en los proveedores disponibles \(orígenes de datos\) que buscan uno con el nombre especificado.|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|Recupera la interfaz de `IMoniker` para el registro actual.|  
|[Abrir](../../data/oledb/cenumerator-open.md)|Abra el enumerador.|  
  
## Comentarios  
 Puede recuperar los datos de **ISourcesRowset** indirectamente de esta clase.  
  
## Requisitos  
 **Header:**atldbcli.h  
  
## Vea también  
 [DBViewer](../../top/visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)