---
title: "CForeignKeys, CForeignKeysInfo | Microsoft Docs"
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
  - "m_szPKColumnName"
  - "FK_TABLE_NAME"
  - "m_guidFKColumn"
  - "FK_COLUMN_NAME"
  - "m_guidPKColumn"
  - "DELETE_RULE"
  - "m_szPKTableSchema"
  - "FK_COLUMN_PROPID"
  - "m_nFKColumnPropID"
  - "m_szFKTableCatalog"
  - "CForeignKeysInfo"
  - "FK_TABLE_SCHEMA"
  - "m_szPKTableCatalog"
  - "m_szDeleteRule"
  - "m_szUpdateRule"
  - "m_szPKTableName"
  - "m_szFKTableSchema"
  - "ORDINAL"
  - "m_nPKColumnPropID"
  - "m_szFKColumnName"
  - "FK_TABLE_CATALOG"
  - "FK_COLUMN_GUID"
  - "m_szFKTableName"
  - "CForeignKeys"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CForeignKeys (clase de definiciones de tipo)"
  - "CForeignKeysInfo (clase de parámetro)"
  - "DELETE_RULE"
  - "FK_COLUMN_GUID"
  - "FK_COLUMN_NAME"
  - "FK_COLUMN_PROPID"
  - "FK_TABLE_CATALOG"
  - "FK_TABLE_NAME"
  - "FK_TABLE_SCHEMA"
  - "m_guidFKColumn"
  - "m_guidPKColumn"
  - "m_nFKColumnPropID"
  - "m_nOrdinal"
  - "m_nPKColumnPropID"
  - "m_szDeleteRule"
  - "m_szFKColumnName"
  - "m_szFKTableCatalog"
  - "m_szFKTableName"
  - "m_szFKTableSchema"
  - "m_szPKColumnName"
  - "m_szPKTableCatalog"
  - "m_szPKTableName"
  - "m_szPKTableSchema"
  - "m_szUpdateRule"
  - "ORDINAL (miembro de datos)"
ms.assetid: 1c401a4a-0827-4255-9214-bc893e1cd79d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CForeignKeys, CForeignKeysInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Asigne a la clase **CForeignKeys** typedef para implementar la clase **CForeignKeysInfo**del parámetro.  
  
## Comentarios  
 Vea [Clases de conjunto de filas de esquema y clases de Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre cómo utilizar clases typedef.  
  
 Esta clase identifica las columnas de clave externa definidas en el catálogo por un usuario determinado.  
  
 La tabla siguiente se enumeran los miembros de datos de la clase y sus columnas correspondientes de OLE DB.  Vea [Conjunto de filas FOREIGN\_KEYS](https://msdn.microsoft.com/en-us/library/ms711276.aspx) en *la referencia del* programador para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|-----------------------|------------------------|  
|m\_szPKTableCatalog|PK\_TABLE\_CATALOG|  
|m\_szPKTableSchema|PK\_TABLE\_SCHEMA|  
|m\_szPKTableName|PK\_TABLE\_NAME|  
|m\_szPKColumnName|PK\_COLUMN\_NAME|  
|m\_guidPKColumn|PK\_COLUMN\_GUID|  
|m\_nPKColumnPropID|PK\_COLUMN\_PROPID|  
|m\_szFKTableCatalog|FK\_TABLE\_CATALOG|  
|m\_szFKTableSchema|FK\_TABLE\_SCHEMA|  
|m\_szFKTableName|FK\_TABLE\_NAME|  
|m\_szFKColumnName|FK\_COLUMN\_NAME|  
|m\_guidFKColumn|FK\_COLUMN\_GUID|  
|m\_nFKColumnPropID|FK\_COLUMN\_PROPID|  
|m\_nOrdinal|ORDINAL|  
|m\_szUpdateRule|UPDATE\_RULE|  
|m\_szDeleteRule|DELETE\_RULE|  
  
## Requisitos  
 **Header:** atldbsch.h  
  
## Vea también  
 [CRestrictions \(Clase\)](../../data/oledb/crestrictions-class.md)