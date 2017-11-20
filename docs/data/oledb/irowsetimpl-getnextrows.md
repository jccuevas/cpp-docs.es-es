---
title: 'IRowsetImpl:: GetNextRows | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetNextRows
- ATL.IRowsetImpl.GetNextRows
- ATL::IRowsetImpl::GetNextRows
- IRowsetImpl::GetNextRows
- IRowsetImpl.GetNextRows
dev_langs: C++
helpviewer_keywords: GetNextRows method
ms.assetid: 1c0975d6-d770-4884-830b-6986c6fa8e65
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6876cd59a36177ce89a196d6fe0ae403d16bfa68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="irowsetimplgetnextrows"></a>IRowsetImpl::GetNextRows
Captura filas secuencialmente, teniendo en cuenta la posición anterior.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      STDMETHOD( GetNextRows )(  
   HCHAPTER hReserved,  
   DBROWOFFSET lRowsOffset,  
   DBROWCOUNT cRows,  
   DBCOUNTITEM* pcRowsObtained,  
   HROW** prghRows   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowset:: GetNextRows](https://msdn.microsoft.com/en-us/library/ms709827.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (clase)](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl:: Addrefrows](../../data/oledb/irowsetimpl-addrefrows.md)   
 [IRowsetImpl::ReleaseRows](../../data/oledb/irowsetimpl-releaserows.md)