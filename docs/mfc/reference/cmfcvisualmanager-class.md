---
title: "CMFCVisualManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManager class"
ms.assetid: beed80f7-36a2-4d64-9f09-e807cfefc3fe
caps.latest.revision: 58
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 60
---
# CMFCVisualManager Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona compatibilidad para cambiar la apariencia de la aplicación en un nivel global.  La clase de `CMFCVisualManager` funciona junto con una clase que proporcione instrucciones de dibujar controles de GUI de aplicaciones utilizando un estilo coherente.  Se conocen estas otras clases como visual los administradores y heredan de `CMFCBaseVisualManager`.  
  
## Sintaxis  
  
```  
class CMFCVisualManager : public CMFCBaseVisualManager  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCVisualManager::CMFCVisualManager`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCVisualManager::AdjustFrames](../Topic/CMFCVisualManager::AdjustFrames.md)||  
|[CMFCVisualManager::AdjustToolbars](../Topic/CMFCVisualManager::AdjustToolbars.md)||  
|[CMFCVisualManager::AlwaysHighlight3DTabs](../Topic/CMFCVisualManager::AlwaysHighlight3DTabs.md)|Llamado por el marco para determinar si las fichas 3D se deben dibujar siempre mediante un resaltado color.|  
|[CMFCVisualManager::DestroyInstance](../Topic/CMFCVisualManager::DestroyInstance.md)||  
|[CMFCVisualManager::DoDrawHeaderSortArrow](../Topic/CMFCVisualManager::DoDrawHeaderSortArrow.md)||  
|[CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md)||  
|[CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md)||  
|[CMFCVisualManager::DrawTextOnGlass](../Topic/CMFCVisualManager::DrawTextOnGlass.md)||  
|[CMFCVisualManager::GetAutoHideButtonTextColor](../Topic/CMFCVisualManager::GetAutoHideButtonTextColor.md)|Llamado por el marco para recuperar el color del texto para un botón de ocultar automáticamente.|  
|[CMFCVisualManager::GetButtonExtraBorder](../Topic/CMFCVisualManager::GetButtonExtraBorder.md)|Llamado por el marco para recuperar el mayor tamaño del botón que el administrador visual actual requiere para dibujar un botón.|  
|[CMFCVisualManager::GetCaptionBarTextColor](../Topic/CMFCVisualManager::GetCaptionBarTextColor.md)|Llamado por el marco para recuperar el color del texto de una barra de título.|  
|[CMFCVisualManager::GetDockingTabsBordersSize](../Topic/CMFCVisualManager::GetDockingTabsBordersSize.md)|Llamado por el marco para recuperar el tamaño del borde de una barra con fichas acoplada.|  
|[CMFCVisualManager::GetHighlightedMenuItemTextColor](../Topic/CMFCVisualManager::GetHighlightedMenuItemTextColor.md)||  
|[CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)|Devuelve un puntero al objeto de `CMFCVisualManager` .|  
|[CMFCVisualManager::GetMDITabsBordersSize](../Topic/CMFCVisualManager::GetMDITabsBordersSize.md)|Llamado por el marco para recuperar el tamaño del borde de la ventana de MDITabs.|  
|[CMFCVisualManager::GetMenuItemTextColor](../Topic/CMFCVisualManager::GetMenuItemTextColor.md)||  
|[CMFCVisualManager::GetMenuShadowDepth](../Topic/CMFCVisualManager::GetMenuShadowDepth.md)|Devuelve un valor que determina el ancho y el alto de una sombra del menú.|  
|[CMFCVisualManager::GetNcBtnSize](../Topic/CMFCVisualManager::GetNcBtnSize.md)|Llamado por el marco para determinar el tamaño de los botones del sistema según el administrador visual actual.  Los botones del sistema son los botones en la leyenda del marco principal que se asignan a los comandos **Cerrar**, **Minimizar**, **Maximizar**, y **Restaurar**.|  
|[CMFCVisualManager::GetPopupMenuBorderSize](../Topic/CMFCVisualManager::GetPopupMenuBorderSize.md)|Llamado por el marco para recuperar el tamaño del borde de un menú emergente.|  
|[CMFCVisualManager::GetPropertyGridGroupColor](../Topic/CMFCVisualManager::GetPropertyGridGroupColor.md)|Llamado por el marco para recuperar el color de fondo de una lista de propiedades.|  
|[CMFCVisualManager::GetPropertyGridGroupTextColor](../Topic/CMFCVisualManager::GetPropertyGridGroupTextColor.md)|Llamado por el marco para recuperar el color del texto de una lista de propiedades.|  
|[CMFCVisualManager::GetRibbonHyperlinkTextColor](../Topic/CMFCVisualManager::GetRibbonHyperlinkTextColor.md)||  
|[CMFCVisualManager::GetRibbonPopupBorderSize](../Topic/CMFCVisualManager::GetRibbonPopupBorderSize.md)||  
|[CMFCVisualManager::GetRibbonQuickAccessToolBarTextColor](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarTextColor.md)||  
|[CMFCVisualManager::GetRibbonSliderColors](../Topic/CMFCVisualManager::GetRibbonSliderColors.md)||  
|[CMFCVisualManager::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManager::GetShowAllMenuItemsHeight.md)||  
|[CMFCVisualManager::GetSmartDockingBaseGuideColors](../Topic/CMFCVisualManager::GetSmartDockingBaseGuideColors.md)||  
|[CMFCVisualManager::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManager::GetSmartDockingHighlightToneColor.md)||  
|[CMFCVisualManager::GetSmartDockingTheme](../Topic/CMFCVisualManager::GetSmartDockingTheme.md)|Devuelve un tema utilizado para mostrar marcadores inteligentes de acoplamiento.|  
|[CMFCVisualManager::GetStatusBarPaneTextColor](../Topic/CMFCVisualManager::GetStatusBarPaneTextColor.md)||  
|[CMFCVisualManager::GetTabFrameColors](../Topic/CMFCVisualManager::GetTabFrameColors.md)|Llamado por el marco para recuperar el conjunto de colores para utilizar cuando dibuja un cuadro de la pestaña.|  
|[CMFCVisualManager::GetTabTextColor](../Topic/CMFCVisualManager::GetTabTextColor.md)||  
|[CMFCVisualManager::GetToolbarButtonTextColor](../Topic/CMFCVisualManager::GetToolbarButtonTextColor.md)|Llamado por el marco para recuperar el color actual del texto del botón de la barra de herramientas.  Este color varía según el administrador visual actual y el estado del botón.|  
|[CMFCVisualManager::GetToolbarDisabledTextColor](../Topic/CMFCVisualManager::GetToolbarDisabledTextColor.md)|Llamado por el marco para determinar el color del texto que se muestra en elementos deshabilitados de la barra de herramientas.|  
|[CMFCVisualManager::GetToolbarHighlightColor](../Topic/CMFCVisualManager::GetToolbarHighlightColor.md)||  
|[CMFCVisualManager::GetToolTipInfo](../Topic/CMFCVisualManager::GetToolTipInfo.md)||  
|[CMFCVisualManager::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManager::HasOverlappedAutoHideButtons.md)|Especifica si ocultar automáticamente la superposición de los botones.|  
|[CMFCVisualManager::IsDockingTabHasBorder](../Topic/CMFCVisualManager::IsDockingTabHasBorder.md)|Especifica si el administrador visual actual dibuja un borde alrededor de las barras de acoplamiento con fichas.|  
|[CMFCVisualManager::IsEmbossDisabledImage](../Topic/CMFCVisualManager::IsEmbossDisabledImage.md)|Especifica si las imágenes deshabilitadas deben ser grabada en relieves.|  
|[CMFCVisualManager::IsFadeInactiveImage](../Topic/CMFCVisualManager::IsFadeInactiveImage.md)|Llamado por el marco para determinar si las imágenes inactivas en una barra de herramientas o un menú aparecen en gris.|  
|[CMFCVisualManager::IsMenuFlatLook](../Topic/CMFCVisualManager::IsMenuFlatLook.md)|Especifica si los botones de menú tienen un aspecto quitar información de estructura jerárquica.|  
|[CMFCVisualManager::IsOfficeXPStyleMenus](../Topic/CMFCVisualManager::IsOfficeXPStyleMenus.md)|Especifica si el administrador visual implementa menús de XP\-estilo de Office.|  
|[CMFCVisualManager::IsOwnerDrawCaption](../Topic/CMFCVisualManager::IsOwnerDrawCaption.md)|Especifica si el administrador visual actual implementa leyendas propietario\-drenados de una ventana de marco.|  
|[CMFCVisualManager::IsShadowHighlightedImage](../Topic/CMFCVisualManager::IsShadowHighlightedImage.md)|Especifica si una imagen resaltado tiene una sombra.|  
|[CMFCVisualManager::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManager::OnDrawAutoHideButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de ocultar automáticamente.|  
|[CMFCVisualManager::OnDrawBarGripper](../Topic/CMFCVisualManager::OnDrawBarGripper.md)|Llamado por el marco cuando dibuja el agarrador de una barra de controles.  el usuario debe hacer clic el agarrador para mover la barra de control.|  
|[CMFCVisualManager::OnDrawBrowseButton](../Topic/CMFCVisualManager::OnDrawBrowseButton.md)|Llamado por el marco cuando dibuja un botón examinar que pertenezca a un control de edición \([CMFCEditBrowseCtrl Class](../../mfc/reference/cmfceditbrowsectrl-class.md)\).|  
|[CMFCVisualManager::OnDrawButtonBorder](../Topic/CMFCVisualManager::OnDrawButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la barra de herramientas.|  
|[CMFCVisualManager::OnDrawButtonSeparator](../Topic/CMFCVisualManager::OnDrawButtonSeparator.md)||  
|[CMFCVisualManager::OnDrawCaptionBarBorder](../Topic/CMFCVisualManager::OnDrawCaptionBarBorder.md)|Llamado por el marco cuando dibuja el borde de la barra de título.|  
|[CMFCVisualManager::OnDrawCaptionBarButtonBorder](../Topic/CMFCVisualManager::OnDrawCaptionBarButtonBorder.md)||  
|[CMFCVisualManager::OnDrawCaptionBarInfoArea](../Topic/CMFCVisualManager::OnDrawCaptionBarInfoArea.md)||  
|[CMFCVisualManager::OnDrawCaptionButton](../Topic/CMFCVisualManager::OnDrawCaptionButton.md)|Llamado por el marco cuando dibuja un botón de título.|  
|[CMFCVisualManager::OnDrawCheckBox](../Topic/CMFCVisualManager::OnDrawCheckBox.md)||  
|[CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md)||  
|[CMFCVisualManager::OnDrawComboBorder](../Topic/CMFCVisualManager::OnDrawComboBorder.md)|Llamado por el marco cuando dibuja el borde de un botón del cuadro combinado.|  
|[CMFCVisualManager::OnDrawComboDropButton](../Topic/CMFCVisualManager::OnDrawComboDropButton.md)|Llamado por el marco cuando dibuja un botón de desplegar el cuadro combinado.|  
|[CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md)||  
|[CMFCVisualManager::OnDrawDefaultRibbonImage](../Topic/CMFCVisualManager::OnDrawDefaultRibbonImage.md)|Llamado por el marco cuando se dibuja la imagen predeterminada de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawEditBorder](../Topic/CMFCVisualManager::OnDrawEditBorder.md)|Llamado por el marco cuando dibuja un borde alrededor de un objeto de [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) .|  
|[CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md)||  
|[CMFCVisualManager::OnDrawFloatingToolbarBorder](../Topic/CMFCVisualManager::OnDrawFloatingToolbarBorder.md)|Llamado por el marco cuando dibuja los bordes de una barra de herramientas flotante.  La barra de herramientas flotante es una barra de herramientas que aparece como una ventana de marco recudido.|  
|[CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md)|Llamado por el marco cuando dibuja el borde que contiene el control de encabezado.|  
|[CMFCVisualManager::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManager::OnDrawHeaderCtrlSortArrow.md)|Llamado por el marco cuando dibuja el control de encabezado ordenar la flecha.|  
|[CMFCVisualManager::OnDrawMenuArrowOnCustomizeList](../Topic/CMFCVisualManager::OnDrawMenuArrowOnCustomizeList.md)||  
|[CMFCVisualManager::OnDrawMenuBorder](../Topic/CMFCVisualManager::OnDrawMenuBorder.md)|Llamado por el marco cuando dibuja un borde del menú.|  
|[CMFCVisualManager::OnDrawMenuCheck](../Topic/CMFCVisualManager::OnDrawMenuCheck.md)||  
|[CMFCVisualManager::OnDrawMenuItemButton](../Topic/CMFCVisualManager::OnDrawMenuItemButton.md)||  
|[CMFCVisualManager::OnDrawMenuLabel](../Topic/CMFCVisualManager::OnDrawMenuLabel.md)||  
|[CMFCVisualManager::OnDrawMenuResizeBar](../Topic/CMFCVisualManager::OnDrawMenuResizeBar.md)||  
|[CMFCVisualManager::OnDrawMenuScrollButton](../Topic/CMFCVisualManager::OnDrawMenuScrollButton.md)|Llamado por el marco cuando dibuja un botón de navegación del menú.|  
|[CMFCVisualManager::OnDrawMenuShadow](../Topic/CMFCVisualManager::OnDrawMenuShadow.md)||  
|[CMFCVisualManager::OnDrawMenuSystemButton](../Topic/CMFCVisualManager::OnDrawMenuSystemButton.md)|Llamado por el marco cuando dibuja los botones **Cerrar**, **Minimizar**, **Maximizar**, y **Restaurar**de sistema de menú.|  
|[CMFCVisualManager::OnDrawMiniFrameBorder](../Topic/CMFCVisualManager::OnDrawMiniFrameBorder.md)||  
|[CMFCVisualManager::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManager::OnDrawOutlookBarSplitter.md)|Llamado por el marco cuando dibuja el divisor para una barra de Outlook.  El divisor es una barra horizontal utilizada para los controles de grupo.|  
|[CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la página de Outlook.  Los botones de la página de Outlook aparecen si el panel de barra de Outlook contiene varios botones que se pueden mostrar.|  
|[CMFCVisualManager::OnDrawPaneBorder](../Topic/CMFCVisualManager::OnDrawPaneBorder.md)|Llamado por el marco cuando dibuja el borde de [CPane Class](../../mfc/reference/cpane-class.md).|  
|[CMFCVisualManager::OnDrawPaneCaption](../Topic/CMFCVisualManager::OnDrawPaneCaption.md)|Llamado por el marco cuando dibuja la leyenda de `CPane`.|  
|[CMFCVisualManager::OnDrawPaneDivider](../Topic/CMFCVisualManager::OnDrawPaneDivider.md)||  
|[CMFCVisualManager::OnDrawPopupWindowBorder](../Topic/CMFCVisualManager::OnDrawPopupWindowBorder.md)||  
|[CMFCVisualManager::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManager::OnDrawPopupWindowButtonBorder.md)||  
|[CMFCVisualManager::OnDrawPopupWindowCaption](../Topic/CMFCVisualManager::OnDrawPopupWindowCaption.md)||  
|[CMFCVisualManager::OnDrawRibbonApplicationButton](../Topic/CMFCVisualManager::OnDrawRibbonApplicationButton.md)|Llamado por el marco cuando dibuja **botón principal** en la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonButtonBorder](../Topic/CMFCVisualManager::OnDrawRibbonButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManager::OnDrawRibbonButtonsGroup.md)|Llamado por el marco cuando dibuja un grupo de botones en la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCaption](../Topic/CMFCVisualManager::OnDrawRibbonCaption.md)|Llamado por el marco cuando dibuja la leyenda del marco principal, pero solo si la barra de la cinta de opciones se integra con el cuadro.|  
|[CMFCVisualManager::OnDrawRibbonCaptionButton](../Topic/CMFCVisualManager::OnDrawRibbonCaptionButton.md)|Llamado por el marco cuando dibuja un botón de título situado en la barra de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCategory](../Topic/CMFCVisualManager::OnDrawRibbonCategory.md)|Llamado por el marco cuando dibuja una categoría de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManager::OnDrawRibbonCategoryCaption.md)|Llamado por el marco cuando dibuja la leyenda de una categoría de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCategoryScroll](../Topic/CMFCVisualManager::OnDrawRibbonCategoryScroll.md)||  
|[CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md)|Llamado por el marco cuando se dibuja la pestaña para una categoría de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCheckBoxOnList](../Topic/CMFCVisualManager::OnDrawRibbonCheckBoxOnList.md)||  
|[CMFCVisualManager::OnDrawRibbonColorPaletteBox](../Topic/CMFCVisualManager::OnDrawRibbonColorPaletteBox.md)||  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButtonContext](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButtonContext.md)||  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButton.md)|Llamado por el marco cuando dibuja el botón predeterminado del panel de la cinta de opciones.  El botón predeterminado aparece cuando el usuario reduce un panel ribbon para demasiado pequeño mostrar los elementos de la cinta de opciones.  El botón predeterminado se dibuja en su lugar y los elementos de la cinta de opciones se agregan como elementos de un menú desplegable.|  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButtonIndicator](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButtonIndicator.md)||  
|[CMFCVisualManager::OnDrawRibbonGalleryBorder](../Topic/CMFCVisualManager::OnDrawRibbonGalleryBorder.md)||  
|[CMFCVisualManager::OnDrawRibbonGalleryButton](../Topic/CMFCVisualManager::OnDrawRibbonGalleryButton.md)||  
|[CMFCVisualManager::OnDrawRibbonKeyTip](../Topic/CMFCVisualManager::OnDrawRibbonKeyTip.md)||  
|[CMFCVisualManager::OnDrawRibbonLabel](../Topic/CMFCVisualManager::OnDrawRibbonLabel.md)|Llamado por el marco cuando se dibuja la etiqueta de cinta.|  
|[CMFCVisualManager::OnDrawRibbonMainPanelButtonBorder](../Topic/CMFCVisualManager::OnDrawRibbonMainPanelButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la cinta que se coloca en el panel de **Principal** .  el panel de **Principal** es el panel que aparece cuando un usuario hace clic **botón principal**.|  
|[CMFCVisualManager::OnDrawRibbonMainPanelFrame](../Topic/CMFCVisualManager::OnDrawRibbonMainPanelFrame.md)|Llamado por el marco cuando dibuja el cuadro alrededor del panel de **Principal** .|  
|[CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../Topic/CMFCVisualManager::OnDrawRibbonMenuCheckFrame.md)||  
|[CMFCVisualManager::OnDrawRibbonPanel](../Topic/CMFCVisualManager::OnDrawRibbonPanel.md)|Llamado por el marco cuando dibuja un panel de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonPanelCaption](../Topic/CMFCVisualManager::OnDrawRibbonPanelCaption.md)|Llamado por el marco cuando dibuja la leyenda de un panel de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md)|Llamado por el marco cuando se dibuja un objeto de [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) .|  
|[CMFCVisualManager::OnDrawRibbonQuickAccessToolBarSeparator](../Topic/CMFCVisualManager::OnDrawRibbonQuickAccessToolBarSeparator.md)|Llamado por el marco cuando dibuja un separador en **barra de herramientas de acceso rápido**de una cinta.|  
|[CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../Topic/CMFCVisualManager::OnDrawRibbonRecentFilesFrame.md)|Llamado por el marco cuando dibuja un cuadro alrededor de una lista de archivos recientes.|  
|[CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md)|Llamado por el marco cuando dibuja el canal de un objeto de [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) .|  
|[CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md)|Llamado por el marco cuando dibuja al arrastrar un objeto de `CMFCRibbonSlider` .|  
|[CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md)|Llamado por el marco cuando dibuja los botones de zoom de un objeto de `CMFCRibbonSlider` .|  
|[CMFCVisualManager::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManager::OnDrawRibbonStatusBarPane.md)|Llamado por el marco cuando dibuja el panel de barra de estado de una cinta.|  
|[CMFCVisualManager::OnDrawRibbonTabsFrame](../Topic/CMFCVisualManager::OnDrawRibbonTabsFrame.md)|Llamado por el marco cuando dibuja un cuadro alrededor de un conjunto de fichas de cinta.|  
|[CMFCVisualManager::OnDrawScrollButtons](../Topic/CMFCVisualManager::OnDrawScrollButtons.md)||  
|[CMFCVisualManager::OnDrawSeparator](../Topic/CMFCVisualManager::OnDrawSeparator.md)|Llamado por el marco cuando dibuja un separador.  El separador se usa normalmente en una barra de controles para separar grupos de iconos.|  
|[CMFCVisualManager::OnDrawShowAllMenuItems](../Topic/CMFCVisualManager::OnDrawShowAllMenuItems.md)||  
|[CMFCVisualManager::OnDrawSpinButtons](../Topic/CMFCVisualManager::OnDrawSpinButtons.md)|Llamado por el marco cuando dibuja los botones de número.|  
|[CMFCVisualManager::OnDrawSplitterBorder](../Topic/CMFCVisualManager::OnDrawSplitterBorder.md)|Llamado por el marco cuando dibuja el borde de una ventana dividida.|  
|[CMFCVisualManager::OnDrawSplitterBox](../Topic/CMFCVisualManager::OnDrawSplitterBox.md)|Llamado por el marco cuando dibuja el cuadro de arrastre splitter para una ventana dividida.|  
|[CMFCVisualManager::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManager::OnDrawStatusBarPaneBorder.md)|Llamado por el marco cuando dibuja el borde de un panel de barra de estado.|  
|[CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md)|Llamado por el marco cuando dibuja el indicador de progreso de la barra de estado.|  
|[CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md)|Llamado por el marco cuando dibuja el control del tamaño de la barra de estado.|  
|[CMFCVisualManager::OnDrawTab](../Topic/CMFCVisualManager::OnDrawTab.md)|Llamado por el marco cuando se dibuja un objeto de [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md) .|  
|[CMFCVisualManager::OnDrawTabCloseButton](../Topic/CMFCVisualManager::OnDrawTabCloseButton.md)|Llamado por el marco cuando dibuja el botón de **Cerrar** en la pestaña activa.|  
|[CMFCVisualManager::OnDrawTabContent](../Topic/CMFCVisualManager::OnDrawTabContent.md)|Llamado por el marco cuando dibuja el interior de tabulación \(imágenes, texto\).|  
|[CMFCVisualManager::OnDrawTabsButtonBorder](../Topic/CMFCVisualManager::OnDrawTabsButtonBorder.md)|Llamado por el marco cuando dibuja el borde de un botón de la ficha.|  
|[CMFCVisualManager::OnDrawTask](../Topic/CMFCVisualManager::OnDrawTask.md)|Llamado por el marco cuando dibuja una tarea en el panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManager::OnDrawTasksGroupAreaBorder.md)|Llamado por el marco cuando dibuja un borde alrededor de un área de grupo del panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupCaption](../Topic/CMFCVisualManager::OnDrawTasksGroupCaption.md)|Llamado por el marco cuando dibuja la leyenda de un grupo de tareas en el panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupIcon](../Topic/CMFCVisualManager::OnDrawTasksGroupIcon.md)||  
|[CMFCVisualManager::OnDrawTearOffCaption](../Topic/CMFCVisualManager::OnDrawTearOffCaption.md)|Llamado por el marco cuando dibuja la leyenda del rasgón para una barra de rasgón.|  
|[CMFCVisualManager::OnDrawToolBoxFrame](../Topic/CMFCVisualManager::OnDrawToolBoxFrame.md)||  
|[CMFCVisualManager::OnEraseMDIClientArea](../Topic/CMFCVisualManager::OnEraseMDIClientArea.md)|Llamado por el marco cuando borra el área de cliente MDI.|  
|[CMFCVisualManager::OnErasePopupWindowButton](../Topic/CMFCVisualManager::OnErasePopupWindowButton.md)||  
|[CMFCVisualManager::OnEraseTabsArea](../Topic/CMFCVisualManager::OnEraseTabsArea.md)|Llamado por el marco cuando borra el área de la pestaña en una ventana de la pestaña.|  
|[CMFCVisualManager::OnEraseTabsButton](../Topic/CMFCVisualManager::OnEraseTabsButton.md)|Llamado por el marco cuando borra el icono y el texto de un botón de la ficha.|  
|[CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md)|Llamado por el marco cuando borra un cuadro de la pestaña.|  
|[CMFCVisualManager::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManager::OnFillAutoHideButtonBackground.md)|Llamado por el marco cuando rellena el fondo de un botón de ocultar automáticamente.|  
|[CMFCVisualManager::OnFillBarBackground](../Topic/CMFCVisualManager::OnFillBarBackground.md)|Llamado por el marco cuando rellena el fondo de una barra de controles.|  
|[CMFCVisualManager::OnFillButtonInterior](../Topic/CMFCVisualManager::OnFillButtonInterior.md)|Llamado por el marco cuando rellena el fondo de un botón de la barra de herramientas.|  
|[CMFCVisualManager::OnFillCaptionBarButton](../Topic/CMFCVisualManager::OnFillCaptionBarButton.md)||  
|[CMFCVisualManager::OnFillCommandsListBackground](../Topic/CMFCVisualManager::OnFillCommandsListBackground.md)|Llamado por el marco cuando rellena el fondo de un botón de la barra de herramientas que pertenece a una lista de comando que, a su vez, forma parte de un cuadro de diálogo personalización.|  
|[CMFCVisualManager::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManager::OnFillHeaderCtrlBackground.md)|Llamado por el marco cuando rellena el fondo de un control de encabezado.|  
|[CMFCVisualManager::OnFillMiniFrameCaption](../Topic/CMFCVisualManager::OnFillMiniFrameCaption.md)|Llamado por el marco cuando rellena la leyenda de una mini ventana de marco.|  
|[CMFCVisualManager::OnFillOutlookBarCaption](../Topic/CMFCVisualManager::OnFillOutlookBarCaption.md)|Llamado por el marco cuando rellena el fondo de una leyenda de la barra de Outlook.|  
|[CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md)|Llamado por el marco cuando rellena el interior de un botón de la página de Outlook.|  
|[CMFCVisualManager::OnFillPopupWindowBackground](../Topic/CMFCVisualManager::OnFillPopupWindowBackground.md)|Llamado por el marco cuando rellena el fondo de una ventana emergente.|  
|[CMFCVisualManager::OnFillRibbonButton](../Topic/CMFCVisualManager::OnFillRibbonButton.md)|Llamado por el marco cuando rellena el interior de un botón de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonEdit](../Topic/CMFCVisualManager::OnFillRibbonEdit.md)|Llamado por el marco cuando rellena el interior de un control de edición de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonMainPanelButton](../Topic/CMFCVisualManager::OnFillRibbonMainPanelButton.md)|Llamado por el marco cuando rellena el interior de un botón de la cinta de opciones ubicado en el panel de **Principal** .|  
|[CMFCVisualManager::OnFillRibbonMenuFrame](../Topic/CMFCVisualManager::OnFillRibbonMenuFrame.md)|Llamado por el marco cuando rellena el cuadro del menú del panel principal de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../Topic/CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup.md)||  
|[CMFCVisualManager::OnFillSplitterBackground](../Topic/CMFCVisualManager::OnFillSplitterBackground.md)|Llamado por el marco cuando rellena el fondo de una ventana dividida.|  
|[CMFCVisualManager::OnFillTab](../Topic/CMFCVisualManager::OnFillTab.md)|Llamado por el marco cuando rellena el fondo de una pestaña.|  
|[CMFCVisualManager::OnFillTasksGroupInterior](../Topic/CMFCVisualManager::OnFillTasksGroupInterior.md)|Llamado por el marco cuando rellena el interior de un objeto de [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) en [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md).|  
|[CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md)|Llamado por el marco cuando rellena el fondo de un control de `CMFCTasksPane` .|  
|[CMFCVisualManager::OnHighlightMenuItem](../Topic/CMFCVisualManager::OnHighlightMenuItem.md)|Llamado por el marco cuando dibuja un elemento de menú resaltado.|  
|[CMFCVisualManager::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManager::OnHighlightRarelyUsedMenuItems.md)|Llamado por el marco cuando dibuja un elemento de menú resaltado y raramente utilizado.|  
|[CMFCVisualManager::OnNcPaint](../Topic/CMFCVisualManager::OnNcPaint.md)|Llamado por el marco cuando dibuja el área no cliente.|  
|[CMFCVisualManager::OnSetWindowRegion](../Topic/CMFCVisualManager::OnSetWindowRegion.md)|Llamado por el marco cuando establece una región que contiene los cuadros y menús emergentes.|  
|[CMFCVisualManager::OnUpdateSystemColors](../Topic/CMFCVisualManager::OnUpdateSystemColors.md)|Llamado por el marco cuando cambia el valor del color del sistema.|  
|[CMFCVisualManager::RedrawAll](../Topic/CMFCVisualManager::RedrawAll.md)|Dibuja de nuevo todas las barras de controles en la aplicación.|  
|[CMFCVisualManager::RibbonCategoryColorToRGB](../Topic/CMFCVisualManager::RibbonCategoryColorToRGB.md)||  
|[CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)|Establece el administrador visual predeterminado.|  
|[CMFCVisualManager::SetEmbossDisabledImage](../Topic/CMFCVisualManager::SetEmbossDisabledImage.md)|Habilita o deshabilita el modo en relieve para las imágenes deshabilitadas de la barra de herramientas.|  
|[CMFCVisualManager::SetFadeInactiveImage](../Topic/CMFCVisualManager::SetFadeInactiveImage.md)|Habilita o deshabilita el efecto luminoso para las imágenes inactivas en un menú o una barra de herramientas.|  
|[CMFCVisualManager::SetMenuFlatLook](../Topic/CMFCVisualManager::SetMenuFlatLook.md)|Establece una marca que indica si los botones de menú de la aplicación tienen un aspecto quitar información de estructura jerárquica.|  
|[CMFCVisualManager::SetMenuShadowDepth](../Topic/CMFCVisualManager::SetMenuShadowDepth.md)|Establece el ancho y el alto de la sombra del menú.|  
|[CMFCVisualManager::SetShadowHighlightedImage](../Topic/CMFCVisualManager::SetShadowHighlightedImage.md)|Establece una marca que indica si mostrar la sombra al representar imágenes resaltado.|  
  
