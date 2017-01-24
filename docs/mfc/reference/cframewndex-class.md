---
title: "CFrameWndEx Class | Microsoft Docs"
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
  - "CFrameWndEx"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFrameWndEx class"
ms.assetid: 5830aca8-4a21-4f31-91f1-dd5477ffcc8d
caps.latest.revision: 39
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFrameWndEx Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad de una ventana superpuesta \(SDI\) móvil o de interfaz de un único documento de Windows en el cuadro, y proporciona miembros para administrar la ventana.  Extiende la clase de [CFrameWnd](../../mfc/reference/cframewnd-class.md) .  
  
## Sintaxis  
  
```  
class CFrameWndEx : public CFrameWnd  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFrameWndEx::ActiveItemRecalcLayout](../Topic/CFrameWndEx::ActiveItemRecalcLayout.md)|Ajusta el diseño del elemento de cliente OLE y del área de cliente del cuadro.|  
|`CFrameWndEx::AddDockSite`|Este método no se utiliza.|  
|[CFrameWndEx::AddPane](../Topic/CFrameWndEx::AddPane.md)|Registra una barra de controles con el administrador de acoplamiento.|  
|[CFrameWndEx::AdjustDockingLayout](../Topic/CFrameWndEx::AdjustDockingLayout.md)|Actualiza el diseño de todos los paneles que se acoplan a la ventana de marco.|  
|[CFrameWndEx::DelayUpdateFrameMenu](../Topic/CFrameWndEx::DelayUpdateFrameMenu.md)|Establece el menú y después las actualizaciones de cuadro él cuando el procesamiento de comando está inactivo.|  
|[CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md)|Acoplar el panel especificado a la ventana de marco.|  
|[CFrameWndEx::DockPaneLeftOf](../Topic/CFrameWndEx::DockPaneLeftOf.md)|Lo acopla un panel a la izquierda de otro panel.|  
|[CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md)|Habilita el modo de ocultar automáticamente para los paneles cuando se acoplan a los lados especificados de la ventana de marco principal.|  
|[CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md)|Habilita el acoplamiento de los paneles que pertenecen a la ventana de marco.|  
|[CFrameWndEx::EnableFullScreenMainMenu](../Topic/CFrameWndEx::EnableFullScreenMainMenu.md)|Muestra u oculta el modo de menú principal en pantalla completa.|  
|[CFrameWndEx::EnableFullScreenMode](../Topic/CFrameWndEx::EnableFullScreenMode.md)|Habilita el modo de pantalla completa para la ventana de marco.|  
|[CFrameWndEx::EnableLoadDockState](../Topic/CFrameWndEx::EnableLoadDockState.md)|Permisos o neutralizaciones la carga del estado de vinculación.|  
|[CFrameWndEx::EnablePaneMenu](../Topic/CFrameWndEx::EnablePaneMenu.md)|Habilita o deshabilita el control automático de menú del panel.|  
|[CFrameWndEx::GetActivePopup](../Topic/CFrameWndEx::GetActivePopup.md)|Devuelve un puntero al menú emergente mostrado actualmente.|  
|[CFrameWndEx::GetDefaultResId](../Topic/CFrameWndEx::GetDefaultResId.md)|Devuelve el Id. de recurso que especificó al marco ha cargado la ventana de marco.|  
|[CFrameWndEx::GetDockingManager](../Topic/CFrameWndEx::GetDockingManager.md)|Recupera el objeto de [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) para la ventana de marco.|  
|[CFrameWndEx::GetMenuBar](../Topic/CFrameWndEx::GetMenuBar.md)|Devuelve un puntero al objeto de la barra de menús asociado a la ventana de marco.|  
|[CFrameWndEx::GetPane](../Topic/CFrameWndEx::GetPane.md)|Devuelve un puntero al panel que tiene el identificador especificado|  
|[CFrameWndEx::GetRibbonBar](../Topic/CFrameWndEx::GetRibbonBar.md)|Recupera el control de barra de la cinta de opciones del cuadro.|  
|[CFrameWndEx::GetTearOffBars](../Topic/CFrameWndEx::GetTearOffBars.md)|Devuelve una lista de objetos de panel que están en estado de rasgón.|  
|[CFrameWndEx::GetToolbarButtonToolTipText](../Topic/CFrameWndEx::GetToolbarButtonToolTipText.md)|Llamado por el marco cuando la aplicación muestra información sobre herramientas de un botón de la barra de herramientas.|  
|[CFrameWndEx::InsertPane](../Topic/CFrameWndEx::InsertPane.md)|Registra un panel con el administrador de acoplamiento.|  
|[CFrameWndEx::IsFullScreen](../Topic/CFrameWndEx::IsFullScreen.md)|Determina si la ventana de marco está en modo de pantalla completa.|  
|[CFrameWndEx::IsMenuBarAvailable](../Topic/CFrameWndEx::IsMenuBarAvailable.md)|Determina si el puntero al objeto de la barra de menús es válido.|  
|[CFrameWndEx::IsPointNearDockSite](../Topic/CFrameWndEx::IsPointNearDockSite.md)|Indica si el punto se encuentra en una zona de alineación.|  
|[CFrameWndEx::IsPrintPreview](../Topic/CFrameWndEx::IsPrintPreview.md)|Indica si la ventana de marco está en modo de vista previa de impresión.|  
|[CFrameWndEx::LoadFrame](../Topic/CFrameWndEx::LoadFrame.md)|Se llama a este método después de la construcción para crear la ventana de marco y cargar los recursos.|  
|[CFrameWndEx::NegotiateBorderSpace](../Topic/CFrameWndEx::NegotiateBorderSpace.md)|Implementa la negociación OLE del borde del cliente.|  
|[CFrameWndEx::OnActivate](../Topic/CFrameWndEx::OnActivate.md)|El marco de trabajo llama a este método cuando los datos proporcionados por el usuario se intercambia o fuera del control.|  
|[CFrameWndEx::OnActivateApp](../Topic/CFrameWndEx::OnActivateApp.md)|Llamado por el marco cuando se selecciona o se anule la selección de la aplicación.|  
|[CFrameWndEx::OnChangeVisualManager](../Topic/CFrameWndEx::OnChangeVisualManager.md)|Llamado por el marco cuando un cambio en el cuadro requiere un cambio el administrador visual.|  
|[CFrameWndEx::OnClose](../Topic/CFrameWndEx::OnClose.md)|El marco de trabajo llama a este método para cerrar el cuadro.|  
|[CFrameWndEx::OnCloseDockingPane](../Topic/CFrameWndEx::OnCloseDockingPane.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Cerrar** en un panel acoplable.|  
|[CFrameWndEx::OnCloseMiniFrame](../Topic/CFrameWndEx::OnCloseMiniFrame.md)|Llamado por el marco cuando el usuario hace clic en el botón de **Cerrar** en una mini ventana flotante del cuadro.|  
|[CFrameWndEx::OnClosePopupMenu](../Topic/CFrameWndEx::OnClosePopupMenu.md)|Llamado por el marco cuando un menú emergente activo procesa un mensaje WM\_DESTROY.|  
|[CFrameWndEx::OnCmdMsg](../Topic/CFrameWndEx::OnCmdMsg.md)|Envía mensajes de comando.|  
|[CFrameWndEx::OnContextHelp](../Topic/CFrameWndEx::OnContextHelp.md)|Llamado por el marco para mostrar contexto relacionados a los ayuda.|  
|[CFrameWndEx::OnCreate](../Topic/CFrameWndEx::OnCreate.md)|Llamado por el marco después del cuadro se crea.|  
|[CFrameWndEx::OnDestroy](../Topic/CFrameWndEx::OnDestroy.md)|Llamado por el marco cuando se destruye el cuadro.|  
|[CFrameWndEx::OnDrawMenuImage](../Topic/CFrameWndEx::OnDrawMenuImage.md)|Llamado por el marco cuando la aplicación se dibuja la imagen asociada a un elemento de menú.|  
|[CFrameWndEx::OnDrawMenuLogo](../Topic/CFrameWndEx::OnDrawMenuLogo.md)|Llamado por el marco cuando un objeto de `CMFCPopupMenu` procesa un mensaje de [WM\_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) .|  
|[CFrameWndEx::OnDWMCompositionChanged](../Topic/CFrameWndEx::OnDWMCompositionChanged.md)|Llamado por el marco cuando se ha habilitado o deshabilitado la composición de \(DWM\) del administrador de ventanas de escritorio.|  
|[CFrameWndEx::OnExitSizeMove](../Topic/CFrameWndEx::OnExitSizeMove.md)|Llamado por el marco cuando el cuadro detiene el desplazamiento o el cambio de tamaño.|  
|[CFrameWndEx::OnGetMinMaxInfo](../Topic/CFrameWndEx::OnGetMinMaxInfo.md)|Llamado por el marco cuando el cuadro cambia de tamaño para establecer límites de la dimensión de la ventana.|  
|[CFrameWndEx::OnIdleUpdateCmdUI](../Topic/CFrameWndEx::OnIdleUpdateCmdUI.md)|Llamado por el marco para actualizar la presentación del cuadro cuando el procesamiento de comando está inactivo.|  
|[CFrameWndEx::OnLButtonDown](../Topic/CFrameWndEx::OnLButtonDown.md)|El marco de trabajo llama a este método cuando el usuario presiona el botón primario.|  
|[CFrameWndEx::OnLButtonUp](../Topic/CFrameWndEx::OnLButtonUp.md)|El marco de trabajo llama a este método cuando el usuario suelta el botón primario.|  
|[CFrameWndEx::OnMenuButtonToolHitTest](../Topic/CFrameWndEx::OnMenuButtonToolHitTest.md)|Llamado por el marco cuando un objeto de `CMFCToolBarButton` procesa un mensaje de `WM_NCHITTEST` .|  
|[CFrameWndEx::OnMenuChar](../Topic/CFrameWndEx::OnMenuChar.md)|Llamado por el marco cuando se muestra un menú y el usuario presiona una tecla que no corresponde a un comando.|  
|[CFrameWndEx::OnMouseMove](../Topic/CFrameWndEx::OnMouseMove.md)|El marco de trabajo llama a este método cuando el puntero se mantiene.|  
|[CFrameWndEx::OnMoveMiniFrame](../Topic/CFrameWndEx::OnMoveMiniFrame.md)|Llamado por el marco cuando la ventana de panel se mueve.|  
|[CFrameWndEx::OnNcActivate](../Topic/CFrameWndEx::OnNcActivate.md)|Llamado por el marco al área de no cliente de conversión se debe volver a dibujar para indicar un cambio en el estado activo.|  
|[CFrameWndEx::OnNcCalcSize](../Topic/CFrameWndEx::OnNcCalcSize.md)|Llamado por el marco cuando el tamaño y la posición del área cliente deben calcularse.|  
|[CFrameWndEx::OnNcHitTest](../Topic/CFrameWndEx::OnNcHitTest.md)|Llamado por el marco cuando el puntero se desplaza o cuando se presiona o se suelta un botón del mouse.|  
|[CFrameWndEx::OnNcMouseMove](../Topic/CFrameWndEx::OnNcMouseMove.md)|Llamado por el marco cuando el puntero se mantiene en un área de cliente.|  
|[CFrameWndEx::OnNcPaint](../Topic/CFrameWndEx::OnNcPaint.md)|Llamado por el marco al área de no cliente debe ser pinta.|  
|[CFrameWndEx::OnPaneCheck](../Topic/CFrameWndEx::OnPaneCheck.md)|Llamado por el marco para controlar la visibilidad de un panel.|  
|[CFrameWndEx::OnPostPreviewFrame](../Topic/CFrameWndEx::OnPostPreviewFrame.md)|Llamado por el marco cuando el usuario ha cambiado el modo de vista previa de impresión.|  
|[CFrameWndEx::OnPowerBroadcast](../Topic/CFrameWndEx::OnPowerBroadcast.md)|Llamado por el marco cuando un evento de administración de energía aparece.|  
|[CFrameWndEx::OnSetMenu](../Topic/CFrameWndEx::OnSetMenu.md)|Llamado por el marco para reemplazar el menú de la ventana de marco.|  
|[CFrameWndEx::OnSetPreviewMode](../Topic/CFrameWndEx::OnSetPreviewMode.md)|Llamado por el marco para establecer el modo de vista previa de impresión del cuadro.|  
|[CFrameWndEx::OnSetText](../Topic/CFrameWndEx::OnSetText.md)|Llamado por el marco para establecer el texto de una ventana.|  
|[CFrameWndEx::OnShowCustomizePane](../Topic/CFrameWndEx::OnShowCustomizePane.md)|Llamado por el marco cuando un rápido personaliza se habilita el panel.|  
|[CFrameWndEx::OnShowPanes](../Topic/CFrameWndEx::OnShowPanes.md)|Llamado por el marco para mostrar u ocultar paneles.|  
|[CFrameWndEx::OnShowPopupMenu](../Topic/CFrameWndEx::OnShowPopupMenu.md)|Llamado por el marco cuando se habilita un menú emergente.|  
|[CFrameWndEx::OnSize](../Topic/CFrameWndEx::OnSize.md)|El marco de trabajo llama a este método después de que el tamaño de cuadro.|  
|[CFrameWndEx::OnSizing](../Topic/CFrameWndEx::OnSizing.md)|El marco de trabajo llama a este método cuando el usuario cambia el tamaño del cuadro.|  
|[CFrameWndEx::OnSysColorChange](../Topic/CFrameWndEx::OnSysColorChange.md)|Llamado por el marco cuando cambian los colores del sistema.|  
|[CFrameWndEx::OnTearOffMenu](../Topic/CFrameWndEx::OnTearOffMenu.md)|Llamado por el marco cuando se habilita un menú que tiene una barra de rasgón.|  
|[CFrameWndEx::OnToolbarContextMenu](../Topic/CFrameWndEx::OnToolbarContextMenu.md)|Llamado por el marco para compilar un menú contextual de la barra de herramientas.|  
|[CFrameWndEx::OnToolbarCreateNew](../Topic/CFrameWndEx::OnToolbarCreateNew.md)|El marco de trabajo llama a este método para crear una nueva barra de herramientas.|  
|[CFrameWndEx::OnToolbarDelete](../Topic/CFrameWndEx::OnToolbarDelete.md)|Llamado por el marco cuando se elimina una barra de herramientas.|  
|[CFrameWndEx::OnUpdateFrameMenu](../Topic/CFrameWndEx::OnUpdateFrameMenu.md)|Llamado por el marco para establecer el menú del cuadro.|  
|[CFrameWndEx::OnUpdateFrameTitle](../Topic/CFrameWndEx::OnUpdateFrameTitle.md)|El marco de trabajo llama a este método para actualizar la barra de título de la ventana de marco.|  
|[CFrameWndEx::OnUpdatePaneMenu](../Topic/CFrameWndEx::OnUpdatePaneMenu.md)|Llamado por el marco para actualizar el menú del panel.|  
|[CFrameWndEx::OnWindowPosChanged](../Topic/CFrameWndEx::OnWindowPosChanged.md)|Llamado por el marco cuando el tamaño de trama, la posición, o el orden z ha cambiado debido a una llamada a un método de administración de ventanas.|  
|[CFrameWndEx::PaneFromPoint](../Topic/CFrameWndEx::PaneFromPoint.md)|Devuelve el panel acoplable que contiene el punto especificado.|  
|[CFrameWndEx::PreTranslateMessage](../Topic/CFrameWndEx::PreTranslateMessage.md)|Mensajes específicos de la ventana de identificadores antes de que se envíen.|  
|[CFrameWndEx::RecalcLayout](../Topic/CFrameWndEx::RecalcLayout.md)|Ajustar el diseño del marco y de sus ventanas secundarias.|  
|[CFrameWndEx::RemovePaneFromDockManager](../Topic/CFrameWndEx::RemovePaneFromDockManager.md)|Anula un panel y colóquelo en la lista interna en el administrador de acoplamiento.|  
|[CFrameWndEx::SetDockState](../Topic/CFrameWndEx::SetDockState.md)|Restablece el diseño de acoplamiento el estado de vinculación almacenado en el registro.|  
|[CFrameWndEx::SetPrintPreviewFrame](../Topic/CFrameWndEx::SetPrintPreviewFrame.md)|Establece la ventana cuadro de vista previa de impresión.|  
|[CFrameWndEx::SetupToolbarMenu](../Topic/CFrameWndEx::SetupToolbarMenu.md)|Inserta comandos definidos por el usuario en un menú de barras de herramientas.|  
|[CFrameWndEx::ShowFullScreen](../Topic/CFrameWndEx::ShowFullScreen.md)|Cambia el marco principal entre los modos de plena pantalla y regulares.|  
|[CFrameWndEx::ShowPane](../Topic/CFrameWndEx::ShowPane.md)|Muestra u oculta el panel especificado.|  
|[CFrameWndEx::UpdateCaption](../Topic/CFrameWndEx::UpdateCaption.md)|Llamado por el marco para actualizar la leyenda de la ventana.|  
|[CFrameWndEx::WinHelp](../Topic/CFrameWndEx::WinHelp.md)|Invoca la aplicación de `WinHelp` o ayuda relacionada contexto.|  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo derivar una clase de la clase de `CFrameWndEx` .  El ejemplo muestra las signaturas de la subclase, y cómo reemplazar el método de `OnShowPopupMenu` .  Este fragmento de código es parte de [Ejemplo de pista de word](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#3](../../mfc/reference/codesnippet/CPP/cframewndex-class_1.h)]  
[!code-cpp[NVC_MFC_WordPad#4](../../mfc/reference/codesnippet/CPP/cframewndex-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CFrameWndEx](../../mfc/reference/cframewndex-class.md)  
  
## Requisitos  
 **encabezado:** afxframewndex.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)