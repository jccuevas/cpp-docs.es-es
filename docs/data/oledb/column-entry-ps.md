---
title: COLUMN_ENTRY_PS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- COLUMN_ENTRY_PS
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_ENTRY_PS macro
ms.assetid: 563c12b0-3376-49d5-a14f-aa68d1e63a7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ceb72192856422218c9a059380a11cba93f4d972
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="columnentryps"></a>COLUMN_ENTRY_PS
Representa un enlace en el conjunto de filas a la columna específica en el conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en el *referencia del programador OLE DB*.  
  
 `nOrdinal`  
 [in] El número de columna.  
  
 `nPrecision`  
 [in] La precisión máxima de la columna que desea enlazar.  
  
 `nScale`  
 [in] La escala de la columna que desea enlazar.  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
## <a name="remarks"></a>Comentarios  
 Permite especificar la precisión y escala de la columna que desea enlazar. Se utiliza en los lugares siguientes:  
  
-   Entre los [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) y [END_COLUMN_MAP](../../data/oledb/end-column-map.md) macros.  
  
-   Entre los [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros.  
  
-   Entre los [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) y [END_PARAM_MAP](../../data/oledb/end-param-map.md) macros.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)   
 [COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)   
 [COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)   
 [COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)   
 [COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)   
 [COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)   
 [COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)   
 [END_ACCESSOR](../../data/oledb/end-accessor.md)   
 [END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)