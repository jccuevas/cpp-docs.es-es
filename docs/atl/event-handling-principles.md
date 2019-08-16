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
ms.openlocfilehash: 066c8db60afed31ceba1c9ef6f4a10d5f842e608
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492141"
---
# <a name="event-handling-principles"></a>Principios de control de eventos

Hay tres pasos comunes para todo el control de eventos. Tendrá que:

- Implemente la interfaz de eventos en el objeto.

- Notificar al origen de eventos que el objeto desea recibir eventos.

- Desaconseje el origen del evento cuando el objeto ya no necesite recibir eventos.

La forma en que se implementará la interfaz de eventos dependerá de su tipo. Una interfaz de eventos puede ser vtable, dual o dispinterface. Depende del diseñador del origen de eventos definir la interfaz; depende de usted implementar la interfaz.

> [!NOTE]
>  Aunque no hay ninguna razón técnica para que una interfaz de eventos no sea dual, hay una serie de razones de diseño adecuadas para evitar el uso de duales. Sin embargo, se trata de una decisión tomada por el diseñador o implementador del *origen*del evento. Puesto que está trabajando desde la perspectiva del evento `sink`, debe permitir la posibilidad de que no tenga ninguna opción, pero para implementar una interfaz de eventos duales. Para obtener más información sobre interfaces duales, vea [interfaces duales y ATL](../atl/dual-interfaces-and-atl.md).

El asesoramiento del origen de eventos se puede dividir en tres pasos:

- Consulte el objeto de origen para [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Llame a [IConnectionPointContainer:: FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) pasando el IID de la interfaz de eventos que le interese. Si se realiza correctamente, devolverá la interfaz [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) en un objeto de punto de conexión.

- Llame a [IConnectionPoint::](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) Advise `IUnknown` pasando el del receptor de eventos. Si se realiza correctamente, devolverá una `DWORD` cookie que representa la conexión.

Una vez que haya registrado correctamente su interés en la recepción de eventos, se llamará a los métodos de la interfaz de eventos del objeto según los eventos desencadenados por el objeto de origen. Cuando ya no necesite recibir eventos, puede volver a pasar la cookie al punto de conexión mediante [IConnectionPoint::](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)unaconseje. Esto interrumpirá la conexión entre el origen y el receptor.

Tenga cuidado de evitar ciclos de referencia al controlar eventos.

## <a name="see-also"></a>Vea también

[Control de eventos](../atl/event-handling-and-atl.md)
