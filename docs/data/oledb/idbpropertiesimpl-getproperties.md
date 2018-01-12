---
title: 'Idbpropertiesimpl:: GetProperties | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- GetProperties
dev_langs: C++
helpviewer_keywords: GetProperties method
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ac54b08dba170dd33d2e5e19cae50715aeab4fb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idbpropertiesimplgetproperties"></a>IDBPropertiesImpl::GetProperties
Devuelve los valores de propiedades de los grupos de propiedades de origen de datos, información de origen de datos y la inicialización que están establecidos actualmente en el objeto de origen de datos o los valores de propiedades en el grupo de propiedades de inicialización que están establecidas actualmente en el enumerador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties    
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) en el *referencia del programador OLE DB*.  
  
 Algunos parámetros corresponden a *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en **IDBProperties::GetProperties**:  
  
|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|  
|--------------------------------|------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## <a name="remarks"></a>Comentarios  
 Si se inicializa el proveedor, este método devuelve los valores de propiedades en el **DBPROPSET_DATASOURCE**, **DBPROPSET_DATASOURCEINFO**, **DBPROPSET_DBINIT** grupos de propiedades que están establecidos actualmente en el objeto de origen de datos. Si no se inicializa el proveedor, devuelve **DBPROPSET_DBINIT** solo propiedades del grupo.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBPropertiesImpl (clase)](../../data/oledb/idbpropertiesimpl-class.md)   
 [Idbpropertiesimpl:: GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)