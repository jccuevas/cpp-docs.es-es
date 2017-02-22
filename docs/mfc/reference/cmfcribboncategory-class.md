---
title: "CMFCRibbonCategory Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonCategory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonCategory class"
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
caps.latest.revision: 38
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 40
---
# CMFCRibbonCategory Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonCategory` implementa una ficha de cinta que contiene un grupo de [paneles de la cinta de opciones](../../mfc/reference/cmfcribbonpanel-class.md).  
  
## Sintaxis  
  
```  
class CMFCRibbonCategory : public CObject  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCategory::CMFCRibbonCategory](../Topic/CMFCRibbonCategory::CMFCRibbonCategory.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonCategory::AddHidden](../Topic/CMFCRibbonCategory::AddHidden.md)|Agrega un elemento sombreado a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::AddPanel](../Topic/CMFCRibbonCategory::AddPanel.md)|Agregar un nuevo panel a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::CopyFrom](../Topic/CMFCRibbonCategory::CopyFrom.md)||  
|[CMFCRibbonCategory::FindByData](../Topic/CMFCRibbonCategory::FindByData.md)||  
|[CMFCRibbonCategory::FindByID](../Topic/CMFCRibbonCategory::FindByID.md)||  
|[CMFCRibbonCategory::FindPanelWithElem](../Topic/CMFCRibbonCategory::FindPanelWithElem.md)||  
|[CMFCRibbonCategory::GetContextID](../Topic/CMFCRibbonCategory::GetContextID.md)|devuelve el Id. de contexto de la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::GetData](../Topic/CMFCRibbonCategory::GetData.md)|Devuelve los datos definidos por el usuario que está asociado a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::GetDroppedDown](../Topic/CMFCRibbonCategory::GetDroppedDown.md)||  
|[CMFCRibbonCategory::GetElements](../Topic/CMFCRibbonCategory::GetElements.md)||  
|[CMFCRibbonCategory::GetElementsByID](../Topic/CMFCRibbonCategory::GetElementsByID.md)||  
|[CMFCRibbonCategory::GetFirstVisibleElement](../Topic/CMFCRibbonCategory::GetFirstVisibleElement.md)|obtenga un primer elemento visible que pertenece a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::GetFocused](../Topic/CMFCRibbonCategory::GetFocused.md)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonCategory::GetHighlighted](../Topic/CMFCRibbonCategory::GetHighlighted.md)|Devuelve un elemento resaltado.|  
|[CMFCRibbonCategory::GetImageCount](../Topic/CMFCRibbonCategory::GetImageCount.md)||  
|[CMFCRibbonCategory::GetImageSize](../Topic/CMFCRibbonCategory::GetImageSize.md)||  
|[CMFCRibbonCategory::GetItemIDsList](../Topic/CMFCRibbonCategory::GetItemIDsList.md)||  
|[CMFCRibbonCategory::GetLastVisibleElement](../Topic/CMFCRibbonCategory::GetLastVisibleElement.md)|Obtenga un último elemento visible que pertenece a la categoría de la cinta de opciones|  
|[CMFCRibbonCategory::GetLargeImages](../Topic/CMFCRibbonCategory::GetLargeImages.md)|devuelve una referencia a la lista de imágenes grandes que la categoría de la cinta de opciones utilice.|  
|[CMFCRibbonCategory::GetMaxHeight](../Topic/CMFCRibbonCategory::GetMaxHeight.md)||  
|[CMFCRibbonCategory::GetName](../Topic/CMFCRibbonCategory::GetName.md)||  
|[CMFCRibbonCategory::GetPanel](../Topic/CMFCRibbonCategory::GetPanel.md)|Devuelve un puntero al panel de la cinta que se encuentra en el índice especificado.|  
|[CMFCRibbonCategory::GetPanelCount](../Topic/CMFCRibbonCategory::GetPanelCount.md)|Devuelve el número de paneles de la cinta de opciones en la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::GetPanelFromPoint](../Topic/CMFCRibbonCategory::GetPanelFromPoint.md)||  
|[CMFCRibbonCategory::GetPanelIndex](../Topic/CMFCRibbonCategory::GetPanelIndex.md)|Devuelve el índice del panel especificado de la cinta de opciones.|  
|[CMFCRibbonCategory::GetParentButton](../Topic/CMFCRibbonCategory::GetParentButton.md)||  
|[CMFCRibbonCategory::GetParentMenuBar](../Topic/CMFCRibbonCategory::GetParentMenuBar.md)||  
|[CMFCRibbonCategory::GetParentRibbonBar](../Topic/CMFCRibbonCategory::GetParentRibbonBar.md)||  
|[CMFCRibbonCategory::GetRect](../Topic/CMFCRibbonCategory::GetRect.md)||  
|[CMFCRibbonCategory::GetSmallImages](../Topic/CMFCRibbonCategory::GetSmallImages.md)|devuelve una referencia a la lista de pequeñas imágenes que la categoría utilice.|  
|[CMFCRibbonCategory::GetTabColor](../Topic/CMFCRibbonCategory::GetTabColor.md)|Devuelve el color de tabulación de la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::GetTabRect](../Topic/CMFCRibbonCategory::GetTabRect.md)||  
|[CMFCRibbonCategory::GetTextTopLine](../Topic/CMFCRibbonCategory::GetTextTopLine.md)||  
|[CMFCRibbonCategory::GetVisibleElements](../Topic/CMFCRibbonCategory::GetVisibleElements.md)|Obtiene todos los elementos visibles que pertenecen a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::HighlightPanel](../Topic/CMFCRibbonCategory::HighlightPanel.md)||  
|[CMFCRibbonCategory::HitTest](../Topic/CMFCRibbonCategory::HitTest.md)||  
|[CMFCRibbonCategory::HitTestEx](../Topic/CMFCRibbonCategory::HitTestEx.md)||  
|[CMFCRibbonCategory::HitTestScrollButtons](../Topic/CMFCRibbonCategory::HitTestScrollButtons.md)||  
|[CMFCRibbonCategory::IsActive](../Topic/CMFCRibbonCategory::IsActive.md)||  
|[CMFCRibbonCategory::IsVisible](../Topic/CMFCRibbonCategory::IsVisible.md)|Determina si la categoría de la cinta de opciones está visible.|  
|[CMFCRibbonCategory::IsWindows7Look](../Topic/CMFCRibbonCategory::IsWindows7Look.md)|Indica si la cinta primario hace que el estilo de Windows 7 busque \(botoncito rectangular de la aplicación\)|  
|[CMFCRibbonCategory::NotifyControlCommand](../Topic/CMFCRibbonCategory::NotifyControlCommand.md)||  
|[CMFCRibbonCategory::OnCancelMode](../Topic/CMFCRibbonCategory::OnCancelMode.md)||  
|[CMFCRibbonCategory::OnDraw](../Topic/CMFCRibbonCategory::OnDraw.md)||  
|[CMFCRibbonCategory::OnDrawImage](../Topic/CMFCRibbonCategory::OnDrawImage.md)||  
|[CMFCRibbonCategory::OnDrawMenuBorder](../Topic/CMFCRibbonCategory::OnDrawMenuBorder.md)||  
|[CMFCRibbonCategory::OnKey](../Topic/CMFCRibbonCategory::OnKey.md)|Llamado por el marco cuando un usuario presiona un botón de teclado.|  
|[CMFCRibbonCategory::OnLButtonDown](../Topic/CMFCRibbonCategory::OnLButtonDown.md)||  
|[CMFCRibbonCategory::OnLButtonUp](../Topic/CMFCRibbonCategory::OnLButtonUp.md)||  
|[CMFCRibbonCategory::OnMouseMove](../Topic/CMFCRibbonCategory::OnMouseMove.md)||  
|[CMFCRibbonCategory::OnRTLChanged](../Topic/CMFCRibbonCategory::OnRTLChanged.md)||  
|[CMFCRibbonCategory::OnScrollHorz](../Topic/CMFCRibbonCategory::OnScrollHorz.md)||  
|[CMFCRibbonCategory::OnUpdateCmdUI](../Topic/CMFCRibbonCategory::OnUpdateCmdUI.md)||  
|[CMFCRibbonCategory::RecalcLayout](../Topic/CMFCRibbonCategory::RecalcLayout.md)||  
|[CMFCRibbonCategory::RemovePanel](../Topic/CMFCRibbonCategory::RemovePanel.md)||  
|[CMFCRibbonCategory::ReposPanels](../Topic/CMFCRibbonCategory::ReposPanels.md)||  
|[CMFCRibbonCategory::SetCollapseOrder](../Topic/CMFCRibbonCategory::SetCollapseOrder.md)|Define el orden de recepción de los paneles de la cinta que se encuentran en la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::SetData](../Topic/CMFCRibbonCategory::SetData.md)|Almacena los datos definidos por el usuario en la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::SetKeys](../Topic/CMFCRibbonCategory::SetKeys.md)|asigna un keytip a la categoría de la cinta de opciones.|  
|[CMFCRibbonCategory::SetName](../Topic/CMFCRibbonCategory::SetName.md)||  
|[CMFCRibbonCategory::SetTabColor](../Topic/CMFCRibbonCategory::SetTabColor.md)|Establece el color de la categoría de la cinta de opciones.|  
  
## Comentarios  
 Normalmente, se crea una categoría de la cinta de opciones indirectamente llamando a [CMFCRibbonBar::AddCategory](../Topic/CMFCRibbonBar::AddCategory.md), que devuelve un puntero a la categoría creada recientemente de la cinta de opciones.  Agregue los paneles a la categoría llamando a [CMFCRibbonCategory::AddPanel](../Topic/CMFCRibbonCategory::AddPanel.md).  
  
 La clase de `CMFCRibbonTab` dibuja categorías de la cinta de opciones.  es derivada de [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md).  
  
 El ejemplo siguiente muestra cómo crear una categoría de la cinta de opciones y agregar un panel a.  
  
 `// Create a new ribbon category and get a pointer to it`  
  
 `CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory`  
  
 `(_T("&Write"),           // Category name`  
  
 `IDB_WRITE,              // Category small images (16 x 16)`  
  
 `IDB_WRITE_LARGE);   // Category large images (32 x 32)`  
  
 `// Add a panel to the new category`  
  
 `CMFCRibbonPanel* pPanel = pCategory->AddPanel (`  
  
 `_T("Clipboard"),                       // Panel name`  
  
 `m_PanelIcons.ExtractIcon (0));  // Panel icon`  
  
 El diagrama siguiente se muestra una ilustración de la categoría principal de la aplicación de ejemplo de RibbonApp.  
  
 ![Imagen de CMFCRibbonCategory](../../mfc/reference/media/cmfcribboncategory.png "CMFCRibbonCategory")  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)  
  
## Requisitos  
 **encabezado:** afxribboncategory.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)