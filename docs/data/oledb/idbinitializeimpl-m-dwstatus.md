---
title: 'Idbinitializeimpl:: M_dwstatus | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
dev_langs: C++
helpviewer_keywords: m_dwStatus
ms.assetid: 7621ccff-ca60-4b75-9c6a-c104bd0e2038
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 360eeb936e2bf7b4219e9e6dc8eb95fe40c52c6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="idbinitializeimplmdwstatus"></a>IDBInitializeImpl::m_dwStatus
Marcas del origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DWORD m_dwStatus;  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas marcas especifican o indican el estado de varios atributos para el objeto de origen de datos. Contiene uno o varios de los siguientes `enum` valores:  
  
```  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|**DSF_MASK_INIT**|Una máscara para habilitar la restauración del estado sin inicializar.|  
|**DSF_PERSIST_DIRTY**|Establece si el objeto de origen de datos requiere la persistencia (es decir, si ha habido cambios).|  
|**DSF_INITIALIZED**|Establece si se ha inicializado el origen de datos.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBInitializeImpl (clase)](../../data/oledb/idbinitializeimpl-class.md)   
 [Idbinitializeimpl:: Idbinitializeimpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)   
 [IDBInitializeImpl::Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)