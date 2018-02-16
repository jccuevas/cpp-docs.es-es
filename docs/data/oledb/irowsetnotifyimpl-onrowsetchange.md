---
title: 'IRowsetNotifyImpl:: Onrowsetchange | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnRowsetChange
- IRowsetNotifyImpl::OnRowsetChange
- IRowsetNotifyImpl.OnRowsetChange
dev_langs:
- C++
helpviewer_keywords:
- OnRowsetChange method
ms.assetid: 5125b0c8-f175-4ee6-befa-8df2c904d5e0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 01cdef46ad1bb74041e8cfee3e2dff7fd01cc4ef
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifyimplonrowsetchange"></a>IRowsetNotifyImpl::OnRowsetChange
Notifica al consumidor de cualquier cambio que afecte a todo el conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
   STDMETHOD(OnRowsetChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) para descripciones de parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Vea [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) para descripciones de los valores de retorno.  
  
## <a name="remarks"></a>Comentarios  
 Este método ajusta el [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx) método. Consulte la descripción de ese método en la referencia del programador de OLE DB para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetNotifyImpl (clase)](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowsetChange](https://msdn.microsoft.com/en-us/library/ms722669.aspx)