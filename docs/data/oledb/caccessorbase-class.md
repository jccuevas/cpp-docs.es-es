---
title: "CAccessorBase (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CAccessorBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAccessorBase (clase)"
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# CAccessorBase (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Todos los descriptores de acceso de las plantillas OLE DB derivan de esta clase.  `CAccessorBase` permite que un conjunto de filas administrar múltiples descriptores de acceso.  También proporciona el enlace para ambas columnas de los parámetros y de salida.  
  
## Sintaxis  
  
```  
// Replace with syntax  
```  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[Cerrar](../../data/oledb/caccessorbase-close.md)|Cierre los descriptores de acceso.|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|Recupera el identificador de descriptor de acceso.|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|Recupera el número de descriptores de acceso creados por la clase.|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|Comprueba si el descriptor de acceso especificado es autoaccessor\).|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|Libera los descriptores de acceso.|  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)