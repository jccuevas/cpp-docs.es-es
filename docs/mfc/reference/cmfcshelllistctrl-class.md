---
title: "CMFCShellListCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCShellListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCShellListCtrl class"
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCShellListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCShellListCtrl` proporciona funcionalidad de control de lista de Windows y expandirlo incluida la capacidad para mostrar una lista de elementos de shell.  
  
## Sintaxis  
  
```  
class CMFCShellListCtrl : public CMFCListCtrl  
```  
  
## Members  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCShellListCtrl::DisplayFolder](../Topic/CMFCShellListCtrl::DisplayFolder.md)|Muestra una lista de elementos contenidos en una carpeta proporcionada.|  
|[CMFCShellListCtrl::DisplayParentFolder](../Topic/CMFCShellListCtrl::DisplayParentFolder.md)|Muestra una lista de elementos contenidos en la carpeta que es el elemento primario de la carpeta mostrada actualmente.|  
|[CMFCShellListCtrl::EnableShellContextMenu](../Topic/CMFCShellListCtrl::EnableShellContextMenu.md)|Habilita o deshabilita el menú contextual.|  
|[CMFCShellListCtrl::GetCurrentFolder](../Topic/CMFCShellListCtrl::GetCurrentFolder.md)|Recupera la ruta de acceso de la carpeta actual.|  
|[CMFCShellListCtrl::GetCurrentFolderName](../Topic/CMFCShellListCtrl::GetCurrentFolderName.md)|recupera el nombre de la carpeta actual.|  
|[CMFCShellListCtrl::GetCurrentItemIdList](../Topic/CMFCShellListCtrl::GetCurrentItemIdList.md)|Devuelve el PIDL del elemento del control de lista actual.|  
|[CMFCShellListCtrl::GetCurrentShellFolder](../Topic/CMFCShellListCtrl::GetCurrentShellFolder.md)|Devuelve un puntero a la carpeta actual de shell.|  
|[CMFCShellListCtrl::GetItemPath](../Topic/CMFCShellListCtrl::GetItemPath.md)|Devuelve la ruta de texto de un elemento.|  
|[CMFCShellListCtrl::GetItemTypes](../Topic/CMFCShellListCtrl::GetItemTypes.md)|Devuelve los tipos de elemento de shell mostrados por el control de lista.|  
|[CMFCShellListCtrl::IsDesktop](../Topic/CMFCShellListCtrl::IsDesktop.md)|Comprueba si la carpeta actualmente seleccionada es la carpeta de escritorio.|  
|[CMFCShellListCtrl::OnCompareItems](../Topic/CMFCShellListCtrl::OnCompareItems.md)|El marco de trabajo llama a este método cuando compara dos elementos.  \(Reemplaza [CMFCListCtrl::OnCompareItems](../Topic/CMFCListCtrl::OnCompareItems.md).\)|  
|[CMFCShellListCtrl::OnFormatFileDate](../Topic/CMFCShellListCtrl::OnFormatFileDate.md)|Se llama cuando el marco recupera la fecha del archivo mostrada por el control de lista.|  
|[CMFCShellListCtrl::OnFormatFileSize](../Topic/CMFCShellListCtrl::OnFormatFileSize.md)|Se llama cuando el marco convierte el tamaño de un control de lista.|  
|[CMFCShellListCtrl::OnGetItemIcon](../Topic/CMFCShellListCtrl::OnGetItemIcon.md)|Se llama cuando el marco recupera el icono de un elemento de control list.|  
|[CMFCShellListCtrl::OnGetItemText](../Topic/CMFCShellListCtrl::OnGetItemText.md)|Se llama cuando el marco convierte el texto de un elemento de control list.|  
|[CMFCShellListCtrl::OnSetColumns](../Topic/CMFCShellListCtrl::OnSetColumns.md)|Llamado por el marco cuando establece los nombres de las columnas.|  
|[CMFCShellListCtrl::Refresh](../Topic/CMFCShellListCtrl::Refresh.md)|Actualiza redibuje y el control de lista.|  
|[CMFCShellListCtrl::SetItemTypes](../Topic/CMFCShellListCtrl::SetItemTypes.md)|Establece el tipo de elementos mostrados por el control de lista.|  
  
## Comentarios  
 La clase de `CMFCShellListCtrl` extiende la funcionalidad de [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md) habilitando el programa para enumerar elementos del shell de Windows.  El tamaño de representación se utiliza como el de una vista de lista para una ventana del Explorador.  
  
 Un objeto de [CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md) puede estar asociado a un objeto de `CMFCShellListCtrl` crear una ventana completa del Explorador.  A continuación, la selección de un elemento de `CMFCShellTreeCtrl` hará que el objeto de `CMFCShellListCtrl` para enumerar el contenido del elemento seleccionado.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo crear un objeto de clase de `CMFCShellListCtrl` y cómo mostrar la carpeta primaria de la carpeta mostrada actualmente.  Este fragmento de código es parte de [Ejemplo explorer](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_2.cpp)]  
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/CPP/cmfcshelllistctrl-class_3.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
 [CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)  
  
## Requisitos  
 **encabezado:** afxshelllistCtrl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl Class](../../mfc/reference/cmfclistctrl-class.md)   
 [CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)