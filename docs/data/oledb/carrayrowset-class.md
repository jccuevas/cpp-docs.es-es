---
title: CArrayRowset (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
dev_langs:
- C++
helpviewer_keywords:
- CArrayRowset class
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 691776f39c54e843cec478c3c42871e7b7e81da1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="carrayrowset-class"></a>CArrayRowset (Clase)
Elementos de accesos de un conjunto de filas utilizando la sintaxis de la matriz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template < class TAccessor >  
class CArrayRowset :   
   public CVirtualBuffer <TAccessor>,   
   protected CBulkRowset <TAccessor>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 El tipo de clase de descriptor de acceso que desea que las filas que se va a usar.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CArrayRowset](../../data/oledb/carrayrowset-carrayrowset.md)|Constructor.|  
|[Instantánea](../../data/oledb/carrayrowset-snapshot.md)|Lee el conjunto de filas completo en la memoria.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[Operador&#91;&#93;](../../data/oledb/carrayrowset-operator.md)|Tiene acceso a un elemento del conjunto de filas.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[CArrayRowset::m_nRowsRead](../../data/oledb/carrayrowset-m-nrowsread.md)|El número de filas ya leídos.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CRowset (Clase)](../../data/oledb/crowset-class.md)