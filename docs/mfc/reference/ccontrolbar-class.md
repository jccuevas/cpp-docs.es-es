---
title: "CControlBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CControlBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CControlBar class"
  - "control bars [C++], clase base"
  - "dialog bars, clase base"
  - "OLE resize bars"
  - "OLE resize bars, clase base"
  - "barras de estado, clase base"
  - "barras de herramientas [C++], clase base"
ms.assetid: 4d668c55-9b42-4838-97ac-cf2b3000b82c
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CControlBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Clase base para las clases de barra de controles [CStatusBar](../../mfc/reference/cstatusbar-class.md), [CToolBar](../../mfc/reference/ctoolbar-class.md), [CDialogBar](../../mfc/reference/cdialogbar-class.md), [CReBar](../../mfc/reference/crebar-class.md) y [COleResizeBar](../../mfc/reference/coleresizebar-class.md).  
  
## Sintaxis  
  
```  
class CControlBar : public CWnd  
```  
  
## Miembros  
  
### Constructores protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CControlBar::CControlBar](../Topic/CControlBar::CControlBar.md)|Construye un objeto `CControlBar`.|  
  
### Métodos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CControlBar::CalcDynamicLayout](../Topic/CControlBar::CalcDynamicLayout.md)|Devuelve el tamaño de una barra de controles dinámica como un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md).|  
|[CControlBar::CalcFixedLayout](../Topic/CControlBar::CalcFixedLayout.md)|Devuelve el tamaño de la barra de controles como un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md).|  
|[CControlBar::CalcInsideRect](../Topic/CControlBar::CalcInsideRect.md)|Devuelve las dimensiones actuales del área de la barra de controles, incluidos los bordes.|  
|[CControlBar::DoPaint](../Topic/CControlBar::DoPaint.md)|Representa los bordes y la barra de redimensionamiento de la barra de controles.|  
|[CControlBar::DrawBorders](../Topic/CControlBar::DrawBorders.md)|Representa los bordes de la barra de controles.|  
|[CControlBar::DrawGripper](../Topic/CControlBar::DrawGripper.md)|Representa la barra de redimensionamiento de la barra de controles.|  
|[CControlBar::EnableDocking](../Topic/CControlBar::EnableDocking.md)|Permite que una barra de controles esté acoplada o flotante.|  
|[CControlBar::GetBarStyle](../Topic/CControlBar::GetBarStyle.md)|Recupera la configuración de estilo de la barra de controles.|  
|[CControlBar::GetBorders](../Topic/CControlBar::GetBorders.md)|Recupera los valores de borde de la barra de controles.|  
|[CControlBar::GetCount](../Topic/CControlBar::GetCount.md)|Devuelve el número de elementos que no son `HWND` de la barra de controles.|  
|[CControlBar::GetDockingFrame](../Topic/CControlBar::GetDockingFrame.md)|Devuelve un puntero al marco al que está acoplada una barra de controles.|  
|[CControlBar::IsFloating](../Topic/CControlBar::IsFloating.md)|Devuelve un valor distinto de cero si la barra de controles en cuestión es una barra de controles flotante.|  
|[CControlBar::OnUpdateCmdUI](../Topic/CControlBar::OnUpdateCmdUI.md)|Llama a los controladores de la interfaz de usuario de comandos.|  
|[CControlBar::SetBarStyle](../Topic/CControlBar::SetBarStyle.md)|Modifica la configuración de estilo de la barra de controles.|  
|[CControlBar::SetBorders](../Topic/CControlBar::SetBorders.md)|Establece los valores de borde de la barra de controles.|  
|[CControlBar::SetInPlaceOwner](../Topic/CControlBar::SetInPlaceOwner.md)|Cambia el propietario en contexto de una barra de controles.|  
  
### Miembros de datos públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CControlBar::m\_bAutoDelete](../Topic/CControlBar::m_bAutoDelete.md)|Si es distinto de cero, el objeto `CControlBar` se elimina cuando se destruye la barra de controles de Windows.|  
|[CControlBar::m\_pInPlaceOwner](../Topic/CControlBar::m_pInPlaceOwner.md)|Propietario en contexto de la barra de controles.|  
  
## Comentarios  
 Una barra de controles es una ventana que suele estar alineada a la izquierda o a la derecha de una ventana de marco.  Puede contener elementos secundarios que son controles basados en `HWND`, que son ventanas que generan y responden a los mensajes de Windows, o elementos no basados en `HWND`, que no son ventanas y se administran mediante el código de la aplicación o el código del marco.  Los cuadros de lista y los controles de edición son ejemplos de controles basados en `HWND`; los paneles de la barra de estado y los botones de mapa de bits son ejemplos de controles no basados en `HWND`.  
  
 Las ventanas de barra de controles suelen ser ventanas secundarias de una ventana de marco principal y suelen ser elementos relacionados de la vista del cliente o del cliente MDI de la ventana de marco.  Un objeto `CControlBar` utiliza información acerca del rectángulo cliente de su ventana primaria para colocarse.  Después informa a la ventana primaria de cuánto espacio queda sin asignar en el área cliente de la ventana primaria.  
  
 Para obtener más información sobre `CControlBar`, vea:  
  
-   [Barras de controles](../../mfc/control-bars.md)  
  
-   [Nota técnica 31: barras de controles](../../mfc/tn031-control-bars.md).  
  
-   Artículo Q242577 de Knowledge Base: PRB: Los controladores de la interfaz de usuario de comandos de actualización no funcionan para un menú asociado a un cuadro de diálogo  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CControlBar`  
  
## Requisitos  
 **Encabezado:** afxext.h  
  
## Vea también  
 [CTRLBARS de ejemplo de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CToolBar Class](../../mfc/reference/ctoolbar-class.md)   
 [CDialogBar Class](../../mfc/reference/cdialogbar-class.md)   
 [CStatusBar Class](../../mfc/reference/cstatusbar-class.md)   
 [CReBar Class](../../mfc/reference/crebar-class.md)