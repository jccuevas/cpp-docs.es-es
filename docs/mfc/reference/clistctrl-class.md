---
title: "CListCtrl Class | Microsoft Docs"
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
  - "CListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListCtrl (clase)"
  - "list view controls"
  - "list view controls, CListCtrl (clase)"
  - "LVS_ICON"
  - "LVS_LIST"
  - "LVS_REPORT"
  - "LVS_SMALLICON"
  - "Windows common controls [C++], CListCtrl"
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula la funcionalidad de un “control de la vista de lista,” que muestra una colección de elementos cada uno que consta de un icono \(de una imagen lista\) y una etiqueta.  
  
## Sintaxis  
  
```  
class CListCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListCtrl::CListCtrl](../Topic/CListCtrl::CListCtrl.md)|Crea un objeto `CListCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CListCtrl::ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md)|Determina el ancho y el alto necesarios para mostrar los elementos de un control de vista de lista.|  
|[CListCtrl::Arrange](../Topic/CListCtrl::Arrange.md)|alinea elementos en una cuadrícula.|  
|[CListCtrl::CancelEditLabel](../Topic/CListCtrl::CancelEditLabel.md)|Cancela la operación de edición de texto del elemento.|  
|[CListCtrl::Create](../Topic/CListCtrl::Create.md)|Crea un control de lista y lo asocia a un objeto de `CListCtrl` .|  
|[CListCtrl::CreateDragImage](../Topic/CListCtrl::CreateDragImage.md)|Crea una imagen de arrastre incluida para un elemento especificado.|  
|[CListCtrl::CreateEx](../Topic/CListCtrl::CreateEx.md)|Crea un control de lista con Windows especificado extendidas estilos y lo asocia a un objeto de `CListCtrl` .|  
|[CListCtrl::DeleteAllItems](../Topic/CListCtrl::DeleteAllItems.md)|Elimina todos los elementos del control.|  
|[CListCtrl::DeleteColumn](../Topic/CListCtrl::DeleteColumn.md)|Elimina una columna del control de vista de lista.|  
|[CListCtrl::DeleteItem](../Topic/CListCtrl::DeleteItem.md)|Elimina un elemento del control.|  
|[CListCtrl::DrawItem](../Topic/CListCtrl::DrawItem.md)|Se invoca cuando un aspecto visual de un control de dibujo propietario.|  
|[CListCtrl::EditLabel](../Topic/CListCtrl::EditLabel.md)|Inicia la edición en contexto de texto de un elemento.|  
|[CListCtrl::EnableGroupView](../Topic/CListCtrl::EnableGroupView.md)|Habilita o deshabilita si los elementos en una vista de lista de control muestre como grupo.|  
|[CListCtrl::EnsureVisible](../Topic/CListCtrl::EnsureVisible.md)|Garantiza que un elemento sea visible.|  
|[CListCtrl::FindItem](../Topic/CListCtrl::FindItem.md)|Buscar un elemento listview que especifica características.|  
|[CListCtrl::GetBkColor](../Topic/CListCtrl::GetBkColor.md)|Recupera el color de fondo de un control de vista de lista.|  
|[CListCtrl::GetBkImage](../Topic/CListCtrl::GetBkImage.md)|Recupera la imagen de fondo actual de un control de vista de lista.|  
|[CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md)|Recupera la máscara de devolución de llamada para un control de vista de lista.|  
|[CListCtrl::GetCheck](../Topic/CListCtrl::GetCheck.md)|Recupera el estado actual de la imagen del estado asociado a un elemento.|  
|[CListCtrl::GetColumn](../Topic/CListCtrl::GetColumn.md)|recupera los atributos de una columna de control.|  
|[CListCtrl::GetColumnOrderArray](../Topic/CListCtrl::GetColumnOrderArray.md)|Recupera el orden de la columna \(de izquierda a derecha\) de un control de vista de lista.|  
|[CListCtrl::GetColumnWidth](../Topic/CListCtrl::GetColumnWidth.md)|Recupera el ancho de una columna en la vista de informe o una vista de lista.|  
|[CListCtrl::GetCountPerPage](../Topic/CListCtrl::GetCountPerPage.md)|Calcula el número de elementos que pueden ajustarse verticalmente en un control de vista de lista.|  
|[CListCtrl::GetEditControl](../Topic/CListCtrl::GetEditControl.md)|Recupera el identificador del control de edición se usa para editar el texto de un elemento.|  
|[CListCtrl::GetEmptyText](../Topic/CListCtrl::GetEmptyText.md)|Recupera la cadena para mostrar si el control actual de la vista de lista está vacío.|  
|[CListCtrl::GetExtendedStyle](../Topic/CListCtrl::GetExtendedStyle.md)|Recupera los estilos extendidos actuales de un control de vista de lista.|  
|[CListCtrl::GetFirstSelectedItemPosition](../Topic/CListCtrl::GetFirstSelectedItemPosition.md)|Recupera la posición del primer elemento seleccionado de la vista de lista en un control de vista de lista.|  
|[CListCtrl::GetFocusedGroup](../Topic/CListCtrl::GetFocusedGroup.md)|Recupera el grupo que tiene el foco de teclado en el control actual de la vista de lista.|  
|[CListCtrl::GetGroupCount](../Topic/CListCtrl::GetGroupCount.md)|Recupera el número de grupos en el control actual de la vista de lista.|  
|[CListCtrl::GetGroupInfo](../Topic/CListCtrl::GetGroupInfo.md)|Obtiene la información para un grupo especificado del control de vista de lista.|  
|[CListCtrl::GetGroupInfoByIndex](../Topic/CListCtrl::GetGroupInfoByIndex.md)|Información de recupera sobre un grupo especificado en el control actual de la vista de lista.|  
|[CListCtrl::GetGroupMetrics](../Topic/CListCtrl::GetGroupMetrics.md)|Recupera las medidas de un grupo.|  
|[CListCtrl::GetGroupRect](../Topic/CListCtrl::GetGroupRect.md)|recupera el rectángulo delimitador para un grupo especificado en el control actual de la vista de lista.|  
|[CListCtrl::GetGroupState](../Topic/CListCtrl::GetGroupState.md)|Recupera el estado para un grupo especificado en el control actual de la vista de lista.|  
|[CListCtrl::GetHeaderCtrl](../Topic/CListCtrl::GetHeaderCtrl.md)|Recupera el control de encabezado de un control de vista de lista.|  
|[CListCtrl::GetHotCursor](../Topic/CListCtrl::GetHotCursor.md)|Recupera el cursor utilizado cuando el seguimiento activo se habilita para un control de vista de lista.|  
|[CListCtrl::GetHotItem](../Topic/CListCtrl::GetHotItem.md)|Recupera el elemento de vista de lista actualmente en el cursor.|  
|[CListCtrl::GetHoverTime](../Topic/CListCtrl::GetHoverTime.md)|Recupera la hora actual de suspensión de un control de vista de lista.|  
|[CListCtrl::GetImageList](../Topic/CListCtrl::GetImageList.md)|Recupera el identificador de una imagen que se utiliza para dibujar los elementos de la vista de lista.|  
|[CListCtrl::GetInsertMark](../Topic/CListCtrl::GetInsertMark.md)|Recupera la posición actual de marca de inserción.|  
|[CListCtrl::GetInsertMarkColor](../Topic/CListCtrl::GetInsertMarkColor.md)|Recupera el color actual de marca de inserción.|  
|[CListCtrl::GetInsertMarkRect](../Topic/CListCtrl::GetInsertMarkRect.md)|recupera el rectángulo que limita el punto de inserción.|  
|[CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)|Recupera los atributos de un elemento de vista de lista.|  
|[CListCtrl::GetItemCount](../Topic/CListCtrl::GetItemCount.md)|Recupera el número de elementos en un control de vista de lista.|  
|[CListCtrl::GetItemData](../Topic/CListCtrl::GetItemData.md)|Recupera el valor específico de la aplicación asociada a un elemento.|  
|[CListCtrl::GetItemIndexRect](../Topic/CListCtrl::GetItemIndexRect.md)|Recupera el rectángulo delimitador del todo o parte de un subelemento en el control actual de la vista de lista.|  
|[CListCtrl::GetItemPosition](../Topic/CListCtrl::GetItemPosition.md)|Recupera la posición de un elemento de vista de lista.|  
|[CListCtrl::GetItemRect](../Topic/CListCtrl::GetItemRect.md)|recupera el rectángulo delimitador para un elemento.|  
|[CListCtrl::GetItemSpacing](../Topic/CListCtrl::GetItemSpacing.md)|Calcula el espaciado entre los elementos del control actual de la vista de lista.|  
|[CListCtrl::GetItemState](../Topic/CListCtrl::GetItemState.md)|Recupera el estado de un elemento de vista de lista.|  
|[CListCtrl::GetItemText](../Topic/CListCtrl::GetItemText.md)|Recupera el texto de un elemento o un subelemento de la vista de lista.|  
|[CListCtrl::GetNextItem](../Topic/CListCtrl::GetNextItem.md)|Buscar un elemento listview con las propiedades y con la relación especificada a un elemento determinado.|  
|[CListCtrl::GetNextItemIndex](../Topic/CListCtrl::GetNextItemIndex.md)|Recupera el índice del elemento en el control actual de la vista de lista que tiene un conjunto especificado de propiedades.|  
|[CListCtrl::GetNextSelectedItem](../Topic/CListCtrl::GetNextSelectedItem.md)|Recupera el índice de una posición del elemento de vista de lista, y la posición del elemento seleccionado siguiente de la vista de lista para recorrer.|  
|[CListCtrl::GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md)|Recupera el número actual de zonas de trabajo para un control de vista de lista.|  
|[CListCtrl::GetOrigin](../Topic/CListCtrl::GetOrigin.md)|Recupera el origen de la vista actual para un control de vista de lista.|  
|[CListCtrl::GetOutlineColor](../Topic/CListCtrl::GetOutlineColor.md)|Recupera el color del borde de un control de vista de lista.|  
|[CListCtrl::GetSelectedColumn](../Topic/CListCtrl::GetSelectedColumn.md)|Recupera el índice de la columna actualmente seleccionada en el control de lista.|  
|[CListCtrl::GetSelectedCount](../Topic/CListCtrl::GetSelectedCount.md)|Recupera el número de elementos seleccionados en el control de vista de lista.|  
|[CListCtrl::GetSelectionMark](../Topic/CListCtrl::GetSelectionMark.md)|Recupera la marca de la selección de un control de vista de lista.|  
|[CListCtrl::GetStringWidth](../Topic/CListCtrl::GetStringWidth.md)|Determina el ancho de columna mínimo necesario mostrar toda la cadena especificada.|  
|[CListCtrl::GetSubItemRect](../Topic/CListCtrl::GetSubItemRect.md)|Recupera el rectángulo delimitador de un elemento en un control de vista de lista.|  
|[CListCtrl::GetTextBkColor](../Topic/CListCtrl::GetTextBkColor.md)|Recupera el color de fondo del texto de un control de vista de lista.|  
|[CListCtrl::GetTextColor](../Topic/CListCtrl::GetTextColor.md)|Recupera el color del texto de un control de vista de lista.|  
|[CListCtrl::GetTileInfo](../Topic/CListCtrl::GetTileInfo.md)|Información de recupera sobre un mosaico en un control de vista de lista.|  
|[CListCtrl::GetTileViewInfo](../Topic/CListCtrl::GetTileViewInfo.md)|Información de recupera sobre un control de vista de lista en la vista en mosaico.|  
|[CListCtrl::GetToolTips](../Topic/CListCtrl::GetToolTips.md)|Recupera el control de información sobre herramientas del control de vista de lista utiliza para mostrar información sobre herramientas.|  
|[CListCtrl::GetTopIndex](../Topic/CListCtrl::GetTopIndex.md)|Recupera el índice del elemento visible superior.|  
|[CListCtrl::GetView](../Topic/CListCtrl::GetView.md)|Obtiene la vista de control de la vista de lista.|  
|[CListCtrl::GetViewRect](../Topic/CListCtrl::GetViewRect.md)|Recupera el rectángulo delimitador de todos los elementos del control de vista de lista.|  
|[CListCtrl::GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md)|Recupera las zonas de trabajo actuales de un control de vista de lista.|  
|[CListCtrl::HasGroup](../Topic/CListCtrl::HasGroup.md)|Determina si el control de vista de lista tiene el grupo especificado.|  
|[CListCtrl::HitTest](../Topic/CListCtrl::HitTest.md)|Determina que el elemento de vista de lista aparece en una posición especificada.|  
|[CListCtrl::InsertColumn](../Topic/CListCtrl::InsertColumn.md)|Inserta una nueva columna en un control de vista de lista.|  
|[CListCtrl::InsertGroup](../Topic/CListCtrl::InsertGroup.md)|Inserta un grupo en el control de vista de lista.|  
|[CListCtrl::InsertGroupSorted](../Topic/CListCtrl::InsertGroupSorted.md)|Inserta el grupo especificado en una lista ordenada de grupos.|  
|[CListCtrl::InsertItem](../Topic/CListCtrl::InsertItem.md)|Inserta un nuevo elemento en un control de vista de lista.|  
|[CListCtrl::InsertMarkHitTest](../Topic/CListCtrl::InsertMarkHitTest.md)|Recupera el punto de inserción más próximo a un punto especificado.|  
|[CListCtrl::IsGroupViewEnabled](../Topic/CListCtrl::IsGroupViewEnabled.md)|Determina si la vista del grupo está habilitada para un control de vista de lista.|  
|[CListCtrl::IsItemVisible](../Topic/CListCtrl::IsItemVisible.md)|Indica si un elemento especificado en el control actual de la vista de lista está visible.|  
|[CListCtrl::MapIDToIndex](../Topic/CListCtrl::MapIDToIndex.md)|Asigna el identificador único de un elemento en el control actual de la lista\-vista para un índice.|  
|[CListCtrl::MapIndexToID](../Topic/CListCtrl::MapIndexToID.md)|asigna el índice de un elemento en el control actual de la vista de lista a una identificación única|  
|[CListCtrl::MoveGroup](../Topic/CListCtrl::MoveGroup.md)|Mueve el grupo especificado.|  
|[CListCtrl::MoveItemToGroup](../Topic/CListCtrl::MoveItemToGroup.md)|Mueve el grupo especificado al cero índice basado especificado del control de vista de lista.|  
|[CListCtrl::RedrawItems](../Topic/CListCtrl::RedrawItems.md)|Fuerza un control de vista de lista para que vuelva a un intervalo de elementos.|  
|[CListCtrl::RemoveAllGroups](../Topic/CListCtrl::RemoveAllGroups.md)|Quita todos los grupos de un control de vista de lista.|  
|[CListCtrl::RemoveGroup](../Topic/CListCtrl::RemoveGroup.md)|Quita el grupo especificado del control de vista de lista.|  
|[CListCtrl::Scroll](../Topic/CListCtrl::Scroll.md)|Desplaza el contenido de un control de vista de lista.|  
|[CListCtrl::SetBkColor](../Topic/CListCtrl::SetBkColor.md)|Establece el color de fondo del control de vista de lista.|  
|[CListCtrl::SetBkImage](../Topic/CListCtrl::SetBkImage.md)|Establece la imagen de fondo actual de un control de vista de lista.|  
|[CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md)|Establece la máscara de devolución de llamada para un control de vista de lista.|  
|[CListCtrl::SetCheck](../Topic/CListCtrl::SetCheck.md)|Establece el estado actual de la imagen del estado asociado a un elemento.|  
|[CListCtrl::SetColumn](../Topic/CListCtrl::SetColumn.md)|establece los atributos de una columna de la vista de lista.|  
|[CListCtrl::SetColumnOrderArray](../Topic/CListCtrl::SetColumnOrderArray.md)|Establece el orden de la columna \(de izquierda a derecha\) de un control de vista de lista.|  
|[CListCtrl::SetColumnWidth](../Topic/CListCtrl::SetColumnWidth.md)|Cambia el ancho de una columna en la vista de informe o una vista de lista.|  
|[CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md)|Establece los estilos extendidos actuales de un control de vista de lista.|  
|[CListCtrl::SetGroupInfo](../Topic/CListCtrl::SetGroupInfo.md)|Establece la información del grupo especificado de un control de vista de lista.|  
|[CListCtrl::SetGroupMetrics](../Topic/CListCtrl::SetGroupMetrics.md)|Establece las métricas de grupo de un control de vista de lista.|  
|[CListCtrl::SetHotCursor](../Topic/CListCtrl::SetHotCursor.md)|Establece el cursor utilizado cuando el seguimiento activo se habilita para un control de vista de lista.|  
|[CListCtrl::SetHotItem](../Topic/CListCtrl::SetHotItem.md)|Establece el caso muy actual actual de un control de vista de lista.|  
|[CListCtrl::SetHoverTime](../Topic/CListCtrl::SetHoverTime.md)|Establece la hora actual de suspensión de un control de vista de lista.|  
|[CListCtrl::SetIconSpacing](../Topic/CListCtrl::SetIconSpacing.md)|Establece el espaciado entre los iconos en un control de vista de lista.|  
|[CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md)|Asigna una lista de imágenes a un control de vista de lista.|  
|[CListCtrl::SetInfoTip](../Topic/CListCtrl::SetInfoTip.md)|establece el texto de información sobre herramientas.|  
|[CListCtrl::SetInsertMark](../Topic/CListCtrl::SetInsertMark.md)|Establece el punto de inserción en la posición definido.|  
|[CListCtrl::SetInsertMarkColor](../Topic/CListCtrl::SetInsertMarkColor.md)|Establece el color del punto de inserción.|  
|[CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md)|Establece algunos o todos los atributos de un elemento de vista de lista.|  
|[CListCtrl::SetItemCount](../Topic/CListCtrl::SetItemCount.md)|Prepara un control de vista de lista para agregar un gran número de elementos.|  
|[CListCtrl::SetItemCountEx](../Topic/CListCtrl::SetItemCountEx.md)|Establece el número de elementos de un control de la vista de lista virtual.|  
|[CListCtrl::SetItemData](../Topic/CListCtrl::SetItemData.md)|Establece el valor específico de la aplicación del elemento.|  
|[CListCtrl::SetItemIndexState](../Topic/CListCtrl::SetItemIndexState.md)|Establece el estado de un elemento en el control actual de la vista de lista.|  
|[CListCtrl::SetItemPosition](../Topic/CListCtrl::SetItemPosition.md)|Mueve un elemento en una posición especificada de un control de vista de lista.|  
|[CListCtrl::SetItemState](../Topic/CListCtrl::SetItemState.md)|Cambia el estado de un elemento en un control de vista de lista.|  
|[CListCtrl::SetItemText](../Topic/CListCtrl::SetItemText.md)|Cambia el texto de un elemento o un subelemento de la vista de lista.|  
|[CListCtrl::SetOutlineColor](../Topic/CListCtrl::SetOutlineColor.md)|Establece el color del borde de un control de vista de lista.|  
|[CListCtrl::SetSelectedColumn](../Topic/CListCtrl::SetSelectedColumn.md)|Establece la columna seleccionada del control de vista de lista.|  
|[CListCtrl::SetSelectionMark](../Topic/CListCtrl::SetSelectionMark.md)|Establece la marca de la selección de un control de vista de lista.|  
|[CListCtrl::SetTextBkColor](../Topic/CListCtrl::SetTextBkColor.md)|Establece el color de fondo del texto en un control de vista de lista.|  
|[CListCtrl::SetTextColor](../Topic/CListCtrl::SetTextColor.md)|Establece el color del texto de un control de vista de lista.|  
|[CListCtrl::SetTileInfo](../Topic/CListCtrl::SetTileInfo.md)|Establece la información de un mosaico del control de vista de lista.|  
|[CListCtrl::SetTileViewInfo](../Topic/CListCtrl::SetTileViewInfo.md)|Establece la información que un control de vista de lista utiliza en la vista en mosaico.|  
|[CListCtrl::SetToolTips](../Topic/CListCtrl::SetToolTips.md)|Establece el control de información sobre herramientas del control de vista de lista utilizará para mostrar información sobre herramientas.|  
|[CListCtrl::SetView](../Topic/CListCtrl::SetView.md)|Establece la vista del control de vista de lista.|  
|[CListCtrl::SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md)|Establece el área donde los iconos se pueden mostrar en un control de vista de lista.|  
|[CListCtrl::SortGroups](../Topic/CListCtrl::SortGroups.md)|Ordena los grupos de un control listview con una función definida por el usuario.|  
|[CListCtrl::SortItems](../Topic/CListCtrl::SortItems.md)|Los elementos de la vista de lista de las ordenaciones utilizando una comparación definido por la aplicación funciona.|  
|[CListCtrl::SortItemsEx](../Topic/CListCtrl::SortItemsEx.md)|Los elementos de la vista de lista de las ordenaciones utilizando una comparación definido por la aplicación funciona.|  
|[CListCtrl::SubItemHitTest](../Topic/CListCtrl::SubItemHitTest.md)|Determina que el elemento de vista de lista, si existe, en una posición determinada.|  
|[CListCtrl::Update](../Topic/CListCtrl::Update.md)|Fuerza el control para que vuelva a un elemento especificado.|  
  
