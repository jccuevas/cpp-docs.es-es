---
title: IRowsetNotifyCP::Fire_OnRowChange | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
dev_langs:
- C++
helpviewer_keywords:
- Fire_OnRowChange method
ms.assetid: 6f9beed6-7a69-4c92-936f-422e98f3de5c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a1b957ebf13dce0b276955bd9f089b461677b556
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetnotifycpfireonrowchange"></a>IRowsetNotifyCP::Fire_OnRowChange
Difunde un [OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) eventos en todos los agentes de escucha en el punto de conexión **IID_IRowsetNotify** notificar a los consumidores de un cambio que afecta a las filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBREASON eReason,  
   DBEVENTPHASE ePhase,  
   BOOL fCantDeny);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetNotify::OnRowChange](https://msdn.microsoft.com/en-us/library/ms722694.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetNotifyCP (Clase)](../../data/oledb/irowsetnotifycp-class.md)