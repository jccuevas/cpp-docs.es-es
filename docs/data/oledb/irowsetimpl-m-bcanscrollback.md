---
title: IRowsetImpl::m_bCanScrollBack | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IRowsetImpl::m_bCanScrollBack
- ATL::IRowsetImpl::m_bCanScrollBack
- IRowsetImpl.m_bCanScrollBack
- ATL.IRowsetImpl.m_bCanScrollBack
- m_bCanScrollBack
dev_langs:
- C++
helpviewer_keywords:
- m_bCanScrollBack
ms.assetid: 69de3179-bf56-415e-935f-e98bcb34debe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c388092aaeb935dc8eaf9f76d7d64adb974310b3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="irowsetimplmbcanscrollback"></a>IRowsetImpl::m_bCanScrollBack
Indica si un proveedor puede tener su desplazamiento de cursor con las versiones anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
unsigned  m_bCanScrollBack:1;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Vinculado a la **DBPROP_CANSCROLLBACKWARDS** propiedad en el **DBPROPSET_ROWSET** grupo. El proveedor debe admitir **DBPROP_CANSCROLLBACKWARDS** para **m_bCanFetchBackwards** se establezca en true.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (clase)](../../data/oledb/irowsetimpl-class.md)   
 [IRowsetImpl::m_bCanFetchBack](../../data/oledb/irowsetimpl-m-bcanfetchback.md)