## Comentarios  
 Además de un icono y una etiqueta, cada elemento puede tener información mostrada en columnas a la derecha del icono y label.  Este control \(y por consiguiente la clase de `CListCtrl` \) sólo está disponible para los programas que se ejecutan en versión 3,51 de Windows 95 \/98 y Windows NT y posterior.  
  
 A continuación se muestra una información general de la clase de `CListCtrl` .  Para obtener una explicación detallada, conceptual, vea [Mediante CListCtrl](../../mfc/using-clistctrl.md) y [Controles](../../mfc/controls-mfc.md).  
  
## Vistas  
 Los controles de la vista de lista pueden mostrar su contenido en cuatro maneras diferentes, denominadas “vistas.”  
  
-   vista de iconos  
  
     Cada elemento aparece como píxeles del mismo tamaño de icono \(32 x 32\) con una etiqueta debajo de.  el usuario puede arrastrar los elementos a cualquier ubicación en la ventana de la vista de lista.  
  
-   pequeña vista de iconos  
  
     Cada elemento aparece como pequeños píxeles de icono \(16 x 16\) con la etiqueta a la derecha de.  el usuario puede arrastrar los elementos a cualquier ubicación en la ventana de la vista de lista.  
  
-   vista de lista  
  
     Cada elemento aparece como un pequeño icono con una etiqueta a la derecha de.  Los elementos se organizan en columnas y no se pueden arrastrar a cualquier ubicación en la ventana de la vista de lista.  
  
