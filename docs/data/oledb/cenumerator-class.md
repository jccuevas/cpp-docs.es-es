---
title: CEnumerator (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b7e390212da53f85cb50dd5bb151ea6740784b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cenumerator-class"></a>CEnumerator (Clase)
Se usa un objeto de enumerador de OLE DB, que expone el [ISourcesRowset](https://msdn.microsoft.com/en-us/library/ms715969.aspx) interfaz para devolver un conjunto de filas que describe todos los orígenes de datos y los enumeradores.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Buscar](../../data/oledb/cenumerator-find.md)|Búsquedas a través de proveedores disponibles (orígenes de datos) buscando uno con el nombre especificado.|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|Recupera el `IMoniker` interfaz para el registro actual.|  
|[Abrir](../../data/oledb/cenumerator-open.md)|Se abre el enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Puede recuperar el **ISourcesRowset** datos indirectamente de esta clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [DBViewer](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)