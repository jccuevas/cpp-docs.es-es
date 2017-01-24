---
title: "IConnectionPointImpl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.IConnectionPointImpl"
  - "IConnectionPointImpl"
  - "ATL::IConnectionPointImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "puntos de conexión [C++], implementar"
  - "IConnectionPointImpl class"
ms.assetid: 27992115-3b86-45dd-bc9e-54f32876c557
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IConnectionPointImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa un punto de conexión.  
  
## Sintaxis  
  
```  
  
      template<  
   class T,  
   const IID* piid,  
   class CDV = CComDynamicUnkArray   
>  
class ATL_NO_VTABLE IConnectionPointImpl :  
   public _ICPLocator< piid >  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IConnectionPointImpl`.  
  
 `piid`  
 Un puntero al identificador IID de la interfaz representada por el objeto de punto de conexión.  
  
 `CDV`  
 Una clase que administra las conexiones.  El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas.  También puede utilizar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointImpl::Advise](../Topic/IConnectionPointImpl::Advise.md)|establece una conexión entre el punto de conexión y un receptor.|  
|[IConnectionPointImpl::EnumConnections](../Topic/IConnectionPointImpl::EnumConnections.md)|Crea un enumerador para recorrer en iteración las conexiones para el punto de conexión.|  
|[IConnectionPointImpl::GetConnectionInterface](../Topic/IConnectionPointImpl::GetConnectionInterface.md)|Recupera el IID de la interfaz representada por el punto de conexión.|  
|[IConnectionPointImpl::GetConnectionPointContainer](../Topic/IConnectionPointImpl::GetConnectionPointContainer.md)|Recupera un puntero de interfaz al objeto conectable.|  
|[IConnectionPointImpl::Unadvise](../Topic/IConnectionPointImpl::Unadvise.md)|finaliza una conexión establecida previamente con `Advise`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[IConnectionPointImpl::m\_vec](../Topic/IConnectionPointImpl::m_vec.md)|Administra las conexiones para el punto de conexión.|  
  
## Comentarios  
 `IConnectionPointImpl` implementa un punto de conexión, que permite a un objeto exponer una interfaz de salida al cliente.  El cliente implementa esta interfaz en un objeto denominado receptor.  
  
 ATL utiliza [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) para implementar el objeto conectable.  Cada punto de conexión dentro del objeto conectable representa una interfaz de salida, identificada por `piid`.  La clase *CDV* administra las conexiones entre el punto de conexión y un receptor.  Cada conexión se identifica de forma exclusiva por una “cookie”.  
  
 Para obtener más información sobre cómo utilizar los puntos de conexión en ATL, vea el artículo [Puntos de conexión](../../atl/atl-connection-points.md).  
  
## Jerarquía de herencia  
 `_ICPLocator`  
  
 `IConnectionPointImpl`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318)   
 [Class Overview](../../atl/atl-class-overview.md)