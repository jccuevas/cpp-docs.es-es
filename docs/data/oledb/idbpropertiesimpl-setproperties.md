---
title: 'Idbpropertiesimpl:: SetProperties | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl.SetProperties
- SetProperties
- IDBPropertiesImpl::SetProperties
dev_langs:
- C++
helpviewer_keywords:
- SetProperties method
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9cd0b425a61d3a9dd669f99e4c4471e728e68662
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="idbpropertiesimplsetproperties"></a>IDBPropertiesImpl::SetProperties
Establece propiedades en los grupos de propiedades origen de datos y la inicialización de objetos de origen de datos, o el grupo de propiedades de inicialización de los enumeradores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(SetProperties)(ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IDBProperties:: SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Si se inicializa el proveedor, este método establece los valores de propiedades en el **DBPROPSET_DATASOURCE**, **DBPROPSET_DATASOURCEINFO**, **DBPROPSET_DBINIT** propiedad grupos para el objeto de origen de datos. Si no se inicializa el proveedor, establece **DBPROPSET_DBINIT** solo propiedades del grupo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBPropertiesImpl (clase)](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)