---
title: "Clase CMDIChildWndEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMDIChildWndEx"
  - "GetThisClass"
  - "CMDIChildWndEx::PreTranslateMessage"
  - "CMDIChildWndEx::ActivateFrame"
  - "CMDIChildWndEx.GetThisClass"
  - "CMDIChildWndEx::AddDockSite"
  - "CMDIChildWndEx.CreateObject"
  - "CMDIChildWndEx::CreateObject"
  - "CMDIChildWndEx.ActivateFrame"
  - "CMDIChildWndEx::GetThisClass"
  - "CMDIChildWndEx.PreTranslateMessage"
  - "PreTranslateMessage"
  - "ActivateFrame"
  - "CreateObject"
  - "CMDIChildWndEx.AddDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMDIChildWndEx (clase)"
  - "ActivateFrame (método)"
  - "PreTranslateMessage (método)"
  - "GetThisClass (método)"
  - "CreateObject (método)"
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# Clase CMDIChildWndEx
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMDIChildWndEx` proporciona la funcionalidad de una ventana secundaria de \(MDI\) de interfaz de múltiples documentos de Windows.  Extiende la funcionalidad de [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md).  El marco requiere esta clase cuando una aplicación MDI utiliza determinadas clases MFC.  
  
## Sintaxis  
  
```  
class CMDIChildWndEx : public CMDIChildWnd  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMDIChildWndEx::ActivateTopLevelFrame](../Topic/CMDIChildWndEx::ActivateTopLevelFrame.md)|Denominado internamente por el marco para activar el cuadro de nivel superior cuando la aplicación se debe provocar de una ficha de la barra de tareas.|  
|`CMDIChildWndEx::AddDockSite`|Este método no se utiliza o se implementa.|  
|[CMDIChildWndEx::AddPane](../Topic/CMDIChildWndEx::AddPane.md)|Agrega un panel.|  
|[CMDIChildWndEx::AddTabbedPane](../Topic/CMDIChildWndEx::AddTabbedPane.md)|Agrega un panel con fichas.|  
|[CMDIChildWndEx::AdjustDockingLayout](../Topic/CMDIChildWndEx::AdjustDockingLayout.md)|Ajustar el diseño de acoplamiento.|  
|[CMDIChildWndEx::CanShowOnMDITabs](../Topic/CMDIChildWndEx::CanShowOnMDITabs.md)||  
|[CMDIChildWndEx::CanShowOnTaskBarTabs](../Topic/CMDIChildWndEx::CanShowOnTaskBarTabs.md)|Indica el marco si este elemento secundario MDI puede generarse en las pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::CanShowOnWindowsList](../Topic/CMDIChildWndEx::CanShowOnWindowsList.md)|Devuelve `TRUE` si el nombre de la ventana MDI secundaria se puede mostrar en el cuadro de diálogo de [CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md).  En caso contrario, devuelve `FALSE`.|  
|`CMDIChildWndEx::CreateObject`|Llamado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMDIChildWndEx::DockPane](../Topic/CMDIChildWndEx::DockPane.md)|Acoplar un panel.|  
|[CMDIChildWndEx::DockPaneLeftOf](../Topic/CMDIChildWndEx::DockPaneLeftOf.md)|Lo acopla un panel a la izquierda de otro panel.|  
|[CMDIChildWndEx::EnableAutoHidePanes](../Topic/CMDIChildWndEx::EnableAutoHidePanes.md)|Enables oculta automáticamente el modo para los paneles cuando se acoplan en los lados especificados de la ventana.|  
|[CMDIChildWndEx::EnableDocking](../Topic/CMDIChildWndEx::EnableDocking.md)|Habilita el acoplamiento de la ventana secundaria al marco principal.|  
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::EnableTaskbarThumbnailClipRect.md)|Habilita o deshabilita a la selección automática de una parte del área cliente de una ventana para mostrar como miniaturas de esa ventana en la barra de tareas.|  
|[CMDIChildWndEx::GetDockingManager](../Topic/CMDIChildWndEx::GetDockingManager.md)||  
|[CMDIChildWndEx::GetDocumentName](../Topic/CMDIChildWndEx::GetDocumentName.md)|Devuelve el nombre del documento que se muestra en la ventana MDI secundaria.|  
|[CMDIChildWndEx::GetFrameIcon](../Topic/CMDIChildWndEx::GetFrameIcon.md)|Llamado por el marco para recuperar el icono de una ventana secundaria de MDI.|  
|[CMDIChildWndEx::GetFrameText](../Topic/CMDIChildWndEx::GetFrameText.md)|Llamado por el marco para recuperar el texto de la ventana MDI secundaria.|  
|[CMDIChildWndEx::GetPane](../Topic/CMDIChildWndEx::GetPane.md)|Encuentra un panel por identificador especificada del control|  
|[CMDIChildWndEx::GetRelatedTabGroup](../Topic/CMDIChildWndEx::GetRelatedTabGroup.md)||  
|[CMDIChildWndEx::GetTabbedPane](../Topic/CMDIChildWndEx::GetTabbedPane.md)|Devuelve un puntero a un panel incrustado de acoplamiento que se ha convertido en un documento con fichas.|  
|[CMDIChildWndEx::GetTabProxyWnd](../Topic/CMDIChildWndEx::GetTabProxyWnd.md)|Devuelve la ventana de proxy de la pestaña registrada realmente con pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::GetTaskbarPreviewWnd](../Topic/CMDIChildWndEx::GetTaskbarPreviewWnd.md)|Llamado por el marco cuando necesita obtener una ventana secundaria \(normalmente una ventana de vista o splitter\) que se mostrará en miniatura de la ficha de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::GetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::GetTaskbarThumbnailClipRect.md)|Llamado por el marco cuando seleccionan una parte del área cliente de una ventana para mostrar como miniaturas de esa ventana en la barra de tareas.|  
|`CMDIChildWndEx::GetThisClass`|Llamado por el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|[CMDIChildWndEx::GetToolbarButtonToolTipText](../Topic/CMDIChildWndEx::GetToolbarButtonToolTipText.md)|Llamado por el marco para recuperar la información sobre herramientas de un botón de la barra de herramientas.|  
|[CMDIChildWndEx::InsertPane](../Topic/CMDIChildWndEx::InsertPane.md)|Registra el panel especificado con el administrador de acoplamiento.|  
|[CMDIChildWndEx::InvalidateIconicBitmaps](../Topic/CMDIChildWndEx::InvalidateIconicBitmaps.md)|Invalida la representación bitmap icónica MDI secundario.|  
|[CMDIChildWndEx::IsPointNearDockSite](../Topic/CMDIChildWndEx::IsPointNearDockSite.md)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CMDIChildWndEx::IsReadOnly](../Topic/CMDIChildWndEx::IsReadOnly.md)|Devuelve `TRUE` si el documento que se muestra en la ventana secundaria es de solo lectura.  En caso contrario, devuelve `FALSE`.|  
|[CMDIChildWndEx::IsRegisteredWithTaskbarTabs](../Topic/CMDIChildWndEx::IsRegisteredWithTaskbarTabs.md)|Devuelve TRUE si se registran el elemento secundario de MDI correctamente con las fichas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::IsTabbedPane](../Topic/CMDIChildWndEx::IsTabbedPane.md)|Devuelve `TRUE` si la ventana MDI secundaria contiene un panel acoplable.  En caso contrario, devuelve `FALSE`.|  
|[CMDIChildWndEx::IsTaskbarTabsSupportEnabled](../Topic/CMDIChildWndEx::IsTaskbarTabsSupportEnabled.md)|Indica si el elemento secundario de MDI podría producirse en las pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](../Topic/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled.md)|Indica si la selección automática de una parte del área cliente de una ventana en la pantalla como miniaturas de esa ventana en la barra de tareas está habilitada o deshabilitada.|  
|[CMDIChildWndEx::m\_dwDefaultTaskbarTabPropertyFlags](../Topic/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags.md)|Una combinación de marcadores, que se pasa por el marco al método de SetTaskbarTabProperties, cuando una tabulación \(elemento secundario MDI\) se está registrando con pestañas de la barra de tareas de Windows 7.  La combinación predeterminada es STPF\_USEAPPTHUMBNAILWHENACTIVE &#124; STPF\_USEAPPPEEKWHENACTIVE.|  
|[CMDIChildWndEx::OnGetIconicLivePreviewBitmap](../Topic/CMDIChildWndEx::OnGetIconicLivePreviewBitmap.md)|Llamado por el marco cuando necesita obtener un mapa de bits para la vista previa dinámica MDI secundario.|  
|[CMDIChildWndEx::OnGetIconicThumbnail](../Topic/CMDIChildWndEx::OnGetIconicThumbnail.md)|Llamado por el marco cuando necesita obtener un mapa de bits para la miniatura icónica MDI secundario.|  
|[CMDIChildWndEx::OnMoveMiniFrame](../Topic/CMDIChildWndEx::OnMoveMiniFrame.md)|Llamado por el marco para mover una ventana de mini\- cuadro.|  
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](../Topic/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton.md)|Llamado por el marco cuando el usuario presiona el botón cerrar en miniatura de la ficha de la barra de tareas.|  
|[CMDIChildWndEx::OnSetPreviewMode](../Topic/CMDIChildWndEx::OnSetPreviewMode.md)|Llamado por el marco para entrar o salir de modo vista previa de impresión.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailActivate.md)|Llamado por el marco cuando la miniatura de la ficha de la barra de tareas debe procesar el mensaje de WM\_ACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate.md)|Llamado por el marco cuando la miniatura de la ficha de la barra de tareas debe procesar el mensaje de WM\_MOUSEACTIVATE.|  
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](../Topic/CMDIChildWndEx::OnTaskbarTabThumbnailStretch.md)|Llamado por el marco cuando necesita ajustar un mapa de bits para la vista previa de miniaturas de la ficha de la barra de tareas de Windows 7 MDI secundario.|  
|[CMDIChildWndEx::OnUpdateFrameTitle](../Topic/CMDIChildWndEx::OnUpdateFrameTitle.md)|Llamado por el marco para actualizar el título del cuadro.  \(Reemplaza `CMDIChildWnd::OnUpdateFrameTitle`.\)|  
|[CMDIChildWndEx::PaneFromPoint](../Topic/CMDIChildWndEx::PaneFromPoint.md)|Devuelve el panel que contiene el punto determinado.|  
|`CMDIChildWndEx::PreTranslateMessage`|Utiliza la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CMDIChildWndEx::RecalcLayout](../Topic/CMDIChildWndEx::RecalcLayout.md)|Actualiza el diseño de la ventana.|  
|[CMDIChildWndEx::RegisterTaskbarTab](../Topic/CMDIChildWndEx::RegisterTaskbarTab.md)|Elemento secundario de MDI de registros con pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::RemovePaneFromDockManager](../Topic/CMDIChildWndEx::RemovePaneFromDockManager.md)|Quita un panel del administrador de acoplamiento.|  
|[CMDIChildWndEx::SetRelatedTabGroup](../Topic/CMDIChildWndEx::SetRelatedTabGroup.md)||  
|[CMDIChildWndEx::SetTaskbarTabActive](../Topic/CMDIChildWndEx::SetTaskbarTabActive.md)|Provoca corresponder la ficha de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabOrder](../Topic/CMDIChildWndEx::SetTaskbarTabOrder.md)|Inserta el elemento secundario de MDI antes de ventana especificada en las pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarTabProperties](../Topic/CMDIChildWndEx::SetTaskbarTabProperties.md)|Establece las propiedades de una ficha de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::SetTaskbarThumbnailClipRect](../Topic/CMDIChildWndEx::SetTaskbarThumbnailClipRect.md)|Denominado internamente por el marco para establecer el rectángulo de recorte para seleccionar una parte del área cliente de una ventana para mostrar como miniaturas de esa ventana en la barra de tareas.|  
|[CMDIChildWndEx::ShowPane](../Topic/CMDIChildWndEx::ShowPane.md)||  
|[CMDIChildWndEx::UnregisterTaskbarTab](../Topic/CMDIChildWndEx::UnregisterTaskbarTab.md)|Quita el elemento secundario de MDI de las pestañas de la barra de tareas de Windows 7.|  
|[CMDIChildWndEx::UpdateTaskbarTabIcon](../Topic/CMDIChildWndEx::UpdateTaskbarTabIcon.md)|Icono de la ficha de la barra de tareas de Windows 7 de las actualizaciones.|  
  
## Comentarios  
 Para aprovechar características extendidas de acoplamiento en las aplicaciones MDI, derive la clase de ventana secundaria MDI de la aplicación de `CMDIChildWndEx` en lugar de [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md).  
  
## Ejemplo  
 El ejemplo siguiente crea una clase derivada de `CMDIChildWndEx`.  Este fragmento de código procede de [Ejemplo de VisualStudioDemo: Aplicación MFC Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/CPP/cmdichildwndex-class_1.h)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)  
  
 [CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)  
  
## Requisitos  
 **Encabezado:** afxMDIChildWndEx.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIChildWnd Class](../../mfc/reference/cmdichildwnd-class.md)   
 [CMFCWindowsManagerDialog Class](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)   
 [CMDIFrameWndEx \(Clase\)](../../mfc/reference/cmdiframewndex-class.md)