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
ms.openlocfilehash: 129b805379fa68cb4f50ee1f8e3ac7d1b725d9ec
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622325"
---
# <a name="mfc-activex-controls-events"></a>Controles ActiveX MFC: Eventos

Los controles ActiveX utilizan eventos para notificar a un contenedor que se ha producido algo en el control. Entre los ejemplos comunes de eventos se incluyen los clics en el control, los datos especificados mediante el teclado y los cambios en el estado del control. Cuando se producen estas acciones, el control activa un evento para alertar al contenedor.

Los eventos también se denominan mensajes.

MFC admite dos tipos de eventos: estándar y personalizado. Los eventos estándar son aquellos que la clase [COleControl](reference/colecontrol-class.md) controla automáticamente. Para obtener una lista completa de eventos estándar, vea el artículo [controles ActiveX de MFC: agregar eventos estándar](mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Los eventos personalizados permiten un control de la capacidad de notificar al contenedor cuando se produce una acción específica de ese control. Algunos ejemplos serían un cambio en el estado interno de un control o recepción de un mensaje de ventana determinado.

Para que el control Active los eventos correctamente, la clase de control debe asignar cada evento del control a una función miembro a la que se debe llamar cuando se produzca el evento relacionado. Este mecanismo de asignación (denominado mapa de eventos) centraliza la información sobre el evento y permite a Visual Studio acceder fácilmente a los eventos del control y manipularlos. Esta asignación de eventos se declara mediante la siguiente macro, ubicada en el encabezado (. H) de la declaración de clase del control:

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

Una vez declarado el mapa de eventos, debe definirse en la implementación del control (. CPP). Las siguientes líneas de código definen el mapa de eventos, lo que permite que el control Active eventos específicos:

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Si usa el Asistente para controles ActiveX de MFC para crear el proyecto, agrega automáticamente estas líneas. Si no usa el Asistente para controles ActiveX MFC, debe agregar estas líneas manualmente.

Con Vista de clases, puede agregar eventos estándar que admiten `COleControl` los eventos de clase o personalizados que defina. Para cada nuevo evento, Vista de clases agrega automáticamente la entrada adecuada al mapa de eventos del control y al del control. Archivo IDL.

En otros dos artículos se describen los eventos en detalle:

- [Controles ActiveX MFC: agregar eventos estándar](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Controles ActiveX MFC: Agregar eventos personalizados](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)
