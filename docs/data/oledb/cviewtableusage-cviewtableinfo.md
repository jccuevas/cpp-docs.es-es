---
title: CViewTableUsage, CViewTableInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- m_szTableSchema
- m_szCatalog
- CViewTableInfo
- m_szTableCatalog
- m_szSchema
- m_szTableName
- m_szName
- CViewTableUsage
dev_langs:
- C++
helpviewer_keywords:
- CViewTableInfo parameter class
- CViewTableUsage typedef class
- m_szSchema
- m_szTableSchema
- TABLE_CATALOG
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- m_szName
- m_szTableCatalog
- m_szTableName
ms.assetid: 10b74f2a-8010-4f97-acc2-ffce07349981
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b66c159e2825884ef59fbfb278b5eddd99d38c0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cviewtableusage-cviewtableinfo"></a>CViewTableUsage, CViewTableInfo
Llamar a la clase de typedef **CViewTableUsage** para implementar su clase de parámetro **CViewTableInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica las tablas vistas, definidas en el catálogo, que son accesibles para un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas VIEW_TABLE_USAGE](https://msdn.microsoft.com/en-us/library/ms719727.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szCatalog|VIEW_CATALOG|  
|m_szSchema|VIEW_SCHEMA|  
|m_szName|VIEW_NAME|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)