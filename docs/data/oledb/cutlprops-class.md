---
title: "CUtlProps (Clase) | Microsoft Docs"
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
  - "CUtlProps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CUtlProps (clase)"
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CUtlProps (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa las propiedades de una variedad de interfaces de propiedades OLE DB \(por ejemplo, `IDBProperties`, `IDBProperties`, y `IRowsetInfo`\).  
  
## Sintaxis  
  
```  
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
#### Parámetros  
 `T`  
 La clase que contiene `BEGIN_PROPSET_MAP`.  
  
## Miembros  
  
### Métodos  
  
|||  
|-|-|  
|[GetPropValue](../../data/oledb/cutlprops-getpropvalue.md)|Obtiene una propiedad de un conjunto de propiedades.|  
|[IsValidValue](../../data/oledb/cutlprops-isvalidvalue.md)|Se utiliza para validar un valor antes de establecer una propiedad.|  
|[OnInterfaceRequested](../../data/oledb/cutlprops-oninterfacerequested.md)|Orden de los identificadores una interfaz opcional cuando un consumidor llama a un método de una interfaz de la creación de objetos.|  
|[OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)|Se llama después de establecer una propiedad para controlar propiedades vinculadas.|  
|[SetPropValue](../../data/oledb/cutlprops-setpropvalue.md)|Establece una propiedad en un conjunto de propiedades.|  
  
## Comentarios  
 La mayor parte de esta clase es un detalle de implementación.  
  
 `CUtlProps` contiene dos miembros para establecer propiedades internamente: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) y [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Para obtener más información sobre las macros utilizadas en un mapa del conjunto de propiedades, vea [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) y [END\_PROPSET\_MAP](../../data/oledb/end-propset-map.md).  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)