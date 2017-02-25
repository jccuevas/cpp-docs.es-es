---
title: "CMFCToolBarComboBoxButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCToolBarComboBoxButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCToolBarComboBoxButton class"
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CMFCToolBarComboBoxButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un botón de la barra de herramientas que contiene un control de cuadro combinado \([CComboBox Class](../../mfc/reference/ccombobox-class.md)\).  
  
## Sintaxis  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](../Topic/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton.md)|Construye un `CMFCToolBarComboBoxButton`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](../Topic/CMFCToolBarComboBoxButton::AddItem.md)|Agrega un elemento al final de la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](../Topic/CMFCToolBarComboBoxButton::AddSortedItem.md)|Agrega un elemento a la lista del cuadro combinado.  El orden de elementos de la lista es especificado por `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](../Topic/CMFCToolBarComboBoxButton::Compare.md)|Compara dos elementos.  Denominado para ordenar los elementos que `AddSortedItems` agrega a la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::CreateEdit](../Topic/CMFCToolBarComboBoxButton::CreateEdit.md)|Crea un nuevo control de edición para el botón del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::DeleteItem](../Topic/CMFCToolBarComboBoxButton::DeleteItem.md)|Elimina un elemento de la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::FindItem](../Topic/CMFCToolBarComboBoxButton::FindItem.md)|Devuelve el índice del elemento que contiene una cadena especificada.|  
|[CMFCToolBarComboBoxButton::GetByCmd](../Topic/CMFCToolBarComboBoxButton::GetByCmd.md)|Devuelve un puntero al botón del cuadro combinado con un identificador especificada de comando|  
|[CMFCToolBarComboBoxButton::GetComboBox](../Topic/CMFCToolBarComboBoxButton::GetComboBox.md)|Devuelve un puntero al control de cuadro combinado que se inserta en el botón del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetCount](../Topic/CMFCToolBarComboBoxButton::GetCount.md)|Devuelve el número de elementos en la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetCountAll](../Topic/CMFCToolBarComboBoxButton::GetCountAll.md)|Encuentra el botón del cuadro combinado que tiene un identificador especificada de comando  Devuelve el número de elementos en la lista del cuadro combinado del botón.|  
|[CMFCToolBarComboBoxButton::GetCurSel](../Topic/CMFCToolBarComboBoxButton::GetCurSel.md)|Devuelve el índice del elemento seleccionado en la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](../Topic/CMFCToolBarComboBoxButton::GetCurSelAll.md)|Encuentra el botón del cuadro combinado que tiene un id. especificado de comando, y devuelve el índice del elemento seleccionado en la lista del cuadro combinado del botón.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](../Topic/CMFCToolBarComboBoxButton::GetEditCtrl.md)|Devuelve un puntero al control de edición que se inserta en el botón del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetItem](../Topic/CMFCToolBarComboBoxButton::GetItem.md)|Devuelve la cadena asociada al índice especificado en la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetItemAll](../Topic/CMFCToolBarComboBoxButton::GetItemAll.md)|Encuentra el botón del cuadro combinado que tiene un id. especificado de comando, y devuelve la cadena que se asocia a un índice en la lista del cuadro combinado del botón.|  
|[CMFCToolBarComboBoxButton::GetItemData](../Topic/CMFCToolBarComboBoxButton::GetItemData.md)|Devuelve el valor de 32 bits que se asocia a un índice especificado en la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataAll.md)|Encuentra el botón del cuadro combinado que tiene un id. especificado de comando, y devuelve el valor de 32 bits que se asocia a un índice en la lista del cuadro combinado del botón.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](../Topic/CMFCToolBarComboBoxButton::GetItemDataPtrAll.md)|Encuentra el botón del cuadro combinado que tiene un identificador especificada de comando  Recupera el valor de 32 bits que se asocia un índice en la lista del cuadro combinado de ese botón, y devuelve el valor de 32 bits como puntero.|  
|[CMFCToolBarComboBoxButton::GetText](../Topic/CMFCToolBarComboBoxButton::GetText.md)|Devuelve el texto del control de edición del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetTextAll](../Topic/CMFCToolBarComboBoxButton::GetTextAll.md)|Encuentra el botón del cuadro combinado que tiene un id. especificado de comando, y devuelve el texto del control de edición de ese botón.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](../Topic/CMFCToolBarComboBoxButton::IsCenterVert.md)|Determina si los botones del cuadro combinado de la aplicación están centrados o alineados con la parte superior de la barra de herramientas.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](../Topic/CMFCToolBarComboBoxButton::IsFlatMode.md)|Determina si los botones del cuadro combinado en la aplicación tienen una apariencia plana.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](../Topic/CMFCToolBarComboBoxButton::RemoveAllItems.md)|Quita todos los elementos de cuadro de lista y control de edición del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::SelectItem](../Topic/CMFCToolBarComboBoxButton::SelectItem.md)|Selecciona un elemento en el cuadro combinado según su índice, valor de 32 bits, o cadena, y notifica al control de cuadro combinado sobre la selección.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](../Topic/CMFCToolBarComboBoxButton::SelectItemAll.md)|Encuentra el botón del cuadro combinado que tiene un identificador especificada de comando  Llama a `SelectItem` para seleccionar un elemento en el cuadro combinado de ese botón según la cadena, se indiza, o un valor de 32 bits.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](../Topic/CMFCToolBarComboBoxButton::SetCenterVert.md)|Especifica si los botones del cuadro combinado de la aplicación se centrarán verticalmente o alineados con la parte superior de la barra de herramientas.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](../Topic/CMFCToolBarComboBoxButton::SetDropDownHeight.md)|Establece el alto del cuadro de lista desplegable.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](../Topic/CMFCToolBarComboBoxButton::SetFlatMode.md)|Especifica si los botones del cuadro combinado en la aplicación tienen una apariencia plana.|  
  
## Comentarios  
 Para agregar un botón del cuadro combinado en una barra de herramientas, siga estos pasos:  
  
 1.  Reserva un Id. de recurso ficticio para el botón del recurso primario de la barra de herramientas.  
  
 2.  Construya un objeto `CMFCToolBarComboBoxButton`.  
  
 3.  En el controlador de mensajes que procesa el mensaje de `AFX_WM_RESETTOOLBAR` , reemplace el botón ficticio con el nuevo botón de cuadro combinado con [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md).  
  
 Para obtener más información, vea [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md).  Para obtener un ejemplo de un botón de la barra de herramientas del cuadro combinado, vea proyecto VisualStudioDemo de ejemplo.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCToolBarComboBoxButton` .  El ejemplo muestra cómo habilitar la edición y cuadros combinados, establece la posición vertical de los botones del cuadro combinado de la aplicación, establezca el alto del cuadro de lista cuando se quita siguiente, establece la apariencia plano de estilo de los botones del cuadro combinado de la aplicación, y establece el texto del cuadro de edición del botón del cuadro combinado.  Este fragmento de código es parte de [Ejemplo de demostración de Visual Studio](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/CPP/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## Requisitos  
 **encabezado:** afxtoolbarcomboboxbutton.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarButton Class](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox Class](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../Topic/CMFCToolBar::ReplaceButton.md)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)