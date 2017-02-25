---
title: "CMFCVisualManagerOffice2003 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerOffice2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerOffice2003 class"
ms.assetid: 115482cd-e349-450a-8dc4-c6023d092aab
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCVisualManagerOffice2003 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerOffice2003` da a la aplicación un aspecto de Microsoft Office 2003.  
  
## Sintaxis  
  
```  
class CMFCVisualManagerOffice2003 : public CMFCVisualManagerOfficeXP  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCVisualManagerOffice2003::DrawComboBorderWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboBorderWinXP.md)|Dibuja el borde del cuadro combinado con el tema actual de Windows XP.  \(Reemplaza [CMFCVisualManager::DrawComboBorderWinXP](../Topic/CMFCVisualManager::DrawComboBorderWinXP.md).\)|  
|[CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP.md)|Dibuja un botón desplegable de cuadro combinado con el tema actual de Windows XP.  \(Reemplaza [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md).\)|  
|[CMFCVisualManagerOffice2003::DrawCustomizeButton](../Topic/CMFCVisualManagerOffice2003::DrawCustomizeButton.md)|Dibuja un botón de personalizar.|  
|[CMFCVisualManagerOffice2003::DrawPushButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawPushButtonWinXP.md)|Dibuja un botón de comando con el tema actual de Windows XP.  \(Reemplaza [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md).\)|  
|[CMFCVisualManagerOffice2003::GetBaseThemeColor](../Topic/CMFCVisualManagerOffice2003::GetBaseThemeColor.md)|Obtiene el tema base color.|  
|[CMFCVisualManagerOffice2003::GetHighlightMenuItemColor](../Topic/CMFCVisualManagerOffice2003::GetHighlightMenuItemColor.md)|Obtiene el color utilizado para el elemento de menú resaltado.|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md)|El marco de trabajo llama a este método para obtener el color de fondo de una lista de propiedades.  \(Reemplaza `CMFCVisualManagerOfficeXP::GetPropertyGridGroupColor`.\)|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor.md)|El marco de trabajo llama a este método para recuperar el color del texto de una lista de propiedades.  \(Reemplaza `CMFCVisualManagerOfficeXP::GetPropertyGridGroupTextColor`.\)|  
|[CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight.md)|Devuelve el mayor de todos los elementos de menú.  \(Reemplaza [CMFCVisualManager::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManager::GetShowAllMenuItemsHeight.md).\)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors.md)|Establece el color de fondo especificado y el color del borde del grupo base.  \(Reemplaza `CMFCVisualManagerOfficeXP::GetSmartDockingBaseGuideColors`.\)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor.md)|Obtiene el tono color de resaltado.  \(Reemplaza [CMFCVisualManager::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManager::GetSmartDockingHighlightToneColor.md).\)|  
|[CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md)|El marco de trabajo llama a esta función cuando tiene que recuperar el conjunto de colores para dibujar una ventana de la pestaña.  \(Reemplaza [CMFCVisualManager::GetTabFrameColors](../Topic/CMFCVisualManager::GetTabFrameColors.md).\)|  
|[CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin](../Topic/CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin.md)|Obtiene el margen de la barra de herramientas personalizan el botón.  \(Reemplaza `CMFCVisualManager::GetToolBarCustomizeButtonMargin`.\)|  
|[CMFCVisualManagerOffice2003::GetToolbarDisabledColor](../Topic/CMFCVisualManagerOffice2003::GetToolbarDisabledColor.md)|Obtiene el color deshabilitado para la barra de herramientas.  \(Reemplaza `CMFCVisualManager::GetToolbarDisabledColor`.\)|  
|[CMFCVisualManagerOffice2003::GetToolTipInfo](../Topic/CMFCVisualManagerOffice2003::GetToolTipInfo.md)|Llamado por el marco para obtener información sobre herramientas.  \(Reemplaza [CMFCVisualManager::GetToolTipInfo](../Topic/CMFCVisualManager::GetToolTipInfo.md).\)|  
|[CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled](../Topic/CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled.md)|Indica si el administrador visual utiliza colores del tema de Windows XP nativo.|  
|[CMFCVisualManagerOffice2003::IsDockingTabHasBorder](../Topic/CMFCVisualManagerOffice2003::IsDockingTabHasBorder.md)|Devuelve si el administrador visual actual dibuja los bordes alrededor de los paneles que se acoplan y con fichas.  \(Reemplaza [CMFCVisualManager::IsDockingTabHasBorder](../Topic/CMFCVisualManager::IsDockingTabHasBorder.md).\)|  
|[CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs](../Topic/CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs.md)|Indica si las fichas de OneNote deben aparecer resaltadas.  \(Reemplaza `CMFCVisualManager::IsHighlightOneNoteTabs`.\)|  
|[CMFCVisualManagerOffice2003::IsOffsetPressedButton](../Topic/CMFCVisualManagerOffice2003::IsOffsetPressedButton.md)|Llamado por el marco al dibujar un botón de la barra de herramientas.  \(Reemplaza `CMFCVisualManager::IsOffsetPressedButton`.\)|  
|[CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook.md)|Indica si existe una barra de estado con Office XP aspecto.|  
|[CMFCVisualManagerOffice2003::IsToolbarRoundShape](../Topic/CMFCVisualManagerOffice2003::IsToolbarRoundShape.md)|Indica si una barra de herramientas especificada tiene una forma redonda.  \(Reemplaza [CMFCVisualManager::IsToolbarRoundShape](../Topic/CMFCVisualManager::IsToolbarRoundShape.md).\)|  
|[CMFCVisualManagerOffice2003::IsUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::IsUseGlobalTheme.md)|Indica si un tema global de Windows XP se utilizan.|  
|[CMFCVisualManagerOffice2003::IsWindowsThemingSupported](../Topic/CMFCVisualManagerOffice2003::IsWindowsThemingSupported.md)|Indica si Windows theming es.  \(Reemplaza [CMFCVisualManager::IsWindowsThemingSupported](../Topic/CMFCVisualManager::IsWindowsThemingSupported.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultar automáticamente.  \(Reemplaza [CMFCVisualManager::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManager::OnDrawAutoHideButtonBorder.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawBarGripper](../Topic/CMFCVisualManagerOffice2003::OnDrawBarGripper.md)|Llamado por el marco cuando dibuja el agarrador a una barra de controles.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawBarGripper`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawBrowseButton](../Topic/CMFCVisualManagerOffice2003::OnDrawBrowseButton.md)|El marco de trabajo llama a este método cuando dibuja el botón examinar para un control de edición.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawButtonBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de la barra de herramientas.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un objeto de [CMFCCaptionBar \(Clase\)](../../mfc/reference/cmfccaptionbar-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawCaptionBarBorder](../Topic/CMFCVisualManager::OnDrawCaptionBarBorder.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerOffice2003::OnDrawCheckBoxEx.md)|El marco de trabajo llama a este método cuando se dibuja una casilla.  \(Reemplaza [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawComboBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawComboBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde alrededor de un objeto de [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawComboBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawComboDropButton](../Topic/CMFCVisualManagerOffice2003::OnDrawComboDropButton.md)|El marco de trabajo llama a este método cuando dibuja el botón de desplegar de [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawControlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawControlBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un control.  \(Reemplaza [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawExpandingBox](../Topic/CMFCVisualManagerOffice2003::OnDrawExpandingBox.md)|El marco de trabajo llama a este método cuando dibuja un cuadro que expanda.  \(Reemplaza [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawMenuBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawMenuBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter.md)|El marco de trabajo llama a este método cuando dibuja el divisor para una barra de Outlook.  \(Reemplaza [CMFCVisualManager::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManager::OnDrawOutlookBarSplitter.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la página de Outlook.  \(Reemplaza [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un objeto de [CPane Class](../../mfc/reference/cpane-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md)|El marco de trabajo llama a este método cuando dibuja una leyenda para un objeto de [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de una ventana emergente.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPopupWindowBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un botón en una ventana emergente.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption.md)|El marco de trabajo llama a este método cuando dibuja la leyenda de una ventana emergente.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawPopupWindowCaption`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup.md)|El marco de trabajo llama a este método cuando dibuja un grupo de botones en la cinta de opciones.  \(Reemplaza [CMFCVisualManager::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManager::OnDrawRibbonButtonsGroup.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption.md)|El marco de trabajo llama a este método cuando se dibuja la barra de título de una categoría de la cinta de opciones.  \(Reemplaza [CMFCVisualManager::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManager::OnDrawRibbonCategoryCaption.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab.md)|El marco de trabajo llama a este método cuando se dibuja la pestaña para una categoría de la cinta de opciones.  \(Reemplaza [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar.md)|El marco de trabajo llama a este método cuando dibuja [CMFCRibbonProgressBar Class](../../mfc/reference/cmfcribbonprogressbar-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator.md)|El marco de trabajo llama a este método cuando dibuja un separador de la barra de herramientas de acceso rápido de una cinta.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawRibbonQuickAccessToolBarSeparator`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel.md)|El marco de trabajo llama a este método cuando dibuja el canal de [CMFCRibbonSlider Class](../../mfc/reference/cmfcribbonslider-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb.md)|El marco de trabajo llama a este método cuando dibuja al arrastrar un objeto de [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton.md)|El marco de trabajo llama a este método cuando dibuja los botones de zoom para un objeto de [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane.md)|El marco de trabajo llama a este método cuando dibuja un panel en la barra de estado.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawRibbonStatusBarPane`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawScrollButtons](../Topic/CMFCVisualManagerOffice2003::OnDrawScrollButtons.md)|El marco de trabajo llama a este método cuando dibuja los botones de navegación.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md)|El marco de trabajo llama a este método cuando dibuja un separador.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawSeparator`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems](../Topic/CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems.md)|El marco de trabajo llama a este método cuando dibuja todos los elementos de un menú.  \(Reemplaza [CMFCVisualManager::OnDrawShowAllMenuItems](../Topic/CMFCVisualManager::OnDrawShowAllMenuItems.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un objeto de [CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarProgress.md)|El marco de trabajo llama a este método cuando dibuja el indicador de progreso en el objeto de [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox.md)|El marco de trabajo llama a este método cuando dibuja el control de tamaño para [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md).  \(Reemplaza [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md).\)|  
|[CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md)|El marco de trabajo llama a este método cuando dibuja las pestañas para un objeto de [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTab`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder.md)|El marco de trabajo llama a este método cuando dibuja el borde de un botón de la ficha.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawTask](../Topic/CMFCVisualManagerOffice2003::OnDrawTask.md)|El marco de trabajo llama a este método cuando se dibuja un objeto de [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTask`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder.md)|El marco de trabajo llama a este método cuando dibuja un borde alrededor de un grupo en un objeto de [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption.md)|El marco de trabajo llama a este método cuando dibuja la leyenda de un objeto de [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`.\)|  
|[CMFCVisualManagerOffice2003::OnDrawTearOffCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTearOffCaption.md)|El marco de trabajo llama a este método cuando dibuja la leyenda de un objeto de [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`.\)|  
|[CMFCVisualManagerOffice2003::OnErasePopupWindowButton](../Topic/CMFCVisualManagerOffice2003::OnErasePopupWindowButton.md)|El marco de trabajo llama a este método cuando borra un botón en una ventana emergente.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`.\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md)|El marco de trabajo llama a este método cuando borra el área de la ficha de una ventana de la pestaña.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnEraseTabsArea`.\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsButton](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsButton.md)|El marco de trabajo llama a este método cuando borra el texto y el icono de un botón de la ficha.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnEraseTabsButton`.\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsFrame](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsFrame.md)|El marco de trabajo llama a este método cuando borra un cuadro en [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md).  \(Reemplaza [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md).\)|  
|[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultar automáticamente.  \(Reemplaza [CMFCVisualManager::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManager::OnFillAutoHideButtonBackground.md).\)|  
|[CMFCVisualManagerOffice2003::OnFillBarBackground](../Topic/CMFCVisualManagerOffice2003::OnFillBarBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un objeto de [CBasePane Class](../../mfc/reference/cbasepane-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillBarBackground`.\)|  
|[CMFCVisualManagerOffice2003::OnFillButtonInterior](../Topic/CMFCVisualManagerOffice2003::OnFillButtonInterior.md)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de la barra de herramientas.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillButtonInterior`.\)|  
|[CMFCVisualManagerOffice2003::OnFillCommandsListBackground](../Topic/CMFCVisualManagerOffice2003::OnFillCommandsListBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un botón de la barra de herramientas que pertenece a una lista de comandos.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`.\)|  
|[CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un control de encabezado.  \(Reemplaza [CMFCVisualManager::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManager::OnFillHeaderCtrlBackground.md).\)|  
|[CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md)|El marco de trabajo llama a este método cuando rellena el área resaltada de un botón de la barra de herramientas.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillHighlightedArea`.\)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookBarCaption](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookBarCaption.md)|El marco de trabajo llama a este método cuando rellena el fondo de una barra de título de Outlook.  \(Reemplaza [CMFCVisualManager::OnFillOutlookBarCaption](../Topic/CMFCVisualManager::OnFillOutlookBarCaption.md).\)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookPageButton](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookPageButton.md)|El marco de trabajo llama a este método cuando rellena el interior de un botón de la página de Outlook.  \(Reemplaza [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md).\)|  
|[CMFCVisualManagerOffice2003::OnFillPopupWindowBackground](../Topic/CMFCVisualManagerOffice2003::OnFillPopupWindowBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de una ventana emergente.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillPopupWindowBackground`.\)|  
|[CMFCVisualManagerOffice2003::OnFillTab](../Topic/CMFCVisualManagerOffice2003::OnFillTab.md)|El marco de trabajo llama a este método cuando rellena el fondo de una ventana de la pestaña.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillTab`.\)|  
|[CMFCVisualManagerOffice2003::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerOffice2003::OnFillTasksGroupInterior.md)|El marco de trabajo llama a este método cuando rellena el interior de un objeto de [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md).  \(Reemplaza `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`.\)|  
|[CMFCVisualManagerOffice2003::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerOffice2003::OnFillTasksPaneBackground.md)|El marco de trabajo llama a este método cuando rellena el fondo de un control de [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md).  \(Reemplaza [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md).\)|  
|[CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton](../Topic/CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton.md)|El marco de trabajo llama a este método cuando dibuja un resaltado rápido\- personaliza el botón de menú.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnHighlightQuickCustomizeMenuButton`.\)|  
|[CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems.md)|El marco de trabajo llama a este método cuando dibuja un comando de menú resaltado.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`.\)|  
|[CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md)|El marco de trabajo llama a esta función cuando cambian los colores del sistema.  \(Reemplaza `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`.\)|  
|[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](../Topic/CMFCVisualManagerOffice2003::SetDefaultWinXPColors.md)|Especifica si el administrador visual debe utilizar los colores de tema de Windows XP nativo o los colores obtenidos de [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371).|  
|[CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook.md)|Especifica que el tema global de Windows XP se debe utilizar.|  
|[CMFCVisualManagerOffice2003::SetUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::SetUseGlobalTheme.md)|Especifica si el administrador visual utiliza un tema global.|  
  
## Comentarios  
 Utiliza la clase de `CMFCVisualManagerOffice2003` para cambiar la apariencia visual de la aplicación para ser similar a Microsoft Office 2003.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo configurar el administrador de la representación visual de la oficina 2003.  Este fragmento de código es parte de [Ejemplo alerta demo de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#6](../../mfc/reference/codesnippet/CPP/cmfcvisualmanageroffice2003-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
## Requisitos  
 **Encabezado:** afxvisualmanageroffice2003.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)