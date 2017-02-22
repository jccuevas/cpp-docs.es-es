---
title: "CMFCToolTipCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolTipCtrl class"
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una implementación de información sobre herramientas extendida, basada en la [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md).  Una información sobre herramientas basada en la clase `CMFCToolTipCtrl` puede mostrar un icono, una etiqueta y una descripción.  Puede personalizar su apariencia visual mediante un relleno de degradado, colores de texto y bordes personalizados, texto en negrita, esquinas redondeadas o un estilo de globo.  
  
## Sintaxis  
  
```  
class CMFCToolTipCtrl : public CToolTipCtrl  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolTipCtrl::GetIconSize](../Topic/CMFCToolTipCtrl::GetIconSize.md)|Devuelve el tamaño de un icono en una información sobre herramientas.|  
|[CMFCToolTipCtrl::GetParams](../Topic/CMFCToolTipCtrl::GetParams.md)|Devuelve la configuración de visualización en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawBorder](../Topic/CMFCToolTipCtrl::OnDrawBorder.md)|Dibuja el borde de una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawDescription](../Topic/CMFCToolTipCtrl::OnDrawDescription.md)||  
|[CMFCToolTipCtrl::OnDrawIcon](../Topic/CMFCToolTipCtrl::OnDrawIcon.md)|Muestra un icono en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnDrawLabel](../Topic/CMFCToolTipCtrl::OnDrawLabel.md)|Dibuja la etiqueta de una información sobre herramientas o calcula el tamaño de la etiqueta.|  
|[CMFCToolTipCtrl::OnDrawSeparator](../Topic/CMFCToolTipCtrl::OnDrawSeparator.md)|Dibuja el separador entre la etiqueta y la descripción en una información sobre herramientas.|  
|[CMFCToolTipCtrl::OnFillBackground](../Topic/CMFCToolTipCtrl::OnFillBackground.md)|Rellena el fondo de la información sobre herramientas.|  
|[CMFCToolTipCtrl::SetDescription](../Topic/CMFCToolTipCtrl::SetDescription.md)|Establece la descripción que se mostrará en la información sobre herramientas.|  
|[CMFCToolTipCtrl::SetFixedWidth](../Topic/CMFCToolTipCtrl::SetFixedWidth.md)||  
|[CMFCToolTipCtrl::SetHotRibbonButton](../Topic/CMFCToolTipCtrl::SetHotRibbonButton.md)||  
|[CMFCToolTipCtrl::SetLocation](../Topic/CMFCToolTipCtrl::SetLocation.md)||  
|[CMFCToolTipCtrl::SetParams](../Topic/CMFCToolTipCtrl::SetParams.md)|Especifica la apariencia visual de una información sobre herramientas con un objeto `CMFCToolTipInfo`.|  
  
## Comentarios  
 Use los objetos `CMFCToolTipCtrl`, `CMFCToolTipInfo` y [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md) de forma conjunta para implementar las informaciones sobre herramientas personalizadas en una aplicación.  
  
 Por ejemplo, para usar informaciones sobre herramientas con estilo de globo, siga estos pasos:  
  
 1.  Use el método [CWinAppEx Class](../../mfc/reference/cwinappex-class.md) para inicializar el administrador de informaciones sobre herramientas de la aplicación.  
  
 2.  Cree una estructura `CMFCToolTipInfo` para especificar el estilo visual que desee:  
  
```  
CMFCToolTipInfo params;  
 params.m_bBoldLabel = FALSE;  
 params.m_bDrawDescription = FALSE;  
 params.m_bDrawIcon = FALSE;  
 params.m_bRoundedCorners = TRUE;  
 params.m_bDrawSeparator = FALSE;  
 if (m_bCustomColors)  
 {  
  params.m_clrFill = RGB (255, 255, 255);  
  params.m_clrFillGradient = RGB (228, 228, 240);  
  params.m_clrText = RGB (61, 83, 80);  
  params.m_clrBorder = RGB (144, 149, 168);  
 }  
```  
  
 3.  Use el método [CTooltipManager::SetTooltipParams](../Topic/CTooltipManager::SetTooltipParams.md) para establecer el estilo visual de todas las informaciones sobre herramientas de la aplicación con los estilos definidos en el objeto `CMFCToolTipInfo`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);  
```  
  
 También puede derivar una clase nueva de `CMFCToolTipCtrl` para controlar la representación y el comportamiento de la información sobre herramientas.  Para especificar una nueva clase de control de información sobre herramientas, use el método `CTooltipManager::SetTooltipParams`:  
  
```  
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    RUNTIME_CLASS (CMyToolTipCtrl))  
```  
  
 Para restaurar la clase de control predeterminada de información sobre herramientas y restablecer la apariencia de esta información a su estado predeterminado, especifique NULL en los parámetros de información sobre herramientas y de información de clase en tiempo de ejecución de `SetTooltipParams`:  
  
```  
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,  
    NULL, NULL);  
```  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCToolTipCtrl`, se establece la descripción que se muestra en la información sobre herramientas y se establece también el ancho del control de esta información.  
  
 [!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/CPP/cmfctooltipctrl-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)  
  
 [CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)  
  
## Requisitos  
 **Encabezado:** afxtooltipctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)   
 [CTooltipManager Class](../../mfc/reference/ctooltipmanager-class.md)   
 [CMFCToolTipInfo Class](../../mfc/reference/cmfctooltipinfo-class.md)   
 [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)