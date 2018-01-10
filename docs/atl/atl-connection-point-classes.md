---
title: "Clases de puntos de conexión ATL | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9845fdffdd951809ee7127c5fec86097a6219354
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atl-connection-point-classes"></a>Clases de puntos de conexión ATL
ATL utiliza las siguientes clases para admitir puntos de conexión:  
  
-   [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión. El IID de la interfaz de salida que representa se pasa como un parámetro de plantilla.  
  
-   [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa el contenedor de punto de conexión y administra la lista de `IConnectionPointImpl` objetos.  
  
-   [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa el [IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) interfaz.  
  
-   [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra un número arbitrario de conexiones entre el punto de conexión y sus receptores.  
  
-   [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número predefinido de conexiones según lo especificado por el parámetro de plantilla.  
  
-   [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que la propiedad de un objeto ha cambiado o va a cambiar.  
  
-   [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para puntos de conexión para un objeto COM de ATL. Estos puntos de conexión se asignan a un mapa de receptores de eventos, que se proporciona mediante el objeto COM.  
  
-   [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el mapa de receptores de eventos en la clase de eventos de ruta a la función de controlador adecuado.  
  
## <a name="see-also"></a>Vea también  
 [Punto de conexión](../atl/atl-connection-points.md)

