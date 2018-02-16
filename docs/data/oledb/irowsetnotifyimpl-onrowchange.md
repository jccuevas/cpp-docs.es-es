---
title: 'IRowsetNotifyImpl:: Onrowchange | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyImpl::OnRowChange
- IRowsetNotifyImpl.OnRowChange
- OnRowChange
dev_langs:
- C++
helpviewer_keywords:
- OnRowChange method
ms.assetid: 148bee03-3707-4bbf-8c51-657efc63645f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cd965dc1f16be25ee4ab9ea5a6f2cbcf185952c1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifyimplonrowchange"></a>IRowsetNotifyImpl::OnRowChange
Notifica al consumidor del primer cambio en una fila o de cualquier cambio que afecta a toda la fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(OnRowChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ DBCOUNTITEM /* cRows */,  
/* [size_is][in] */ const HROW /* rghRows*/ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) para descripciones de parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) para descripciones de los valores de retorno.  
  
## <a name="remarks"></a>Comentarios  
 Este método ajusta el [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) método. Consulte la descripción de ese método en la referencia del programador de OLE DB para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetNotifyImpl (clase)](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx)