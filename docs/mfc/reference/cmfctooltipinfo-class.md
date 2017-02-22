---
title: "CMFCToolTipInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipInfo class"
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCToolTipInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Almacena información sobre el aspecto visual de la información sobre herramientas.  
  
## Sintaxis  
  
```  
class CMFCToolTipInfo  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolTipInfo::operator\=](../Topic/CMFCToolTipInfo::operator=.md)||  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCToolTipInfo::m\_bBalloonTooltip](../Topic/CMFCToolTipInfo::m_bBalloonTooltip.md)|Variable booleana que indica si la información sobre herramientas tiene apariencia de globo.|  
|[CMFCToolTipInfo::m\_bBoldLabel](../Topic/CMFCToolTipInfo::m_bBoldLabel.md)|Variable booleana que indica si las etiquetas de información sobre herramientas se muestran en negrita.|  
|[CMFCToolTipInfo::m\_bDrawDescription](../Topic/CMFCToolTipInfo::m_bDrawDescription.md)|Variable booleana que indica si la información sobre herramientas contiene una descripción.|  
|[CMFCToolTipInfo::m\_bDrawIcon](../Topic/CMFCToolTipInfo::m_bDrawIcon.md)|Variable booleana que indica si la información sobre herramientas contiene un icono.|  
|[CMFCToolTipInfo::m\_bDrawSeparator](../Topic/CMFCToolTipInfo::m_bDrawSeparator.md)|Variable booleana que indica si se muestra un separador entre la etiqueta de información sobre herramientas y la descripción de la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_bRoundedCorners](../Topic/CMFCToolTipInfo::m_bRoundedCorners.md)|Variable booleana que indica si la información sobre herramientas tiene esquinas redondeadas.|  
|[CMFCToolTipInfo::m\_bVislManagerTheme](../Topic/CMFCToolTipInfo::m_bVislManagerTheme.md)|Variable booleana que indica si la apariencia de la información sobre herramientas debe controlarse mediante un administrador visual \(vea [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)\).|  
|[CMFCToolTipInfo::m\_clrBorder](../Topic/CMFCToolTipInfo::m_clrBorder.md)|Color del borde de la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_clrFill](../Topic/CMFCToolTipInfo::m_clrFill.md)|Color del fondo de la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_clrFillGradient](../Topic/CMFCToolTipInfo::m_clrFillGradient.md)|Color del relleno de degradado en la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_clrText](../Topic/CMFCToolTipInfo::m_clrText.md)|Color del texto en la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_nGradientAngle](../Topic/CMFCToolTipInfo::m_nGradientAngle.md)|Ángulo del relleno de degradado en la información sobre herramientas.|  
|[CMFCToolTipInfo::m\_nMaxDescrWidth](../Topic/CMFCToolTipInfo::m_nMaxDescrWidth.md)|Ancho máximo posible, en píxeles, de la descripción en la información sobre herramientas.|  
  
## Comentarios  
 Use [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md), `CMFCToolTipInfo` y [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) juntos para implementar información sobre herramientas personalizada en su aplicación.  Para ver un ejemplo de cómo usar estas clases de información sobre herramientas, vea el tema [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer los valores de las distintas variables de miembro en la clase `CMFCToolTipInfo`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/CPP/cmfctooltipinfo-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)  
  
## Requisitos  
 **Encabezado:** afxtooltipctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipCtrl Class](../../mfc/reference/cmfctooltipctrl-class.md)