---
title: CSchemata, CSchemataInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DEFAULT_CHARACTER_SET_CATALOG
- DEFAULT_CHARACTER_SET_SCHEMA
- m_szCharName
- CSchemataInfo
- m_szCatalog
- m_szCharCatalog
- m_szOwner
- m_szCharSchema
- CSchemata
- m_szName
- DEFAULT_CHARACTER_SET_NAME
dev_langs:
- C++
helpviewer_keywords:
- m_szCharName
- CSchemata typedef class
- DEFAULT_CHARACTER_SET_NAME
- m_szOwner
- CSchemataInfo parameter class
- DEFAULT_CHARACTER_SET_CATALOG
- m_szCharSchema
- m_szCatalog
- m_szName
- m_szCharCatalog
- DEFAULT_CHARACTER_SET_SCHEMA
ms.assetid: 9d06d65a-c27b-446d-bc42-c7e487b0d9c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c5bcd0477fe2285f5009aeb04c871f72c564365e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cschemata-cschematainfo"></a>CSchemata, CSchemataInfo
Llamar a la clase de typedef **CSchemata** para implementar su clase de parámetro **CSchemataInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica los esquemas que pertenecen a un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas de esquemas](https://msdn.microsoft.com/en-us/library/ms716887.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szCatalog|CATALOG_NAME|  
|m_szName|SCHEMA_NAME|  
|m_szOwner|SCHEMA_OWNER|  
|m_szCharCatalog|DEFAULT_CHARACTER_SET_CATALOG|  
|m_szCharSchema|DEFAULT_CHARACTER_SET_SCHEMA|  
|m_szCharName|DEFAULT_CHARACTER_SET_NAME|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)