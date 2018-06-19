---
title: 'IRowsetCreatorImpl:: SetSite | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: af2883b261b754cee04e2c5090d1ef9b9887c04f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101389"
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