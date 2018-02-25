---
title: 'IRowsetUpdateImpl:: Getpendingrows | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
dev_langs:
- C++
helpviewer_keywords:
- GetPendingRows method
ms.assetid: 2d1ef748-da6d-4184-98dc-096427358dfd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a1086059facf686cca3bc876c78a44f298c1e4d3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplgetpendingrows"></a>IRowsetUpdateImpl::GetPendingRows
Devuelve una lista de filas con cambios pendientes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hReserved`  
 [in] Corresponde a la `hChapter` parámetro en [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx).  
  
 Para otros parámetros, vea [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IRowsetUpdate::GetPendingRows](https://msdn.microsoft.com/en-us/library/ms719626.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)