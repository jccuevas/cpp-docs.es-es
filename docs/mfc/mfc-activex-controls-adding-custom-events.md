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
ms.openlocfilehash: d22eb6016635c509d6b8bb2068f00125d0227ca2
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907317"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>Controles ActiveX MFC: Agregar eventos personalizados

Los eventos personalizados se diferencian de los eventos estándar en que no se activan automáticamente mediante la clase `COleControl`. Un evento personalizado reconoce una acción determinada, determinada por el desarrollador del control, como un evento. La macro EVENT_CUSTOM representa las entradas del mapa de eventos para los eventos personalizados. En la siguiente sección se implementa un evento personalizado para un proyecto de control ActiveX creado mediante el Asistente para controles ActiveX.

##  <a name="_core_adding_a_custom_event_with_classwizard"></a>Agregar un evento personalizado con el Asistente para agregar eventos

El siguiente procedimiento agrega un evento personalizado específico, haga clic en. Puede usar este procedimiento para agregar otros eventos personalizados. Sustituya el nombre del evento personalizado y sus parámetros por el nombre y los parámetros del evento click-in.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>Para agregar el evento personalizado Clickon mediante el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En **vista de clases**, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En el cuadro **nombre del evento** , seleccione primero cualquier evento existente, haga clic en el botón de opción **personalizado** y, a continuación, escriba *click*.

1. En el cuadro **nombre interno** , escriba el nombre de la función de activación del evento. En este ejemplo, use el valor predeterminado proporcionado por el Asistente para agregar eventos`FireClickIn`().

1. Agregue un parámetro, denominado *xCoord* (tipo *OLE_XPOS_PIXELS*), con los controles **nombre de parámetro** y tipo de **parámetro** .

1. Agregue un segundo parámetro, denominado *yCoord* (tipo *OLE_YPOS_PIXELS*).

1. Haga clic en **Finalizar** para crear el evento.

##  <a name="_core_classwizard_changes_for_custom_events"></a>Cambios del Asistente para agregar eventos para eventos personalizados

Al agregar un evento personalizado, el Asistente para agregar eventos realiza cambios en la clase del control. H,. CPP y. Archivos IDL. Los siguientes ejemplos de código son específicos del evento Clickon.

Las líneas siguientes se agregan al encabezado (. H) de la clase del control:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Este código declara una función insertada denominada `FireClickIn` que llama a [COleControl:: fireEvent](../mfc/reference/colecontrol-class.md#fireevent) con el evento Clickon y los parámetros definidos mediante el Asistente para agregar eventos.

Además, se agrega la línea siguiente al mapa de eventos para el control, ubicado en la implementación de (. CPP) de la clase del control:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Este código asigna el evento click en la función `FireClickIn`Inline, pasando los parámetros definidos mediante el Asistente para agregar eventos.

Por último, se agrega la línea siguiente al del control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Esta línea asigna al evento clicka un número de identificador específico, tomado de la posición del evento en la lista de eventos del Asistente para agregar eventos. La entrada en la lista de eventos permite que un contenedor prevea el evento. Por ejemplo, podría proporcionar el código de controlador que se va a ejecutar cuando se desencadene el evento.

##  <a name="_core_calling_fireclickin"></a>Llamando a FireClickIn

Ahora que ha agregado el evento personalizado Clickon mediante el Asistente para agregar eventos, debe decidir cuándo se va a desencadenar este evento. Para ello, debe llamar `FireClickIn` a cuando se produce la acción adecuada. En este debate, el control utiliza la `InCircle` función dentro de `WM_LBUTTONDOWN` un controlador de mensajes para desencadenar el evento Clickon cuando un usuario hace clic dentro de una región circular o elíptica. En el siguiente procedimiento se `WM_LBUTTONDOWN` agrega el controlador.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>Para agregar un controlador de mensajes con el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En **vista de clases**, seleccione la clase de control ActiveX.

1. En la ventana **propiedades** , verá una lista de mensajes que se pueden controlar mediante el control ActiveX. Los mensajes mostrados en negrita ya tienen una función de controlador asignada.

1. Seleccione el mensaje que desea controlar. En este ejemplo, seleccione `WM_LBUTTONDOWN`.

1. En el cuadro de lista desplegable de la derecha, seleccione  **\<agregar > OnLButtonDown**.

1. Haga doble clic en la nueva función de controlador en **vista de clases** para saltar al código del controlador de mensajes de la implementación (. CPP) del control ActiveX.

El siguiente ejemplo de código llama `InCircle` a la función cada vez que se hace clic en el botón primario del mouse dentro de la ventana del control. Este ejemplo se puede encontrar en la `WM_LBUTTONDOWN` función de controlador `OnLButtonDown`,, en el Resumen de [ejemplo Circ](../overview/visual-cpp-samples.md) .

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
>  Cuando el Asistente para agregar eventos crea controladores de mensajes para las acciones del botón del mouse, se agrega automáticamente una llamada al mismo controlador de mensajes de la clase base. No quite esta llamada. Si el control utiliza cualquiera de los mensajes del mouse estándar, se debe llamar a los controladores de mensajes de la clase base para asegurarse de que la captura del mouse se administra correctamente.

En el ejemplo siguiente, el evento solo se desencadena cuando el clic se produce dentro de una región circular o elíptica dentro del control. Para lograr este comportamiento, puede colocar la `InCircle` función en la implementación del control (. CPP):

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

También tendrá que agregar la siguiente declaración de la `InCircle` función al encabezado del control (. H):

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

##  <a name="_core_custom_events_with_stock_names"></a>Eventos personalizados con nombres de existencias

Puede crear eventos personalizados con el mismo nombre que los eventos estándar, pero no puede implementar ambos en el mismo control. Por ejemplo, puede que desee crear un evento personalizado llamado click que no se desencadene cuando el evento click de acciones se active normalmente. Después, puede activar el evento click en cualquier momento llamando a su función de activación.

El procedimiento siguiente agrega un evento click personalizado.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>Para agregar un evento personalizado que utiliza un nombre de evento bursátil

1. Cargue el proyecto del control.

1. En **vista de clases**, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En la lista desplegable **nombre de evento** , seleccione un nombre de evento estándar. En este ejemplo, seleccione **haga clic en**.

1. En **tipo de evento**, seleccione **personalizado**.

1. Haga clic en **Finalizar** para crear el evento.

1. Llame `FireClick` a en los lugares adecuados del código.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX de MFC: métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
