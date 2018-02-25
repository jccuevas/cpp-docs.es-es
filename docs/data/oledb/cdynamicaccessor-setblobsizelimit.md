---
title: CDynamicAccessor::SetBlobSizeLimit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicAccessor::SetBlobSizeLimit
- SetBlobSizeLimit
- CDynamicAccessor.SetBlobSizeLimit
- ATL.CDynamicAccessor.SetBlobSizeLimit
- ATL::CDynamicAccessor::SetBlobSizeLimit
dev_langs:
- C++
helpviewer_keywords:
- SetBlobSizeLimit method
ms.assetid: fb8cb85d-f841-408e-a344-37895b10993f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a2fac05c1380e2b612cb39994716387d99bef237
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicaccessorsetblobsizelimit"></a>CDynamicAccessor::SetBlobSizeLimit
Establece el tamaño máximo de BLOB en bytes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      void SetBlobSizeLimit(DBLENGTH nBlobSize);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nBlobSize`  
 Especifica el límite de tamaño BLOB.  
  
## <a name="remarks"></a>Comentarios  
 Establece el tamaño máximo de BLOB en bytes; datos de columna mayores que este valor se tratan como un BLOB. Algunos proveedores ofrecen un gran tamaño en columnas (por ejemplo, 2 GB). En lugar de intentar asignar memoria para una columna de este tamaño, se haría normalmente intenta enlazar estas columnas como BLOBs. En este modo no es necesario asignar toda la memoria, pero todavía puede leer todos los datos sin riesgo de truncamiento. Sin embargo, hay algunos casos en los que puede forzar `CDynamicAccessor` para enlazar las columnas de gran tamaño en sus tipos de datos nativos. Para ello, llame a `SetBlobSizeLimit` antes de llamar a **abiertos**.  
  
 El método de constructor [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) establece el tamaño máximo de BLOB en un valor predeterminado de 8.000 bytes.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)