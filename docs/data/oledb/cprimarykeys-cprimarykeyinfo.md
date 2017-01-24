---
title: "CPrimaryKeys, CPrimaryKeyInfo | Microsoft Docs"
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
  - "m_nOrdinal"
  - "m_szTableSchema"
  - "m_nColumnPropID"
  - "CPrimaryKeys"
  - "COLUMN_GUID"
  - "CPrimaryKeyInfo"
  - "m_szColumnName"
  - "m_szTableCatalog"
  - "COLUMN_PROPID"
  - "m_guidColumn"
  - "ORDINAL"
  - "m_szTableName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COLUMN_GUID"
  - "COLUMN_NAME"
  - "COLUMN_PROPID"
  - "CPrimaryKeyInfo (clase de parámetro)"
  - "CPrimaryKeys (clase de definiciones de tipo)"
  - "m_guidColumn"
  - "m_nColumnPropID"
  - "m_nOrdinal"
  - "m_szColumnName"
  - "m_szTableCatalog"
  - "m_szTableName"
  - "m_szTableSchema"
  - "ORDINAL (miembro de datos)"
  - "TABLE_CATALOG"
  - "TABLE_NAME"
  - "TABLE_SCHEMA"
ms.assetid: c27b97a4-a156-4f66-89e3-95f85d7d6281
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPrimaryKeys, CPrimaryKeyInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CPrimaryKeys** typedef para implementar la clase **CPrimaryKeyInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica las columnas de clave principal definida en el catálogo por un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas PRIMARY\_KEYS](https://msdn.microsoft.com/en-us/library/ms714362.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szTableCatalog|TABLE\_CATALOG|  
|m\_szTableSchema|TABLE\_SCHEMA|  
|m\_szTableName|TABLE\_NAME|  
|m\_szColumnName|COLUMN\_NAME|  
|m\_guidColumn|COLUMN\_GUID|  
|m\_nColumnPropID|COLUMN\_PROPID|  
|m\_nOrdinal|ORDINAL|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)