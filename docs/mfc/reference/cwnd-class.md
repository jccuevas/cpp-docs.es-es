---
title: "CWnd (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWnd (clase)"
  - "window objects [C++]"
  - "windows [C++]"
ms.assetid: 49a832ee-bc34-4126-88b3-bc1d9974f6c4
caps.latest.revision: 27
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWnd (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad básica de todas las clases de ventana en la biblioteca MFC \(Microsoft Foundation Class\).  
  
## Sintaxis  
  
```  
class CWnd : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CWnd::CWnd](../Topic/CWnd::CWnd.md)|Construye un objeto `CWnd`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CWnd::accDoDefaultAction](../Topic/CWnd::accDoDefaultAction.md)|El marco llama a este método para realizar la acción predeterminada del objeto.|  
|[CWnd::accHitTest](../Topic/CWnd::accHitTest.md)|El marco llama a este método para recuperar el elemento u objeto secundario situado en un punto dado de la pantalla.|  
|[CWnd::accLocation](../Topic/CWnd::accLocation.md)|El marco llama a este método para recuperar la ubicación actual del objeto especificado en la pantalla.|  
|[CWnd::accNavigate](../Topic/CWnd::accNavigate.md)|El marco llama a este método para ir a otro elemento de la interfaz de usuario dentro de un contenedor y, si es posible, recuperar el objeto.|  
|[CWnd::accSelect](../Topic/CWnd::accSelect.md)|El marco llama a este método para modificar la selección o desplazar el foco de teclado del objeto especificado.|  
|[CWnd::AnimateWindow](../Topic/CWnd::AnimateWindow.md)|Anima el objeto de ventana asociado.|  
|[CWnd::ArrangeIconicWindows](../Topic/CWnd::ArrangeIconicWindows.md)|Organiza todas las ventanas secundarias \(iconos\) minimizadas.|  
|[CWnd::Attach](../Topic/CWnd::Attach.md)|Asocia un identificador de Windows a un objeto `CWnd`.|  
|[CWnd::BeginModalState](../Topic/CWnd::BeginModalState.md)|Llame a esta función miembro para convertir una ventana marco en modal.|  
|[CWnd::BeginPaint](../Topic/CWnd::BeginPaint.md)|Prepara `CWnd` para pintar.|  
|[CWnd::BindDefaultProperty](../Topic/CWnd::BindDefaultProperty.md)|Enlaza la propiedad enlazada simple predeterminada del objeto que llama, tal y como se indica en la biblioteca de tipos, a un cursor asociado con un control de origen de datos.|  
|[CWnd::BindProperty](../Topic/CWnd::BindProperty.md)|Enlaza una propiedad enlazada del cursor en un control enlazado a datos a un control de origen de datos, y registra dicha relación con el administrador de enlaces de MFC.|  
|[CWnd::BringWindowToTop](../Topic/CWnd::BringWindowToTop.md)|Lleva `CWnd` al principio de una pila de ventanas superpuestas.|  
|[CWnd::CalcWindowRect](../Topic/CWnd::CalcWindowRect.md)|Se llama para calcular el rectángulo de la ventana a partir del rectángulo de cliente.|  
|[CWnd::CancelToolTips](../Topic/CWnd::CancelToolTips.md)|Deshabilita el control de información sobre herramientas.|  
|[CWnd::CenterWindow](../Topic/CWnd::CenterWindow.md)|Centra una ventana con respecto a su elemento primario.|  
|[CWnd::ChangeClipboardChain](../Topic/CWnd::ChangeClipboardChain.md)|Quita `CWnd` de la cadena de visores del Portapapeles.|  
|[CWnd::CheckDlgButton](../Topic/CWnd::CheckDlgButton.md)|Pone o quita una marca de verificación al lado de un control de botón.|  
|[CWnd::CheckRadioButton](../Topic/CWnd::CheckRadioButton.md)|Selecciona el botón de radio especificado y quita la marca de verificación de los demás botones de radio en el grupo de botones especificado.|  
|[CWnd::ChildWindowFromPoint](../Topic/CWnd::ChildWindowFromPoint.md)|Determina cuál de las ventanas secundarias \(si las hay\) contiene el punto especificado.|  
|[CWnd::ClientToScreen](../Topic/CWnd::ClientToScreen.md)|Convierte a las coordenadas de cliente de un punto o rectángulo determinado en pantalla en las coordenadas de pantalla.|  
|[CWnd::CloseWindow](../Topic/CWnd::CloseWindow.md)|Minimiza la ventana.|  
|[CWnd::ContinueModal](../Topic/CWnd::ContinueModal.md)|Continúa el estado modal de una ventana.|  
|[CWnd::Create](../Topic/CWnd::Create.md)|Crea e inicializa la ventana secundaria asociada con el objeto `CWnd`.|  
|[CWnd::CreateAccessibleProxy](../Topic/CWnd::CreateAccessibleProxy.md)|Crea a un proxy de Active Accessibility para el objeto especificado.|  
|[CWnd::CreateCaret](../Topic/CWnd::CreateCaret.md)|Crea una nueva forma para el símbolo de inserción y se hace con la propiedad de ese símbolo de inserción.|  
|[CWnd::CreateControl](../Topic/CWnd::CreateControl.md)|Crea un control ActiveX que se va a representar en un programa MFC con un objeto `CWnd`.|  
|[CWnd::CreateEx](../Topic/CWnd::CreateEx.md)|Crea una ventana de Windows superpuesta, emergente o secundaria y la asocia con un objeto `CWnd`.|  
|[CWnd::CreateGrayCaret](../Topic/CWnd::CreateGrayCaret.md)|Crea un bloque de color gris para el símbolo de inserción y se hace con la propiedad de ese símbolo de inserción.|  
|[CWnd::CreateSolidCaret](../Topic/CWnd::CreateSolidCaret.md)|Crea un bloque sólido para el símbolo de inserción y se hace con la propiedad de ese símbolo de inserción.|  
|[CWnd::DeleteTempMap](../Topic/CWnd::DeleteTempMap.md)|Clase llamada automáticamente por el controlador de tiempo de inactividad `CWinApp` que elimina los objetos `CWnd` temporales creados por `FromHandle`.|  
|[CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md)|Destruye la ventana de Windows asociada.|  
|[CWnd::Detach](../Topic/CWnd::Detach.md)|Desasocia un identificador de Windows de un objeto `CWnd` y devuelve el identificador.|  
|[CWnd::DlgDirList](../Topic/CWnd::DlgDirList.md)|Rellena un cuadro de lista con una lista de archivos o directorios.|  
|[CWnd::DlgDirListComboBox](../Topic/CWnd::DlgDirListComboBox.md)|Rellena el cuadro de lista de un cuadro combinado con una lista de archivos o directorios.|  
|[CWnd::DlgDirSelect](../Topic/CWnd::DlgDirSelect.md)|Recupera la selección actual de un cuadro de lista.|  
|[CWnd::DlgDirSelectComboBox](../Topic/CWnd::DlgDirSelectComboBox.md)|Recupera la selección actual del cuadro de lista de un cuadro combinado.|  
|[CWnd::DragAcceptFiles](../Topic/CWnd::DragAcceptFiles.md)|Indica que la ventana aceptará archivos arrastrados.|  
|[CWnd::DragDetect](../Topic/CWnd::DragDetect.md)|Captura el mouse y realiza un seguimiento de su movimiento hasta que el usuario suelta el botón primario, presiona la tecla ESC o mueve el mouse fuera del rectángulo de arrastre alrededor del punto especificado.|  
|[CWnd::DrawAnimatedRects](../Topic/CWnd::DrawAnimatedRects.md)|Dibuja un rectángulo de trama de alambres y lo anima para señalar un icono abierto o una ventana minimizada o maximizada.|  
|[CWnd::DrawCaption](../Topic/CWnd::DrawCaption.md)|Dibuja una leyenda.|  
|[CWnd::DrawMenuBar](../Topic/CWnd::DrawMenuBar.md)|Vuelve a dibujar la barra de menús.|  
|[CWnd::EnableActiveAccessibility](../Topic/CWnd::EnableActiveAccessibility.md)|Habilita las funciones de `Active Accessibility` definidas por el usuario.|  
|[CWnd::EnableDynamicLayout](../Topic/CWnd::EnableDynamicLayout.md)|Permite que la posición y el tamaño de las ventanas secundarias se ajusten dinámicamente cuando el usuario cambie el tamaño de la ventana.|  
|[CWnd::EnableD2DSupport](../Topic/CWnd::EnableD2DSupport.md)|Habilita o deshabilita la compatibilidad de `D2D` de ventana.  Llame a este método antes de que se inicialice la ventana principal.|  
|[CWnd::EnableScrollBar](../Topic/CWnd::EnableScrollBar.md)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|  
|[CWnd::EnableScrollBarCtrl](../Topic/CWnd::EnableScrollBarCtrl.md)|Habilita o deshabilita un control de barra de desplazamiento del mismo nivel.|  
|[CWnd::EnableToolTips](../Topic/CWnd::EnableToolTips.md)|Habilita el control de información sobre herramientas.|  
|[CWnd::EnableTrackingToolTips](../Topic/CWnd::EnableTrackingToolTips.md)|Habilita el control de información sobre herramientas en el modo de seguimiento.|  
|[CWnd::EnableWindow](../Topic/CWnd::EnableWindow.md)|Habilita o deshabilita la entrada de mouse y de teclado.|  
|[CWnd::EndModalLoop](../Topic/CWnd::EndModalLoop.md)|Finaliza el estado modal de una ventana.|  
|[CWnd::EndModalState](../Topic/CWnd::EndModalState.md)|Llame a esta función miembro para cambiar una ventana marco de modal a no modal.|  
|[CWnd::EndPaint](../Topic/CWnd::EndPaint.md)|Marca el final de la pintura.|  
|[CWnd::ExecuteDlgInit](../Topic/CWnd::ExecuteDlgInit.md)|Inicia un recurso de cuadro de diálogo.|  
|[CWnd::FilterToolTipMessage](../Topic/CWnd::FilterToolTipMessage.md)|Recupera el título o el texto asociado a un control en un cuadro de diálogo.|  
|[CWnd::FindWindow](../Topic/CWnd::FindWindow.md)|Devuelve el identificador de la ventana, que se reconoce por su nombre de ventana y su clase de ventana.|  
|[CWnd::FindWindowEx](../Topic/CWnd::FindWindowEx.md)|Devuelve el identificador de la ventana, que se reconoce por su nombre de ventana y su clase de ventana.|  
|[CWnd::FlashWindow](../Topic/CWnd::FlashWindow.md)|Hace que la ventana parpadee una vez.|  
|[CWnd::FlashWindowEx](../Topic/CWnd::FlashWindowEx.md)|Hace que la ventana parpadee con una funcionalidad adicional.|  
|[CWnd::FromHandle](../Topic/CWnd::FromHandle.md)|Devuelve un puntero a un objeto `CWnd` cuando se especifica un identificador a una ventana.  Si no hay un objeto `CWnd` asociado al identificador, se crea y asocia un objeto `CWnd` temporal.|  
|[CWnd::FromHandlePermanent](../Topic/CWnd::FromHandlePermanent.md)|Devuelve un puntero a un objeto `CWnd` cuando se especifica un identificador a una ventana.  Si no hay un objeto `CWnd` asociado al identificador, se crea y asocia un objeto `CWnd` temporal.|  
|[CWnd::get\_accChild](../Topic/CWnd::get_accChild.md)|El marco llama a este método para recuperar la dirección de una interfaz `IDispatch` del elemento secundario especificado.|  
|[CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md)|El marco llama a este método para recuperar el número de elementos secundarios que pertenecen a este objeto.|  
|[CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md)|El marco llama a este método para recuperar una cadena que describe la acción predeterminada del objeto.|  
|[CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md)|El marco llama a este método para recuperar una cadena que describe la apariencia visual del objeto especificado.|  
|[CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md)|El marco llama a este método para recuperar el objeto que tiene el foco de teclado.|  
|[CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md)|El marco llama a este método para recuperar la cadena de propiedad **Help** de un objeto.|  
|[CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md)|El marco llama a este método para recuperar la ruta de acceso completa del archivo `WinHelp` asociado al objeto especificado y el identificador del tema correspondiente dentro de ese archivo.|  
|[CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md)|El marco llama a este método para recuperar la tecla de método abreviado o la tecla de acceso del objeto especificado.|  
|[CWnd::get\_accName](../Topic/CWnd::get_accName.md)|El marco llama a este método para recuperar el nombre del objeto especificado.|  
|[CWnd::get\_accParent](../Topic/CWnd::get_accParent.md)|El marco llama a este método para recuperar la interfaz `IDispatch` del elemento principal del objeto.|  
|[CWnd::get\_accRole](../Topic/CWnd::get_accRole.md)|El marco llama a este método para recuperar información que describe el rol del objeto especificado.|  
|[CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md)|El marco llama a este método para recuperar el elemento secundario seleccionado de este objeto.|  
|[CWnd::get\_accState](../Topic/CWnd::get_accState.md)|El marco llama a este método para recuperar el estado actual del objeto especificado.|  
|[CWnd::get\_accValue](../Topic/CWnd::get_accValue.md)|El marco llama a este método para recuperar el valor del objeto especificado.|  
|[CWnd::GetActiveWindow](../Topic/CWnd::GetActiveWindow.md)|Recupera la ventana activa.|  
|[CWnd::GetAncestor](../Topic/CWnd::GetAncestor.md)|Recupera el objeto de ventana antecesor de la ventana especificada.|  
|[CWnd::GetCapture](../Topic/CWnd::GetCapture.md)|Recupera el objeto `CWnd` que tiene la captura del mouse.|  
|[CWnd::GetCaretPos](../Topic/CWnd::GetCaretPos.md)|Recupera las coordenadas de cliente de la posición actual del cursor de inserción.|  
|[CWnd::GetCheckedRadioButton](../Topic/CWnd::GetCheckedRadioButton.md)|Devuelve el identificador del botón de radio actualmente activado en un grupo de botones.|  
|[CWnd::GetClientRect](../Topic/CWnd::GetClientRect.md)|Obtiene las dimensiones del área cliente `CWnd`.|  
|[CWnd::GetClipboardOwner](../Topic/CWnd::GetClipboardOwner.md)|Recupera un puntero al propietario actual del Portapapeles.|  
|[CWnd::GetClipboardViewer](../Topic/CWnd::GetClipboardViewer.md)|Recupera un puntero a la primera ventana de la cadena de visores del Portapapeles.|  
|[CWnd::GetControlUnknown](../Topic/CWnd::GetControlUnknown.md)|Recupera un puntero a un control ActiveX desconocido.|  
|[CWnd::GetDC](../Topic/CWnd::GetDC.md)|Recupera un contexto de presentación del área cliente.|  
|[CWnd::GetDCEx](../Topic/CWnd::GetDCEx.md)|Recupera un contexto de presentación del área cliente y permite recortar mientras se dibuja.|  
|[CWnd::GetDCRenderTarget](../Topic/CWnd::GetDCRenderTarget.md)|Recupera el destino de representación \(DC\) del contexto de dispositivo de la ventana `CWnd`.|  
|[CWnd::GetDescendantWindow](../Topic/CWnd::GetDescendantWindow.md)|Encuentra todas las ventanas descendientes y devuelve aquella con el identificador especificado.|  
|[CWnd::GetDesktopWindow](../Topic/CWnd::GetDesktopWindow.md)|Recupera la ventana de escritorio de Windows.|  
|[CWnd::GetDlgCtrlID](../Topic/CWnd::GetDlgCtrlID.md)|Si el objeto `CWnd` es una ventana secundaria, la llamada a esta función devuelve su valor de identificador correspondiente.|  
|[CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md)|Recupera el control con el identificador especificado del cuadro de diálogo especificado.|  
|[CWnd::GetDlgItemInt](../Topic/CWnd::GetDlgItemInt.md)|Convierte el texto de un control en el cuadro de diálogo determinado en un valor entero.|  
|[CWnd::GetDlgItemText](../Topic/CWnd::GetDlgItemText.md)|Recupera la leyenda o el texto asociado a un control.|  
|[CWnd::GetDSCCursor](../Topic/CWnd::GetDSCCursor.md)|Recupera un puntero al cursor subyacente que se define mediante las propiedades DataSource, UserName, Password y SQL de un control de origen de datos.|  
|[CWnd::GetDynamicLayout](../Topic/CWnd::GetDynamicLayout.md)|Recupera un puntero al objeto del administrador de diseño dinámico.|  
|[CWnd::GetExStyle](../Topic/CWnd::GetExStyle.md)|Devuelve el estilo extendido de ventana.|  
|[CWnd::GetFocus](../Topic/CWnd::GetFocus.md)|Recupera el objeto `CWnd` que tiene el foco de entrada actualmente.|  
|[CWnd::GetFont](../Topic/CWnd::GetFont.md)|Recupera la fuente actual.|  
|[CWnd::GetForegroundWindow](../Topic/CWnd::GetForegroundWindow.md)|Devuelve un puntero a la ventana de primer plano \(la ventana de nivel superior con la que el usuario está trabajando actualmente\).|  
|[CWnd::GetIcon](../Topic/CWnd::GetIcon.md)|Recupera el identificador de un icono.|  
|[CWnd::GetLastActivePopup](../Topic/CWnd::GetLastActivePopup.md)|Determina cuál fue la ventana emergente propiedad de `CWnd` activa más recientemente.|  
|[CWnd::GetLayeredWindowAttributes](../Topic/CWnd::GetLayeredWindowAttributes.md)|Recupera la clave de color de transparencia y opacidad de una ventana superpuesta.|  
|[CWnd::GetMenu](../Topic/CWnd::GetMenu.md)|Recupera un puntero al menú especificado.|  
|[CWnd::GetNextDlgGroupItem](../Topic/CWnd::GetNextDlgGroupItem.md)|Busca el control siguiente \(o anterior\) dentro de un grupo de controles.|  
|[CWnd::GetNextDlgTabItem](../Topic/CWnd::GetNextDlgTabItem.md)|Recupera el primer control con el estilo [WS\_TABSTOP](../../mfc/reference/window-styles.md) que sigue \(o precede\) al control especificado.|  
|[CWnd::GetNextWindow](../Topic/CWnd::GetNextWindow.md)|Devuelve la ventana siguiente \(o anterior\) en la lista del Administrador de ventanas.|  
|[CWnd::GetOleControlSite](../Topic/CWnd::GetOleControlSite.md)|Recupera el sitio personalizado del control ActiveX especificado.|  
|[CWnd::GetOpenClipboardWindow](../Topic/CWnd::GetOpenClipboardWindow.md)|Recupera un puntero a la ventana que tiene actualmente el Portapapeles abierto.|  
|[CWnd::GetOwner](../Topic/CWnd::GetOwner.md)|Recupera un puntero al propietario de un objeto `CWnd`.|  
|[CWnd::GetParent](../Topic/CWnd::GetParent.md)|Recupera la ventana primaria de `CWnd` \(si existe\).|  
|[CWnd::GetParentFrame](../Topic/CWnd::GetParentFrame.md)|Recupera la ventana marco primaria del objeto `CWnd`.|  
|[CWnd::GetParentOwner](../Topic/CWnd::GetParentOwner.md)|Devuelve un puntero a la ventana primaria de una ventana secundaria.|  
|[CWnd::GetProperty](../Topic/CWnd::GetProperty.md)|Recupera una propiedad de control ActiveX.|  
|[CWnd::GetRenderTarget](../Topic/CWnd::GetRenderTarget.md)|Obtiene un destino de presentación asociado a esta ventana.|  
|[CWnd::GetSafeHwnd](../Topic/CWnd::GetSafeHwnd.md)|Devuelve `m_hWnd` o bien `NULL` si el puntero `this` es `NULL`.|  
|[CWnd::GetSafeOwner](../Topic/CWnd::GetSafeOwner.md)|Recupera el propietario seguro de la ventana especificada.|  
|[CWnd::GetScrollBarCtrl](../Topic/CWnd::GetScrollBarCtrl.md)|Devuelve un control de barra de desplazamiento del mismo nivel.|  
|[CWnd::GetScrollBarInfo](../Topic/CWnd::GetScrollBarInfo.md)|Recupera información sobre la barra de desplazamiento especificada.|  
|[CWnd::GetScrollInfo](../Topic/CWnd::GetScrollInfo.md)|Recupera la información que la estructura `SCROLLINFO` mantiene sobre una barra de desplazamiento.|  
|[CWnd::GetScrollLimit](../Topic/CWnd::GetScrollLimit.md)|Recupera el límite de la barra de desplazamiento.|  
|[CWnd::GetScrollPos](../Topic/CWnd::GetScrollPos.md)|Recupera la posición actual de un cuadro de desplazamiento.|  
|[CWnd::GetScrollRange](../Topic/CWnd::GetScrollRange.md)|Copia las posiciones mínima y máxima actuales de la barra de desplazamiento especificada.|  
|[CWnd::GetStyle](../Topic/CWnd::GetStyle.md)|Devuelve el estilo de ventana actual.|  
|[CWnd::GetSystemMenu](../Topic/CWnd::GetSystemMenu.md)|Permite a la aplicación tener acceso al menú de sistema para hacer copias y modificaciones.|  
|[CWnd::GetTitleBarInfo](../Topic/CWnd::GetTitleBarInfo.md)|Recupera información sobre la barra de título especificada.|  
|[CWnd::GetTopLevelFrame](../Topic/CWnd::GetTopLevelFrame.md)|Recupera la ventana marco de nivel superior de la ventana.|  
|[CWnd::GetTopLevelOwner](../Topic/CWnd::GetTopLevelOwner.md)|Recupera la ventana de nivel superior.|  
|[CWnd::GetTopLevelParent](../Topic/CWnd::GetTopLevelParent.md)|Recupera el elemento principal de nivel superior de la ventana.|  
|[CWnd::GetTopWindow](../Topic/CWnd::GetTopWindow.md)|Devuelve la primera ventana secundaria que pertenece al objeto `CWnd`.|  
|[CWnd::GetUpdateRect](../Topic/CWnd::GetUpdateRect.md)|Recupera las coordenadas del rectángulo más pequeño que contiene toda la región de actualización de `CWnd`.|  
|[CWnd::GetUpdateRgn](../Topic/CWnd::GetUpdateRgn.md)|Recupera la región de actualización de `CWnd`.|  
|[CWnd::GetWindow](../Topic/CWnd::GetWindow.md)|Devuelve la ventana con la relación especificada con esta ventana.|  
|[CWnd::GetWindowContextHelpId](../Topic/CWnd::GetWindowContextHelpId.md)|Recupera el identificador de contexto de Ayuda.|  
|[CWnd::GetWindowDC](../Topic/CWnd::GetWindowDC.md)|Recupera el contexto de presentación de toda la ventana, como la barra de título, los menús y las barras de desplazamiento.|  
|[CWnd::GetWindowedChildCount](../Topic/CWnd::GetWindowedChildCount.md)|Devuelve al número de ventanas secundarias asociadas.|  
|[CWnd::GetWindowInfo](../Topic/CWnd::GetWindowInfo.md)|Devuelve información sobre la ventana.|  
|[CWnd::GetWindowlessChildCount](../Topic/CWnd::GetWindowlessChildCount.md)|Devuelve el número de ventanas secundarias asociadas sin ventanas.|  
|[CWnd::GetWindowPlacement](../Topic/CWnd::GetWindowPlacement.md)|Recupera el estado de visualización y las posiciones normal \(restaurada\), minimizada y maximizada de una ventana.|  
|[CWnd::GetWindowRect](../Topic/CWnd::GetWindowRect.md)|Obtiene las coordenadas de pantalla de `CWnd`.|  
|[CWnd::GetWindowRgn](../Topic/CWnd::GetWindowRgn.md)|Recupera una copia de la región de ventana de una ventana.|  
|[CWnd::GetWindowText](../Topic/CWnd::GetWindowText.md)|Devuelve el título de texto o de leyenda de la ventana \(si lo hay\).|  
|[CWnd::GetWindowTextLength](../Topic/CWnd::GetWindowTextLength.md)|Devuelve la longitud del título de texto o de leyenda de la ventana.|  
|[CWnd::HideCaret](../Topic/CWnd::HideCaret.md)|Quita el cursor de inserción de la presentación en pantalla para ocultarlo.|  
|[CWnd::HiliteMenuItem](../Topic/CWnd::HiliteMenuItem.md)|Resalta un elemento de menú de nivel superior \(barra de menús\) o quita el resaltado de este.|  
|[CWnd::HtmlHelp](../Topic/CWnd::HtmlHelp.md)|Se llama para iniciar la aplicación HTMLHelp.|  
|[CWnd::Invalidate](../Topic/CWnd::Invalidate.md)|Invalida toda el área cliente.|  
|[CWnd::InvalidateRect](../Topic/CWnd::InvalidateRect.md)|Invalida el área cliente dentro del rectángulo especificado agregando dicho rectángulo a la región de actualización actual.|  
|[CWnd::InvalidateRgn](../Topic/CWnd::InvalidateRgn.md)|Invalida el área cliente dentro de la región especificada agregando dicha región a la región de actualización actual.|  
|[CWnd::InvokeHelper](../Topic/CWnd::InvokeHelper.md)|Invoca un método o una propiedad de control ActiveX.|  
|[CWnd::IsChild](../Topic/CWnd::IsChild.md)|Indica si `CWnd` es una ventana secundaria u otro descendiente directo de la ventana especificada.|  
|[CWnd::IsD2DSupportEnabled](../Topic/CWnd::IsD2DSupportEnabled.md)|Determina si la compatibilidad con `D2D` está habilitada.|  
|[CWnd::IsDialogMessage](../Topic/CWnd::IsDialogMessage.md)|Determina si el mensaje en cuestión está pensado para el cuadro de diálogo no modal y, si es así, lo procesa.|  
|[CWnd::IsDlgButtonChecked](../Topic/CWnd::IsDlgButtonChecked.md)|Determina si un control de botón está seleccionado.|  
|[CWnd::IsDynamicLayoutEnabled](../Topic/CWnd::IsDynamicLayoutEnabled.md)|Determina si el diseño dinámico está habilitado en esta ventana.  Si el diseño dinámico está habilitado, la posición y el tamaño de las ventanas secundarias pueden cambiar cuando el usuario cambie el tamaño de la ventana primaria.|  
|[CWnd::IsIconic](../Topic/CWnd::IsIconic.md)|Determina si `CWnd` está minimizado \(icono\).|  
|[CWnd::IsTouchWindow](../Topic/CWnd::IsTouchWindow.md)|Especifica si `CWnd` es compatible con la entrada táctil.|  
|[CWnd::IsWindowEnabled](../Topic/CWnd::IsWindowEnabled.md)|Determina si la ventana está habilitada para la entrada de mouse y de teclado.|  
|[CWnd::IsWindowVisible](../Topic/CWnd::IsWindowVisible.md)|Determina si la ventana está visible.|  
|[CWnd::IsZoomed](../Topic/CWnd::IsZoomed.md)|Determina si `CWnd` está maximizado.|  
|[CWnd::KillTimer](../Topic/CWnd::KillTimer.md)|Elimina un cronómetro del sistema.|  
|[CWnd::LockWindowUpdate](../Topic/CWnd::LockWindowUpdate.md)|No permite o vuelve a permitir que se dibuje en la ventana especificada.|  
|[CWnd::MapWindowPoints](../Topic/CWnd::MapWindowPoints.md)|Convierte \(asigna\) un conjunto de puntos del espacio de coordenadas de `CWnd` al espacio de coordenadas de otra ventana.|  
|[CWnd::MessageBox](../Topic/CWnd::MessageBox.md)|Crea y muestra una ventana que contiene un mensaje y una leyenda proporcionados por la aplicación.|  
|[CWnd::ModifyStyle](../Topic/CWnd::ModifyStyle.md)|Modifica el estilo de ventana actual.|  
|[CWnd::ModifyStyleEx](../Topic/CWnd::ModifyStyleEx.md)|Modifica el estilo extendido de ventana.|  
|[CWnd::MoveWindow](../Topic/CWnd::MoveWindow.md)|Cambia la posición y las dimensiones de `CWnd`.|  
|[CWnd::NotifyWinEvent](../Topic/CWnd::NotifyWinEvent.md)|Indica al sistema que se ha producido un evento predefinido.|  
|[CWnd::OnAmbientProperty](../Topic/CWnd::OnAmbientProperty.md)|Implemente valores de propiedad ambiente.|  
|[CWnd::OnDrawIconicThumbnailOrLivePreview](../Topic/CWnd::OnDrawIconicThumbnailOrLivePreview.md)|El marco llama a este método cuando necesita obtener un mapa de bits para mostrarlo en la miniatura de pestañas de Windows 7 o en el cliente para ojear la aplicación.|  
|[CWnd::OnHelp](../Topic/CWnd::OnHelp.md)|Controla la Ayuda de F1 de la aplicación \(usando el contexto actual\).|  
|[CWnd::OnHelpFinder](../Topic/CWnd::OnHelpFinder.md)|Controla los comandos `ID_HELP_FINDER` e `ID_DEFAULT_HELP`.|  
|[CWnd::OnHelpIndex](../Topic/CWnd::OnHelpIndex.md)|Controla el comando `ID_HELP_INDEX` y proporciona un tema de Ayuda predeterminado.|  
|[CWnd::OnHelpUsing](../Topic/CWnd::OnHelpUsing.md)|Controla el comando `ID_HELP_USING`.|  
|[CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md)|Determina si un punto está en el rectángulo delimitador de la herramienta especificada y recupera información sobre dicha herramienta.|  
|[CWnd::OpenClipboard](../Topic/CWnd::OpenClipboard.md)|Abre el Portapapeles.  Otras aplicaciones no podrán modificar el Portapapeles hasta que se llame a la función [CloseClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649035) de Windows.|  
|[CWnd::PaintWindowlessControls](../Topic/CWnd::PaintWindowlessControls.md)|Dibuja controles sin ventanas en el contenedor del control.|  
|[CWnd::PostMessage](../Topic/CWnd::PostMessage.md)|Pone un mensaje en la cola de la aplicación y vuelve sin esperar a que la ventana procese el mensaje.|  
|[CWnd::PreCreateWindow](../Topic/CWnd::PreCreateWindow.md)|Se llama antes de crear la ventana de Windows asociada a este objeto `CWnd`.|  
|[CWnd::PreSubclassWindow](../Topic/CWnd::PreSubclassWindow.md)|Permite que otras subclases necesarias ocurran antes de llamar a [SubclassWindow](../Topic/CWnd::SubclassWindow.md).|  
|[CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)|Utilizado por `CWinApp` para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows `TranslateMessage` y `DispatchMessage`.|  
|[CWnd::Print](../Topic/CWnd::Print.md)|Dibuja la ventana actual en el contexto de dispositivo especificado.|  
|[CWnd::PrintClient](../Topic/CWnd::PrintClient.md)|Dibuja cualquier ventana en el contexto de dispositivo especificado \(normalmente, un contexto de dispositivo de impresora\).|  
|[CWnd::PrintWindow](../Topic/CWnd::PrintWindow.md)|Copia una ventana visual en el contexto de dispositivo especificado \(normalmente, un DC de impresora\).|  
|[CWnd::RedrawWindow](../Topic/CWnd::RedrawWindow.md)|Actualiza el rectángulo o la región especificados en el área cliente.|  
|[CWnd::RegisterTouchWindow](../Topic/CWnd::RegisterTouchWindow.md)|Registre la compatibilidad con entrada táctil de Windows de la ventana o anule ese registro.|  
|[CWnd::ReleaseDC](../Topic/CWnd::ReleaseDC.md)|Libera los contextos de dispositivo de cliente y de ventana, de forma que están disponibles para que los usen otras aplicaciones.|  
|[CWnd::RepositionBars](../Topic/CWnd::RepositionBars.md)|Vuelve a colocar las barras de control en el área cliente.|  
|[CWnd::RunModalLoop](../Topic/CWnd::RunModalLoop.md)|Recupera, convierte o envía mensajes relativos a una ventana que está en estado modal.|  
|[CWnd::ScreenToClient](../Topic/CWnd::ScreenToClient.md)|Convierte las coordenadas de pantalla de un punto o rectángulo determinado en pantalla en las coordenadas de pantalla.|  
|[CWnd::ScrollWindow](../Topic/CWnd::ScrollWindow.md)|Desplaza el contenido del área cliente.|  
|[CWnd::ScrollWindowEx](../Topic/CWnd::ScrollWindowEx.md)|Desplaza el contenido del área cliente.  Similar a `ScrollWindow`, con más características.|  
|[CWnd::SendChildNotifyLastMsg](../Topic/CWnd::SendChildNotifyLastMsg.md)|Proporciona un mensaje de notificación a una ventana secundaria, desde la ventana primaria, de forma que la ventana secundaria pueda controlar una tarea.|  
|[CWnd::SendDlgItemMessage](../Topic/CWnd::SendDlgItemMessage.md)|Envía un mensaje al control especificado.|  
|[CWnd::SendMessage](../Topic/CWnd::SendMessage.md)|Envía un mensaje al objeto `CWnd` y no vuelve hasta que el mensaje se ha procesado.|  
|[CWnd::SendMessageToDescendants](../Topic/CWnd::SendMessageToDescendants.md)|Envía un mensaje a todas las ventanas descendientes de la ventana.|  
|[CWnd::SendNotifyMessage](../Topic/CWnd::SendNotifyMessage.md)|Envía el mensaje especificado a la ventana y vuelve tan pronto como sea posible, dependiendo de si el subproceso de llamada creó la ventana.|  
|[CWnd::SetActiveWindow](../Topic/CWnd::SetActiveWindow.md)|Activa la ventana.|  
|[CWnd::SetCapture](../Topic/CWnd::SetCapture.md)|Hace que todas las entradas de mouse siguientes se envíen a `CWnd`.|  
|[CWnd::SetCaretPos](../Topic/CWnd::SetCaretPos.md)|Mueve el cursor de inserción a la posición especificada.|  
|[CWnd::SetClipboardViewer](../Topic/CWnd::SetClipboardViewer.md)|Agrega `CWnd` a la cadena de ventanas a las que se notifica cada vez que el contenido del Portapapeles cambia.|  
|[CWnd::SetDlgCtrlID](../Topic/CWnd::SetDlgCtrlID.md)|Establece el identificador de ventana o de control de la ventana \(que puede ser cualquier ventana secundaria, no solo un control en un cuadro de diálogo\).|  
|[CWnd::SetDlgItemInt](../Topic/CWnd::SetDlgItemInt.md)|Establece el texto de un control en la cadena que representa un valor entero.|  
|[CWnd::SetDlgItemText](../Topic/CWnd::SetDlgItemText.md)|Establece la leyenda o el texto de un control en el cuadro de diálogo especificado.|  
|[CWnd::SetFocus](../Topic/CWnd::SetFocus.md)|Reclama el foco de entrada.|  
|[CWnd::SetFont](../Topic/CWnd::SetFont.md)|Establece la fuente actual.|  
|[CWnd::SetForegroundWindow](../Topic/CWnd::SetForegroundWindow.md)|Pone en primer plano el subproceso que creó la ventana y activa la ventana.|  
|[CWnd::SetIcon](../Topic/CWnd::SetIcon.md)|Establece el identificador en un icono específico.|  
|[CWnd::SetLayeredWindowAttributes](../Topic/CWnd::SetLayeredWindowAttributes.md)|Establece la clave de color de transparencia y opacidad de una ventana superpuesta.|  
|[CWnd::SetMenu](../Topic/CWnd::SetMenu.md)|Establece el menú en el menú especificado.|  
|[CWnd::SetOwner](../Topic/CWnd::SetOwner.md)|Cambia el propietario de un objeto `CWnd`.|  
|[CWnd::SetParent](../Topic/CWnd::SetParent.md)|Cambia la ventana primaria.|  
|[CWnd::SetProperty](../Topic/CWnd::SetProperty.md)|Establece una propiedad de control ActiveX.|  
|[CWnd::SetRedraw](../Topic/CWnd::SetRedraw.md)|Permite o impide volver a dibujar los cambios en `CWnd`.|  
|[CWnd::SetScrollInfo](../Topic/CWnd::SetScrollInfo.md)|Establece la información acerca de la barra de desplazamiento.|  
|[CWnd::SetScrollPos](../Topic/CWnd::SetScrollPos.md)|Establece la posición actual de un cuadro de desplazamiento y, si se especifica, vuelve a dibujar la barra de desplazamiento para reflejar la nueva posición.|  
|[CWnd::SetScrollRange](../Topic/CWnd::SetScrollRange.md)|Establece los valores de posición mínimo y máximo de la barra de desplazamiento especificada.|  
|[CWnd::SetTimer](../Topic/CWnd::SetTimer.md)|Instala un cronómetro del sistema que envía un mensaje [WM\_TIMER](../Topic/CWnd::OnTimer.md) al activarse.|  
|[CWnd::SetWindowContextHelpId](../Topic/CWnd::SetWindowContextHelpId.md)|Establece el identificador de contexto de Ayuda.|  
|[CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)|Establece el estado de visualización y las posiciones normal \(restaurada\), minimizada y maximizada de una ventana.|  
|[CWnd::SetWindowPos](../Topic/CWnd::SetWindowPos.md)|Cambia el tamaño, la posición y el orden de las ventanas secundarias, emergentes y de nivel superior.|  
|[CWnd::SetWindowRgn](../Topic/CWnd::SetWindowRgn.md)|Establece la región de una ventana.|  
|[CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)|Establece el título de texto o de leyenda de la ventana \(si lo hay\) en el texto especificado.|  
|[CWnd::ShowCaret](../Topic/CWnd::ShowCaret.md)|Muestra el cursor de intersección en pantalla en la posición del cursor de intersección.  Ya en pantalla, el cursor de intersección comienza a parpadear automáticamente.|  
|[CWnd::ShowOwnedPopups](../Topic/CWnd::ShowOwnedPopups.md)|Muestra u oculta todas las ventanas emergentes propiedad de la ventana.|  
|[CWnd::ShowScrollBar](../Topic/CWnd::ShowScrollBar.md)|Muestra u oculta una barra de desplazamiento.|  
|[CWnd::ShowWindow](../Topic/CWnd::ShowWindow.md)|Muestra u oculta la ventana.|  
|[CWnd::SubclassDlgItem](../Topic/CWnd::SubclassDlgItem.md)|Asocia un control de Windows a un objeto `CWnd` y le hace enrutar mensajes a través del mapa de mensajes de `CWnd`.|  
|[CWnd::SubclassWindow](../Topic/CWnd::SubclassWindow.md)|Asocia una ventana a un objeto `CWnd` y le hace enrutar mensajes a través del mapa de mensajes de `CWnd`.|  
|[CWnd::UnlockWindowUpdate](../Topic/CWnd::UnlockWindowUpdate.md)|Desbloquea una ventana que se bloqueó con `CWnd::LockWindowUpdate`.|  
|[CWnd::UnsubclassWindow](../Topic/CWnd::UnsubclassWindow.md)|Desasocia una ventana de un objeto `CWnd` .|  
|[CWnd::UpdateData](../Topic/CWnd::UpdateData.md)|Inicializa o recupera datos de un cuadro de diálogo.|  
|[CWnd::UpdateDialogControls](../Topic/CWnd::UpdateDialogControls.md)|Llame a este método para actualizar el estado de los botones del cuadro de diálogo y de otros controles.|  
|[CWnd::UpdateLayeredWindow](../Topic/CWnd::UpdateLayeredWindow.md)|Actualiza la posición, el tamaño, la forma, el contenido y la transparencia de una ventana superpuesta.|  
|[CWnd::UpdateWindow](../Topic/CWnd::UpdateWindow.md)|Actualiza el área de cliente.|  
|[CWnd::ValidateRect](../Topic/CWnd::ValidateRect.md)|Valida el área cliente dentro del rectángulo especificado quitando dicho rectángulo de la región de actualización actual.|  
|[CWnd::ValidateRgn](../Topic/CWnd::ValidateRgn.md)|Valida el área cliente dentro de la región especificada quitando dicha región de la región de actualización actual.|  
|[CWnd::WindowFromPoint](../Topic/CWnd::WindowFromPoint.md)|Identifica la ventana que contiene el punto especificado.|  
|[CWnd::WinHelp](../Topic/CWnd::WinHelp.md)|Se llama para iniciar la aplicación WinHelp.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWnd::Default](../Topic/CWnd::Default.md)|Llama al procedimiento de ventana predeterminado, que proporciona el procesamiento predeterminado de los mensajes de ventana que una aplicación no procesa.|  
|[CWnd::DefWindowProc](../Topic/CWnd::DefWindowProc.md)|Llama al procedimiento de ventana predeterminado, que proporciona procesamiento predeterminado de los mensajes de ventana que una aplicación no procesa.|  
|[CWnd::DoDataExchange](../Topic/CWnd::DoDataExchange.md)|Sirve para intercambiar y validar datos de cuadros de diálogo.  Es llamado por el método `UpdateData`.|  
|[CWnd::GetCurrentMessage](../Topic/CWnd::GetCurrentMessage.md)|Devuelve un puntero al mensaje que esta ventana está procesando actualmente.  Solo es necesario llamarlo cuando se está en una función miembro de controlador de mensajes `On`*Message*.|  
|[CWnd::InitDynamicLayout](../Topic/CWnd::InitDynamicLayout.md)|El marco llama a este método para inicializar el diseño dinámico de una ventana.|  
|[CWnd::LoadDynamicLayoutResource](../Topic/CWnd::LoadDynamicLayoutResource.md)|Carga información de diseño dinámico desde el archivo de recursos.|  
|[CWnd::OnActivate](../Topic/CWnd::OnActivate.md)|Se llama cuando `CWnd` se está activando o desactivando.|  
|[CWnd::OnActivateApp](../Topic/CWnd::OnActivateApp.md)|Se llama cuando la aplicación está a punto de activarse o desactivarse.|  
|[CWnd::OnAppCommand](../Topic/CWnd::OnAppCommand.md)|Se llama cuando el usuario genera un evento de comando de la aplicación.|  
|[CWnd::OnAskCbFormatName](../Topic/CWnd::OnAskCbFormatName.md)|Una aplicación de visor del Portapapeles llama a este método cuando un propietario del Portapapeles va a mostrar el contenido del Portapapeles.|  
|[CWnd::OnCancelMode](../Topic/CWnd::OnCancelMode.md)|Se llama para permitir que `CWnd` cancele cualquier modo interno, como la captura del mouse.|  
|[CWnd::OnCaptureChanged](../Topic/CWnd::OnCaptureChanged.md)|Envía un mensaje a la ventana que está perdiendo la captura del mouse.|  
|[CWnd::OnChangeCbChain](../Topic/CWnd::OnChangeCbChain.md)|Notifica una ventana especificada se está quitando de la cadena.|  
|[CWnd::OnChangeUIState](../Topic/CWnd::OnChangeUIState.md)|Se llama cuando es necesario cambiar el estado de la interfaz de usuario.|  
|[CWnd::OnChar](../Topic/CWnd::OnChar.md)|Se llama cuando una pulsación de tecla se convierte en un carácter que no es del sistema.|  
|[CWnd::OnCharToItem](../Topic/CWnd::OnCharToItem.md)|Un cuadro de lista secundario con el estilo [LBS\_WANTKEYBOARDINPUT](../../mfc/reference/list-box-styles.md) llama a este método en respuesta a un mensaje [WM\_CHAR](../Topic/CWnd::OnChar.md).|  
|[CWnd::OnChildActivate](../Topic/CWnd::OnChildActivate.md)|Se llama en relación con ventanas secundarias de interfaz múltiples documentos \(MDI\) cada vez que el tamaño o la posición de `CWnd` cambia o `CWnd` se activa.|  
|[CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md)|Una ventana primaria llama a este método para que un control notificado tenga la oportunidad de responder a la notificación de control.|  
|[CWnd::OnClipboardUpdate](../Topic/CWnd::OnClipboardUpdate.md)|Se llama cuando el contenido del Portapapeles cambia.|  
|[CWnd::OnClose](../Topic/CWnd::OnClose.md)|Se llama como una señal de que `CWnd` debe cerrarse.|  
|[CWnd::OnColorizationColorChanged](../Topic/CWnd::OnColorizationColorChanged.md)|Se llama cuando cambia la directiva de representación en el área no cliente.|  
|[CWnd::OnCommand](../Topic/CWnd::OnCommand.md)|Se llama cuando el usuario selecciona un comando.|  
|[CWnd::OnCompacting](../Topic/CWnd::OnCompacting.md)|Se llama cuando Windows detecta que la memoria del sistema es baja.|  
|[CWnd::OnCompareItem](../Topic/CWnd::OnCompareItem.md)|Se llama para averiguar la posición relativa de un nuevo elemento en un cuadro de lista o un cuadro combinado secundario ordenado dibujado por el propietario.|  
|[CWnd::OnCompositionChanged](../Topic/CWnd::OnCompositionChanged.md)|Se llama en relación con todas las ventanas de nivel superior cuando se habilita o deshabilita la composición del Administrador de ventanas de escritorio \(DWM\).|  
|[CWnd::OnContextMenu](../Topic/CWnd::OnContextMenu.md)|Se llama cuando el usuario hace clic con el botón secundario del mouse en la ventana.|  
|[CWnd::OnCopyData](../Topic/CWnd::OnCopyData.md)|Copia datos de una aplicación a otra.|  
|[CWnd::OnCreate](../Topic/CWnd::OnCreate.md)|Se llama como parte de la creación de una ventana.|  
|[CWnd::OnCtlColor](../Topic/CWnd::OnCtlColor.md)|Se llama si `CWnd` es el elemento primario de un control cuando el control se va a dibujar.|  
|[CWnd::OnDeadChar](../Topic/CWnd::OnDeadChar.md)|Se llama cuando una pulsación de tecla se convierte en un carácter inactivo que no es de sistema \(por ejemplo, caracteres acentuados\).|  
|[CWnd::OnDeleteItem](../Topic/CWnd::OnDeleteItem.md)|Se llama cuando se destruye un cuadro de lista o un cuadro combinado secundario dibujado por el propietario, o cuando se quitan elementos del control.|  
|[CWnd::OnDestroy](../Topic/CWnd::OnDestroy.md)|Se llama cuando `CWnd` se está destruyendo.|  
|[CWnd::OnDestroyClipboard](../Topic/CWnd::OnDestroyClipboard.md)|Se llama cuando el Portapapeles se vacía llamando a la función de Windows [EmptyClipboard](http://msdn.microsoft.com/library/windows/desktop/ms649037).|  
|[CWnd::OnDeviceChange](../Topic/CWnd::OnDeviceChange.md)|Notifica a un controlador de dispositivo o aplicación de un cambio en la configuración de hardware de un dispositivo o del equipo.|  
|[CWnd::OnDevModeChange](../Topic/CWnd::OnDevModeChange.md)|Se llama en relación con todas las ventanas de nivel superior cuando el usuario cambia la configuración de modo de dispositivo.|  
|[CWnd::OnDrawClipboard](../Topic/CWnd::OnDrawClipboard.md)|Se llama cuando el contenido del Portapapeles cambia.|  
|[CWnd::OnDrawItem](../Topic/CWnd::OnDrawItem.md)|Se llama cuando es necesario dibujar un aspecto visual de un control de botón, un control de cuadro combinado, un control de cuadro de lista o un menú secundario dibujado por el propietario.|  
|[CWnd::OnDropFiles](../Topic/CWnd::OnDropFiles.md)|Se llama cuando el usuario suelta el botón primario del mouse en una ventana que se ha registrado como destinataria de los archivos colocados.|  
|[CWnd::OnEnable](../Topic/CWnd::OnEnable.md)|Se llama cuando `CWnd` se habilita o deshabilita.|  
|[CWnd::OnEndSession](../Topic/CWnd::OnEndSession.md)|Se llama cuando una sesión finaliza.|  
|[CWnd::OnEnterIdle](../Topic/CWnd::OnEnterIdle.md)|Se llama para informar al procedimiento de ventana principal de una aplicación de que un menú o un cuadro de diálogo modal está entrando en estado inactivo.|  
|[CWnd::OnEnterMenuLoop](../Topic/CWnd::OnEnterMenuLoop.md)|Se llama cuando se ha entrado en un bucle modal de menú.|  
|[CWnd::OnEnterSizeMove](../Topic/CWnd::OnEnterSizeMove.md)|Se llama después de que la ventana afectada entre en un bucle modal de movimiento o de tamaño.|  
|[CWnd::OnEraseBkgnd](../Topic/CWnd::OnEraseBkgnd.md)|Se llama cuando es necesario borrar el fondo de la ventana.|  
|[CWnd::OnExitMenuLoop](../Topic/CWnd::OnExitMenuLoop.md)|Se llama cuando se ha salido de un bucle modal de menú.|  
|[CWnd::OnExitSizeMove](../Topic/CWnd::OnExitSizeMove.md)|Se llama después de que la ventana afectada salga de un bucle modal de movimiento o de tamaño.|  
|[CWnd::OnFontChange](../Topic/CWnd::OnFontChange.md)|Se llama cuando el grupo de recursos de fuente cambia.|  
|[CWnd::OnGetDlgCode](../Topic/CWnd::OnGetDlgCode.md)|Se llama en relación con un control para que el control pueda procesar por sí mismo las entradas de tecla de dirección y de tecla TAB.|  
|[CWnd::OnGetMinMaxInfo](../Topic/CWnd::OnGetMinMaxInfo.md)|Se llama siempre que Windows necesita conocer la posición o dimensiones maximizadas, o bien el tamaño de seguimiento mínimo o máximo.|  
|[CWnd::OnHelpInfo](../Topic/CWnd::OnHelpInfo.md)|El marco llama a este método cuando el usuario presiona la tecla F1.|  
|[CWnd::OnHotKey](../Topic/CWnd::OnHotKey.md)|Se llama cuando el usuario presiona una tecla de acceso rápido de todo el sistema.|  
|[CWnd::OnHScroll](../Topic/CWnd::OnHScroll.md)|Se llama cuando el usuario hace clic en la barra de desplazamiento horizontal de `CWnd`.|  
|[CWnd::OnHScrollClipboard](../Topic/CWnd::OnHScrollClipboard.md)|Se llama cuando un propietario de Portapapeles tiene que desplazarse por la imagen del Portapapeles, invalidar la sección correspondiente y actualizar los valores de la barra de desplazamiento.|  
|[CWnd::OnIconEraseBkgnd](../Topic/CWnd::OnIconEraseBkgnd.md)|Se llama cuando `CWnd` está minimizado \(icono\) y el fondo del icono se tiene que rellenar antes de pintar el icono.|  
|[CWnd::OnInitMenu](../Topic/CWnd::OnInitMenu.md)|Se llama cuando un menú está a punto de activarse.|  
|[CWnd::OnInitMenuPopup](../Topic/CWnd::OnInitMenuPopup.md)|Se llama cuando un menú emergente está a punto de activarse.|  
|[CWnd::OnInputDeviceChange](../Topic/CWnd::OnInputDeviceChange.md)|Se llama cuando un dispositivo de E\/S se agrega al sistema o se quita de él.|  
|[CWnd::OnInputLangChange](../Topic/CWnd::OnInputLangChange.md)|Se llama después de que el idioma de entrada de una aplicación cambie.|  
|[CWnd::OnInputLangChangeRequest](../Topic/CWnd::OnInputLangChangeRequest.md)|Se llama cuando el usuario elige un nuevo idioma de entrada.|  
|[CWnd::OnKeyDown](../Topic/CWnd::OnKeyDown.md)|Se llama cuando se presiona una tecla que no es del sistema.|  
|[CWnd::OnKeyUp](../Topic/CWnd::OnKeyUp.md)|Se llama cuando se suelta una tecla que no es del sistema.|  
|[CWnd::OnKillFocus](../Topic/CWnd::OnKillFocus.md)|Se llama inmediatamente antes de que `CWnd` pierda el foco de entrada.|  
|[CWnd::OnLButtonDblClk](../Topic/CWnd::OnLButtonDblClk.md)|Se llama cuando el usuario hace doble clic con el botón primario del mouse.|  
|[CWnd::OnLButtonDown](../Topic/CWnd::OnLButtonDown.md)|Se llama cuando el usuario presiona el botón primario del mouse.|  
|[CWnd::OnLButtonUp](../Topic/CWnd::OnLButtonUp.md)|Se llama cuando el usuario suelta el botón primario del mouse.|  
|[CWnd::OnMButtonDblClk](../Topic/CWnd::OnMButtonDblClk.md)|Se llama cuando el usuario hace doble clic con el botón central del mouse.|  
|[CWnd::OnMButtonDown](../Topic/CWnd::OnMButtonDown.md)|Se llama cuando el usuario presiona el botón central del mouse.|  
|[CWnd::OnMButtonUp](../Topic/CWnd::OnMButtonUp.md)|Se llama cuando el usuario suelta el botón central del mouse.|  
|[CWnd::OnMDIActivate](../Topic/CWnd::OnMDIActivate.md)|Se llama lugar cuando una ventana secundaria MDI se activa o desactiva.|  
|[CWnd::OnMeasureItem](../Topic/CWnd::OnMeasureItem.md)|Se llama en relación con un cuadro combinado, un cuadro de lista o un elemento de menú secundario dibujado por el propietario cuando el control se crea.  `CWnd` informa a Windows de las dimensiones del control.|  
|[CWnd::OnMenuChar](../Topic/CWnd::OnMenuChar.md)|Se llama cuando el usuario presiona un carácter de acceso de menú que no coincide con ninguna de las teclas de acceso predefinidas en el menú actual.|  
|[CWnd::OnMenuDrag](../Topic/CWnd::OnMenuDrag.md)|Se llama cuando el usuario empieza a arrastrar un elemento de menú.|  
|[CWnd::OnMenuGetObject](../Topic/CWnd::OnMenuGetObject.md)|Se llama cuando el cursor del mouse entra en un elemento de menú o se mueve desde el centro del elemento hasta el principio o el final del elemento.|  
|[CWnd::OnMenuRButtonUp](../Topic/CWnd::OnMenuRButtonUp.md)|Se llama cuando el usuario suelta el botón secundario del mouse mientras el cursor se encuentra en un elemento de menú.|  
|[CWnd::OnMenuSelect](../Topic/CWnd::OnMenuSelect.md)|Se llama cuando el usuario selecciona un elemento de menú.|  
|[CWnd::OnMouseActivate](../Topic/CWnd::OnMouseActivate.md)|Se llama cuando el cursor está en una ventana inactiva y el usuario presiona un botón del mouse.|  
|[CWnd::OnMouseHover](../Topic/CWnd::OnMouseHover.md)|Se llama cuando el cursor se sitúa sobre el área cliente de la ventana durante el período de tiempo especificado en una llamada anterior a [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265).|  
|[CWnd::OnMouseHWheel](../Topic/CWnd::OnMouseHWheel.md)|Se llama cuando la ventana actual ha sido compuesta por el Administrador de ventanas de escritorio \(DWM\) y esa ventana está maximizada.|  
|[CWnd::OnMouseLeave](../Topic/CWnd::OnMouseLeave.md)|Se llama cuando el cursor abandona el área cliente de la ventana especificada en una llamada anterior a [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265).|  
|[CWnd::OnMouseMove](../Topic/CWnd::OnMouseMove.md)|Se llama cuando el cursor del mouse se mueve.|  
|[CWnd::OnMouseWheel](../Topic/CWnd::OnMouseWheel.md)|Se llama cuando un usuario gira la rueda del mouse.  Usa el control de mensajes de Windows NT 4.0.|  
|[CWnd::OnMove](../Topic/CWnd::OnMove.md)|Se llama después de que la posición del objeto `CWnd` haya cambiado.|  
|[CWnd::OnMoving](../Topic/CWnd::OnMoving.md)|Indica que un usuario está moviendo un objeto `CWnd`.|  
|[CWnd::OnNcActivate](../Topic/CWnd::OnNcActivate.md)|Se llama cuando es necesario cambiar el área no cliente para indicar un estado activo o inactivo.|  
|[CWnd::OnNcCalcSize](../Topic/CWnd::OnNcCalcSize.md)|Se llama cuando hay que calcular el tamaño y la posición del área cliente.|  
|[CWnd::OnNcCreate](../Topic/CWnd::OnNcCreate.md)|Se llama antes de [OnCreate](../Topic/CWnd::OnCreate.md) cuando se está creando el área no cliente.|  
|[CWnd::OnNcDestroy](../Topic/CWnd::OnNcDestroy.md)|Se llama cuando el área no cliente se está destruyendo.|  
|[CWnd::OnNcHitTest](../Topic/CWnd::OnNcHitTest.md)|Windows llama a este método cada vez que el mouse se mueve si `CWnd` contiene el cursor o ha capturado la entrada del mouse con `SetCapture`.|  
|[CWnd::OnNcLButtonDblClk](../Topic/CWnd::OnNcLButtonDblClk.md)|Se llama cuando el usuario hace doble clic en el botón primario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcLButtonDown](../Topic/CWnd::OnNcLButtonDown.md)|Se llama cuando el usuario presiona el botón primario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcLButtonUp](../Topic/CWnd::OnNcLButtonUp.md)|Se llama cuando el usuario suelta el botón primario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcMButtonDblClk](../Topic/CWnd::OnNcMButtonDblClk.md)|Se llama cuando el usuario hace doble clic en el botón central del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcMButtonDown](../Topic/CWnd::OnNcMButtonDown.md)|Se llama cuando el usuario presiona el botón central del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcMButtonUp](../Topic/CWnd::OnNcMButtonUp.md)|Se llama cuando el usuario suelta el botón central del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcMouseHover](../Topic/CWnd::OnNcMouseHover.md)|Se llama cuando el cursor se sitúa sobre el área no cliente de la ventana durante el período de tiempo especificado en una llamada anterior a [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265).|  
|[CWnd::OnNcMouseLeave](../Topic/CWnd::OnNcMouseLeave.md)|El marco llama a este método miembro cuando el cursor abandona el área no cliente de la ventana especificada en una llamada anterior a [TrackMouseEvent](http://msdn.microsoft.com/library/windows/desktop/ms646265).|  
|[CWnd::OnNcMouseMove](../Topic/CWnd::OnNcMouseMove.md)|Se llama cuando el cursor se mueve dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcPaint](../Topic/CWnd::OnNcPaint.md)|Se llama cuando es necesario pintar el área no cliente.|  
|[CWnd::OnNcRButtonDblClk](../Topic/CWnd::OnNcRButtonDblClk.md)|Se llama cuando el usuario hace doble clic en el botón secundario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcRButtonDown](../Topic/CWnd::OnNcRButtonDown.md)|Se llama cuando el usuario presiona el botón secundario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcRButtonUp](../Topic/CWnd::OnNcRButtonUp.md)|Se llama cuando el usuario suelta el botón secundario del mouse mientras el cursor se encuentra dentro de un área no cliente de `CWnd`.|  
|[CWnd::OnNcRenderingChanged](../Topic/CWnd::OnNcRenderingChanged.md)|Se llama cuando cambia la directiva de representación en el área no cliente.|  
|[CWnd::OnNcXButtonDblClk](../Topic/CWnd::OnNcXButtonDblClk.md)|Se llama cuando el usuario hace doble clic en XBUTTON1 o XBUTTON2 mientras el cursor se encuentra en el área no cliente de una ventana.|  
|[CWnd::OnNcXButtonDown](../Topic/CWnd::OnNcXButtonDown.md)|Se llama cuando el usuario presiona XBUTTON1 o XBUTTON2 del mouse mientras el cursor se encuentra en el área no cliente de una ventana.|  
|[CWnd::OnNcXButtonUp](../Topic/CWnd::OnNcXButtonUp.md)|Se llama cuando el usuario suelta XBUTTON1 o XBUTTON2 en el mouse mientras el cursor se encuentra en el área no cliente de una ventana.|  
|[CWnd::OnNextMenu](../Topic/CWnd::OnNextMenu.md)|Se llama cuando la tecla de dirección derecha o izquierda se usa para cambiar de la barra de menús al menú del sistema.|  
|[CWnd::OnNotify](../Topic/CWnd::OnNotify.md)|El marco llama a este método para informar a una ventana primaria de que se ha producido un evento en uno de sus controles o de que el control necesita información.|  
|[CWnd::OnNotifyFormat](../Topic/CWnd::OnNotifyFormat.md)|Se llama para averiguar si la ventana actual acepta estructuras ANSI o Unicode en el mensaje de notificación WM\_NOTIFY.|  
|[CWnd::OnPaint](../Topic/CWnd::OnPaint.md)|Se llama para volver a dibujar una parte de la ventana.|  
|[CWnd::OnPaintClipboard](../Topic/CWnd::OnPaintClipboard.md)|Se llama cuando es necesario volver a pintar el área cliente del visor del Portapapeles.|  
|[CWnd::OnPaletteChanged](../Topic/CWnd::OnPaletteChanged.md)|Se llama para permitir que las ventanas que usan una paleta de colores realicen sus paletas lógicas y actualicen sus áreas cliente.|  
|[CWnd::OnPaletteIsChanging](../Topic/CWnd::OnPaletteIsChanging.md)|Informa a otras aplicaciones cuando una aplicación va a realizar su paleta lógica.|  
|[CWnd::OnParentNotify](../Topic/CWnd::OnParentNotify.md)|Se llama cuando se crea o se destruye una ventana secundaria, o cuando el usuario hace clic en un botón del mouse mientras el cursor está sobre la ventana secundaria.|  
|[CWnd::OnPowerBroadcast](../Topic/CWnd::OnPowerBroadcast.md)|Se llama cuando se ocurre un evento de administración de energía.|  
|[CWnd::OnQueryDragIcon](../Topic/CWnd::OnQueryDragIcon.md)|Se llama cuando un objeto `CWnd` minimizado \(icono\) está a punto de ser arrastrado por el usuario.|  
|[CWnd::OnQueryEndSession](../Topic/CWnd::OnQueryEndSession.md)|Se llama cuando el usuario decide finalizar la sesión de Windows.|  
|[CWnd::OnQueryNewPalette](../Topic/CWnd::OnQueryNewPalette.md)|Informa a `CWnd` de que está a punto de recibir el foco de entrada.|  
|[CWnd::OnQueryOpen](../Topic/CWnd::OnQueryOpen.md)|Se llama cuando el objeto `CWnd` es un icono y el usuario solicita que se abra.|  
|[CWnd::OnQueryUIState](../Topic/CWnd::OnQueryUIState.md)|Se llama para recuperar el estado de la interfaz de usuario de una ventana.|  
|[CWnd::OnRawInput](../Topic/CWnd::OnRawInput.md)|Se llama cuando la ventana actual obtiene una entrada sin procesar.|  
|[CWnd::OnRButtonDblClk](../Topic/CWnd::OnRButtonDblClk.md)|Se llama cuando el usuario hace doble clic con el botón secundario del mouse.|  
|[CWnd::OnRButtonDown](../Topic/CWnd::OnRButtonDown.md)|Se llama cuando el usuario presiona el botón secundario del mouse.|  
|[CWnd::OnRButtonUp](../Topic/CWnd::OnRButtonUp.md)|Se llama cuando el usuario suelta el botón secundario del mouse.|  
|[CWnd::OnRenderAllFormats](../Topic/CWnd::OnRenderAllFormats.md)|Se llama cuando la aplicación del propietario se está destruyendo y necesita representar todos los formatos.|  
|[CWnd::OnRenderFormat](../Topic/CWnd::OnRenderFormat.md)|Se llama en relación con el propietario del Portapapeles cuando es necesario representar un formato determinado con representación aplazada.|  
|[CWnd::OnSessionChange](../Topic/CWnd::OnSessionChange.md)|Se llama para notificar a una aplicación de un cambio de estado de sesión.|  
|[CWnd::OnSetCursor](../Topic/CWnd::OnSetCursor.md)|Se llama si no se captura la entrada de mouse y el mouse provoca un movimiento de cursor dentro de una ventana.|  
|[CWnd::OnSetFocus](../Topic/CWnd::OnSetFocus.md)|Se llama después de que `CWnd` reciba el foco de entrada.|  
|[CWnd::OnSettingChange](../Topic/CWnd::OnSettingChange.md)|Se llama cuando la función `SystemParametersInfo` de Win32 cambia una configuración de todo el sistema.|  
|[CWnd::OnShowWindow](../Topic/CWnd::OnShowWindow.md)|Se llama cuando `CWnd` se oculta o se muestra.|  
|[CWnd::OnSize](../Topic/CWnd::OnSize.md)|Se llama después de que el tamaño de `CWnd` haya cambiado.|  
|[CWnd::OnSizeClipboard](../Topic/CWnd::OnSizeClipboard.md)|Se llama cuando ha cambiado el tamaño del área cliente de la ventana del visor del Portapapeles.|  
|[CWnd::OnSizing](../Topic/CWnd::OnSizing.md)|Indica que el usuario está cambiando el tamaño del rectángulo.|  
|[CWnd::OnSpoolerStatus](../Topic/CWnd::OnSpoolerStatus.md)|Se llama desde el Administrador de impresión cada vez que un trabajo se agrega a la cola del Administrador de impresión o se quita de ella.|  
|[CWnd::OnStyleChanged](../Topic/CWnd::OnStyleChanged.md)|Indica que la función de Windows [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) ha cambiado uno o varios de los estilos de ventana.|  
|[CWnd::OnStyleChanging](../Topic/CWnd::OnStyleChanging.md)|Indica que la función de Windows [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) va a cambiar uno o varios de los estilos de ventana.|  
|[CWnd::OnSysChar](../Topic/CWnd::OnSysChar.md)|Se llama cuando una pulsación de tecla se convierte en un carácter de sistema.|  
|[CWnd::OnSysColorChange](../Topic/CWnd::OnSysColorChange.md)|Se llama en relación con todas las ventanas de nivel superior cuando se realiza un cambio en la configuración de color del sistema.|  
|[CWnd::OnSysCommand](../Topic/CWnd::OnSysCommand.md)|Se llama cuando el usuario selecciona un comando en el menú de sistema, o cuando el usuario selecciona el botón para maximizar o minimizar.|  
|[CWnd::OnSysDeadChar](../Topic/CWnd::OnSysDeadChar.md)|Se llama cuando una pulsación de tecla se convierte en un carácter inactivo de sistema \(por ejemplo, caracteres acentuados\).|  
|[CWnd::OnSysKeyDown](../Topic/CWnd::OnSysKeyDown.md)|Se llama cuando el usuario mantiene presionada la tecla ALT y, luego, presiona otra tecla.|  
|[CWnd::OnSysKeyUp](../Topic/CWnd::OnSysKeyUp.md)|Se llama cuando el usuario suelta una tecla que se presionó mientras se presionaba la tecla ALT.|  
|[CWnd::OnTCard](../Topic/CWnd::OnTCard.md)|Se llama cuando el usuario hace clic en un botón que se puede modificar.|  
|[CWnd::OnTimeChange](../Topic/CWnd::OnTimeChange.md)|Se llama en relación con todas las ventanas de nivel superior después de cambiar la hora de sistema.|  
|[CWnd::OnTimer](../Topic/CWnd::OnTimer.md)|Se llama después de cada intervalo especificado en [SetTimer](../Topic/CWnd::SetTimer.md).|  
|[CWnd::OnTouchInput](../Topic/CWnd::OnTouchInput.md)|Procese una única entrada de tecnología táctil de Windows.|  
|[CWnd::OnTouchInputs](../Topic/CWnd::OnTouchInputs.md)|Procese entradas de tecnología táctil de Windows.|  
|[CWnd::OnUniChar](../Topic/CWnd::OnUniChar.md)|Se llama cuando se presiona una tecla.  Es decir, la ventana actual tiene el foco del teclado y un mensaje [WM\_KEYDOWN](http://msdn.microsoft.com/library/windows/desktop/ms646280) se convierte con la función [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955).|  
|[CWnd::OnUnInitMenuPopup](../Topic/CWnd::OnUnInitMenuPopup.md)|Se llama cuando se destruye un menú desplegable o submenú.|  
|[CWnd::OnUpdateUIState](../Topic/CWnd::OnUpdateUIState.md)|Se llama para cambiar el estado de la interfaz de usuario de la ventana especificada y de todas sus ventanas secundarias.|  
|[CWnd::OnUserChanged](../Topic/CWnd::OnUserChanged.md)|Se llama cuando el usuario inicia o cierra sesión.|  
|[CWnd::OnVKeyToItem](../Topic/CWnd::OnVKeyToItem.md)|Un cuadro de lista propiedad de `CWnd` llama a esta función en respuesta a un mensaje [WM\_KEYDOWN](../Topic/CWnd::OnKeyDown.md).|  
|[CWnd::OnVScroll](../Topic/CWnd::OnVScroll.md)|Se llama cuando el usuario hace clic en la barra de desplazamiento vertical de la ventana.|  
|[CWnd::OnVScrollClipboard](../Topic/CWnd::OnVScrollClipboard.md)|Se llama cuando el propietario tiene que desplazarse por la imagen del Portapapeles, invalidar la sección correspondiente y actualizar los valores de la barra de desplazamiento.|  
|[CWnd::OnWindowPosChanged](../Topic/CWnd::OnWindowPosChanged.md)|Se llama cuando el tamaño, la posición o el orden Z ha cambiado como resultado de una llamada a [SetWindowPos](../Topic/CWnd::SetWindowPos.md) o a otra función de administración de ventanas.|  
|[CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)|Se llama cuando el tamaño, la posición o el orden Z va a cambiar como resultado de una llamada a [SetWindowPos](../Topic/CWnd::SetWindowPos.md) o a otra función de administración de ventanas.|  
|[CWnd::OnWinIniChange](../Topic/CWnd::OnWinIniChange.md)|Se llama en relación con todas las ventanas de nivel superior después de que cambie el archivo de inicialización de Windows, WIN.INI.|  
|[CWnd::OnWndMsg](../Topic/CWnd::OnWndMsg.md)|Indica si se ha controlado un mensaje de ventana.|  
|[CWnd::OnXButtonDblClk](../Topic/CWnd::OnXButtonDblClk.md)|Se llama cuando el usuario hace doble clic en XBUTTON1 o XBUTTON2 mientras el cursor se encuentra en el área cliente de una ventana.|  
|[CWnd::OnXButtonDown](../Topic/CWnd::OnXButtonDown.md)|Se llama cuando el usuario presiona XBUTTON1 o XBUTTON2 mientras el cursor se encuentra en el área cliente de una ventana.|  
|[CWnd::OnXButtonUp](../Topic/CWnd::OnXButtonUp.md)|Se llama cuando el usuario suelta XBUTTON1 o XBUTTON2 mientras el cursor se encuentra en el área cliente de una ventana.|  
|[CWnd::PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)|La función predeterminada [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md) llama a esta función virtual después de que se haya destruido la ventana.|  
|[CWnd::ReflectChildNotify](../Topic/CWnd::ReflectChildNotify.md)|Función auxiliar que refleja un mensaje a su origen.|  
|[CWnd::ReflectLastMsg](../Topic/CWnd::ReflectLastMsg.md)|Refleja el último mensaje a la ventana secundaria.|  
|[CWnd::ResizeDynamicLayout](../Topic/CWnd::ResizeDynamicLayout.md)|El marco llama a este método cuando el tamaño de la ventana cambia para ajustar el diseño de las ventanas secundarias, si el diseño dinámico está habilitado en esa ventana.|  
|[CWnd::WindowProc](../Topic/CWnd::WindowProc.md)|Proporciona un procedimiento de ventana para un objeto `CWnd`.  El valor predeterminado envía mensajes a través del mapa de mensajes.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWnd::operator HWND](../Topic/CWnd::operator%20HWND.md)|Llame para obtener un identificador de una ventana.|  
|[CWnd::operator \!\=](../Topic/CWnd::operator%20!=.md)|Determina si una ventana no es la misma que la ventana cuyo identificador es [m\_hWnd](../Topic/CWnd::m_hWnd.md).|  
|[CWnd::operator \=\=](../Topic/CWnd::operator%20==.md)|Determina si una ventana es la misma que la ventana cuyo identificador es [m\_hWnd](../Topic/CWnd::m_hWnd.md).|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWnd::m\_hWnd](../Topic/CWnd::m_hWnd.md)|Indica el objeto `HWND` asociado a este objeto `CWnd`.|  
  
## Comentarios  
 Un objeto `CWnd` es distinto de una ventana de Windows, pero los dos están estrechamente vinculados.  El constructor y destructor `CWnd` crea o destruye un objeto `CWnd`.  La ventana de Windows, por su parte, es una estructura de datos interna de Windows que se crea con una función miembro **Create** y se destruye con el destructor virtual `CWnd`.  La función [DestroyWindow](../Topic/CWnd::DestroyWindow.md) destruye la ventana de Windows sin destruir el objeto.  
  
 La clase `CWnd` y el mecanismo de mapa de mensajes ocultan la función **WndProc**.  Los mensajes de notificación de Windows entrantes se enrutan automáticamente con el mapa de mensajes a las funciones miembro de `CWnd` **On***Message* correspondientes.  Las funciones miembro **On***Message* se invalidan para administrar un mensaje particular de un miembro en sus clases derivadas.  
  
 Con la clase `CWnd` también se puede crear una ventana secundaria de Windows para la aplicación.  Derive una clase de `CWnd` y, luego, agregue variables miembro a esa clase derivada para almacenar datos específicos de la aplicación.  Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Una ventana secundaria se crea en dos pasos.  En primer lugar, llame al constructor de `CWnd` para construir el objeto `CWnd`, llame a la función miembro [Create](../Topic/CWnd::Create.md) para crear la ventana secundaria y asóciela al objeto `CWnd`.  
  
 Cuando el usuario finalice la ventana secundaria, destruya el objeto `CWnd` o llame a la función miembro `DestroyWindow` para quitar la ventana y destruir sus estructuras de datos.  
  
 Dentro de la biblioteca MFC \(Microsoft Foundation Class\), se derivan más clases de `CWnd` para proporcionar tipos de ventana específicos.  Muchas de estas clases, como [CFrameWnd](../../mfc/reference/cframewnd-class.md), [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md), [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md), [CView](../../mfc/reference/cview-class.md) y [CDialog](../../mfc/reference/cdialog-class.md), están diseñadas para seguir derivándose.  Las clases de control derivadas de `CWnd`, como [CButton](../../mfc/reference/cbutton-class.md), se pueden usar directamente o bien emplearse para derivar clases aún más.  
  
 Para obtener más información sobre cómo usar `CWnd`, vea [Ventanas de marco](../../mfc/frame-windows.md) y [Objetos de ventana](../../mfc/window-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWnd`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)