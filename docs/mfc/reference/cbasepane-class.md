---
title: "CBasePane Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CBasePane::get_accKeyboardShortcut"
  - "CBasePane.get_accKeyboardShortcut"
  - "CBasePane.accSelect"
  - "get_accDefaultAction"
  - "accSelect"
  - "CBasePane.accHitTest"
  - "CBasePane.get_accRole"
  - "get_accKeyboardShortcut"
  - "CBasePane::Serialize"
  - "CBasePane"
  - "CBasePane::get_accDefaultAction"
  - "get_accParent"
  - "CBasePane::accSelect"
  - "accLocation"
  - "CBasePane.get_accDescription"
  - "get_accName"
  - "CBasePane::get_accChildCount"
  - "CBasePane.get_accChild"
  - "CBasePane::accHitTest"
  - "accHitTest"
  - "get_accHelp"
  - "CBasePane.get_accChildCount"
  - "CBasePane.get_accValue"
  - "CBasePane::get_accDescription"
  - "get_accChildCount"
  - "CBasePane.accLocation"
  - "CBasePane.PreTranslateMessage"
  - "CBasePane.get_accName"
  - "PreTranslateMessage"
  - "CBasePane::get_accFocus"
  - "get_accDescription"
  - "CBasePane::get_accRole"
  - "get_accValue"
  - "CBasePane.Serialize"
  - "CBasePane::accLocation"
  - "get_accRole"
  - "CBasePane::get_accChild"
  - "get_accFocus"
  - "CBasePane::get_accHelp"
  - "CBasePane.get_accDefaultAction"
  - "CBasePane.get_accHelp"
  - "CBasePane::PreTranslateMessage"
  - "CBasePane::get_accState"
  - "CBasePane.get_accParent"
  - "CBasePane::get_accParent"
  - "get_accChild"
  - "CBasePane::get_accValue"
  - "Serialize"
  - "get_accState"
  - "CBasePane.get_accState"
  - "CBasePane.get_accFocus"
  - "CBasePane::get_accName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accHitTest method"
  - "accLocation method"
  - "accSelect method"
  - "CBasePane class"
  - "get_accChild method"
  - "get_accChildCount method"
  - "get_accDefaultAction method"
  - "get_accDescription method"
  - "get_accFocus method"
  - "get_accHelp method"
  - "get_accKeyboardShortcut method"
  - "get_accName method"
  - "get_accParent method"
  - "get_accRole method"
  - "get_accState method"
  - "get_accValue method"
  - "PreTranslateMessage method"
  - "Serialize method"
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 44
---
# CBasePane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

clase base para todos los paneles en MFC.  
  
## Sintaxis  
  
