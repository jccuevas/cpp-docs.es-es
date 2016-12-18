---
title: "IDBPropertiesImpl::GetProperties | Microsoft Docs"
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
  - "IDBPropertiesImpl::GetProperties"
  - "IDBPropertiesImpl.GetProperties"
  - "GetProperties"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProperties (método)"
ms.assetid: ab24aebd-366d-49a1-b49b-bb46c6d90f05
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl::GetProperties
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve los valores de propiedades en los grupos de propiedades de origen de datos, la información del origen de datos, y de inicialización que se establecen actualmente en el objeto de origen de datos o los valores de las propiedades en el grupo de propiedades de inicialización que se establecen actualmente en el enumerador.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(GetProperties)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcProperties,   
   DBPROPSET ** prgProperties    
);  
```  
  
#### Parámetros  
 Vea [IDBProperties::GetProperties](https://msdn.microsoft.com/en-us/library/ms714344.aspx) en *la referencia del*programador.  
  
 Algunos parámetros corresponden *a OLE DB parámetros de referencia* de nombres diferentes, que se describen en **IDBProperties::GetProperties**:  
  
|Parámetros de plantilla OLE DB|*Los parámetros de referencia del programador de OLE DB*|  
|------------------------------------|--------------------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
|*pcProperties*|*pcPropertySets*|  
|*prgProperties*|*prgPropertySets*|  
  
## Comentarios  
 Si se inicializa el proveedor, este método devuelve los valores de las propiedades en **DBPROPSET\_DATASOURCE**, **DBPROPSET\_DATASOURCEINFO**, los grupos de propiedades de **DBPROPSET\_DBINIT** establecidas actualmente en el objeto de origen de datos.  Si no se inicializa el proveedor, devuelve las propiedades de grupo de **DBPROPSET\_DBINIT** únicamente.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IDBPropertiesImpl \(Clase\)](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)