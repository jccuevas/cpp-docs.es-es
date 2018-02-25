---
title: CTable (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CTable
- ATL.CTable
- CTable
dev_langs:
- C++
helpviewer_keywords:
- CTable class
ms.assetid: f13fdaa3-e198-4557-977d-54b0bbc3454d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c8bf7bb8daa33a69dfbc6a3de41171004244cbd5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ctable-class"></a>CTable (Clase)
Proporciona un medio para tener acceso directamente a un conjunto de filas simple (uno sin parámetros).  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor, 
            template <typename T> class TRowset = CRowset>  
class CTable :  
   public CAccessorRowset <TAccessor, TRowset>  
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
|[Abrir](../../data/oledb/ctable-open.md)|Se abre la tabla.|  
  
## <a name="remarks"></a>Comentarios  
 Vea [CCommand](../../data/oledb/ccommand-class.md) para obtener información sobre cómo ejecutar un comando para tener acceso a un conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [IOpenRowset::OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx)