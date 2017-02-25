---
title: "CWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CWindow"
  - "ATL::CWindow"
  - "CWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindow class"
ms.assetid: fefa00c8-f053-4bcf-87bc-dc84f5386683
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para manipular una ventana.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CWindow  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWindow::CWindow](../Topic/CWindow::CWindow.md)|Constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWindow::ArrangeIconicWindows](../Topic/CWindow::ArrangeIconicWindows.md)|organiza todas las ventanas secundarias minimizadas.|  
|[CWindow::Attach](../Topic/CWindow::Attach.md)|Adjunta una ventana al objeto de `CWindow` .|  
|[CWindow::BeginPaint](../Topic/CWindow::BeginPaint.md)|prepara la ventana para pintar.|  
|[CWindow::BringWindowToTop](../Topic/CWindow::BringWindowToTop.md)|Trae la en la parte superior del orden Z.|  
|[CWindow::CenterWindow](../Topic/CWindow::CenterWindow.md)|Centra la ventana en una ventana especificada.|  
|[CWindow::ChangeClipboardChain](../Topic/CWindow::ChangeClipboardChain.md)|Quita la ventana de la cadena de visores del Portapapeles.|  
|[CWindow::CheckDlgButton](../Topic/CWindow::CheckDlgButton.md)|Cambia el estado de activación del botón especificado.|  
|[CWindow::CheckRadioButton](../Topic/CWindow::CheckRadioButton.md)|Comprueba el botón de radio especificado.|  
|[CWindow::ChildWindowFromPoint](../Topic/CWindow::ChildWindowFromPoint.md)|recupera la ventana secundaria que contiene el punto especificado.|  
|[CWindow::ChildWindowFromPointEx](../Topic/CWindow::ChildWindowFromPointEx.md)|Recupera un tipo determinado de ventana secundaria que contiene el punto especificado.|  
|[CWindow::ClientToScreen](../Topic/CWindow::ClientToScreen.md)|Convierte las coordenadas de cliente a coordenadas de pantalla.|  
|[CWindow::Create](../Topic/CWindow::Create.md)|crea una ventana.|  
|[CWindow::CreateCaret](../Topic/CWindow::CreateCaret.md)|crea una nueva forma para el símbolo de intercalación.|  
|[CWindow::CreateGrayCaret](../Topic/CWindow::CreateGrayCaret.md)|crea un rectángulo deshabilitado para el símbolo de intercalación.|  
|[CWindow::CreateSolidCaret](../Topic/CWindow::CreateSolidCaret.md)|crea un rectángulo sólido para el símbolo de intercalación.|  
|[CWindow::DeferWindowPos](../Topic/CWindow::DeferWindowPos.md)|actualiza la estructura especificada de la múltiple\-ventana\-posición para la ventana especificada.|  
|[CWindow::DestroyWindow](../Topic/CWindow::DestroyWindow.md)|Destruye la ventana asociada con el objeto de `CWindow` .|  
|[CWindow::Detach](../Topic/CWindow::Detach.md)|Desconecte la ventana del objeto de `CWindow` .|  
|[CWindow::DlgDirList](../Topic/CWindow::DlgDirList.md)|Llena un cuadro de lista con los nombres de todos los archivos que coinciden con una ruta de acceso especificada o un nombre de archivo.|  
|[CWindow::DlgDirListComboBox](../Topic/CWindow::DlgDirListComboBox.md)|Llena un cuadro combinado con los nombres de todos los archivos que coinciden con una ruta de acceso especificada o un nombre de archivo.|  
|[CWindow::DlgDirSelect](../Topic/CWindow::DlgDirSelect.md)|recupera la selección actual de un cuadro de lista.|  
|[CWindow::DlgDirSelectComboBox](../Topic/CWindow::DlgDirSelectComboBox.md)|recupera la selección actual de un cuadro combinado.|  
|[CWindow::DragAcceptFiles](../Topic/CWindow::DragAcceptFiles.md)|Registra si la ventana acepta archivos arrastrados.|  
|[CWindow::DrawMenuBar](../Topic/CWindow::DrawMenuBar.md)|Redibuja la barra de menús de la ventana.|  
|[CWindow::EnableScrollBar](../Topic/CWindow::EnableScrollBar.md)|Habilita o deshabilita las flechas de la barra de desplazamiento.|  
|[CWindow::EnableWindow](../Topic/CWindow::EnableWindow.md)|Habilita o deshabilita entrada.|  
|[CWindow::EndPaint](../Topic/CWindow::EndPaint.md)|Marca el final de dibujo.|  
|[CWindow::FlashWindow](../Topic/CWindow::FlashWindow.md)|inicia la ventana una vez.|  
|[CWindow::GetClientRect](../Topic/CWindow::GetClientRect.md)|Recupera las coordenadas del área de cliente.|  
|[CWindow::GetDC](../Topic/CWindow::GetDC.md)|Recupera un contexto para el área de cliente.|  
|[CWindow::GetDCEx](../Topic/CWindow::GetDCEx.md)|Recupera un contexto para el área cliente y permite el recorte de opciones.|  
|[CWindow::GetDescendantWindow](../Topic/CWindow::GetDescendantWindow.md)|Recupera la ventana especificada descendientes.|  
|[CWindow::GetDlgControl](../Topic/CWindow::GetDlgControl.md)|recupera una interfaz en el control especificado.|  
|[CWindow::GetDlgCtrlID](../Topic/CWindow::GetDlgCtrlID.md)|Recupera el identificador de la ventana \(para las ventanas secundarias solo\).|  
|[CWindow::GetDlgHost](../Topic/CWindow::GetDlgHost.md)|Recupera un puntero a una interfaz al Control ATL que hospeda el contenedor.|  
|[CWindow::GetDlgItem](../Topic/CWindow::GetDlgItem.md)|recupera la ventana secundaria especificada.|  
|[CWindow::GetDlgItemInt](../Topic/CWindow::GetDlgItemInt.md)|traduce el texto de un control a un entero.|  
|[CWindow::GetDlgItemText](../Topic/CWindow::GetDlgItemText.md)|recupera el texto de un control.|  
|[CWindow::GetExStyle](../Topic/CWindow::GetExStyle.md)|Recupera los estilos de ventana extendidas.|  
|[CWindow::GetFont](../Topic/CWindow::GetFont.md)|recupera la fuente actual de la ventana.|  
|[CWindow::GetHotKey](../Topic/CWindow::GetHotKey.md)|Determina la tecla de acceso rápido asociado a la ventana.|  
|[CWindow::GetIcon](../Topic/CWindow::GetIcon.md)|Recupera el icono o pequeño de la ventana.|  
|[CWindow::GetLastActivePopup](../Topic/CWindow::GetLastActivePopup.md)|Recupera la ventana emergente activo más recientemente.|  
|[CWindow::GetMenu](../Topic/CWindow::GetMenu.md)|Recupera el menú de la ventana.|  
|[CWindow::GetNextDlgGroupItem](../Topic/CWindow::GetNextDlgGroupItem.md)|Recupera el control siguiente o anterior dentro de un grupo de controles.|  
|[CWindow::GetNextDlgTabItem](../Topic/CWindow::GetNextDlgTabItem.md)|recupera el control anterior o siguiente que tiene el estilo de **WS\_TABSTOP** .|  
|[CWindow::GetParent](../Topic/CWindow::GetParent.md)|recupera la ventana primaria inmediata.|  
|[CWindow::GetScrollInfo](../Topic/CWindow::GetScrollInfo.md)|recupera los parámetros de una barra de desplazamiento.|  
|[CWindow::GetScrollPos](../Topic/CWindow::GetScrollPos.md)|Recupera la posición del cuadro de desplazamiento.|  
|[CWindow::GetScrollRange](../Topic/CWindow::GetScrollRange.md)|recupera el intervalo de la barra de desplazamiento.|  
|[CWindow::GetStyle](../Topic/CWindow::GetStyle.md)|Recupera los estilos de ventana.|  
|[CWindow::GetSystemMenu](../Topic/CWindow::GetSystemMenu.md)|Crea una copia del menú sistema para modificarlo.|  
|[CWindow::GetTopLevelParent](../Topic/CWindow::GetTopLevelParent.md)|Recupera la ventana de nivel superior del elemento primario o propietario.|  
|[CWindow::GetTopLevelWindow](../Topic/CWindow::GetTopLevelWindow.md)|Recupera la ventana de nivel superior del propietario.|  
|[CWindow::GetTopWindow](../Topic/CWindow::GetTopWindow.md)|Recupera la ventana secundaria de nivel superior.|  
|[CWindow::GetUpdateRect](../Topic/CWindow::GetUpdateRect.md)|Recupera las coordenadas del rectángulo menor que agrega completamente la región de actualización.|  
|[CWindow::GetUpdateRgn](../Topic/CWindow::GetUpdateRgn.md)|Recupera la región de actualización y la copia en un área concreta.|  
|[CWindow::GetWindow](../Topic/CWindow::GetWindow.md)|recupera la ventana especificada.|  
|[CWindow::GetWindowContextHelpId](../Topic/CWindow::GetWindowContextHelpId.md)|Recupera el identificador de contexto de ayuda de la ventana.|  
|[CWindow::GetWindowDC](../Topic/CWindow::GetWindowDC.md)|Recupera un contexto para la ventana completa.|  
|[CWindow::GetWindowLong](../Topic/CWindow::GetWindowLong.md)|recupera un valor de 32 bits en un desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::GetWindowLongPtr](../Topic/CWindow::GetWindowLongPtr.md)|Recupera información sobre la ventana especificada, incluido un valor en un desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::GetWindowPlacement](../Topic/CWindow::GetWindowPlacement.md)|Recupera el estado y las posiciones de presentación.|  
|[CWindow::GetWindowProcessID](../Topic/CWindow::GetWindowProcessID.md)|Recupera el identificador de proceso que creó la ventana.|  
|[CWindow::GetWindowRect](../Topic/CWindow::GetWindowRect.md)|recupera las dimensiones de limitación de la ventana.|  
|[CWindow::GetWindowRgn](../Topic/CWindow::GetWindowRgn.md)|obtiene una copia de la región de la ventana de una ventana.|  
|[CWindow::GetWindowText](../Topic/CWindow::GetWindowText.md)|recupera el texto de la ventana.|  
|[CWindow::GetWindowTextLength](../Topic/CWindow::GetWindowTextLength.md)|Recupera la longitud del texto de la ventana.|  
|[CWindow::GetWindowThreadID](../Topic/CWindow::GetWindowThreadID.md)|Recupera el identificador del subproceso que creó la ventana especificada.|  
|[CWindow::GetWindowWord](../Topic/CWindow::GetWindowWord.md)|recupera un valor de 16 bits en un desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::GotoDlgCtrl](../Topic/CWindow::GotoDlgCtrl.md)|Establece el foco de teclado a un control en el cuadro de diálogo.|  
|[CWindow::HideCaret](../Topic/CWindow::HideCaret.md)|oculta el símbolo de intercalación.|  
|[CWindow::HiliteMenuItem](../Topic/CWindow::HiliteMenuItem.md)|Resalta o quita el resaltado de un elemento de menú de nivel superior.|  
|[CWindow::Invalidate](../Topic/CWindow::Invalidate.md)|Reemplaza el área cliente completa.|  
|[CWindow::InvalidateRect](../Topic/CWindow::InvalidateRect.md)|Reemplaza el área cliente dentro del rectángulo especificado.|  
|[CWindow::InvalidateRgn](../Topic/CWindow::InvalidateRgn.md)|Reemplaza el área cliente de la región especificada.|  
|[CWindow::IsChild](../Topic/CWindow::IsChild.md)|determina si la ventana especificada es una ventana secundaria.|  
|[CWindow::IsDialogMessage](../Topic/CWindow::IsDialogMessage.md)|Determina si un mensaje está diseñado para el cuadro de diálogo especificado.|  
|[CWindow::IsDlgButtonChecked](../Topic/CWindow::IsDlgButtonChecked.md)|Determina el estado de la comprobación del botón.|  
|[CWindow::IsIconic](../Topic/CWindow::IsIconic.md)|determina si la ventana está minimizada.|  
|[CWindow::IsParentDialog](../Topic/CWindow::IsParentDialog.md)|Determina si la ventana primaria de un control es una ventana de cuadro de diálogo.|  
|[CWindow::IsWindow](../Topic/CWindow::IsWindow.md)|determina si el identificador de ventana especificado identifica una ventana existente.|  
|[CWindow::IsWindowEnabled](../Topic/CWindow::IsWindowEnabled.md)|determina si la ventana está habilitada para la entrada.|  
|[CWindow::IsWindowUnicode](../Topic/CWindow::IsWindowUnicode.md)|determina si la ventana especificada es una ventana nativa de Unicode.|  
|[CWindow::IsWindowVisible](../Topic/CWindow::IsWindowVisible.md)|Determina el estado de visibilidad de la ventana.|  
|[CWindow::IsZoomed](../Topic/CWindow::IsZoomed.md)|determina si la ventana está maximizada.|  
|[CWindow::KillTimer](../Topic/CWindow::KillTimer.md)|Destruye un evento de temporizador.|  
|[CWindow::LockWindowUpdate](../Topic/CWindow::LockWindowUpdate.md)|Deshabilita o habilita el diagrama en la ventana.|  
|[CWindow::MapWindowPoints](../Topic/CWindow::MapWindowPoints.md)|Convierte un conjunto de puntos del espacio de coordenadas de la ventana al espacio de coordenadas de otra ventana.|  
|[CWindow::MessageBox](../Topic/CWindow::MessageBox.md)|Muestra un cuadro de mensaje.|  
|[CWindow::ModifyStyle](../Topic/CWindow::ModifyStyle.md)|Modifica los estilos de ventana.|  
|[CWindow::ModifyStyleEx](../Topic/CWindow::ModifyStyleEx.md)|Modifica los estilos de ventana extendidas.|  
|[CWindow::MoveWindow](../Topic/CWindow::MoveWindow.md)|Cambia el tamaño y la posición de la ventana.|  
|[CWindow::NextDlgCtrl](../Topic/CWindow::NextDlgCtrl.md)|Establece el foco de teclado al control siguiente en el cuadro de diálogo.|  
|[CWindow::OpenClipboard](../Topic/CWindow::OpenClipboard.md)|Abra el portapapeles.|  
|[CWindow::PostMessage](../Topic/CWindow::PostMessage.md)|Coloca un mensaje en la cola de mensajes asociado al subproceso que creó la ventana.  vuelve sin esperar el subproceso para procesar el mensaje.|  
|[CWindow::PrevDlgCtrl](../Topic/CWindow::PrevDlgCtrl.md)|Establece el foco de teclado al control anterior en el cuadro de diálogo.|  
|[CWindow::Print](../Topic/CWindow::Print.md)|Las solicitudes que la ventana se dibujan en un contexto especificado del dispositivo.|  
|[CWindow::PrintClient](../Topic/CWindow::PrintClient.md)|Las solicitudes que el área de cliente de la ventana se dibujan en un contexto especificado del dispositivo.|  
|[CWindow::RedrawWindow](../Topic/CWindow::RedrawWindow.md)|actualiza un rectángulo o una región especificado en el área cliente.|  
|[CWindow::ReleaseDC](../Topic/CWindow::ReleaseDC.md)|Libere un contexto de dispositivo.|  
|[CWindow::ResizeClient](../Topic/CWindow::ResizeClient.md)|Cambia el tamaño de la ventana.|  
|[CWindow::ScreenToClient](../Topic/CWindow::ScreenToClient.md)|Convierte las coordenadas de pantalla a coordenadas de cliente.|  
|[CWindow::ScrollWindow](../Topic/CWindow::ScrollWindow.md)|desplaza el área cliente especificada.|  
|[CWindow::ScrollWindowEx](../Topic/CWindow::ScrollWindowEx.md)|Desplaza el área cliente especificada con características adicionales.|  
|[CWindow::SendDlgItemMessage](../Topic/CWindow::SendDlgItemMessage.md)|envía un mensaje a un control.|  
|[CWindow::SendMessage](../Topic/CWindow::SendMessage.md)|Envía un mensaje en la y no vuelve hasta que el procedimiento de ventana haya procesado el mensaje.|  
|[CWindow::SendMessageToDescendants](../Topic/CWindow::SendMessageToDescendants.md)|Envía un mensaje a las ventanas especificadas descendientes.|  
|[CWindow::SendNotifyMessage](../Topic/CWindow::SendNotifyMessage.md)|Envía un mensaje en la ventana.  Si la ventana creada por el subproceso de la llamada, `SendNotifyMessage` no vuelve hasta que el procedimiento de ventana haya procesado el mensaje.  si no, vuelve inmediatamente.|  
|[CWindow::SetActiveWindow](../Topic/CWindow::SetActiveWindow.md)|activa la ventana.|  
|[CWindow::SetCapture](../Topic/CWindow::SetCapture.md)|Envía toda la entrada subsiguiente del mouse en la ventana.|  
|[CWindow::SetClipboardViewer](../Topic/CWindow::SetClipboardViewer.md)|Agrega la ventana a la cadena del visor del Portapapeles.|  
|[CWindow::SetDlgCtrlID](../Topic/CWindow::SetDlgCtrlID.md)|cambia el identificador de la ventana.|  
|[CWindow::SetDlgItemInt](../Topic/CWindow::SetDlgItemInt.md)|Cambia el texto de un control en la representación de cadena de un valor entero.|  
|[CWindow::SetDlgItemText](../Topic/CWindow::SetDlgItemText.md)|cambia el texto de un control.|  
|[CWindow::SetFocus](../Topic/CWindow::SetFocus.md)|Establece el foco a la ventana.|  
|[CWindow::SetFont](../Topic/CWindow::SetFont.md)|Cambiar la fuente actual de la ventana.|  
|[CWindow::SetHotKey](../Topic/CWindow::SetHotKey.md)|asocia una tecla de acceso rápido a la ventana.|  
|[CWindow::SetIcon](../Topic/CWindow::SetIcon.md)|Cambia el icono o pequeño de la ventana.|  
|[CWindow::SetMenu](../Topic/CWindow::SetMenu.md)|cambia el menú actual de la ventana.|  
|[CWindow::SetParent](../Topic/CWindow::SetParent.md)|cambia la ventana primaria.|  
|[CWindow::SetRedraw](../Topic/CWindow::SetRedraw.md)|Establece o desactive el marcador actualizar.|  
|[CWindow::SetScrollInfo](../Topic/CWindow::SetScrollInfo.md)|establece los parámetros de una barra de desplazamiento.|  
|[CWindow::SetScrollPos](../Topic/CWindow::SetScrollPos.md)|Cambia la posición del cuadro de desplazamiento.|  
|[CWindow::SetScrollRange](../Topic/CWindow::SetScrollRange.md)|cambia el intervalo de la barra de desplazamiento.|  
|[CWindow::SetTimer](../Topic/CWindow::SetTimer.md)|Crea un evento de temporizador.|  
|[CWindow::SetWindowContextHelpId](../Topic/CWindow::SetWindowContextHelpId.md)|Establece el identificador de contexto de ayuda de la ventana.|  
|[CWindow::SetWindowLong](../Topic/CWindow::SetWindowLong.md)|establece un valor de 32 bits en un desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::SetWindowLongPtr](../Topic/CWindow::SetWindowLongPtr.md)|cambia un atributo de la ventana especificada, y también establece un valor en el desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::SetWindowPlacement](../Topic/CWindow::SetWindowPlacement.md)|Establece el estado y las posiciones de presentación.|  
|[CWindow::SetWindowPos](../Topic/CWindow::SetWindowPos.md)|Establece el tamaño, la posición, y el orden Z.|  
|[CWindow::SetWindowRgn](../Topic/CWindow::SetWindowRgn.md)|establece la región de la ventana de una ventana.|  
|[CWindow::SetWindowText](../Topic/CWindow::SetWindowText.md)|cambia el texto de la ventana.|  
|[CWindow::SetWindowWord](../Topic/CWindow::SetWindowWord.md)|establece un valor de 16 bits en un desplazamiento especificado en memoria adicional de la ventana.|  
|[CWindow::ShowCaret](../Topic/CWindow::ShowCaret.md)|Muestra el símbolo de intercalación.|  
|[CWindow::ShowOwnedPopups](../Topic/CWindow::ShowOwnedPopups.md)|Muestra u oculta las ventanas emergentes son propiedad de la ventana.|  
|[CWindow::ShowScrollBar](../Topic/CWindow::ShowScrollBar.md)|Muestra u oculta una barra de desplazamiento.|  
|[CWindow::ShowWindow](../Topic/CWindow::ShowWindow.md)|Establece el estado de la ventana.|  
|[CWindow::ShowWindowAsync](../Topic/CWindow::ShowWindowAsync.md)|Establece el estado de una ventana creada por un subproceso diferente.|  
|[CWindow::UpdateWindow](../Topic/CWindow::UpdateWindow.md)|actualiza el área cliente.|  
|[CWindow::ValidateRect](../Topic/CWindow::ValidateRect.md)|Valida el área cliente dentro del rectángulo especificado.|  
|[CWindow::ValidateRgn](../Topic/CWindow::ValidateRgn.md)|Valida el área cliente de la región especificada.|  
|[CWindow::WinHelp](../Topic/CWindow::WinHelp.md)|Ayuda de Windows de inicio.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWindow::operator HWND](../Topic/CWindow::operator%20HWND.md)|convierte el objeto de `CWindow` a `HWND`.|  
|[CWindow::operator \=](../Topic/CWindow::operator%20=.md)|Asigna `HWND` al objeto de `CWindow` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWindow::m\_hWnd](../Topic/CWindow::m_hWnd.md)|El identificador de la ventana asociada con el objeto de `CWindow` .|  
|[CWindow::rcDefault](../Topic/CWindow::rcDefault.md)|contiene dimensiones predeterminadas de la ventana.|  
  
