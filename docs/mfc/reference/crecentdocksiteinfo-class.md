---
title: "CRecentDockSiteInfo Class | Microsoft Docs"
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
  - "CRecentDockSiteInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRecentDockSiteInfo class"
ms.assetid: 2dd14f95-d5a2-4461-a7a5-2c6c36a3a165
caps.latest.revision: 26
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRecentDockSiteInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase `CRecentDockSiteInfo` es una clase auxiliar que almacena la información de estado reciente para la [CPane Class](../../mfc/reference/cpane-class.md).  
  
## Sintaxis  
  
```  
class CRecentDockSiteInfo : public CObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CRecentDockSiteInfo::CRecentDockSiteInfo`|Constructor predeterminado.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRecentDockSiteInfo::CleanUp](../Topic/CRecentDockSiteInfo::CleanUp.md)||  
|[CRecentDockSiteInfo::GetRecentDefaultPaneDivider](../Topic/CRecentDockSiteInfo::GetRecentDefaultPaneDivider.md)||  
|[CRecentDockSiteInfo::GetRecentDockedPercent](../Topic/CRecentDockSiteInfo::GetRecentDockedPercent.md)||  
|[CRecentDockSiteInfo::GetRecentDockedRect](../Topic/CRecentDockSiteInfo::GetRecentDockedRect.md)||  
|[CRecentDockSiteInfo::GetRecentListOfPanes](../Topic/CRecentDockSiteInfo::GetRecentListOfPanes.md)||  
|[CRecentDockSiteInfo::GetRecentPaneContainer](../Topic/CRecentDockSiteInfo::GetRecentPaneContainer.md)||  
|[CRecentDockSiteInfo::GetRecentTabContainer](../Topic/CRecentDockSiteInfo::GetRecentTabContainer.md)||  
|[CRecentDockSiteInfo::Init](../Topic/CRecentDockSiteInfo::Init.md)||  
|[CRecentDockSiteInfo::IsRecentLeftPane](../Topic/CRecentDockSiteInfo::IsRecentLeftPane.md)||  
|[CRecentDockSiteInfo::operator \=](../Topic/CRecentDockSiteInfo::operator%20=.md)||  
|[CRecentDockSiteInfo::SaveListOfRecentPanes](../Topic/CRecentDockSiteInfo::SaveListOfRecentPanes.md)||  
|[CRecentDockSiteInfo::SetInfo](../Topic/CRecentDockSiteInfo::SetInfo.md)||  
|[CRecentDockSiteInfo::StoreDockInfo](../Topic/CRecentDockSiteInfo::StoreDockInfo.md)||  
  
## Comentarios  
 La clase `CRecentDockSiteInfo` es una clase de administración de datos.  Realiza un seguimiento del último estado de `CPane` durante su transición entre acoplado y flotante.  Cuando un usuario hace doble clic en un panel acoplable flotante, se acopla.  Si hace doble clic en el panel acoplado, vuelve a su ubicación, tamaño y estado anteriores.  De forma similar, cuando el panel se vuelve a acoplar, regresa a su ubicación de acoplamiento anterior.  Esta clase de datos es lo que hace que sea posible.  Dado que los miembros de esta clase almacenan información de estado del panel acoplado, la aplicación no debe modificarlos directamente.  
  
 Se crea un objeto `CRecentDockSiteInfo` cada vez que se crea un panel.  Cada objeto `CPane` tiene una variable miembro, [CPane::m\_recentDockInfo](../Topic/CPane::m_recentDockInfo.md), para almacenar esta información.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)  
  
## Requisitos  
 **Encabezado:** afxrecentDockSiteInfo.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CDockSite Class](../../mfc/reference/cdocksite-class.md)