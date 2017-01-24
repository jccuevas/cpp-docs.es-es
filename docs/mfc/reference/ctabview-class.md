---
title: "CTabView Class | Microsoft Docs"
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
  - "CTabView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTabView class"
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTabView Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CTabView` simplifica el uso de la clase del control de ficha \([CMFCTabCtrl](../../mfc/reference/ctabview-class.md)\) en aplicaciones que utilizan el documento de MFC y la arquitectura de la vista.  
  
## Sintaxis  
  
```  
class CTabbedView : public CView  
```  
  
## Miembros  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabView::AddView](../Topic/CTabView::AddView.md)|Agrega una nueva vista al control de ficha.|  
|[CTabView::FindTab](../Topic/CTabView::FindTab.md)|Devuelve el índice de la vista especificada en el control de ficha.|  
|[CTabView::GetActiveView](../Topic/CTabView::GetActiveView.md)|Devuelve un puntero actualmente a la vista activa|  
|[CTabView::GetTabControl](../Topic/CTabView::GetTabControl.md)|Devuelve una referencia al control de ficha asociado a la vista.|  
|[CTabView::RemoveView](../Topic/CTabView::RemoveView.md)|Quita la vista de control de la ficha.|  
|[CTabView::SetActiveView](../Topic/CTabView::SetActiveView.md)|Crea un activo de la vista.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTabView::IsScrollBar](../Topic/CTabView::IsScrollBar.md)|Llamado por el marco al crear una vista de la pestaña para determinar si la vista de la ficha tiene una barra de desplazamiento horizontal compartida.|  
|[CTabView::OnActivateView](../Topic/CTabView::OnActivateView.md)|Llamado por el marco cuando la vista de la pestaña se crea activo o inactivo.|  
  
## Comentarios  
 Esta clase crea fácil colocar una vista con fichas en una aplicación de documento y vista.  `CTabView` es `CView`\- la clase derivada que contiene un objeto incrustado de `CMFCTabCtrl` .  `CTabView` controla todos los mensajes necesarios para admitir el objeto de `CMFCTabCtrl` .  Deriva simplemente una clase de `CTabView` y tápela en la aplicación, agregue `CView`\- clases derivadas utilizando el método de `AddView` .  El control de ficha mostrará esas vistas como fichas.  
  
 Por ejemplo, podría tener un documento que se puede representar de maneras diferentes: como hoja de cálculo, un gráfico, un formulario modificable, etc.  Puede crear vistas individuales que dibujan los datos según sea necesario, insertarlos en `CTabView`\- objeto derivado y hacer tabular sin ninguna codificación adicional.  
  
 [ejemplo de TabbedView: MFC con la aplicación de visualización](../../top/visual-cpp-samples.md) muestra el uso de `CTabView`.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo `CTabView` se utiliza en el ejemplo de TabbedView.  
  
 [!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/CPP/ctabview-class_1.h)]  
  
## Requisitos  
 **encabezado:** afxTabView.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CTabView Class](../../mfc/reference/ctabview-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)