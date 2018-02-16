---
title: CEnumerator (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CEnumerator
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f15ed0f0963987dab0c6170cc9a05bf4c28abdce
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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
|[Find](../../data/oledb/cenumerator-find.md)|Búsquedas a través de proveedores disponibles (orígenes de datos) buscando uno con el nombre especificado.|  
|[GetMoniker](../../data/oledb/cenumerator-getmoniker.md)|Recupera el `IMoniker` interfaz para el registro actual.|  
|[Abrir](../../data/oledb/cenumerator-open.md)|Se abre el enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Puede recuperar el **ISourcesRowset** datos indirectamente de esta clase.  
  
## <a name="requirements"></a>Requisitos  
 **Header:**atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [DBViewer](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)