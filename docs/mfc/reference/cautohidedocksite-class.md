---
title: "CAutoHideDockSite Class | Microsoft Docs"
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
  - "CAutoHideDockSite"
  - "AllowShowOnPaneMenu"
  - "CAutoHideDockSite::AllowShowOnPaneMenu"
  - "CAutoHideDockSite.AllowShowOnPaneMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AllowShowOnPaneMenu method"
  - "CAutoHideDockSite class"
ms.assetid: 2a0f6bec-c369-4ab7-977d-564e7946ebad
caps.latest.revision: 32
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAutoHideDockSite Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CAutoHideDockSite` extiende [CDockSite Class](../../mfc/reference/cdocksite-class.md) a implementar oculta automáticamente los paneles de vinculación.  
  
## Sintaxis  
  
```  
class CAutoHideDockSite : public CDockSite  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CAutoHideDockSite::CAutoHideDockSite`|Crea un objeto `CAutoHideDockSite`.|  
|`CAutoHideDockSite::~CAutoHideDockSite`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|`CAutoHideDockSite::AllowShowOnPaneMenu`|Indica si `CAutoHideDockSite` se muestra en el menú del panel.|  
|[CAutoHideDockSite::CanAcceptPane](../Topic/CAutoHideDockSite::CanAcceptPane.md)|Determina si un objeto base del panel se deriva de [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md).|  
|[CAutoHideDockSite::DockPane](../Topic/CAutoHideDockSite::DockPane.md)|Acoplar un panel a este objeto de `CAuotHideDockSite` .|  
|[CAutoHideDockSite::GetAlignRect](../Topic/CAutoHideDockSite::GetAlignRect.md)|Recupera el tamaño del sitio de vinculación en coordenadas de pantalla.|  
|[CAutoHideDockSite::RepositionPanes](../Topic/CAutoHideDockSite::RepositionPanes.md)|Dibuja de nuevo el panel en `CAutoHideDockSite` con los márgenes y el espaciado globales del botón.|  
|[CAutoHideDockSite::SetOffsetLeft](../Topic/CAutoHideDockSite::SetOffsetLeft.md)|Establece el margen en el lado izquierdo de la barra de acoplamiento.|  
|[CAutoHideDockSite::SetOffsetRight](../Topic/CAutoHideDockSite::SetOffsetRight.md)|Establece el margen en el lado derecho de la barra de acoplamiento.|  
|[CAutoHideDockSite::UnSetAutoHideMode](../Topic/CAutoHideDockSite::UnSetAutoHideMode.md)|Llamadas [CMFCAutoHideBar::UnSetAutoHideMode](../Topic/CMFCAutoHideBar::UnSetAutoHideMode.md) para los objetos de `CAutoHideDockSite`.|  
  
### miembros de datos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CAutoHideDockSite::m\_nExtraSpace](../Topic/CAutoHideDockSite::m_nExtraSpace.md)|Define el tamaño del espacio entre las barras de herramientas y el borde de la barra de acoplamiento.  Este espacio se mide el borde izquierdo o del borde superior, dependiendo de alineación del espacio de vinculación.|  
  
## Comentarios  
 Cuando se llama a [CFrameWndEx::EnableAutoHidePanes](../Topic/CFrameWndEx::EnableAutoHidePanes.md), el marco de trabajo crea automáticamente un objeto de `CAutoHideDockSite` .  En la mayoría de los casos, no debería tener que crear instancias o utilizar esta clase directamente.  
  
 La barra de acoplamiento es el intervalo entre el lado izquierdo del panel de acoplamiento y el lado izquierdo de [CMFCAutoHideButton Class](../../mfc/reference/cmfcautohidebutton-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo recuperar un objeto de `CAutoHideDockSite` de un objeto de `CMFCAutoHideBar` , y cómo establecer los márgenes izquierdo y derecho de la barra de acoplamiento.  
  
 [!code-cpp[NVC_MFC_RibbonApp#29](../../mfc/reference/codesnippet/CPP/cautohidedocksite-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** afxautohidedocksite.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)