---
title: "CMFCHeaderCtrl Class | Microsoft Docs"
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
  - "CMFCHeaderCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCHeaderCtrl class"
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCHeaderCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCHeaderCtrl` admite ordenar varias columnas en un control de encabezado.  
  
## Sintaxis  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](../Topic/CMFCHeaderCtrl::CMFCHeaderCtrl.md)|Crea un objeto `CMFCHeaderCtrl`.|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::EnableMultipleSort](../Topic/CMFCHeaderCtrl::EnableMultipleSort.md)|Habilita o deshabilita el modo *múltiple de ordenación de la columna* para el control de encabezado actual.|  
|[CMFCHeaderCtrl::GetColumnState](../Topic/CMFCHeaderCtrl::GetColumnState.md)|Indica si una columna no está ordenada, o se ordena de forma ascendente o descendente.|  
|[CMFCHeaderCtrl::GetSortColumn](../Topic/CMFCHeaderCtrl::GetSortColumn.md)|Recupera el índice de base cero de la primera columna ordenada en el control de encabezado.|  
|`CMFCHeaderCtrl::GetThisClass`|Utiliza el marco para obtener un puntero al objeto de [Recursos](../../mfc/reference/cruntimeclass-structure.md) que está asociado a este tipo de clase.|  
|[CMFCHeaderCtrl::IsAscending](../Topic/CMFCHeaderCtrl::IsAscending.md)|Indica si las columnas en el control de encabezado está ordenada de forma ascendente.|  
|[CMFCHeaderCtrl::IsDialogControl](../Topic/CMFCHeaderCtrl::IsDialogControl.md)|Indica si la ventana principal del control de encabezado actual es un cuadro de diálogo.|  
|[CMFCHeaderCtrl::IsMultipleSort](../Topic/CMFCHeaderCtrl::IsMultipleSort.md)|Indica si el control de encabezado actual está en modo *múltiple de ordenación de la columna* .|  
|[CMFCHeaderCtrl::RemoveSortColumn](../Topic/CMFCHeaderCtrl::RemoveSortColumn.md)|Quita la columna especificada de la lista de columnas ordenadas.|  
|[CMFCHeaderCtrl::SetSortColumn](../Topic/CMFCHeaderCtrl::SetSortColumn.md)|Establece el criterio de ordenación de una columna especificada en un control de encabezado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](../Topic/CMFCHeaderCtrl::OnDrawItem.md)|Llamado por el marco para dibujar una columna de control de encabezado.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](../Topic/CMFCHeaderCtrl::OnDrawSortArrow.md)|Llamado por el marco para dibujar la flecha de la ordenación.|  
|[CMFCHeaderCtrl::OnFillBackground](../Topic/CMFCHeaderCtrl::OnFillBackground.md)|Llamado por el marco para rellenar el fondo de una columna de control de encabezado.|  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCHeaderCtrl` , y cómo habilitar *la columna varios ordenar* el modo para el control de encabezado actual.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/CPP/cmfcheaderctrl-class_1.cpp)]  
  
## Comentarios  
 La clase de `CMFCHeaderCtrl` dibuja una flecha de ordenación de una columna de control de encabezado para indicar que la columna está ordenada.  Utilice el modo *múltiple de ordenación de la columna* si un conjunto de columnas en el control de lista primario \([CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)\) puede ser el tamaño al mismo tiempo.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxheaderctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)