---
title: "CDockingManager Class | Microsoft Docs"
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
  - "CDockingManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockingManager class"
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
caps.latest.revision: 37
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockingManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad básica que controla el diseño de acoplamiento en una ventana de marco principal.  
  
## Sintaxis  
  
```  
class CDockingManager : public CObject  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockingManager::AddDockSite](../Topic/CDockingManager::AddDockSite.md)|Crear un panel de acoplamiento y lo agrega a la lista de barras de controles.|  
|[CDockingManager::AddHiddenMDITabbedBar](../Topic/CDockingManager::AddHiddenMDITabbedBar.md)|Agrega un identificador a un panel de barra a la lista de paneles con pestañas MDI ocultos de la barra.|  
|[CDockingManager::AddMiniFrame](../Topic/CDockingManager::AddMiniFrame.md)|Agrega un cuadro a la lista de mini marcos.|  
|[CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md)|Registra un panel con el administrador de acoplamiento.|  
|[CDockingManager::AdjustDockingLayout](../Topic/CDockingManager::AdjustDockingLayout.md)|Actualiza y ajusta el diseño de todos los paneles en una ventana de marco.|  
|[CDockingManager::AdjustPaneFrames](../Topic/CDockingManager::AdjustPaneFrames.md)|Hace que el mensaje de `WM_NCCALCSIZE` se envía a todos los paneles y ventanas de `CPaneFrameWnd` .|  
|[CDockingManager::AdjustRectToClientArea](../Topic/CDockingManager::AdjustRectToClientArea.md)|ajusta la alineación de un rectángulo.|  
|[CDockingManager::AlignAutoHidePane](../Topic/CDockingManager::AlignAutoHidePane.md)|Cambia el tamaño de un panel acoplable en ocultan automáticamente el modo para registrar el ancho completo o el alto del área de cliente del cuadro entre los sitios de vinculación.|  
|[CDockingManager::AutoHidePane](../Topic/CDockingManager::AutoHidePane.md)|Crea una barra de herramientas de ocultar automáticamente.|  
|[CDockingManager::BringBarsToTop](../Topic/CDockingManager::BringBarsToTop.md)|Aporta las barras acopladas que tienen la alineación especificada a la parte superior.|  
|[CDockingManager::BuildPanesMenu](../Topic/CDockingManager::BuildPanesMenu.md)|Agregar nombres de los paneles y las barras de herramientas acoplable a un menú.|  
|[CDockingManager::CalcExpectedDockedRect](../Topic/CDockingManager::CalcExpectedDockedRect.md)|calcula el rectángulo esperado de una ventana acoplada.|  
|[CDockingManager::Create](../Topic/CDockingManager::Create.md)|Crea un administrador de acoplamiento.|  
|[CDockingManager::DeterminePaneAndStatus](../Topic/CDockingManager::DeterminePaneAndStatus.md)|Determina el panel que contiene un punto determinado y su estado de acoplamiento.|  
|[CDockingManager::DisableRestoreDockState](../Topic/CDockingManager::DisableRestoreDockState.md)|Habilita o deshabilita la carga del diseño de acoplamiento de registro.|  
|[CDockingManager::DockPane](../Topic/CDockingManager::DockPane.md)|Acoplar un panel a otro panel o a una ventana de marco.|  
|[CDockingManager::DockPaneLeftOf](../Topic/CDockingManager::DockPaneLeftOf.md)|Acoplar un panel a la izquierda de otro panel.|  
|[CDockingManager::EnableAutoHidePanes](../Topic/CDockingManager::EnableAutoHidePanes.md)|Habilita el acoplamiento del panel al cuadro principal, crea un panel de acoplamiento, y lo agrega a la lista de barras de controles.|  
|[CDockingManager::EnableDocking](../Topic/CDockingManager::EnableDocking.md)|Crear un panel de acoplamiento y habilita el acoplamiento del panel al cuadro principal.|  
|[CDockingManager::EnableDockSiteMenu](../Topic/CDockingManager::EnableDockSiteMenu.md)|Muestra un botón adicional que abre un menú emergente en leyendas de todos los paneles de acoplamiento.|  
|[CDockingManager::EnablePaneContextMenu](../Topic/CDockingManager::EnablePaneContextMenu.md)|Indica a la biblioteca que muestra un menú contextual especial que tenga una lista de barras de herramientas de la aplicación y paneles de acoplamiento cuando el usuario hace clic con el botón secundario del mouse y la biblioteca está procesando el mensaje de WM\_CONTEXTMENU.|  
|[CDockingManager::FindDockSite](../Topic/CDockingManager::FindDockSite.md)|Recupera el panel de barra que está en la posición especificada y que tiene la alineación especificada.|  
|[CDockingManager::FindDockSiteByPane](../Topic/CDockingManager::FindDockSiteByPane.md)|Devuelve el panel de barra que tiene el id. del panel de barra de destino.|  
|[CDockingManager::FindPaneByID](../Topic/CDockingManager::FindPaneByID.md)|Encuentra un panel por identificador especificada del control|  
|[CDockingManager::FixupVirtualRects](../Topic/CDockingManager::FixupVirtualRects.md)|Confirma todas las posiciones actuales de la barra de herramientas a los rectángulos virtuales.|  
|[CDockingManager::FrameFromPoint](../Topic/CDockingManager::FrameFromPoint.md)|Devuelve el cuadro que contiene el punto determinado.|  
|[CDockingManager::GetClientAreaBounds](../Topic/CDockingManager::GetClientAreaBounds.md)|Obtiene el rectángulo que contiene los límites del área de cliente.|  
|[CDockingManager::GetDockingMode](../Topic/CDockingManager::GetDockingMode.md)|Devuelve el modo actual de acoplamiento.|  
|[CDockingManager::GetDockSiteFrameWnd](../Topic/CDockingManager::GetDockSiteFrameWnd.md)|Obtiene un puntero al cuadro de la ventana primaria.|  
|[CDockingManager::GetEnabledAutoHideAlignment](../Topic/CDockingManager::GetEnabledAutoHideAlignment.md)|Devuelve la alineación habilitado de paneles.|  
|[CDockingManager::GetMiniFrames](../Topic/CDockingManager::GetMiniFrames.md)|obtiene una lista de miniframes.|  
|[CDockingManager::GetOuterEdgeBounds](../Topic/CDockingManager::GetOuterEdgeBounds.md)|Obtiene un rectángulo que contiene los bordes externos de conversión.|  
|[CDockingManager::GetPaneList](../Topic/CDockingManager::GetPaneList.md)|Devuelve una lista de paneles que pertenecen al administrador de acoplamiento.  Esto incluye todos los paneles de punto flotante.|  
|[CDockingManager::GetSmartDockingManager](../Topic/CDockingManager::GetSmartDockingManager.md)|Recupera un puntero al administrador inteligente de acoplamiento.|  
|[CDockingManager::GetSmartDockingManagerPermanent](../Topic/CDockingManager::GetSmartDockingManagerPermanent.md)|Recupera un puntero al administrador inteligente de acoplamiento.|  
|[CDockingManager::GetSmartDockingParams](../Topic/CDockingManager::GetSmartDockingParams.md)|Devuelve los parámetros inteligentes de acoplamiento para el administrador de acoplamiento.|  
|[CDockingManager::GetSmartDockingTheme](../Topic/CDockingManager::GetSmartDockingTheme.md)|Un método estático que devuelve un tema utilizado para mostrar marcadores inteligentes de acoplamiento.|  
|[CDockingManager::HideAutoHidePanes](../Topic/CDockingManager::HideAutoHidePanes.md)|Oculta un panel que sea en ocultar automáticamente el modo.|  
|[CDockingManager::InsertDockSite](../Topic/CDockingManager::InsertDockSite.md)|Crear un panel de acoplamiento y se inserta en la lista de barras de controles.|  
|[CDockingManager::InsertPane](../Topic/CDockingManager::InsertPane.md)|Inserta un panel de control en la lista de barras de controles.|  
|[CDockingManager::IsDockSiteMenu](../Topic/CDockingManager::IsDockSiteMenu.md)|Especifica si un menú emergente aparece en leyendas de todos los paneles.|  
|[CDockingManager::IsInAdjustLayout](../Topic/CDockingManager::IsInAdjustLayout.md)|Determina si los diseños de todos los paneles se encapsulan.|  
|[CDockingManager::IsOLEContainerMode](../Topic/CDockingManager::IsOLEContainerMode.md)|Especifica si el administrador de acoplamiento está en modo OLE del contenedor.|  
|[CDockingManager::IsPointNearDockSite](../Topic/CDockingManager::IsPointNearDockSite.md)|Determina si un punto especificado está cerca del sitio de vinculación.|  
|[CDockingManager::IsPrintPreviewValid](../Topic/CDockingManager::IsPrintPreviewValid.md)|Determina si está establecido el modo de vista previa de impresión.|  
|[CDockingManager::LoadState](../Topic/CDockingManager::LoadState.md)|Carga el estado del administrador de acoplamiento de registro.|  
|[CDockingManager::LockUpdate](../Topic/CDockingManager::LockUpdate.md)|Bloquea la ventana especificada.|  
|[CDockingManager::OnActivateFrame](../Topic/CDockingManager::OnActivateFrame.md)|Llamado por el marco cuando la ventana de marco se crea activa o desactiva.|  
|[CDockingManager::OnClosePopupMenu](../Topic/CDockingManager::OnClosePopupMenu.md)|Llamado por el marco cuando un menú emergente activo procesa un mensaje WM\_DESTROY.|  
|[CDockingManager::OnMoveMiniFrame](../Topic/CDockingManager::OnMoveMiniFrame.md)|Llamado por el marco para mover una ventana de marco recudido.|  
|[CDockingManager::OnPaneContextMenu](../Topic/CDockingManager::OnPaneContextMenu.md)|Llamado por el marco cuando compila un menú que tenga una lista de paneles.|  
|[CDockingManager::PaneFromPoint](../Topic/CDockingManager::PaneFromPoint.md)|Devuelve el panel que contiene el punto determinado.|  
|[CDockingManager::ProcessPaneContextMenuCommand](../Topic/CDockingManager::ProcessPaneContextMenuCommand.md)|Llamado por el marco a activar o desactivar una casilla para el comando especificado y actualizar el diseño de un panel mostrado.|  
|[CDockingManager::RecalcLayout](../Topic/CDockingManager::RecalcLayout.md)|Actualiza el diseño interno de controles presentes en la lista de controles.|  
|[CDockingManager::ReleaseEmptyPaneContainers](../Topic/CDockingManager::ReleaseEmptyPaneContainers.md)|Libera los contenedores vacíos del panel.|  
|[CDockingManager::RemoveHiddenMDITabbedBar](../Topic/CDockingManager::RemoveHiddenMDITabbedBar.md)|Quita el panel oculto especificado de la barra.|  
|[CDockingManager::RemoveMiniFrame](../Topic/CDockingManager::RemoveMiniFrame.md)|Quita un cuadro especificado de la lista de mini marcos.|  
|[CDockingManager::RemovePaneFromDockManager](../Topic/CDockingManager::RemovePaneFromDockManager.md)|Anula un panel y colóquelo en la lista en el administrador de acoplamiento.|  
|[CDockingManager::ReplacePane](../Topic/CDockingManager::ReplacePane.md)|reemplaza un panel con otro.|  
|[CDockingManager::ResortMiniFramesForZOrder](../Topic/CDockingManager::ResortMiniFramesForZOrder.md)|Recurren los marcos en la lista de mini marcos.|  
|[CDockingManager::SaveState](../Topic/CDockingManager::SaveState.md)|Guarda el estado del administrador de acoplamiento al registro.|  
|[CDockingManager::SendMessageToMiniFrames](../Topic/CDockingManager::SendMessageToMiniFrames.md)|envía el mensaje especificado a todos los mini cuadros.|  
|[CDockingManager::Serialize](../Topic/CDockingManager::Serialize.md)|Escribe el administrador de acoplamiento en un archivo.  \(Reemplaza [CObject::Serialize](../Topic/CObject::Serialize.md).\)|  
|[CDockingManager::SetAutohideZOrder](../Topic/CDockingManager::SetAutohideZOrder.md)|Establece el tamaño, el ancho, y el alto de las barras de control y del panel especificado.|  
|[CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md)|Establece el modo de acoplamiento.|  
|[CDockingManager::SetDockState](../Topic/CDockingManager::SetDockState.md)|Establece el estado de acoplamiento de las barras de control, los mini fotogramas, y las barras de ocultar automáticamente.|  
|[CDockingManager::SetPrintPreviewMode](../Topic/CDockingManager::SetPrintPreviewMode.md)|Establece el modo de vista previa de impresión de barras que se muestran en la vista previa de impresión.|  
|[CDockingManager::SetSmartDockingParams](../Topic/CDockingManager::SetSmartDockingParams.md)|Establece los parámetros que definen el comportamiento del acoplamiento inteligente.|  
|[CDockingManager::ShowDelayShowMiniFrames](../Topic/CDockingManager::ShowDelayShowMiniFrames.md)|Muestra u oculta las ventanas de los mini marcos.|  
|[CDockingManager::ShowPanes](../Topic/CDockingManager::ShowPanes.md)|Muestra u oculta los paneles del control y oculta automáticamente las barras.|  
|[CDockingManager::StartSDocking](../Topic/CDockingManager::StartSDocking.md)|Inicia el acoplamiento inteligente de la ventana especificada como la alineación de administrador inteligente de acoplamiento.|  
|[CDockingManager::StopSDocking](../Topic/CDockingManager::StopSDocking.md)|Detiene el acoplamiento inteligente.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockingManager::m\_bHideDockingBarsInContainerMode](../Topic/CDockingManager::m_bHideDockingBarsInContainerMode.md)|Especifica si el administrador de acoplamiento oculta los paneles en modo de contenedor OLE.|  
|[CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md)|Especifica el modo global de acoplamiento.|  
|[CDockingManager::m\_nDockSensitivity](../Topic/CDockingManager::m_nDockSensitivity.md)|Especifica el carácter de acoplamiento.|  
|[CDockingManager::m\_nTimeOutBeforeDockingBarDock](../Topic/CDockingManager::m_nTimeOutBeforeDockingBarDock.md)|Especifica el tiempo, en milisegundos, antes de que un panel acoplable está acoplado en modo inmediato de acoplamiento.|  
|[CDockingManager::m\_nTimeOutBeforeToolBarDock](../Topic/CDockingManager::m_nTimeOutBeforeToolBarDock.md)|Especifica el tiempo, en milisegundos, antes de que una barra de herramientas está acoplada a la ventana de marco principal.|  
  
## Comentarios  
 La ventana de marco principal crea e inicializa esta clase automáticamente.  
  
 El objeto de administrador de acoplamiento contiene una lista de todos los paneles que están en el diseño de acoplamiento, así como una lista de todas las ventanas de [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) que pertenecen a la ventana de marco principal.  
  
 La clase de `CDockingManager` implementa algunos servicios que puede utilizar para buscar un panel o una ventana de `CPaneFrameWnd` .  No llama normalmente estos servicios directamente porque se incluyen en el objeto de la ventana de marco principal.  Para obtener más información, vea [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md).  
  
## Sugerencias de personalización  
 Las sugerencias siguientes se aplican a los objetos de `CDockingManager` :  
  
-   [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md) admite estos modos de acoplamiento:  
  
    -   `AFX_DOCK_TYPE::DT_IMMEDIATE`  
  
    -   `AFX_DOCK_TYPE::DT_STANDARD`  
  
    -   `AFX_DOCK_TYPE::DT_SMART`  
  
     Estos modos de acoplamiento son definidas por [CDockingManager::m\_dockModeGlobal](../Topic/CDockingManager::m_dockModeGlobal.md) y se establecen llamando a [CDockingManager::SetDockingMode](../Topic/CDockingManager::SetDockingMode.md).  
  
-   Si desea crear un panel no\-flotante, no\-dimensionable, llame al método de [CDockingManager::AddPane](../Topic/CDockingManager::AddPane.md) .  Este método registra el panel con el administrador de acoplamiento, que es responsable del diseño del panel.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CDockingManager` para configurar un objeto de `CDockingManager` .  El ejemplo muestra cómo mostrar un botón adicional que abre un menú emergente en leyendas de todos los paneles de acoplamiento y cómo establecer el modo de acoplamiento del objeto.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/CPP/cdockingmanager-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDockingManager](../../mfc/reference/cdockingmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxDockingManager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)