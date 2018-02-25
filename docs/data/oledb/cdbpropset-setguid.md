---
title: CDBPropSet::SetGUID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
helpviewer_keywords:
- SetGUID method
- AddProperty method
ms.assetid: a4cce036-cf1f-4897-9712-7b01eaf887ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: edf9720e0f116060a06ffa56bf5c3e6c4c8691e1
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdbpropsetsetguid"></a>CDBPropSet::SetGUID
Establece el **guidPropertySet** campo el **DBPROPSET** estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      void SetGUID(const GUID& guid) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Un GUID que se utiliza para establecer el **guidPropertySet** campo de la [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) estructura.  
  
## <a name="remarks"></a>Comentarios  
 Este campo se puede establecer la [constructor](../../data/oledb/cdbpropset-cdbpropset.md) así.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBPropSet (Clase)](../../data/oledb/cdbpropset-class.md)