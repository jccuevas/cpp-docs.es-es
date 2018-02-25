---
title: CPrimaryKeys, CPrimaryKeyInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- m_nOrdinal
- m_szTableSchema
- m_nColumnPropID
- CPrimaryKeys
- COLUMN_GUID
- CPrimaryKeyInfo
- m_szColumnName
- m_szTableCatalog
- COLUMN_PROPID
- m_guidColumn
- ORDINAL
- m_szTableName
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_PROPID
- m_szTableSchema
- TABLE_CATALOG
- ORDINAL data member
- CPrimaryKeys typedef class
- TABLE_NAME
- m_nColumnPropID
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szTableCatalog
- m_szTableName
- m_nOrdinal
- CPrimaryKeyInfo parameter class
- COLUMN_GUID
- m_guidColumn
ms.assetid: c27b97a4-a156-4f66-89e3-95f85d7d6281
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a7c4be146df38e0dd55a09005af27deef175318c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cprimarykeys-cprimarykeyinfo"></a>CPrimaryKeys, CPrimaryKeyInfo
Llamar a la clase de typedef **CPrimaryKeys** para implementar su clase de parámetro **CPrimaryKeyInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica las columnas de clave principal definidas en el catálogo por un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas PRIMARY_KEYS](https://msdn.microsoft.com/en-us/library/ms714362.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_nOrdinal|ORDINAL|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)