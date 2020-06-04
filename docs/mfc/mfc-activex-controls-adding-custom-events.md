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
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364731"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Controles ActiveX MFC: Agregar eventos personalizados

Los eventos personalizados difieren de los eventos `COleControl`de stock en que no se desencadenan automáticamente por clase. Un evento personalizado reconoce una acción determinada, determinada por el desarrollador del control, como un evento. Las entradas del mapa de eventos para eventos personalizados se representan mediante la macro EVENT_CUSTOM. En la siguiente sección se implementa un evento personalizado para un proyecto de control ActiveX que se creó mediante el Asistente para controles ActiveX.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Agregar un evento personalizado con el Asistente para agregar eventos

El siguiente procedimiento agrega un evento personalizado específico, ClickIn. Puede usar este procedimiento para agregar otros eventos personalizados. Sustituya el nombre del evento personalizado y sus parámetros por el nombre y los parámetros del evento ClickIn.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Para agregar el evento personalizado ClickIn mediante el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En la vista de **clases**, haga clic con el botón derecho en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En el cuadro **Nombre** del evento, seleccione primero cualquier evento existente y, a continuación, haga clic en el botón de opción **Personalizado** y, a continuación, escriba *ClickIn*.

1. En el cuadro **Nombre interno,** escriba el nombre de la función de activación del evento. En este ejemplo, utilice el valor predeterminado`FireClickIn`proporcionado por el Asistente para agregar eventos ( ).

1. Agregue un parámetro, denominado *xCoord* (tipo *OLE_XPOS_PIXELS*), mediante los controles Nombre de **parámetro** y Tipo de **parámetro.**

1. Agregue un segundo parámetro, denominado *yCoord* (tipo *OLE_YPOS_PIXELS*).

1. Haga clic en **Finalizar** para crear el evento.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Agregar cambios del Asistente para eventos para eventos personalizados

Al agregar un evento personalizado, el Asistente para agregar eventos realiza cambios en la clase de control. H. CPP, y . Archivos IDL. Los siguientes ejemplos de código son específicos del evento ClickIn.

Las siguientes líneas se agregan al encabezado (. H) de la clase de control:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Este código declara una función en línea llamada `FireClickIn` que llama a [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) con el ClickIn eventos y parámetros definidos mediante el Asistente para agregar eventos.

Además, la siguiente línea se agrega al mapa de eventos para el control, ubicado en la implementación (. CPP) de la clase de control:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Este código asigna el evento ClickIn `FireClickIn`a la función en línea, pasando los parámetros definidos mediante el Asistente para agregar eventos.

Por último, la siguiente línea se agrega a la . Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Esta línea asigna al evento ClickIn un número de ID específico, tomado de la posición del evento en la lista de eventos del Asistente para agregar eventos. La entrada de la lista de eventos permite que un contenedor anticipe el evento. Por ejemplo, podría proporcionar código de controlador que se ejecutará cuando se desencadena el evento.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Llamando a FireClickIn

Ahora que ha agregado el evento personalizado ClickIn mediante el Asistente para agregar eventos, debe decidir cuándo se va a desencadenar este evento. Para ello, `FireClickIn` llame cuando se produzca la acción adecuada. Para esta discusión, `InCircle` el control `WM_LBUTTONDOWN` usa la función dentro de un controlador de mensajes para desencadenar el ClickIn eventos cuando un usuario hace clic dentro de una región circular o elíptica. El siguiente procedimiento `WM_LBUTTONDOWN` agrega el controlador.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Para agregar un controlador de mensajes con el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En **la vista de clases**, seleccione la clase de control ActiveX.

1. En la ventana **Propiedades,** verá una lista de mensajes que puede controlar el control ActiveX. Cualquier mensaje que se muestre en negrita ya tiene una función de controlador asignada.

1. Seleccione el mensaje que desea controlar. Para este ejemplo, seleccione `WM_LBUTTONDOWN`.

1. En el cuadro de lista desplegable de la derecha, seleccione ** \<Agregar> OnLButtonDown**.

1. Haga doble clic **en** la nueva función de controlador en la vista de clases para saltar al código del controlador de mensajes en la implementación (. CPP) del control ActiveX.

En el ejemplo `InCircle` de código siguiente se llama a la función cada vez que se hace clic en el botón izquierdo del mouse dentro de la ventana de control. Este ejemplo se puede `WM_LBUTTONDOWN` encontrar `OnLButtonDown`en la función de controlador, , en el resumen [de ejemplo De.](../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Cuando el Asistente para agregar eventos crea controladores de mensajes para acciones de botón del mouse, se agrega automáticamente una llamada al mismo controlador de mensajes de la clase base. No quite esta llamada. Si el control utiliza cualquiera de los mensajes del mouse de stock, se debe llamar a los controladores de mensajes de la clase base para asegurarse de que la captura del mouse se controla correctamente.

En el ejemplo siguiente, el evento se desencadena solo cuando el clic se produce dentro de una región circular o elíptica dentro del control. Para lograr este comportamiento, `InCircle` puede colocar la función en la implementación del control (. CPP) archivo:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

También tendrá que agregar la siguiente `InCircle` declaración de la función al encabezado del control (. H) archivo:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Eventos personalizados con nombres de stock

Puede crear eventos personalizados con el mismo nombre que los eventos de stock, sin embargo, no puede implementar ambos en el mismo control. Por ejemplo, es posible que desee crear un evento personalizado denominado Click que no se active cuando el evento de stock Click se activanormalmente. A continuación, puede desencadenar el Click eventos en cualquier momento mediante una llamada a su función de disparo.

El siguiente procedimiento agrega un evento Click personalizado.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Para agregar un evento personalizado que utilice un nombre de evento de stock

1. Cargue el proyecto del control.

1. En la vista de **clases**, haga clic con el botón derecho en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En la lista desplegable **Nombre del** evento, seleccione un nombre de evento de stock. Para este ejemplo, seleccione **Click**.

1. En **Tipo de evento**, seleccione **Personalizado**.

1. Haga clic en **Finalizar** para crear el evento.

1. Llame `FireClick` a los lugares apropiados en su código.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
