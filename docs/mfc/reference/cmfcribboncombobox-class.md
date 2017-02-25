---
title: "CMFCRibbonComboBox Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonComboBox"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonComboBox class"
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 37
---
# CMFCRibbonComboBox Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCRibbonComboBox` implementa un control de cuadro combinado que puede agregar a una barra de la cinta de opciones, panel de la cinta de opciones, o un menú emergente de la cinta de opciones.  
  
## Sintaxis  
  
```  
class CMFCRibbonComboBox : public CMFCRibbonEdit  
```  
  
## Members  
  
### Constructores  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonComboBox::CMFCRibbonComboBox](../Topic/CMFCRibbonComboBox::CMFCRibbonComboBox.md)|construye un objeto de CMFCRibbonComboBox.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonComboBox::AddItem](../Topic/CMFCRibbonComboBox::AddItem.md)|Anexa un elemento único al cuadro de lista.|  
|[CMFCRibbonComboBox::DeleteItem](../Topic/CMFCRibbonComboBox::DeleteItem.md)|Elimina un elemento especificado del cuadro de lista.|  
|[CMFCRibbonComboBox::EnableDropDownListResize](../Topic/CMFCRibbonComboBox::EnableDropDownListResize.md)|Especifica si el cuadro de lista puede cambiar el tamaño cuando interrumpe a continuación.|  
|[CMFCRibbonComboBox::FindItem](../Topic/CMFCRibbonComboBox::FindItem.md)|Devuelve el índice del primer elemento del cuadro de lista que coincide con una cadena especificada.|  
|[CMFCRibbonComboBox::GetCount](../Topic/CMFCRibbonComboBox::GetCount.md)|Devuelve el número de elementos del cuadro de lista.|  
|[CMFCRibbonComboBox::GetCurSel](../Topic/CMFCRibbonComboBox::GetCurSel.md)|Obtiene el índice del elemento actualmente seleccionado en el cuadro de lista.|  
|[CMFCRibbonComboBox::GetDropDownHeight](../Topic/CMFCRibbonComboBox::GetDropDownHeight.md)|Obtiene el alto del cuadro de lista cuando el cuadro de lista se quita a continuación.|  
|[CMFCRibbonComboBox::GetIntermediateSize](../Topic/CMFCRibbonComboBox::GetIntermediateSize.md)|Devuelve el tamaño del cuadro combinado como se muestra en modo intermedio.|  
|[CMFCRibbonComboBox::GetItem](../Topic/CMFCRibbonComboBox::GetItem.md)|Devuelve la cadena asociado a un elemento en un índice especificado en el cuadro de lista.|  
|[CMFCRibbonComboBox::GetItemData](../Topic/CMFCRibbonComboBox::GetItemData.md)|Devuelve los datos asociados a un elemento en un índice especificado en el cuadro de lista.|  
|[CMFCRibbonComboBox::HasEditBox](../Topic/CMFCRibbonComboBox::HasEditBox.md)|indica si el control contiene un cuadro de edición.|  
|[CMFCRibbonComboBox::IsResizeDropDownList](../Topic/CMFCRibbonComboBox::IsResizeDropDownList.md)|Indica si el cuadro de lista puede cambiar de tamaño.|  
|[CMFCRibbonComboBox::OnSelectItem](../Topic/CMFCRibbonComboBox::OnSelectItem.md)|Llamado por el marco cuando el usuario selecciona un elemento en el cuadro de lista.|  
|[CMFCRibbonComboBox::RemoveAllItems](../Topic/CMFCRibbonComboBox::RemoveAllItems.md)|Elimina todos los elementos de cuadro de lista y borre el cuadro de edición.|  
|[CMFCRibbonComboBox::SelectItem](../Topic/CMFCRibbonComboBox::SelectItem.md)|selecciona un elemento en el cuadro de lista.|  
|[CMFCRibbonComboBox::SetDropDownHeight](../Topic/CMFCRibbonComboBox::SetDropDownHeight.md)|Establece el alto del cuadro de lista cuando se quita a continuación.|  
  
## Comentarios  
 El cuadro combinado de la cinta de opciones se compone de un cuadro de lista combinado con una etiqueta estática o la etiqueta que se puedan modificar por el usuario.  Debe especificar que deseado cuando se crea el cuadro combinado de la cinta de opciones.  
  
## Ejemplo  
 El ejemplo siguiente muestra cómo construir un objeto de clase de `CMFCRibbonComboBox` , agregar un elemento al cuadro combinado, seleccione un elemento en el cuadro combinado, y agrega un cuadro combinado a un panel.  
  
 [!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/CPP/cmfcribboncombobox-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)  
  
 [CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)  
  
## Requisitos  
 **encabezado:** afxribboncombobox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonEdit Class](../../mfc/reference/cmfcribbonedit-class.md)