## Comentarios  
 Dado que la clase de `CMFCVisualManager` controla GUI de aplicación, cada aplicación puede tener una instancia de `CMFCVisualManager`, o una instancia de una clase derivada de `CMFCVisualManager`.  La aplicación también puede funcionar sin `CMFCVisualManager`.  Utilice el método estático `GetInstance` para obtener un puntero a `CMFCVisualManager`actual \(objeto derivado.  
  
 Para cambiar el aspecto de la aplicación debe utilizar otras clases que proporcionan métodos para dibujar todos los elementos visuales de la aplicación.  algunos ejemplos de estas clases son [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md), [CMFCVisualManagerOffice2003 Class](../../mfc/reference/cmfcvisualmanageroffice2003-class.md), y [CMFCVisualManagerOffice2007 Class](../../mfc/reference/cmfcvisualmanageroffice2007-class.md).  Si desea cambiar el aspecto de la aplicación, pase uno de estos administradores visuales en el método `SetDefaultManager`.  Para obtener un ejemplo de cómo la aplicación puede imitar el aspecto de Microsoft Office 2003, vea [CMFCVisualManagerOffice2003 Class](../../mfc/reference/cmfcvisualmanageroffice2003-class.md).  
  
 Todos los métodos de dibujo son virtuales.  Esto permite crear un estilo visual personalizado para GUI de la aplicación.  Si desea crear dispone de estilo visual, derive una clase de una de las clases visuales de administrador y reemplazar los métodos de dibujo que desea cambiar.  
  
## Ejemplo  
 Este ejemplo muestra cómo crear instancias de objetos de `CMFCVisualManager` del estándar y personalizadas.  
  
```  
void CMFCSkinsApp::SetSkin (int iIndex)  
{   // destroy the current visual manager  
   if (CMFCVisualManager::GetInstance () != NULL)  
   {  
      delete CMFCVisualManager::GetInstance ();  
   }  
   switch (iIndex)  
  {  
   case 0:  
      CMFCVisualManager::GetInstance (); // create the standard visual manager  
      break;  
   case 1:  
      new CMyVisualManager (); // create the first custom visual manager  
      break;  
   case 2:  
      new CMacStyle ();  // create the second custom visual manager  
      break;  
   }  
  
   // access the manager and set it properly  
   CMFCVisualManager::GetInstance ()->SetLook2000 ();  
   CMFCVisualManager::GetInstance ()->RedrawAll ();  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar los valores predeterminados de un objeto de `CMFCVisualManager` .  Este fragmento de código es parte de [Ejemplo del panel de tareas](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_TasksPane#1](../../mfc/reference/codesnippet/CPP/cmfcvisualmanager-class_1.h)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
## Requisitos  
 **encabezado:** afxvisualmanager.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager::GetInstance](../Topic/CMFCVisualManager::GetInstance.md)   
 [Administrador de visualización](../../mfc/visualization-manager.md)