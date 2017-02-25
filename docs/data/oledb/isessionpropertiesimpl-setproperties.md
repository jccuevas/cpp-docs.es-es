---
title: "ISessionPropertiesImpl::SetProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ISessionPropertiesImpl.SetProperties"
  - "SetProperties"
  - "ISessionPropertiesImpl::SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties (método)"
ms.assetid: 2e1219ed-0e1e-460e-84d6-031acfbfd3d2
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# ISessionPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establezca las propiedades en el grupo de propiedades de **DBPROPSET\_SESSION** .  
  
## Sintaxis  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### Parámetros  
 Vea [ISessionProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms714405.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ISessionPropertiesImpl \(Clase\)](../../data/oledb/isessionpropertiesimpl-class.md)   
 [ISessionPropertiesImpl::GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)