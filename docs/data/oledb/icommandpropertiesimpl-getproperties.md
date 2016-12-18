---
title: "ICommandPropertiesImpl::GetProperties | Microsoft Docs"
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
  - "ICommandPropertiesImpl::GetProperties"
  - "ICommandPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties (método)"
ms.assetid: 1bee5f1b-bd08-435a-956a-e4cebcdf5d5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve todos los conjuntos solicitados de propiedad mediante la asignación de la propiedad del comando.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(GetProperties)(   
   const ULONG cPropertyIDSets,   
   const DBPROPIDSET rgPropertyIDSets[],   
   ULONG * pcPropertySets,   
   DBPROPSET ** prgPropertySets    
);  
```  
  
#### Parámetros  
 Vea [ICommandProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms723119.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Vea [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [ICommandPropertiesImpl \(Clase\)](../../data/oledb/icommandpropertiesimpl-class.md)   
 [ICommandPropertiesImpl::SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)