---
title: "IEnumOnSTLImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IEnumOnSTLImpl"
  - "ATL.IEnumOnSTLImpl"
  - "ATL::IEnumOnSTLImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IEnumOnSTLImpl class"
ms.assetid: 1789e77b-88b8-447d-a490-806b918912ce
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# IEnumOnSTLImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase define una interfaz de enumerador basada en una colección de STL.  
  
## Sintaxis  
  
```  
  
      template <  
   class Base,  
   const IID* piid,  
   class T,  
   class Copy,  
   class CollType  
>  
class ATL_NO_VTABLE IEnumOnSTLImpl :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 Una interfaz COM de enumerador \(\).  
  
 `piid`  
 Un puntero al identificador de la interfaz de la interfaz del enumerador.  
  
 `T`  
 El tipo de elemento expuesto por la interfaz del enumerador.  
  
 `Copy`  
 [copie la clase de directiva](../../atl/atl-copy-policy-classes.md).  
  
 `CollType`  
 Una clase de contenedor de STL.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IEnumOnSTLImpl::Clone](../Topic/IEnumOnSTLImpl::Clone.md)|la implementación de [:: clon](https://msdn.microsoft.com/en-us/library/ms690336.aspx).|  
|[IEnumOnSTLImpl::Init](../Topic/IEnumOnSTLImpl::Init.md)|Inicializa el enumerador.|  
|[IEnumOnSTLImpl::Next](../Topic/IEnumOnSTLImpl::Next.md)|la implementación de [:: Siguiente](https://msdn.microsoft.com/en-us/library/ms695273.aspx).|  
|[IEnumOnSTLImpl::Reset](../Topic/IEnumOnSTLImpl::Reset.md)|la implementación de [:: Restablecer](https://msdn.microsoft.com/en-us/library/ms693414.aspx).|  
|[IEnumOnSTLImpl::Skip](../Topic/IEnumOnSTLImpl::Skip.md)|la implementación de [:: Omitir](https://msdn.microsoft.com/en-us/library/ms690392.aspx).|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IEnumOnSTLImpl::m\_iter](../Topic/IEnumOnSTLImpl::m_iter.md)|El iterador que representa la posición actual del enumerador dentro de la colección.|  
|[IEnumOnSTLImpl::m\_pcollection](../Topic/IEnumOnSTLImpl::m_pcollection.md)|Un puntero al contenedor de STL que contiene los elementos que se van a mostrar.|  
|[IEnumOnSTLImpl::m\_spUnk](../Topic/IEnumOnSTLImpl::m_spUnk.md)|El puntero de **IUnknown** del objeto que proporciona la colección.|  
  
## Comentarios  
 `IEnumOnSTLImpl` proporciona la implementación de una interfaz COM de enumerador donde los elementos enumerados se almacenan en un contenedor de STL\- compatible.  Esta clase es análoga a la clase de [CComEnumImpl](../../atl/reference/ccomenumimpl-class.md) , que proporciona una implementación de una interfaz de enumerador basada en una matriz.  
  
> [!NOTE]
>  Vea [CComEnumImpl::Init](../Topic/CComEnumImpl::Init.md) para obtener información sobre otras diferencias entre `CComEnumImpl` y `IEnumOnSTLImpl`.  
  
 Normalmente, no necesitará crear dispone de la clase enumerator derivando de esta implementación de la interfaz.  Si desea utilizar un enumerador ATL\- proporcionado por un contenedor STL, es más común crear una instancia de [CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md), o crear una clase de colección que devuelve un enumerador derivando de [ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md).  
  
 Sin embargo, si necesita proporcionar un enumerador personalizado \(por ejemplo, uno que expone interfaces además de la interfaz del enumerador\), puede derivar de esta clase.  En esta situación es probable que necesite reemplazar el método de [clon](../Topic/IEnumOnSTLImpl::Clone.md) para proporcionar su propia implementación.  
  
## Jerarquía de herencia  
 `Base`  
  
 `IEnumOnSTLImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)