-   Vista de informe  
  
     Cada elemento aparece en su propia línea, con información adicional organizada en columnas a la derecha.  la columna situada más a la izquierda contiene el pequeños icono y etiqueta, y las columnas subsiguientes contienen subelementos según lo especificado por la aplicación.  un control de encabezado incrustado \(clase [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)\) implementa estas columnas.  Para obtener más información sobre el control y las columnas del encabezado en una vista de informe, vea [Mediante CListCtrl: Agregar columnas al Control \(vista de informe\)](../../mfc/adding-columns-to-the-control-report-view.md).  
  
 Vea también:  
  
-   Caso Q250614 de Knowledge Base: HOWTO: Ordenación de elementos en un CListCtrl en la vista de informe  
  
-   Caso Q200054 de Knowledge Base: PRB: OnTimer\(\) es Repeatedly denominado No para un control de lista  
  
 El estilo de la vista de lista actual del control determina la vista actual.  Para obtener más información sobre estos estilos y su uso, vea [Mediante CListCtrl: Cambiar los estilos del control de lista](../../mfc/changing-list-control-styles.md).  
  
## Estilos extendidos  
 Además de los estilos de lista estándar, la clase `CListCtrl` admite un conjunto grande de estilos extendidos, proporcionando funcionalidad enriquecida.  Algunos ejemplos de esta funcionalidad son:  
  
