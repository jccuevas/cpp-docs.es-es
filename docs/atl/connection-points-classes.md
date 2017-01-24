---
title: "Connection Points Classes | Microsoft Docs"
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
  - "vc.atl.connection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], puntos de conexión"
  - "connection points classes"
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Connection Points Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes proporcionan compatibilidad para los puntos de conexión:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa un contenedor de punto de conexión.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa la interfaz de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) .  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra conexiones ilimitadas entre un punto de conexión y sus receptores.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número fijo de conexiones entre un punto de conexión y sus receptores.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) Notifies el receptor de un cliente que la propiedad de un objeto ha cambiado o va a cambiar.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para los puntos de conexión para un objeto COM ATL.  Estos puntos de conexión se asignan a un mapa de receptor de eventos, proporcionado por el objeto COM.  
  
-   Los trabajos de[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) junto con el mapa de receptor de eventos en la clase para enrutar el evento al controlador adecuado funcionan.  
  
## artículos relacionados  
 [puntos de conexión](../atl/atl-connection-points.md)  
  
 [control de eventos y ATL](../atl/event-handling-and-atl.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)   
 [Connection Point Macros](../atl/reference/connection-point-macros.md)   
 [Connection Point Global Functions](../atl/reference/connection-point-global-functions.md)