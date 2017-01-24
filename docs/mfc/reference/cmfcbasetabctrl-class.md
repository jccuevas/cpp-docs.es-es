---
title: "CMFCBaseTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCBaseTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCBaseTabCtrl class"
ms.assetid: 7270c55f-6f6e-4dd2-b0d2-291afeac3882
caps.latest.revision: 41
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCBaseTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la funcionalidad básica para las ventanas con pestañas.  
  
## Sintaxis  
  
```  
class CMFCBaseTabCtrl : public CWnd  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::AddIcon](../Topic/CMFCBaseTabCtrl::AddIcon.md)||  
|[CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md)|Agrega una pestaña nueva a la ventana con pestañas.|  
|[CMFCBaseTabCtrl::ApplyRestoredTabInfo](../Topic/CMFCBaseTabCtrl::ApplyRestoredTabInfo.md)||  
|[CMFCBaseTabCtrl::AutoDestroyWindow](../Topic/CMFCBaseTabCtrl::AutoDestroyWindow.md)||  
|[CMFCBaseTabCtrl::CalcRectEdit](../Topic/CMFCBaseTabCtrl::CalcRectEdit.md)||  
|[CMFCBaseTabCtrl::CleanUp](../Topic/CMFCBaseTabCtrl::CleanUp.md)||  
|[CMFCBaseTabCtrl::ClearImageList](../Topic/CMFCBaseTabCtrl::ClearImageList.md)||  
|[CMFCBaseTabCtrl::DetachTab](../Topic/CMFCBaseTabCtrl::DetachTab.md)|Desasocia una pestaña de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::EnableActivateLastActive](../Topic/CMFCBaseTabCtrl::EnableActivateLastActive.md)||  
|[CMFCBaseTabCtrl::EnableAutoColor](../Topic/CMFCBaseTabCtrl::EnableAutoColor.md)|Habilita o deshabilita el coloreado automático de las pestañas.|  
|[CMFCBaseTabCtrl::EnableCustomToolTips](../Topic/CMFCBaseTabCtrl::EnableCustomToolTips.md)|Habilita o deshabilita la información sobre herramientas personalizada para las pestañas.|  
|[CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)|Habilita o deshabilita la edición directa de etiquetas de pestaña.|  
|[CMFCBaseTabCtrl::EnableTabDetach](../Topic/CMFCBaseTabCtrl::EnableTabDetach.md)|Habilita la capacidad de desasociar pestañas.|  
|[CMFCBaseTabCtrl::EnableTabSwap](../Topic/CMFCBaseTabCtrl::EnableTabSwap.md)|Permite o no que el usuario cambie el orden de las pestañas con el mouse.|  
|[CMFCBaseTabCtrl::EnsureVisible](../Topic/CMFCBaseTabCtrl::EnsureVisible.md)|Desplaza las pestañas hasta que la pestaña especificada sea visible. Este método no tiene ningún efecto si la pestaña especificada ya es visible.|  
|[CMFCBaseTabCtrl::EnterDragMode](../Topic/CMFCBaseTabCtrl::EnterDragMode.md)||  
|[CMFCBaseTabCtrl::FindTargetWnd](../Topic/CMFCBaseTabCtrl::FindTargetWnd.md)|Devuelve un panel que contiene un punto especificado.|  
|[CMFCBaseTabCtrl::FireChangeActiveTab](../Topic/CMFCBaseTabCtrl::FireChangeActiveTab.md)||  
|[CMFCBaseTabCtrl::FireChangingActiveTab](../Topic/CMFCBaseTabCtrl::FireChangingActiveTab.md)||  
|[CMFCBaseTabCtrl::GetActiveTab](../Topic/CMFCBaseTabCtrl::GetActiveTab.md)|Devuelve el índice de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveTabColor](../Topic/CMFCBaseTabCtrl::GetActiveTabColor.md)|Devuelve el color de fondo de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveTabTextColor](../Topic/CMFCBaseTabCtrl::GetActiveTabTextColor.md)|Devuelve el color del texto de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveWnd](../Topic/CMFCBaseTabCtrl::GetActiveWnd.md)|Devuelve un puntero a la página activa del control de pestañas.|  
|[CMFCBaseTabCtrl::GetAutoColors](../Topic/CMFCBaseTabCtrl::GetAutoColors.md)|Devuelve una referencia a la matriz de colores que se usan para el coloreado automático.|  
|[CMFCBaseTabCtrl::GetFirstVisibleTab](../Topic/CMFCBaseTabCtrl::GetFirstVisibleTab.md)|Devuelve un puntero a la primera pestaña visible.|  
|[CMFCBaseTabCtrl::GetFirstVisibleTabNum](../Topic/CMFCBaseTabCtrl::GetFirstVisibleTabNum.md)||  
|[CMFCBaseTabCtrl::GetHighlightedTab](../Topic/CMFCBaseTabCtrl::GetHighlightedTab.md)|Devuelve el índice de la pestaña resaltada actualmente.|  
|[CMFCBaseTabCtrl::GetImageList](../Topic/CMFCBaseTabCtrl::GetImageList.md)||  
|[CMFCBaseTabCtrl::GetImageSize](../Topic/CMFCBaseTabCtrl::GetImageSize.md)||  
|[CMFCBaseTabCtrl::GetLastVisibleTab](../Topic/CMFCBaseTabCtrl::GetLastVisibleTab.md)||  
|[CMFCBaseTabCtrl::GetLocation](../Topic/CMFCBaseTabCtrl::GetLocation.md)|Devuelve una variable del tipo de datos LOCATION, que indica dónde se sitúa el área de pestañas en relación con el control de pestaña. Por ejemplo, en la parte superior o en la parte inferior.|  
|[CMFCBaseTabCtrl::GetMaxWindowSize](../Topic/CMFCBaseTabCtrl::GetMaxWindowSize.md)||  
|[CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)|Devuelve el tamaño y la posición del área de pestañas de la ventana con pestañas. La posición del área de pestañas se define con coordenadas.|  
|[CMFCBaseTabCtrl::GetTabBkColor](../Topic/CMFCBaseTabCtrl::GetTabBkColor.md)|Devuelve el color de fondo de la pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabBorderSize](../Topic/CMFCBaseTabCtrl::GetTabBorderSize.md)|Devuelve el tamaño de los bordes de la pestaña en el control de pestaña.|  
|[CMFCBaseTabCtrl::GetTabByID](../Topic/CMFCBaseTabCtrl::GetTabByID.md)|Devuelve el índice de la pestaña que se identifica con un id. especificado.|  
|[CMFCBaseTabCtrl::GetTabCloseButton](../Topic/CMFCBaseTabCtrl::GetTabCloseButton.md)||  
|[CMFCBaseTabCtrl::GetTabFromHwnd](../Topic/CMFCBaseTabCtrl::GetTabFromHwnd.md)|Devuelve el índice de una pestaña que contiene un objeto HWND especificado.|  
|[CMFCBaseTabCtrl::GetTabFromPoint](../Topic/CMFCBaseTabCtrl::GetTabFromPoint.md)|Devuelve la pestaña que contiene un punto especificado.|  
|[CMFCBaseTabCtrl::GetTabFullWidth](../Topic/CMFCBaseTabCtrl::GetTabFullWidth.md)||  
|[CMFCBaseTabCtrl::GetTabHicon](../Topic/CMFCBaseTabCtrl::GetTabHicon.md)|Devuelve el icono asociado a la pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabID](../Topic/CMFCBaseTabCtrl::GetTabID.md)|Devuelve el id. de una pestaña con el índice de la pestaña.|  
|[CMFCBaseTabCtrl::GetTabIcon](../Topic/CMFCBaseTabCtrl::GetTabIcon.md)|Devuelve el id. del icono de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabLabel](../Topic/CMFCBaseTabCtrl::GetTabLabel.md)|Devuelve el texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabRect](../Topic/CMFCBaseTabCtrl::GetTabRect.md)|Recupera el tamaño y la posición de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabsHeight](../Topic/CMFCBaseTabCtrl::GetTabsHeight.md)||  
|[CMFCBaseTabCtrl::GetTabsRect](../Topic/CMFCBaseTabCtrl::GetTabsRect.md)||  
|[CMFCBaseTabCtrl::GetTabTextColor](../Topic/CMFCBaseTabCtrl::GetTabTextColor.md)|Devuelve el color del texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabWnd](../Topic/CMFCBaseTabCtrl::GetTabWnd.md)|Devuelve el puntero a un panel que se encuentra en una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabWndNoWrapper](../Topic/CMFCBaseTabCtrl::GetTabWndNoWrapper.md)|Devuelve el puntero directo a un control que se encuentra en una pestaña especificada, incluso si el control tiene un contenedor.|  
|[CMFCBaseTabCtrl::GetTabsNum](../Topic/CMFCBaseTabCtrl::GetTabsNum.md)|Devuelve el número de pestañas que se encuentran en el control de pestaña.|  
|[CMFCBaseTabCtrl::GetToolTipCtrl](../Topic/CMFCBaseTabCtrl::GetToolTipCtrl.md)|Devuelve una referencia al control de información sobre herramientas asociado al objeto `CMFCBaseTabCtrl`.|  
|[CMFCBaseTabCtrl::GetVisibleTabsNum](../Topic/CMFCBaseTabCtrl::GetVisibleTabsNum.md)|Devuelve el número de pestañas visibles.|  
|[CMFCBaseTabCtrl::HasImage](../Topic/CMFCBaseTabCtrl::HasImage.md)||  
|[CMFCBaseTabCtrl::HideSingleTab](../Topic/CMFCBaseTabCtrl::HideSingleTab.md)|Establece una opción que oculta la pestaña de una ventana, pero solo si la ventana con pestañas muestra una sola pestaña visible.|  
|[CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md)|Inserta una pestaña nueva.|  
|[CMFCBaseTabCtrl::InvalidateTab](../Topic/CMFCBaseTabCtrl::InvalidateTab.md)||  
|[CMFCBaseTabCtrl::IsActiveTabCloseButton](../Topic/CMFCBaseTabCtrl::IsActiveTabCloseButton.md)||  
|[CMFCBaseTabCtrl::IsAutoColor](../Topic/CMFCBaseTabCtrl::IsAutoColor.md)|Devuelve un valor que indica si una ventana con pestañas está en modo de color automático.|  
|[CMFCBaseTabCtrl::IsAutoDestroyWindow](../Topic/CMFCBaseTabCtrl::IsAutoDestroyWindow.md)||  
|[CMFCBaseTabCtrl::IsColored](../Topic/CMFCBaseTabCtrl::IsColored.md)||  
|[CMFCBaseTabCtrl::IsDialogControl](../Topic/CMFCBaseTabCtrl::IsDialogControl.md)||  
|[CMFCBaseTabCtrl::IsDrawNoPrefix](../Topic/CMFCBaseTabCtrl::IsDrawNoPrefix.md)||  
|[CMFCBaseTabCtrl::IsFlatFrame](../Topic/CMFCBaseTabCtrl::IsFlatFrame.md)|Devuelve un valor que indica si el formato del marco del área de pestañas es plano o en 3D.|  
|[CMFCBaseTabCtrl::IsFlatTab](../Topic/CMFCBaseTabCtrl::IsFlatTab.md)||  
|[CMFCBaseTabCtrl::IsHideSingleTab](../Topic/CMFCBaseTabCtrl::IsHideSingleTab.md)|Devuelve un valor que indica si el control de pestaña está configurado para ocultar una pestaña, pero solo si la ventana con pestañas tiene una sola pestaña visible.|  
|[CMFCBaseTabCtrl::IsIconAdded](../Topic/CMFCBaseTabCtrl::IsIconAdded.md)||  
|[CMFCBaseTabCtrl::IsInPlaceEdit](../Topic/CMFCBaseTabCtrl::IsInPlaceEdit.md)|Indica si los usuarios pueden modificar la etiqueta de una pestaña.|  
|[CMFCBaseTabCtrl::IsLeftRightRounded](../Topic/CMFCBaseTabCtrl::IsLeftRightRounded.md)||  
|[CMFCBaseTabCtrl::IsMDITab](../Topic/CMFCBaseTabCtrl::IsMDITab.md)||  
|[CMFCBaseTabCtrl::IsOneNoteStyle](../Topic/CMFCBaseTabCtrl::IsOneNoteStyle.md)|Indica si una ventana con pestañas muestra las pestañas con el estilo de Microsoft OneNote.|  
|[CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)|Comprueba si existe un punto especificado en el área de pestañas.|  
|[CMFCBaseTabCtrl::IsTabCloseButtonHighlighted](../Topic/CMFCBaseTabCtrl::IsTabCloseButtonHighlighted.md)||  
|[CMFCBaseTabCtrl::IsTabCloseButtonPressed](../Topic/CMFCBaseTabCtrl::IsTabCloseButtonPressed.md)||  
|[CMFCBaseTabCtrl::IsTabDetachable](../Topic/CMFCBaseTabCtrl::IsTabDetachable.md)|Indica si una pestaña se puede desasociar.|  
|[CMFCBaseTabCtrl::IsTabIconOnly](../Topic/CMFCBaseTabCtrl::IsTabIconOnly.md)|Indica si las pestañas muestran iconos pero no etiquetas.|  
|[CMFCBaseTabCtrl::IsTabSwapEnabled](../Topic/CMFCBaseTabCtrl::IsTabSwapEnabled.md)|Indica si el usuario puede cambiar la posición de las pestañas arrastrándolas.|  
|[CMFCBaseTabCtrl::IsTabVisible](../Topic/CMFCBaseTabCtrl::IsTabVisible.md)|Indica si una pestaña especificada es visible.|  
|[CMFCBaseTabCtrl::IsVS2005Style](../Topic/CMFCBaseTabCtrl::IsVS2005Style.md)||  
|[CMFCBaseTabCtrl::MoveTab](../Topic/CMFCBaseTabCtrl::MoveTab.md)||  
|[CMFCBaseTabCtrl::OnChangeTabs](../Topic/CMFCBaseTabCtrl::OnChangeTabs.md)|Llamado por el marco cuando cambia el número de pestañas.|  
|[CMFCBaseTabCtrl::OnDragEnter](../Topic/CMFCBaseTabCtrl::OnDragEnter.md)||  
|[CMFCBaseTabCtrl::OnDragLeave](../Topic/CMFCBaseTabCtrl::OnDragLeave.md)||  
|[CMFCBaseTabCtrl::OnDragOver](../Topic/CMFCBaseTabCtrl::OnDragOver.md)||  
|[CMFCBaseTabCtrl::OnDrop](../Topic/CMFCBaseTabCtrl::OnDrop.md)||  
|[CMFCBaseTabCtrl::OnRenameTab](../Topic/CMFCBaseTabCtrl::OnRenameTab.md)||  
|[CMFCBaseTabCtrl::PreTranslateMessage](../Topic/CMFCBaseTabCtrl::PreTranslateMessage.md)|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934). \(Invalida [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md)\).|  
|[CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)|Vuelve a calcular el diseño interno de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::RemoveAllTabs](../Topic/CMFCBaseTabCtrl::RemoveAllTabs.md)|Quita todas las pestañas de la ventana con pestañas.|  
|[CMFCBaseTabCtrl::RemoveTab](../Topic/CMFCBaseTabCtrl::RemoveTab.md)|Quita una pestaña de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::RenameTab](../Topic/CMFCBaseTabCtrl::RenameTab.md)||  
|[CMFCBaseTabCtrl::ResetImageList](../Topic/CMFCBaseTabCtrl::ResetImageList.md)|Restablece la lista de imágenes que se adjunta a una ventana con pestañas.|  
|[CMFCBaseTabCtrl::Serialize](../Topic/CMFCBaseTabCtrl::Serialize.md)|Lee o escribe este objeto de o en un archivo. \(Invalida [CObject::Serialize](../Topic/CObject::Serialize.md)\).|  
|[CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)|Activa una pestaña.|  
|[CMFCBaseTabCtrl::SetActiveTabColor](../Topic/CMFCBaseTabCtrl::SetActiveTabColor.md)|Establece el color de fondo de la pestaña actualmente activa.|  
|[CMFCBaseTabCtrl::SetActiveTabTextColor](../Topic/CMFCBaseTabCtrl::SetActiveTabTextColor.md)|Establece el color del texto de las pestañas activas.|  
|[CMFCBaseTabCtrl::SetAutoColors](../Topic/CMFCBaseTabCtrl::SetAutoColors.md)|Establece los colores de control de pestaña que se aplican en el modo de color automático.|  
|[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../Topic/CMFCBaseTabCtrl::SetDockingBarWrapperRTC.md)|Establece la clase de contenedor que se usa para los objetos que no derivan de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCBaseTabCtrl::SetDrawNoPrefix](../Topic/CMFCBaseTabCtrl::SetDrawNoPrefix.md)|Habilita y deshabilita el procesamiento de caracteres de prefijo cuando se dibujan las etiquetas de la pestaña.|  
|[CMFCBaseTabCtrl::SetImageList](../Topic/CMFCBaseTabCtrl::SetImageList.md)|Establece la lista de imágenes de iconos.|  
|[CMFCBaseTabCtrl::SetLocation](../Topic/CMFCBaseTabCtrl::SetLocation.md)||  
|[CMFCBaseTabCtrl::SetTabBkColor](../Topic/CMFCBaseTabCtrl::SetTabBkColor.md)|Establece el color de fondo de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabBorderSize](../Topic/CMFCBaseTabCtrl::SetTabBorderSize.md)|Establece un nuevo tamaño de borde de pestaña.|  
|[CMFCBaseTabCtrl::SetTabHicon](../Topic/CMFCBaseTabCtrl::SetTabHicon.md)|Establece un icono de pestaña.|  
|[CMFCBaseTabCtrl::SetTabIcon](../Topic/CMFCBaseTabCtrl::SetTabIcon.md)|Establece un id. de icono de pestaña.|  
|[CMFCBaseTabCtrl::SetTabIconOnly](../Topic/CMFCBaseTabCtrl::SetTabIconOnly.md)|Habilita y deshabilita el modo "solo icono" de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabLabel](../Topic/CMFCBaseTabCtrl::SetTabLabel.md)|Establece una etiqueta de pestaña igual que un valor de cadena especificado.|  
|[CMFCBaseTabCtrl::SetTabsHeight](../Topic/CMFCBaseTabCtrl::SetTabsHeight.md)||  
|[CMFCBaseTabCtrl::SetTabTextColor](../Topic/CMFCBaseTabCtrl::SetTabTextColor.md)|Establece el color del texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabsOrder](../Topic/CMFCBaseTabCtrl::SetTabsOrder.md)|Organiza las pestañas en el orden especificado.|  
|[CMFCBaseTabCtrl::ShowTab](../Topic/CMFCBaseTabCtrl::ShowTab.md)|Muestra u oculta la pestaña especificada.|  
|[CMFCBaseTabCtrl::StartRenameTab](../Topic/CMFCBaseTabCtrl::StartRenameTab.md)||  
|[CMFCBaseTabCtrl::SwapTabs](../Topic/CMFCBaseTabCtrl::SwapTabs.md)||  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::CreateWrapper](../Topic/CMFCBaseTabCtrl::CreateWrapper.md)|Crea un contenedor para un objeto derivado de [CWnd](../../mfc/reference/cwnd-class.md) que no deriva de `CDockablePane`. Para acoplar un objeto `CMFCBaseTabCtrl`, cada control incrustado debe tener un contenedor de acoplamiento o bien debe derivarse de `CDockablePane`.<br /><br /> Establece la clase del contenedor mediante `SetDockingBayWrapperRTC`.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCBaseTabCtrl::m\_bActivateTabOnRightClick](../Topic/CMFCBaseTabCtrl::m_bActivateTabOnRightClick.md)|Especifica si las pestañas se seleccionan con un clic en el botón izquierdo o secundario del mouse.|  
|[CMFCBaseTabCtrl::m\_bAutoDestroyWindow](../Topic/CMFCBaseTabCtrl::m_bAutoDestroyWindow.md)|Especifica si los paneles incluidos en las pestañas se destruyen automáticamente.|  
  
## Comentarios  
 La clase `CMFCBaseTabCtrl` es abstracta. Por lo tanto, no se pueden crear instancias en ella. Para crear una ventana con pestañas, debe derivar una clase de `CMFCBaseTabCtrl`. La biblioteca MFC contiene algunos ejemplos de clases derivadas, dos de las cuales son [CMFCTabCtrl Class](../../mfc/reference/cmfctabctrl-class.md) y [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md).  
  
 A partir de [!INCLUDE[vs_dev14](../../ide/includes/vs_dev14_md.md)], esta clase es compatible con Microsoft Active Accessibility.  
  
## Sugerencias de personalización  
 Las siguientes sugerencias se refieren a la [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) y a todas sus clases heredadas:  
  
-   Si permite que las pestañas se puedan desasociar, no mantenga los punteros a las ventanas con pestañas. Estas pestañas desasociables se pueden crear y destruir de forma dinámica. Por lo tanto, los punteros pueden quedar invalidados.  
  
-   Puede configurar el control de pestaña para que los usuarios puedan mover las pestañas dinámicamente en un control de pestaña con el mouse. Esta funcionalidad está integrada en la clase `CMFCBaseTabCtrl`. Para habilitarla, llame a [CMFCBaseTabCtrl::EnableTabSwap](../Topic/CMFCBaseTabCtrl::EnableTabSwap.md).  
  
-   De forma predeterminada, las pestañas son desasociables al agregarlas a un control de pestaña. También puede agregar pestañas no desasociables mediante [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md). Si establece el parámetro `bDetachable` en `FALSE`, la pestaña no se podrá desasociar. También puede cambiar si las pestañas son desasociables llamando al método [CMFCBaseTabCtrl::EnableTabDetach](../Topic/CMFCBaseTabCtrl::EnableTabDetach.md).  
  
-   Los objetos que se derivan de la [CWnd \(clase\)](../../mfc/reference/cwnd-class.md) se pueden colocar en una barra de control acoplable o en una pestaña acoplable. Para que todo el control quede acoplado, debe convertir el objeto `CWnd` en acoplable. Para ello, MFC usa una clase contenedora. Esta clase de contenedor es [CDockablePaneAdapter Class](../../mfc/reference/cdockablepaneadapter-class.md). Cualquier objeto `CWnd` que se agregue a una barra de control acoplable o a una pestaña acoplable se ajustará dentro de un objeto `CDockablePaneAdapter`. Puede deshabilitar el ajuste automático estableciendo el parámetro `m_bEnableWrapping` del objeto `CMFCBaseTablCtrl` en `FALSE`. También puede cambiar la clase de la aplicación podrá usar como un contenedor mediante el método [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../Topic/CMFCBaseTabCtrl::SetDockingBarWrapperRTC.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
## Requisitos  
 **Encabezado:** afxbasetabctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl Class](../../mfc/reference/cmfctabctrl-class.md)   
 [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md)