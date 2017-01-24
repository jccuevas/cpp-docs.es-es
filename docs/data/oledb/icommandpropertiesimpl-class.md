---
title: "ICommandPropertiesImpl (Clase) | Microsoft Docs"
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
  - "ICommandPropertiesImpl"
  - "ATL.ICommandPropertiesImpl"
  - "ATL::ICommandPropertiesImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandPropertiesImpl (clase)"
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ICommandPropertiesImpl (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una implementación de la interfaz de [ICommandProperties](https://msdn.microsoft.com/en-us/library/ms723044.aspx) .  
  
## Sintaxis  
  
```  
template <class T, class PropClass = T>  
class ATL_NO_VTABLE ICommandPropertiesImpl   
   : public ICommandProperties, public CUtlProps<PropClass>  
```  
  
#### Parámetros  
 `T`  
 La clase, derivada de  
  
 `PropClass`  
 La clase de propiedades.  
  
## Miembros  
  
### Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](../../data/oledb/icommandpropertiesimpl-getproperties.md)|Devuelve la lista de propiedades del grupo de propiedades del conjunto de filas que se soliciten actualmente para el conjunto de filas.|  
|[SetProperties](../../data/oledb/icommandpropertiesimpl-setproperties.md)|Establezca las propiedades en el grupo de propiedades de conjunto de filas.|  
  
## Comentarios  
 Esto es obligatorio en comandos.  La implementación proporcionada por una función estática definida por la macro de [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md) .  
  
## Requisitos  
 **Header:** atldb.h  
  
## Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)