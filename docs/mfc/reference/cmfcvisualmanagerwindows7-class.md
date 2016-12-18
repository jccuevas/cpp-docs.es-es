---
title: "CMFCVisualManagerWindows7 Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxvisualmanagerwindows7/CMFCVisualManagerWindows7"
  - "CMFCVisualManagerWindows7"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows7 class"
ms.assetid: e8d87df1-0c09-4b58-8ade-4e911f796e42
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerWindows7 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerWindows7` proporciona a aplicación la apariencia de una aplicación de [!INCLUDE[win7](../../build/includes/win7_md.md)] .  
  
## Sintaxis  
  
```  
class CMFCVisualManagerWindows7 : public CMFCVisualManagerWindows;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCVisualManagerWindows7::CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::CMFCVisualManagerWindows7.md)|Constructor predeterminado.|  
|[CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7](../Topic/CMFCVisualManagerWindows7::~CMFCVisualManagerWindows7.md)|Un destructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCVisualManagerWindows7::CleanStyle`|Borra el estilo visual actual y restaura el estilo visual predeterminado.|  
|`CMFCVisualManagerWindows7::CleanUp`|Borra todos los objetos de la interfaz de usuario y restaura los menús.|  
|`CMFCVisualManagerWindows7::DrawNcBtn`|Dibuja un botón en el área de no cliente en el cuadro.  El marco de trabajo usa este método para dibujar minimiza, maximiza, cierre y botones de restauración en la esquina superior derecha de la ventana.  Este método no se llama cuando el programa utiliza un tema de no\-Aero.|  
|`CMFCVisualManagerWindows7::DrawNcText`|Dibuja el texto en el área de no cliente en el cuadro.  El marco de trabajo usa este método para dibujar el título de la aplicación en la barra de título en la parte superior de la ventana de marco.|  
|`CMFCVisualManagerWindows7::DrawSeparator`|Dibuja un separador en [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md).|  
|`CMFCVisualManagerWindows7::GetRibbonBar`|Recupera [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md) asociado a la interfaz de usuario.|  
|[CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor](../Topic/CMFCVisualManagerWindows7::GetRibbonEditBackgroundColor.md)|Obtiene un color de fondo del cuadro de edición de la cinta de opciones.|  
|`CMFCVisualManagerWindows7::GetRibbonPopupBorderSize`|Reemplaza [CMFCVisualManager::GetRibbonPopupBorderSize](../Topic/CMFCVisualManager::GetRibbonPopupBorderSize.md).|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarChevronOffset`|Reemplaza [CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset.md).|  
|`CMFCVisualManagerWindows7::GetRibbonQuickAccessToolBarRightMargin`|Reemplaza [CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin](../Topic/CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin.md).|  
|`CMFCVisualManagerWindows7::IsHighlightWholeMenuItem`|Reemplaza [CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md).|  
|`CMFCVisualManagerWindows7::IsOwnerDrawMenuCheck`|Reemplaza [CMFCVisualManager::IsOwnerDrawMenuCheck](../Topic/CMFCVisualManager::IsOwnerDrawMenuCheck.md).|  
|`CMFCVisualManagerWindows7::IsRibbonPresent`|Determina si `CMFCRibbonBar` está presente y visible.|  
|`CMFCVisualManagerWindows7::OnDrawButtonBorder`|Reemplaza [CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md).|  
|`CMFCVisualManagerWindows7::OnDrawCheckBoxEx`|Reemplaza [CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md).|  
|`CMFCVisualManagerWindows7::OnDrawComboDropButton`|Reemplaza [CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawDefaultRibbonImage`|Reemplaza [CMFCVisualManager::OnDrawDefaultRibbonImage](../Topic/CMFCVisualManager::OnDrawDefaultRibbonImage.md).|  
|`CMFCVisualManagerWindows7::OnDrawMenuBorder`|Reemplaza [CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md).|  
|`CMFCVisualManagerWindows7::OnDrawMenuCheck`|Reemplaza [CMFCVisualManager::OnDrawMenuCheck](../Topic/CMFCVisualManager::OnDrawMenuCheck.md).|  
|`CMFCVisualManagerWindows7::OnDrawMenuLabel`|Reemplaza [CMFCVisualManager::OnDrawMenuLabel](../Topic/CMFCVisualManager::OnDrawMenuLabel.md).|  
|`CMFCVisualManagerWindows7::OnDrawRadioButton`|Reemplaza `CMFCVisualManager::OnDrawRadioButton`.|  
|`CMFCVisualManagerWindows7::OnDrawRibbonApplicationButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonApplicationButton](../Topic/CMFCVisualManager::OnDrawRibbonApplicationButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonButtonBorder`|Reemplaza [CMFCVisualManager::OnDrawRibbonButtonBorder](../Topic/CMFCVisualManager::OnDrawRibbonButtonBorder.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaption`|Reemplaza [CMFCVisualManager::OnDrawRibbonCaption](../Topic/CMFCVisualManager::OnDrawRibbonCaption.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCaptionButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonCaptionButton](../Topic/CMFCVisualManager::OnDrawRibbonCaptionButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategory`|Reemplaza [CMFCVisualManager::OnDrawRibbonCategory](../Topic/CMFCVisualManager::OnDrawRibbonCategory.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonCategoryTab`|Reemplaza [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonDefaultPaneButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonDefaultPaneButton](../Topic/CMFCVisualManager::OnDrawRibbonDefaultPaneButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonGalleryButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonGalleryButton](../Topic/CMFCVisualManager::OnDrawRibbonGalleryButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonLaunchButton`|Reemplaza `CMFCVisualManager::OnDrawRibbonLaunchButton`.|  
|`CMFCVisualManagerWindows7::OnDrawRibbonMenuCheckFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonMenuCheckFrame](../Topic/CMFCVisualManager::OnDrawRibbonMenuCheckFrame.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanel`|Reemplaza [CMFCVisualManager::OnDrawRibbonPanel](../Topic/CMFCVisualManager::OnDrawRibbonPanel.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonPanelCaption`|Reemplaza [CMFCVisualManager::OnDrawRibbonPanelCaption](../Topic/CMFCVisualManager::OnDrawRibbonPanelCaption.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonProgressBar`|Reemplaza [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonRecentFilesFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonRecentFilesFrame](../Topic/CMFCVisualManager::OnDrawRibbonRecentFilesFrame.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderChannel`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderThumb`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonSliderZoomButton`|Reemplaza [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonStatusBarPane`|Reemplaza [CMFCVisualManager::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManager::OnDrawRibbonStatusBarPane.md).|  
|`CMFCVisualManagerWindows7::OnDrawRibbonTabsFrame`|Reemplaza [CMFCVisualManager::OnDrawRibbonTabsFrame](../Topic/CMFCVisualManager::OnDrawRibbonTabsFrame.md).|  
|`CMFCVisualManagerWindows7::OnDrawStatusBarSizeBox`|Reemplaza [CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md).|  
|`CMFCVisualManagerWindows7::OnFillBarBackground`|Reemplaza [CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md).|  
|`CMFCVisualManagerWindows7::OnFillButtonInterior`|Reemplaza [CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md).|  
|[CMFCVisualManagerWindows7::OnFillMenuImageRect](../Topic/CMFCVisualManagerWindows7::OnFillMenuImageRect.md)|El marco de trabajo llama a este método cuando rellena área alrededor de imágenes del elemento de menú.|  
|`CMFCVisualManagerWindows7::OnFillRibbonButton`|Reemplaza [CMFCVisualManager::OnFillRibbonButton](../Topic/CMFCVisualManager::OnFillRibbonButton.md).|  
|`CMFCVisualManagerWindows7::OnFillRibbonQuickAccessToolBarPopup`|Reemplaza [CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](../Topic/CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup.md).|  
|`CMFCVisualManagerWindows7::OnHighlightMenuItem`|Reemplaza [CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md).|  
|`CMFCVisualManagerWindows7::OnNcActivate`|Reemplaza [CMFCVisualManager::OnNcActivate](../Topic/CMFCVisualManager::OnNcActivate.md).|  
|`CMFCVisualManagerWindows7::OnNcPaint`|Reemplaza [CMFCVisualManager::OnNcPaint](../Topic/CMFCVisualManager::OnNcPaint.md).|  
|`CMFCVisualManagerWindows7::OnUpdateSystemColors`|Reemplaza [CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md).|  
|`CMFCVisualManagerWindows7::SetResourceHandle`|Establece el identificador de recurso que describe los atributos de administrador visual.|  
|`CMFCVisualManagerWindows7::SetStyle`|establece la combinación de colores de `CMFCVisualManagerWindows7` GUI.|  
  
## Comentarios  
 utilice la clase de `CMFCVisualManagerWindows7` para cambiar el aspecto de la aplicación para imitar una aplicación predeterminada de [!INCLUDE[win7](../../build/includes/win7_md.md)] .  Esta clase puede no ser válido si la aplicación se ejecuta en una versión anterior de Windows que [!INCLUDE[win7](../../build/includes/win7_md.md)].  En este caso, la aplicación utiliza el administrador visual predeterminado definido en [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md).  
  
 El CMFCVisualManagerWindows7 hereda varios métodos de [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md) y la clase de `CMFCVisualManager` .  los métodos enumerados en la sección anterior son métodos nuevos a la clase de `CMFCVisualManagerWindows7` .  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
 `CMFCVisualManagerWindows7`  
  
## Requisitos  
 **encabezado:** afxvisualmanagerwindows7.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)