---
title: "CReferentialConstraints, CReferentialConstraintInfo | Microsoft Docs"
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
  - "m_szUniqueName"
  - "m_szCatalog"
  - "DELETE_RULE"
  - "m_szUniqueCatalog"
  - "CONSTRAINT_NAME"
  - "CReferentialConstraintInfo"
  - "MATCH_OPTION"
  - "m_szSchema"
  - "m_szDeleteRule"
  - "m_szUpdateRule"
  - "m_szUniqueSchema"
  - "CReferentialConstraints"
  - "m_szName"
  - "CONSTRAINT_CATALOG"
  - "m_szMatchOption"
  - "CONSTRAINT_SCHEMA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "CReferentialConstraintInfo (clase de parámetro)"
  - "CReferentialConstraints (clase de definiciones de tipo)"
  - "DELETE_RULE"
  - "DESCRIPTION (miembro de datos de clase)"
  - "m_szCatalog"
  - "m_szDeleteRule"
  - "m_szDescription"
  - "m_szMatchOption"
  - "m_szName"
  - "m_szSchema"
  - "m_szUniqueCatalog"
  - "m_szUniqueName"
  - "m_szUniqueSchema"
  - "m_szUpdateRule"
  - "MATCH_OPTION"
ms.assetid: 5d485358-be29-41c2-b0ce-19e023598e73
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CReferentialConstraints, CReferentialConstraintInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CReferentialConstraints** typedef para implementar la clase **CReferentialConstraintInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica las restricciones de referencia, definidos en el catálogo, que pertenecen a un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas de REFERENTIAL\_CONSTRAINTS](https://msdn.microsoft.com/en-us/library/ms719737.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_szUniqueCatalog|UNIQUE\_CONSTRAINT\_CATALOG|  
|m\_szUniqueSchema|UNIQUE\_CONSTRAINT\_SCHEMA|  
|m\_szUniqueName|UNIQUE\_CONSTRAINT\_NAME|  
|m\_szMatchOption|MATCH\_OPTION|  
|m\_szUpdateRule|UPDATE\_RULE|  
|m\_szDeleteRule|DELETE\_RULE|  
|m\_szDescription|DESCRIPTION|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)