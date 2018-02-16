---
title: 'Igetdatasourceimpl:: GetDatasource | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- GetDataSource method
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7a41d6600fc48c530e79a7a2632752e35211becc
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="igetdatasourceimplgetdatasource"></a>IGetDataSourceImpl::GetDataSource
Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Resulta útil si necesita tener acceso a propiedades en el objeto de origen de datos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IGetDataSourceImpl (Clase)](../../data/oledb/igetdatasourceimpl-class.md)