-   Selección de suspensión  
  
     Cuando está habilitada, permite la selección automática de un elemento cuando el cursor se mantiene sobre el elemento por un período de tiempo.  
  
-   vistas de lista virtuales  
  
     Cuando está habilitada, permite que el control admita hasta `DWORD` elementos.  Esto es posible colocar la sobrecarga de administración de datos de la aplicación.  Salvo la selección de elementos y la información de foco, toda la información sobre el elemento se debe controlar por la aplicación.  Para obtener más información, vea [Mediante CListCtrl: controles de lista virtuales](../../mfc/virtual-list-controls.md).  
  
-   activación de uno y dos clic  
  
     Cuando está habilitada, permite el seguimiento activo \(el resaltado automático del texto del elemento\) y la activación de uno o dos en el elemento resaltado.  
  
-   El orden de arrastrar y colocar de columna  
  
     Cuando está habilitada, permite reordenar arrastrar y colocar de columnas en un control de vista de lista.  Sólo disponible en la vista de informe.  
  
 Para obtener información sobre cómo utilizar estos nuevos estilos extendidos, vea [Mediante CListCtrl: Cambiar los estilos del control de lista](../../mfc/changing-list-control-styles.md).  
  
## elementos y subelementos  
 Cada elemento en un control de vista de lista está formada por un icono \(de una imagen lista\), una etiqueta, un estado actual, y un valor definido por la aplicación \(denominado “datos de elemento”\).  Uno o más subelementos también pueden estar asociado a cada elemento.  Un “subelemento” es una cadena que, en la vista de informe, se puede mostrar en una columna a la derecha del icono y la etiqueta de un elemento.  Todos los elementos en un control de vista de lista deben tener el mismo número de subelementos.  
  
 La clase **CListCtrl** proporciona varias funciones para insertar, eliminar, buscar, y modificar estos elementos.  Para obtener más información, vea [CListCtrl:: GetItem](../Topic/CListCtrl::GetItem.md), [CListCtrl:: InsertItem](../Topic/CListCtrl::InsertItem.md), y [CListCtrl:: FindItem](../Topic/CListCtrl::FindItem.md), [Mediante CListCtrl: Agregar elementos al Control](../../mfc/adding-items-to-the-control.md), y [Mediante CListCtrl: El desplazamiento, la disposición, el cambio y, al encontrar en controles de lista](../../mfc/scrolling-arranging-sorting-and-finding-in-list-controls.md).  
  
 De forma predeterminada, el control de vista de lista es responsable de almacenar el icono y los atributos de texto de un elemento.  Sin embargo, además de estos tipos de elemento, la clase `CListCtrl` admite “elementos de devolución de llamada”. Un “elemento de devolución de llamada” es un elemento de la vista de lista para el que la aplicación — en lugar del control \)almacena el texto, el icono, o ambos.  Una máscara de devolución de llamada se utiliza para especificar que los atributos del elemento \(texto o icono\) son proporcionados por la aplicación.  Si una aplicación usa elementos de devolución de llamada, debe poder proporcionar los atributos de texto ni del icono a petición.  Los elementos de devolución de llamada son útiles cuando la aplicación mantiene ya parte de esta información.  Para obtener más información, vea [Mediante CListCtrl: Elementos y el De Callback de devolución de llamada](../../mfc/callback-items-and-the-callback-mask.md).  
  
