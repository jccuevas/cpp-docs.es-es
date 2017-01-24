---
title: "CMFCPropertyGridToolTipCtrl Class | Microsoft Docs"
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
  - "CMFCPropertyGridToolTipCtrl::PreTranslateMessage"
  - "~CMFCPropertyGridToolTipCtrl"
  - "PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl.~CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl"
  - "CMFCPropertyGridToolTipCtrl.PreTranslateMessage"
  - "CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~CMFCPropertyGridToolTipCtrl destructor"
  - "CMFCPropertyGridToolTipCtrl class"
  - "CMFCPropertyGridToolTipCtrl class, destructor"
  - "PreTranslateMessage method"
ms.assetid: 84b436e5-6695-4da0-9569-1a875e087711
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPropertyGridToolTipCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un control de información sobre herramientas que [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md) utiliza para mostrar información sobre herramientas.  
  
## Sintaxis  
  
```  
class CMFCPropertyGridToolTipCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl](../Topic/CMFCPropertyGridToolTipCtrl::CMFCPropertyGridToolTipCtrl.md)|Crea un objeto `CMFCPropertyGridToolTipCtrl`.|  
|`CMFCPropertyGridToolTipCtrl::~CMFCPropertyGridToolTipCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCPropertyGridToolTipCtrl::Create](../Topic/CMFCPropertyGridToolTipCtrl::Create.md)|Crea una ventana para el control de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Deactivate](../Topic/CMFCPropertyGridToolTipCtrl::Deactivate.md)|Desactiva y oculta el control tooltip.|  
|[CMFCPropertyGridToolTipCtrl::GetLastRect](../Topic/CMFCPropertyGridToolTipCtrl::GetLastRect.md)|Devuelve las coordenadas de posición del control de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Hide](../Topic/CMFCPropertyGridToolTipCtrl::Hide.md)|Oculta el control tooltip.|  
|`CMFCPropertyGridToolTipCtrl::PreTranslateMessage`|Utiliza la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se envíen a las funciones de [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y de [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows.  \(Reemplaza [CWnd::PreTranslateMessage](../Topic/CWnd::PreTranslateMessage.md).\)|  
|[CMFCPropertyGridToolTipCtrl::SetTextMargin](../Topic/CMFCPropertyGridToolTipCtrl::SetTextMargin.md)|Establece el espaciado entre el texto de información sobre herramientas y el borde de la ventana de información sobre herramientas.|  
|[CMFCPropertyGridToolTipCtrl::Track](../Topic/CMFCPropertyGridToolTipCtrl::Track.md)|Muestra el control de información sobre herramientas.|  
  
## Comentarios  
 Se muestra la información sobre herramientas cuando el puntero se encuentra sobre un nombre de propiedad.  Muestra de clase de [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md) una información sobre herramientas para que sea fácilmente legible por el usuario.  Normalmente, la posición de una información sobre herramientas viene determinada por la posición del puntero.  Con esta clase, la información sobre herramientas aparece sobre el nombre y se parece a la extensión natural de la propiedad, de modo que el nombre de propiedad sea totalmente visible.  
  
 MFC crea automáticamente este control y lo utiliza en [CMFCPropertyGridCtrl Class](../../mfc/reference/cmfcpropertygridctrl-class.md).  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCPropertyGridToolTipCtrl` , y cómo mostrar el control tooltip.  
  
 [!code-cpp[NVC_MFC_RibbonApp#23](../../mfc/reference/codesnippet/CPP/cmfcpropertygridtooltipctrl-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCPropertyGridToolTipCtrl](../../mfc/reference/cmfcpropertygridtooltipctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxpropertygridtooltipctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)