---
title: CEnumeratorAccessor (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
dev_langs: C++
helpviewer_keywords: CEnumeratorAccessor class
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4a82b09a65cb4ebe6f0f796ba9aeb46ac5a2106a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor (Clase)
Utilizado por [CEnumerator](../../data/oledb/cenumerator-class.md) para tener acceso a los datos del conjunto de filas de enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CEnumeratorAccessor  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_bIsParent](../../data/oledb/cenumeratoraccessor-m-bisparent.md)|Una variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.|  
|[m_nType](../../data/oledb/cenumeratoraccessor-m-ntype.md)|Una variable que indica si la fila describe un origen de datos o un enumerador.|  
|[m_szDescription](../../data/oledb/cenumeratoraccessor-m-szdescription.md)|La descripción del origen de datos o enumerador.|  
|[m_szName](../../data/oledb/cenumeratoraccessor-m-szname.md)|El nombre del origen de datos o enumerador.|  
|[m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)|Cadena que se pasarán a [IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604) para obtener un moniker para el origen de datos o enumerador.|  
  
## <a name="remarks"></a>Comentarios  
 Este conjunto de filas se compone de los orígenes de datos y los enumeradores visibles desde el enumerador actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)