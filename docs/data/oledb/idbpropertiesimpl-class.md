---
title: "IDBPropertiesImpl (Clase) | Microsoft Docs"
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
  - "IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl"
  - "ATL.IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl<T>"
  - "ATL::IDBPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBPropertiesImpl (clase)"
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDBPropertiesImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de `IDBProperties` .  
  
## Sintaxis  
  
```  
template <class T>   
class ATL_NO_VTABLE IDBPropertiesImpl   
   : public IDBProperties, public CUtlProps<T>  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `IDBPropertiesImpl`.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/idbpropertiesimpl-getproperties.md)|Devuelve los valores de propiedades en los grupos de propiedades de origen de datos, la información del origen de datos, y de inicialización que se establecen actualmente en el objeto de origen de datos o los valores de las propiedades en el grupo de propiedades de inicialización que se establecen actualmente en el enumerador.|  
|[GetPropertyInfo](../../data/oledb/idbpropertiesimpl-getpropertyinfo.md)|Devuelve información sobre todas las propiedades admitidas por el proveedor.|  
|[SetProperties](../../data/oledb/idbpropertiesimpl-setproperties.md)|Establece las propiedades de los grupos de propiedades de origen de datos y de inicialización, para objetos de origen de datos, o el grupo de propiedades de inicialización, para los enumeradores.|  
  
## Comentarios  
 [IDBProperties](https://msdn.microsoft.com/en-us/library/ms719607.aspx) es una interfaz de enlace para los objetos de origen de datos y una interfaz opcional para los enumeradores.  Sin embargo, si un enumerador expone [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx), debe exponer `IDBProperties`.  `IDBPropertiesImpl` implementa `IDBProperties` mediante una función estática definida por [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)