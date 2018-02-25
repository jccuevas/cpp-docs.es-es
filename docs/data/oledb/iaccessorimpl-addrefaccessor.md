---
title: 'IAccessorImpl:: Addrefaccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IAccessorImpl::AddRefAccessor
- AddRefAccessor
- IAccessorImpl::AddRefAccessor
- IAccessorImpl.AddRefAccessor
- ATL.IAccessorImpl.AddRefAccessor
dev_langs:
- C++
helpviewer_keywords:
- AddRefAccessor method
ms.assetid: 4c15392c-944b-4cbd-8cc7-2a5c2f308a70
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 74ae97d1e9397d401b7e2eaadecb9abcc61306ff
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="iaccessorimpladdrefaccessor"></a>IAccessorImpl::AddRefAccessor
Agrega un recuento de referencias a un descriptor de acceso existente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(AddRefAccessor)(HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IAccessor::AddRefAccessor](https://msdn.microsoft.com/en-us/library/ms714978.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IAccessorImpl (clase)](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)