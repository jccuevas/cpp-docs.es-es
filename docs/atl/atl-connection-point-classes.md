---
title: Clases de puntos de conexión ATL
ms.date: 11/04/2016
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
ms.openlocfilehash: 8644fc087d7f0a651724c40d2868e96c9b6ec96a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491820"
---
# <a name="atl-connection-point-classes"></a>Clases de puntos de conexión ATL

ATL utiliza las clases siguientes para admitir puntos de conexión:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión. El IID de la interfaz de salida que representa se pasa como un parámetro de plantilla.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa el contenedor de puntos de conexión y administra la lista `IConnectionPointImpl` de objetos.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa la interfaz [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) .

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra un número arbitrario de conexiones entre el punto de conexión y sus receptores.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número predefinido de conexiones tal y como se especifica en el parámetro de plantilla.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que la propiedad de un objeto ha cambiado o está a punto de cambiar.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para los puntos de conexión de un objeto COM ATL. Estos puntos de conexión se asignan a una asignación de receptor de eventos, proporcionada por el objeto COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el mapa del receptor de eventos en la clase para enrutar los eventos a la función de controlador adecuada.

## <a name="see-also"></a>Vea también

[Punto de conexión](../atl/atl-connection-points.md)
