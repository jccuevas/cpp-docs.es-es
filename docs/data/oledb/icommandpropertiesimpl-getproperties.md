---
title: 'Icommandpropertiesimpl:: GetProperties | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- GetProperties
dev_langs:
- C++
helpviewer_keywords:
- GetProperties method
ms.assetid: 1bee5f1b-bd08-435a-956a-e4cebcdf5d5e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cc935986c5b1ad83e7faaca9b4cb7e76645aac62
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="icommandpropertiesimplgetproperties"></a>ICommandPropertiesImpl::GetProperties
Devuelve todos los conjuntos de propiedad solicitado mediante la asignación de propiedad del comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [ICommandProperties:: GetProperties](https://msdn.microsoft.com/en-us/library/ms723119.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [ICommandPropertiesImpl (clase)](../../data/oledb/icommandpropertiesimpl-class.md)   
 [ICommandPropertiesImpl::SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)