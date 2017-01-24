---
title: "IGetDataSourceImpl::GetDataSource | Microsoft Docs"
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
  - "GetDataSource"
  - "IGetDataSourceImpl.GetDataSource"
  - "IGetDataSourceImpl::GetDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetDataSource (método)"
ms.assetid: b70995d2-b951-452e-a2d4-fb3eb085886e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IGetDataSourceImpl::GetDataSource
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(GetDataSource)(   
   REFIID riid,   
   IUnknown ** ppDataSource    
);  
```  
  
#### Parámetros  
 Vea [IGetDataSource::GetDataSource](https://msdn.microsoft.com/en-us/library/ms725443.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Útil si necesita tener acceso a las propiedades del objeto de origen de datos.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IGetDataSourceImpl \(Clase\)](../../data/oledb/igetdatasourceimpl-class.md)