---
title: CIndexes, CIndexInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- INITIAL_SIZE
- NULL_COLLATION
- m_szFilterCondition
- m_bPrimaryKey
- m_szTableSchema
- m_bSortBookmarks
- m_szIndexSchema
- m_nColumnPropID
- ORDINAL_POSITION
- INDEX_CATALOG
- m_nOrdinalPosition
- COLUMN_GUID
- m_bAutoUpdate
- m_nNullCollation
- CLUSTERED
- NULLS
- m_szColumnName
- m_nFillFactor
- m_nPages
- INDEX_NAME
- m_szTableCatalog
- m_szIndexName
- m_szIndexCatalog
- m_nCardinality
- m_nInitialSize
- m_bUnique
- COLUMN_PROPID
- m_guidColumn
- m_nNulls
- m_szTableName
- FILL_FACTOR
- m_nType
- m_bClustered
- COLLATION
- FILTER_CONDITION
- m_nCollation
- CIndexes
- INDEX_SCHEMA
- CIndexInfo
dev_langs: C++
helpviewer_keywords:
- COLUMN_PROPID
- ORDINAL_POSITION
- INDEX_CATALOG
- NULLS
- CIndexInfo parameter class
- m_szFilterCondition
- m_szIndexCatalog
- CLUSTERED
- m_nType
- FILL_FACTOR
- m_nPages
- m_nCardinality
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- INDEX_SCHEMA
- m_nInitialSize
- m_nOrdinalPosition
- m_nColumnPropID
- FILTER_CONDITION
- TABLE_SCHEMA
- m_szColumnName
- INDEX_NAME
- NULL_COLLATION
- m_bUnique
- m_bSortBookmarks
- m_bAutoUpdate
- COLUMN_NAME
- INITIAL_SIZE
- m_szTableCatalog
- m_nNullCollation
- m_bClustered
- m_szTableName
- CIndexes typedef class
- m_nCollation
- COLUMN_GUID
- m_guidColumn
- m_nNulls
- m_bPrimaryKey
- m_szIndexName
- m_nFillFactor
- m_szIndexSchema
ms.assetid: 592fa773-fd23-4332-8d47-d76101f9ddd7
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c051e233c15959f71d57fa6eef1e398257b6d51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cindexes-cindexinfo"></a>CIndexes, CIndexInfo
Llamar a la clase de typedef **CIndexes** para implementar su clase de parámetro **CIndexInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica los índices definidos en el catálogo que pertenecen a un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas INDEXES](https://msdn.microsoft.com/en-us/library/ms709712.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szIndexCatalog|INDEX_CATALOG|  
|m_szIndexSchema|INDEX_SCHEMA|  
|m_szIndexName|INDEX_NAME|  
|m_bPrimaryKey|PRIMARY_KEY|  
|m_bUnique|UNIQUE|  
|m_bClustered|CLUSTERED|  
|m_nType|TYPE|  
|m_nFillFactor|FILL_FACTOR|  
|m_nInitialSize|INITIAL_SIZE|  
|m_nNulls|NULLS|  
|m_bSortBookmarks|SORT_BOOKMARKS|  
|m_bAutoUpdate|AUTO_UPDATE|  
|m_nNullCollation|NULL_COLLATION|  
|m_nOrdinalPosition|ORDINAL_POSITION|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nCollation|COLLATION|  
|m_nCardinality|CARDINALITY|  
|m_nPages|PAGES|  
|m_szFilterCondition|FILTER_CONDITION|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)