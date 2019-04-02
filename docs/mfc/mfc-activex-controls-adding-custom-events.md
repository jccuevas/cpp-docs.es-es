---
title: 'Controles ActiveX MFC: Agregar eventos personalizados'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
ms.openlocfilehash: 48c5ddbc8a3bcf6f74c251820e83cdebcef05bc9
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58781008"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Controles ActiveX MFC: Agregar eventos personalizados

Eventos personalizados se diferencian de los eventos estándar en que no se activan automáticamente mediante la clase `COleControl`. Un evento personalizado reconoce una acción determinada, determinada por el desarrollador del control, como un evento. Las entradas del mapa de eventos para los eventos personalizados se representan mediante la macro EVENT_CUSTOM. En la sección siguiente implementa un evento personalizado para un proyecto de control ActiveX que se creó mediante el Asistente para controles ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a> Agregar un evento personalizado con el Asistente para agregar eventos

El siguiente procedimiento agrega un evento personalizado específico, ClickIn. Puede usar este procedimiento para agregar otros eventos personalizados. Sustituya el nombre del evento personalizado y sus parámetros para el nombre del evento ClickIn y los parámetros.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Para agregar el evento personalizado ClickIn mediante el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En la vista de clases, haga clic en la clase del control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar evento**.

   Se abrirá al Asistente para agregar eventos.

1. En el **nombre de evento** cuadro, primero seleccione cualquier evento existente y luego haga clic en el **personalizado** radio botón y, después, escriba *ClickIn*.

1. En el **nombre interno** , escriba el nombre de función de activación del evento. En este ejemplo, utilice el valor predeterminado proporcionado por el Asistente para agregar eventos (`FireClickIn`).

1. Agregar un parámetro, llamado *xCoord* (tipo *OLE_XPOS_PIXELS*), mediante el **nombre del parámetro** y **tipo de parámetro** controles.

1. Agregar un segundo parámetro, llamado *yCoord* (tipo *OLE_YPOS_PIXELS*).

1. Haga clic en **finalizar** para crear el evento.

##  <a name="_core_classwizard_changes_for_custom_events"></a> Agregar evento cambios del Asistente para eventos personalizados

Cuando se agrega un evento personalizado, el Asistente para agregar eventos realiza cambios en la clase de control. H. CPP, y. Archivos IDL. Ejemplos de código siguientes son específicos para el evento ClickIn.

Las líneas siguientes se agregan al encabezado (. H) archivo de de la clase del control:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Este código declara una función inline denominada `FireClickIn` que llama a [a COleControl:: FireEvent](../mfc/reference/colecontrol-class.md#fireevent) con el evento ClickIn y los parámetros definidos mediante el Asistente para agregar eventos.

Además, se agrega la siguiente línea al mapa de eventos para el control, situado en la implementación (. Archivo CPP) de la clase del control:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Este código asigna el evento ClickIn a la función insertada `FireClickIn`, pasando los parámetros definidos mediante el Asistente para agregar eventos.

Por último, se agrega la siguiente línea a su control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Esta línea asigna a un número de Id. específico, que se toman de la posición del evento en la lista de eventos del Asistente para agregar eventos de ClickIn (evento). La entrada en la lista de eventos permite que un contenedor prever el evento. Por ejemplo, puede proporcionar el código del controlador que se ejecuta cuando se desencadena el evento.

##  <a name="_core_calling_fireclickin"></a> Llamar a FireClickIn

Ahora que ha agregado el evento personalizado ClickIn mediante el Asistente para agregar eventos, debe decidir cuando este evento está en activarse. Para ello, una llamada a `FireClickIn` cuando se produce la acción apropiada. Para este análisis, el control utiliza el `InCircle` función dentro de un controlador de mensajes WM_LBUTTONDOWN para desencadenar el evento ClickIn cuando un usuario hace clic dentro de una región circular o elíptica. El procedimiento siguiente agrega el controlador WM_LBUTTONDOWN.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Para agregar un controlador de mensajes con el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En la vista de clases, seleccione la clase del control ActiveX.

1. En la ventana Propiedades, haga clic en el **mensajes** botón.

   La ventana Propiedades muestra una lista de los mensajes que pueden controlarse mediante el control ActiveX. Cualquier mensaje que se muestra en negrita ya tiene una función de controlador asignada a él.

1. En la ventana Propiedades, seleccione el mensaje que desee controlar. En este ejemplo, seleccione WM_LBUTTONDOWN.

1. En el cuadro de lista desplegable de la derecha, seleccione  **\<Agregar > OnLButtonDown**.

1. Haga doble clic en la nueva función de controlador de vista de clases para saltar al código del controlador de mensaje en la implementación (. Archivo CPP) del control ActiveX.

El siguiente código de ejemplo llama a la `InCircle` función cada vez que se hace clic en el botón primario del mouse dentro de la ventana de control. En este ejemplo puede encontrarse en la función de controlador WM_LBUTTONDOWN, `OnLButtonDown`, en el [ejemplo Circ](../overview/visual-cpp-samples.md) abstracta.

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Cuando el Asistente para agregar eventos crea controladores de mensajes para las acciones de botón del mouse, se agrega automáticamente una llamada al mismo controlador de mensajes de la clase base. No quite esta llamada. Si el control utiliza cualquiera de los mensajes estándar del mouse, los controladores de mensajes en la clase base deben llamarse para asegurarse de que la captura del mouse se controlan correctamente.

En el ejemplo siguiente, el evento desencadena únicamente cuando se produce el clic dentro de una región circular o elíptica dentro del control. Para lograr este comportamiento, puede colocar el `InCircle` función en la implementación del control (. Archivo CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

También deberá agregar la siguiente declaración de la `InCircle` función al encabezado del control (. H) archivo de:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a> Eventos personalizados con nombres de cotizaciones

Puede crear eventos personalizados con el mismo nombre que los eventos estándar, sin embargo, no se pueden implementar tanto en el mismo control. Por ejemplo, es posible que desee crear un evento personalizado denominado Click que no se desencadenará cuando el evento estándar haga clic en que se desencadene. A continuación, se desencadena el evento Click en cualquier momento llamando a su función de activación.

El siguiente procedimiento agrega un clic personalizado eventos.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Para agregar un evento personalizado que utiliza un nombre de evento estándar

1. Cargue el proyecto del control.

1. En la vista de clases, haga clic en la clase del control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar evento**.

   Se abrirá al Asistente para agregar eventos.

1. En el **nombre de evento** lista desplegable, seleccione un nombre de evento estándar. En este ejemplo, seleccione **haga clic en**.

1. Para **tipo de evento**, seleccione **personalizado**.

1. Haga clic en **finalizar** para crear el evento.

1. Llamar a `FireClick` en lugares apropiados en el código.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
