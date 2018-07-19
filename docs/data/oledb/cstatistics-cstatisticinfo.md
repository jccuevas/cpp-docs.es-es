---
title: CStatistics, CStatisticInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CStatistics
- m_szTableSchema
- CStatisticInfo
- m_szTableCatalog
- m_nCardinality
- m_szTableName
dev_langs:
- C++
helpviewer_keywords:
- m_nCardinality
- m_szTableSchema
- TABLE_CATALOG
- TABLE_NAME
- TABLE_SCHEMA
- CStatistics typedef class
- m_szTableCatalog
- m_szTableName
- CStatisticInfo parameter class
ms.assetid: 5822231c-6963-44a6-ae2f-29aca76e1600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ad61624077eb1c02337fdd4737853522533a8a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101502"
---
# <a name="cstatistics-cstatisticinfo"></a>CStatistics, CStatisticInfo
Llamar a la clase de typedef **CStatistics** para implementar su clase de parámetro **CStatisticInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica las estadísticas definidas en el catálogo que pertenecen a un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas de las estadísticas](https://msdn.microsoft.com/en-us/library/ms715957.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szTableCatalog|TABLE_CATALOG|  
|m_szTableSchema|TABLE_SCHEMA|  
|m_szTableName|TABLE_NAME|  
|m_nCardinality|CARDINALITY|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)