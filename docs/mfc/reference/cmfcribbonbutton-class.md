---
title: "CMFCRibbonButton Class | Microsoft Docs"
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
  - "CMFCRibbonButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonButton class"
ms.assetid: 732e941c-9504-4b83-a691-d18075965d53
caps.latest.revision: 42
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCRibbonButton` implementa botones que puede colocar en elementos de barra de cinta como paneles, barras de herramientas de acceso rápido y menús emergentes.  
  
## Sintaxis  
  
```  
class CMFCRibbonButton : public CMFCRibbonBaseElement  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::CMFCRibbonButton](../Topic/CMFCRibbonButton::CMFCRibbonButton.md)|Construye un objeto de botón de la cinta.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::AddSubItem](../Topic/CMFCRibbonButton::AddSubItem.md)|Agrega un elemento de menú al menú emergente asociado al botón.|  
|[CMFCRibbonButton::CanBeStretched](../Topic/CMFCRibbonButton::CanBeStretched.md)|\(Invalida [CMFCRibbonBaseElement::CanBeStretched](../Topic/CMFCRibbonBaseElement::CanBeStretched.md)\).|  
|[CMFCRibbonButton::CleanUpSizes](../Topic/CMFCRibbonButton::CleanUpSizes.md)|\(Invalida [CMFCRibbonBaseElement::CleanUpSizes](../Topic/CMFCRibbonBaseElement::CleanUpSizes.md)\).|  
|[CMFCRibbonButton::ClosePopupMenu](../Topic/CMFCRibbonButton::ClosePopupMenu.md)|\(Invalida [CMFCRibbonBaseElement::ClosePopupMenu](../Topic/CMFCRibbonBaseElement::ClosePopupMenu.md)\).|  
|[CMFCRibbonButton::DrawBottomText](../Topic/CMFCRibbonButton::DrawBottomText.md)||  
|[CMFCRibbonButton::DrawImage](../Topic/CMFCRibbonButton::DrawImage.md)|\(Invalida [CMFCRibbonBaseElement::DrawImage](../Topic/CMFCRibbonBaseElement::DrawImage.md)\).|  
|[CMFCRibbonButton::DrawRibbonText](../Topic/CMFCRibbonButton::DrawRibbonText.md)||  
|[CMFCRibbonButton::FindSubItemIndexByID](../Topic/CMFCRibbonButton::FindSubItemIndexByID.md)|Devuelve el índice de un elemento de menú emergente asociado al id. de comando especificado.|  
|[CMFCRibbonButton::GetCommandRect](../Topic/CMFCRibbonButton::GetCommandRect.md)||  
|[CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)|Devuelve el tamaño compacto del elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::GetCompactSize](../Topic/CMFCRibbonBaseElement::GetCompactSize.md)\).|  
|[CMFCRibbonButton::GetIcon](../Topic/CMFCRibbonButton::GetIcon.md)||  
|[CMFCRibbonButton::GetImageIndex](../Topic/CMFCRibbonButton::GetImageIndex.md)|Devuelve el índice de la imagen asociada al botón.|  
|[CMFCRibbonButton::GetImageSize](../Topic/CMFCRibbonButton::GetImageSize.md)|Devuelve el tamaño de la imagen del elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::GetImageSize](../Topic/CMFCRibbonBaseElement::GetImageSize.md)\).|  
|[CMFCRibbonButton::GetIntermediateSize](../Topic/CMFCRibbonButton::GetIntermediateSize.md)|Devuelve el tamaño del elemento de la cinta en su estado intermedio.  \(Invalida [CMFCRibbonBaseElement::GetIntermediateSize](../Topic/CMFCRibbonBaseElement::GetIntermediateSize.md)\).|  
|[CMFCRibbonButton::GetMenu](../Topic/CMFCRibbonButton::GetMenu.md)|Devuelve un controlador a un menú de Windows que se asigna al botón de la cinta.|  
|[CMFCRibbonButton::GetMenuRect](../Topic/CMFCRibbonButton::GetMenuRect.md)||  
|[CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)|Devuelve el tamaño normal del elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md)\).|  
|[CMFCRibbonButton::GetSubItems](../Topic/CMFCRibbonButton::GetSubItems.md)||  
|[CMFCRibbonButton::GetTextRowHeight](../Topic/CMFCRibbonButton::GetTextRowHeight.md)||  
|[CMFCRibbonButton::GetToolTipText](../Topic/CMFCRibbonButton::GetToolTipText.md)|Devuelve el texto de información sobre herramientas del elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::GetToolTipText](../Topic/CMFCRibbonBaseElement::GetToolTipText.md)\).|  
|[CMFCRibbonButton::HasCompactMode](../Topic/CMFCRibbonButton::HasCompactMode.md)|Especifica si el elemento de la cinta tiene un modo compacto.  \(Invalida [CMFCRibbonBaseElement::HasCompactMode](../Topic/CMFCRibbonBaseElement::HasCompactMode.md)\).|  
|[CMFCRibbonButton::HasIntermediateMode](../Topic/CMFCRibbonButton::HasIntermediateMode.md)|Especifica si el elemento de la cinta tiene un modo intermedio.  \(Invalida [CMFCRibbonBaseElement::HasIntermediateMode](../Topic/CMFCRibbonBaseElement::HasIntermediateMode.md)\).|  
|[CMFCRibbonButton::HasLargeMode](../Topic/CMFCRibbonButton::HasLargeMode.md)|Determina si el elemento de la cinta tiene un modo grande.  \(Invalida [CMFCRibbonBaseElement::HasLargeMode](../Topic/CMFCRibbonBaseElement::HasLargeMode.md)\).|  
|[CMFCRibbonButton::HasMenu](../Topic/CMFCRibbonButton::HasMenu.md)|\(Invalida [CMFCRibbonBaseElement::HasMenu](../Topic/CMFCRibbonBaseElement::HasMenu.md)\).|  
|[CMFCRibbonButton::IsAlwaysDrawBorder](../Topic/CMFCRibbonButton::IsAlwaysDrawBorder.md)||  
|[CMFCRibbonButton::IsAlwaysLargeImage](../Topic/CMFCRibbonButton::IsAlwaysLargeImage.md)|\(Invalida [CMFCRibbonBaseElement::IsAlwaysLargeImage](../Topic/CMFCRibbonBaseElement::IsAlwaysLargeImage.md)\).|  
|[CMFCRibbonButton::IsApplicationButton](../Topic/CMFCRibbonButton::IsApplicationButton.md)||  
|[CMFCRibbonButton::IsCommandAreaHighlighted](../Topic/CMFCRibbonButton::IsCommandAreaHighlighted.md)||  
|[CMFCRibbonButton::IsDefaultCommand](../Topic/CMFCRibbonButton::IsDefaultCommand.md)|Determina si se ha habilitado el comando predeterminado de un botón de la cinta.|  
|[CMFCRibbonButton::IsDefaultPanelButton](../Topic/CMFCRibbonButton::IsDefaultPanelButton.md)||  
|[CMFCRibbonButton::IsDrawTooltipImage](../Topic/CMFCRibbonButton::IsDrawTooltipImage.md)||  
|[CMFCRibbonButton::IsLargeImage](../Topic/CMFCRibbonButton::IsLargeImage.md)||  
|[CMFCRibbonButton::IsMenuAreaHighlighted](../Topic/CMFCRibbonButton::IsMenuAreaHighlighted.md)||  
|[CMFCRibbonButton::IsMenuOnBottom](../Topic/CMFCRibbonButton::IsMenuOnBottom.md)||  
|[CMFCRibbonButton::IsPopupDefaultMenuLook](../Topic/CMFCRibbonButton::IsPopupDefaultMenuLook.md)||  
|[CMFCRibbonButton::IsRightAlignMenu](../Topic/CMFCRibbonButton::IsRightAlignMenu.md)|Determina si el menú está alineado a la derecha.|  
|[CMFCRibbonButton::IsSingleLineText](../Topic/CMFCRibbonButton::IsSingleLineText.md)||  
|[CMFCRibbonButton::OnCalcTextSize](../Topic/CMFCRibbonButton::OnCalcTextSize.md)|\(Invalida [CMFCRibbonBaseElement::OnCalcTextSize](../Topic/CMFCRibbonBaseElement::OnCalcTextSize.md)\).|  
|[CMFCRibbonButton::OnDrawBorder](../Topic/CMFCRibbonButton::OnDrawBorder.md)||  
|[CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)|Llamado por el marco de trabajo para dibujar el elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md)\).|  
|[CMFCRibbonButton::OnFillBackground](../Topic/CMFCRibbonButton::OnFillBackground.md)||  
|[CMFCRibbonButton::RemoveAllSubItems](../Topic/CMFCRibbonButton::RemoveAllSubItems.md)|Quita todos los elementos del menú emergente.|  
|[CMFCRibbonButton::RemoveSubItem](../Topic/CMFCRibbonButton::RemoveSubItem.md)|Quita un elemento del menú emergente.|  
|[CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)|\(Invalida [CMFCRibbonBaseElement::SetACCData](../Topic/CMFCRibbonBaseElement::SetACCData.md)\).|  
|[CMFCRibbonButton::SetAlwaysLargeImage](../Topic/CMFCRibbonButton::SetAlwaysLargeImage.md)|Especifica si el botón muestra una imagen grande o pequeña cuando el usuario lo contrae.|  
|[CMFCRibbonButton::SetDefaultCommand](../Topic/CMFCRibbonButton::SetDefaultCommand.md)|Habilita el comando predeterminado del botón de la cinta.|  
|[CMFCRibbonButton::SetDescription](../Topic/CMFCRibbonButton::SetDescription.md)|Establece la descripción del elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::SetDescription](../Topic/CMFCRibbonBaseElement::SetDescription.md)\).|  
|[CMFCRibbonButton::SetImageIndex](../Topic/CMFCRibbonButton::SetImageIndex.md)|Asigna un índice a la imagen del botón.|  
|[CMFCRibbonButton::SetMenu](../Topic/CMFCRibbonButton::SetMenu.md)|Asigna un menú emergente al botón de la cinta.|  
|[CMFCRibbonButton::SetParentCategory](../Topic/CMFCRibbonButton::SetParentCategory.md)|\(Invalida [CMFCRibbonBaseElement::SetParentCategory](../Topic/CMFCRibbonBaseElement::SetParentCategory.md)\).|  
|[CMFCRibbonButton::SetRightAlignMenu](../Topic/CMFCRibbonButton::SetRightAlignMenu.md)|Alinea el menú emergente a la derecha del botón.|  
|[CMFCRibbonButton::SetText](../Topic/CMFCRibbonButton::SetText.md)|Establece el texto para el elemento de la cinta.  \(Invalida [CMFCRibbonBaseElement::SetText](../Topic/CMFCRibbonBaseElement::SetText.md)\).|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonButton::OnClick](../Topic/CMFCRibbonButton::OnClick.md)|Llamado por el marco de trabajo cuando el usuario hace clic en el botón.|  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCRibbonButton`.  En el ejemplo se muestra cómo construir un objeto de la clase `CMFCRibbonButton`, asignar un menú emergente al botón de la cinta, establecer la descripción del botón, quitar un elemento del menú emergente y alinear a la derecha el menú emergente hacia el borde del botón.  
  
 [!code-cpp[NVC_MFC_RibbonApp#7](../../mfc/reference/codesnippet/CPP/cmfcribbonbutton-class_1.cpp)]  
  
## Comentarios  
 Para usar un botón de la cinta en una aplicación, construya el objeto de botón y agréguelo al [panel](../../mfc/reference/cmfcribbonpanel-class.md) de la cinta adecuado.  
  
```  
CMFCRibbonPanel* pPanel = pCategory->AddPanel (  
    _T("Clipboard"),                       // Panel name  
    m_PanelIcons.ExtractIcon (0));  // Panel icon  
// Create the first button ("Paste"):  
CMFCRibbonButton* pPasteButton =   
    new CMFCRibbonButton (ID_EDIT_PASTE, _T("Paste"), -1, 0);  
// The third parameter (-1) disables small images for button.  
// This button is always displayed with a large image  
// Associate a pop-up menu with the "Paste" button:  
pPasteButton->SetMenu (IDR_CONTEXT_MENU);  
// Add buttons to the panel. These buttons have only small images.  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_CUT, _T("Cut"), 1));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_COPY, _T("Copy"), 2));  
pPanel->Add (new CMFCRibbonButton (ID_EDIT_PAINT, _T("Paint"), 9));  
```  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
## Requisitos  
 **Encabezado:** afxribbonbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)