---
title: CAccessorBase (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorBase
dev_langs:
- C++
helpviewer_keywords:
- CAccessorBase class
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f598f49d279085b23e0bd3b94c48620363b5a816
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090801"
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