```  
class CBasePane : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CBasePane::CBasePane`|Constructor predeterminado.|  
|`CBasePane::~CBasePane`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CBasePane::accHitTest`|Llamado por el marco para recuperar el elemento secundario o el objeto secundario en un punto determinado de la pantalla.  \(Reemplaza [CWnd::accHitTest](../Topic/CWnd::accHitTest.md).\)|  
|`CBasePane::accLocation`|Llamado por el marco para recuperar la ubicación actual de la pantalla para el objeto especificado.  \(Reemplaza [CWnd::accLocation](../Topic/CWnd::accLocation.md).\)|  
|[CBasePane::AccNotifyObjectFocusEvent](../Topic/CBasePane::AccNotifyObjectFocusEvent.md)|`CBasePane` no utiliza este método.|  
|`CBasePane::accSelect`|Llamado por el marco para modificar la selección o para mover el foco de teclado del objeto especificado.  \(Reemplaza [CWnd::accSelect](../Topic/CWnd::accSelect.md).\)|  
|[CBasePane::AddPane](../Topic/CBasePane::AddPane.md)|Agrega un panel al administrador de acoplamiento.|  
|[CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)|Redirige una llamada al administrador de acoplamiento para ajustar el diseño de acoplamiento.|  
|[CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)|Llamado por el marco cuando el panel debe ajustar su diseño interno.|  
|[CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)|Calcula el tamaño horizontal de una barra de controles.|  
|[CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)|Determina si otro panel se puede acoplar el panel.|  
|[CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md)|Determina si el panel admite oculta automáticamente el modo.|  
|[CBasePane::CanBeAttached](../Topic/CBasePane::CanBeAttached.md)|determina si el panel se puede acoplar a otro panel.|  
|[CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)|Determina si el panel puede cerrarse.|  
|[CBasePane::CanBeDocked](../Topic/CBasePane::CanBeDocked.md)|determina si el panel se puede acoplar a otro panel.|  
|[CBasePane::CanBeResized](../Topic/CBasePane::CanBeResized.md)|Determina si el panel puede cambiar de tamaño.|  
|[CBasePane::CanBeTabbedDocument](../Topic/CBasePane::CanBeTabbedDocument.md)|Especifica si el panel se puede convertir en un documento con fichas MDI.|  
|[CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md)|determina si el panel puede flotar.|  
|[CBasePane::CanFocus](../Topic/CBasePane::CanFocus.md)|Especifica si el panel puede recibir el foco.|  
|[CBasePane::CopyState](../Topic/CBasePane::CopyState.md)|Copia el estado de un panel especificado.|  
|[CBasePane::CreateDefaultMiniframe](../Topic/CBasePane::CreateDefaultMiniframe.md)|Si el panel puede desacoplar, crea una ventana de marco recudido.|  
|[CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)|Crear el control del panel.|  
|[CBasePane::DockPane](../Topic/CBasePane::DockPane.md)|Acoplar un panel a otro panel o a una ventana de marco.|  
|[CBasePane::DockPaneUsingRTTI](../Topic/CBasePane::DockPaneUsingRTTI.md)|Acoplar el panel utilizando la información de tipo en tiempo de ejecución.|  
|[CBasePane::DockToFrameWindow](../Topic/CBasePane::DockToFrameWindow.md)|Acoplar un panel acoplable un marco.|  
|[CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)|determina si otro panel se puede insertar dinámicamente entre este panel y el cuadro primario.|  
|[CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md)|Habilita el acoplamiento del panel al cuadro principal.|  
|[CBasePane::EnableGripper](../Topic/CBasePane::EnableGripper.md)|Habilita o deshabilita el agarrador.  Si se habilita el agarrador, puede arrastrarlo para colocar el panel de nuevo.|  
|`CBasePane::FillWindowRect`|Utilizado de forma interna.|  
|[CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md)|flota el panel.|  
|`CBasePane::get_accChild`|Llamado por el marco para recuperar la dirección de una interfaz de `IDispatch` para el elemento secundario especificado.  \(Reemplaza [CWnd::get\_accChild](../Topic/CWnd::get_accChild.md).\)|  
|`CBasePane::get_accChildCount`|Llamado por el marco para recuperar el número de elementos secundarios que pertenecen a este objeto.  \(Reemplaza [CWnd::get\_accChildCount](../Topic/CWnd::get_accChildCount.md).\)|  
|`CBasePane::get_accDefaultAction`|Llamado por el marco para recuperar una cadena que describe la acción predeterminada del objeto.  \(Reemplaza [CWnd::get\_accDefaultAction](../Topic/CWnd::get_accDefaultAction.md).\)|  
|`CBasePane::get_accDescription`|Llamado por el marco para recuperar una cadena que describe la apariencia visual del objeto especificado.  \(Reemplaza [CWnd::get\_accDescription](../Topic/CWnd::get_accDescription.md).\)|  
|`CBasePane::get_accFocus`|Llamado por el marco para recuperar el objeto que tiene el foco de teclado.  \(Reemplaza [CWnd::get\_accFocus](../Topic/CWnd::get_accFocus.md).\)|  
|`CBasePane::get_accHelp`|Llamado por el marco para recuperar una cadena de la propiedad de Ayuda para el objeto.  \(Reemplaza [CWnd::get\_accHelp](../Topic/CWnd::get_accHelp.md).\)|  
|[CBasePane::get\_accHelpTopic](../Topic/CBasePane::get_accHelpTopic.md)|Llamado por el marco para recuperar la ruta de acceso completa del WinHelpfileasociado al objeto especificado y el identificador del tema adecuado en ese archivo.  \(Reemplaza [CWnd::get\_accHelpTopic](../Topic/CWnd::get_accHelpTopic.md).\)|  
|`CBasePane::get_accKeyboardShortcut`|Llamado por el marco para recuperar la tecla de método abreviado especificada para el objeto.  \(Reemplaza [CWnd::get\_accKeyboardShortcut](../Topic/CWnd::get_accKeyboardShortcut.md).\)|  
|`CBasePane::get_accName`|Llamado por el marco para recuperar el nombre del objeto especificado.  \(Reemplaza [CWnd::get\_accName](../Topic/CWnd::get_accName.md).\)|  
|`CBasePane::get_accParent`|Llamado por el marco para recuperar la interfaz de `IDispatch` para el elemento primario del objeto.  \(Reemplaza [CWnd::get\_accParent](../Topic/CWnd::get_accParent.md).\)|  
|`CBasePane::get_accRole`|Llamado por el marco para recuperar la información que describe el rol del objeto especificado.  \(Reemplaza [CWnd::get\_accRole](../Topic/CWnd::get_accRole.md).\)|  
|[CBasePane::get\_accSelection](../Topic/CBasePane::get_accSelection.md)|Llamado por el marco para recuperar los elementos secundarios de este objeto.  \(Reemplaza [CWnd::get\_accSelection](../Topic/CWnd::get_accSelection.md).\)|  
|`CBasePane::get_accState`|Llamado por el marco para recuperar el estado actual del objeto especificado.  \(Reemplaza [CWnd::get\_accState](../Topic/CWnd::get_accState.md).\)|  
|`CBasePane::get_accValue`|Llamado por el marco para recuperar el valor del objeto especificado.  \(Reemplaza [CWnd::get\_accValue](../Topic/CWnd::get_accValue.md).\)|  
|[CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)|Devuelve el alto de la leyenda.|  
|[CBasePane::GetControlBarStyle](../Topic/CBasePane::GetControlBarStyle.md)|devuelve el estilo de la barra de control.|  
|[CBasePane::GetCurrentAlignment](../Topic/CBasePane::GetCurrentAlignment.md)|Devuelve la alineación actual del panel.|  
|[CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md)|Devuelve el modo actual de acoplamiento del panel.|  
|[CBasePane::GetDockSiteFrameWnd](../Topic/CBasePane::GetDockSiteFrameWnd.md)|Devuelve un puntero a la ventana que es el sitio dock en el panel.|  
|[CBasePane::GetEnabledAlignment](../Topic/CBasePane::GetEnabledAlignment.md)|Devuelve los estilos de CBRS\_ALIGN\_ que se aplican al panel.|  
|[CBasePane::GetMFCStyle](../Topic/CBasePane::GetMFCStyle.md)|Devuelve los estilos del panel específicos de MFC.|  
|[CBasePane::GetPaneIcon](../Topic/CBasePane::GetPaneIcon.md)|Devuelve un identificador al icono del panel.|  
|`CBasePane::GetPaneRect`|Utilizado de forma interna.|  
|[CBasePane::GetPaneRow](../Topic/CBasePane::GetPaneRow.md)|Devuelve un puntero al objeto de [CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)donde el panel está acoplado.|  
|[CBasePane::GetPaneStyle](../Topic/CBasePane::GetPaneStyle.md)|Devuelve el estilo del panel.|  
|[CBasePane::GetParentDockSite](../Topic/CBasePane::GetParentDockSite.md)|Devuelve un puntero al sitio primario de vinculación.|  
|[CBasePane::GetParentMiniFrame](../Topic/CBasePane::GetParentMiniFrame.md)|Devuelve un puntero a la ventana primaria de marco recudido.|  
|[CBasePane::GetParentTabbedPane](../Topic/CBasePane::GetParentTabbedPane.md)|Devuelve un puntero al panel con fichas elemento primario.|  
|[CBasePane::GetParentTabWnd](../Topic/CBasePane::GetParentTabWnd.md)|Devuelve un puntero a la ventana primaria que está dentro de una pestaña.|  
|[CBasePane::GetRecentVisibleState](../Topic/CBasePane::GetRecentVisibleState.md)|El marco de trabajo llama a este método cuando un panel se restaura de un archivo.|  
|[CBasePane::HideInPrintPreviewMode](../Topic/CBasePane::HideInPrintPreviewMode.md)|Especifica si el panel está oculto en la vista previa de impresión.|  
|[CBasePane::InsertPane](../Topic/CBasePane::InsertPane.md)|Registra el panel especificado con el administrador de acoplamiento.|  
|[CBasePane::IsAccessibilityCompatible](../Topic/CBasePane::IsAccessibilityCompatible.md)|Especifica si el panel admite accesibilidad activo.|  
|[CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md)|Determina si es un panel en oculta automáticamente el modo.|  
|[CBasePane::IsDialogControl](../Topic/CBasePane::IsDialogControl.md)|Especifica si el panel es un control de cuadro de diálogo.|  
|[CBasePane::IsDocked](../Topic/CBasePane::IsDocked.md)|determina si el panel está acoplado.|  
|[CBasePane::IsFloating](../Topic/CBasePane::IsFloating.md)|Determina si el panel está flotando.|  
|[CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md)|determina si el panel está acoplado horizontalmente.|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](../Topic/CBasePane::IsInFloatingMultiPaneFrameWnd.md)|Especifica si el panel está en una ventana de marco de multi\- panel.|  
|[CBasePane::IsMDITabbed](../Topic/CBasePane::IsMDITabbed.md)|Determina si el panel se ha agregado a una ventana MDI secundaria como un documento con fichas.|  
|[CBasePane::IsPaneVisible](../Topic/CBasePane::IsPaneVisible.md)|Especifica si el indicador de `WS_VISIBLE` está establecido para el panel.|  
|[CBasePane::IsPointNearDockSite](../Topic/CBasePane::IsPointNearDockSite.md)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)|Determina si el panel puede cambiar de tamaño.|  
|[CBasePane::IsRestoredFromRegistry](../Topic/CBasePane::IsRestoredFromRegistry.md)|Determina si el panel está restaurado del registro.|  
|[CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md)|Determina si el panel se ha insertado en el control de ficha de una ventana con fichas.|  
|`CBasePane::IsTooltipTopmost`|Utilizado de forma interna.|  
|[CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md)|Determina si el panel está visible.|  
|[CBasePane::LoadState](../Topic/CBasePane::LoadState.md)|Carga el estado del registro.|  
|[CBasePane::MoveWindow](../Topic/CBasePane::MoveWindow.md)|mueve el panel.|  
|[CBasePane::OnAfterChangeParent](../Topic/CBasePane::OnAfterChangeParent.md)|Llamado por el marco cuando se ha cambiado el elemento primario del panel.|  
|[CBasePane::OnBeforeChangeParent](../Topic/CBasePane::OnBeforeChangeParent.md)|Llamado por el marco justo antes del panel cambia su ventana primaria.|  
|[CBasePane::OnDrawCaption](../Topic/CBasePane::OnDrawCaption.md)|El marco de trabajo llama a este método cuando se dibuja la leyenda.|  
|[CBasePane::OnMovePaneDivider](../Topic/CBasePane::OnMovePaneDivider.md)|Este método no se utiliza actualmente.|  
|[CBasePane::OnPaneContextMenu](../Topic/CBasePane::OnPaneContextMenu.md)|Llamado por el marco cuando compila un menú que tenga una lista de paneles.|  
|[CBasePane::OnRemoveFromMiniFrame](../Topic/CBasePane::OnRemoveFromMiniFrame.md)|Llamado por el marco cuando un panel se quitará de la mini ventana de marco principal.|  
|[CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)|`CBasePane` no utiliza este método.|  
|`CBasePane::OnUpdateCmdUI`|Utilizado de forma interna.|  
|[CBasePane::PaneFromPoint](../Topic/CBasePane::PaneFromPoint.md)|Devuelve el panel que contiene el punto determinado.|  
|`CBasePane::PreTranslateMessage`|Utiliza la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md)|`CBasePane` no utiliza este método.|  
|[CBasePane::RemovePaneFromDockManager](../Topic/CBasePane::RemovePaneFromDockManager.md)|Anula un panel y colóquelo en la lista en el administrador de acoplamiento.|  
|[CBasePane::SaveState](../Topic/CBasePane::SaveState.md)|Guarda el estado del panel al registro.|  
|[CBasePane::SelectDefaultFont](../Topic/CBasePane::SelectDefaultFont.md)|Selecciona la fuente predeterminada para un contexto especificado del dispositivo.|  
|`CBasePane::Serialize`|Lee o escribe este objeto o un archivo.  \(Reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md).\)|  
|[CBasePane::SetControlBarStyle](../Topic/CBasePane::SetControlBarStyle.md)|establece el estilo de la barra de control.|  
|[CBasePane::SetDockingMode](../Topic/CBasePane::SetDockingMode.md)|Establece el modo de acoplamiento del panel.|  
|`CBasePane::SetMDITabbed`|Utilizado de forma interna.|  
|[CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md)|Establece la alineación del panel.|  
|`CBasePane::SetPaneRect`|Utilizado de forma interna.|  
|[CBasePane::SetPaneStyle](../Topic/CBasePane::SetPaneStyle.md)|Establece el estilo del panel.|  
|`CBasePane::SetRestoredFromRegistry`|Utilizado de forma interna.|  
|[CBasePane::SetWindowPos](../Topic/CBasePane::SetWindowPos.md)|Cambia el tamaño, la posición, y el orden Z de un panel.|  
|[CBasePane::ShowPane](../Topic/CBasePane::ShowPane.md)|Muestra u oculta el panel.|  
|[CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)|Ajusta un panel vertical u horizontalmente.|  
|[CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md)|Quita el panel del sitio de acoplamiento, slider predeterminado, o la ventana de marco recudido donde está acoplado actualmente.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBasePane::DoPaint](../Topic/CBasePane::DoPaint.md)|Rellena el fondo del panel.|  
  
## Comentarios  
 Si desea crear una clase panel que admite las características extendidas de acoplamiento disponibles en MFC, deberá derivarlo de `CBasePane` o de [CPane Class](../../mfc/reference/cpane-class.md).  
  
## Sugerencias de personalización  
 Las siguientes sugerencias de personalización pertenecen a [CBasePane Class](../../mfc/reference/cbasepane-class.md) y a las clases que heredan de:  
  
-   Cuando crea un panel, puede aplicar varios nuevos estilos:  
  
    -   `AFX_CBRS_FLOAT` hace que el panel flota.  
  
    -   los permisos de`AFX_CBRS_AUTOHIDE` ocultan automáticamente el modo.  
  
    -   `AFX_CBRS_CLOSE` habilita el panel que se cerrará \(oculto\).  
  
     Éstos son marcas que se puede combinar con a bit a bit la operación.  
  
     `CBasePane` implementa los métodos booleanos virtuales siguientes para reflejar estos indicadores: [CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md), [CBasePane::CanAutoHide](../Topic/CBasePane::CanAutoHide.md), [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md).  Se pueden reemplazar en clases derivadas para personalizar su comportamiento.  
  
-   Puede personalizar el comportamiento del acoplamiento reemplazando [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md).  Tiene el retorno `FALSE` de panel de este método para evitar otro panel acoplable al.  
  
-   Si desea crear un panel estático que no pueden desacoplar y que evite cualquier otro panel acoplable antes de \(similar a la barra de Outlook en el ejemplo de OutlookDemo\), créelo como no\-flotante e invalidar [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md) para devolver `FALSE`.  la implementación predeterminada devuelve `FALSE` si el panel se crea sin el estilo de `AFX_CBRS_FLOAT` .  
  
-   Cree todos los paneles con id. distinto de \-1.  
  
-   Para determinar la visibilidad del panel, utilice [CBasePane::IsVisible](../Topic/CBasePane::IsVisible.md).  Correctamente controla el estado de visibilidad en con fichas y oculta automáticamente los modos.  
  
-   Si desea crear un panel de no\-flotante, créelo sin el estilo de `AFX_CBRS_FLOAT` y llame a [CFrameWnd::DockControlBar](../Topic/CFrameWnd::DockControlBar.md).  
  
-   Para excluir un panel de un diseño de acoplamiento o quitar una barra de herramientas de la barra de acoplamiento, llame a [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md).  No llame a este método para paneles en ocultan automáticamente el modo o para los paneles que residen en las pestañas de ventanas con fichas.  
  
-   Si desea flotar o desacoplar un panel que esté en ocultar automáticamente el modo, debe llamar a [CDockablePane::SetAutoHideMode](../Topic/CDockablePane::SetAutoHideMode.md) con `FALSE` como primer argumento antes de llamar a [CBasePane::FloatPane](../Topic/CBasePane::FloatPane.md) o [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CBasePane` .  El ejemplo muestra cómo recuperar un panel de la clase de `CFrameWndEx` y cómo establecer el modo de acoplamiento, la alineación del panel, y el estilo del panel.  El código es de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#2](../../mfc/reference/codesnippet/CPP/cbasepane-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## Requisitos  
 **encabezado:** afxbasepane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)