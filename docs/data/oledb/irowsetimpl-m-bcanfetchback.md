---
title: IRowsetImpl::m_bCanFetchBack | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.IRowsetImpl.m_bCanFetchBack
- ATL::IRowsetImpl::m_bCanFetchBack
- IRowsetImpl.m_bCanFetchBack
- IRowsetImpl::m_bCanFetchBack
- m_bCanFetchBack
dev_langs:
- C++
helpviewer_keywords:
- m_bCanFetchBack
ms.assetid: cfa007b0-7ba5-48a3-9d05-9f1916305fb7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b01ea2c44475e6924aac8e58cc9671cdf81ec7c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplmbcanfetchback"></a>IRowsetImpl::m_bCanFetchBack
Indica si un proveedor admite la captura con versiones anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
unsigned m_bCanFetchBack:1;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Vinculado a la **DBPROP_CANFETCHBACKWARDS** propiedad en el **DBPROPSET_ROWSET** grupo. El proveedor debe admitir **DBPROP_CANFETCHBACKWARDS** para **m_bCanFetchBackwards** se establezca en true.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (clase)](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanScrollBack](../../data/oledb/irowsetimpl-m-bcanscrollback.md)