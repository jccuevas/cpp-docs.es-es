---
title: 'Controles ActiveX MFC: Agregar eventos estándar a un control ActiveX'
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: a97c08baaf3c11b0436e52bb4fd4ac380999d69a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615592"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Controles ActiveX MFC: Agregar eventos estándar a un control ActiveX

Los eventos estándar se diferencian de los eventos personalizados en que los desencadena automáticamente la clase [COleControl](reference/colecontrol-class.md). `COleControl`contiene funciones miembro predefinidas que desencadenan eventos resultantes de acciones comunes. Algunas de las acciones comunes implementadas por `COleControl` incluyen los dos clics únicos en el control, los eventos de teclado y los cambios en el estado de los botones del mouse. Las entradas del mapa de eventos para los eventos estándar siempre van precedidas del prefijo EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Eventos estándar admitidos por el Asistente para agregar eventos

La `COleControl` clase proporciona diez eventos estándar, que se muestran en la tabla siguiente. Puede especificar los eventos que desee en el control mediante el [Asistente para agregar eventos](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Eventos estándar

|Evento|Función de activación|Comentarios|
|-----------|---------------------|--------------|
|Haga clic|**void FireClick ()**|Se desencadena cuando el control captura el mouse, se recibe el mensaje **BUTTONUP** (izquierda, central o derecha) y el botón se suelta sobre el control. Los eventos MouseDown y MouseUp de stock se producen antes de este evento.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_CLICK ()**|
|DblClick|**void FireDblClick ()**|Similar a hacer clic, pero se desencadena cuando se recibe un mensaje **BUTTONDBLCLK** .<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_DBLCLICK ()**|
|Error|**void FireError ((SCODE***SCODE* **, LPCSTR** `lpszDescription` **, uint** `nHelpID` **= 0)**        |Se desencadena cuando se produce un error dentro del control ActiveX fuera del ámbito de una llamada al método o acceso a una propiedad.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_ERROREVENT ()**|
|KeyDown|**void FireKeyDown (Short** `nChar` **, Short** `nShiftState` **)**      |Se desencadena cuando `WM_SYSKEYDOWN` `WM_KEYDOWN` se recibe un mensaje o.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_KEYDOWN ()**|
|KeyPress|**void FireKeyPress (Short** <strong>\*</strong> `pnChar` **)**    |Se desencadena cuando `WM_CHAR` se recibe un mensaje.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_KEYPRESS ()**|
|KeyUp|**void FireKeyUp (Short** `nChar` **, Short** `nShiftState` **)**      |Se desencadena cuando `WM_SYSKEYUP` `WM_KEYUP` se recibe un mensaje o.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_KEYUP ()**|
|Eventos|**void FireMouseDown (Short** `nButton` **, Short** `nShiftState` **, Float***x* **, Float***y***)**          |Se desencadena si se recibe cualquier **BUTTONDOWN** (izquierda, central o derecha). El mouse se captura inmediatamente antes de que se desencadene este evento.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_MOUSEDOWN ()**|
|MouseMove|**void FireMouseMove (Short** `nButton` **, Short** `nShiftState` **, Float***x* **, Float***y***)**          |Se desencadena cuando se recibe un mensaje de WM_MOUSEMOVE.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_MOUSEMOVE ()**|
|MouseUp|**void FireMouseUp (Short** `nButton` **, Short** `nShiftState` **, Float***x* **, Float***y***)**          |Se desencadena si se recibe cualquier **BUTTONUP** (izquierda, central o derecha). La captura del mouse se libera antes de que se desencadene este evento.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_MOUSEUP ()**|
|ReadyStateChange|**void FireReadyStateChange ()**|Se desencadena cuando un control realiza la transición al siguiente estado preparado debido a la cantidad de datos recibidos.<br /><br /> Entrada de mapa de eventos: **EVENT_STOCK_READYSTATECHANGE ()**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Agregar un evento estándar mediante el Asistente para agregar eventos

La adición de eventos estándar requiere menos trabajo que agregar eventos personalizados porque la clase base controla automáticamente la activación del evento real `COleControl` . El procedimiento siguiente agrega un evento estándar a un control desarrollado mediante el [Asistente para controles ActiveX MFC](reference/mfc-activex-control-wizard.md). El evento, denominado KeyPress, se desencadena cuando se presiona una tecla y el control está activo. Este procedimiento también se puede usar para agregar otros eventos estándar. Sustituya el nombre del evento bursátil seleccionado por KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Para agregar el evento estándar KeyPress mediante el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En Vista de clases, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En la lista desplegable **nombre de evento** , seleccione `KeyPress` .

1. Haga clic en **Finalizar**

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Cambios del Asistente para agregar eventos para eventos estándar

Dado que la clase base del control controla los eventos estándar, el Asistente para agregar eventos no cambia la declaración de clase de ningún modo. Agrega el evento al mapa de eventos del control y crea una entrada en su. Archivo IDL. La línea siguiente se agrega al mapa de eventos del control, que se encuentra en la implementación de la clase de control (. CPP):

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Al agregar este código, se desencadena un evento KeyPress cuando se recibe un mensaje de WM_CHAR y el control está activo. El evento KeyPress se puede desencadenar en otros momentos llamando a su función de activación (por ejemplo, `FireKeyPress` ) desde el código de control.

El Asistente para agregar eventos agrega la siguiente línea de código al del control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Esta línea asocia el evento KeyPress a su identificador de envío estándar y permite que el contenedor Anticipe el evento KeyPress.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)
