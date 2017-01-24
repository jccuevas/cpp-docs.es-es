---
title: "CEnumeratorAccessor (Clase) | Microsoft Docs"
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
  - "ATL::CEnumeratorAccessor"
  - "CEnumeratorAccessor"
  - "ATL.CEnumeratorAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEnumeratorAccessor (clase)"
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEnumeratorAccessor (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Utilizado por [CEnumerator](../../data/oledb/cenumerator-class.md) para tener acceso a los datos del conjunto de filas de enumeradores.  
  
## Sintaxis  
  
```  
class CEnumeratorAccessor  
```  
  
## Miembros  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Una variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.|  
|[m\_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Una variable que indica si la fila describe un origen de datos o un enumerador.|  
|[m\_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|Descripción del origen de datos o del enumerador.|  
|[m\_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|El nombre del origen de datos o del enumerador.|  
|[m\_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Cadena que pasar a [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) para obtener un moniker para el origen de datos o el enumerador.|  
  
## Comentarios  
 Este conjunto de filas está formado por los orígenes de datos y los enumeradores visible del enumerador actual.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)