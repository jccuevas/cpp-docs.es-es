---
title: "IDBPropertiesImpl::SetProperties | Microsoft Docs"
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
  - "IDBPropertiesImpl.SetProperties"
  - "SetProperties"
  - "IDBPropertiesImpl::SetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetProperties (método)"
ms.assetid: 2f9fc1de-7f35-4bca-bab3-7b427bf92c26
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl::SetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece las propiedades de los grupos de propiedades de origen de datos y de inicialización, para objetos de origen de datos, o el grupo de propiedades de inicialización, para los enumeradores.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(SetProperties)(   
   ULONG cPropertySets,   
   DBPROPSET rgPropertySets[]    
);  
```  
  
#### Parámetros  
 Vea [IDBProperties::SetProperties](https://msdn.microsoft.com/en-us/library/ms723049.aspx) en *la referencia del*programador.  
  
## Comentarios  
 Si se inicializa el proveedor, este método establece los valores de las propiedades en **DBPROPSET\_DATASOURCE**, **DBPROPSET\_DATASOURCEINFO**, grupos de propiedades de **DBPROPSET\_DBINIT** para el objeto de origen de datos.  Si no se inicializa el proveedor, establece las propiedades de grupo de **DBPROPSET\_DBINIT** únicamente.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IDBPropertiesImpl \(Clase\)](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)