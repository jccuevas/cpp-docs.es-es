---
title: IRowsetCreatorImpl::SetSite | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IRowsetCreatorImpl.SetSite
- IRowsetCreatorImpl<T>::SetSite
- IRowsetCreatorImpl::SetSite
- SetSite
- ATL.IRowsetCreatorImpl.SetSite
- ATL::IRowsetCreatorImpl<T>::SetSite
- ATL::IRowsetCreatorImpl::SetSite
- ATL.IRowsetCreatorImpl<T>.SetSite
dev_langs:
- C++
helpviewer_keywords:
- SetSite method
ms.assetid: e92e63d5-93e4-4ee0-9ef7-bb6583cc8091
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 57d5a2027203c912ff004d7f4dcce0d23724b233
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetcreatorimplsetsite"></a>IRowsetCreatorImpl::SetSite
Establece el sitio que contiene el objeto de conjunto de filas. Para obtener más información, consulte [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(SetSite )(IUnknown* pCreator);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCreator`  
 [in] Puntero a la **IUnknown** puntero de interfaz del sitio administrando el objeto de conjunto de filas.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Además, `IRowsetCreatorImpl::SetSite` permite OLE DB **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS** propiedades.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetCreatorImpl (Clase)](../../data/oledb/irowsetcreatorimpl-class.md)