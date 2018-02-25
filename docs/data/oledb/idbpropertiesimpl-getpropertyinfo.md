---
title: IDBPropertiesImpl::GetPropertyInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
dev_langs:
- C++
helpviewer_keywords:
- GetPropertyInfo method
ms.assetid: 170e9640-5010-4e0d-8a54-f50b23af08ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa96d49ae5a0ac01d90d6f6c5a0efe020d7a5a3e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="idbpropertiesimplgetpropertyinfo"></a>IDBPropertiesImpl::GetPropertyInfo
Devuelve información sobre las propiedades compatible con el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IDBProperties:: GetPropertyInfo](https://msdn.microsoft.com/en-us/library/ms718175.aspx) en el *referencia del programador OLE DB*.  
  
 Algunos parámetros corresponden a *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en **IDBProperties:: GetPropertyInfo**:  
  
|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
  
## <a name="remarks"></a>Comentarios  
 Usa [idbinitializeimpl:: M_pcutlpropinfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) para implementar esta funcionalidad.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBPropertiesImpl (clase)](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)