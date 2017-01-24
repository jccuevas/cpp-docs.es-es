---
title: "CMFCVisualManagerWindows Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerWindows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows class"
ms.assetid: 568b6e9e-8e67-4477-9a3d-2981cbd09861
caps.latest.revision: 46
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerWindows Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerWindows` imita el aspecto de Microsoft Windows XP o Microsoft Vista cuando el usuario selecciona un tema de Windows XP o de Vista.  
  
## Sintaxis  
  
```  
class CMFCVisualManagerWindows : public CMFCVisualManagerOfficeXP  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCVisualManagerWindows::CMFCVisualManagerWindows`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCVisualManagerWindows::AlwaysHighlight3DTabs](../Topic/CMFCVisualManagerWindows::AlwaysHighlight3DTabs.md)|El marco de trabajo llama a este método para determinar si las fichas 3D siempre deben aparecer resaltado en la aplicación.  \(Reemplaza [CMFCVisualManager::AlwaysHighlight3DTabs](../Topic/CMFCVisualManager::AlwaysHighlight3DTabs.md).\)|  
|[CMFCVisualManagerWindows::DrawComboBorderWinXP](../Topic/CMFCVisualManagerWindows::DrawComboBorderWinXP.md)|\(Reemplaza `CMFCVisualManager::DrawComboBorderWinXP`.\)|  
|[CMFCVisualManagerWindows::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawComboDropButtonWinXP.md)|\(Reemplaza [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md).\)|  
|[CMFCVisualManagerWindows::DrawPushButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawPushButtonWinXP.md)|\(Reemplaza [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md).\)|  
|[CMFCVisualManagerWindows::GetButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetButtonExtraBorder.md)|El marco de trabajo llama a este método cuando dibuja un botón de la barra de herramientas.  \(Reemplaza [CMFCVisualManager::GetButtonExtraBorder](../Topic/CMFCVisualManager::GetButtonExtraBorder.md).\)|  
|[CMFCVisualManagerWindows::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetCaptionButtonExtraBorder.md)|\(Reemplaza [CMFCVisualManager::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManager::GetCaptionButtonExtraBorder.md).\)|  
|[CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight](../Topic/CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight.md)|\(Reemplaza `CMFCVisualManager::GetDockingPaneCaptionExtraHeight`.\)|  
|[CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor](../Topic/CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::GetHighlightedMenuItemTextColor`.\)|  
|[CMFCVisualManagerWindows::GetPopupMenuGap](../Topic/CMFCVisualManagerWindows::GetPopupMenuGap.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::GetPopupMenuGap`.\)|  
|[CMFCVisualManagerWindows::GetToolbarButtonTextColor](../Topic/CMFCVisualManagerWindows::GetToolbarButtonTextColor.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::GetToolbarButtonTextColor`.\)|  
|[CMFCVisualManagerWindows::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManagerWindows::IsDefaultWinXPPopupButton.md)|\(Reemplaza [CMFCVisualManager::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManager::IsDefaultWinXPPopupButton.md).\)|  
|[CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::IsHighlightWholeMenuItem`.\)|  
|[CMFCVisualManagerWindows::IsOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeStyleMenus.md)||  
|[CMFCVisualManagerWindows::IsOfficeXPStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeXPStyleMenus.md)|Indica si el administrador visual implementa menús de XP\-estilo de Office.  \(Reemplaza [CMFCVisualManager::IsOfficeXPStyleMenus](../Topic/CMFCVisualManager::IsOfficeXPStyleMenus.md).\)|  
|[CMFCVisualManagerWindows::IsWindowsThemingSupported](../Topic/CMFCVisualManagerWindows::IsWindowsThemingSupported.md)|\(Reemplaza `CMFCVisualManager::IsWindowsThemingSupported`.\)|  
|[CMFCVisualManagerWindows::IsWinXPThemeAvailable](../Topic/CMFCVisualManagerWindows::IsWinXPThemeAvailable.md)|Indica si un tema de Windows está disponible.  Un tema puede ser un tema de Windows XP o un tema de [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] .|  
|[CMFCVisualManagerWindows::OnDrawBarGripper](../Topic/CMFCVisualManagerWindows::OnDrawBarGripper.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawBarGripper`.\)|  
|[CMFCVisualManagerWindows::OnDrawBrowseButton](../Topic/CMFCVisualManagerWindows::OnDrawBrowseButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`.\)|  
|[CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawButtonSeparator](../Topic/CMFCVisualManagerWindows::OnDrawButtonSeparator.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawButtonSeparator`.\)|  
|[CMFCVisualManagerWindows::OnDrawCaptionButton](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`.\)|  
|[CMFCVisualManagerWindows::OnDrawCaptionButtonIcon](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButtonIcon.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawCaptionButtonIcon`.\)|  
|[CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md)|\(Reemplaza [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md).\)|  
|[CMFCVisualManagerWindows::OnDrawComboBorder](../Topic/CMFCVisualManagerWindows::OnDrawComboBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawComboBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`.\)|  
|[CMFCVisualManagerWindows::OnDrawControlBorder](../Topic/CMFCVisualManagerWindows::OnDrawControlBorder.md)|\(Reemplaza [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md).\)|  
|[CMFCVisualManagerWindows::OnDrawEditBorder](../Topic/CMFCVisualManagerWindows::OnDrawEditBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawEditBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawExpandingBox](../Topic/CMFCVisualManagerWindows::OnDrawExpandingBox.md)|\(Reemplaza [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md).\)|  
|[CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder](../Topic/CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawFloatingToolbarBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md).\)|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow.md)|El marco de trabajo llama a esta función cuando se dibuja la flecha de ordenación de un control de encabezado.  \(Reemplaza [CMFCVisualManager::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManager::OnDrawHeaderCtrlSortArrow.md).\)|  
|[CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawMenuSystemButton](../Topic/CMFCVisualManagerWindows::OnDrawMenuSystemButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawMenuSystemButton`.\)|  
|[CMFCVisualManagerWindows::OnDrawMiniFrameBorder](../Topic/CMFCVisualManagerWindows::OnDrawMiniFrameBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawMiniFrameBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la página de Outlook.  \(Reemplaza [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md).\)|  
|[CMFCVisualManagerWindows::OnDrawPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawPaneBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawPaneCaption](../Topic/CMFCVisualManagerWindows::OnDrawPaneCaption.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`.\)|  
|[CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawScrollButtons](../Topic/CMFCVisualManagerWindows::OnDrawScrollButtons.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`.\)|  
|[CMFCVisualManagerWindows::OnDrawSeparator](../Topic/CMFCVisualManagerWindows::OnDrawSeparator.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawSeparator`.\)|  
|[CMFCVisualManagerWindows::OnDrawSpinButtons](../Topic/CMFCVisualManagerWindows::OnDrawSpinButtons.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawSpinButtons`.\)|  
|[CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarProgress.md)|El marco de trabajo llama a este método cuando dibuja el indicador de progreso en el objeto de [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) .  \(Reemplaza [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md).\)|  
|[CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md)|El marco de trabajo llama a este método cuando dibuja el control de tamaño para [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md).\)|  
|[CMFCVisualManagerWindows::OnDrawTab](../Topic/CMFCVisualManagerWindows::OnDrawTab.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTab`.\)|  
|[CMFCVisualManagerWindows::OnDrawTabCloseButton](../Topic/CMFCVisualManagerWindows::OnDrawTabCloseButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTabCloseButton`.\)|  
|[CMFCVisualManagerWindows::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawTabsButtonBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawTask](../Topic/CMFCVisualManagerWindows::OnDrawTask.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTask`.\)|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`.\)|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupCaption.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`.\)|  
|[CMFCVisualManagerWindows::OnDrawTearOffCaption](../Topic/CMFCVisualManagerWindows::OnDrawTearOffCaption.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`.\)|  
|[CMFCVisualManagerWindows::OnErasePopupWindowButton](../Topic/CMFCVisualManagerWindows::OnErasePopupWindowButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`.\)|  
|[CMFCVisualManagerWindows::OnEraseTabsArea](../Topic/CMFCVisualManagerWindows::OnEraseTabsArea.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnEraseTabsArea`.\)|  
|[CMFCVisualManagerWindows::OnEraseTabsButton](../Topic/CMFCVisualManagerWindows::OnEraseTabsButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnEraseTabsButton`.\)|  
|[CMFCVisualManagerWindows::OnEraseTabsFrame](../Topic/CMFCVisualManagerWindows::OnEraseTabsFrame.md)|El marco de trabajo llama a este método cuando borra un cuadro en [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md).  \(Reemplaza [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md).\)|  
|[CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillBarBackground`.\)|  
|[CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillButtonInterior`.\)|  
|[CMFCVisualManagerWindows::OnFillCommandsListBackground](../Topic/CMFCVisualManagerWindows::OnFillCommandsListBackground.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`.\)|  
|[CMFCVisualManagerWindows::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerWindows::OnFillMiniFrameCaption.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`.\)|  
|[CMFCVisualManagerWindows::OnFillOutlookPageButton](../Topic/CMFCVisualManagerWindows::OnFillOutlookPageButton.md)|El marco de trabajo llama a este método cuando rellena el interior de un botón de la página de Outlook.  \(Reemplaza [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md).\)|  
|[CMFCVisualManagerWindows::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerWindows::OnFillTasksGroupInterior.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`.\)|  
|[CMFCVisualManagerWindows::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerWindows::OnFillTasksPaneBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un control de [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) .  \(Reemplaza [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md).\)|  
|[CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnHighlightMenuItem`.\)|  
|[CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`.\)|  
|[CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`.\)|  
|[CMFCVisualManagerWindows::SetOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::SetOfficeStyleMenus.md)||  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCVisualManagerWindows::m\_b3DTabsXPTheme](../Topic/CMFCVisualManagerWindows::m_b3DTabsXPTheme.md)|Especifica si el tema de Windows XP muestra las pestañas 3D.|  
  
## Comentarios  
 Utilice la clase de `CMFCVisualManagerWindows` para cambiar la apariencia de la aplicación para imitar Windows XP o el tema actual de [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] en el equipo donde se ejecuta la aplicación.  
  
 Sin embargo, un tema de Windows podría no estar disponible si la aplicación se está ejecutando en una versión de Windows anterior a Windows XP o si están deshabilitados los temas porque el usuario está utilizando la vista de **Clásica** .  Si no hay ningún tema disponible, la aplicación utiliza el administrador visual predeterminada definida en [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo utilizar `CMFCVisualManagerWindows`.  Este fragmento de código es parte de [Ejemplo de demostración de alerta de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#10](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagerwindows-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
## Requisitos  
 **encabezado:** afxvisualmanagerwindows.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)