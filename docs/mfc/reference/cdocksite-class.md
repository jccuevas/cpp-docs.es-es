---
title: "CDockSite Class | Microsoft Docs"
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
  - "CDockSite"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockSite class"
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
caps.latest.revision: 28
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Proporciona la funcionalidad para organizar los paneles que se derivan de la [CPane Class](../../mfc/reference/cpane-class.md) en conjuntos de filas.  
  
## Sintaxis  
  
```  
class CDockSite: public CBasePane  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockSite::AddRow](../Topic/CDockSite::AddRow.md)||  
|[CDockSite::AdjustDockingLayout](../Topic/CDockSite::AdjustDockingLayout.md)|\(Reemplaza a [CBasePane::AdjustDockingLayout](../Topic/CBasePane::AdjustDockingLayout.md)\).|  
|[CDockSite::AdjustLayout](../Topic/CDockSite::AdjustLayout.md)|\(Reemplaza a [CBasePane::AdjustLayout](../Topic/CBasePane::AdjustLayout.md)\).|  
|[CDockSite::AlignDockSite](../Topic/CDockSite::AlignDockSite.md)||  
|[CDockSite::CalcFixedLayout](../Topic/CDockSite::CalcFixedLayout.md)|\(Reemplaza a [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\).|  
|[CDockSite::CanAcceptPane](../Topic/CDockSite::CanAcceptPane.md)|\(Reemplaza a [CBasePane::CanAcceptPane](../Topic/CBasePane::CanAcceptPane.md)\).|  
|[CDockSite::CreateEx](../Topic/CDockSite::CreateEx.md)|\(Reemplaza a [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)\).|  
|[CDockSite::CreateRow](../Topic/CDockSite::CreateRow.md)||  
|[CDockSite::DockPane](../Topic/CDockSite::DockPane.md)|\(Reemplaza a [CBasePane::DockPane](../Topic/CBasePane::DockPane.md)\).|  
|[CDockSite::DoesAllowDynInsertBefore](../Topic/CDockSite::DoesAllowDynInsertBefore.md)|\(Reemplaza a [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)\).|  
|[CDockSite::FindRowIndex](../Topic/CDockSite::FindRowIndex.md)||  
|[CDockSite::FixupVirtualRects](../Topic/CDockSite::FixupVirtualRects.md)||  
|[CDockSite::GetDockSiteID](../Topic/CDockSite::GetDockSiteID.md)||  
|[CDockSite::GetDockSiteRowsList](../Topic/CDockSite::GetDockSiteRowsList.md)||  
|[CDockSite::IsAccessibilityCompatible](../Topic/CDockSite::IsAccessibilityCompatible.md)|\(Reemplaza a `CBasePane::IsAccessibilityCompatible`\).|  
|[CDockSite::IsDragMode](../Topic/CDockSite::IsDragMode.md)||  
|[CDockSite::IsLastRow](../Topic/CDockSite::IsLastRow.md)||  
|[CDockSite::IsRectWithinDockSite](../Topic/CDockSite::IsRectWithinDockSite.md)||  
|[CDockSite::IsResizable](../Topic/CDockSite::IsResizable.md)|\(Reemplaza a [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md)\).|  
|[CDockSite::MovePane](../Topic/CDockSite::MovePane.md)||  
|[CDockSite::OnInsertRow](../Topic/CDockSite::OnInsertRow.md)||  
|[CDockSite::OnRemoveRow](../Topic/CDockSite::OnRemoveRow.md)||  
|[CDockSite::OnResizeRow](../Topic/CDockSite::OnResizeRow.md)||  
|[CDockSite::OnSetWindowPos](../Topic/CDockSite::OnSetWindowPos.md)||  
|[CDockSite::OnShowRow](../Topic/CDockSite::OnShowRow.md)||  
|[CDockSite::OnSizeParent](../Topic/CDockSite::OnSizeParent.md)||  
|[CDockSite::PaneFromPoint](../Topic/CDockSite::PaneFromPoint.md)|Devuelve un panel que está acoplado en el sitio de vinculación en el punto especificado por el parámetro dado.|  
|[CDockSite::DockPaneLeftOf](../Topic/CDockSite::DockPaneLeftOf.md)|Acopla un panel a la izquierda de otro panel.|  
|[CDockSite::FindPaneByID](../Topic/CDockSite::FindPaneByID.md)|Devuelve el panel identificado por el identificador especificado.|  
|[CDockSite::GetPaneList](../Topic/CDockSite::GetPaneList.md)|Devuelve una lista de paneles acoplados en el sitio de vinculación.|  
|[CDockSite::RectSideFromPoint](../Topic/CDockSite::RectSideFromPoint.md)||  
|[CDockSite::RemovePane](../Topic/CDockSite::RemovePane.md)||  
|[CDockSite::RemoveRow](../Topic/CDockSite::RemoveRow.md)||  
|[CDockSite::ReplacePane](../Topic/CDockSite::ReplacePane.md)||  
|[CDockSite::RepositionPanes](../Topic/CDockSite::RepositionPanes.md)||  
|[CDockSite::ResizeDockSite](../Topic/CDockSite::ResizeDockSite.md)||  
|[CDockSite::ResizeRow](../Topic/CDockSite::ResizeRow.md)||  
|[CDockSite::ShowPane](../Topic/CDockSite::ShowPane.md)|Muestra el panel.|  
|[CDockSite::ShowRow](../Topic/CDockSite::ShowRow.md)||  
|[CDockSite::SwapRows](../Topic/CDockSite::SwapRows.md)||  
  
## Comentarios  
 El marco de trabajo crea objetos `CDockSite` automáticamente al llamar a [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md).  Las ventanas del sitio de vinculación están colocadas en el borde del área de cliente de la ventana de marco principal.  
  
 Normalmente no es necesario llamar a los servicios proporcionados por el sitio de vinculación porque [CFrameWndEx Class](../../mfc/reference/cframewndex-class.md) controla estos servicios.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CDockSite`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/CPP/cdocksite-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## Requisitos  
 **Encabezado:** afxDockSite.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)