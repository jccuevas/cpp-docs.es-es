---
title: BLOB_NAME_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_NAME_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME_STATUS macro
ms.assetid: 4564e4a0-8e5e-436a-bd1e-012d2a1b8642
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4d55e65872a2939a8aa252f0a839ed41570bbcd4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="blobnamestatus"></a>BLOB_NAME_STATUS
Usar con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Similar a [BLOB_NAME](../../data/oledb/blob-name.md), salvo que esta macro también obtiene el estado de la columna de datos BLOB.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data  
, status )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszName`  
 [in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando un 'L' delante del nombre, por ejemplo: `L"MyColumn"`.  
  
 *IID*  
 [in] Interfaz GUID, como **IDD_ISequentialStream**, que se usa para recuperar el BLOB.  
  
 `flags`  
 [in] Marcas de modo de almacenamiento tal como se define por el modelo de almacenamiento estructurado OLE (por ejemplo, **STGM_READ**).  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
 *status*  
 [out] El estado del campo BLOB.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME](../../data/oledb/blob-name.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)