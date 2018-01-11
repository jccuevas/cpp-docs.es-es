---
title: "Controles ActiveX MFC: Agregar eventos estándar a un Control ActiveX | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 99de785bba9f566c5dbb4751f788320b96782427
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>Controles ActiveX MFC: Agregar eventos estándar a un control ActiveX
Eventos estándar se diferencian de los eventos personalizados en que se activan automáticamente por clase [COleControl](../mfc/reference/colecontrol-class.md). `COleControl`contiene funciones miembro predefinidas que activan eventos resultantes de acciones comunes. Algunas acciones comunes implementadas por `COleControl` incluir solo - y doble - clicks en el control, los eventos de teclado y los cambios en el estado de los botones del mouse. Entradas del mapa de eventos para eventos estándar siempre están precedidas por la **EVENT_STOCK** prefijo.  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a>Eventos estándar admitidos por el Asistente para agregar eventos  
 La `COleControl` clase proporciona diez eventos estándar, que aparecen en la tabla siguiente. Puede especificar los eventos que desee en el control mediante la [Asistente para agregar eventos](../ide/add-event-wizard.md).  
  
### <a name="stock-events"></a>Eventos estándar  
  
|evento|Función de activación|Comentarios|  
|-----------|---------------------|--------------|  
|Clic|**void FireClick)**|Se desencadena cuando el control captura el mouse, cualquier **BUTTONUP** se recibe el mensaje (izquierdo, central o derecho) y se suelta el botón sobre el control. El estándar MouseDown y MouseUp eventos se producen antes de este evento.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_CLICK)**|  
|DblClick|**void FireClick)**|Similar a Click, pero activa cuando un **BUTTONDBLCLK** recibirlo.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_DBLCLICK)**|  
|Error|**void FireError (SCODE***scode* **, LPCSTR** `lpszDescription` **, UINT**`nHelpID`**= 0)** |Se desencadena cuando se produce un error en el control ActiveX fuera del ámbito de un acceso de propiedad o llamada de método.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_ERROREVENT)**|  
|KeyDown|**void FireKeyDown (short** `nChar` **, short**`nShiftState`**)** |Se desencadena cuando una `WM_SYSKEYDOWN` o `WM_KEYDOWN` recibirlo.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_KEYDOWN)**|  
|KeyPress|**void FireKeyPress (short\***`pnChar`**)** |Se desencadena cuando una `WM_CHAR` recibirlo.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_KEYPRESS)**|  
|KeyUp|**void FireKeyDown (short** `nChar` **, short**`nShiftState`**)** |Se desencadena cuando una `WM_SYSKEYUP` o `WM_KEYUP` recibirlo.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_KEYUP)**|  
|MouseDown|**void FireMouseDown (short** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Se desencadena si cualquier **BUTTONDOWN** (izquierda, centro o derecha) que se recibe. El mouse se captura inmediatamente antes de que se desencadena este evento.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_MOUSEDOWN)**|  
|MouseMove|**void FireMouseDown (short** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Se desencadena cuando una `WM_MOUSEMOVE` recibirlo.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_MOUSEMOVE)**|  
|MouseUp|**void FireMouseDown (short** `nButton` **, short** `nShiftState` **, float***x* **, float** *y***)** |Se desencadena si cualquier **BUTTONUP** (izquierda, centro o derecha) que se recibe. La captura del mouse se libera antes de que se desencadena este evento.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_MOUSEUP)**|  
|ReadyStateChange|**void FireReadyStateChange)**|Se desencadena cuando un control vaya hasta el siguiente estado preparado debido a la cantidad de datos recibidos.<br /><br /> Entrada del mapa de eventos: **EVENT_STOCK_READYSTATECHANGE)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a>Agrega un evento estándar mediante el Asistente para agregar eventos  
 Agregar eventos estándar requiere menos trabajo que agregar eventos personalizados, porque la activación del evento real se controla automáticamente por la clase base, `COleControl`. El siguiente procedimiento agrega un evento estándar a un control que se desarrolló utilizando [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md). El evento, denominado KeyPress, se desencadena cuando se presiona una tecla y el control está activo. Este procedimiento también se puede utilizar para agregar otros eventos estándar. Sustituya el nombre de evento estándar seleccionado por KeyPress.  
  
#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>Para agregar el evento estándar KeyPress mediante el Asistente para agregar eventos  
  
1.  Cargue el proyecto del control.  
  
2.  En la vista de clases, haga clic en la clase del control ActiveX para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **agregar** y, a continuación, haga clic en **Agregar evento**.  
  
     Se abrirá al Asistente para agregar eventos.  
  
4.  En el **nombre del evento** lista desplegable, seleccione `KeyPress`.  
  
5.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a>Agregar los cambios del Asistente para eventos de eventos estándar  
 Ya eventos estándar están controlados por la clase base del control, el Asistente para agregar eventos no cambia la declaración de clase de ninguna manera. Agrega el evento al mapa de eventos del control y crea una entrada en su. Este archivo IDL. Se agrega la siguiente línea al mapa de eventos del control, situado en la implementación de la clase de control (. Archivo CPP):  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Agregar este código desencadena un evento KeyPress cuando un `WM_CHAR` se recibe el mensaje y el control está activo. El evento KeyPress puede activarse en otras ocasiones, llamando a su función de activación (por ejemplo, `FireKeyPress`) desde el código del control.  
  
 El Asistente para agregar eventos, se agrega la siguiente línea de código para el control. Este archivo IDL:  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Esta línea asocia el evento KeyPress con su identificador de envío estándar y permite al contenedor prever el evento KeyPress.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX de MFC: métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl (clase)](../mfc/reference/colecontrol-class.md)
