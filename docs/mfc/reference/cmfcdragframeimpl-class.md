---
title: "CMFCDragFrameImpl Class | Microsoft Docs"
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
  - "CMFCDragFrameImpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCDragFrameImpl class"
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
caps.latest.revision: 26
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCDragFrameImpl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCDragFrameImpl` dibuja el rectángulo de arrastre que aparece cuando el usuario arrastra un panel en modo estándar de vinculación.  
  
## Sintaxis  
  
```  
class CMFCDragFrameImpl  
```  
  
## Comentarios  
 Un objeto de esta clase se inserta en cada objeto de [CPane Class](../../mfc/reference/cpane-class.md) .  Así, cada panel que utiliza el método de `CanFloat` muestra un rectángulo de arrastre cuando el usuario lo arrastra.  
  
 Puede controlar el grosor del rectángulo de arrastre mediante [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessFloat](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat.md) y [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessDock](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock.md).  
  
## Jerarquía de herencia  
 [CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)  
  
## Requisitos  
 **encabezado:** afxdragframeimpl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessFloat](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat.md)   
 [AFX\_GLOBAL\_DATA::m\_nDragFrameThicknessDock](../Topic/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock.md)