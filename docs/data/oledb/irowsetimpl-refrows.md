---
title: 'IRowsetImpl:: Refrows | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IRowsetImpl::RefRows
- ATL.IRowsetImpl.RefRows
- IRowsetImpl.RefRows
- RefRows
- IRowsetImpl::RefRows
dev_langs:
- C++
helpviewer_keywords:
- RefRows method
ms.assetid: 1c048a2a-65dc-4bba-9c81-a23c0dc249c8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c804d012029bd72d8c2837c17c74a2ece0e6848d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplrefrows"></a>IRowsetImpl::RefRows
Llamado por el método [AddRefRows](../../data/oledb/irowsetimpl-addrefrows.md) y [ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md) para incrementar o un recuento de referencias para un identificador de fila existente de la versión.  
  
## <a name="syntax"></a>Sintaxis  
  
```
HRESULT RefRows(DBCOUNTITEM cRows,  
   const HROWrghRows[],  
   DBREFCOUNT rgRefCounts[],  
   DBROWSTATUS rgRowStatus[],  
   BOOL bAdd);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (clase)](../../data/oledb/irowsetimpl-class.md)   
 [CSimpleRow (Clase)](../../data/oledb/csimplerow-class.md)