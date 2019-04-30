---
title: Principios (ATL) de control de eventos
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: b882a1d356a431f75be1feb6e7bd997abed41c33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234776"
---
# <a name="event-handling-principles"></a>Principios de control de eventos

Hay tres pasos comunes a todo el control de eventos. Necesitará:

- Implemente la interfaz de eventos en el objeto.

- Notificar al origen de eventos que su objeto quiere recibir eventos.

- No notificar el origen del evento cuando el objeto ya no necesita recibir eventos.

La forma en que se implementa la interfaz de eventos dependerá de su tipo. Una interfaz de eventos puede ser vtable, una interfaz dispinterface o doble. Resulta al diseñador del origen del evento para definir la interfaz; depende de cómo implementar esa interfaz.

> [!NOTE]
>  Aunque no hay ninguna razón técnica que una interfaz de eventos no puede ser dual, hay una serie de motivos de buen diseño para evitar el uso de duales. Sin embargo, esto es una decisión realizada por el diseñador o implementador del evento *origen*. Puesto que trabaja desde la perspectiva del evento `sink`, necesario para permitir la posibilidad de que no puede tener cualquier elección, pero para implementar una interfaz de evento dual. Para obtener más información sobre interfaces duales, consulte [Interfaces duales y ATL](../atl/dual-interfaces-and-atl.md).

El origen del evento que avisa de puede dividirse en tres pasos:

- Consultar el objeto de origen para [IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Llame a [IConnectionPointContainer:: FindConnectionPoint](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) pasando el IID de la interfaz de eventos que le interese. Si es correcto, se devolverá el [IConnectionPoint](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpoint) interfaz en un objeto de punto de conexión.

- Llame a [IConnectionPoint:: Advise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-advise) pasando el `IUnknown` del receptor de eventos. Si es correcto, esto devolverá un `DWORD` cookie que representa la conexión.

Una vez que se ha registrado correctamente su interés en recibir eventos, métodos de interfaz de eventos del objeto llamará según los eventos desencadenados por el objeto de origen. Cuando ya no necesite recibir eventos, puede pasar la cookie de vuelta al punto de conexión a través de [IConnectionPoint:: Unadvise](/windows/desktop/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Esto interrumpirá la conexión entre el origen y receptor.

Tenga cuidado para evitar la referencia de los ciclos al control de eventos.

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)
