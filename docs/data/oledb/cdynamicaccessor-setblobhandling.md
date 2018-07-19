---
title: 'CDynamicAccessor:: Setblobhandling | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobHandling
- CDynamicAccessor.SetBlobHandling
- ATL::CDynamicAccessor::SetBlobHandling
- SetBlobHandling
- ATL.CDynamicAccessor.SetBlobHandling
dev_langs:
- C++
helpviewer_keywords:
- SetBlobHandling method
ms.assetid: fa8b0bb3-a21b-4d64-aeef-e79bf61d079c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ee2c2d57f9f413346bb33a178fc3d8fa90439e1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095851"
---
# <a name="cdynamicaccessorsetblobhandling"></a>CDynamicAccessor::SetBlobHandling
Establece el BLOB de control de valor de la fila actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      bool SetBlobHandling(DBBLOBHANDLINGENUM eBlobHandling);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `eBlobHandling`  
 Especifica cómo se controlan los datos de BLOB. Puede tomar los siguientes valores:  
  
-   **DBBLOBHANDLING_DEFAULT**: administrar los datos de columna mayor que `nBlobSize` (tal como lo establece `SetBlobSizeLimit`) como datos de blobs y recuperarlo a través de un `ISequentialStream` o `IStream` objeto. Esta opción intentará enlazar cada columna que contiene datos superiores a `nBlobSize` o enumeradas como **DBTYPE_IUNKNOWN** como datos de BLOB.  
  
-   **DBBLOBHANDLING_NOSTREAMS**: administrar los datos de columna mayor que `nBlobSize` (tal como lo establece `SetBlobSizeLimit`) como datos de BLOB y recuperar a través de referencia en la memoria asignada por el proveedor, propia del consumidor. Esta opción es útil para las tablas que tienen más de una columna BLOB y el proveedor admite solo una `ISequentialStream` objeto cada descriptor de acceso.  
  
-   **DBBLOBHANDLING_SKIP**: Skip (no enlazar) las columnas que se califica como contenedor de BLOBs (el descriptor de acceso no enlazar o recuperar el valor de columna, pero todavía se recuperarán el estado de la columna y la longitud).  
  
## <a name="remarks"></a>Comentarios  
 Debe llamar a `SetBlobHandling` antes de llamar a **abiertos**.  
  
 El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el BLOB de control de valor a **DBBLOBHANDLING_DEFAULT**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)