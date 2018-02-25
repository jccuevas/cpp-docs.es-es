---
title: COLUMN_ENTRY_TYPE_SIZE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COLUMN_ENTRY_TYPE_SIZE
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_TYPE_SIZE macro
ms.assetid: d8b169e8-af22-464b-8cb3-eaa346f7a739
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cec18aa88ea5d34589e69e41b4a08136d6edf525
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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