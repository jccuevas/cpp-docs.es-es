---
title: "CMFCRibbonCheckBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonCheckBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonCheckBox class"
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCRibbonCheckBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCRibbonCheckBox` implementa una casilla que se puede agregar a un menú emergente, a la barra de herramientas de acceso rápido o al panel de cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonCheckBox : public CMFCRibbonButton  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](../Topic/CMFCRibbonCheckBox::CMFCRibbonCheckBox.md)|El constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCheckBox::GetCompactSize](../Topic/CMFCRibbonCheckBox::GetCompactSize.md)|\(Invalida [CMFCRibbonButton::GetCompactSize](../Topic/CMFCRibbonButton::GetCompactSize.md)\).|  
|[CMFCRibbonCheckBox::GetIntermediateSize](../Topic/CMFCRibbonCheckBox::GetIntermediateSize.md)|\(Invalida [CMFCRibbonButton::GetIntermediateSize](../Topic/CMFCRibbonButton::GetIntermediateSize.md)\).|  
|[CMFCRibbonCheckBox::GetRegularSize](../Topic/CMFCRibbonCheckBox::GetRegularSize.md)|\(Invalida [CMFCRibbonButton::GetRegularSize](../Topic/CMFCRibbonButton::GetRegularSize.md)\).|  
|[CMFCRibbonCheckBox::IsDrawTooltipImage](../Topic/CMFCRibbonCheckBox::IsDrawTooltipImage.md)|\(Invalida `CMFCRibbonButton::IsDrawTooltipImage`\).|  
|[CMFCRibbonCheckBox::OnDraw](../Topic/CMFCRibbonCheckBox::OnDraw.md)|\(Invalida [CMFCRibbonButton::OnDraw](../Topic/CMFCRibbonButton::OnDraw.md)\).|  
|[CMFCRibbonCheckBox::OnDrawMenuImage](../Topic/CMFCRibbonCheckBox::OnDrawMenuImage.md)|\(Invalida [CMFCRibbonBaseElement::OnDrawMenuImage](../Topic/CMFCRibbonBaseElement::OnDrawMenuImage.md)\).|  
|[CMFCRibbonCheckBox::OnDrawOnList](../Topic/CMFCRibbonCheckBox::OnDrawOnList.md)|\(Invalida `CMFCRibbonButton::OnDrawOnList`\).|  
|[CMFCRibbonCheckBox::SetACCData](../Topic/CMFCRibbonCheckBox::SetACCData.md)|\(Invalida [CMFCRibbonButton::SetACCData](../Topic/CMFCRibbonButton::SetACCData.md)\).|  
  
## Comentarios  
 Para usar un elemento `CMFCRibbonCheckBox` en su aplicación, agregue el siguiente constructor al código:  
  
```  
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)  
```  
  
 `nID` es el identificador de comando de la casilla y `lpszText` la etiqueta de texto de la casilla.  
  
 Para agregar una casilla a un panel de cinta de opciones, use [CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)  
  
## Requisitos  
 **Encabezado:** afxribboncheckbox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonPanel Class](../../mfc/reference/cmfcribbonpanel-class.md)