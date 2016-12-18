---
title: "COleControl Class | Microsoft Docs"
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
  - "COleControl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControl class"
  - "controles [MFC], OLE"
  - "controles [MFC], windowless"
  - "controles OLE, MFC"
  - "windowless controls"
  - "windowless controls, MFC"
ms.assetid: 53e95299-38e8-447b-9c5f-a381d27f5123
caps.latest.revision: 25
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleControl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase base eficaz para controles OLE que se convierten.  
  
## Sintaxis  
  
```  
class COleControl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControl::COleControl](../Topic/COleControl::COleControl.md)|Crea un objeto `COleControl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControl::AmbientAppearance](../Topic/COleControl::AmbientAppearance.md)|Recupera el aspecto del control actual.|  
|[COleControl::AmbientBackColor](../Topic/COleControl::AmbientBackColor.md)|devuelve el valor de la propiedad BackColor ambiente.|  
|[COleControl::AmbientDisplayName](../Topic/COleControl::AmbientDisplayName.md)|Devuelve el nombre del control según lo especificado por el contenedor.|  
|[COleControl::AmbientFont](../Topic/COleControl::AmbientFont.md)|Devuelve el valor de la propiedad de fuente ambiente.|  
|[COleControl::AmbientForeColor](../Topic/COleControl::AmbientForeColor.md)|Devuelve el valor de la propiedad ForeColor de ambiente.|  
|[COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md)|Devuelve el identificador de la configuración regional del contenedor|  
|[COleControl::AmbientScaleUnits](../Topic/COleControl::AmbientScaleUnits.md)|devuelve el tipo de unidades utilizadas por el contenedor.|  
|[COleControl::AmbientShowGrabHandles](../Topic/COleControl::AmbientShowGrabHandles.md)|Determina si se muestran los controladores de arrastre.|  
|[COleControl::AmbientShowHatching](../Topic/COleControl::AmbientShowHatching.md)|Determina si se muestra la trama.|  
|[COleControl::AmbientTextAlign](../Topic/COleControl::AmbientTextAlign.md)|Devuelve el tipo de alineación del texto especificado en el contenedor.|  
|[COleControl::AmbientUIDead](../Topic/COleControl::AmbientUIDead.md)|Determina si el control responde a las acciones de la interfaz de usuario.|  
|[COleControl::AmbientUserMode](../Topic/COleControl::AmbientUserMode.md)|Determina el modo del contenedor.|  
|[COleControl::BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md)|Notifica al contenedor que se ha cambiado una propiedad enlazada.|  
|[COleControl::BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md)|Solicita permiso para modificar el valor de propiedad.|  
|[COleControl::ClientToParent](../Topic/COleControl::ClientToParent.md)|Convierte un punto en relación con el origen del control a un punto en relación con el origen del contenedor.|  
|[COleControl::ClipCaretRect](../Topic/COleControl::ClipCaretRect.md)|Ajusta un rectángulo del símbolo de intercalación si es superpuesto por un control.|  
|[COleControl::ControlInfoChanged](../Topic/COleControl::ControlInfoChanged.md)|Llame a esta función después del conjunto de teclas controlado por el control ha cambiado.|  
|[COleControl::DisplayError](../Topic/COleControl::DisplayError.md)|Muestra almacenan eventos Error al usuario del control.|  
|[COleControl::DoClick](../Topic/COleControl::DoClick.md)|Implementación del método común de `DoClick` .|  
|[COleControl::DoPropExchange](../Topic/COleControl::DoPropExchange.md)|Serializa las propiedades de un objeto de `COleControl` .|  
|[COleControl::DoSuperclassPaint](../Topic/COleControl::DoSuperclassPaint.md)|Rediseña un control OLE que se ha derivado de un control de Windows.|  
|[COleControl::EnableSimpleFrame](../Topic/COleControl::EnableSimpleFrame.md)|Compatibilidad simple del cuadro de permisos para un control.|  
|[COleControl::ExchangeExtent](../Topic/COleControl::ExchangeExtent.md)|Serializa el ancho y el alto del control.|  
|[COleControl::ExchangeStockProps](../Topic/COleControl::ExchangeStockProps.md)|Serializa las propiedades estándar de control.|  
|[COleControl::ExchangeVersion](../Topic/COleControl::ExchangeVersion.md)|Serializa el número de versión del control.|  
|[COleControl::FireClick](../Topic/COleControl::FireClick.md)|Desencadena el evento común de `Click` .|  
|[COleControl::FireDblClick](../Topic/COleControl::FireDblClick.md)|Desencadena el evento común de `DblClick` .|  
|[COleControl::FireError](../Topic/COleControl::FireError.md)|Desencadena el evento común de `Error` .|  
|[COleControl::FireEvent](../Topic/COleControl::FireEvent.md)|Desencadena un evento personalizado.|  
|[COleControl::FireKeyDown](../Topic/COleControl::FireKeyDown.md)|Desencadena el evento común de `KeyDown` .|  
|[COleControl::FireKeyPress](../Topic/COleControl::FireKeyPress.md)|Desencadena el evento común de `KeyPress` .|  
|[COleControl::FireKeyUp](../Topic/COleControl::FireKeyUp.md)|Desencadena el evento común de `KeyUp` .|  
|[COleControl::FireMouseDown](../Topic/COleControl::FireMouseDown.md)|Desencadena el evento común de `MouseDown` .|  
|[COleControl::FireMouseMove](../Topic/COleControl::FireMouseMove.md)|Desencadena el evento común de `MouseMove` .|  
|[COleControl::FireMouseUp](../Topic/COleControl::FireMouseUp.md)|Desencadena el evento común de `MouseUp` .|  
|[COleControl::FireReadyStateChange](../Topic/COleControl::FireReadyStateChange.md)|Activa un evento cuando cambia el estado listo del control.|  
|[COleControl::GetActivationPolicy](../Topic/COleControl::GetActivationPolicy.md)|Modifica el comportamiento predeterminado de activación de un control que admita la interfaz de `IPointerInactive` .|  
|[COleControl::GetAmbientProperty](../Topic/COleControl::GetAmbientProperty.md)|Devuelve el valor de propiedad de ambiente especificada.|  
|[COleControl::GetAppearance](../Topic/COleControl::GetAppearance.md)|Devuelve el valor de la propiedad de apariencia común.|  
|[COleControl::GetBackColor](../Topic/COleControl::GetBackColor.md)|Devuelve el valor de la propiedad BackColor común.|  
|[COleControl::GetBorderStyle](../Topic/COleControl::GetBorderStyle.md)|Devuelve el valor de la propiedad común BorderStyle.|  
|[COleControl::GetCapture](../Topic/COleControl::GetCapture.md)|Determina si un objeto sin ventana, se genera el control tiene la captura del mouse.|  
|[COleControl::GetClassID](../Topic/COleControl::GetClassID.md)|Recupera el id. de clase OLE del control.|  
|[COleControl::GetClientOffset](../Topic/COleControl::GetClientOffset.md)|Recupera la diferencia entre la esquina superior izquierda del área rectangular de control y la esquina superior izquierda del área cliente.|  
|[COleControl::GetClientRect](../Topic/COleControl::GetClientRect.md)|Recupera el tamaño del área de cliente del control.|  
|[COleControl::GetClientSite](../Topic/COleControl::GetClientSite.md)|Consultas un objeto para el puntero al sitio actual del cliente dentro de su contenedor.|  
|[COleControl::GetControlFlags](../Topic/COleControl::GetControlFlags.md)|Recupera los valores de marcador del control.|  
|[COleControl::GetControlSize](../Topic/COleControl::GetControlSize.md)|Devuelve la posición y el tamaño de controles activex.|  
|[COleControl::GetDC](../Topic/COleControl::GetDC.md)|Proporciona los medios para que un control sin ventana obtenga un contexto de dispositivo de su contenedor.|  
|[COleControl::GetEnabled](../Topic/COleControl::GetEnabled.md)|Devuelve el valor de la propiedad enabled común.|  
|[COleControl::GetExtendedControl](../Topic/COleControl::GetExtendedControl.md)|Recupera un puntero a un objeto extendido de control que pertenece al contenedor.|  
|[COleControl::GetFocus](../Topic/COleControl::GetFocus.md)|Determina si el control tiene el foco.|  
|[COleControl::GetFont](../Topic/COleControl::GetFont.md)|Devuelve el valor de la propiedad de fuente común.|  
|[COleControl::GetFontTextMetrics](../Topic/COleControl::GetFontTextMetrics.md)|Devuelve métricas de un objeto de `CFontHolder` .|  
|[COleControl::GetForeColor](../Topic/COleControl::GetForeColor.md)|Devuelve el valor de la propiedad ForeColor común.|  
|[COleControl::GetHwnd](../Topic/COleControl::GetHwnd.md)|Devuelve el valor de la propiedad común de HWND.|  
|[COleControl::GetMessageString](../Topic/COleControl::GetMessageString.md)|Proporciona el texto de la barra de estado para un elemento de menú.|  
|[COleControl::GetNotSupported](../Topic/COleControl::GetNotSupported.md)|Evita el acceso al valor de propiedad de un control de usuario.|  
|[COleControl::GetReadyState](../Topic/COleControl::GetReadyState.md)|Devuelve el estado de la eliminación del control.|  
|[COleControl::GetRectInContainer](../Topic/COleControl::GetRectInContainer.md)|Devuelve el rectángulo de control en relación con el contenedor.|  
|[COleControl::GetStockTextMetrics](../Topic/COleControl::GetStockTextMetrics.md)|Devuelve métricas de la propiedad de fuente común.|  
|[COleControl::GetText](../Topic/COleControl::GetText.md)|Devuelve el valor de texto o de la propiedad caption común.|  
|[COleControl::GetWindowlessDropTarget](../Topic/COleControl::GetWindowlessDropTarget.md)|Reemplace para permitir que un control sin ventana sea el destino de las operaciones de arrastrar y colocar.|  
|[COleControl::InitializeIIDs](../Topic/COleControl::InitializeIIDs.md)|Informa a la clase base el los identificadores IID que el control utilizará.|  
|[COleControl::InternalGetFont](../Topic/COleControl::InternalGetFont.md)|Devuelve un objeto de `CFontHolder` para la propiedad de fuente común.|  
|[COleControl::InternalGetText](../Topic/COleControl::InternalGetText.md)|Recupera la leyenda o la propiedad de texto común.|  
|[COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md)|Establece el estado de la eliminación del control y desencadena el evento de listo\-provincia\- cambio.|  
|[COleControl::InvalidateControl](../Topic/COleControl::InvalidateControl.md)|Reemplaza un área de control mostrado, produciendolo que se rediseñará.|  
|[COleControl::InvalidateRgn](../Topic/COleControl::InvalidateRgn.md)|Reemplaza el área cliente de la ventana contenedora dentro de la región determinada.  Se puede utilizar para actualizar los controles sin ventana en la región.|  
|[COleControl::IsConvertingVBX](../Topic/COleControl::IsConvertingVBX.md)|Allows especializado la carga de un control OLE.|  
|[COleControl::IsModified](../Topic/COleControl::IsModified.md)|Determina si el estado de control ha cambiado.|  
|[COleControl::IsOptimizedDraw](../Topic/COleControl::IsOptimizedDraw.md)|Indica si el contenedor admite el dibujo optimizado para la operación actual del gráfico.|  
|[COleControl::IsSubclassedControl](../Topic/COleControl::IsSubclassedControl.md)|Denominado para determinar si el control crea una subclase de un control de Windows.|  
|[COleControl::Load](../Topic/COleControl::Load.md)|Restaura los datos asincrónico anterior e inicia una nueva carga de propiedad asincrónica del control.|  
|[COleControl::LockInPlaceActive](../Topic/COleControl::LockInPlaceActive.md)|Determina si el control se puede desactivar en el contenedor.|  
|[COleControl::OnAmbientPropertyChange](../Topic/COleControl::OnAmbientPropertyChange.md)|Se invoca cuando cambia una propiedad de ambiente.|  
|[COleControl::OnAppearanceChanged](../Topic/COleControl::OnAppearanceChanged.md)|Se invoca cuando cambia la propiedad de apariencia común.|  
|[COleControl::OnBackColorChanged](../Topic/COleControl::OnBackColorChanged.md)|Se invoca cuando cambia la propiedad BackColor común.|  
|[COleControl::OnBorderStyleChanged](../Topic/COleControl::OnBorderStyleChanged.md)|Se invoca cuando cambia la propiedad BorderStyle de la acción.|  
|[COleControl::OnClick](../Topic/COleControl::OnClick.md)|Denominado para desencadenar el evento Click común.|  
|[COleControl::OnClose](../Topic/COleControl::OnClose.md)|Notifica al control que se ha llamado a `IOleControl::Close` .|  
|[COleControl::OnDoVerb](../Topic/COleControl::OnDoVerb.md)|Se llama después de que se ha ejecutado un verbo del control.|  
|[COleControl::OnDraw](../Topic/COleControl::OnDraw.md)|Llamado cuando un control se solicita para actualizarse.|  
|[COleControl::OnDrawMetafile](../Topic/COleControl::OnDrawMetafile.md)|Llamado por el contenedor cuando un control se solicita para actualizarse mediante un contexto de dispositivo de metarchivo.|  
|[COleControl::OnEdit](../Topic/COleControl::OnEdit.md)|Llamado por el contenedor a la interfaz de usuario Activar un control OLE.|  
|[COleControl::OnEnabledChanged](../Topic/COleControl::OnEnabledChanged.md)|Se invoca cuando cambia la propiedad enabled común.|  
|[COleControl::OnEnumVerbs](../Topic/COleControl::OnEnumVerbs.md)|Llamado por el contenedor para enumerar los verbos de un control.|  
|[COleControl::OnEventAdvise](../Topic/COleControl::OnEventAdvise.md)|Se invoca cuando los controladores de eventos están conectados o desconectados de un control.|  
|[COleControl::OnFontChanged](../Topic/COleControl::OnFontChanged.md)|Se invoca cuando cambia la propiedad de fuente común.|  
|[COleControl::OnForeColorChanged](../Topic/COleControl::OnForeColorChanged.md)|Se invoca cuando se cambia la propiedad ForeColor común.|  
|[COleControl::OnFreezeEvents](../Topic/COleControl::OnFreezeEvents.md)|Se invoca cuando se inmovilizan o se liberan los eventos de un control.|  
|[COleControl::OnGetColorSet](../Topic/COleControl::OnGetColorSet.md)|Notifica al control que se ha llamado a `IOleObject::GetColorSet` .|  
|[COleControl::OnGetControlInfo](../Topic/COleControl::OnGetControlInfo.md)|Proporciona información mnemotécnica al contenedor.|  
|[COleControl::OnGetDisplayString](../Topic/COleControl::OnGetDisplayString.md)|Denominado para obtener una cadena que represente un valor de propiedad.|  
|[COleControl::OnGetInPlaceMenu](../Topic/COleControl::OnGetInPlaceMenu.md)|Solicita el identificador del menú de control que se combina con el menú del contenedor.|  
|[COleControl::OnGetNaturalExtent](../Topic/COleControl::OnGetNaturalExtent.md)|Reemplazo para recuperar el tamaño de presentación del control más cercano al modo propuesto del tamaño y la extensión.|  
|[COleControl::OnGetPredefinedStrings](../Topic/COleControl::OnGetPredefinedStrings.md)|Cadenas de retornos que representan los valores posibles para la propiedad.|  
|[COleControl::OnGetPredefinedValue](../Topic/COleControl::OnGetPredefinedValue.md)|Devuelve el valor correspondiente a una cadena predefinida.|  
|[COleControl::OnGetViewExtent](../Topic/COleControl::OnGetViewExtent.md)|Reemplace para recuperar el tamaño de las áreas de presentación del control \(se puede utilizar para habilitar el gráfico de dos\- paso\).|  
|[COleControl::OnGetViewRect](../Topic/COleControl::OnGetViewRect.md)|Reemplace para convertir el tamaño del control en un rectángulo inicial en una posición determinada.|  
|[COleControl::OnGetViewStatus](../Topic/COleControl::OnGetViewStatus.md)|Reemplace para recuperar el estado de vista del control.|  
|[COleControl::OnHideToolBars](../Topic/COleControl::OnHideToolBars.md)|Llamado por el contenedor cuando el control se interfaz de usuario unchecked.|  
|[COleControl::OnInactiveMouseMove](../Topic/COleControl::OnInactiveMouseMove.md)|Reemplace para obtener el contenedor del control inactivo en los mensajes de `WM_MOUSEMOVE` de envío del puntero del mouse en el control.|  
|[COleControl::OnInactiveSetCursor](../Topic/COleControl::OnInactiveSetCursor.md)|Reemplace para obtener el contenedor del control inactivo en los mensajes de `WM_SETCURSOR` de envío del puntero del mouse en el control.|  
|[COleControl::OnKeyDownEvent](../Topic/COleControl::OnKeyDownEvent.md)|Se llama después de que se ha desencadenado el evento KeyDown de la acción.|  
|[COleControl::OnKeyPressEvent](../Topic/COleControl::OnKeyPressEvent.md)|Se llama después de que se ha desencadenado el evento KeyPress de la acción.|  
|[COleControl::OnKeyUpEvent](../Topic/COleControl::OnKeyUpEvent.md)|Se llama después de que se ha desencadenado el evento KeyUp de la acción.|  
|[COleControl::OnMapPropertyToPage](../Topic/COleControl::OnMapPropertyToPage.md)|Indica qué página de propiedades para editar una propiedad.|  
|[COleControl::OnMnemonic](../Topic/COleControl::OnMnemonic.md)|Llamado cuando una clave mnemotécnica de control se ha presionado.|  
|[COleControl::OnProperties](../Topic/COleControl::OnProperties.md)|Se invoca cuando se ha invocado el verbo de “properties” del control.|  
|[COleControl::OnQueryHitPoint](../Topic/COleControl::OnQueryHitPoint.md)|Reemplace para ver si la presentación de un control se superpone a un punto determinado.|  
|[COleControl::OnQueryHitRect](../Topic/COleControl::OnQueryHitRect.md)|Reemplace para ver si la presentación de un control se superpone a cualquier punto en un rectángulo determinado.|  
|[COleControl::OnRenderData](../Topic/COleControl::OnRenderData.md)|Llamado por el marco para recuperar datos en el formato especificado.|  
|[COleControl::OnRenderFileData](../Topic/COleControl::OnRenderFileData.md)|Llamado por el marco para recuperar datos de un archivo en el formato especificado.|  
|[COleControl::OnRenderGlobalData](../Topic/COleControl::OnRenderGlobalData.md)|Llamado por el marco para recuperar datos de la memoria global en el formato especificado.|  
|[COleControl::OnResetState](../Topic/COleControl::OnResetState.md)|Restablece las propiedades de un control a los valores predeterminados.|  
|[COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md)|Notifica al control que se ha llamado a `IOleControl::SetClientSite` .|  
|[COleControl::OnSetData](../Topic/COleControl::OnSetData.md)|Reemplaza los datos del control con otro valor.|  
|[COleControl::OnSetExtent](../Topic/COleControl::OnSetExtent.md)|Con el nombre de la extensión de control ha cambiado.|  
|[COleControl::OnSetObjectRects](../Topic/COleControl::OnSetObjectRects.md)|Se llama después de que se han modificado las dimensiones del control.|  
|[COleControl::OnShowToolBars](../Topic/COleControl::OnShowToolBars.md)|Se llama cuando el control se ha interfaz de usuario elevado.|  
|[COleControl::OnTextChanged](../Topic/COleControl::OnTextChanged.md)|Se invoca cuando se cambia el texto o la propiedad caption común.|  
|[COleControl::OnWindowlessMessage](../Topic/COleControl::OnWindowlessMessage.md)|Mensajes de la ventana procesos \(distinto de mensajes del teclado y de mouse\) para los controles sin ventana.|  
|[COleControl::ParentToClient](../Topic/COleControl::ParentToClient.md)|Convierte un punto en relación con el origen del contenedor a un punto en relación con el origen del control.|  
|[COleControl::PostModalDialog](../Topic/COleControl::PostModalDialog.md)|Notifica al contenedor que se ha cerrado un cuadro de diálogo modal.|  
|[COleControl::PreModalDialog](../Topic/COleControl::PreModalDialog.md)|Notifica al contenedor de un cuadro de diálogo modal está a punto de mostrarse.|  
|[COleControl::RecreateControlWindow](../Topic/COleControl::RecreateControlWindow.md)|Destruye y vuelve a crear la ventana de control.|  
|[COleControl::Refresh](../Topic/COleControl::Refresh.md)|Fuerza una repintura de la apariencia de un control.|  
|[COleControl::ReleaseCapture](../Topic/COleControl::ReleaseCapture.md)|Captura del mouse de las versiones.|  
|[COleControl::ReleaseDC](../Topic/COleControl::ReleaseDC.md)|Libera el contexto del dispositivo de pantalla de un contenedor de un control sin ventana.|  
|[COleControl::ReparentControlWindow](../Topic/COleControl::ReparentControlWindow.md)|Restablece el elemento primario de la ventana de control.|  
|[COleControl::ResetStockProps](../Topic/COleControl::ResetStockProps.md)|Inicialice las propiedades de la acción de `COleControl` a sus valores predeterminados.|  
|[COleControl::ResetVersion](../Topic/COleControl::ResetVersion.md)|Inicializa el número de versión a un valor especificado.|  
|[COleControl::ScrollWindow](../Topic/COleControl::ScrollWindow.md)|Permite que un control sin ventana desplácese un área dentro de su imagen activo en contexto en la pantalla.|  
|[COleControl::SelectFontObject](../Topic/COleControl::SelectFontObject.md)|Seleccione una propiedad de la fuente personalizada en un contexto de dispositivo.|  
|[COleControl::SelectStockFont](../Topic/COleControl::SelectStockFont.md)|Selecciona la propiedad de la fuente común en un contexto de dispositivo.|  
|[COleControl::SerializeExtent](../Topic/COleControl::SerializeExtent.md)|Serializa o inicializa el espacio de presentación del control.|  
|[COleControl::SerializeStockProps](../Topic/COleControl::SerializeStockProps.md)|Serializa o inicializa las propiedades de la acción de `COleControl` .|  
|[COleControl::SerializeVersion](../Topic/COleControl::SerializeVersion.md)|Serializa o inicializa la información de versión del control.|  
|[COleControl::SetAppearance](../Topic/COleControl::SetAppearance.md)|Establece el valor de la propiedad de apariencia común.|  
|[COleControl::SetBackColor](../Topic/COleControl::SetBackColor.md)|Establece el valor de la propiedad BackColor común.|  
|[COleControl::SetBorderStyle](../Topic/COleControl::SetBorderStyle.md)|Establece el valor de la propiedad común BorderStyle.|  
|[COleControl::SetCapture](../Topic/COleControl::SetCapture.md)|Hace que la ventana del contenedor del control para tomar la propiedad de la captura del mouse en nombre del control.|  
|[COleControl::SetControlSize](../Topic/COleControl::SetControlSize.md)|Establece la posición y el tamaño de controles activex.|  
|[COleControl::SetEnabled](../Topic/COleControl::SetEnabled.md)|Establece el valor de la propiedad enabled común.|  
|[COleControl::SetFocus](../Topic/COleControl::SetFocus.md)|Hace que la ventana del contenedor del control para tomar la propiedad del foco de entrada en nombre del control.|  
|[COleControl::SetFont](../Topic/COleControl::SetFont.md)|Establece el valor de la propiedad de fuente común.|  
|[COleControl::SetForeColor](../Topic/COleControl::SetForeColor.md)|Establece el valor de la propiedad ForeColor común.|  
|[COleControl::SetInitialSize](../Topic/COleControl::SetInitialSize.md)|Establece el tamaño de un control OLE cuando se muestra por primera vez en un contenedor.|  
|[COleControl::SetModifiedFlag](../Topic/COleControl::SetModifiedFlag.md)|Cambia el estado modificada de un control.|  
|[COleControl::SetNotPermitted](../Topic/COleControl::SetNotPermitted.md)|Indica que hay un error en una llamada de edición de texto.|  
|[COleControl::SetNotSupported](../Topic/COleControl::SetNotSupported.md)|Evita la modificación en el valor de propiedad de un control de usuario.|  
|[COleControl::SetRectInContainer](../Topic/COleControl::SetRectInContainer.md)|Establece el rectángulo de control en relación con el contenedor.|  
|[COleControl::SetText](../Topic/COleControl::SetText.md)|Establece el valor de texto o de la propiedad caption común.|  
|[COleControl::ThrowError](../Topic/COleControl::ThrowError.md)|Indica que se ha producido un error a en un control OLE.|  
|[COleControl::TransformCoords](../Topic/COleControl::TransformCoords.md)|Las transformaciones coordinan valores entre un contenedor y.|  
|[COleControl::TranslateColor](../Topic/COleControl::TranslateColor.md)|Convierte un valor de **OLE\_COLOR** a un valor de **COLORREF** .|  
|[COleControl::WillAmbientsBeValidDuringLoad](../Topic/COleControl::WillAmbientsBeValidDuringLoad.md)|Determina si las propiedades de ambiente estará disponible la próxima vez que el control se cargan.|  
|[COleControl::WindowProc](../Topic/COleControl::WindowProc.md)|proporciona un procedimiento de Windows para un objeto de `COleControl` .|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleControl::DrawContent](../Topic/COleControl::DrawContent.md)|Llamado por el marco cuando la apariencia del control debe actualizarse.|  
|[COleControl::DrawMetafile](../Topic/COleControl::DrawMetafile.md)|Llamado por el marco cuando se utiliza el contexto de dispositivo de metarchivo.|  
|[COleControl::IsInvokeAllowed](../Topic/COleControl::IsInvokeAllowed.md)|Habilita la invocación de método de automatización.|  
|[COleControl::SetInitialDataFormats](../Topic/COleControl::SetInitialDataFormats.md)|Llamado por el marco para inicializar la lista de formatos de datos admitidos por el control.|  
  
