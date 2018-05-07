---
title: 'IRowsetUpdateImpl:: GetOriginalData | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
dev_langs:
- C++
helpviewer_keywords:
- GetOriginalData method
ms.assetid: 7477b3b7-6b1b-49a7-8167-b34323f0fdcc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3684b9e1b7e6998d47b37d0d1a03fc08182c6a28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="irowsetupdateimplgetoriginaldata"></a>IRowsetUpdateImpl::GetOriginalData
Obtiene los datos transmitidos a más recientemente u obtenido del origen de datos, pasando por alto los cambios pendientes.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetUpdateImpl (Clase)](../../data/oledb/irowsetupdateimpl-class.md)