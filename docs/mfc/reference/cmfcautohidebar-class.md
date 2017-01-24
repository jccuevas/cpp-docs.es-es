---
title: "CMFCAutoHideBar Class | Microsoft Docs"
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
  - "CMFCAutoHideBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideToolBar class"
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: 35
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCAutoHideBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CMFCAutoHideBar` es una clase especial de la barra de herramientas que implementa la característica Ocultar automáticamente.  
  
## Sintaxis  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](../Topic/CMFCAutoHideBar::CMFCAutoHideBar.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](../Topic/CMFCAutoHideBar::AddAutoHideWindow.md)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](../Topic/CMFCAutoHideBar::AllowShowOnPaneMenu.md)|\(Reemplaza a `CPane::AllowShowOnPaneMenu`\).|  
|[CMFCAutoHideBar::CalcFixedLayout](../Topic/CMFCAutoHideBar::CalcFixedLayout.md)|\(Reemplaza a [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\).|  
|[CMFCAutoHideBar::Create](../Topic/CMFCAutoHideBar::Create.md)|Crea una barra de control y la adjunta al objeto [CPane](../../mfc/reference/cpane-class.md).  \(Reemplaza a [CPane::Create](../Topic/CPane::Create.md)\).|  
|[CMFCAutoHideBar::GetFirstAHWindow](../Topic/CMFCAutoHideBar::GetFirstAHWindow.md)||  
|[CMFCAutoHideBar::GetVisibleCount](../Topic/CMFCAutoHideBar::GetVisibleCount.md)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](../Topic/CMFCAutoHideBar::OnShowControlBarMenu.md)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial.  \(Reemplaza a [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)\).|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](../Topic/CMFCAutoHideBar::RemoveAutoHideWindow.md)||  
|[CMFCAutoHideBar::SetActiveInGroup](../Topic/CMFCAutoHideBar::SetActiveInGroup.md)|\(Reemplaza a [CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)\).|  
|[CMFCAutoHideBar::SetRecentVisibleState](../Topic/CMFCAutoHideBar::SetRecentVisibleState.md)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](../Topic/CMFCAutoHideBar::ShowAutoHideWindow.md)||  
|[CMFCAutoHideBar::StretchPane](../Topic/CMFCAutoHideBar::StretchPane.md)|Expande un panel vertical u horizontalmente.  \(Reemplaza a [CBasePane::StretchPane](../Topic/CBasePane::StretchPane.md)\).|  
|[CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md)||  
|[CMFCAutoHideBar::UpdateVisibleState](../Topic/CMFCAutoHideBar::UpdateVisibleState.md)||  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CMFCAutoHideBar::m\_nShowAHWndDelay](../Topic/CMFCAutoHideBar::m_nShowAHWndDelay.md)|El tiempo de retraso entre el momento en que el usuario coloca el cursor del mouse sobre una [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md) y el momento en que el marco muestra la ventana asociada.|  
  
## Comentarios  
 Cuando el usuario cambia un panel de acoplamiento a modo de ocultación automática, el marco crea automáticamente un objeto `CMFCAutoHideBar`.  También crea los objetos necesarios [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) y [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md).  Cada objeto `CAutoHideDockSite` está asociado a un `CMFCAutoHideButton` individual.  
  
 La clase `CMFCAutoHideBar` implementa la presentación de un `CAutoHideDockSite` cuando el mouse de un usuario se mantiene sobre un `CMFCAutoHideButton`.  Cuando la barra de herramientas recibe un mensaje WM\_MOUSEMOVE, `CMFCAutoHideBar` inicia un temporizador.  Cuando el temporizador finaliza, envía a la barra de herramientas una notificación de evento WM\_TIMER.  Para controlar este evento, la barra de herramientas comprueba si el puntero del mouse está situado sobre el mismo botón de ocultación automática que cuando se inició el temporizador.  Si es así, se muestra el objeto `CAutoHideDockSite` adjunto.  
  
 Para controlar la duración del retraso del temporizador, defina `m_nShowAHWndDelay`.  El valor predeterminado es de 400 ms.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAutoHideBar` y usar su método `GetDockSiteRow`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/CPP/cmfcautohidebar-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## Requisitos  
 **Encabezado:** afxautohidebar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md)