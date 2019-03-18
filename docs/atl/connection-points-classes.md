---
title: Clases de puntos de conexión (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], connection points
- connection points classes
ms.assetid: 076365fa-299a-4dce-84c3-a5dff0e0da1f
ms.openlocfilehash: 8e1ee67f75af1fa38693f7ddb487580ab733cc58
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57819004"
---
# <a name="connection-points-classes"></a>Clases de puntos de conexión

Las clases siguientes proporcionan compatibilidad para puntos de conexión:

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa un contenedor de punto de conexión.

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa el [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfaz.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra conexiones ilimitadas entre un punto de conexión y sus receptores.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número fijo de conexiones entre un punto de conexión y sus receptores.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que ha cambiado una propiedad del objeto o que va a cambiar.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para puntos de conexión para un objeto COM de ATL. Estos puntos de conexión se asignan mediante un mapa de receptor de eventos, que se proporciona mediante el objeto COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el receptor de eventos se asigna en la clase para enrutar eventos a la función de controlador adecuado.

## <a name="related-articles"></a>Artículos relacionados

[Puntos de conexión](../atl/atl-connection-points.md)

[Control de eventos en ATL](../atl/event-handling-and-atl.md)

## <a name="see-also"></a>Vea también

[Información general de clases](../atl/atl-class-overview.md)<br/>
[Macros de punto de conexión](../atl/reference/connection-point-macros.md)<br/>
[Funciones globales de punto de conexión](../atl/reference/connection-point-global-functions.md)
