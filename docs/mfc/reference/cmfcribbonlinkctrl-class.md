---
title: "CMFCRibbonLinkCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonLinkCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonLinkCtrl class"
ms.assetid: 77ae1941-e0ab-4a9d-911e-1752d34c079b
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCRibbonLinkCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un hipervínculo que se coloca en una cinta.  El hipervínculo abre una página web cuando se hace clic en él.  
  
## Sintaxis  
  
```  
class CMFCRibbonLinkCtrl : public CMFCRibbonButton  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl](../Topic/CMFCRibbonLinkCtrl::CMFCRibbonLinkCtrl.md)|Construye e inicializa un objeto `CMFCRibbonLinkCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonLinkCtrl::CopyFrom](../Topic/CMFCRibbonLinkCtrl::CopyFrom.md)|\(Invalida `CMFCRibbonButton::CopyFrom`\).|  
|[CMFCRibbonLinkCtrl::GetCompactSize](../Topic/CMFCRibbonLinkCtrl::GetCompactSize.md)|\(Invalida [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)\).|  
|[CMFCRibbonLinkCtrl::GetLink](../Topic/CMFCRibbonLinkCtrl::GetLink.md)|Devuelve el valor del hipervínculo.|  
|[CMFCRibbonLinkCtrl::GetRegularSize](../Topic/CMFCRibbonLinkCtrl::GetRegularSize.md)|\(Invalida [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)\).|  
|[CMFCRibbonLinkCtrl::GetToolTipText](../Topic/CMFCRibbonLinkCtrl::GetToolTipText.md)|\(Invalida [CMFCRibbonButton::GetToolTipText](../Topic/CMFCRibbonButton::GetToolTipText.md)\).|  
|[CMFCRibbonLinkCtrl::IsDrawTooltipImage](../Topic/CMFCRibbonLinkCtrl::IsDrawTooltipImage.md)|\(Invalida `CMFCRibbonButton::IsDrawTooltipImage`\).|  
|[CMFCRibbonLinkCtrl::OnDraw](../Topic/CMFCRibbonLinkCtrl::OnDraw.md)|\(Invalida [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)\).|  
|[CMFCRibbonLinkCtrl::OnDrawMenuImage](../Topic/CMFCRibbonLinkCtrl::OnDrawMenuImage.md)|\(Invalida [CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)\).|  
|[CMFCRibbonLinkCtrl::OnMouseMove](../Topic/CMFCRibbonLinkCtrl::OnMouseMove.md)|\(Invalida `CMFCRibbonButton::OnMouseMove`\).|  
|[CMFCRibbonLinkCtrl::OnSetIcon](../Topic/CMFCRibbonLinkCtrl::OnSetIcon.md)||  
|[CMFCRibbonLinkCtrl::OpenLink](../Topic/CMFCRibbonLinkCtrl::OpenLink.md)|Se abre la página web especificada en el hipervínculo.|  
|[CMFCRibbonLinkCtrl::SetLink](../Topic/CMFCRibbonLinkCtrl::SetLink.md)|Establece el valor del hipervínculo.|  
  
## Comentarios  
 Después de crear un hipervínculo, agréguelo a un panel llamando a [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) [CMFCRibbonLinkCtrl](../../mfc/reference/cmfcribbonlinkctrl-class.md)  
  
## Requisitos  
 **Encabezado:** afxRibbonLinkCtrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton Class](../../mfc/reference/cmfcribbonbutton-class.md)