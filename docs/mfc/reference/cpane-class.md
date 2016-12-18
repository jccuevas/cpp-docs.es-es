---
title: "CPane Class | Microsoft Docs"
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
  - "CPane"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPane class"
ms.assetid: 5c651a64-3c79-4d94-9676-45f6402a6bc5
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPane Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CPane` es un aumento de [CControlBar Class](../../mfc/reference/ccontrolbar-class.md).  Si está actualizando un proyecto MFC existente, reemplace todas las apariciones de `CControlBar` con `CPane`.  
  
## Sintaxis  
  
```  
class CPane : public CBasePane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CPane::~CPane`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md)|inmediatamente actualiza el diseño de un panel.|  
|[CPane::AllocElements](../Topic/CPane::AllocElements.md)|Asigna el almacenamiento para uso interno.|  
|[CPane::AllowShowOnPaneMenu](../Topic/CPane::AllowShowOnPaneMenu.md)|Especifica si el panel se muestra en la lista runtime\- generada de paneles para la aplicación.|  
|[CPane::CalcAvailableSize](../Topic/CPane::CalcAvailableSize.md)|Calcula la diferencia de tamaño entre un rectángulo especificado y el rectángulo de ventana actual.|  
|[CPane::CalcInsideRect](../Topic/CPane::CalcInsideRect.md)|Calcula el rectángulo dentro de un panel, teniendo en cuenta los bordes y los agarradores.|  
|[CPane::CalcRecentDockedRect](../Topic/CPane::CalcRecentDockedRect.md)|Calcula el rectángulo recientemente acoplado.|  
|[CPane::CalcSize](../Topic/CPane::CalcSize.md)|Calcula el tamaño del panel.|  
|[CPane::CanBeDocked](../Topic/CPane::CanBeDocked.md)|Determina si el panel se puede acoplar en el panel base especificado.|  
|[CPane::CanBeTabbedDocument](../Topic/CPane::CanBeTabbedDocument.md)|Determina si el panel se puede convertir en un documento con fichas.|  
|[CPane::ConvertToTabbedDocument](../Topic/CPane::ConvertToTabbedDocument.md)|Convierte un panel acoplable a un documento con fichas.|  
|[CPane::CopyState](../Topic/CPane::CopyState.md)|Copia el estado de un panel.  \(Reemplaza [CBasePane::CopyState](../Topic/CBasePane::CopyState.md).\)|  
|[CPane::Create](../Topic/CPane::Create.md)|Crea una barra de controles y la agrega al objeto de `CPane` .|  
|[CPane::CreateDefaultMiniframe](../Topic/CPane::CreateDefaultMiniframe.md)|Crea una ventana de marco recudido para un panel flotante.|  
|[CPane::CreateEx](../Topic/CPane::CreateEx.md)|Crea una barra de controles y la agrega al objeto de `CPane` .|  
|`CPane::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CPane::DockByMouse](../Topic/CPane::DockByMouse.md)|Acoplar un panel utilizando el método de acoplamiento del mouse.|  
|[CPane::DockPane](../Topic/CPane::DockPane.md)|Acoplar el panel flotante a un panel base.|  
|[CPane::DockPaneStandard](../Topic/CPane::DockPaneStandard.md)|Acoplar un panel mediante el acoplamiento de esquema \(estándar\).|  
|[CPane::DockToFrameWindow](../Topic/CPane::DockToFrameWindow.md)|Acoplar un panel acoplable un marco.  \(Reemplaza `CBasePane::DockToFrameWindow`.\)|  
|[CPane::DoesAllowSiblingBars](../Topic/CPane::DoesAllowSiblingBars.md)|Indica si puede acoplar otro panel en la misma fila donde el panel actual está acoplado.|  
|[CPane::FloatPane](../Topic/CPane::FloatPane.md)|flota el panel.|  
|[CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md)|Devuelve la cantidad, en píxeles, que el panel puede expandir.|  
|[CPane::GetAvailableStretchSize](../Topic/CPane::GetAvailableStretchSize.md)|Devuelve la cantidad, en píxeles, que el panel puede reducir.|  
|[CPane::GetBorders](../Topic/CPane::GetBorders.md)|Devuelve el ancho de los bordes del panel.|  
|[CPane::GetClientHotSpot](../Topic/CPane::GetClientHotSpot.md)|Devuelve *la zona activa* del panel.|  
|[CPane::GetDockSiteRow](../Topic/CPane::GetDockSiteRow.md)|Devuelve la fila de acoplamiento en la que el panel está acoplado.|  
|[CPane::GetExclusiveRowMode](../Topic/CPane::GetExclusiveRowMode.md)|Determina si el panel está en modo exclusivo de la fila.|  
|[CPane::GetHotSpot](../Topic/CPane::GetHotSpot.md)|Devuelve la zona activa que se almacenan en un objeto subyacente de `CMFCDragFrameImpl` .|  
|[CPane::GetMinSize](../Topic/CPane::GetMinSize.md)|Recupera el mínimo permitido el tamaño del panel.|  
|[CPane::GetPaneName](../Topic/CPane::GetPaneName.md)|Recupera el título del panel.|  
|`CPane::GetResizeStep`|Utilizado de forma interna.|  
|`CPane::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CPane::GetVirtualRect](../Topic/CPane::GetVirtualRect.md)|Recupera *el rectángulo virtual* del panel.|  
|[CPane::IsChangeState](../Topic/CPane::IsChangeState.md)|Mientras se mueve el panel, este método analiza la posición del panel en relación con otros paneles, dock filas, y las ventanas de mini\- cuadro, y retornos el valor apropiado de `AFX_CS_STATUS` .|  
|[CPane::IsDragMode](../Topic/CPane::IsDragMode.md)|Especifica si se arrastra el panel.|  
|[CPane::IsInFloatingMultiPaneFrameWnd](../Topic/CPane::IsInFloatingMultiPaneFrameWnd.md)|Especifica si el panel está en una ventana de marco de multi\- panel.  \(Reemplaza `CBasePane::IsInFloatingMultiPaneFrameWnd`.\)|  
|[CPane::IsLeftOf](../Topic/CPane::IsLeftOf.md)|Determina si el panel está obsoleta \(o anterior\) del rectángulo especificado.|  
|[CPane::IsResizable](../Topic/CPane::IsResizable.md)|Determina si el panel puede cambiar de tamaño.  \(Reemplaza [CBasePane::IsResizable](../Topic/CBasePane::IsResizable.md).\)|  
|[CPane::IsTabbed](../Topic/CPane::IsTabbed.md)|Determina si el panel se ha insertado en el control de ficha de una ventana con fichas.  \(Reemplaza [CBasePane::IsTabbed](../Topic/CBasePane::IsTabbed.md).\)|  
|[CPane::LoadState](../Topic/CPane::LoadState.md)|Carga el estado del registro.  \(Reemplaza [CBasePane::LoadState](../Topic/CBasePane::LoadState.md).\)|  
|[CPane::MoveByAlignment](../Topic/CPane::MoveByAlignment.md)|Mueve el panel y el rectángulo virtual en la cantidad especificada.|  
|[CPane::MovePane](../Topic/CPane::MovePane.md)|Mueve el panel al rectángulo especificado.|  
|[CPane::OnAfterChangeParent](../Topic/CPane::OnAfterChangeParent.md)|Llamado por el marco al elemento primario de un panel ha cambiado.|  
|[CPane::OnBeforeChangeParent](../Topic/CPane::OnBeforeChangeParent.md)|Llamado por el marco al elemento primario del panel va a cambiar.|  
|[CPane::OnPressCloseButton](../Topic/CPane::OnPressCloseButton.md)|Llamado por el marco cuando el usuario elige el botón cerrar en la leyenda para el panel.|  
|`CPane::OnProcessDblClk`|Utilizado de forma interna.|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|Llamado por el marco cuando un menú especial de panel se va a mostrar.|  
|[CPane::OnShowControlBarMenu](../Topic/CPane::OnShowControlBarMenu.md)|Llamado por el marco cuando un menú especial de panel se va a mostrar.|  
|`CPane::PrepareToDock`|Utilizado de forma interna.|  
|[CPane::RecalcLayout](../Topic/CPane::RecalcLayout.md)|Actualiza la información de diseño del panel.  \(Reemplaza [CBasePane::RecalcLayout](../Topic/CBasePane::RecalcLayout.md).\)|  
|[CPane::SaveState](../Topic/CPane::SaveState.md)|Guarda el estado del panel al registro.  \(Reemplaza [CBasePane::SaveState](../Topic/CBasePane::SaveState.md).\)|  
|[CPane::SetActiveInGroup](../Topic/CPane::SetActiveInGroup.md)|Marca un panel como activo.|  
|[CPane::SetBorders](../Topic/CPane::SetBorders.md)|Establece los valores del borde del panel.|  
|[CPane::SetClientHotSpot](../Topic/CPane::SetClientHotSpot.md)|Establece la zona activa del panel.|  
|[CPane::SetDockState](../Topic/CPane::SetDockState.md)|Restaura la información de estado de acoplamiento para el panel.|  
|[CPane::SetExclusiveRowMode](../Topic/CPane::SetExclusiveRowMode.md)|Habilita o deshabilita el modo exclusivo de la fila.|  
|[CPane::SetMiniFrameRTC](../Topic/CPane::SetMiniFrameRTC.md)|Establece la información de la clase en tiempo de ejecución para la ventana predeterminada de marco recudido.|  
|[CPane::SetMinSize](../Topic/CPane::SetMinSize.md)|Establece el mínimo permitido el tamaño del panel.|  
|[CPane::SetVirtualRect](../Topic/CPane::SetVirtualRect.md)|Establece *el rectángulo virtual* del panel.|  
|[CPane::StretchPaneDeferWndPos](../Topic/CPane::StretchPaneDeferWndPos.md)|Expande el panel vertical u horizontalmente basado en estilo de acoplamiento.|  
|[CPane::ToggleAutoHide](../Topic/CPane::ToggleAutoHide.md)|Alterna ocultan automáticamente el modo.|  
|[CPane::UndockPane](../Topic/CPane::UndockPane.md)|Quita el panel del sitio de acoplamiento, slider predeterminado, o la ventana de marco recudido donde está acoplado actualmente.  \(Reemplaza [CBasePane::UndockPane](../Topic/CBasePane::UndockPane.md).\)|  
|[CPane::UpdateVirtualRect](../Topic/CPane::UpdateVirtualRect.md)|Actualiza el rectángulo virtual.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPane::OnAfterDock](../Topic/CPane::OnAfterDock.md)|Llamado por el marco cuando un panel ha estado acoplado.|  
|[CPane::OnAfterFloat](../Topic/CPane::OnAfterFloat.md)|Llamado por el marco cuando queda flotando un panel.|  
|[CPane::OnBeforeDock](../Topic/CPane::OnBeforeDock.md)|Llamado por el marco cuando el panel está a punto de acoplarse.|  
|[CPane::OnBeforeFloat](../Topic/CPane::OnBeforeFloat.md)|Llamado por el marco cuando un panel está a punto de ser dejarla flotando.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPane::m\_bHandleMinSize](../Topic/CPane::m_bHandleMinSize.md)|Permite administrar coherente de tamaño mínimo de los paneles.|  
|[CPane::m\_recentDockInfo](../Topic/CPane::m_recentDockInfo.md)|Contiene información reciente de acoplamiento.|  
  
## Comentarios  
 Normalmente, los objetos de `CPane` no se crean instancias directamente.  Si necesita un panel con funcionalidad de acoplamiento, derive el objeto de [CDockablePane](../../mfc/reference/cdockablepane-class.md).  Si necesita funcionalidad de la barra de herramientas, derive el objeto de [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md).  
  
 Al derivar una clase de `CPane`, puede acoplar en [CDockSite](../../mfc/reference/cdocksite-class.md) y puede ser dejarla flotando en [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
## Requisitos  
 **encabezado:** afxPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)