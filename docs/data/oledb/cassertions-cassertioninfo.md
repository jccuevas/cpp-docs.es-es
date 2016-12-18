---
title: "CAssertions, CAssertionInfo | Microsoft Docs"
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
  - "CAssertions"
  - "m_szCatalog"
  - "m_bInitiallyDeferred"
  - "CONSTRAINT_NAME"
  - "m_szSchema"
  - "INITIALLY_DEFERRED"
  - "m_bIsDeferrable"
  - "m_szName"
  - "CAssertionInfo"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_SCHEMA"
  - "IS_DEFERRABLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAssertionInfo (clase de parámetro)"
  - "CAssertions (clase de definiciones de tipo)"
  - "CONSTRAINT_CATALOG"
  - "CONSTRAINT_NAME"
  - "CONSTRAINT_SCHEMA"
  - "DESCRIPTION (miembro de datos de clase)"
  - "INITIALLY_DEFERRED"
  - "IS_DEFERRABLE"
  - "m_bInitiallyDeferred"
  - "m_bIsDeferrable"
  - "m_szCatalog"
  - "m_szDescription"
  - "m_szName"
  - "m_szSchema"
ms.assetid: 2a79c2da-5c9b-4fa6-98e8-90b7f5d6f021
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAssertions, CAssertionInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CAssertions** typedef para implementar la clase **CAssertionInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica las aserciones definidas en el catálogo que son propiedad de un usuario determinado.  
  
 La tabla siguiente se muestran los miembros de datos de la clase para **CAssertionInfo** y las columnas correspondientes de OLE DB.  Vea [Conjunto de filas ASERCIONES](https://msdn.microsoft.com/en-us/library/ms719776.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szCatalog|CONSTRAINT\_CATALOG|  
|m\_szSchema|CONSTRAINT\_SCHEMA|  
|m\_szName|CONSTRAINT\_NAME|  
|m\_bIsDeferrable|IS\_DEFERRABLE|  
|m\_bInitiallyDeferred|INITIALLY\_DEFERRED|  
|m\_szDescription|DESCRIPTION|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)