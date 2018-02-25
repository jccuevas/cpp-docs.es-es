---
title: IRowsetImpl::m_bReset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.m_bReset
- IRowsetImpl.m_bReset
- m_bReset
- IRowsetImpl::m_bReset
- ATL::IRowsetImpl::m_bReset
dev_langs:
- C++
helpviewer_keywords:
- m_bReset
ms.assetid: d423f9f3-4d48-4d0c-b152-684c81a0b34e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3605c23ab14cb769ede5a1aec263beb957e1666f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplmbreset"></a>IRowsetImpl::m_bReset
Un indicador de bits que se usa para determinar si la posición del cursor se define en el conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
unsigned m_bReset:1;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Si el consumidor llama [GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md) con negativo `lOffset` o *cRows* y `m_bReset` es true, `GetNextRows` se desplaza hasta el final del conjunto de filas. Si `m_bReset` es false, el consumidor recibe un código de error, de acuerdo con la especificación de OLE DB. El `m_bReset` marca queda establecida en **true** cuando se crea por primera vez el conjunto de filas y cuando el consumidor llama [IRowsetImpl:: RestartPosition](../../data/oledb/irowsetimpl-restartposition.md). Obtiene el conjunto **false** cuando se llama a `GetNextRows`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)