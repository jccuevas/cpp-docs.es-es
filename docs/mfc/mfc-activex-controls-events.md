---
title: 'Controles ActiveX MFC: Eventos'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 0d8a881d07a3e48673c6dc3298816d165273be0d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57276772"
---
# <a name="mfc-activex-controls-events"></a>Controles ActiveX MFC: Eventos

Controles ActiveX usar eventos para notificar a un contenedor que ha sucedido algo al control. Algunos ejemplos comunes de los eventos son los clics en el control, los datos introducidos mediante el teclado y los cambios en el estado del control. Cuando se producen estas acciones, el control activa un evento para generar una alerta en el contenedor.

Los eventos también se denominan mensajes.

MFC admite dos tipos de eventos: estándar y personalizados. Los eventos estándar son los eventos que la clase [COleControl](../mfc/reference/colecontrol-class.md) controla automáticamente. Para obtener una lista completa de eventos estándar, consulte el artículo [controles ActiveX MFC: Agregar eventos estándar](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Eventos personalizados permiten un control de la capacidad notificar al contenedor cuando se produce una acción específica en ese control. Algunos ejemplos serían un cambio en el estado interno de un control o la recepción de un determinado mensaje de ventana.

Para que el control desencadenar eventos correctamente, la clase del control debe asignar cada evento del control a una función miembro que se debe llamar cuando se produce el evento relacionado. Este mecanismo de asignación (denominado un mapa de eventos) centraliza la información sobre el evento y permite que Visual Studio fácilmente tener acceso y manipular los eventos del control. Este mapa de eventos se declara mediante la siguiente macro, ubicada en el encabezado (. H) archivo de de la declaración de clase de control:

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

Después de que se ha declarado el mapa de eventos, debe definirse en la implementación del control (. Archivo CPP). Las siguientes líneas de código definen el mapa de eventos, lo que permite al control activar eventos específicos:

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Si usa al Asistente para controles de ActiveX de MFC para crear el proyecto, agrega automáticamente estas líneas. Si no usa al Asistente para controles de ActiveX de MFC, debe agregar estas líneas manualmente.

Con la vista de clases, puede agregar eventos estándar compatibles con la clase `COleControl` o eventos personalizados que defina. Para cada nuevo evento, vista de clases agrega automáticamente la entrada adecuada para el mapa de eventos del control y el control. Archivo IDL.

Dos artículos describen los eventos en detalle:

- [Controles ActiveX MFC: Agregar eventos estándar](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Controles ActiveX MFC: Agregar eventos personalizados](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
