---
title: PROVIDER_COLUMN_ENTRY_GN | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- PROVIDER_COLUMN_ENTRY_GN
dev_langs:
- C++
helpviewer_keywords:
- PROVIDER_COLUMN_ENTRY_GN macro
ms.assetid: be77ba85-634c-4e28-832f-d2fa40413254
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ff73cda1e676387b4f8ca79ce1ef7cbf8fce13e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="providercolumnentrygn"></a>PROVIDER_COLUMN_ENTRY_GN
Representa una columna específica admitida por el proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name  
, ordinal, flags, colSize, dbtype, precision, scale, guid )  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 `ordinal`  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 `flags`  
 [in] Especifica cómo se devuelven los datos. Consulte la `dwFlags` descripción en [estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *colSize*  
 [in] El tamaño de la columna.  
  
 `dbtype`  
 [in] Indica el tipo de datos del valor. Consulte la **wType** descripción en [estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 *precision*  
 [in] Indica la precisión que se utilizará al obtener los datos si *dbType* es `DBTYPE_NUMERIC` o **DBTYPE_DECIMAL**. Consulte la **bPrecision** descripción en [estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `scale`  
 [in] Indica la escala que se utilizará al obtener los datos si dbType es `DBTYPE_NUMERIC` o **DBTYPE_DECIMAL**. Consulte la **bScale** descripción en [estructuras DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx).  
  
 `guid`  
 Un conjunto de filas de esquema GUID. Vea [IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx) en el *referencia del programador de OLE DB* para obtener una lista de conjuntos de filas de esquema y sus GUID.  
  
## <a name="remarks"></a>Comentarios  
 Permite especificar el tamaño de la columna, tipo de datos, precisión, escala y GUID del conjunto de filas de esquema.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)