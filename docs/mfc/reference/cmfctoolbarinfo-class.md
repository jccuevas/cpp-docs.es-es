---
title: "CMFCToolBarInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarInfo class"
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMFCToolBarInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contiene los id. de recurso de las imágenes de la barra de herramientas en estados diferentes.  `CMFCToolBarInfo` es una clase auxiliar que se utiliza como parámetro del método de [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md) .  
  
## Sintaxis  
  
```  
class CMFCToolBarInfo  
```  
  
## Members  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarInfo::m\_uiColdResID](../Topic/CMFCToolBarInfo::m_uiColdResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes \(en frío\) normales de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiDisabledResID](../Topic/CMFCToolBarInfo::m_uiDisabledResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes deshabilitadas de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiHotResID](../Topic/CMFCToolBarInfo::m_uiHotResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes \(activo\) seleccionado de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiLargeColdResID](../Topic/CMFCToolBarInfo::m_uiLargeColdResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes grandes, normal de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiLargeDisabledResID](../Topic/CMFCToolBarInfo::m_uiLargeDisabledResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes grandes, deshabilitadas de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiLargeHotResID](../Topic/CMFCToolBarInfo::m_uiLargeHotResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes grandes, seleccionado de la barra de herramientas.|  
|[CMFCToolBarInfo::m\_uiMenuDisabledResID](../Topic/CMFCToolBarInfo::m_uiMenuDisabledResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes deshabilitadas de menú.|  
|[CMFCToolBarInfo::m\_uiMenuResID](../Topic/CMFCToolBarInfo::m_uiMenuResID.md)|Id. de recurso de mapa de bits de la barra de herramientas que contiene imágenes de menú.|  
  
## Comentarios  
 Un mapa de bits completo de la barra de herramientas consta de las pequeñas imágenes de la barra de herramientas \(botones\) de un tamaño fijo.  Cada Id. de recurso que se almacenan en un objeto de `CMFCToolBarInfo` es un mapa de bits que contiene un conjunto completo de imágenes de la barra de herramientas en una sola estado \(por ejemplo, las imágenes seleccionadas, deshabilitadas, grandes, o en el menú\).  
  
## Jerarquía de herencia  
 [CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)   
 [CMFCToolBar::LoadToolBarEx](../Topic/CMFCToolBar::LoadToolBarEx.md)