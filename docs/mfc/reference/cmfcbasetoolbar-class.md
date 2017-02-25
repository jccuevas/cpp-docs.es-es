---
title: "CMFCBaseToolBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCBaseToolBar::CreateObject"
  - "~CMFCBaseToolBar"
  - "CMFCBaseToolBar"
  - "CMFCBaseToolBar::CMFCBaseToolBar"
  - "CMFCBaseToolBar::~CMFCBaseToolBar"
  - "CMFCBaseToolBar.~CMFCBaseToolBar"
  - "CreateObject"
  - "CMFCBaseToolBar.CMFCBaseToolBar"
  - "CMFCBaseToolBar.CreateObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCBaseToolBar destructor"
  - "CMFCBaseToolBar class"
  - "CMFCBaseToolBar class, constructor"
  - "CMFCBaseToolBar class, destructor"
  - "CreateObject method"
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CMFCBaseToolBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Clase base para las barras de herramientas.  
  
## Sintaxis  
  
```  
class CMFCBaseToolBar : public CPane  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CMFCBaseToolBar`|Constructor predeterminado.|  
|`CMFCBaseToolBar::~CMFCBaseToolBar`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCBaseToolBar::CreateObject`|Utiliza el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCBaseToolBar::GetDockingMode](../Topic/CMFCBaseToolBar::GetDockingMode.md)|Devuelve el modo de acoplamiento.  \(Reemplaza [CBasePane::GetDockingMode](../Topic/CBasePane::GetDockingMode.md).\)|  
|[CMFCBaseToolBar::GetMinSize](../Topic/CMFCBaseToolBar::GetMinSize.md)|Devuelve el tamaño mínimo de una barra de herramientas.  \(Reemplaza [CPane::GetMinSize](../Topic/CPane::GetMinSize.md).\)|  
|[CMFCBaseToolBar::OnAfterChangeParent](../Topic/CMFCBaseToolBar::OnAfterChangeParent.md)|Llamado por el marco después del elemento primario del panel.  \(Reemplaza [CBasePane::OnAfterChangeParent](../Topic/CBasePane::OnAfterChangeParent.md).\)|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
## Requisitos  
 **encabezado:** afxbasetoolbar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)