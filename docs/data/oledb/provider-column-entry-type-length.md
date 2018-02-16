---
title: PROVIDER_COLUMN_ENTRY_TYPE_LENGTH | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
ms.assetid: a60b1a8b-0903-4ff4-91ec-ed62126449fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f75dd0171d117259acd4a8f4956eb3be99412290
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="providercolumnentrytypelength"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
Representa una columna específica admitida por el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name  
, ordinal, dbtype, size, member )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
  
 [in] El nombre de columna.  
  
 `ordinal`  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 `dbtype`  
 [in] El tipo de datos en [DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx).  
  
 `size`  
 [in] El tamaño de columna en bytes.  
  
 `member`  
 [in] La variable de miembro de la clase de datos que almacena los datos.  
  
## <a name="remarks"></a>Comentarios  
 Similar a [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , pero también le permite especificar el tipo de datos de la columna, así como el tamaño.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)