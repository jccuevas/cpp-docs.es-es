---
title: "CCollations, CCollationInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COLLATION_CATALOG"
  - "m_szCatalog"
  - "CCollationInfo"
  - "CCollations"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "m_szCharSetName"
  - "m_szSchema"
  - "CHARACTER_SET_CATALOG"
  - "m_szCharSetSchema"
  - "m_szCharSetCatalog"
  - "m_szPadAttribute"
  - "COLLATION_NAME"
  - "COLLATION_SCHEMA"
  - "m_szName"
  - "COLLATIONS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCollationInfo (clase de parámetro)"
  - "CCollations (clase de definiciones de tipo)"
  - "CHARACTER_SET_CATALOG"
  - "CHARACTER_SET_NAME"
  - "CHARACTER_SET_SCHEMA"
  - "COLLATION_CATALOG"
  - "COLLATION_NAME"
  - "COLLATION_SCHEMA"
  - "COLLATIONS (conjunto de registros)"
  - "m_szCatalog"
  - "m_szCharSetCatalog"
  - "m_szCharSetName"
  - "m_szCharSetSchema"
  - "m_szName"
  - "m_szPadAttribute"
  - "m_szSchema"
ms.assetid: d8b43c4d-9dd5-4043-b4c8-38c03bfa0c72
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CCollations, CCollationInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CCollations** typedef para implementar la clase **CCollationInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica las intercalaciones de caracteres, definidas en el catálogo, que son accesibles a un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas INTERCALACIONES](https://msdn.microsoft.com/en-us/library/ms715783.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szCatalog|COLLATION\_CATALOG|  
|m\_szSchema|COLLATION\_SCHEMA|  
|m\_szName|COLLATION\_NAME|  
|m\_szCharSetCatalog|CHARACTER\_SET\_CATALOG|  
|m\_szCharSetSchema|CHARACTER\_SET\_SCHEMA|  
|m\_szCharSetName|CHARACTER\_SET\_NAME|  
|m\_szPadAttribute|PAD\_ATTRIBUTE|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)