---
title: "Controles ActiveX MFC: Agregar eventos est&#225;ndar a un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EVENT__STOCK_ERROR"
  - "EVENT__STOCK_READYSTATECHANGE"
  - "ReadyStateChange"
  - "EVENT__STOCK_MOUSEMOVE"
  - "EVENT__STOCK_MOUSEUP"
  - "EVENT__STOCK_DBLCLICK"
  - "KeyPress"
  - "EVENT__STOCK_KEYDOWN"
  - "EVENT__STOCK"
  - "EVENT__STOCK_MOUSEDOWN"
  - "EVENT__STOCK_KEYPRESS"
  - "EVENT__STOCK_CLICK"
  - "EVENT__STOCK_KEYUP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EVENT_STOCK (prefijo)"
  - "EVENT_STOCK_CLICK (evento)"
  - "EVENT_STOCK_DBLCLICK (evento)"
  - "EVENT_STOCK_ERROREVENT (evento)"
  - "EVENT_STOCK_KEYDOWN (evento)"
  - "EVENT_STOCK_KEYPRESS (evento)"
  - "EVENT_STOCK_KEYPRESS (macro)"
  - "EVENT_STOCK_KEYUP (evento)"
  - "EVENT_STOCK_MOUSEDOWN (evento)"
  - "EVENT_STOCK_MOUSEMOVE (evento)"
  - "EVENT_STOCK_MOUSEUP (evento)"
  - "EVENT_STOCK_READYSTATECHANGE (evento)"
  - "eventos [C++], estándar"
  - "FireClick (evento)"
  - "FireDblClick (evento)"
  - "FireError (evento)"
  - "FireKeyDown (evento)"
  - "FireKeyPress (evento)"
  - "FireKeyUp (evento)"
  - "FireMouseDown (evento)"
  - "FireMouseMove (evento)"
  - "FireMouseUp (evento)"
  - "KeyPress (evento)"
  - "controles ActiveX en MFC, eventos"
  - "ReadyStateChange (evento)"
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Controles ActiveX MFC: Agregar eventos est&#225;ndar a un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Eventos comunes difieren de eventos personalizados de que automáticamente son desencadenados por la clase [COleControl](../mfc/reference/colecontrol-class.md).  `COleControl` contiene el miembro predefinido funciona que los eventos fire resultando de acciones comunes.  Algunas acciones comunes implementados por `COleControl` incluyen único y doble clic en el control, los eventos de teclado, y cambios en el estado de los botones del mouse.  Las entradas del mapa de eventos para eventos comunes son precedidas siempre al prefijo de **EVENT\_STOCK** .  
  
##  <a name="_core_stock_events_supported_by_classwizard"></a> Eventos comunes admitidos por el asistente para agregar eventos  
 La clase de `COleControl` proporciona diez eventos comunes, incluidos en la tabla siguiente.  Puede especificar los eventos que desee en el control con [Asistente para agregar eventos](../ide/add-event-wizard.md).  
  
### Eventos comunes  
  
