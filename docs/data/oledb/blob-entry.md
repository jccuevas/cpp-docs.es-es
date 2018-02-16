---
title: BLOB_ENTRY | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BLOB_ENTRY
dev_langs:
- C++
helpviewer_keywords:
- BLOB_ENTRY macro
ms.assetid: 89e40678-0869-49ed-b502-0fa2630a9081
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9ca27d4dffccdf644aec5f28d2523cebcd374f24
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="blobentry"></a>BLOB_ENTRY
Usar con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)  
  
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
  
## <a name="example"></a>Ejemplo  
 Vea [¿cómo puedo recuperar un objeto BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)   
 [BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)   
 [BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)