## Comentarios  
 `CWindow` proporciona la funcionalidad básica para manipular una ventana en ATL.  Muchos de ajuste uno de los métodos de `CWindow` de la API Win32 funcionan simplemente.  por ejemplo, compare los prototipos para `CWindow::ShowWindow` y `ShowWindow`:  
  
|método de CWindow|función de Win32|  
|-----------------------|----------------------|  
|**BOOL ShowWindow\( int**  `nCmdShow`\);|**BOOL ShowWindow\( HWND**  `hWnd` **, int**  `nCmdShow`\);|  
  
 `CWindow::ShowWindow` llama a la función `ShowWindow` Win32 pasando `CWindow::m_hWnd` como primer parámetro.  Cada método de `CWindow` que incluye directamente una función Win32 pasa al miembro de `m_hWnd` ; por consiguiente, gran parte de la documentación de `CWindow` verá a [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
> [!NOTE]
>  No cada función ventana\-relacionada Win32 es ajustada por `CWindow`, y los ajustes de no cada método de `CWindow` una función de Win32.  
  
 `CWindow::m_hWnd` almacena `HWND` que identifica una ventana.  `HWND` se adjunta el objeto cuando:  
  
-   especifique `HWND` en el constructor de los entity\_CWindow.  
  
-   Llamar a `CWindow::Attach`.  
  
-   **operador \=**de los entity\_CWindow de uso.  
  
-   Cree o cree subclases de una ventana mediante una de las siguientes clases derivadas de `CWindow`:  
  
     [CWindowImpl](../../atl/reference/cwindowimpl-class.md) Allow permite crear una nueva ventana o crear subclases de una ventana existente.  
  
     [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) implementa una ventana contenida dentro de otro objeto.  Puede crear una nueva ventana o crear subclases de una ventana existente.  
  
     [CDialogImpl](../../atl/reference/cdialogimpl-class.md) Allow permite crear un cuadro de diálogo modal o no modal.  
  
 Para obtener más información sobre las ventanas, vea [Ventanas](http://msdn.microsoft.com/library/windows/desktop/ms632595) y los temas siguientes en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  Para obtener más información sobre cómo utilizar las ventanas en ATL, vea el artículo [Clases de ventana ATL](../../atl/atl-window-classes.md).  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)