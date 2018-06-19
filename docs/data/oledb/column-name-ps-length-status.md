---
title: COLUMN_NAME_PS_LENGTH_STATUS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_PS_LENGTH_STATUS macro
ms.assetid: a1a2e2ca-f0ae-4896-8aa3-67a96c270b05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 033b04c98ba7f7cee56cd6ecc235a0679a62754d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091335"
---
# <a name="columnnamepslengthstatus"></a>COLUMN_NAME_PS_LENGTH_STATUS
Representa un enlace en el conjunto de filas a la columna específica en el conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también usa la precisión, escala, longitud de la columna y estado de la columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszName`  
 [in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando un 'L' delante del nombre, por ejemplo: `L"MyColumn"`.  
  
 `nPrecision`  
 [in] La precisión máxima de la columna que desea enlazar.  
  
 `nScale`  
 [in] La escala de la columna que desea enlazar.  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
 *length*  
 [in] La variable se puede enlazar a la longitud de columna.  
  
 *status*  
 [in] La variable esté enlazado con el estado de la columna.  
  
## <a name="remarks"></a>Comentarios  
 Vea [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde el **COLUMN_NAME_\***  se utilizan macros.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)