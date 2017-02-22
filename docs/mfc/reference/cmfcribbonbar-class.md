---
title: "CMFCRibbonBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonBar class"
ms.assetid: a65d06fa-1a28-4cc0-8971-bc9d7c9198fe
caps.latest.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 43
---
# CMFCRibbonBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCRibbonBar` implementa una barra de cinta similar a la que se usaba en Office 2007.  
  
## Sintaxis  
  
```  
class CMFCRibbonBar : public CPane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonBar::CMFCRibbonBar`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonBar::ActivateContextCategory](../Topic/CMFCRibbonBar::ActivateContextCategory.md)|Activa una categoría de contexto que ya está visible.|  
|[CMFCRibbonBar::AddCategory](../Topic/CMFCRibbonBar::AddCategory.md)|Agrega una nueva categoría de cinta de opciones a la cinta.|  
|[CMFCRibbonBar::AddContextCategory](../Topic/CMFCRibbonBar::AddContextCategory.md)|Agrega una categoría de contexto.|  
|[CMFCRibbonBar::AddMainCategory](../Topic/CMFCRibbonBar::AddMainCategory.md)|Agrega una nueva categoría principal de cinta de opciones.|  
|[CMFCRibbonBar::AddPrintPreviewCategory](../Topic/CMFCRibbonBar::AddPrintPreviewCategory.md)||  
|[CMFCRibbonBar::AddQATOnlyCategory](../Topic/CMFCRibbonBar::AddQATOnlyCategory.md)||  
|[CMFCRibbonBar::AddToTabs](../Topic/CMFCRibbonBar::AddToTabs.md)|Agrega un elemento de la cinta de opciones a la derecha de una barra de cinta.|  
|[CMFCRibbonBar::CreateEx](../Topic/CMFCRibbonBar::CreateEx.md)|Crea una barra de control y la adjunta al objeto [CPane](../../mfc/reference/cpane-class.md).  \(Invalida [CPane::CreateEx](../Topic/CPane::CreateEx.md)\).|  
|[CMFCRibbonBar::Create](../Topic/CMFCRibbonBar::Create.md)|Crea un control de barra de cinta y lo adjunta a una barra de cinta.|  
|[CMFCRibbonBar::DeactivateKeyboardFocus](../Topic/CMFCRibbonBar::DeactivateKeyboardFocus.md)||  
|[CMFCRibbonBar::DrawMenuImage](../Topic/CMFCRibbonBar::DrawMenuImage.md)||  
|[CMFCRibbonBar::DWMCompositionChanged](../Topic/CMFCRibbonBar::DWMCompositionChanged.md)||  
|[CMFCRibbonBar::EnableKeyTips](../Topic/CMFCRibbonBar::EnableKeyTips.md)|Habilita o deshabilita las sugerencias de teclas para el control de la cinta de opciones.|  
|[CMFCRibbonBar::EnablePrintPreview](../Topic/CMFCRibbonBar::EnablePrintPreview.md)|Habilita la pestaña **Vista previa de impresión**.|  
|[CMFCRibbonBar::EnableToolTips](../Topic/CMFCRibbonBar::EnableToolTips.md)|Habilita o deshabilita las descripciones de información sobre herramientas y la información sobre herramientas en la barra de cinta.|  
|[CMFCRibbonBar::FindByData](../Topic/CMFCRibbonBar::FindByData.md)|Busca un elemento de la cinta de opciones usando los datos que un usuario especifica.|  
|[CMFCRibbonBar::FindByID](../Topic/CMFCRibbonBar::FindByID.md)|Busca un elemento de la cinta de opciones que tiene el identificador de comando especificado.|  
|[CMFCRibbonBar::FindCategoryIndexByData](../Topic/CMFCRibbonBar::FindCategoryIndexByData.md)|Busca el índice de la categoría de la cinta que contiene los datos definidos por el usuario.|  
|[CMFCRibbonBar::ForceRecalcLayout](../Topic/CMFCRibbonBar::ForceRecalcLayout.md)||  
|[CMFCRibbonBar::GetActiveCategory](../Topic/CMFCRibbonBar::GetActiveCategory.md)|Obtiene un puntero a una categoría activa.|  
|[CMFCRibbonBar::GetCaptionHeight](../Topic/CMFCRibbonBar::GetCaptionHeight.md)|Devuelve la altura del título.  \(Invalida [CBasePane::GetCaptionHeight](../Topic/CBasePane::GetCaptionHeight.md)\).|  
|[CMFCRibbonBar::GetCategory](../Topic/CMFCRibbonBar::GetCategory.md)|Obtiene el puntero a una categoría ubicada en un índice especificado.|  
|[CMFCRibbonBar::GetCategoryCount](../Topic/CMFCRibbonBar::GetCategoryCount.md)|Obtiene el número de categorías de la cinta de la barra de cinta.|  
|[CMFCRibbonBar::GetCategoryHeight](../Topic/CMFCRibbonBar::GetCategoryHeight.md)||  
|[CMFCRibbonBar::GetCategoryIndex](../Topic/CMFCRibbonBar::GetCategoryIndex.md)|Devuelve el índice de una categoría de la cinta.|  
|[CMFCRibbonBar::GetContextName](../Topic/CMFCRibbonBar::GetContextName.md)|Recupera el título de la categoría de contexto especificada con un identificador.|  
|[CMFCRibbonBar::GetDroppedDown](../Topic/CMFCRibbonBar::GetDroppedDown.md)||  
|[CMFCRibbonBar::GetElementsByID](../Topic/CMFCRibbonBar::GetElementsByID.md)|Obtiene una matriz que contiene los punteros a todos los elementos de la cinta de opciones que tienen el identificador especificado.|  
|[CMFCRibbonBar::GetApplicationButton](../Topic/CMFCRibbonBar::GetApplicationButton.md)|Obtiene un puntero a un botón de la cinta de opciones.|  
|[CMFCRibbonBar::GetFocused](../Topic/CMFCRibbonBar::GetFocused.md)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonBar::GetHideFlags](../Topic/CMFCRibbonBar::GetHideFlags.md)||  
|[CMFCRibbonBar::GetItemIDsList](../Topic/CMFCRibbonBar::GetItemIDsList.md)||  
|[CMFCRibbonBar::GetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::GetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelCurrent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelCurrent.md)||  
|[CMFCRibbonBar::GetKeyboardNavLevelParent](../Topic/CMFCRibbonBar::GetKeyboardNavLevelParent.md)||  
|[CMFCRibbonBar::GetMainCategory](../Topic/CMFCRibbonBar::GetMainCategory.md)|Devuelve un puntero a la categoría de cinta de opciones seleccionada actualmente.|  
|[CMFCRibbonBar::GetQATCommandsLocation](../Topic/CMFCRibbonBar::GetQATCommandsLocation.md)||  
|[CMFCRibbonBar::GetQATDroppedDown](../Topic/CMFCRibbonBar::GetQATDroppedDown.md)||  
|[CMFCRibbonBar::GetQuickAccessCommands](../Topic/CMFCRibbonBar::GetQuickAccessCommands.md)|Rellena una lista que contiene los identificadores de comando de todos los elementos que aparecen en la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::GetQuickAccessToolbarLocation](../Topic/CMFCRibbonBar::GetQuickAccessToolbarLocation.md)||  
|[CMFCRibbonBar::GetTabTrancateRatio](../Topic/CMFCRibbonBar::GetTabTrancateRatio.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthLargeImage](../Topic/CMFCRibbonBar::GetTooltipFixedWidthLargeImage.md)||  
|[CMFCRibbonBar::GetTooltipFixedWidthRegular](../Topic/CMFCRibbonBar::GetTooltipFixedWidthRegular.md)||  
|[CMFCRibbonBar::GetVisibleCategoryCount](../Topic/CMFCRibbonBar::GetVisibleCategoryCount.md)||  
|[CMFCRibbonBar::HideAllContextCategories](../Topic/CMFCRibbonBar::HideAllContextCategories.md)|Oculta todas las categorías que están activas y visibles.|  
|[CMFCRibbonBar::HideKeyTips](../Topic/CMFCRibbonBar::HideKeyTips.md)||  
|[CMFCRibbonBar::HitTest](../Topic/CMFCRibbonBar::HitTest.md)|Busca un puntero al elemento de la cinta de opciones que se encuentra en el punto especificado en las coordenadas de cliente de la barra de cinta.|  
|[CMFCRibbonBar::IsKeyTipEnabled](../Topic/CMFCRibbonBar::IsKeyTipEnabled.md)|Determina si se habilitan sugerencias de teclas.|  
|[CMFCRibbonBar::IsMainRibbonBar](../Topic/CMFCRibbonBar::IsMainRibbonBar.md)||  
|[CMFCRibbonBar::IsPrintPreviewEnabled](../Topic/CMFCRibbonBar::IsPrintPreviewEnabled.md)|Determina si la pestaña **Vista previa de impresión** está habilitada.|  
|[CMFCRibbonBar::IsQATEmpty](../Topic/CMFCRibbonBar::IsQATEmpty.md)||  
|[CMFCRibbonBar::IsQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::IsQuickAccessToolbarOnTop.md)|Especifica si la barra de herramientas de acceso rápido se encuentra encima de la barra de cinta.|  
|[CMFCRibbonBar::IsReplaceFrameCaption](../Topic/CMFCRibbonBar::IsReplaceFrameCaption.md)|Determina si la barra de cinta reemplaza al título del marco principal o si se agrega debajo de la leyenda del marco.|  
|[CMFCRibbonBar::IsShowGroupBorder](../Topic/CMFCRibbonBar::IsShowGroupBorder.md)||  
|[CMFCRibbonBar::IsToolTipDescrEnabled](../Topic/CMFCRibbonBar::IsToolTipDescrEnabled.md)|Determina si las descripciones de la información sobre herramientas están habilitadas.|  
|[CMFCRibbonBar::IsToolTipEnabled](../Topic/CMFCRibbonBar::IsToolTipEnabled.md)|Determina si la información sobre herramientas de la barra de cinta está habilitada.|  
|[CMFCRibbonBar::IsTransparentCaption](../Topic/CMFCRibbonBar::IsTransparentCaption.md)||  
|[CMFCRibbonBar::IsWindows7Look](../Topic/CMFCRibbonBar::IsWindows7Look.md)|Indica si la cinta de opciones tiene la apariencia de Windows 7 \(botón de aplicación rectangular pequeño\).|  
|[CMFCRibbonBar::LoadFromResource](../Topic/CMFCRibbonBar::LoadFromResource.md)|Sobrecargado.  Carga una barra de cinta a partir de los recursos de la aplicación.|  
|[CMFCRibbonBar::OnClickButton](../Topic/CMFCRibbonBar::OnClickButton.md)||  
|[CMFCRibbonBar::OnEditContextMenu](../Topic/CMFCRibbonBar::OnEditContextMenu.md)||  
|[CMFCRibbonBar::OnRTLChanged](../Topic/CMFCRibbonBar::OnRTLChanged.md)|\(Invalida `CPane::OnRTLChanged`\).|  
|[CMFCRibbonBar::OnSetAccData](../Topic/CMFCRibbonBar::OnSetAccData.md)|\(Invalida [CBasePane::OnSetAccData](../Topic/CBasePane::OnSetAccData.md)\).|  
|[CMFCRibbonBar::OnShowRibbonContextMenu](../Topic/CMFCRibbonBar::OnShowRibbonContextMenu.md)||  
|[CMFCRibbonBar::OnShowRibbonQATMenu](../Topic/CMFCRibbonBar::OnShowRibbonQATMenu.md)||  
|[CMFCRibbonBar::OnSysKeyDown](../Topic/CMFCRibbonBar::OnSysKeyDown.md)||  
|[CMFCRibbonBar::OnSysKeyUp](../Topic/CMFCRibbonBar::OnSysKeyUp.md)||  
|[CMFCRibbonBar::PopTooltip](../Topic/CMFCRibbonBar::PopTooltip.md)||  
|[CMFCRibbonBar::PreTranslateMessage](../Topic/CMFCRibbonBar::PreTranslateMessage.md)|\(Invalida `CBasePane::PreTranslateMessage`\).|  
|[CMFCRibbonBar::RecalcLayout](../Topic/CMFCRibbonBar::RecalcLayout.md)|\(Invalida [CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)\).|  
|[CMFCRibbonBar::RemoveAllCategories](../Topic/CMFCRibbonBar::RemoveAllCategories.md)|Quita todas las categorías de la cinta de opciones de la barra de cinta.|  
|[CMFCRibbonBar::RemoveAllFromTabs](../Topic/CMFCRibbonBar::RemoveAllFromTabs.md)|Quita todos los elementos de la cinta de opciones del área de pestañas.|  
|[CMFCRibbonBar::RemoveCategory](../Topic/CMFCRibbonBar::RemoveCategory.md)|Quita la categoría de cinta de opciones que se encuentra en el índice especificado.|  
|[CMFCRibbonBar::SaveToXMLBuffer](../Topic/CMFCRibbonBar::SaveToXMLBuffer.md)|Guarda la barra de cinta en un búfer.|  
|[CMFCRibbonBar::SaveToXMLFile](../Topic/CMFCRibbonBar::SaveToXMLFile.md)|Guarda la barra de cinta en un archivo XML.|  
|[CMFCRibbonBar::SetActiveCategory](../Topic/CMFCRibbonBar::SetActiveCategory.md)|Establece una categoría especificada de la cinta de opciones como activa.|  
|[CMFCRibbonBar::SetActiveMDIChild](../Topic/CMFCRibbonBar::SetActiveMDIChild.md)||  
|[CMFCRibbonBar::SetElementKeys](../Topic/CMFCRibbonBar::SetElementKeys.md)|Establece las sugerencias de teclas especificadas para todos los elementos de la cinta de opciones que tienen el identificador de comando especificado.|  
|[CMFCRibbonBar::SetApplicationButton](../Topic/CMFCRibbonBar::SetApplicationButton.md)|Asigna un botón de la cinta de opciones de aplicación a la barra de cinta.|  
|[CMFCRibbonBar::SetKeyboardNavigationLevel](../Topic/CMFCRibbonBar::SetKeyboardNavigationLevel.md)||  
|[CMFCRibbonBar::SetMaximizeMode](../Topic/CMFCRibbonBar::SetMaximizeMode.md)||  
|[CMFCRibbonBar::SetQuickAccessCommands](../Topic/CMFCRibbonBar::SetQuickAccessCommands.md)|Agrega uno o más elementos de la cinta de opciones a la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::SetQuickAccessDefaultState](../Topic/CMFCRibbonBar::SetQuickAccessDefaultState.md)|Especifica el estado predeterminado de la barra de herramientas de acceso rápido.|  
|[CMFCRibbonBar::SetQuickAccessToolbarOnTop](../Topic/CMFCRibbonBar::SetQuickAccessToolbarOnTop.md)|Coloca la barra de herramientas de acceso rápido \(QAT\) encima o debajo de la barra de cinta.|  
|[CMFCRibbonBar::SetTooltipFixedWidth](../Topic/CMFCRibbonBar::SetTooltipFixedWidth.md)||  
|[CMFCRibbonBar::SetWindows7Look](../Topic/CMFCRibbonBar::SetWindows7Look.md)|Habilita\/deshabilita la apariencia de Windows 7 \(botón de aplicación rectangular pequeño\) para la cinta de opciones.|  
|[CMFCRibbonBar::ShowCategory](../Topic/CMFCRibbonBar::ShowCategory.md)|Muestra u oculta la categoría de la cinta de opciones especificada.|  
|[CMFCRibbonBar::ShowContextCategories](../Topic/CMFCRibbonBar::ShowContextCategories.md)|Muestra u oculta las categorías de contexto que tienen el identificador especificado.|  
|[CMFCRibbonBar::ShowKeyTips](../Topic/CMFCRibbonBar::ShowKeyTips.md)||  
|[CMFCRibbonBar::ToggleMimimizeState](../Topic/CMFCRibbonBar::ToggleMimimizeState.md)|Alterna la barra de cinta entre los estados minimizado y maximizado.|  
|[CMFCRibbonBar::TranslateChar](../Topic/CMFCRibbonBar::TranslateChar.md)||  
  
