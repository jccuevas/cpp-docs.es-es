---
title: "IObjectWithSiteImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl<T>"
  - "IObjectWithSiteImpl"
  - "ATL.IObjectWithSiteImpl"
  - "ATL::IObjectWithSiteImpl<T>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IObjectWithSiteImpl class"
ms.assetid: 4e1f774f-bc3d-45ee-9a1c-c3533a511588
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# IObjectWithSiteImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos permitiendo que un objeto se comunique con el sitio.  
  
## Sintaxis  
  
```  
  
      template<  
   class T   
>  
class ATL_NO_VTABLE IObjectWithSiteImpl :  
   public IObjectWithSite  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IObjectWithSiteImpl`.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::GetSite](../Topic/IObjectWithSiteImpl::GetSite.md)|Consulta el sitio de un puntero de interfaz.|  
|[IObjectWithSiteImpl::SetChildSite](../Topic/IObjectWithSiteImpl::SetChildSite.md)|Proporciona el objeto con el puntero de **IUnknown** de sitio.|  
|[IObjectWithSiteImpl::SetSite](../Topic/IObjectWithSiteImpl::SetSite.md)|Proporciona el objeto con el puntero de **IUnknown** de sitio.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IObjectWithSiteImpl::m\_spUnkSite](../Topic/IObjectWithSiteImpl::m_spUnkSite.md)|Administra el puntero de **IUnknown** de sitio.|  
  
## Comentarios  
 La interfaz de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) permite que un objeto se comunique con el sitio.  La clase `IObjectWithSiteImpl` proporciona una implementación predeterminada de esta interfaz y implementa **IUnknown** enviando información del dispositivo de volcado en versiones de depuración.  
  
 `IObjectWithSiteImpl` especifica dos métodos.  El cliente llama `SetSite`primero, pasando el puntero de **IUnknown** de sitio.  Este puntero se almacena dentro del objeto, y se puede recuperar después con una llamada a `GetSite`.  
  
 Normalmente, debe derivar la clase de `IObjectWithSiteImpl` cuando se crea un objeto que no es un control.  Para los controles, derive la clase de [IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md), que también proporciona un puntero de sitio.  No derivar la clase de `IObjectWithSiteImpl` y de `IOleObjectImpl`.  
  
## Jerarquía de herencia  
 `IObjectWithSite`  
  
 `IObjectWithSiteImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)