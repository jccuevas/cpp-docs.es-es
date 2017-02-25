---
title: "CMFCImageEditorPaletteBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImageEditorPaletteBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImageEditorPaletteBar class"
ms.assetid: 3fb7ba8e-f254-4d56-b913-9941b4ed8138
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMFCImageEditorPaletteBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona funcionalidad de la barra de la paleta en un cuadro de diálogo del editor de imágenes.  
  
## Sintaxis  
  
```  
class CMFCImageEditorPaletteBar : public CMFCToolBar  
```  
  
## Members  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCImageEditorPaletteBar::GetRowHeight](../Topic/CMFCImageEditorPaletteBar::GetRowHeight.md)|devuelve el alto de botones de la barra de herramientas.  \(Reemplaza [CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md).\)|  
|[CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable](../Topic/CMFCImageEditorPaletteBar::IsButtonExtraSizeAvailable.md)|Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos.  \(Reemplaza [CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md).\)|  
  
### Comentarios  
 Esta clase no está pensada para utilizarla directamente desde el código.  
  
 El marco de trabajo usa esta clase para mostrar una barra de la paleta en un cuadro de diálogo editor de imagen.  Para obtener más información sobre el cuadro de diálogo editor de imágenes, vea [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBa](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCImageEditorPaletteBar](../../mfc/reference/cmfcimageeditorpalettebar-class.md)  
  
## Requisitos  
 **encabezado:** afximageeditordialog.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)