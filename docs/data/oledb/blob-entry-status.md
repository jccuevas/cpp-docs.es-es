---
title: BLOB_ENTRY_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BLOB_ENTRY_STATUS
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY_STATUS macro
ms.assetid: 191007f4-dfcc-4ae2-a7fc-6f7899accc9f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 207f42094ea62db103fb39a0057f595182a2ec9a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="blobentrystatus"></a>BLOB_ENTRY_STATUS
Usar con `BEGIN_COLUMN_MAP` o `BEGIN_ACCESSOR_MAP` para enlazar un objeto binario grande ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro también obtiene el estado de la columna BLOB.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nOrdinal`  
 [in] El número de columna.  
  
 *IID*  
 [in] Interfaz GUID, como **IDD_ISequentialStream**, que se usa para recuperar el BLOB.  
  
 `flags`  
 [in] Marcas de modo de almacenamiento tal como se define por el modelo de almacenamiento estructurado OLE (por ejemplo, **STGM_READ**).  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
 *status*  
 [out] El estado del campo BLOB.  
  
## <a name="example"></a>Ejemplo  
 Vea [¿cómo puedo recuperar un objeto BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY](../../data/oledb/blob-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)