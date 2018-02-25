---
title: 'IRowsetUpdateImpl:: Update | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
dev_langs:
- C++
helpviewer_keywords:
- Update method
ms.assetid: 9ec6884d-aa9c-4871-a803-c048f162403c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b398bcc4d522fdb682778de1088c60c5b3ac63f3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetupdateimplupdate"></a>IRowsetUpdateImpl::Update
Transmite los cambios realizados en la fila desde la última captura o de actualización.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hReserved`  
 [in] Corresponde a la `hChapter` parámetro en [IRowsetUpdate:: Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx).  
  
 Para otros parámetros, vea [IRowsetUpdate:: Update](https://msdn.microsoft.com/en-us/library/ms719709.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Cambios se transmiten mediante una llamada a [IRowsetChangeImpl:: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). El consumidor debe llamar a [CRowset:: Update](../../data/oledb/crowset-update.md) para que los cambios surtan efecto. Establecer *prgRowstatus* en un valor adecuado, tal como se describe en [Estados de fila](https://msdn.microsoft.com/en-us/library/ms722752.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)