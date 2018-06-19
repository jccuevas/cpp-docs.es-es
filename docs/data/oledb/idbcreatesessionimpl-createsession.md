---
title: 'Idbcreatesessionimpl:: CreateSession | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateSessionImpl::CreateSession
- IDBCreateSessionImpl.CreateSession
- CreateSession
dev_langs:
- C++
helpviewer_keywords:
- CreateSession method
ms.assetid: 035e5ddb-56e6-43b1-874d-89c0e40b103b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fe8117d77ae82e4287e7ed4a81a07569848c213b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33099204"
---
# <a name="idbcreatesessionimplcreatesession"></a>IDBCreateSessionImpl::CreateSession
Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(CreateSession)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppDBSession);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IDBCreateSession::](https://msdn.microsoft.com/en-us/library/ms714942.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBCreateSessionImpl (Clase)](../../data/oledb/idbcreatesessionimpl-class.md)