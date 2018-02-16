---
title: IRowsetLocateImpl::GetRowsByBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetLocateImpl::GetRowsByBookmark
- IRowsetLocateImpl.GetRowsByBookmark
- GetRowsByBookmark
dev_langs:
- C++
helpviewer_keywords:
- GetRowsByBookmark method
ms.assetid: 07906e42-3582-427e-812a-aa19791e3c56
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f76bbcbe13ccbdcb19a1ba8452804810066c9f5b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetlocateimplgetrowsbybookmark"></a>IRowsetLocateImpl::GetRowsByBookmark
Obtiene una o varias filas que coinciden con los marcadores especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetRowsByBookmark )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const DBBKMARK rgcbBookmarks[],  
   const BYTE* rgpBookmarks,  
   HROW rghRows[],  
   DBROWSTATUS* rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hReserved`  
 [in] Corresponde a `hChapter` parámetro [IRowsetLocate:: Getrowsbybookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx).  
  
 Para otros parámetros, vea [IRowsetLocate:: Getrowsbybookmark](https://msdn.microsoft.com/en-us/library/ms725420.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 El marcador puede ser un valor que defina u OLE DB [marcadores estándares](https://msdn.microsoft.com/en-us/library/ms712954.aspx) (**DBBMK_FIRST** o **DBBMK_LAST**). No cambia la posición del cursor.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetLocateImpl (clase)](../../data/oledb/irowsetlocateimpl-class.md)   
 [IRowsetLocateImpl::GetRowsAt](../../data/oledb/irowsetlocateimpl-getrowsat.md)