---
title: "Clases de puntos de conexión (ATL) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.atl.connection
dev_langs: C++
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ef188a5fc03a60c3481477d000662d595b7d4dd9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="connection-points-classes"></a>Clases de puntos de conexión
Las clases siguientes proporcionan compatibilidad para puntos de conexión:  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa un contenedor de punto de conexión.  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa el [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra conexiones ilimitadas entre un punto de conexión y sus receptores.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número fijo de conexiones entre un punto de conexión y sus receptores.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que la propiedad de un objeto ha cambiado o va a cambiar.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para puntos de conexión para un objeto COM de ATL. Estos puntos de conexión se asignan a un mapa de receptores de eventos, que se proporciona mediante el objeto COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el receptor de eventos se asigna en la clase de eventos de ruta a la función de controlador adecuado.  
  
## <a name="related-articles"></a>Artículos relacionados  
 [Puntos de conexión](../atl/atl-connection-points.md)  
  
 [Control de eventos en ATL](../atl/event-handling-and-atl.md)  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../atl/atl-class-overview.md)   
 [Macros de punto de conexión](../atl/reference/connection-point-macros.md)   
 [Funciones globales de punto de conexión](../atl/reference/connection-point-global-functions.md)

