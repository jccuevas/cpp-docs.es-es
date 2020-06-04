---
title: Principios de control de eventos (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319565"
---
# <a name="event-handling-principles"></a>Principios de manejo de eventos

Hay tres pasos comunes a todo el control de eventos. Usted tendrá que:

- Implemente la interfaz de eventos en el objeto.

- Aconseje al origen de eventos que el objeto desea recibir eventos.

- Desavisar el origen de eventos cuando el objeto ya no necesite recibir eventos.

La forma en que implementará la interfaz de eventos dependerá de su tipo. Una interfaz de eventos puede ser vtable, dual o dispinterface. Depende del diseñador del origen de eventos definir la interfaz; depende de usted implementar esa interfaz.

> [!NOTE]
> Aunque no hay razones técnicas por las que una interfaz de eventos no puede ser dual, hay una serie de buenas razones de diseño para evitar el uso de duales. Sin embargo, se trata de una decisión tomada por el diseñador/implementador del *origen*del evento. Puesto que está trabajando desde `sink`la perspectiva del evento, debe permitir la posibilidad de que no tenga otra opción que implementar una interfaz de eventos dual. Para obtener más información sobre las interfaces duales, consulte [Interfaces duales y ATL.](../atl/dual-interfaces-and-atl.md)

El asesoramiento al origen del evento se puede dividir en tres pasos:

- Consulte el objeto de origen para [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Llame a [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) pasando el IID de la interfaz de eventos que le interesa. Si se realiza correctamente, se devolverá la interfaz [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) en un objeto de punto de conexión.

- Llame a [IConnectionPoint::Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) pasando el `IUnknown` receptor de eventos. Si se realiza correctamente, se devolverá una `DWORD` cookie que representa la conexión.

Una vez que haya registrado correctamente su interés en recibir eventos, se llamará a los métodos de la interfaz de eventos del objeto según los eventos desencadenados por el objeto de origen. Cuando ya no necesite recibir eventos, puede devolver la cookie al punto de conexión a través de [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise). Esto interrumpirá la conexión entre el origen y el receptor.

Tenga cuidado de evitar ciclos de referencia al controlar eventos.

## <a name="see-also"></a>Consulte también

[Manejo de eventos](../atl/event-handling-and-atl.md)
