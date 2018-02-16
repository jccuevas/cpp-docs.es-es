---
title: CDynamicAccessor::AddBindEntry | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicAccessor::AddBindEntry
- AddBindEntry
- CDynamicAccessor.AddBindEntry
- CDynamicAccessor::AddBindEntry
- ATL.CDynamicAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8f139376-7db3-4193-ba3b-63fe938ffa79
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f2c5a9efdc0ed13fa20b3ee0bd2cad74a8601f25
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessoraddbindentry"></a>CDynamicAccessor::AddBindEntry
Agrega una entrada de enlace a las columnas de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddBindEntry(const DBCOLUMNINFO& info) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `info`  
 [in] A **DBCOLUMNINFO** estructura que contiene información de columna. Vea "Estructuras DBCOLUMNINFO" en [IColumnsInfo:: GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 Utilice este método al reemplazar el descriptor de acceso predeterminado creado con `CDynamicAccessor` (consulte [¿cómo puedo recuperar datos?](../../data/oledb/fetching-data.md)).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)