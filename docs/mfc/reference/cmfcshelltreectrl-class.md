---
title: "CMFCShellTreeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCShellTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellTreeCtrl class"
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCShellTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCShellTreeCtrl` extiende la funcionalidad de [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md) muestra una jerarquía de elementos de shell.  
  
## Sintaxis  
  
```  
class CMFCShellTreeCtrl : public CTreeCtrl  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCShellTreeCtrl::EnableShellContextMenu](../Topic/CMFCShellTreeCtrl::EnableShellContextMenu.md)|Habilita o deshabilita el menú contextual.|  
|[CMFCShellTreeCtrl::GetFlags](../Topic/CMFCShellTreeCtrl::GetFlags.md)|Devuelve una combinación de marcas que se pasen a [IShellFolder::EnumObjects](http://msdn.microsoft.com/library/windows/desktop/bb775066).|  
|[CMFCShellTreeCtrl::GetItemPath](../Topic/CMFCShellTreeCtrl::GetItemPath.md)|Recupera la ruta de acceso a un elemento.|  
|[CMFCShellTreeCtrl::GetRelatedList](../Topic/CMFCShellTreeCtrl::GetRelatedList.md)|Devuelve un puntero al objeto de [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md) que se utiliza junto con este objeto de `CMFCShellTreeCtrl` para crear Explorador\- como la ventana.|  
|[CMFCShellTreeCtrl::OnChildNotify](../Topic/CMFCShellTreeCtrl::OnChildNotify.md)|Esta función miembro llaman la ventana principal de esta ventana cuando recibe un mensaje de notificación que se aplique a esta ventana.  \(Reemplaza [CWnd::OnChildNotify](../Topic/CWnd::OnChildNotify.md).\)|  
|[CMFCShellTreeCtrl::OnGetItemIcon](../Topic/CMFCShellTreeCtrl::OnGetItemIcon.md)||  
|[CMFCShellTreeCtrl::OnGetItemText](../Topic/CMFCShellTreeCtrl::OnGetItemText.md)||  
|[CMFCShellTreeCtrl::Refresh](../Topic/CMFCShellTreeCtrl::Refresh.md)|Las actualizaciones y repintan el objeto actual de `CMFCShellTreeCtrl` .|  
|[CMFCShellTreeCtrl::SelectPath](../Topic/CMFCShellTreeCtrl::SelectPath.md)|Selecciona el elemento adecuado del control de árbol basada en una ruta proporcionada de PIDL o de cadena.|  
|[CMFCShellTreeCtrl::SetFlags](../Topic/CMFCShellTreeCtrl::SetFlags.md)|Los conjuntos se marcan para filtrar el contexto del árbol \(similar a los marcadores utilizados por `IShellFolder::EnumObjects`\).|  
|[CMFCShellTreeCtrl::SetRelatedList](../Topic/CMFCShellTreeCtrl::SetRelatedList.md)|Establece una relación entre el objeto actual de `CMFCShellTreeCtrl` y un objeto de `CMFCShellListCtrl` .|  
  
## Comentarios  
 Esta clase extiende la clase de `CTreeCtrl` habilitando el programa para incluir elementos del shell de Windows en el árbol.  Esta clase puede asociarse a un objeto de `CMFCShellListCtrl` para crear una ventana completa del Explorador.  A continuación, la selección de un elemento del árbol mostrará una lista de elementos del shell de Windows en la lista asociada.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CTreeCtrl](../../mfc/reference/ctreectrl-class.md)  
  
 [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)  
  
## Requisitos  
 **encabezado:** afxshelltreeCtrl.h  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo crear un objeto de clase de `CMFCShellTreeCtrl` .  Este fragmento de código es parte de [Ejemplo explorer](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/CPP/cmfcshelltreectrl-class_2.cpp)]  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)   
 [CMFCShellListCtrl Class](../../mfc/reference/cmfcshelllistctrl-class.md)