## Listas de imágenes  
 Contienen los iconos, imágenes de elemento de encabezado, y estados definidos por la aplicación para los elementos de la vista de lista en varias listas de imágenes \(implementados por la clase [CImageList](../../mfc/reference/cimagelist-class.md)\), que crea y asignar el control de vista de lista.  Cada control de la vista de lista puede tener hasta cuatro tipos diferentes de listas de imágenes:  
  
-   icono grande  
  
     Utilizado en la vista de iconos para los iconos del mismo tamaño.  
  
-   Icono pequeño  
  
     Utilizado en el pequeños icono, lista, y vistas de informe para versiones más pequeñas de los iconos utilizados en la vista de iconos.  
  
-   estado definido por la aplicación  
  
     Contiene imágenes de estado, que se muestran junto al icono de un elemento para indicar un estado definido por la aplicación.  
  
-   Header Item  
  
     Utilizado en la vista de informe para las pequeñas imágenes que aparecen en cada elemento del control de encabezado.  
  
 De forma predeterminada, un control de vista de lista destruye listas de la imagen asignada al cuando se destruye; sin embargo, el programador puede personalizar este comportamiento destruyendo cada imagen que aparece cuando ya no se usa, determinado por la aplicación.  Para obtener más información, vea [Mediante CListCtrl: Elementos de lista y listas de Imágenes](../../mfc/list-items-and-image-lists.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo ROWLIST de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)