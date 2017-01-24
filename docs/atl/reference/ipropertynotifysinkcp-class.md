---
title: "IPropertyNotifySinkCP Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "IPropertyNotifySinkCP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "puntos de conexión [C++], administrar"
  - "IPropertyNotifySinkCP class"
  - "sinks, notifying of changes"
ms.assetid: 1b41445e-bc88-4fa6-bb62-d68aacec2bd5
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IPropertyNotifySinkCP Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase expone la interfaz de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) como interfaz de salida en un objeto conectable.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
## Sintaxis  
  
```  
  
      template< class   
      T  
      , class  
      CDV   
      = CComDynamicUnkArray >  
class IPropertyNotifySinkCP :   
public IConnectionPointImpl< T, &IID_IPropertyNotifySink, CDV>  
```  
  
#### Parámetros  
 `T`  
 la clase, derivada de `IPropertyNotifySinkCP`.  
  
 `CDV`  
 Una clase que administra las conexiones entre un punto de conexión y sus receptores.  El valor predeterminado es [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), que permite conexiones ilimitadas.  También puede utilizar [CComUnkArray](../../atl/reference/ccomunkarray-class.md), que especifica un número fijo de conexiones.  
  
## Comentarios  
 `IPropertyNotifySinkCP` hereda todos los métodos a través de su clase base, [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md).  
  
 La interfaz de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) permite a un objeto de receptor recibir notificaciones sobre cambios de propiedad.  La clase `IPropertyNotifySinkCP` expone esta interfaz como interfaz de salida en un objeto conectable.  El cliente debe implementar los métodos de `IPropertyNotifySink` en el receptor.  
  
 Derive la clase de `IPropertyNotifySinkCP` cuando desee crear un punto de conexión que representa la interfaz de `IPropertyNotifySink` .  
  
 Para obtener más información sobre cómo utilizar los puntos de conexión en ATL, vea el artículo [Puntos de conexión](../../atl/atl-connection-points.md).  
  
## Requisitos  
 **encabezado:** atlctl.h  
  
## Vea también  
 [IConnectionPointImpl Class](../../atl/reference/iconnectionpointimpl-class.md)   
 [IConnectionPointContainerImpl Class](../../atl/reference/iconnectionpointcontainerimpl-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)