## Comentarios  
 Derivado de `CWnd`, esta clase hereda toda la funcionalidad de un objeto de la ventana de Windows más específico de la función adicional a OLE, como desencadenamiento de eventos y la capacidad de admitir métodos y propiedades.  
  
 Controles OLE pueden incrustar en aplicaciones contenedoras VIEJAS y comunicarse con el contenedor mediante un sistema bidireccional de desencadenamiento de eventos y métodos el exponer y propiedades al contenedor.  Observe que los contenedores de OLE estándar sólo admiten la funcionalidad básica de un control activex.  No pueden admitir características extendidas de un control OLE.  El desencadenamiento de evento se produce cuando los eventos se envían al contenedor como resultado de acciones que tienen lugar en el control.  A su vez, el contenedor se comunica con el control utilizando un conjunto expuesto de métodos y propiedades análogas a las funciones miembro y los miembros de datos de C\+\+. ordenan.  Este enfoque permite al desarrollador controla la apariencia del control y notifica el contenedor cuando algunas acciones aparecen.  
  
## Controles sin ventana  
 Controles OLE pueden estar activo en contexto utilizado sin una ventana.  Los controles sin ventana tienen ventajas importantes:  
  
-   Los controles sin ventana pueden ser transparente y no rectangulares  
  
-   Los controles sin ventana reduce el tamaño de la instancia y la hora de creación de objetos  
  
 Los Controles no necesitan una ventana.  Los servicios que una ventana proporciona se pueden proporcionar con facilidad mediante una sola ventana compartida \(normalmente el contenedor\) y un poco de enviar codificada.  Tener una ventana es principalmente una complicación innecesaria del objeto.  
  
 Cuando se utiliza la activación sin ventana, el contenedor \(que tiene una ventana\) es responsable de proporcionar los servicios que pudieran estar proporcionados de otra manera por la propia ventana de control.  Por ejemplo, si sus necesidades de control de ver el foco de teclado, de ver la captura del mouse, o de obtener un contexto de dispositivo, estas operaciones son administradas por el contenedor.  `COleControl`[funciones miembro de la sin ventana\- operación](http://msdn.microsoft.com/es-es/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) invoca estas operaciones en el contenedor.  
  
 Cuando está sin ventana se habilita la activación, los mensajes de entrada de los delegados de contenedor a la interfaz de `IOleInPlaceObjectWindowless` de control \(una extensión de [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646) para compatibilidad sin ventana\).  la implementación de los entity\_COleControl de esta interfaz envía estos mensajes a través del mapa de mensajes del control, después de ajustar las coordenadas del mouse correctamente.  Puede procesar estos mensajes como mensajes normales de la ventana, agregando las entradas correspondientes al mapa de mensajes.  
  
 En un control sin ventana, debe utilizar siempre las funciones miembro de `COleControl` en lugar de las funciones correspondientes del miembro de `CWnd` o la API de Windows relacionada funciona.  
  
 Los objetos de controles activex también pueden crear una ventana cuando pasan a ser activo, pero la cantidad de trabajo necesaria para la transición de inactivo\- activo sube y la velocidad de transición va a continuación.  Hay casos cuando éste es un problema: como ejemplo, considere una cuadrícula de cuadros de texto.  El cursoring arriba y abajo a través de la columna, cada control se debe haber producido en contexto y después unchecked.  La velocidad de transición inactiva\/activo afecta directamente a la velocidad de desplazamiento.  
  
 Para obtener más información sobre cómo desarrollar un marco de controles activex, vea los artículos [Controles ActiveX de MFC](../../mfc/mfc-activex-controls.md) y [información general: Crear un programa de control ActiveX de MFC](../../mfc/reference/mfc-activex-control-wizard.md).  Para obtener información sobre cómo optimizar controles OLE, incluidos los controles sin ventana y libres de centelleo, vea [Controles ActiveX de MFC: optimización](../../mfc/mfc-activex-controls-optimization.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `COleControl`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [ejemplo CIRC3 de MFC](../../top/visual-cpp-samples.md)   
 [ejemplo TESTHELP de MFC](../../top/visual-cpp-samples.md)   
 [COlePropertyPage Class](../../mfc/reference/colepropertypage-class.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)   
 [CPictureHolder Class](../../mfc/reference/cpictureholder-class.md)