|Evento|Desencadenar la función|Comentarios|  
|------------|-----------------------------|-----------------|  
|Haga clic en|**FireClick vacío \(\)**|Se desencadena cuando el control captura el mouse, se recibe los mensajes de **BUTTONUP** \(se, centro, o derecha\), y el botón se libera sobre el control.  Eventos comunes MouseDown y de MouseUp aparecen antes de este evento.<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_CLICK\( \)**|  
|DblClick|**FireDblClick vacío \(\)**|Similar al clic pero se desencadena cuando se recibe un mensaje de **BUTTONDBLCLK** .<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_DBLCLICK\( \)**|  
|Error|*scode* **, LPCSTR**  `lpszDescription` **, UINT**  `nHelpID`  **\= 0 \)**de**void FireError\( SCODE**|Se desencadena cuando se produce un error dentro del control ActiveX fuera del ámbito de una llamada al método o un acceso de propiedad.<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_ERROREVENT\( \)**|  
|KeyDown|**void FireKeyDown\( short**  `nChar` **, short**  `nShiftState`  **\)**|Se desencadena cuando se recibe un mensaje de `WM_SYSKEYDOWN` o de `WM_KEYDOWN` .<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_KEYDOWN\( \)**|  
|KeyPress|**void FireKeyPress\( short\***  `pnChar`  **\)**|Se desencadena cuando se recibe un mensaje de `WM_CHAR` .<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_KEYPRESS\( \)**|  
|KeyUp|**void FireKeyUp\( short**  `nChar` **, short**  `nShiftState`  **\)**|Se desencadena cuando se recibe un mensaje de `WM_SYSKEYUP` o de `WM_KEYUP` .<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_KEYUP\( \)**|  
|MouseDown|*y*  **\)**de**void FireMouseDown\( short** `nButton`**, short** `nShiftState`**, float** *x***, float**|Desencadena si cualquier **BUTTONDOWN** \(izquierda, centro, o derecha\) se reciben.  Se captura el mouse inmediatamente antes de que se desencadena este evento.<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_MOUSEDOWN\( \)**|  
|MouseMove|*y*  **\)**de**void FireMouseMove\( short** `nButton`**, short** `nShiftState`**, float** *x***, float**|Se desencadena cuando se recibe un mensaje de `WM_MOUSEMOVE` .<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_MOUSEMOVE\( \)**|  
|MouseUp|*y*  **\)**de**void FireMouseUp\( short** `nButton`**, short** `nShiftState`**, float** *x***, float**|Desencadena si cualquier **BUTTONUP** \(izquierda, centro, o derecha\) se reciben.  Se libera la captura del mouse antes de que se desencadene este evento.<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_MOUSEUP\( \)**|  
|ReadyStateChange|**FireReadyStateChange vacío \(\)**|Se desencadena cuando las transiciones de un control al estado listo siguiente debido a la cantidad de datos recibieron.<br /><br /> Entrada de asignación de eventos: **EVENT\_STOCK\_READYSTATECHANGE\( \)**|  
  
##  <a name="_core_adding_a_stock_event_using_classwizard"></a> Agregando un evento común Con el asistente para agregar eventos  
 Agregar eventos comunes requiere menos trabajo que los eventos personalizados porque el desencadenamiento de evento real controla automáticamente por la clase base, `COleControl`de suma.  El procedimiento siguiente se agrega un evento común a un control desarrollado mediante [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md).  El evento, denominado KeyPress, se desencadena cuando se presiona una tecla y el control está activo.  Este procedimiento se puede utilizar para agregar otros eventos comunes.  Sustituya el nombre de evento común seleccionado para KeyPress.  
  
#### Para agregar el a que almacene el evento mediante el asistente para agregar eventos  
  
1.  Cargue el proyecto de control.  
  
2.  En la vista de clases, haga clic con el botón secundario en la clase de control ActiveX para abrir el menú contextual.  
  
3.  En el menú contextual, haga clic en **Add** y haga clic en **Agregar evento**.  
  
     Se abrirá el asistente para agregar eventos.  
  
4.  En la lista desplegable de **Nombre de evento** , seleccione `KeyPress`.  
  
5.  Haga clic en **Finalizar**.  
  
##  <a name="_core_classwizard_changes_for_stock_events"></a> Agregue los cambios del asistente de eventos para eventos comunes  
 Como los eventos comunes son controlados por la clase base de controles, el asistente para agregar eventos no cambia la declaración de clase de ningún modo.  Agrega el evento al evento de control asignado y crea una entrada en el archivo de .IDL.  La siguiente línea se agrega al mapa del evento de control, ubicado en el archivo de implementación de la clase control \(.CPP\):  
  
 [!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]  
  
 Agregar este código desencadena un evento KeyPress cuando se recibe un mensaje de `WM_CHAR` y el control está activo.  El evento KeyPress posible desencadenador en otros momentos llamando a la función bounce \(por ejemplo, `FireKeyPress`\) dentro de código.  
  
 El asistente para agregar eventos agrega la siguiente línea de código al archivo de .IDL de control:  
  
 [!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/CPP/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]  
  
 Esta línea asocia el eventos KeyPress a su identificador estándar send y permite que el contenedor prever el evento KeyPress.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX MFC: Métodos](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)