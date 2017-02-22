---
title: "CMFCColorPopupMenu Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCColorPopupMenu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCColorPopupMenu class"
ms.assetid: 0bf9efe8-aed5-4ab7-b23b-eb284b4668be
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# CMFCColorPopupMenu Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un menú emergente que usan los usuarios seleccionar colores en un documento o aplicación.  
  
## Sintaxis  
  
```  
class CMFCColorPopupMenu : public CMFCPopupMenu  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCColorPopupMenu::CMFCColorPopupMenu](../Topic/CMFCColorPopupMenu::CMFCColorPopupMenu.md)|Crea un objeto `CMFCColorPopupMenu`.|  
|`CMFCColorPopupMenu::~CMFCColorPopupMenu`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCColorPopupMenu::CreateTearOffBar](../Topic/CMFCColorPopupMenu::CreateTearOffBar.md)|Crea un acoplable rasgan la barra de color.  \(Reemplaza [CMFCPopupMenu::CreateTearOffBar](../Topic/CMFCPopupMenu::CreateTearOffBar.md).\)|  
|[CMFCColorPopupMenu::GetMenuBar](../Topic/CMFCColorPopupMenu::GetMenuBar.md)|Devuelve [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) incrustados dentro del elemento emergente.  \(Reemplaza [CMFCPopupMenu::GetMenuBar](../Topic/CMFCPopupMenu::GetMenuBar.md).\)|  
|`CMFCColorPopupMenu::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCColorPopupMenu::SetPropList](../Topic/CMFCColorPopupMenu::SetPropList.md)|Establece el objeto de control de cuadrícula de propiedades del objeto incrustado de `CMFCColorBar` .|  
  
### miembros de datos  
  
|||  
|-|-|  
|Name|Descripción|  
|`m_bEnabledInCustomizeMode`|Valor booleano que determina si mostrar la barra de color.|  
|`m_wndColorBar`|El objeto de `CMFCColorBar` que proporciona la selección de color.|  
  
### Comentarios  
 Esta clase hereda la funcionalidad del menú emergente de la clase de `CMFCPopupMenu` y administra un objeto de `CMFCColorBar` que proporciona la selección de color.  Cuando el marco de la barra de herramientas está en modo de personalización y establecer el miembro de `m_bEnabledInCustomizeMode` a `FALSE`, el objeto de la barra de color no se muestra.  Para obtener más información sobre el modo de personalización, vea [CMFCToolBar::IsCustomizeMode](../Topic/CMFCToolBar::IsCustomizeMode.md)  
  
 Para obtener más información sobre `CMFCColorBar`, vea [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)  
  
 [CMFCColorPopupMenu](../../mfc/reference/cmfccolorpopupmenu-class.md)  
  
## Requisitos  
 **encabezado:** afxcolorpopupmenu.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)