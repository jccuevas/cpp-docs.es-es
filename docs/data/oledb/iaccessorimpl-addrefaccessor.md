---
title: "IAccessorImpl::AddRefAccessor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IAccessorImpl::AddRefAccessor"
  - "AddRefAccessor"
  - "IAccessorImpl::AddRefAccessor"
  - "IAccessorImpl.AddRefAccessor"
  - "ATL.IAccessorImpl.AddRefAccessor"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRefAccessor (método)"
ms.assetid: 4c15392c-944b-4cbd-8cc7-2a5c2f308a70
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IAccessorImpl::AddRefAccessor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Agrega un contador de referencias a un descriptor de acceso existente.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(AddRefAccessor)(  
   HACCESSOR hAccessor,  
   DBREFCOUNT* pcRefCount   
);  
```  
  
#### Parámetros  
 Vea [IAccessor::AddRefAccessor](https://msdn.microsoft.com/en-us/library/ms714978.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IAccessorImpl \(Clase\)](../../data/oledb/iaccessorimpl-class.md)   
 [IAccessorImpl::CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)   
 [IAccessorImpl::ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)