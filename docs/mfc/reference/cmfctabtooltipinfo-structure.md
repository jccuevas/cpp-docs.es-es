---
title: "CMFCTabToolTipInfo Structure | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabToolTipInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabToolTipInfo struct"
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CMFCTabToolTipInfo Structure
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta estructura proporciona información sobre la ficha MDI que el usuario mantiene el mouse sobre.  
  
## Sintaxis  
  
```  
struct CMFCTabToolTipInfo  
```  
  
## Members  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTabToolTipInfo::m\_nTabIndex](../Topic/CMFCTabToolTipInfo::m_nTabIndex.md)|Especifica el índice del control de ficha.|  
|[CMFCTabToolTipInfo::m\_pTabWnd](../Topic/CMFCTabToolTipInfo::m_pTabWnd.md)|Un puntero al control de ficha.|  
|[CMFCTabToolTipInfo::m\_strText](../Topic/CMFCTabToolTipInfo::m_strText.md)|Texto de la información sobre herramientas.|  
  
## Comentarios  
 Un puntero a una estructura de `CMFCTabToolTipInfo` se pasa como parámetro del mensaje de `AFX_WM_ON_GET_TAB_TOOLTIP` .  Se genera este mensaje cuando se habilitan las fichas MDI y el puntero del mouse del usuario sobre un control de ficha.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo `CMFCTabToolTipInfo` se utiliza en [ejemplo de MDITabsDemo: MFC con la aplicación MDI](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/CPP/cmfctabtooltipinfo-structure_1.cpp)]  
  
## Jerarquía de herencia  
 [CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)  
  
## Requisitos  
 **encabezado:** afxbasetabctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMDIFrameWndEx::EnableMDITabs](../Topic/CMDIFrameWndEx::EnableMDITabs.md)   
 [CMDITabInfo::m\_bTabCustomTooltips](../Topic/CMDITabInfo::m_bTabCustomTooltips.md)