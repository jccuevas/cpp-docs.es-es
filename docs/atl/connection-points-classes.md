---
title: Clases de puntos de conexión (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 0dba06b072e1e9ca545ccbea196fcfe371b02157
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492444"
---
# <a name="connection-points-classes"></a>Clases de puntos de conexión

Las clases siguientes proporcionan compatibilidad con los puntos de conexión:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) Implementa un contenedor de puntos de conexión.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) Implementa un punto de conexión.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) Implementa un punto de conexión que representa la interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) Administra conexiones ilimitadas entre un punto de conexión y sus receptores.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) Administra un número fijo de conexiones entre un punto de conexión y sus receptores.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) Notifica al receptor de un cliente que la propiedad de un objeto ha cambiado o está a punto de cambiar.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) Proporciona compatibilidad para los puntos de conexión de un objeto COM ATL. Estos puntos de conexión se asignan a una asignación de receptor de eventos, proporcionada por el objeto COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) Funciona junto con el mapa del receptor de eventos en la clase para enrutar los eventos a la función de controlador adecuada.

## <a name="related-articles"></a>Artículos relacionados

[Puntos de conexión](../atl/atl-connection-points.md)

[Control de eventos en ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Vea también

[Información general sobre clases](../atl/atl-class-overview.md)<br/>
[Macros de punto de conexión](../atl/reference/connection-point-macros.md)<br/>
[Funciones globales de punto de conexión](../atl/reference/connection-point-global-functions.md)
