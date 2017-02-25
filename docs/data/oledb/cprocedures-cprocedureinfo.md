---
title: "CProcedures, CProcedureInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CProcedures"
  - "m_szCatalog"
  - "CProcedureInfo"
  - "m_szSchema"
  - "m_szDefinition"
  - "m_szName"
  - "m_nType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProcedureInfo (clase de parámetro)"
  - "CProcedures (clase de definiciones de tipo)"
  - "DESCRIPTION (miembro de datos de clase)"
  - "m_nType"
  - "m_szCatalog"
  - "m_szDefinition"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: d0c7375e-ee0c-441d-aae6-6108150860a0
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CProcedures, CProcedureInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CProcedures** typedef para implementar la clase **CProcedureInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica los procedimientos, definidos en el catálogo, que pertenecen a un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas de los PROCEDIMIENTOS](https://msdn.microsoft.com/en-us/library/ms724021.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szCatalog|PROCEDURE\_CATALOG|  
|m\_szSchema|PROCEDURE\_SCHEMA|  
|m\_szName|PROCEDURE\_NAME|  
|m\_nType|PROCEDURE\_TYPE|  
|m\_szDefinition|PROCEDURE\_DEFINITION|  
|m\_szDescription|DESCRIPTION|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)