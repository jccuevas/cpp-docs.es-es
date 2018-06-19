---
title: 'IRowsetImpl:: M_breset | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a9aec38e3cf7e9a58c4fe99d06f35ae55cfdf81c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102012"
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