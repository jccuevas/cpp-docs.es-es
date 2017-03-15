---
title: "IRowsetCreatorImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::IRowsetCreatorImpl"
  - "ATL.IRowsetCreatorImpl"
  - "ATL::IRowsetCreatorImpl<T>"
  - "ATL.IRowsetCreatorImpl<T>"
  - "IRowsetCreatorImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IRowsetCreatorImpl (clase)"
ms.assetid: 92cc950f-7978-4754-8d9a-defa63867d82
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# IRowsetCreatorImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza las mismas funciones que `IObjectWithSite` pero también habilita las propiedades **DBPROPCANSCROLLBACKWARDS DBPROPCANFETCHBACKWARDS**OLE DB.  
  
## Sintaxis  
  
```  
template < class T >  
class ATL_NO_VTABLE IRowsetCreatorImpl   
   : public IObjectWithSiteImpl< T >  
```  
  
#### Parámetros  
 `T`  
 Una clase derivada de **IRowsetCreator**.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[SetSite](../../data/oledb/irowsetcreatorimpl-setsite.md)|Establece el sitio que contiene el objeto de conjunto de filas.|  
  
## Comentarios  
 Esta clase hereda de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) y reemplaza [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  Cuando un objeto de comando o de sesión del proveedor crea un conjunto de filas, llama a `QueryInterface` en el objeto de conjunto de filas que busca `IObjectWithSite` y llama a `SetSite` que pasa la interfaz de **IUnkown** del objeto de conjunto de filas como la interfaz del sitio.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)