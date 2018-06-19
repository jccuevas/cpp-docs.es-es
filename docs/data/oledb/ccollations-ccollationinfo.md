---
title: CCollations, CCollationInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLLATION_CATALOG
- m_szCatalog
- CCollationInfo
- CCollations
- CHARACTER_SET_NAME
- CHARACTER_SET_SCHEMA
- m_szCharSetName
- m_szSchema
- CHARACTER_SET_CATALOG
- m_szCharSetSchema
- m_szCharSetCatalog
- m_szPadAttribute
- COLLATION_NAME
- COLLATION_SCHEMA
- m_szName
- COLLATIONS
dev_langs:
- C++
helpviewer_keywords:
- m_szSchema
- COLLATION_SCHEMA
- m_szCharSetCatalog
- m_szCatalog
- COLLATIONS recordset
- COLLATION_CATALOG
- CCollationInfo parameter class
- m_szName
- COLLATION_NAME
- m_szPadAttribute
- CHARACTER_SET_NAME
- m_szCharSetName
- CHARACTER_SET_SCHEMA
- CHARACTER_SET_CATALOG
- m_szCharSetSchema
- CCollations typedef class
ms.assetid: d8b43c4d-9dd5-4043-b4c8-38c03bfa0c72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c9a7713df0a3b6cb92f79fde8faa42a15a7a40f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090466"
---
# <a name="ccollations-ccollationinfo"></a>CCollations, CCollationInfo
Llamar a la clase de typedef **CCollations** para implementar su clase de parámetro **CCollationInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica las intercalaciones de caracteres definidas en el catálogo, que son accesibles para un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas COLLATIONS](https://msdn.microsoft.com/en-us/library/ms715783.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szCatalog|COLLATION_CATALOG|  
|m_szSchema|COLLATION_SCHEMA|  
|m_szName|COLLATION_NAME|  
|m_szCharSetCatalog|CHARACTER_SET_CATALOG|  
|m_szCharSetSchema|CHARACTER_SET_SCHEMA|  
|m_szCharSetName|CHARACTER_SET_NAME|  
|m_szPadAttribute|PAD_ATTRIBUTE|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)