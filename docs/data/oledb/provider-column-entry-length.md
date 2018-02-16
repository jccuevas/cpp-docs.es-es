---
title: PROVIDER_COLUMN_ENTRY_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_LENGTH macro
ms.assetid: b4a67246-c049-4622-bb65-242cc8cae4be
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb42c78d5e90e56f2186145621d064671f40fef5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentrylength"></a>PROVIDER_COLUMN_ENTRY_LENGTH
Representa una columna específica admitida por el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name  
, ordinal, size, member )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 `ordinal`  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 `size`  
 [in] El tamaño de columna en bytes.  
  
 `member`  
 [in] La variable de miembro en `dataClass` que almacena los datos de columna.  
  
## <a name="remarks"></a>Comentarios  
 Permite especificar el tamaño de columna.  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)