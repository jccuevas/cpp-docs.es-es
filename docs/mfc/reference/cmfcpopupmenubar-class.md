---
title: "CMFCPopupMenuBar (clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPopupMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenuBar (clase)"
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
caps.latest.revision: 32
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 34
---
# CMFCPopupMenuBar (clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una barra de menús inline en un menú emergente.  
  
## Sintaxis  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## Members  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](../Topic/CMFCPopupMenuBar::AdjustSizeImmediate.md)|Inmediatamente actualiza el diseño de un panel.  \(Reemplaza [CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md).\)|  
|[CMFCPopupMenuBar::BuildOrigItems](../Topic/CMFCPopupMenuBar::BuildOrigItems.md)|Carga elementos de menú emergente del recurso especificado en el menú.|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](../Topic/CMFCPopupMenuBar::CloseDelayedSubMenu.md)|Cierra un botón retrasada de menú emergente.|  
|[CMFCPopupMenuBar::ExportToMenu](../Topic/CMFCPopupMenuBar::ExportToMenu.md)|Compila un menú de los botones de menú emergente.|  
|[CMFCPopupMenuBar::FindDestintationToolBar](../Topic/CMFCPopupMenuBar::FindDestintationToolBar.md)|Busque la barra de herramientas donde se encuentra un punto especificado.|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](../Topic/CMFCPopupMenuBar::GetCurrentMenuImageSize.md)|Indica el tamaño de las imágenes de botón de menú.|  
|[CMFCPopupMenuBar::GetDefaultMenuId](../Topic/CMFCPopupMenuBar::GetDefaultMenuId.md)|Devuelve el identificador del elemento de menú predeterminado.|  
|[CMFCPopupMenuBar::GetLastCommandIndex](../Topic/CMFCPopupMenuBar::GetLastCommandIndex.md)|Obtiene el índice del comando de menú recientemente invocado.|  
|[CMFCPopupMenuBar::GetOffset](../Topic/CMFCPopupMenuBar::GetOffset.md)|Obtiene el desplazamiento de la fila de la barra de menú emergente.|  
|[CMFCPopupMenuBar::ImportFromMenu](../Topic/CMFCPopupMenuBar::ImportFromMenu.md)|Importa los botones de menú emergente de un menú especificado.|  
|[CMFCPopupMenuBar::IsDropDownListMode](../Topic/CMFCPopupMenuBar::IsDropDownListMode.md)|Indica si la barra de menú emergente está en modo de la lista desplegable.|  
|[CMFCPopupMenuBar::IsPaletteMode](../Topic/CMFCPopupMenuBar::IsPaletteMode.md)|Indica si la barra de menú emergente está en modo de la paleta.|  
|[CMFCPopupMenuBar::IsRibbonPanel](../Topic/CMFCPopupMenuBar::IsRibbonPanel.md)|Indica si se trata de un panel de la cinta \(`FALSE` de forma predeterminada\).|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](../Topic/CMFCPopupMenuBar::IsRibbonPanelInRegularMode.md)|Indica si se trata de un panel de cinta de opciones en el modo normal \(`FALSE` de forma predeterminada\).|  
|[CMFCPopupMenuBar::LoadFromHash](../Topic/CMFCPopupMenuBar::LoadFromHash.md)|Carga un menú almacenado.|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](../Topic/CMFCPopupMenuBar::RestoreDelayedSubMenu.md)|Restaurar un botón de menú retrasada para cerrar la barra de menú emergente.|  
|[CMFCPopupMenuBar::SetButtonStyle](../Topic/CMFCPopupMenuBar::SetButtonStyle.md)|Establece el estilo de botón de la barra de herramientas en el índice especificado.  \(Reemplaza [CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md).\)|  
|[CMFCPopupMenuBar::SetOffset](../Topic/CMFCPopupMenuBar::SetOffset.md)|Establece el desplazamiento de la fila de la barra de menú emergente.|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](../Topic/CMFCPopupMenuBar::StartPopupMenuTimer.md)|Inicia el temporizador para un botón retrasada especificado del elemento emergente.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCPopupMenuBar::m\_bDisableSideBarInXPMode](../Topic/CMFCPopupMenuBar::m_bDisableSideBarInXPMode.md)|Especifica si la barra lateral deshabilitada se mostrará cuando la aplicación tiene un aspecto de Windows XP.|  
  
## Comentarios  
 `CMFCPopupMenuBar` se crea al mismo tiempo que [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) y se incrusta dentro de.  `CMFCPopupMenuBar` cubre el área cliente completa del objeto de `CMFCPopupMenu`.  Admite la entrada de teclado y mouse.  También comunica esa entrada a `CMFCPopupMenu` y en la ventana de nivel superior del cuadro.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo inicializar un objeto de `CMFCPopupMenuBar` de un objeto de `CMFCPopupMenu`.  Este fragmento de código es parte de [Ejemplo de cliente de dibujo](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/CPP/cmfcpopupmenubar-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## Requisitos  
 **Encabezado:** afxpopupmenubar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)