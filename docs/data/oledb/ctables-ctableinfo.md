---
title: CTables, CTableInfo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- m_szCatalog
- TABLE_SCHEMA
- CTables
- TABLE_NAME
- TABLE_CATALOG
- CTableInfo
- m_guidTable
- m_szType
- m_szSchema
- m_szName
- TABLE_GUID
dev_langs: C++
helpviewer_keywords:
- DESCRIPTION class data member
- m_szSchema
- TABLE_CATALOG
- m_szType
- m_szCatalog
- TABLE_NAME
- TABLE_SCHEMA
- TABLE_GUID
- m_szName
- m_szDescription
- CTables typedef class
- m_guidTable
- CTableInfo parameter class
ms.assetid: 57670f1b-ba99-43b0-b406-4c75b44f14f6
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6bb693d549420d0fac28e2952ea96789d8d23989
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ctables-ctableinfo"></a>CTables, CTableInfo
Llamar a la clase de typedef **CTables** para implementar su clase de parámetro **CTableInfo**.  
  
## <a name="remarks"></a>Comentarios  
 Vea [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) para obtener más información sobre el uso de clases typedef.  
  
 Esta clase identifica los privilegios en tablas definidas en el catálogo que están disponibles para o conceden a un usuario determinado.  
  
 En la tabla siguiente se enumera los miembros de datos de la clase y sus columnas OLE DB correspondiente. Vea [conjunto de filas TABLES](https://msdn.microsoft.com/en-us/library/ms716980.aspx) en el *referencia del programador de OLE DB* para obtener más información sobre el esquema y las columnas.  
  
|Miembros de datos|Columnas de OLE DB|  
|------------------|--------------------|  
|m_szCatalog|TABLE_CATALOG|  
|m_szSchema|TABLE_SCHEMA|  
|m_szName|TABLE_NAME|  
|m_szType|TABLE_TYPE|  
|m_guidTable|TABLE_GUID|  
|m_szDescription|DESCRIPCIÓN|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [CRestrictions (Clase)](../../data/oledb/crestrictions-class.md)