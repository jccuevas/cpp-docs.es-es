---
title: "CPaneDivider Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPaneDivider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDivider class"
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CPaneDivider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 La clase de `CPaneDivider` divide dos paneles, divide dos grupos de paneles, o separa un grupo de paneles del área de cliente de la ventana de marco principal.  
  
## Sintaxis  
  
```  
class CPaneDivider : public CBasePane  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDivider::CPaneDivider](../Topic/CPaneDivider::CPaneDivider.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDivider::AddPaneContainer](../Topic/CPaneDivider::AddPaneContainer.md)||  
|[CPaneDivider::AddPane](../Topic/CPaneDivider::AddPane.md)||  
|[CPaneDivider::AddRecentPane](../Topic/CPaneDivider::AddRecentPane.md)||  
|[CPaneDivider::CalcExpectedDockedRect](../Topic/CPaneDivider::CalcExpectedDockedRect.md)||  
|[CPaneDivider::CalcFixedLayout](../Topic/CPaneDivider::CalcFixedLayout.md)|\(Reemplaza [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md).\)|  
|[CPaneDivider::CheckVisibility](../Topic/CPaneDivider::CheckVisibility.md)||  
|[CPaneDivider::CreateEx](../Topic/CPaneDivider::CreateEx.md)|\(Reemplaza [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md).\)|  
|[CPaneDivider::DoesAllowDynInsertBefore](../Topic/CPaneDivider::DoesAllowDynInsertBefore.md)|\(Reemplaza [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md).\)|  
|[CPaneDivider::DoesContainFloatingPane](../Topic/CPaneDivider::DoesContainFloatingPane.md)||  
|[CPaneDivider::FindPaneContainer](../Topic/CPaneDivider::FindPaneContainer.md)||  
|[CPaneDivider::FindTabbedPane](../Topic/CPaneDivider::FindTabbedPane.md)||  
|[CPaneDivider::GetDefaultWidth](../Topic/CPaneDivider::GetDefaultWidth.md)||  
|[CPaneDivider::GetFirstPane](../Topic/CPaneDivider::GetFirstPane.md)||  
|[CPaneDivider::GetPaneDividerStyle](../Topic/CPaneDivider::GetPaneDividerStyle.md)||  
|[CPaneDivider::GetRootContainerRect](../Topic/CPaneDivider::GetRootContainerRect.md)||  
|[CPaneDivider::GetWidth](../Topic/CPaneDivider::GetWidth.md)||  
|[CPaneDivider::Init](../Topic/CPaneDivider::Init.md)||  
|[CPaneDivider::InsertPane](../Topic/CPaneDivider::InsertPane.md)||  
|[CPaneDivider::IsAutoHideMode](../Topic/CPaneDivider::IsAutoHideMode.md)|\(Reemplaza [CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md).\)|  
|[CPaneDivider::IsDefault](../Topic/CPaneDivider::IsDefault.md)||  
|[CPaneDivider::IsHorizontal](../Topic/CPaneDivider::IsHorizontal.md)|\(Reemplaza [CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md).\)|  
|[CPaneDivider::Move](../Topic/CPaneDivider::Move.md)||  
|[CPaneDivider::NotifyAboutRelease](../Topic/CPaneDivider::NotifyAboutRelease.md)||  
|[CPaneDivider::OnShowPane](../Topic/CPaneDivider::OnShowPane.md)||  
|[CPaneDivider::ReleaseEmptyPaneContainers](../Topic/CPaneDivider::ReleaseEmptyPaneContainers.md)||  
|[CPaneDivider::RemovePane](../Topic/CPaneDivider::RemovePane.md)||  
|[CPaneDivider::ReplacePane](../Topic/CPaneDivider::ReplacePane.md)||  
|[CPaneDivider::RepositionPanes](../Topic/CPaneDivider::RepositionPanes.md)||  
|[CPaneDivider::Serialize](../Topic/CPaneDivider::Serialize.md)|\(Reemplaza `CBasePane::Serialize`.\)|  
|[CPaneDivider::SetAutoHideMode](../Topic/CPaneDivider::SetAutoHideMode.md)||  
|[CPaneDivider::SetPaneContainerManager](../Topic/CPaneDivider::SetPaneContainerManager.md)||  
|[CPaneDivider::ShowWindow](../Topic/CPaneDivider::ShowWindow.md)||  
|[CPaneDivider::StoreRecentDockSiteInfo](../Topic/CPaneDivider::StoreRecentDockSiteInfo.md)||  
|[CPaneDivider::StoreRecentTabRelatedInfo](../Topic/CPaneDivider::StoreRecentTabRelatedInfo.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDivider::GetPanes](../Topic/CPaneDivider::GetPanes.md)|devuelve la lista de paneles que residan en [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md).  Este método se debe llamar a para los divisores de paneles predeterminados.|  
|[CPaneDivider::GetPaneDividers](../Topic/CPaneDivider::GetPaneDividers.md)|devuelve la lista de divisores de paneles que residan en [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md).  Este método se debe llamar a para los divisores de paneles predeterminados.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneDivider::m\_nDefaultWidth](../Topic/CPaneDivider::m_nDefaultWidth.md)|Especifica el ancho predeterminado en píxeles de todos los divisores de paneles de la aplicación.|  
|[CPaneDivider::m\_pSliderRTC](../Topic/CPaneDivider::m_pSliderRTC.md)|Contiene un puntero a la información sobre `CPaneDivider`\- objeto derivado de la clase en tiempo de ejecución.|  
  
## Comentarios  
 El marco de trabajo crea los objetos de `CPaneDivider` automáticamente cuando un panel está acoplado.  
  
 hay dos tipos de divisores de paneles:  
  
-   se crea un divisor de paneles predeterminado cuando un grupo de paneles se acopla a un lado de la ventana de marco principal.  El divisor de paneles predeterminado contiene un puntero a [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) y redirige la mayoría de las operaciones en el grupo de paneles \(como cambiar el tamaño de un panel, o acoplar otro panel o contenedor\) al administrador del contenedor.  Cada panel acoplable mantiene un puntero al divisor de paneles predeterminado.  
  
-   Un divisor de paneles regular simplemente divide dos paneles en un contenedor.  Para obtener más información, vea [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md).  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo obtener un objeto de `CPaneDivider` de un objeto de `CWorkspaceBar` .  Este fragmento de código es parte de [Ejemplo de demostración de las pestañas de MDI](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/CPP/cpanedivider-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)  
  
## Requisitos  
 **encabezado:** afxPaneDivider.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md)   
 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)   
 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)