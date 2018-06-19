---
title: COLUMN_ENTRY_TYPE_SIZE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1acb969015acda4213532cac3e185bf97a3ac31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097177"
---
# <a name="columnentrytypesize"></a>COLUMN_ENTRY_TYPE_SIZE
Representa un enlace a la columna concreta de la base de datos. Admite `type` y `size` parámetros.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nOrdinal`  
 [in] El número de columna.  
  
 `wType`  
 [in] Tipo de datos de entrada de la columna.  
  
 `nLength`  
 [in] Tamaño de entrada de la columna en bytes.  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro es una variante especializada de la [COLUMN_ENTRY](../../data/oledb/column-entry.md) macro que proporciona un medio para especificar el tamaño de los datos y el tipo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)