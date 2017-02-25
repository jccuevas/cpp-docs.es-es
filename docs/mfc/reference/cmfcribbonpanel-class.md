---
title: "CMFCRibbonPanel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonPanel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonPanel class"
ms.assetid: 51d70749-1140-4386-b103-f14082049ba6
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 36
---
# CMFCRibbonPanel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un panel que contiene un conjunto de elementos de cinta de opciones.  Cuando se dibuja el panel, muestra tantos elementos como sea posible, dado el tamaño del panel.  
  
## Sintaxis  
  
```  
class CMFCRibbonPanel : public CObject  
```  
  
## Members  
  
### Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonPanel::CMFCRibbonPanel](../Topic/CMFCRibbonPanel::CMFCRibbonPanel.md)|Las construcciones e inicializan un objeto de `CMFCRibbonPanel` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonPanel::Add](../Topic/CMFCRibbonPanel::Add.md)|Agrega un elemento cinta al panel.|  
|[CMFCRibbonPanel::AddSeparator](../Topic/CMFCRibbonPanel::AddSeparator.md)|Agrega un separador al panel de la cinta de opciones.|  
|[CMFCRibbonPanel::AddToolBar](../Topic/CMFCRibbonPanel::AddToolBar.md)|Agrega una barra de herramientas del panel de la cinta de opciones.|  
|[CMFCRibbonPanel::FindByData](../Topic/CMFCRibbonPanel::FindByData.md)||  
|[CMFCRibbonPanel::FindByID](../Topic/CMFCRibbonPanel::FindByID.md)|Devuelve un elemento identificado por un identificador especificada de comando|  
|[CMFCRibbonPanel::GetCaptionHeight](../Topic/CMFCRibbonPanel::GetCaptionHeight.md)||  
|[CMFCRibbonPanel::GetCount](../Topic/CMFCRibbonPanel::GetCount.md)|Devuelve el número de elementos en el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::GetData](../Topic/CMFCRibbonPanel::GetData.md)|Devuelve los datos definidos por el usuario asociado al panel.|  
|[CMFCRibbonPanel::GetDefaultButton](../Topic/CMFCRibbonPanel::GetDefaultButton.md)||  
|[CMFCRibbonPanel::GetDroppedDown](../Topic/CMFCRibbonPanel::GetDroppedDown.md)||  
|[CMFCRibbonPanel::GetElement](../Topic/CMFCRibbonPanel::GetElement.md)|Devuelve el elemento cinta situado en el índice especificado.|  
|[CMFCRibbonPanel::GetElements](../Topic/CMFCRibbonPanel::GetElements.md)|Recupera todos los elementos contenidos en el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::GetElementsByID](../Topic/CMFCRibbonPanel::GetElementsByID.md)||  
|[CMFCRibbonPanel::GetFocused](../Topic/CMFCRibbonPanel::GetFocused.md)|Devuelve un elemento que tiene el foco.|  
|[CMFCRibbonPanel::GetGalleryRect](../Topic/CMFCRibbonPanel::GetGalleryRect.md)|Devuelve un rectángulo delimitador del elemento de la galería.|  
|[CMFCRibbonPanel::GetHighlighted](../Topic/CMFCRibbonPanel::GetHighlighted.md)||  
|[CMFCRibbonPanel::GetIndex](../Topic/CMFCRibbonPanel::GetIndex.md)||  
|[CMFCRibbonPanel::GetItemIDsList](../Topic/CMFCRibbonPanel::GetItemIDsList.md)||  
|[CMFCRibbonPanel::GetName](../Topic/CMFCRibbonPanel::GetName.md)||  
|[CMFCRibbonPanel::GetParentButton](../Topic/CMFCRibbonPanel::GetParentButton.md)||  
|[CMFCRibbonPanel::GetParentCategory](../Topic/CMFCRibbonPanel::GetParentCategory.md)|Devuelve la categoría primaria del panel de la cinta de opciones.|  
|[CMFCRibbonPanel::GetParentMenuBar](../Topic/CMFCRibbonPanel::GetParentMenuBar.md)||  
|[CMFCRibbonPanel::GetPreferedMenuLocation](../Topic/CMFCRibbonPanel::GetPreferedMenuLocation.md)||  
|[CMFCRibbonPanel::GetPressed](../Topic/CMFCRibbonPanel::GetPressed.md)||  
|[CMFCRibbonPanel::GetRect](../Topic/CMFCRibbonPanel::GetRect.md)||  
|[CMFCRibbonPanel::GetVisibleElements](../Topic/CMFCRibbonPanel::GetVisibleElements.md)|Obtiene una matriz de elementos visibles.|  
|[CMFCRibbonPanel::HasElement](../Topic/CMFCRibbonPanel::HasElement.md)||  
|[CMFCRibbonPanel::HitTest](../Topic/CMFCRibbonPanel::HitTest.md)||  
|[CMFCRibbonPanel::HitTestEx](../Topic/CMFCRibbonPanel::HitTestEx.md)||  
|[CMFCRibbonPanel::Insert](../Topic/CMFCRibbonPanel::Insert.md)|Inserta un elemento cinta en la posición especificada.|  
|[CMFCRibbonPanel::InsertSeparator](../Topic/CMFCRibbonPanel::InsertSeparator.md)|Inserta un separador en la posición especificada.|  
|[CMFCRibbonPanel::IsCenterColumnVert](../Topic/CMFCRibbonPanel::IsCenterColumnVert.md)|Especifica si todos los elementos panel deben centrar \(alineado\) verticalmente, por columna.|  
|[CMFCRibbonPanel::IsCollapsed](../Topic/CMFCRibbonPanel::IsCollapsed.md)||  
|[CMFCRibbonPanel::IsHighlighted](../Topic/CMFCRibbonPanel::IsHighlighted.md)||  
|[CMFCRibbonPanel::IsJustifyColumns](../Topic/CMFCRibbonPanel::IsJustifyColumns.md)|Especifica si todas las columnas del panel tienen el mismo ancho.|  
|[CMFCRibbonPanel::IsMainPanel](../Topic/CMFCRibbonPanel::IsMainPanel.md)||  
|[CMFCRibbonPanel::IsMenuMode](../Topic/CMFCRibbonPanel::IsMenuMode.md)||  
|[CMFCRibbonPanel::MakeGalleryItemVisible](../Topic/CMFCRibbonPanel::MakeGalleryItemVisible.md)|Desplaza la galería para que el elemento especificado de la cinta de opciones visible.|  
|[CMFCRibbonPanel::OnKey](../Topic/CMFCRibbonPanel::OnKey.md)||  
|[CMFCRibbonPanel::RecalcWidths](../Topic/CMFCRibbonPanel::RecalcWidths.md)||  
|[CMFCRibbonPanel::Remove](../Topic/CMFCRibbonPanel::Remove.md)|Quita y elimina opcionalmente un elemento situado en el índice especificado.|  
|[CMFCRibbonPanel::RemoveAll](../Topic/CMFCRibbonPanel::RemoveAll.md)|Quita todos los elementos del panel de la cinta de opciones.|  
|[CMFCRibbonPanel::Replace](../Topic/CMFCRibbonPanel::Replace.md)|Reemplaza un elemento con otro basándose en los valores de índice respectivos.|  
|[CMFCRibbonPanel::ReplaceByID](../Topic/CMFCRibbonPanel::ReplaceByID.md)|Reemplaza un elemento con otro basado en un identificador especificada de comando|  
|[CMFCRibbonPanel::SetCenterColumnVert](../Topic/CMFCRibbonPanel::SetCenterColumnVert.md)|Pide al panel para alinear elementos verticalmente, por columna.|  
|[CMFCRibbonPanel::SetData](../Topic/CMFCRibbonPanel::SetData.md)|Asocia datos definidos por el usuario al panel de la cinta de opciones.|  
|[CMFCRibbonPanel::SetElementMenu](../Topic/CMFCRibbonPanel::SetElementMenu.md)|Asigna un menú emergente el elemento que tiene el identificador determinada de comando|  
|[CMFCRibbonPanel::SetElementRTC](../Topic/CMFCRibbonPanel::SetElementRTC.md)|Agrega un elemento cinta especificado por la información proporcionada de la clase de runtime al panel de la cinta de opciones.|  
|[CMFCRibbonPanel::SetElementRTCByID](../Topic/CMFCRibbonPanel::SetElementRTCByID.md)|Agrega un elemento cinta especificado por la información proporcionada de la clase de runtime al panel de la cinta de opciones.|  
|[CMFCRibbonPanel::SetFocused](../Topic/CMFCRibbonPanel::SetFocused.md)|Establece el foco en el elemento especificado de la cinta de opciones.|  
|[CMFCRibbonPanel::SetJustifyColumns](../Topic/CMFCRibbonPanel::SetJustifyColumns.md)|Permisos o justificación de la columna de las neutralizaciones.|  
|[CMFCRibbonPanel::SetKeys](../Topic/CMFCRibbonPanel::SetKeys.md)|Establece el método abreviado de teclado que muestra el panel de la cinta de opciones.|  
|[CMFCRibbonPanel::ShowPopup](../Topic/CMFCRibbonPanel::ShowPopup.md)||  
  
## Comentarios  
 Los paneles de la cinta de opciones son agrupaciones lógicas de tareas relacionadas que se crea dentro de categorías de la cinta de opciones.  Como el tamaño de la cinta de opciones, el panel de diseño se ajusta automáticamente para mostrar tantos elementos como sea posible.  
  
 Puede obtener los paneles de una cinta incluido en una categoría de la cinta de opciones llamando al método de [CMFCRibbonCategory::GetPanel](../Topic/CMFCRibbonCategory::GetPanel.md) .  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo configurar un objeto de `CMFCRibbonPanel` mediante varios métodos en la clase de `CMFCRibbonPanel` .  El ejemplo muestra cómo establecer el método abreviado de teclado que muestra el panel de la cinta de opciones, los elementos alinear en el panel verticalmente por columna, y la justificación de la columna de permiso.  Este fragmento de código es parte de [Ejemplo 2007 de demostración de MS Office](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#10](../../mfc/reference/codesnippet/CPP/cmfcribbonpanel-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonPanel.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [CMFCRibbonCategory Class](../../mfc/reference/cmfcribboncategory-class.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)