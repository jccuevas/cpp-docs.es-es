---
title: "ICommandPropertiesImpl::SetProperties | Microsoft Docs"
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
  - "ICommandPropertiesImpl.SetProperties"
  - "ICommandPropertiesImpl::SetProperties"
  - "SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties (método)"
ms.assetid: c42132bb-16a9-4e00-aba6-dee785a98488
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece las propiedades del objeto de comando.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### Parámetros  
 Vea [ICommandProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms711497.aspx) en *la referencia del*programador.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandPropertiesImpl \(Clase\)](../../data/oledb/icommandpropertiesimpl-class.md)   
 [ICommandPropertiesImpl::GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)