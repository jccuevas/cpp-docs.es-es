---
title: "CDockablePaneAdapter Class | Microsoft Docs"
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
  - "CDockablePaneAdapter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDockablePaneAdapter class"
ms.assetid: 6ed6cf82-f39c-4d0c-bf7c-8641495cf8f3
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CDockablePaneAdapter Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona compatibilidad para paneles derivados de `CWnd`.  
  
## Sintaxis  
  
```  
class CDockablePaneAdapter : public CDockablePane  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockablePaneAdapter::GetWrappedWnd](../Topic/CDockablePaneAdapter::GetWrappedWnd.md)|Devuelve la ventana ajustada.|  
|[CDockablePaneAdapter::LoadState](../Topic/CDockablePaneAdapter::LoadState.md)|\(Reemplaza [CDockablePane::LoadState](http://msdn.microsoft.com/es-es/96110136-4f46-4764-8a76-3b4abaf77917)\).|  
|[CDockablePaneAdapter::SaveState](../Topic/CDockablePaneAdapter::SaveState.md)|\(Reemplaza [CDockablePane::SaveState](http://msdn.microsoft.com/es-es/c5c24249-8d0d-46cb-96d9-9f5c6dc191db)\).|  
|[CDockablePaneAdapter::SetWrappedWnd](../Topic/CDockablePaneAdapter::SetWrappedWnd.md)||  
  
## Comentarios  
 Por lo general, el marco de trabajo crea instancias de objetos de esta clase cuando se usan los métodos [CMFCBaseTabCtrl::AddTab](../Topic/CMFCBaseTabCtrl::AddTab.md) o [CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md).  
  
 Si desea personalizar el comportamiento de `CDockablePaneAdapter`, simplemente derive una nueva clase a partir de este elemento y establezca la información de clase en tiempo de ejecución en una ventana con fichas mediante [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](../Topic/CMFCBaseTabCtrl::SetDockingBarWrapperRTC.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPane](../../mfc/reference/cpane-class.md) [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md)  
  
## Requisitos  
 **Encabezado:** afxDockablePaneAdapter.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)