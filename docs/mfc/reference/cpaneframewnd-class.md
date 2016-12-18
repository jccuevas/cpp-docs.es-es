---
title: "CPaneFrameWnd Class | Microsoft Docs"
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
  - "CPaneFrameWnd.Serialize"
  - "CPaneFrameWnd.PreTranslateMessage"
  - "CPaneFrameWnd"
  - "CPaneFrameWnd::Serialize"
  - "PreTranslateMessage"
  - "CPaneFrameWnd::PreTranslateMessage"
  - "Serialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneFrameWnd class"
  - "PreTranslateMessage method"
  - "Serialize method"
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: 28
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPaneFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Implementa una ventana de marco reducido que contiene un panel.  El panel rellena el área cliente de la ventana.  
  
## Sintaxis  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](../Topic/CPaneFrameWnd::AddPane.md)|Agrega un panel.|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](../Topic/CPaneFrameWnd::AddRemovePaneFromGlobalList.md)|Agrega o quita un panel de la lista global.|  
|[CPaneFrameWnd::AdjustLayout](../Topic/CPaneFrameWnd::AdjustLayout.md)|Ajusta el diseño de la ventana de marco reducido.|  
|[CPaneFrameWnd::AdjustPaneFrames](../Topic/CPaneFrameWnd::AdjustPaneFrames.md)||  
|[CPaneFrameWnd::CalcBorderSize](../Topic/CPaneFrameWnd::CalcBorderSize.md)|Calcula el tamaño de los bordes de una ventana de marco reducido.|  
|[CPaneFrameWnd::CalcExpectedDockedRect](../Topic/CPaneFrameWnd::CalcExpectedDockedRect.md)|Calcula el rectángulo esperado de una ventana acoplada.|  
|[CPaneFrameWnd::CanBeAttached](../Topic/CPaneFrameWnd::CanBeAttached.md)|Determina si se puede acoplar el panel actual a otro panel o ventana de marco.|  
|[CPaneFrameWnd::CanBeDockedToPane](../Topic/CPaneFrameWnd::CanBeDockedToPane.md)|Determina si se puede acoplar la ventana de marco reducido a un panel.|  
|[CPaneFrameWnd::CheckGripperVisibility](../Topic/CPaneFrameWnd::CheckGripperVisibility.md)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](../Topic/CPaneFrameWnd::ConvertToTabbedDocument.md)|Convierte el panel en un documento con pestañas.|  
|[CPaneFrameWnd::Create](../Topic/CPaneFrameWnd::Create.md)|Crea una ventana de marco reducido y la adjunta al objeto `CPaneFrameWnd`.|  
|[CPaneFrameWnd::CreateEx](../Topic/CPaneFrameWnd::CreateEx.md)|Crea una ventana de marco reducido y la adjunta al objeto `CPaneFrameWnd`.|  
|[CPaneFrameWnd::DockPane](../Topic/CPaneFrameWnd::DockPane.md)|Acopla el panel.|  
|[CPaneFrameWnd::FindFloatingPaneByID](../Topic/CPaneFrameWnd::FindFloatingPaneByID.md)|Busca un panel con el identificador del control especificado en la lista global de paneles flotantes.|  
|[CPaneFrameWnd::FrameFromPoint](../Topic/CPaneFrameWnd::FrameFromPoint.md)|Busca la ventana de marco reducido que contiene un punto proporcionado por el usuario.|  
|[CPaneFrameWnd::GetCaptionHeight](../Topic/CPaneFrameWnd::GetCaptionHeight.md)|Devuelve el alto del título de la ventana de marco reducido.|  
|[CPaneFrameWnd::GetCaptionRect](../Topic/CPaneFrameWnd::GetCaptionRect.md)|Calcula el rectángulo delimitador del título de una ventana de marco reducido.|  
|[CPaneFrameWnd::GetCaptionText](../Topic/CPaneFrameWnd::GetCaptionText.md)|Devuelve el texto del título.|  
|[CPaneFrameWnd::GetDockingManager](../Topic/CPaneFrameWnd::GetDockingManager.md)||  
|[CPaneFrameWnd::GetDockingMode](../Topic/CPaneFrameWnd::GetDockingMode.md)|Devuelve el modo de acoplamiento.|  
|[CPaneFrameWnd::GetFirstVisiblePane](../Topic/CPaneFrameWnd::GetFirstVisiblePane.md)|Devuelve el primer panel visible que se encuentra en una ventana de marco reducido.|  
|[CPaneFrameWnd::GetHotPoint](../Topic/CPaneFrameWnd::GetHotPoint.md)||  
|[CPaneFrameWnd::GetPane](../Topic/CPaneFrameWnd::GetPane.md)|Devuelve un panel que se encuentra en la ventana de marco reducido.|  
|[CPaneFrameWnd::GetPaneCount](../Topic/CPaneFrameWnd::GetPaneCount.md)|Devuelve el número de paneles que se encuentran en una ventana de marco reducido.|  
|[CPaneFrameWnd::GetParent](../Topic/CPaneFrameWnd::GetParent.md)||  
|[CPaneFrameWnd::GetPinState](../Topic/CPaneFrameWnd::GetPinState.md)||  
|[CPaneFrameWnd::GetRecentFloatingRect](../Topic/CPaneFrameWnd::GetRecentFloatingRect.md)||  
|[CPaneFrameWnd::GetVisiblePaneCount](../Topic/CPaneFrameWnd::GetVisiblePaneCount.md)|Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido.|  
|[CPaneFrameWnd::HitTest](../Topic/CPaneFrameWnd::HitTest.md)|Determina qué parte de una ventana de marco reducido es en un momento dado.|  
|[CPaneFrameWnd::IsCaptured](../Topic/CPaneFrameWnd::IsCaptured.md)||  
|[CPaneFrameWnd::IsDelayShow](../Topic/CPaneFrameWnd::IsDelayShow.md)||  
|[CPaneFrameWnd::IsRollDown](../Topic/CPaneFrameWnd::IsRollDown.md)|Determina si se debe retraer una ventana de marco reducido.|  
|[CPaneFrameWnd::IsRollUp](../Topic/CPaneFrameWnd::IsRollUp.md)|Determina si se debe desplegar una ventana de marco reducido.|  
|[CPaneFrameWnd::KillDockingTimer](../Topic/CPaneFrameWnd::KillDockingTimer.md)|Detiene el temporizador de acoplamiento.|  
|[CPaneFrameWnd::LoadState](../Topic/CPaneFrameWnd::LoadState.md)|Carga el estado del panel desde el registro.|  
|[CPaneFrameWnd::OnBeforeDock](../Topic/CPaneFrameWnd::OnBeforeDock.md)|Determina si es posible el acoplamiento.|  
|[CPaneFrameWnd::OnDockToRecentPos](../Topic/CPaneFrameWnd::OnDockToRecentPos.md)|Acopla la ventana de marco reducido en su posición más reciente.|  
|[CPaneFrameWnd::OnKillRollUpTimer](../Topic/CPaneFrameWnd::OnKillRollUpTimer.md)|Detiene el temporizador de despliegue.|  
|[CPaneFrameWnd::OnMovePane](../Topic/CPaneFrameWnd::OnMovePane.md)|Mueve la ventana de marco reducido a una distancia especificada.|  
|[CPaneFrameWnd::OnPaneRecalcLayout](../Topic/CPaneFrameWnd::OnPaneRecalcLayout.md)|Ajusta el diseño de un panel de contenido.|  
|[CPaneFrameWnd::OnSetRollUpTimer](../Topic/CPaneFrameWnd::OnSetRollUpTimer.md)|Establece el temporizador de despliegue.|  
|[CPaneFrameWnd::OnShowPane](../Topic/CPaneFrameWnd::OnShowPane.md)|Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido.|  
|[CPaneFrameWnd::PaneFromPoint](../Topic/CPaneFrameWnd::PaneFromPoint.md)|Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido.|  
|[CPaneFrameWnd::Pin](../Topic/CPaneFrameWnd::Pin.md)||  
|`CPaneFrameWnd::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CPaneFrameWnd::RedrawAll](../Topic/CPaneFrameWnd::RedrawAll.md)|Vuelve a dibujar todas las ventanas de marco reducido.|  
|[CPaneFrameWnd::RemoveNonValidPanes](../Topic/CPaneFrameWnd::RemoveNonValidPanes.md)|Llamado por el marco de trabajo para quitar los paneles no válidos.|  
|[CPaneFrameWnd::RemovePane](../Topic/CPaneFrameWnd::RemovePane.md)|Quita un panel de la ventana de marco reducido.|  
|[CPaneFrameWnd::ReplacePane](../Topic/CPaneFrameWnd::ReplacePane.md)|Reemplaza un panel con otro.|  
|[CPaneFrameWnd::SaveState](../Topic/CPaneFrameWnd::SaveState.md)|Guarda el estado del panel en el registro.|  
|`CPaneFrameWnd::Serialize`|Lee o escribe este objeto desde un archivo o en un archivo.|  
|[CPaneFrameWnd::SetCaptionButtons](../Topic/CPaneFrameWnd::SetCaptionButtons.md)|Establece botones del título.|  
|[CPaneFrameWnd::SetDelayShow](../Topic/CPaneFrameWnd::SetDelayShow.md)||  
|[CPaneFrameWnd::SetDockingManager](../Topic/CPaneFrameWnd::SetDockingManager.md)||  
|[CPaneFrameWnd::SetDockingTimer](../Topic/CPaneFrameWnd::SetDockingTimer.md)|Establece el temporizador de acoplamiento.|  
|[CPaneFrameWnd::SetDockState](../Topic/CPaneFrameWnd::SetDockState.md)|Establece el estado de acoplamiento.|  
|[CPaneFrameWnd::SetHotPoint](../Topic/CPaneFrameWnd::SetHotPoint.md)||  
|[CPaneFrameWnd::SetPreDockState](../Topic/CPaneFrameWnd::SetPreDockState.md)|Llamado por el marco para establecer el estado previo al acoplamiento.|  
|[CPaneFrameWnd::SizeToContent](../Topic/CPaneFrameWnd::SizeToContent.md)|Ajusta el tamaño de una ventana de marco reducido para que tenga un tamaño equivalente al de un panel de contenido.|  
|[CPaneFrameWnd::StartTearOff](../Topic/CPaneFrameWnd::StartTearOff.md)|Desgaja un menú.|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CPaneFrameWnd::StoreRecentDockSiteInfo.md)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CPaneFrameWnd::StoreRecentTabRelatedInfo.md)||  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](../Topic/CPaneFrameWnd::OnCheckRollState.md)|Determina si se debe desplegar o retraer una ventana de marco reducido.|  
|[CPaneFrameWnd::OnDrawBorder](../Topic/CPaneFrameWnd::OnDrawBorder.md)|Dibuja los bordes de una ventana de marco reducido.|  
  
### Miembros de datos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CPaneFrameWnd::m\_bUseSaveBits](../Topic/CPaneFrameWnd::m_bUseSaveBits.md)|Especifica si se debe registrar la clase de ventana con el estilo de clase `CS_SAVEBITS`.|  
  
## Comentarios  
 El marco crea automáticamente un objeto `CPaneFrameWnd` cuando se cambia un panel de un estado acoplado a un estado flotante.  
  
 Se puede arrastrar una ventana de marco reducido con su contenido visible \(acoplamiento inmediato\) o mediante un rectángulo de arrastre \(acoplamiento estándar\).  El modo de acoplamiento del panel contenedor del marco reducido determina el comportamiento del marco reducido al arrastrarlo.  Para más información, vea [CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md).  
  
 Una ventana de marco reducido muestra botones en el título de acuerdo con el estilo del panel contenido.  Si se puede cerrar el panel \([CBasePane::CanBeClosed](../Topic/CBasePane::CanBeClosed.md)\), muestra un botón Cerrar.  Si el panel tiene el estilo `AFX_CBRS_AUTO_ROLLUP`, muestra una chincheta.  
  
 Si se deriva una clase de `CPaneFrameWnd`, se debe indicar al marco cómo crearla.  Cree la clase invalidando [CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md), o establezca el miembro `CPane::m_pMiniFrameRTC` de forma que apunte a la información de clase en tiempo de ejecución que le corresponda.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
## Requisitos  
 **Encabezado:** afxPaneFrameWnd.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)