## Comentarios  
 Microsoft presentó la cinta de opciones de Office Fluent junto con el lanzamiento de Microsoft Office 2007.  Esta barra de cinta es mucho más que un control nuevo:  representa un nuevo paradigma de interfaz de usuario.  La cinta de opciones es un panel que contiene un conjunto de pestañas denominada categorías.  Cada categoría se divide lógicamente en paneles de cinta y cada panel puede contener varios controles y botones de comando.  
  
 Los elementos que aparecen en la barra de cinta se expanden y se contrae para optimizar el espacio disponible.  Por ejemplo, si un panel de cinta no tiene suficiente espacio para mostrar sus elementos, se convierte en un botón de menú que muestra los subelementos en un menú emergente.  La barra de cinta se comporta como una barra de control estática \(no flotante\) y se puede acoplar en la parte superior de un marco.  
  
 Puede usar la clase `CMFCRibbonStatusBar` para implementar una barra de estado similar a la que se usaba en Office 2007.  Una categoría de cinta de opciones contiene \(y muestra\) un grupo de [paneles de cinta](../../mfc/reference/cmfcribbonpanel-class.md).  Cada panel de cinta contiene uno o más elementos de la cinta de opciones, que se obtienen de [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 Para obtener información sobre cómo agregar una barra de cinta a la aplicación MFC existente, vea [Tutorial: Actualizar la aplicación Scribble de MFC](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)  
  
## Requisitos  
 **Encabezado:** afxribbonbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [Tutorial: Actualizar la aplicación Scribble de MFC](../../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)