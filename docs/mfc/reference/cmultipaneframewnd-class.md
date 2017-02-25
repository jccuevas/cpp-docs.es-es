---
title: "CMultiPaneFrameWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMultiPaneFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPaneFrameWnd class"
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
caps.latest.revision: 36
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 38
---
# CMultiPaneFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la clase de `CMultiPaneFrameWnd` extiende [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md).  Puede admitir varios paneles.  En lugar de un único identificador incrustado a una barra de controles, `CMultiPaneFrameWnd` contiene un objeto que permite al usuario para acoplar un `CMultiPaneFrameWnd` a otro y crear dinámicamente la flotante múltiple, ventanas con fichas de [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) .  
  
## Sintaxis  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiPaneFrameWnd::AddPane](../Topic/CMultiPaneFrameWnd::AddPane.md)|agrega un panel.  \(Reemplaza [CPaneFrameWnd::AddPane](../Topic/CPaneFrameWnd::AddPane.md).\)|  
|[CMultiPaneFrameWnd::AddRecentPane](../Topic/CMultiPaneFrameWnd::AddRecentPane.md)||  
|[CMultiPaneFrameWnd::AdjustLayout](../Topic/CMultiPaneFrameWnd::AdjustLayout.md)|Ajustar el diseño de la ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::AdjustLayout](../Topic/CPaneFrameWnd::AdjustLayout.md).\)|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](../Topic/CMultiPaneFrameWnd::AdjustPaneFrames.md)|\(Reemplaza [CPaneFrameWnd::AdjustPaneFrames](../Topic/CPaneFrameWnd::AdjustPaneFrames.md).\)|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](../Topic/CMultiPaneFrameWnd::CalcExpectedDockedRect.md)|calcula el rectángulo esperado de una ventana acoplada.  \(Reemplaza [CPaneFrameWnd::CalcExpectedDockedRect](../Topic/CPaneFrameWnd::CalcExpectedDockedRect.md).\)|  
|[CMultiPaneFrameWnd::CanBeAttached](../Topic/CMultiPaneFrameWnd::CanBeAttached.md)|Determina si el panel actual puede acoplar en otra ventana del panel o del cuadro.  \(Reemplaza [CPaneFrameWnd::CanBeAttached](../Topic/CPaneFrameWnd::CanBeAttached.md).\)|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](../Topic/CMultiPaneFrameWnd::CanBeDockedToPane.md)|Determina si la ventana de marco recudido puede acoplar a un panel.  \(Reemplaza [CPaneFrameWnd::CanBeDockedToPane](../Topic/CPaneFrameWnd::CanBeDockedToPane.md).\)|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](../Topic/CMultiPaneFrameWnd::CheckGripperVisibility.md)|\(Reemplaza [CPaneFrameWnd::CheckGripperVisibility](../Topic/CPaneFrameWnd::CheckGripperVisibility.md).\)|  
|[CMultiPaneFrameWnd::CloseMiniFrame](../Topic/CMultiPaneFrameWnd::CloseMiniFrame.md)|\(Reemplaza `CPaneFrameWnd::CloseMiniFrame`.\)|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](../Topic/CMultiPaneFrameWnd::ConvertToTabbedDocument.md)|Convierte el panel en un documento con fichas.  \(Reemplaza [CPaneFrameWnd::ConvertToTabbedDocument](../Topic/CPaneFrameWnd::ConvertToTabbedDocument.md).\)|  
|[CMultiPaneFrameWnd::DockFrame](../Topic/CMultiPaneFrameWnd::DockFrame.md)||  
|[CMultiPaneFrameWnd::DockPane](../Topic/CMultiPaneFrameWnd::DockPane.md)|Acoplar el panel.  \(Reemplaza [CPaneFrameWnd::DockPane](../Topic/CPaneFrameWnd::DockPane.md).\)|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](../Topic/CMultiPaneFrameWnd::DockRecentPaneToMainFrame.md)||  
|[CMultiPaneFrameWnd::GetCaptionText](../Topic/CMultiPaneFrameWnd::GetCaptionText.md)|Devuelve el texto de la leyenda.  \(Reemplaza [CPaneFrameWnd::GetCaptionText](../Topic/CPaneFrameWnd::GetCaptionText.md).\)|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](../Topic/CMultiPaneFrameWnd::GetPaneContainerManager.md)|Devuelve una referencia al objeto interno del administrador del contenedor.|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](../Topic/CMultiPaneFrameWnd::GetFirstVisiblePane.md)|Devuelve el primer panel visible de una ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::GetFirstVisiblePane](../Topic/CPaneFrameWnd::GetFirstVisiblePane.md).\)|  
|[CMultiPaneFrameWnd::GetPane](../Topic/CMultiPaneFrameWnd::GetPane.md)|Devuelve un panel incluido en la ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::GetPane](../Topic/CPaneFrameWnd::GetPane.md).\)|  
|[CMultiPaneFrameWnd::GetPaneCount](../Topic/CMultiPaneFrameWnd::GetPaneCount.md)|Devuelve el número de paneles incluidos en una ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::GetPaneCount](../Topic/CPaneFrameWnd::GetPaneCount.md).\)|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](../Topic/CMultiPaneFrameWnd::GetVisiblePaneCount.md)|Devuelve el número de paneles visible incluidos en una ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::GetVisiblePaneCount](../Topic/CPaneFrameWnd::GetVisiblePaneCount.md).\)|  
|[CMultiPaneFrameWnd::InsertPane](../Topic/CMultiPaneFrameWnd::InsertPane.md)||  
|[CMultiPaneFrameWnd::LoadState](../Topic/CMultiPaneFrameWnd::LoadState.md)|Carga el estado del registro.  \(Reemplaza [CPaneFrameWnd::LoadState](../Topic/CPaneFrameWnd::LoadState.md).\)|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](../Topic/CMultiPaneFrameWnd::OnDockToRecentPos.md)|Acoplar la ventana de marco recudido en su posición más reciente.  \(Reemplaza [CPaneFrameWnd::OnDockToRecentPos](../Topic/CPaneFrameWnd::OnDockToRecentPos.md).\)|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](../Topic/CMultiPaneFrameWnd::OnKillRollUpTimer.md)|Detiene el temporizador de consolidado.  \(Reemplaza [CPaneFrameWnd::OnKillRollUpTimer](../Topic/CPaneFrameWnd::OnKillRollUpTimer.md).\)|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](../Topic/CMultiPaneFrameWnd::OnPaneRecalcLayout.md)|Ajustar el diseño de un panel dentro de una ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::OnPaneRecalcLayout](../Topic/CPaneFrameWnd::OnPaneRecalcLayout.md).\)|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](../Topic/CMultiPaneFrameWnd::OnSetRollUpTimer.md)|Establece el temporizador de consolidado.  \(Reemplaza [CPaneFrameWnd::OnSetRollUpTimer](../Topic/CPaneFrameWnd::OnSetRollUpTimer.md).\)|  
|[CMultiPaneFrameWnd::OnShowPane](../Topic/CMultiPaneFrameWnd::OnShowPane.md)|Llamado por el marco cuando un panel en la ventana de marco recudido está oculto o se muestra.  \(Reemplaza [CPaneFrameWnd::OnShowPane](../Topic/CPaneFrameWnd::OnShowPane.md).\)|  
|[CMultiPaneFrameWnd::PaneFromPoint](../Topic/CMultiPaneFrameWnd::PaneFromPoint.md)|Devuelve un panel si contiene un punto tras dentro de una ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::PaneFromPoint](../Topic/CPaneFrameWnd::PaneFromPoint.md).\)|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](../Topic/CMultiPaneFrameWnd::RemoveNonValidPanes.md)|Llamado por el marco para quitar los paneles no\-válidos.  \(Reemplaza [CPaneFrameWnd::RemoveNonValidPanes](../Topic/CPaneFrameWnd::RemoveNonValidPanes.md).\)|  
|[CMultiPaneFrameWnd::RemovePane](../Topic/CMultiPaneFrameWnd::RemovePane.md)|Quita un panel de la ventana de marco recudido.  \(Reemplaza [CPaneFrameWnd::RemovePane](../Topic/CPaneFrameWnd::RemovePane.md).\)|  
|[CMultiPaneFrameWnd::ReplacePane](../Topic/CMultiPaneFrameWnd::ReplacePane.md)|reemplaza un panel con otro.  \(Reemplaza [CPaneFrameWnd::ReplacePane](../Topic/CPaneFrameWnd::ReplacePane.md).\)|  
|[CMultiPaneFrameWnd::SaveState](../Topic/CMultiPaneFrameWnd::SaveState.md)|Guarda el estado del panel al registro.  \(Reemplaza [CPaneFrameWnd::SaveState](../Topic/CPaneFrameWnd::SaveState.md).\)|  
|[CMultiPaneFrameWnd::Serialize](../Topic/CMultiPaneFrameWnd::Serialize.md)|\(Reemplaza `CPaneFrameWnd::Serialize`.\)|  
|[CMultiPaneFrameWnd::SetDockState](../Topic/CMultiPaneFrameWnd::SetDockState.md)|Establece el estado de vinculación.  \(Reemplaza [CPaneFrameWnd::SetDockState](../Topic/CPaneFrameWnd::SetDockState.md).\)|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](../Topic/CMultiPaneFrameWnd::SetLastFocusedPane.md)||  
|[CMultiPaneFrameWnd::SetPreDockState](../Topic/CMultiPaneFrameWnd::SetPreDockState.md)|Establece el estado predocking.  \(Reemplaza [CPaneFrameWnd::SetPreDockState](../Topic/CPaneFrameWnd::SetPreDockState.md).\)|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CMultiPaneFrameWnd::StoreRecentDockSiteInfo.md)|\(Reemplaza [CPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CPaneFrameWnd::StoreRecentDockSiteInfo.md).\)|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo.md)|\(Reemplaza [CPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CPaneFrameWnd::StoreRecentTabRelatedInfo.md).\)|  
  
## Comentarios  
 La mayoría de los métodos de esta clase reemplazan los métodos de la clase de [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) .  
  
 Si un panel utiliza el estilo de `AFX_CBRS_AUTO_ROLLUP` y los acopla de usuario que el panel a una ventana de marco de varios paneles, el usuario puede ejecutar para buscar la ventana independientemente de la configuración de estilo de los otros paneles acoplados.  
  
 El marco de trabajo crea automáticamente un objeto de `CMultiPaneFrameWnd` cuando el usuario flota un panel que utiliza el estilo de `CBRS_FLOAT_MULTI` .  
  
 Para obtener información sobre cómo derivar de una clase de la clase de `CPaneFrameWnd` y crearla dinámicamente, vea [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar un puntero a un objeto de `CMultiPaneFrameWnd` .  Este fragmento de código es parte de [Establezca el ejemplo el tamaño del panel](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/CPP/cmultipaneframewnd-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## Requisitos  
 **encabezado:** afxMultiPaneFrameWnd.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)