---
title: CAccessorBase (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccessorBase
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 030e06c40912a6b32c076b86f4a7456177b4ce93
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="caccessorbase-class"></a>CAccessorBase (Clase)
Todos los descriptores de acceso en las plantillas OLE DB se derivan de esta clase. `CAccessorBase` permite que un conjunto de filas administrar varios descriptores de acceso. También proporciona enlace de parámetros y columnas de salida.  
  
## <a name="syntax"></a>Sintaxis

```cpp
// Replace with syntax  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Cerrar](../../data/oledb/caccessorbase-close.md)|Cierra los descriptores de acceso.|  
|[GetHAccessor](../../data/oledb/caccessorbase-gethaccessor.md)|Recupera el identificador de descriptor de acceso.|  
|[GetNumAccessors](../../data/oledb/caccessorbase-getnumaccessors.md)|Recupera el número de descriptores de acceso creado por la clase.|  
|[IsAutoAccessor](../../data/oledb/caccessorbase-isautoaccessor.md)|Comprueba si el descriptor de acceso especificada es autoaccessor.|  
|[ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md)|Libera los descriptores de acceso.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)