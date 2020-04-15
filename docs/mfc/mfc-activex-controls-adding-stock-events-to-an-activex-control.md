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
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364684"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Controles ActiveX MFC: Agregar eventos estándar a un control ActiveX

Los eventos de stock difieren de los eventos personalizados en que se desencadenan automáticamente por la clase [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`contiene funciones miembro predefinidas que desencadenan eventos resultantes de acciones comunes. Algunas acciones comunes `COleControl` implementadas por incluyen un solo clic y doble clic en el control, eventos de teclado y cambios en el estado de los botones del mouse. Las entradas de mapa de eventos para eventos de stock siempre van precedidas por el prefijo EVENT_STOCK.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Eventos de stock admitidos por el Asistente para agregar eventos

La `COleControl` clase proporciona diez eventos de stock, enumerados en la tabla siguiente. Puede especificar los eventos que desee en el control mediante el [Asistente para agregar eventos](../ide/add-event-wizard.md).

### <a name="stock-events"></a>Eventos bursátiles

|Evento|Función de disparo|Comentarios|
|-----------|---------------------|--------------|
|Haga clic en |**void FireClick( )**|Se activa cuando el control captura el mouse, se recibe cualquier mensaje **BUTTONUP** (izquierda, medio o derecha) y el botón se suelta sobre el control. Los eventos MouseDown y MouseUp de stock se producen antes de este evento.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_CLICK( )**|
|Dblclick|**void FireDblClick( )**|Similar a Click pero activado cuando se recibe un mensaje **BUTTONDBLCLK.**<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_DBLCLICK( )**|
|Error|**void FireError( SCODE***scode* **, LPCSTR** `lpszDescription` , **UINT**`nHelpID`**- 0 )**        |Se desencadena cuando se produce un error dentro del control ActiveX fuera del ámbito de una llamada al método o acceso a la propiedad.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**void FireKeyDown( short** `nChar` **, short**`nShiftState`**)**      |Se activa `WM_SYSKEYDOWN` `WM_KEYDOWN` cuando se recibe un mensaje o un mensaje.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_KEYDOWN( )**|
|Keypress|**void FireKeyPress( short** <strong>\*</strong> `pnChar` **)**    |Se activa `WM_CHAR` cuando se recibe un mensaje.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**void FireKeyUp( corto** `nChar` **, corto**`nShiftState`**)**      |Se activa `WM_SYSKEYUP` `WM_KEYUP` cuando se recibe un mensaje o un mensaje.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_KEYUP( )**|
|Mousedown|**void FireMouseDown( short** `nButton` **, short** `nShiftState` **, float***x* **, float***y***)**          |Se activa si se recibe **algún BUTTONDOWN** (izquierda, medio o derecha). El mouse se captura inmediatamente antes de que se desencadene este evento.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_MOUSEDOWN( )**|
|Mousemove|**vacío FireMouseMove( corto** `nButton` **, corto** `nShiftState` **, flotador***x* **, flotador***y***)**          |Se activa cuando se recibe un mensaje de WM_MOUSEMOVE.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_MOUSEMOVE( )**|
|MouseUp|**vacío FireMouseUp ( corto** `nButton` **, corto** `nShiftState` **, flotador***x* **, flotador***y***)**          |Se activa si se recibe **algún BUTTONUP** (izquierda, centro o derecha). La captura del mouse se libera antes de que se desencadene este evento.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|Se activa cuando un control pasa al siguiente estado listo debido a la cantidad de datos recibidos.<br /><br /> Entrada del mapa de **eventos: EVENT_STOCK_READYSTATECHANGE( )**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Adición de un evento de stock mediante el Asistente para agregar eventos

Agregar eventos de stock requiere menos trabajo que agregar eventos personalizados porque la `COleControl`clase base controla automáticamente la activación del evento real, . El siguiente procedimiento agrega un evento stock a un control que se desarrolló mediante el [Asistente para controles ActiveX](../mfc/reference/mfc-activex-control-wizard.md)de MFC. El evento, llamado KeyPress, se activa cuando se presiona una tecla y el control está activo. Este procedimiento también se puede utilizar para agregar otros eventos de stock. Sustituya el nombre del evento de stock seleccionado por KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Para agregar el evento de stock KeyPress mediante el Asistente para agregar eventos

1. Cargue el proyecto del control.

1. En la vista de clases, haga clic con el botón derecho en la clase de control ActiveX para abrir el menú contextual.

1. En el menú contextual, haga clic en **Agregar** y, a continuación, haga clic en **Agregar evento**.

   Se abrirá el Asistente para agregar eventos.

1. En la lista desplegable Nombre `KeyPress`del **evento,** seleccione .

1. Haga clic en **Finalizar**

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Agregar cambios del Asistente para eventos para eventos de stock

Dado que la clase base del control control controla los eventos de stock, el Asistente para agregar eventos no cambia la declaración de clase de ninguna manera. Agrega el evento al mapa de eventos del control y realiza una entrada en su archivo . IDL. La siguiente línea se agrega al mapa de eventos del control, ubicado en la implementación de la clase de control (. CPP) archivo:

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Agregar este código desencadena un evento KeyPress cuando se recibe un mensaje de WM_CHAR y el control está activo. El evento KeyPress se puede desencadenar en otras ocasiones `FireKeyPress`llamando a su función de activación (por ejemplo, ) desde el código de control.

El Asistente para agregar eventos agrega la siguiente línea de código al control. Archivo IDL:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Esta línea asocia el evento KeyPress con su ID de envío estándar y permite que el contenedor anticipe el evento KeyPress.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)
