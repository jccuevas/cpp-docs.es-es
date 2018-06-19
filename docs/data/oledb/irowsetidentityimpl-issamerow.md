---
title: 'Irowsetidentityimpl:: Issamerow | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IsSameRow
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
dev_langs:
- C++
helpviewer_keywords:
- IsSameRow method
ms.assetid: e35ad54e-73f1-4dc0-8d8c-9e98202baf0a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b7aa1c79cf9d65cefbbe2c1815f2a75c9bc21bbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102077"
---
# <a name="irowsetidentityimplissamerow"></a>IRowsetIdentityImpl::IsSameRow
Compara dos identificadores de fila para ver si hacen referencia a la misma fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(IsSameRow )(HROW hThisRow,  
   HROW hThatRow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetIdentity::IsSameRow](https://msdn.microsoft.com/en-us/library/ms719629.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Para comparar los identificadores de fila, este método convierte el **HROW** identificadores a **RowClass** los miembros y las llamadas `memcmp` en los punteros.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetIdentityImpl (Clase)](../../data/oledb/irowsetidentityimpl-class.md)