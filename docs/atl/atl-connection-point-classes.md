---
title: Clases de puntos de conexión ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CFirePropNotifyEvent class, connection point classes
- connection points [C++], ATL classes
- ATL, connection points
- CComDynamicUnkArray class, connection point classes
- CFirePropNotifyEvent class
- CComUnkArray class, connection point classes
ms.assetid: 9582ba71-7ace-4df4-9c9b-1b0636953efc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 141142db5dff185cf4f8a0ad42c4b322e7d7739a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43763885"
---
# <a name="atl-connection-point-classes"></a>Clases de puntos de conexión ATL

ATL utiliza las siguientes clases para admitir puntos de conexión:

- [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) implementa un punto de conexión. El IID de la interfaz de salida que representa se pasa como un parámetro de plantilla.

- [IConnectionPointContainerImpl](../atl/reference/iconnectionpointcontainerimpl-class.md) implementa el contenedor de punto de conexión y administra la lista de `IConnectionPointImpl` objetos.

- [IPropertyNotifySinkCP](../atl/reference/ipropertynotifysinkcp-class.md) implementa un punto de conexión que representa el [IPropertyNotifySink](/windows/desktop/api/ocidl/nn-ocidl-ipropertynotifysink) interfaz.

- [CComDynamicUnkArray](../atl/reference/ccomdynamicunkarray-class.md) administra un número arbitrario de conexiones entre el punto de conexión y sus receptores.

- [CComUnkArray](../atl/reference/ccomunkarray-class.md) administra un número predefinido de conexiones según lo especificado por el parámetro de plantilla.

- [CFirePropNotifyEvent](../atl/reference/cfirepropnotifyevent-class.md) notifica al receptor de un cliente que ha cambiado una propiedad del objeto o que va a cambiar.

- [IDispEventImpl](../atl/reference/idispeventimpl-class.md) proporciona compatibilidad para puntos de conexión para un objeto COM de ATL. Estos puntos de conexión se asignan mediante un mapa de receptor de eventos, que se proporciona mediante el objeto COM.

- [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) funciona junto con el mapa de receptores de eventos en la clase para enrutar eventos a la función de controlador adecuado.

## <a name="see-also"></a>Vea también

[Punto de conexión](../atl/atl-connection-points.md)

