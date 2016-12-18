---
title: "CMFCRibbonMiniToolBar Class | Microsoft Docs"
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
  - "CMFCRibbonMiniToolBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonMiniToolBar class"
ms.assetid: 7017e963-aeaf-4fe9-b540-e15a7ed41e94
caps.latest.revision: 24
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCRibbonMiniToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una barra de herramientas emergente contextual.  
  
## Sintaxis  
  
```  
class CMFCRibbonMiniToolBar : public CMFCRibbonPanelMenu  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CMFCRibbonMiniToolBar`|Constructor predeterminado.|  
|`CMFCRibbonMiniToolBar::~CMFCRibbonMiniToolBar`|Destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCRibbonMiniToolBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|`CMFCRibbonMiniToolBar::GetThisClass`|Usado por el marco para obtener un puntero al objeto [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) asociado a este tipo de clase.|  
|[CMFCRibbonMiniToolBar::IsContextMenuMode](../Topic/CMFCRibbonMiniToolBar::IsContextMenuMode.md)||  
|[CMFCRibbonMiniToolBar::IsRibbonMiniToolBar](../Topic/CMFCRibbonMiniToolBar::IsRibbonMiniToolBar.md)|\(Invalida `CMFCPopupMenu::IsRibbonMiniToolBar`\).|  
|[CMFCRibbonMiniToolBar::SetCommands](../Topic/CMFCRibbonMiniToolBar::SetCommands.md)|Establece la lista de comandos que se mostrarán en la barra de herramientas.|  
|[CMFCRibbonMiniToolBar::Show](../Topic/CMFCRibbonMiniToolBar::Show.md)|Muestra la minibarra de herramientas en las coordenadas de pantalla especificadas.|  
|[CMFCRibbonMiniToolBar::ShowWithContextMenu](../Topic/CMFCRibbonMiniToolBar::ShowWithContextMenu.md)|Muestra la minibarra de herramientas junto con un menú contextual.|  
  
## Comentarios  
 La minibarra de herramientas se muestra normalmente cuando el usuario selecciona un objeto en un documento.  Por ejemplo, cuando el usuario selecciona un bloque de texto en un procesador de textos, la aplicación muestra una minibarra de herramientas que contiene los comandos de formato de texto.  
  
 La minibarra de herramientas se hace transparente cuando el puntero del mouse está fuera de los límites de la minibarra.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 `CMFCRibbonPanelMenu`  
  
 [CMFCRibbonMiniToolBar](../../mfc/reference/cmfcribbonminitoolbar-class.md)  
  
## Requisitos  
 **Encabezado:** afxRibbonMiniToolBar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)