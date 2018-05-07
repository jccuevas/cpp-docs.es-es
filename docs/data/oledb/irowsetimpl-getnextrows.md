---
title: 'IRowsetImpl:: GetNextRows | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
dev_langs:
- C++
helpviewer_keywords:
- GetNextRows method
ms.assetid: 1c0975d6-d770-4884-830b-6986c6fa8e65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c7106fa4f74ae087a76090b40f86e5c4e5fe947e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetimplgetnextrows"></a>IRowsetImpl::GetNextRows
Captura filas secuencialmente, teniendo en cuenta la posición anterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetNextRows )(HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowset:: GetNextRows](https://msdn.microsoft.com/en-us/library/ms709827.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (clase)](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl:: Addrefrows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)