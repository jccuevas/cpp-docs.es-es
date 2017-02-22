---
title: "IDBInitializeImpl::m_dwStatus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IDBInitializeImpl::m_dwStatus"
  - "IDBInitializeImpl.m_dwStatus"
  - "ATL.IDBInitializeImpl.m_dwStatus"
  - "IDBInitializeImpl::m_dwStatus"
  - "IDBInitializeImpl<T>::m_dwStatus"
  - "ATL.IDBInitializeImpl<T>.m_dwStatus"
  - "ATL::IDBInitializeImpl<T>::m_dwStatus"
  - "m_dwStatus"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "m_dwStatus"
ms.assetid: 7621ccff-ca60-4b75-9c6a-c104bd0e2038
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IDBInitializeImpl::m_dwStatus
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Marcas de origen de datos.  
  
## Sintaxis  
  
```  
  
DWORD m_dwStatus;  
  
```  
  
## Comentarios  
 Estos marcadores especifican o indican el estado de diferentes atributos para el objeto de origen de datos.  Contiene uno o más de los siguientes valores de `enum` :  
  
 `enum DATASOURCE_FLAGS {`  
  
 `DSF_MASK_INIT     = 0xFFFFF00F,`  
  
 `DSF_PERSIST_DIRTY = 0x00000001,`  
  
 `DSF_INITIALIZED   = 0x00000010,`  
  
 `};`  
  
|||  
|-|-|  
|**DSF\_MASK\_INIT**|Una máscara para habilitar la restauración de estado no inicializado.|  
|**DSF\_PERSIST\_DIRTY**|Conjunto si el objeto de origen de datos requiere persistencia \(es decir, si ha habido cambios\).|  
|**DSF\_INITIALIZED**|Conjunto si se ha inicializado el origen de datos.|  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IDBInitializeImpl \(Clase\)](../../data/oledb/idbinitializeimpl-class.md)   
 [IDBInitializeImpl::IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)   
 [IDBInitializeImpl::Uninitialize](../../data/oledb/idbinitializeimpl-uninitialize.md)