---
title: 'IRowsetImpl:: M_rgrowhandles | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetImpl::m_rgRowHandles
- IRowsetImpl.m_rgRowHandles
- m_rgRowHandles
- ATL::IRowsetImpl::m_rgRowHandles
- ATL.IRowsetImpl.m_rgRowHandles
dev_langs:
- C++
helpviewer_keywords:
- m_rgRowHandles
ms.assetid: d3c2578f-58c4-4301-bf59-cf101a523a95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4eeeb9d048cd33513556d8b0585d1e84a0699a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101752"
---
# <a name="irowsetimplmrgrowhandles"></a>IRowsetImpl::m_rgRowHandles
Una asignación de identificadores de fila que contiene actualmente el proveedor en respuesta a `GetNextRows`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
MapClass  
 m_rgRowHandles;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Se quitan los identificadores de fila mediante una llamada a `ReleaseRows`. Consulte la [información general de IRowsetImpl](../../data/oledb/irowsetimpl-class.md) para la definición de *MapClass*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)