---
title: CConstraintColumnUsage, CConstraintColumnUsageInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- m_szConstraintCatalog
- CConstraintColumnUsage
- m_nColumnPropID
- COLUMN_GUID
- CONSTRAINT_NAME
- m_szColumnName
- m_szTableCatalog
- m_szConstraintSchema
- COLUMN_PROPID
- m_guidColumn
- CONSTRAINT_COLUMN_USAGE
- m_szTableName
- CONSTRAINT_CATALOG
- CONSTRAINT_SCHEMA
- CConstraintColumnUsageInfo
- m_szConstraintName
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_PROPID
- m_szConstraintCatalog
- CONSTRAINT_COLUMN_USAGE
- CONSTRAINT_CATALOG
- CConstraintColumnUsageInfo parameter class
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- CONSTRAINT_NAME
- CConstraintColumnUsage typedef class
- m_nColumnPropID
- CONSTRAINT_SCHEMA
- TABLE_SCHEMA
- m_szColumnName
- COLUMN_NAME
- m_szTableCatalog
- m_szConstraintName
- m_szTableName
- m_szConstraintSchema
- COLUMN_GUID
- m_guidColumn
ms.assetid: 7d4d94e8-2025-4fcc-a176-c9b231eca77b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6db36b0f710b0c12fba1c53e7c9fe09bcc89cd45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095390"
---
# <a name="cconstraintcolumnusage-cconstraintcolumnusageinfo"></a>CConstraintColumnUsage, CConstraintColumnUsageInfo
Llamar a la clase de typedef **CConstraintColumnUsage** para implementar su clase de parámetro **CConstraintColumnUsageInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica las columnas utilizadas por las restricciones referenciales, restricciones únicas, restricciones check y aserciones, definidas en el catálogo y pertenecen a un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [filas CONSTRAINT_COLUMN_USAGE](https://msdn.microsoft.com/en-us/library/ms724522.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_szColumnName|COLUMN_NAME|  
|m_guidColumn|COLUMN_GUID|  
|m_nColumnPropID|COLUMN_PROPID|  
|m_szConstraintCatalog|CONSTRAINT_CATALOG|  
|m_szConstraintSchema|CONSTRAINT_SCHEMA|  
|m_szConstraintName|CONSTRAINT_NAME|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)