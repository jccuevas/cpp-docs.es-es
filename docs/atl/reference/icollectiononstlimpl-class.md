---
title: "ICollectionOnSTLImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.ICollectionOnSTLImpl"
  - "ATL::ICollectionOnSTLImpl"
  - "ICollectionOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICollectionOnSTLImpl class"
ms.assetid: 683c88b0-0d97-4779-a762-e493334ba7f9
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# ICollectionOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos utilizados por una clase de colección.  
  
## Sintaxis  
  
```  
  
      template <  
   class T,  
   class CollType,  
   class ItemType,  
   class CopyItem,  
   class EnumType  
>  
class ICollectionOnSTLImpl :  
   public T  
```  
  
#### Parámetros  
 `T`  
 una interfaz de intercalación COM.  
  
 `CollType`  
 Una clase de contenedor de STL.  
  
 *ItemType*  
 El tipo de elemento expuesto por la interfaz del contenedor.  
  
 *CopyItem*  
 [copie la clase de directiva](../../atl/atl-copy-policy-classes.md).  
  
 *EnumType*  
 [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)\- clase compatible de enumerador.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ICollectionOnSTLImpl::get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md)|Devuelve un objeto de enumerador para la colección.|  
|[ICollectionOnSTLImpl::get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md)|Devuelve el número de elementos de la colección.|  
|[ICollectionOnSTLImpl::get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md)|devuelve el elemento solicitado de la colección.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ICollectionOnSTLImpl::m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md)|La colección.|  
  
## Comentarios  
 Esta clase proporciona la implementación de tres métodos de una interfaz de intercalación: [get\_Count](../Topic/ICollectionOnSTLImpl::get_Count.md), [get\_Item](../Topic/ICollectionOnSTLImpl::get_Item.md), y [get\_\_NewEnum](../Topic/ICollectionOnSTLImpl::get__NewEnum.md).  
  
 para utilizar esta clase:  
  
-   Defina \(o ubicaciones\) una interfaz de intercalación que desee que desee implementar.  
  
-   Derive la clase de una especialización de `ICollectionOnSTLImpl` basándose en esta interfaz de intercalación.  
  
-   Utilice la clase derivada para implementar un método de la interfaz de intercalación no controlada por `ICollectionOnSTLImpl`.  
  
> [!NOTE]
>  Si la interfaz de intercalación es una interfaz dual, derive la clase de [IDispatchImpl](../../atl/reference/idispatchimpl-class.md), pasando la especialización de `ICollectionOnSTLImpl` como primer parámetro de plantilla si desea ATL para proporcionar la implementación de los métodos de `IDispatch` .  
  
-   Agregar elementos al miembro de [m\_coll](../Topic/ICollectionOnSTLImpl::m_coll.md) para rellenar la colección.  
  
 Para obtener más información y ejemplos, vea [Colecciones y enumeradores ATL](../../atl/atl-collections-and-enumerators.md).  
  
## Jerarquía de herencia  
 `T`  
  
 `ICollectionOnSTLImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Ejemplo ATLCollections](../../top/visual-cpp-samples.md)   
 [Class Overview](../../atl/atl-class-overview.md)