---
title: "IDBPropertiesImpl::GetPropertyInfo | Microsoft Docs"
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
  - "IDBPropertiesImpl::GetPropertyInfo"
  - "IDBPropertiesImpl.GetPropertyInfo"
  - "GetPropertyInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetPropertyInfo (método)"
ms.assetid: 170e9640-5010-4e0d-8a54-f50b23af08ad
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl::GetPropertyInfo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve información de la propiedad admitida por el origen de datos.  
  
## Sintaxis  
  
```  
  
      STDMETHOD(GetPropertyInfo)(   
   ULONG cPropertySets,   
   const DBPROPIDSET rgPropertySets[],   
   ULONG * pcPropertyInfoSets,   
   DBPROPINFOSET ** prgPropertyInfoSets,   
   OLECHAR ** ppDescBuffer    
);  
```  
  
#### Parámetros  
 Vea [IDBProperties::GetPropertyInfo](https://msdn.microsoft.com/en-us/library/ms718175.aspx) en *la referencia del*programador.  
  
 Algunos parámetros corresponden *a OLE DB parámetros de referencia* de nombres diferentes, que se describen en **IDBProperties::GetPropertyInfo**:  
  
|Parámetros de plantilla OLE DB|*Los parámetros de referencia del programador de OLE DB*|  
|------------------------------------|--------------------------------------------------------------|  
|`cPropertySets`|`cPropertyIDSets`|  
|`rgPropertySets`|`rgPropertyIDSets`|  
  
## Comentarios  
 Utiliza [IDBInitializeImpl::m\_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md) para implementar esta funcionalidad.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [IDBPropertiesImpl \(Clase\)](../../data/oledb/idbpropertiesimpl-class.md)   
 [IDBPropertiesImpl::GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)   
 [IDBPropertiesImpl::SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)