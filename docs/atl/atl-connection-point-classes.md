---
title: "ATL Connection Point Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, puntos de conexión"
  - "CComDynamicUnkArray class, connection point classes"
  - "CComUnkArray class, connection point classes"
  - "CFirePropNotifyEvent class"
  - "CFirePropNotifyEvent class, connection point classes"
  - "puntos de conexión [C++], clases ATL"
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Connection Point Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ATL utiliza las siguientes clases para admitir los puntos de conexión:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión.  El IID de la interfaz de salida que representa se pasa como parámetro de plantilla.  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa el contenedor de punto de conexión y administra la lista de objetos de `IConnectionPointImpl` .  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa la interfaz de [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) .  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra un número arbitrario de conexiones entre el punto de conexión y sus receptores.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número predefinido de conexiones según lo especificado por el parámetro de plantilla.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que la propiedad de un objeto ha cambiado o se va a cambiar.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para los puntos de conexión para un objeto COM ATL.  Estos puntos de conexión se asignan a un mapa de receptor de eventos, proporcionado por el objeto COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el mapa de receptor de eventos en la clase para distribuir eventos a la función adecuada del controlador.  
  
## Vea también  
 [Puntos de conexión](../atl/atl-connection-points.md)