---
title: BLOB_NAME | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BLOB_NAME
dev_langs:
- C++
helpviewer_keywords:
- BLOB_NAME macro
ms.assetid: 757acd0d-946d-447d-937e-94ecd700ba38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 488c2f9cc2570ea5b512d0cf245902793d408dc5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="blobname"></a>BLOB_NAME
Usar con `BEGIN_COLUMN_MAP` y `END_COLUMN_MAP` para enlazar un objeto binario grande ([BLOB](https://msdn.microsoft.com/en-us/library/ms711511.aspx)). Similar a [BLOB_ENTRY](../../data/oledb/blob-entry.md), salvo que esta macro toma un nombre de columna en lugar de un número de columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BLOB_NAME(pszName, IID, flags, data )  
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
  
## <a name="example"></a>Ejemplo  
 Vea [¿cómo puedo recuperar un objeto BLOB?](../../data/oledb/retrieving-a-blob.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)   
 [BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)   
 [BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)