---
title: BEGIN_SCHEMA_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_SCHEMA_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_SCHEMA_MAP macro
ms.assetid: 4e751023-35bc-4efd-9018-5448dd1ad751
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4ad46968919dec9500a826a4bbc5addfdea326a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="beginschemamap"></a>BEGIN_SCHEMA_MAP
Indica el principio de una asignación de esquema.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *SchemaClass*  
 La clase que contiene el mapa. Normalmente se trata de la clase de sesión.  
  
## <a name="remarks"></a>Comentarios  
 Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el SDK de Windows para obtener más información sobre conjuntos de filas de esquema.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [SCHEMA_ENTRY](../../data/oledb/schema-entry.md)   
 [END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)   
 [IDBSchemaRowsetImpl (Clase)](../../data/oledb/idbschemarowsetimpl-class.md)