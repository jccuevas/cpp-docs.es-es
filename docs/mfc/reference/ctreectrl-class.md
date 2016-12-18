---
title: "CTreeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl class"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad del control de vista de árbol común de Windows.  
  
## Sintaxis  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeCtrl::CTreeCtrl](../Topic/CTreeCtrl::CTreeCtrl.md)|Crea un objeto `CTreeCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CTreeCtrl::Create](../Topic/CTreeCtrl::Create.md)|Crea un control de vista de árbol y lo asocia a un objeto de `CTreeCtrl` .|  
|[CTreeCtrl::CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md)|crea un mapa de bits que arrastra para el elemento especificado de la vista de árbol.|  
|[CTreeCtrl::CreateEx](../Topic/CTreeCtrl::CreateEx.md)|Cree un control de árbol con Windows especificado extendidas estilos y lo asocia a un objeto de `CTreeCtrl` .|  
|[CTreeCtrl::DeleteAllItems](../Topic/CTreeCtrl::DeleteAllItems.md)|elimina todos los elementos en un control de vista de árbol.|  
|[CTreeCtrl::DeleteItem](../Topic/CTreeCtrl::DeleteItem.md)|elimina un nuevo elemento en un control de vista de árbol.|  
|[CTreeCtrl::EditLabel](../Topic/CTreeCtrl::EditLabel.md)|Modifica un elemento especificado de la vista de árbol en contexto.|  
|[CTreeCtrl::EndEditLabelNow](../Topic/CTreeCtrl::EndEditLabelNow.md)|Cancela la operación de edición en la etiqueta de un elemento de vista de árbol del control de vista de árbol actual.|  
|[CTreeCtrl::EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md)|Garantiza que un elemento de vista de árbol está visible en el control de vista de árbol.|  
|[CTreeCtrl::Expand](../Topic/CTreeCtrl::Expand.md)|Expanda, o contrae, los elementos secundarios del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetBkColor](../Topic/CTreeCtrl::GetBkColor.md)|Recupera el color de fondo actual del control.|  
|[CTreeCtrl::GetCheck](../Topic/CTreeCtrl::GetCheck.md)|Recupera el estado de la comprobación de un elemento del control de árbol.|  
|[CTreeCtrl::GetChildItem](../Topic/CTreeCtrl::GetChildItem.md)|Recupera el elemento secundario de un elemento específico de la vista de árbol.|  
|[CTreeCtrl::GetCount](../Topic/CTreeCtrl::GetCount.md)|Recupera el número de elementos de árbol asociado a un control de vista de árbol.|  
|[CTreeCtrl::GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md)|Recupera el destino de una operación de arrastrar y colocar.|  
|[CTreeCtrl::GetEditControl](../Topic/CTreeCtrl::GetEditControl.md)|Recupera el identificador del control de edición se usa para editar el elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetExtendedStyle](../Topic/CTreeCtrl::GetExtendedStyle.md)|recupera los estilos extendidos que el control de vista de árbol actual está utilizando.|  
|[CTreeCtrl::GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md)|Recupera el primer elemento visible del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetImageList](../Topic/CTreeCtrl::GetImageList.md)|Recupera el identificador de asociado enumerado imagen con un control de vista de árbol.|  
|[CTreeCtrl::GetIndent](../Topic/CTreeCtrl::GetIndent.md)|Recupera el desplazamiento \(en píxeles\) de un elemento de vista de árbol de su elemento primario.|  
|[CTreeCtrl::GetInsertMarkColor](../Topic/CTreeCtrl::GetInsertMarkColor.md)|Recupera el color utilizado para dibujar la marca de inserción para la vista de árbol.|  
|[CTreeCtrl::GetItem](../Topic/CTreeCtrl::GetItem.md)|Recupera los atributos de un elemento específico de la vista de árbol.|  
|[CTreeCtrl::GetItemData](../Topic/CTreeCtrl::GetItemData.md)|Devuelve el valor específico de la aplicación de 32 bits asociado a un elemento.|  
|[CTreeCtrl::GetItemExpandedImageIndex](../Topic/CTreeCtrl::GetItemExpandedImageIndex.md)|Recupera el índice de la imagen para mostrar cuando el elemento especificado del control de vista de árbol actual está en estado expandida.|  
|[CTreeCtrl::GetItemHeight](../Topic/CTreeCtrl::GetItemHeight.md)|recupera el alto actual de los elementos de la vista de árbol.|  
|[CTreeCtrl::GetItemImage](../Topic/CTreeCtrl::GetItemImage.md)|Recupera las imágenes asociado a un elemento.|  
|[CTreeCtrl::GetItemPartRect](../Topic/CTreeCtrl::GetItemPartRect.md)|Recupera el rectángulo delimitador de una parte concreta de un elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::GetItemRect](../Topic/CTreeCtrl::GetItemRect.md)|Recupera el rectángulo delimitador de un elemento de vista de árbol.|  
|[CTreeCtrl::GetItemState](../Topic/CTreeCtrl::GetItemState.md)|Devuelve el estado de un elemento.|  
|[CTreeCtrl::GetItemStateEx](../Topic/CTreeCtrl::GetItemStateEx.md)|Recupera el estado extendida del elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::GetItemText](../Topic/CTreeCtrl::GetItemText.md)|devuelve el texto de un elemento.|  
|[CTreeCtrl::GetLastVisibleItem](../Topic/CTreeCtrl::GetLastVisibleItem.md)|recupera el elemento expandido pasado en el control de vista de árbol actual.|  
|[CTreeCtrl::GetLineColor](../Topic/CTreeCtrl::GetLineColor.md)|recupera el color de línea actual para el control de vista de árbol.|  
|[CTreeCtrl::GetNextItem](../Topic/CTreeCtrl::GetNextItem.md)|Recupera el siguiente elemento de la vista de árbol que coincide con una relación especificada.|  
|[CTreeCtrl::GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md)|Recupera el siguiente elemento relacionado del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md)|Recupera el elemento visible siguiente del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetParentItem](../Topic/CTreeCtrl::GetParentItem.md)|Recupera el elemento primario del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md)|Recupera el elemento relacionado anterior del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md)|Recupera el elemento visible anterior del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetRootItem](../Topic/CTreeCtrl::GetRootItem.md)|Recupera la raíz del elemento especificado de la vista de árbol.|  
|[CTreeCtrl::GetScrollTime](../Topic/CTreeCtrl::GetScrollTime.md)|Recupera el tiempo máximo de desplazamiento del control de vista de árbol.|  
|[CTreeCtrl::GetSelectedCount](../Topic/CTreeCtrl::GetSelectedCount.md)|Recupera el número de elementos seleccionados en el control de vista de árbol actual.|  
|[CTreeCtrl::GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md)|Recupera el elemento seleccionado de la vista de árbol.|  
|[CTreeCtrl::GetTextColor](../Topic/CTreeCtrl::GetTextColor.md)|Recupera el color del texto del control actual.|  
|[CTreeCtrl::GetToolTips](../Topic/CTreeCtrl::GetToolTips.md)|Recupera el identificador al control secundario de información sobre herramientas utilizado por un control de vista de árbol.|  
|[CTreeCtrl::GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md)|Recupera el número de elementos visibles de árbol asociado a un control de vista de árbol.|  
|[CTreeCtrl::HitTest](../Topic/CTreeCtrl::HitTest.md)|Devuelve la posición actual del cursor relacionado con el objeto de `CTreeCtrl` .|  
|[CTreeCtrl::InsertItem](../Topic/CTreeCtrl::InsertItem.md)|inserta un nuevo elemento en un control de vista de árbol.|  
|[CTreeCtrl::ItemHasChildren](../Topic/CTreeCtrl::ItemHasChildren.md)|Devuelve cero si el elemento especificado tiene elementos secundarios.|  
|[CTreeCtrl::MapAccIdToItem](../Topic/CTreeCtrl::MapAccIdToItem.md)|Asigna el identificador especificado de accesibilidad al identificador a un elemento de vista de árbol del control de vista de árbol actual.|  
|[CTreeCtrl::MapItemToAccID](../Topic/CTreeCtrl::MapItemToAccID.md)|Asigna el identificador especificado a un elemento de vista de árbol del control de vista de árbol actual en un identificador de accesibilidad.|  
|[CTreeCtrl::Select](../Topic/CTreeCtrl::Select.md)|Selecciona, se desplaza en la vista, o rediseña un elemento específico de la vista de árbol.|  
|[CTreeCtrl::SelectDropTarget](../Topic/CTreeCtrl::SelectDropTarget.md)|Dibuja de nuevo el elemento de árbol como destino de una operación de arrastrar y colocar.|  
|[CTreeCtrl::SelectItem](../Topic/CTreeCtrl::SelectItem.md)|Seleccione un elemento especificado de la vista de árbol.|  
|[CTreeCtrl::SelectSetFirstVisible](../Topic/CTreeCtrl::SelectSetFirstVisible.md)|Seleccione un elemento especificado de la vista de árbol como primer elemento visible.|  
|[CTreeCtrl::SetAutoscrollInfo](../Topic/CTreeCtrl::SetAutoscrollInfo.md)|Establece el índice del desplazamiento automático del control de vista de árbol actual.|  
|[CTreeCtrl::SetBkColor](../Topic/CTreeCtrl::SetBkColor.md)|Establece el color de fondo del control.|  
|[CTreeCtrl::SetCheck](../Topic/CTreeCtrl::SetCheck.md)|Establece el estado de la comprobación de un elemento del control de árbol.|  
|[CTreeCtrl::SetExtendedStyle](../Topic/CTreeCtrl::SetExtendedStyle.md)|establece los estilos extendidos para el control de vista de árbol actual.|  
|[CTreeCtrl::SetImageList](../Topic/CTreeCtrl::SetImageList.md)|Establece el identificador de asociado enumerado imagen con un control de vista de árbol.|  
|[CTreeCtrl::SetIndent](../Topic/CTreeCtrl::SetIndent.md)|Establece el desplazamiento \(en píxeles\) de un elemento de vista de árbol de su elemento primario.|  
|[CTreeCtrl::SetInsertMark](../Topic/CTreeCtrl::SetInsertMark.md)|Establece la marca de inserción de un control de vista de árbol.|  
|[CTreeCtrl::SetInsertMarkColor](../Topic/CTreeCtrl::SetInsertMarkColor.md)|Establece el color utilizado para dibujar la marca de inserción para la vista de árbol.|  
|[CTreeCtrl::SetItem](../Topic/CTreeCtrl::SetItem.md)|Establece los atributos de un elemento específico de la vista de árbol.|  
|[CTreeCtrl::SetItemData](../Topic/CTreeCtrl::SetItemData.md)|Establece el valor específico de la aplicación de 32 bits asociado a un elemento.|  
|[CTreeCtrl::SetItemExpandedImageIndex](../Topic/CTreeCtrl::SetItemExpandedImageIndex.md)|Establece el índice de la imagen para mostrar cuando el elemento especificado del control de vista de árbol actual está en estado expandida.|  
|[CTreeCtrl::SetItemHeight](../Topic/CTreeCtrl::SetItemHeight.md)|establece el alto de los elementos de la vista de árbol.|  
|[CTreeCtrl::SetItemImage](../Topic/CTreeCtrl::SetItemImage.md)|asocia imágenes a un elemento.|  
|[CTreeCtrl::SetItemState](../Topic/CTreeCtrl::SetItemState.md)|Establece el estado de un elemento.|  
|[CTreeCtrl::SetItemStateEx](../Topic/CTreeCtrl::SetItemStateEx.md)|Establece el estado extendida del elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::SetItemText](../Topic/CTreeCtrl::SetItemText.md)|establece el texto de un elemento.|  
|[CTreeCtrl::SetLineColor](../Topic/CTreeCtrl::SetLineColor.md)|establece el color de línea actual para el control de vista de árbol.|  
|[CTreeCtrl::SetScrollTime](../Topic/CTreeCtrl::SetScrollTime.md)|Establece el tiempo máximo de desplazamiento del control de vista de árbol.|  
|[CTreeCtrl::SetTextColor](../Topic/CTreeCtrl::SetTextColor.md)|Establece el color del texto del control.|  
|[CTreeCtrl::SetToolTips](../Topic/CTreeCtrl::SetToolTips.md)|Establece el control secundario de información sobre herramientas de un control de vista de árbol.|  
|[CTreeCtrl::ShowInfoTip](../Topic/CTreeCtrl::ShowInfoTip.md)|Muestra el infotip para el elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::SortChildren](../Topic/CTreeCtrl::SortChildren.md)|Ordena los elementos secundarios de un elemento primario especificado.|  
|[CTreeCtrl::SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md)|Ordena los elementos secundarios de un elemento primario especificado mediante una función definido por la aplicación de ordenación.|  
  
## Comentarios  
 Un “control de vista de árbol” es una ventana que muestra una lista jerárquica de los elementos, como los encabezados en un documento, las entradas en un índice, o archivos y directorios en un disco.  Cada elemento consta de una etiqueta y una imagen de mapa de bits opcional, y cada elemento puede tener una lista de subelementos asociado.  Haciendo clic en un elemento, el usuario puede expandir y contraer la lista asociada de subelementos.  
  
 Este control \(y por consiguiente la clase de `CTreeCtrl` \) sólo está disponible para los programas que se ejecutan en versión 4 de Windows 98 y Windows NT y posterior.  
  
 Para obtener más información sobre cómo utilizar `CTreeCtrl`, vea:  
  
-   [Controles](../../mfc/controls-mfc.md)  
  
-   [Mediante CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
-   [Referencia al control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb759988) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
-   Caso Q222905 de Knowledge Base: HOWTO: Mostrar un menú contextual para CTreeCtrl  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)