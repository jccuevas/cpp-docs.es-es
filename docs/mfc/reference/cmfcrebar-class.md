---
title: "CMFCReBar Class | Microsoft Docs"
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
  - "CMFCReBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCReBar class"
ms.assetid: 02a60e29-6224-49c1-9e74-e0a7d9f8d023
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCReBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un objeto de `CMFCReBar` es una barra de control que proporciona el diseño, persistencia, e información de estado del rebar controla.  
  
## Sintaxis  
  
```  
class CMFCReBar : public CPane  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCReBar::AddBar](../Topic/CMFCReBar::AddBar.md)|Agrega una banda un rebar.|  
|[CMFCReBar::CalcFixedLayout](../Topic/CMFCReBar::CalcFixedLayout.md)|\(Reemplaza [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md).\)|  
|[CMFCReBar::CanFloat](../Topic/CMFCReBar::CanFloat.md)|\(Reemplaza [CBasePane::CanFloat](../Topic/CBasePane::CanFloat.md).\)|  
|[CMFCReBar::Create](../Topic/CMFCReBar::Create.md)|Crea el control rebar y lo asocia al objeto de `CMFCReBar` .|  
|[CMFCReBar::EnableDocking](../Topic/CMFCReBar::EnableDocking.md)|\(Reemplaza [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md).\)|  
|[CMFCReBar::GetReBarBandInfoSize](../Topic/CMFCReBar::GetReBarBandInfoSize.md)||  
|[CMFCReBar::GetReBarCtrl](../Topic/CMFCReBar::GetReBarCtrl.md)|Proporciona acceso directo al control común subyacente de [CReBarCtrl](../../mfc/reference/crebarctrl-class.md) .|  
|[CMFCReBar::OnShowControlBarMenu](../Topic/CMFCReBar::OnShowControlBarMenu.md)|\(Reemplaza [CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md).\)|  
|[CMFCReBar::OnToolHitTest](../Topic/CMFCReBar::OnToolHitTest.md)|\(Reemplaza [CWnd::OnToolHitTest](../Topic/CWnd::OnToolHitTest.md).\)|  
|[CMFCReBar::OnUpdateCmdUI](../Topic/CMFCReBar::OnUpdateCmdUI.md)|\(Reemplaza [CBasePane::OnUpdateCmdUI](http://msdn.microsoft.com/es-es/e139f06a-9793-4ee2-bc3d-517389368c77).\)|  
|[CMFCReBar::SetPaneAlignment](../Topic/CMFCReBar::SetPaneAlignment.md)|\(Reemplaza [CBasePane::SetPaneAlignment](../Topic/CBasePane::SetPaneAlignment.md).\)|  
  
## Comentarios  
 Un objeto de `CMFCReBar` puede contener una variedad de ventanas secundarias.  Esto incluye los cuadros de edición, barras de herramientas, y los cuadros de lista.  Puede cambiar el tamaño del rebar mediante programación, o el usuario puede cambiar manualmente el tamaño del rebar arrastrando su barra de.  También puede establecer el fondo de un objeto rebar en un mapa de bits de su elección.  
  
 Un objeto rebar se comporta de forma similar a un objeto de la barra de herramientas.  Un control rebar puede contener una o más bandas, y cada banda puede contener una barra de agarrador, un mapa de bits, una etiqueta de texto, y una ventana secundaria.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCReBar` .  El ejemplo muestra cómo crear un control rebar y agregar una banda cuando.  Las funciones de banda como una barra de herramientas interna.  Este fragmento de código es parte de [Ejemplo del Rebar](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_RebarTest#1](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_1.h)]  
[!code-cpp[NVC_MFC_RebarTest#2](../../mfc/reference/codesnippet/CPP/cmfcrebar-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CMFCReBar](../../mfc/reference/cmfcrebar-class.md)  
  
## Requisitos  
 **encabezado:** afxRebar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CReBarCtrl Class](../../mfc/reference/crebarctrl-class.md)   
 [CPane Class](../../mfc/reference/cpane-class.md)