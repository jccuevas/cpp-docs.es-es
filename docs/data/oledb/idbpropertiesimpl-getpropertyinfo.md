---
title: 'Idbpropertiesimpl:: GetPropertyInfo | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ebd70a60e8629602e25f0a599fdac2225c29eba5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
 [Idbpropertiesimpl:: GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)