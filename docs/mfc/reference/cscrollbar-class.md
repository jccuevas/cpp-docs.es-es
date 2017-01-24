---
title: "CScrollBar Class | Microsoft Docs"
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
  - "CScrollBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [MFC], barra de desplazamiento"
  - "CScrollBar class"
  - "barras de desplazamiento"
  - "SCROLLBAR window class"
  - "Windows common controls [C++], CScrollBar"
ms.assetid: f3735ca5-73ea-46dc-918b-4d824c9fe47f
caps.latest.revision: 21
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CScrollBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

proporciona la funcionalidad de un control de barra de desplazamiento de Windows.  
  
## Sintaxis  
  
```  
class CScrollBar : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollBar::CScrollBar](../Topic/CScrollBar::CScrollBar.md)|Crea un objeto `CScrollBar`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CScrollBar::Create](../Topic/CScrollBar::Create.md)|Crea la barra de desplazamiento de Windows y la asocia al objeto de `CScrollBar` .|  
|[CScrollBar::EnableScrollBar](../Topic/CScrollBar::EnableScrollBar.md)|Habilita o deshabilita una o ambas flechas de una barra de desplazamiento.|  
|[CScrollBar::GetScrollBarInfo](../Topic/CScrollBar::GetScrollBarInfo.md)|Recupera información sobre la barra de desplazamiento mediante una estructura de `SCROLLBARINFO` .|  
|[CScrollBar::GetScrollInfo](../Topic/CScrollBar::GetScrollInfo.md)|Recupera información sobre la barra de desplazamiento.|  
|[CScrollBar::GetScrollLimit](../Topic/CScrollBar::GetScrollLimit.md)|recupera el límite de la barra de desplazamiento|  
|[CScrollBar::GetScrollPos](../Topic/CScrollBar::GetScrollPos.md)|Recupera la posición actual de un cuadro de desplazamiento.|  
|[CScrollBar::GetScrollRange](../Topic/CScrollBar::GetScrollRange.md)|Recupera las posiciones actuales de mínimo y la barra de desplazamiento de máximo para la barra de desplazamiento determinada.|  
|[CScrollBar::SetScrollInfo](../Topic/CScrollBar::SetScrollInfo.md)|establece la información sobre la barra de desplazamiento.|  
|[CScrollBar::SetScrollPos](../Topic/CScrollBar::SetScrollPos.md)|Establece la posición actual de un cuadro de desplazamiento.|  
|[CScrollBar::SetScrollRange](../Topic/CScrollBar::SetScrollRange.md)|Establece los valores mínimos y máximos de la posición de la barra de desplazamiento determinada.|  
|[CScrollBar::ShowScrollBar](../Topic/CScrollBar::ShowScrollBar.md)|Muestra u oculta una barra de desplazamiento.|  
  
## Comentarios  
 Crea un control de barra de desplazamiento en dos pasos.  Primero, llame al constructor `CScrollBar` para construir el objeto de `CScrollBar` , llame a la función miembro de [Crear](../Topic/CScrollBar::Create.md) para crear el control de barra de desplazamiento de Windows y para adjuntarlo al objeto de `CScrollBar` .  
  
 Si crea un objeto de `CScrollBar` dentro de un cuadro de diálogo \(a través de un recurso de cuadro de diálogo\), `CScrollBar` automáticamente se destruye cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un objeto de `CScrollBar` dentro de una ventana, puede necesitar también destruirla.  
  
 Si crea el objeto de `CScrollBar` en la pila, se destruye automáticamente.  Si crea el objeto de `CScrollBar` en la pila mediante la función de **nuevo** , debe llamar a **cancelación** en el objeto para destruirlo cuando el usuario finaliza la barra de desplazamiento de Windows.  
  
 Si asigna cualquier memoria en el objeto de `CScrollBar` , reemplace `CScrollBar` destructor para destruyen las asignaciones.  
  
 Para obtener información relacionada sobre el uso `CScrollBar`, vea [Controles](../../mfc/controls-mfc.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CScrollBar`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [CButton Class](../../mfc/reference/cbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CEdit Class](../../mfc/reference/cedit-class.md)   
 [CListBox Class](../../mfc/reference/clistbox-class.md)   
 [CStatic Class](../../mfc/reference/cstatic-class.md)   
 [CDialog Class](../../mfc/reference/cdialog-class.md)