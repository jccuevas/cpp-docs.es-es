---
title: "IDBInitializeImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL.IDBInitializeImpl<T>"
  - "ATL::IDBInitializeImpl<T>"
  - "IDBInitializeImpl"
  - "ATL::IDBInitializeImpl"
  - "ATL.IDBInitializeImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDBInitializeImpl (clase)"
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# IDBInitializeImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [IDBInitialize](https://msdn.microsoft.com/en-us/library/ms713706.aspx) .  
  
## Sintaxis  
  
```  
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `IDBInitializeImpl`.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-idbinitializeimpl.md)|Constructor.|  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[Inicializar](../../data/oledb/idbinitializeimpl-initialize.md)|Inicia el proveedor.|  
|[Desinicialice](../../data/oledb/idbinitializeimpl-uninitialize.md)|Detiene el proveedor.|  
  
### Miembros de datos  
  
|||  
|-|-|  
|[m\_dwStatus](../../data/oledb/idbinitializeimpl-m-dwstatus.md)|Marcas de origen de datos.|  
|[m\_pCUtlPropInfo](../../data/oledb/idbinitializeimpl-m-pcutlpropinfo.md)|Un puntero a la implementación de la información de las propiedades de DB.|  
  
## Comentarios  
 Una interfaz de enlace en objetos de origen de datos y interfaz opcional de enumeradores.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)