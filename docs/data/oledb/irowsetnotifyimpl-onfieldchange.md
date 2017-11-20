---
title: 'IRowsetNotifyImpl:: Onfieldchange | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyImpl.OnFieldChange
- IRowsetNotifyImpl::OnFieldChange
- OnFieldChange
dev_langs: C++
helpviewer_keywords: OnFieldChange method
ms.assetid: f26b492c-c86e-423b-9374-175e510a2860
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f6816ca96d3fe00e48d0fdca7b560eb628150d4d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetnotifyimplonfieldchange"></a>IRowsetNotifyImpl::OnFieldChange
Notifica al consumidor de cualquier cambio en el valor de una columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
STDMETHOD(OnFieldChange)(   
/* [in] */ IRowset* /* pRowset */,  
/* [in] */ HROW /* hRow */,  
/* [in] */ DBORDINAL /* cColumns */,  
/* [size_is][in] */ DBORDINAL /* rgColumns */ [] ,  
/* [in] */ DBREASON /* eReason */,  
/* [in] */ DBEVENTPHASE /* ePhase */,  
/* [in] */ BOOL /* fCantDeny */)  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) para descripciones de parámetros.  
  
## <a name="return-value"></a>Valor devuelto  
 Vea [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) para descripciones de los valores de retorno.  
  
## <a name="remarks"></a>Comentarios  
 Este método ajusta el [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx) método. Consulte la descripción de ese método en la referencia del programador de OLE DB para obtener más información.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetNotifyImpl (clase)](../../data/oledb/irowsetnotifyimpl-class.md)   
 [IRowsetNotify::OnFieldChange](https://msdn.microsoft.com/en-us/library/ms715961.aspx)