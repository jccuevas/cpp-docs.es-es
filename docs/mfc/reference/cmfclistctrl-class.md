---
title: "CMFCListCtrl Class | Microsoft Docs"
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
  - "CMFCListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCListCtrl class"
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: 29
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCListCtrl` extiende la funcionalidad de la clase de [CListCtrl Class](../../mfc/reference/clistctrl-class.md) admitiendo la funcionalidad avanzada del control de encabezado de [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## Sintaxis  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](../Topic/CMFCListCtrl::EnableMarkSortedColumn.md)|Habilita la capacidad de marcar una columna ordenada con un color de fondo diferente.|  
|[CMFCListCtrl::EnableMultipleSort](../Topic/CMFCListCtrl::EnableMultipleSort.md)|Habilita el modo de ordenación de múltiples.|  
|[CMFCListCtrl::GetHeaderCtrl](../Topic/CMFCListCtrl::GetHeaderCtrl.md)|Devuelve una referencia al control de encabezado subrayado.|  
|[CMFCListCtrl::IsMultipleSort](../Topic/CMFCListCtrl::IsMultipleSort.md)|Comprueba si el control de lista está en varias ordenan el modo.|  
|[CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md)|Llamado por el marco cuando debe comparar dos elementos del control de lista.|  
|[CMFCListCtrl::OnGetCellBkColor](../Topic/CMFCListCtrl::OnGetCellBkColor.md)|Llamado por el marco cuando debe determinar el color de fondo de una celda individual.|  
|[CMFCListCtrl::OnGetCellFont](../Topic/CMFCListCtrl::OnGetCellFont.md)|Llamado por el marco cuando debe obtener a la fuente de la celda que se dibuja.|  
|[CMFCListCtrl::OnGetCellTextColor](../Topic/CMFCListCtrl::OnGetCellTextColor.md)|Llamado por el marco cuando debe determinar el color del texto de una celda individual.|  
|[CMFCListCtrl::RemoveSortColumn](../Topic/CMFCListCtrl::RemoveSortColumn.md)|Quita una columna de ordenación de la lista de columnas ordenadas.|  
|[CMFCListCtrl::SetSortColumn](../Topic/CMFCListCtrl::SetSortColumn.md)|Establece la columna ordenada actual y el criterio de ordenación.|  
|[CMFCListCtrl::Sort](../Topic/CMFCListCtrl::Sort.md)|Ordena el control de lista.|  
  
## Comentarios  
 `CMFCListCtrl` proporciona dos mejoras a la clase de [CListCtrl Class](../../mfc/reference/clistctrl-class.md) .  Primero, indica que la ordenación de columnas es una opción disponible automáticamente dibujando una flecha de ordenación en el encabezado.  En segundo lugar, admite la ordenación de los datos en columnas simultáneamente.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCListCtrl` .  El ejemplo muestra cómo crear un control de lista, inserte las columnas, elementos de inserción, establece el texto de un elemento, y establece la fuente del control de lista.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/CPP/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/CPP/cmfclistctrl-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxlistctrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CListCtrl Class](../../mfc/reference/clistctrl-class.md)