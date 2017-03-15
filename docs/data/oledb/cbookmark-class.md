---
title: "CBookmark (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.CBookmark"
  - "ATL::CBookmark<nSize>"
  - "CBookmark"
  - "ATL.CBookmark<nSize>"
  - "ATL::CBookmark"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBookmark (clase)"
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CBookmark (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contiene un valor de marcador de posición en el búfer.  
  
## Sintaxis  
  
```  
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase  
template < >  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
#### Parámetros  
 `nSize`  
 El tamaño del búfer del marcador en bytes.  Cuando `nSize` es cero, el búfer del marcador se creará dinámicamente en tiempo de ejecución.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[CBookmark](../../data/oledb/cbookmark-class.md)|El constructor|  
|[GetBuffer](../../data/oledb/cbookmark-getbuffer.md)|Recupera el puntero al búfer.|  
|[GetSize](../../data/oledb/cbookmark-getsize.md)|Recupera el tamaño de búfer en bytes.|  
|[SetBookmark](../../data/oledb/cbookmark-setbookmark.md)|Establece el valor del marcador.|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../../data/oledb/cbookmark-operator-equal.md)|Asignaciones una clase de `CBookmark` a otra.|  
  
## Comentarios  
 **CBookmark\<0\>** es una especialización de plantilla de `CBookmark`; el búfer se crea dinámicamente en tiempo de ejecución.  
  
## Requisitos  
 **Header:** atldbcli.h  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)