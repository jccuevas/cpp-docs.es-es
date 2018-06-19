---
title: COLUMN_ENTRY_TYPE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE macro
ms.assetid: ac424261-ff6c-443b-a197-2cec8d78d738
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b297b641913c59c95cd54fdb4e5e02a293dbf71e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091549"
---
# <a name="columnentrytype"></a>COLUMN_ENTRY_TYPE
Representa un enlace a la columna concreta de la base de datos. Admite `type` parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nOrdinal`  
 [in] El número de columna.  
  
 `wType`  
 [in] Tipo de datos de entrada de la columna.  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro es una variante especializada de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro que proporciona un medio para especificar el tipo de datos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)