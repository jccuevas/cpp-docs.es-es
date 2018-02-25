---
title: PROVIDER_COLUMN_ENTRY_WSTR | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_WSTR macro
ms.assetid: 70630bd5-d782-473b-9777-aebbbf5321c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dd0f87bad4fbd758849e33ae18cdcfd6a8e72357
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="providercolumnentrywstr"></a>PROVIDER_COLUMN_ENTRY_WSTR
Representa una columna específica admitida por el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name  
, ordinal, member )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 `ordinal`  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 `member`  
 [in] La variable de miembro de la clase de datos que almacena los datos.  
  
## <a name="remarks"></a>Comentarios  
 Use esta macro cuando los datos de columna están la cadena de caracteres Unicode terminada en null [DBTYPE_WSTR](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)