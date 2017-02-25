---
title: "CMFCVisualManagerVS2005 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerVS2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerVS2005 class"
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCVisualManagerVS2005 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerVS2005` da a la aplicación un aspecto de Microsoft Visual Studio 2005.  
  
## Sintaxis  
  
```  
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetDockingTabsBordersSize.md)|El marco de trabajo llama a este método cuando dibuja un panel acoplado y tabulado.  \(Reemplaza [CMFCVisualManager::GetDockingTabsBordersSize](../Topic/CMFCVisualManager::GetDockingTabsBordersSize.md).\)|  
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetMDITabsBordersSize.md)|El marco de trabajo llama a este método para determinar el tamaño del borde de una ventana de MDITabs antes de que dibuja la ventana.  \(Reemplaza [CMFCVisualManager::GetMDITabsBordersSize](../Topic/CMFCVisualManager::GetMDITabsBordersSize.md).\)|  
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerVS2005::GetPropertyGridGroupColor.md)|\(Reemplaza [CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md).\)|  
|[CMFCVisualManagerVS2005::GetTabFrameColors](../Topic/CMFCVisualManagerVS2005::GetTabFrameColors.md)|\(Reemplaza [CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md).\)|  
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons.md)|Devuelve si ocultar automáticamente los botones se superponen en el administrador visual actual.  \(Reemplaza [CMFCVisualManager::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManager::HasOverlappedAutoHideButtons.md).\)|  
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md).\)|  
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](../Topic/CMFCVisualManagerVS2005::OnDrawCaptionButton.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`.\)|  
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](../Topic/CMFCVisualManagerVS2005::OnDrawPaneCaption.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md).\)|  
|[CMFCVisualManagerVS2005::OnDrawSeparator](../Topic/CMFCVisualManagerVS2005::OnDrawSeparator.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md).\)|  
|[CMFCVisualManagerVS2005::OnDrawTab](../Topic/CMFCVisualManagerVS2005::OnDrawTab.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md).\)|  
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](../Topic/CMFCVisualManagerVS2005::OnDrawToolBoxFrame.md)|\(Reemplaza [CMFCVisualManager::OnDrawToolBoxFrame](../Topic/CMFCVisualManager::OnDrawToolBoxFrame.md).\)|  
|[CMFCVisualManagerVS2005::OnEraseTabsArea](../Topic/CMFCVisualManagerVS2005::OnEraseTabsArea.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md).\)|  
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md).\)|  
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](../Topic/CMFCVisualManagerVS2005::OnFillHighlightedArea.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md).\)|  
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerVS2005::OnFillMiniFrameCaption.md)|\(Reemplaza `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`.\)|  
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](../Topic/CMFCVisualManagerVS2005::OnUpdateSystemColors.md)|\(Reemplaza [CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md).\)|  
  
## Comentarios  
 Utiliza la clase CMFCVisualManagerVS2005 para cambiar la apariencia visual de la aplicación para ser similar al de [!INCLUDE[vsprvsext](../../mfc/reference/includes/vsprvsext_md.md)].  
  
 Todos los miembros de esta clase son funciones virtuales que son derivadas de antecesores de esta clase, [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar el administrador visual VS 2005.  Este fragmento de código es parte de [Ejemplo de demostración de alerta de escritorio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagervs2005-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
 [CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)  
  
## Requisitos  
 **encabezado:** afxvisualmanagervs2005.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManagerOffice2003 Class](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)