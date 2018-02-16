---
title: PROVIDER_COLUMN_ENTRY_FIXED | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_FIXED macro
ms.assetid: 71f9c9aa-56a0-488b-96ba-5c72da9c71d0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f374f5e7d4a2dfd24cdd3b2067b0bda935ce438f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentryfixed"></a>PROVIDER_COLUMN_ENTRY_FIXED
Representa una columna específica admitida por el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name  
, ordinal, dbtype, member )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 `ordinal`  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 `dbtype`  
 [in] El tipo de datos en [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `member`  
 [in] La variable de miembro en `dataClass` que almacena los datos.  
  
## <a name="remarks"></a>Comentarios  
 Permite especificar el tipo de datos de columna.  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)