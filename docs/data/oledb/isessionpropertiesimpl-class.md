---
title: "ISessionPropertiesImpl (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ISessionPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ISessionPropertiesImpl (clase)"
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# ISessionPropertiesImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ISessionPropertiesImpl :  
   public ISessionProperties,    
   public CUtlProps<PropClass>  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de `ISessionPropertiesImpl`.  
  
 `PropClass`  
 Una clase de propiedad definida por el usuario que toma como valor predeterminado la `T`.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/isessionpropertiesimpl-getproperties.md)|Devuelve la lista de propiedades del grupo de propiedades de la sesión que se establecen actualmente en la sesión.|  
|[SetProperties](../../data/oledb/isessionpropertiesimpl-setproperties.md)|Establezca las propiedades en el grupo de propiedades de la sesión.|  
  
## Comentarios  
 Una interfaz de enlace en sesiones.  Esta clase implementa propiedades de sesión llamando a una función estática definida por [mapa del conjunto de propiedades](../../data/oledb/begin-propset-map.md).  El mapa del conjunto de propiedades se debe especificar en la clase de sesión.  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)