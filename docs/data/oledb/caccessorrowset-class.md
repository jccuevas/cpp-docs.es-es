---
title: CAccessorRowset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
dev_langs:
- C++
helpviewer_keywords:
- CAccessorRowset class
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0d64e69e663b27291c34e8b0c238b3967c71566c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="caccessorrowset-class"></a>CAccessorRowset (Clase)
Encapsula un conjunto de filas y sus descriptores de acceso asociados en una sola clase.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor, 
          template <typename T> class TRowset = CRowset>  
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
 `TRowset`  
 Una clase de conjunto de filas.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Bind](../../data/oledb/caccessorrowset-bind.md)|Crea enlaces (se usa cuando **bBind** se especifica como false en [CCommand:: Open](../../data/oledb/ccommand-open.md)).|  
|[CAccessorRowset](../../data/oledb/caccessorrowset-caccessorrowset.md)|Constructor.|  
|[Cerrar](../../data/oledb/caccessorrowset-close.md)|Cierra el conjunto de filas y los descriptores de acceso.|  
|[FreeRecordMemory](../../data/oledb/caccessorrowset-freerecordmemory.md)|Libera las columnas en el registro actual que deben ser liberados.|  
|[GetColumnInfo](../../data/oledb/caccessorrowset-getcolumninfo.md)|Implements [IColumnsInfo::GetColumnInfo](https://msdn.microsoft.com/en-us/library/ms722704.aspx).|  
  
## <a name="remarks"></a>Comentarios  
 Clase `TAccessor` administra el descriptor de acceso. Clase *TRowset* administra el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)