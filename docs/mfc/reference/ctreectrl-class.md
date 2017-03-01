---
title: CTreeCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- directory lists
- tree view controls
- file lists [C++]
- CTreeCtrl class
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5341367b44540e2d0991fd61e52611826bbdcda1
ms.lasthandoff: 02/24/2017

---
# <a name="ctreectrl-class"></a>CTreeCtrl Class
Proporciona la funcionalidad del control de vista de árbol común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTreeCtrl::CTreeCtrl](#ctreectrl)|Construye un objeto `CTreeCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CTreeCtrl::Create](#create)|Crea un control de vista de árbol y se adjunta a un `CTreeCtrl` objeto.|  
|[CTreeCtrl::CreateDragImage](#createdragimage)|Crea un mapa de bits de arrastre para el elemento de vista de árbol especificado.|  
|[CTreeCtrl::CreateEx](#createex)|Crea un control de árbol con los estilos extendidos de Windows especificados y lo adjunta a un `CTreeCtrl` objeto.|  
|[CTreeCtrl::DeleteAllItems](#deleteallitems)|Elimina todos los elementos en un control de vista de árbol.|  
|[CTreeCtrl::DeleteItem](#deleteitem)|Elimina un elemento nuevo en un control de vista de árbol.|  
|[CTreeCtrl::EditLabel](#editlabel)|Modifica un árbol especificado vista elemento local.|  
|[CTreeCtrl::EndEditLabelNow](#endeditlabelnow)|Cancela la operación de edición en la etiqueta de un elemento de vista de árbol en el control de vista de árbol actual.|  
|[CTreeCtrl::EnsureVisible](#ensurevisible)|Garantiza que un elemento de vista de árbol está visible en el control de vista de árbol.|  
|[CTreeCtrl::Expand](#expand)|Expande o contrae los elementos secundarios del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetBkColor](#getbkcolor)|Recupera el color de fondo actual del control.|  
|[CTreeCtrl::GetCheck](#getcheck)|Recupera el estado de activación de un elemento de control de árbol.|  
|[CTreeCtrl::GetChildItem](#getchilditem)|Recupera al elemento secundario de un elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetCount](#getcount)|Recupera el número de elementos del árbol asociada a un control de vista de árbol.|  
|[CTreeCtrl::GetDropHilightItem](#getdrophilightitem)|Recupera el destino de una operación de arrastrar y colocar.|  
|[CTreeCtrl::GetEditControl](#geteditcontrol)|Recupera el identificador del control de edición utilizado para editar el elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que está utilizando el control de vista de árbol actual.|  
|[CTreeCtrl::GetFirstVisibleItem](#getfirstvisibleitem)|Recupera el primer elemento visible del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetImageList](#getimagelist)|Recupera el identificador de la lista de imágenes asociada a un control de vista de árbol.|  
|[CTreeCtrl::GetIndent](#getindent)|Recupera el desplazamiento (en píxeles) de un elemento de vista de árbol de su elemento primario.|  
|[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)|Recupera el color utilizado para dibujar la marca de inserción de la vista de árbol.|  
|[CTreeCtrl::GetItem](#getitem)|Recupera los atributos de un elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetItemData](#getitemdata)|Devuelve el valor específico de la aplicación de 32 bits asociado al elemento.|  
|[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)|Recupera el índice de la imagen que se muestra cuando el elemento especificado del control de vista de árbol actual está expandido.|  
|[CTreeCtrl::GetItemHeight](#getitemheight)|Recupera el alto actual de los elementos de la vista de árbol.|  
|[CTreeCtrl::GetItemImage](#getitemimage)|Recupera las imágenes asociadas a un elemento.|  
|[CTreeCtrl::GetItemPartRect](#getitempartrect)|Recupera el rectángulo delimitador de un elemento especificado de un elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de un elemento de vista de árbol.|  
|[CTreeCtrl::GetItemState](#getitemstate)|Devuelve el estado de un elemento.|  
|[CTreeCtrl::GetItemStateEx](#getitemstateex)|Recupera el estado extendido del elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::GetItemText](#getitemtext)|Devuelve el texto de un elemento.|  
|[CTreeCtrl::GetLastVisibleItem](#getlastvisibleitem)|Recupera el último elemento expandido en el control de vista de árbol actual.|  
|[CTreeCtrl::GetLineColor](#getlinecolor)|Recupera el color de línea actual para el control de vista de árbol.|  
|[CTreeCtrl::GetNextItem](#getnextitem)|Recupera el siguiente elemento de vista de árbol que coincida con una relación especificada.|  
|[CTreeCtrl::GetNextSiblingItem](#getnextsiblingitem)|Recupera al siguiente elemento relacionado del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetNextVisibleItem](#getnextvisibleitem)|Recupera el siguiente elemento visible del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetParentItem](#getparentitem)|Recupera al elemento primario del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetPrevSiblingItem](#getprevsiblingitem)|Recupera al elemento relacionado anterior del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetPrevVisibleItem](#getprevvisibleitem)|Recupera el elemento visible anterior del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetRootItem](#getrootitem)|Recupera la raíz del elemento de vista de árbol especificado.|  
|[CTreeCtrl::GetScrollTime](#getscrolltime)|Recupera el tiempo máximo de desplazamiento para el control de vista de árbol.|  
|[CTreeCtrl::GetSelectedCount](#getselectedcount)|Recupera el número de elementos seleccionados en el control de vista de árbol actual.|  
|[CTreeCtrl::GetSelectedItem](#getselecteditem)|Recupera el elemento de vista de árbol seleccionado actualmente.|  
|[CTreeCtrl::GetTextColor](#gettextcolor)|Recupera el color de texto actual del control.|  
|[CTreeCtrl::GetToolTips](#gettooltips)|Recupera el identificador para el control de información sobre herramientas usado un control de vista de árbol secundario.|  
|[CTreeCtrl::GetVisibleCount](#getvisiblecount)|Recupera el número de elementos del árbol visible asociada a un control de vista de árbol.|  
|[CTreeCtrl::HitTest](#hittest)|Devuelve la posición actual del cursor relacionados con el `CTreeCtrl` objeto.|  
|[CTreeCtrl::InsertItem](#insertitem)|Inserta un nuevo elemento en un control de vista de árbol.|  
|[CTreeCtrl::ItemHasChildren](#itemhaschildren)|Devuelve cero si el elemento especificado tiene elementos secundarios.|  
|[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)|Asigna el identificador de accesibilidad especificadas para el identificador de un elemento de vista de árbol en el control de vista de árbol actual.|  
|[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)|El identificador se asigna a un elemento de vista de árbol en el control de vista de árbol actual a un identificador de accesibilidad.|  
|[CTreeCtrl::Select](#select)|Selecciona, se desplaza en la vista o vuelve a dibujar un elemento de vista de árbol especificado.|  
|[CTreeCtrl::SelectDropTarget](#selectdroptarget)|Vuelve a dibujar el elemento del árbol, como el destino de una operación de arrastrar y colocar.|  
|[CTreeCtrl::SelectItem](#selectitem)|Selecciona un elemento de vista de árbol especificado.|  
|[CTreeCtrl::SelectSetFirstVisible](#selectsetfirstvisible)|Selecciona un elemento de vista de árbol especificado como el primer elemento visible.|  
|[CTreeCtrl::SetAutoscrollInfo](#setautoscrollinfo)|Establece la velocidad de desplazamiento automático del control de vista de árbol actual.|  
|[CTreeCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo del control.|  
|[CTreeCtrl::SetCheck](#setcheck)|Establece el estado de activación de un elemento de control de árbol.|  
|[CTreeCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para el control de vista de árbol actual.|  
|[CTreeCtrl::SetImageList](#setimagelist)|Establece el identificador de la lista de imágenes asociada a un control de vista de árbol.|  
|[CTreeCtrl::SetIndent](#setindent)|Establece el desplazamiento (en píxeles) de un elemento de vista de árbol de su elemento primario.|  
|[CTreeCtrl::SetInsertMark](#setinsertmark)|Establece la marca de inserción en un control de vista de árbol.|  
|[CTreeCtrl::SetInsertMarkColor](#setinsertmarkcolor)|Establece el color utilizado para dibujar la marca de inserción de la vista de árbol.|  
|[CTreeCtrl::SetItem](#setitem)|Establece los atributos de un elemento de vista de árbol especificado.|  
|[CTreeCtrl::SetItemData](#setitemdata)|Establece el valor específico de la aplicación de 32 bits asociado al elemento.|  
|[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)|Establece el índice de la imagen que se muestra cuando el elemento especificado del control de vista de árbol actual está expandido.|  
|[CTreeCtrl::SetItemHeight](#setitemheight)|Establece el alto del árbol de elementos de la vista.|  
|[CTreeCtrl::SetItemImage](#setitemimage)|Asocia imágenes con un elemento.|  
|[CTreeCtrl::SetItemState](#setitemstate)|Establece el estado de un elemento.|  
|[CTreeCtrl::SetItemStateEx](#setitemstateex)|Establece el estado extendido del elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::SetItemText](#setitemtext)|Establece el texto de un elemento.|  
|[CTreeCtrl::SetLineColor](#setlinecolor)|Establece el color de línea actual para el control de vista de árbol.|  
|[CTreeCtrl::SetScrollTime](#setscrolltime)|Establece el tiempo máximo de desplazamiento para el control de vista de árbol.|  
|[CTreeCtrl::SetTextColor](#settextcolor)|Establece el color del texto del control.|  
|[CTreeCtrl::SetToolTips](#settooltips)|Establece a secundarios del control de vista de árbol de control de información sobre herramientas.|  
|[CTreeCtrl::ShowInfoTip](#showinfotip)|Muestra el recuadro informativo para el elemento especificado en el control de vista de árbol actual.|  
|[CTreeCtrl::SortChildren](#sortchildren)|Ordena a los elementos secundarios de un elemento primario especificado.|  
|[CTreeCtrl::SortChildrenCB](#sortchildrencb)|Ordena a los elementos secundarios de un elemento primario dado con una función de ordenación definido por la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control de vista de árbol" es una ventana que muestra una lista jerárquica de elementos, como los encabezados en un documento, las entradas de un índice, o los archivos y directorios en un disco. Cada elemento se compone de una etiqueta y una imagen de mapa de bits opcional, y cada elemento puede tener una lista de subelementos asociados a él. Si hace clic en un elemento, el usuario puede expandir y contraer la lista asociada de subelementos.  
  
 Este control (y por tanto la `CTreeCtrl` clase) está disponible sólo para los programas que se ejecutan en la versión de Windows 98 y Windows NT 4 y versiones posteriores.  
  
 Para obtener más información sobre el uso de `CTreeCtrl`, consulte:  
  
- [Controles](../../mfc/controls-mfc.md)  
  
- [Usar CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
- [Referencia de Control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb759988) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
-   Artículo de Knowledge Base Q222905: HOWTO: mostrar un menú contextual de CTreeCtrl  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="a-namecreatea--ctreectrlcreate"></a><a name="create"></a>CTreeCtrl::Create  
 Si especifica el control de árbol en una plantilla de cuadro de diálogo, o si está utilizando [CTreeView](../../mfc/reference/ctreeview-class.md), el control de árbol se crea automáticamente cuando se crea el cuadro de diálogo o la vista.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de vista de árbol. Aplicar estilos de ventana, se describe en [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)y cualquier combinación de [estilos de control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760013) como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Especifica el tamaño y la posición del control de vista de árbol. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria de la vista control de árbol, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control de vista de árbol  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si desea crear el control de árbol como una ventana secundaria de alguna otra ventana, utilice la **crear** función miembro. Si crea el control de árbol mediante **crear**, debe pasar a esta **WS_VISIBLE**, además de otros estilos de la vista de árbol.  
  
 Construya un `CTreeCtrl` en dos pasos. A continuación, llame la primera llamada al constructor **crear**, que crea el control de vista de árbol y se adjunta a la `CTreeCtrl` objeto.  
  
 Para crear un control de árbol con estilos de ventana extendidos, llame a [CreateEx](#createex) en lugar de **crear**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CTreeCtrl](../../mfc/reference/codesnippet/cpp/ctreectrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--ctreectrlcreateex"></a><a name="createex"></a>CTreeCtrl::CreateEx  
 Llame a esta función para crear un control (una ventana secundaria) y asociarla con el `CTreeCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Especifica el estilo del control de vista de árbol. Aplicar estilos de ventana, se describe en [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)y cualquier combinación de [estilos de control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760013) como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 0 en caso contrario, es distinto de cero si se realiza correctamente.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="a-namecreatedragimagea--ctreectrlcreatedragimage"></a><a name="createdragimage"></a>CTreeCtrl::CreateDragImage  
 Llame a esta función para crear un mapa de bits de arrastre para el elemento especificado en un control de vista de árbol, crear una lista de imágenes de mapa de bits y agregar el mapa de bits a la lista de imágenes.  
  
```  
CImageList* CreateDragImage(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de arrastrar el elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la lista de imágenes a la que se ha agregado el mapa de bits de arrastre, si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Una aplicación utiliza las funciones de la lista de imágenes para mostrar la imagen cuando se arrastra el elemento.  
  
 La `CImageList` objeto es permanente y debe eliminarlo cuando termine. Por ejemplo:  
  
 [!code-cpp[NVC_MFC_CTreeCtrl&#2;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_2.cpp)]  
  
##  <a name="a-namectreectrla--ctreectrlctreectrl"></a><a name="ctreectrl"></a>CTreeCtrl::CTreeCtrl  
 Construye un objeto `CTreeCtrl`.  
  
```  
CTreeCtrl();
```  
  
##  <a name="a-namedeleteallitemsa--ctreectrldeleteallitems"></a><a name="deleteallitems"></a>CTreeCtrl::DeleteAllItems  
 Llame a esta función para eliminar todos los elementos del control de vista de árbol.  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_3.cpp)]  
  
##  <a name="a-namedeleteitema--ctreectrldeleteitem"></a><a name="deleteitem"></a>CTreeCtrl::DeleteItem  
 Llame a esta función para eliminar un elemento de control de vista de árbol.  
  
```  
BOOL DeleteItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento de árbol que se va a eliminar. Si *hitem* tiene la **TVI_ROOT** valor, se eliminan todos los elementos de control de vista de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_4.cpp)]  
  
##  <a name="a-nameeditlabela--ctreectrleditlabel"></a><a name="editlabel"></a>CTreeCtrl::EditLabel  
 Llame a esta función para comenzar a editar en lugar del texto del elemento especificado.  
  
```  
CEdit* EditLabel(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento de árbol para editarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, un puntero a la `CEdit` objeto que se utiliza para editar el texto del elemento; en caso contrario **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La edición se consigue reemplazando el texto del elemento por un control de edición de la línea que contiene el texto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_5.cpp)]  
  
##  <a name="a-nameendeditlabelnowa--ctreectrlendeditlabelnow"></a><a name="endeditlabelnow"></a>CTreeCtrl::EndEditLabelNow  
 Finaliza la operación de edición en la etiqueta de un elemento de vista de árbol en el control de vista de árbol actual.  
  
```  
BOOL EndEditLabelNow(BOOL fCancelWithoutSave);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `fCancelWithoutSave`|`true`Para descartar los cambios en el elemento de vista de árbol antes de concluir la operación de edición o `false` para guardar los cambios en el elemento de vista de árbol antes de concluir la operación.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_ENDEDITLABELNOW](http://msdn.microsoft.com/library/windows/desktop/bb773564) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameensurevisiblea--ctreectrlensurevisible"></a><a name="ensurevisible"></a>CTreeCtrl::EnsureVisible  
 Llame a esta función para asegurarse de que un elemento de vista de árbol está visible.  
  
```  
BOOL EnsureVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento de árbol que se hacen visible.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** si el sistema desplaza los elementos en el control de vista de árbol para asegurarse de que el elemento especificado esté visible. De lo contrario, el valor devuelto es **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si es necesario, la función expande el elemento primario o desplaza el control de vista de árbol para que el elemento está visible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_6.cpp)]  
  
##  <a name="a-nameexpanda--ctreectrlexpand"></a><a name="expand"></a>CTreeCtrl::Expand  
 Llame a esta función para expandir o contraer la lista de elementos secundarios, si existe, asociado con el elemento primario dado.  
  
```  
BOOL Expand(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento de árbol está expandido.  
  
 `nCode`  
 Una marca que indica el tipo de acción que se realizará. Este indicador puede tener uno de los siguientes valores:  
  
- `TVE_COLLAPSE`Contrae la lista.  
  
- `TVE_COLLAPSERESET`Contrae la lista y quita los elementos secundarios. El **TVIS_EXPANDEDONCE** se restablece el indicador de estado. Este indicador se debe usar con el `TVE_COLLAPSE` marca.  
  
- `TVE_EXPAND`Expande la lista.  
  
- `TVE_TOGGLE`Contrae la lista si actualmente se expande o se expandirá si está contraída actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::EnsureVisible](#ensurevisible).  
  
##  <a name="a-namegetbkcolora--ctreectrlgetbkcolor"></a><a name="getbkcolor"></a>CTreeCtrl::GetBkColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773570), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa el color de fondo de ventana actual para el control. Si este valor es -1, el control está usando el color de la ventana sistema. En este caso, puede usar `::GetSysColor(COLOR_WINDOW)` para obtener el color actual del sistema que utiliza el control.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="a-namegetchecka--ctreectrlgetcheck"></a><a name="getcheck"></a>CTreeCtrl::GetCheck  
 Llame a esta función miembro para recuperar el estado de activación de un elemento.  
  
```  
BOOL GetCheck(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 El **HTREEITEM** sobre el que se va a recibir la información de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento de control de árbol está activado; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="a-namegetchilditema--ctreectrlgetchilditem"></a><a name="getchilditem"></a>CTreeCtrl::GetChildItem  
 Llamada a esta función para recuperar el árbol de ver el elemento que es el elemento secundario del elemento especificado por `hItem`.  
  
```  
HTREEITEM GetChildItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento secundario si se realiza correctamente; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#7;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_7.cpp)]  
  
##  <a name="a-namegetcounta--ctreectrlgetcount"></a><a name="getcount"></a>CTreeCtrl::GetCount  
 Llame a esta función para recuperar un recuento de los elementos de un control de vista de árbol.  
  
```  
UINT GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el control de vista de árbol.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_8.cpp)]  
  
##  <a name="a-namegetdrophilightitema--ctreectrlgetdrophilightitem"></a><a name="getdrophilightitem"></a>CTreeCtrl::GetDropHilightItem  
 Llame a esta función para recuperar el elemento que es el destino de una operación de arrastrar y colocar.  
  
```  
HTREEITEM GetDropHilightItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento que se quita si es correcto; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="a-namegeteditcontrola--ctreectrlgeteditcontrol"></a><a name="geteditcontrol"></a>CTreeCtrl::GetEditControl  
 Llame a esta función para recuperar el identificador del control de edición que se usa para editar el texto del elemento de vista de árbol.  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al control de edición que se usa para editar el texto del elemento, si es correcto; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#10;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_10.cpp)]  
  
##  <a name="a-namegetextendedstylea--ctreectrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTreeCtrl::GetExtendedStyle  
 Recupera los estilos extendidos que está utilizando el control de vista de árbol actual.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que contiene una combinación bit a bit (OR) del control de vista de árbol actual de estilos extendidos. Para obtener más información, consulte [estilos extendidos de vista de árbol de Control](http://msdn.microsoft.com/library/windows/desktop/bb759981).  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773580) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetfirstvisibleitema--ctreectrlgetfirstvisibleitem"></a><a name="getfirstvisibleitem"></a>CTreeCtrl::GetFirstVisibleItem  
 Llame a esta función para recuperar el primer elemento visible del control de vista de árbol.  
  
```  
HTREEITEM GetFirstVisibleItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del primer elemento visible; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="a-namegetimagelista--ctreectrlgetimagelist"></a><a name="getimagelist"></a>CTreeCtrl::GetImageList  
 Llame a esta función para recuperar el identificador de la normal o una lista de imágenes de estado asociado con el control de vista de árbol.  
  
```  
CImageList* GetImageList(UINT nImageList) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nImageList`  
 Tipo de lista de imágenes para recuperar. La lista de imágenes puede ser uno de los siguientes valores:  
  
- `TVSIL_NORMAL`Recupera la lista de imágenes normal, que contiene las imágenes seleccionadas y no seleccionadas para el elemento de vista de árbol.  
  
- `TVSIL_STATE`Recupera la lista de imágenes de estado, que contiene las imágenes para los elementos de vista de árbol que se encuentran en un estado definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la lista de imágenes del control si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Cada elemento en un control de vista de árbol puede tener un par de imágenes de mapa de bits asociado. Cuando se selecciona el elemento y la otra se muestra cuando el elemento no está seleccionado, se muestra una imagen. Por ejemplo, un elemento puede mostrar una carpeta abierta cuando se selecciona y una carpeta cerrada cuando no está seleccionada.  
  
 Para obtener más información sobre las listas de imágenes, consulte la [CImageList](../../mfc/reference/cimagelist-class.md) clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#11;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_11.cpp)]  
  
##  <a name="a-namegetindenta--ctreectrlgetindent"></a><a name="getindent"></a>CTreeCtrl::GetIndent  
 Llame a esta función para recuperar la cantidad, en píxeles, que secundarios se aplica sangría a los elementos en relación con sus elementos primarios.  
  
```  
UINT GetIndent() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cantidad de sangría se mide en píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#12;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_12.cpp)]  
  
##  <a name="a-namegetinsertmarkcolora--ctreectrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CTreeCtrl::GetInsertMarkColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773590), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que contiene el color de la marca de inserción actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#13;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_13.cpp)]  
  
##  <a name="a-namegetitema--ctreectrlgetitem"></a><a name="getitem"></a>CTreeCtrl::GetItem  
 Llame a esta función para recuperar los atributos del elemento de vista de árbol especificado.  
  
```  
BOOL GetItem(TVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Un puntero a un [estructura TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::DeleteItem](#deleteitem).  
  
##  <a name="a-namegetitemdataa--ctreectrlgetitemdata"></a><a name="getitemdata"></a>CTreeCtrl::GetItemData  
 Llame a esta función para recuperar el valor específico de la aplicación de 32 bits asociado al elemento especificado.  
  
```  
DWORD_PTR GetItemData(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyos datos se van a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor específico de la aplicación de 32 bits asociado con el elemento especificado por `hItem`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#14;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_14.cpp)]  
  
##  <a name="a-namegetitemexpandedimageindexa--ctreectrlgetitemexpandedimageindex"></a><a name="getitemexpandedimageindex"></a>CTreeCtrl::GetItemExpandedImageIndex  
 Recupera el índice de la imagen que se muestra cuando el elemento especificado del control de vista de árbol actual está expandido.  
  
```  
int GetItemExpandedImageIndex(HTREEITEM hItem)const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de control de vista de árbol.|  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la imagen que se muestra cuando el elemento especificado está expandido.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Que mensaje devuelve el [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura que describe el elemento de control de vista de árbol y, a continuación, este método recupera el `iExpandedImage` miembro de esa estructura.  
  
##  <a name="a-namegetitemheighta--ctreectrlgetitemheight"></a><a name="getitemheight"></a>CTreeCtrl::GetItemHeight  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_GETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773599), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
SHORT GetItemHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto del elemento, en píxeles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#15;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_15.cpp)]  
  
##  <a name="a-namegetitemimagea--ctreectrlgetitemimage"></a><a name="getitemimage"></a>CTreeCtrl::GetItemImage  
 Cada elemento en un control de vista de árbol puede tener un par de imágenes de mapa de bits asociado.  
  
```  
BOOL GetItemImage(
    HTREEITEM hItem,  
    int& nImage,  
    int& nSelectedImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuya imagen se va a recuperar.  
  
 `nImage`  
 Un entero que recibe el índice de la imagen del elemento dentro de la lista de imágenes del control de vista de árbol.  
  
 `nSelectedImage`  
 Un entero que recibe el índice de la imagen del elemento seleccionado en la lista de imágenes del control de vista de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Las imágenes aparecen en el lado izquierdo de la etiqueta de un elemento. Cuando se selecciona el elemento y la otra se muestra cuando el elemento no está seleccionado, se muestra una imagen. Por ejemplo, un elemento puede mostrar una carpeta abierta cuando se selecciona y una carpeta cerrada cuando no está seleccionada.  
  
 Llame a esta función para recuperar el índice de la imagen del elemento y su imagen seleccionada en la lista de imágenes del control de vista de árbol.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&16;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_16.cpp)]  
  
##  <a name="a-namegetitempartrecta--ctreectrlgetitempartrect"></a><a name="getitempartrect"></a>CTreeCtrl::GetItemPartRect  
 Recupera el rectángulo delimitador de un elemento especificado de un elemento especificado en el control de vista de árbol actual.  
  
```  
BOOL GetItemPartRect(
    HTREEITEM hItem,   
    int nPart,   
    LPRECT lpRect)const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de control de vista de árbol.|  
|[in] `nPart`|Identificador de la parte. Debe establecerse en `TVGIPR_BUTTON`.|  
|[out] `lpRect`|Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura. Si este método se realiza correctamente, la estructura recibe las coordenadas del rectángulo de la parte especificada por `hItem` y `nPart`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Cada elemento del control de árbol está limitado por un rectángulo de gráficos. Cada vez que se hace clic en un punto en el rectángulo, el elemento se dice que *aciertos*. Este método devuelve el rectángulo más grande que cuando un punto en el rectángulo que se hace clic, el elemento identificado por el `hItem` visita un parámetro.  
  
 Este método envía el `TVM_GETITEMPARTRECT` mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información, consulte el [TreeView_GetItemPartRect](http://msdn.microsoft.com/library/windows/desktop/bb773847) (macro).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se utiliza un identificador de accesibilidad y la [CTreeCtrl::MapAccIdToItem](#mapaccidtoitem) método para obtener un identificador para el elemento de vista de árbol raíz. A continuación, el ejemplo usa el identificador y el [CTreeCtrl::GetItemPartRect](#getitempartrect) método para dibujar un rectángulo 3D alrededor de ese elemento. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Usamos el [CTreeCtrl::MapItemToAccID](#mapitemtoaccid) para asociar el elemento de vista de árbol raíz con un identificador de accesibilidad.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;5](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="a-namegetitemrecta--ctreectrlgetitemrect"></a><a name="getitemrect"></a>CTreeCtrl::GetItemRect  
 Llame a esta función para recuperar el rectángulo delimitador de `hItem` y determinar si es visible o no.  
  
```  
BOOL GetItemRect(
    HTREEITEM hItem,  
    LPRECT lpRect,  
    BOOL bTextOnly) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 El identificador de un elemento de control de vista de árbol.  
  
 `lpRect`  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe el rectángulo delimitador. Las coordenadas son relativas a la esquina superior izquierda del control de vista de árbol.  
  
 *bTextOnly*  
 Si este parámetro es distinto de cero, el rectángulo delimitador incluye sólo el texto del elemento. De lo contrario, incluye toda la línea que ocupa el elemento en el control de vista de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento está visible, con el rectángulo delimitador contenido en `lpRect`. De lo contrario, 0 con `lpRect` sin inicializar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#17;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_19.cpp)]  
  
##  <a name="a-namegetitemstatea--ctreectrlgetitemstate"></a><a name="getitemstate"></a>CTreeCtrl::GetItemState  
 Devuelve el estado del elemento especificado por `hItem`.  
  
```  
UINT GetItemState(
    HTREEITEM hItem,  
    UINT nStateMask) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyo estado se va a recuperar.  
  
 `nStateMask`  
 Máscara que indica uno o más Estados va a recuperar. Para obtener más información sobre posibles valores de `nStateMask`, vea la explicación de la **estado** y **stateMask** los miembros de la [estructura TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Un **UINT** que contiene la operación OR bit a bit de los valores especificados por nStateMask. Para obtener información sobre los valores posibles, consulte [CTreeCtrl::GetItem](#getitem). Para buscar el valor de un estado específico, realice una operación AND bit a bit del valor de estado y el valor devuelto, como se muestra en el ejemplo siguiente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#18;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_20.cpp)]  
  
##  <a name="a-namegetitemstateexa--ctreectrlgetitemstateex"></a><a name="getitemstateex"></a>CTreeCtrl::GetItemStateEx  
 Recupera el estado extendido del elemento especificado en el control de vista de árbol actual.  
  
```  
UINT GetItemStateEx(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de control de vista de árbol.|  
  
### <a name="return-value"></a>Valor devuelto  
 El estado extendido del elemento. Para obtener más información, consulte el `uStateEx` miembro de la [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Que mensaje devuelve el [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura que describe el elemento de control de vista de árbol y este método recupera el `uStateEx` miembro de esa estructura.  
  
##  <a name="a-namegetitemtexta--ctreectrlgetitemtext"></a><a name="getitemtext"></a>CTreeCtrl::GetItemText  
 Devuelve el texto del elemento especificado por `hItem`.  
  
```  
CString GetItemText(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyo texto se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del elemento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetNextItem](#getnextitem).  
  
##  <a name="a-namegetlastvisibleitema--ctreectrlgetlastvisibleitem"></a><a name="getlastvisibleitem"></a>CTreeCtrl::GetLastVisibleItem  
 Recupera el último elemento no expandido del nodo en el control de vista de árbol actual.  
  
```  
HTREEITEM GetLastVisibleItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del último elemento de nodo sin expandir si el método es correcto; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_GETNEXTITEM](http://msdn.microsoft.com/library/windows/desktop/bb773622) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Para obtener más información, consulte el `TVGN_LASTVISIBLE` marca en el `flag` parámetro de ese mensaje.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Una o varias de estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se recupera un identificador del último elemento del nodo de vista de árbol no expandidas y, a continuación, dibuja un rectángulo 3D alrededor de ese elemento. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1 Nº&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_21.cpp)]  
  
##  <a name="a-namegetlinecolora--ctreectrlgetlinecolor"></a><a name="getlinecolor"></a>CTreeCtrl::GetLineColor  
 Esta función miembro implementa el comportamiento del mensaje de win32 [TVM_GETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773619), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF GetLineColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de línea actual.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&19;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_22.cpp)]  
  
##  <a name="a-namegetnextitema--ctreectrlgetnextitem"></a><a name="getnextitem"></a>CTreeCtrl::GetNextItem  
 Llamada a esta función para recuperar el árbol de ver el elemento que tiene la relación especificada, indicada por la `nCode` parámetro a `hItem`.  
  
```  
HTREEITEM GetNextItem(
    HTREEITEM hItem,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
 `nCode`  
 Una marca que indica el tipo de relación `hItem`. Este indicador puede ser uno de los siguientes valores:  
  
- `TVGN_CARET`Recupera el elemento seleccionado actualmente.  
  
- `TVGN_CHILD`Recupera el primer elemento secundario del elemento especificado por el `hItem` parámetro.  
  
- `TVGN_DROPHILITE`Recupera el elemento que es el destino de una operación de arrastrar y colocar.  
  
- `TVGN_FIRSTVISIBLE`Recupera el primer elemento visible.  
  
- `TVGN_LASTVISIBLE`Recupera el último elemento expandido en el árbol. Esto no recupera el último elemento visible en la ventana de vista de árbol.  
  
- `TVGN_NEXT`Recupera el siguiente elemento relacionado.  
  
- `TVGN_NEXTVISIBLE`Recupera el siguiente elemento visible que sigue al elemento especificado.  
  
- `TVGN_PARENT`Recupera al elemento primario del elemento especificado.  
  
- `TVGN_PREVIOUS`Recupera el elemento relacionado anterior.  
  
- `TVGN_PREVIOUSVISIBLE`Recupera el primer elemento visible que precede el elemento especificado.  
  
- `TVGN_ROOT`Recupera el primer elemento secundario del elemento raíz de que el elemento especificado es una parte.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento siguiente si se realiza correctamente; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devolverá **NULL** si el elemento que se va a recuperar es el nodo raíz del árbol. Por ejemplo, si usa este mensaje con la `TVGN_PARENT` marca en un elemento secundario de primer nivel del nodo raíz de la vista de árbol, se devolverá el mensaje **NULL**.  
  
### <a name="example"></a>Ejemplo  
 Para obtener un ejemplo del uso de `GetNextItem` en un bucle, consulte [CTreeCtrl::DeleteItem](#deleteitem).  
  
 [!code-cpp[NVC_MFC_CTreeCtrl&#20;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_23.cpp)]  
  
##  <a name="a-namegetnextsiblingitema--ctreectrlgetnextsiblingitem"></a><a name="getnextsiblingitem"></a>CTreeCtrl::GetNextSiblingItem  
 Llame a esta función para recuperar el siguiente elemento relacionado de `hItem`.  
  
```  
HTREEITEM GetNextSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento relacionado siguiente; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_CTreeCtrl](../../mfc/reference/codesnippet/cpp/ctreectrl-class_24.cpp)]  
  
##  <a name="a-namegetnextvisibleitema--ctreectrlgetnextvisibleitem"></a><a name="getnextvisibleitem"></a>CTreeCtrl::GetNextVisibleItem  
 Llame a esta función para recuperar el siguiente elemento visible de `hItem`.  
  
```  
HTREEITEM GetNextVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento visible siguiente; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="a-namegetparentitema--ctreectrlgetparentitem"></a><a name="getparentitem"></a>CTreeCtrl::GetParentItem  
 Llame a esta función para recuperar el elemento primario de `hItem`.  
  
```  
HTREEITEM GetParentItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento primario; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función devolverá **NULL** si el elemento primario del elemento especificado es el nodo raíz del árbol.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::EnsureVisible](#ensurevisible).  
  
##  <a name="a-namegetprevsiblingitema--ctreectrlgetprevsiblingitem"></a><a name="getprevsiblingitem"></a>CTreeCtrl::GetPrevSiblingItem  
 Llame a esta función para recuperar el elemento relacionado anterior de `hItem`.  
  
```  
HTREEITEM GetPrevSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del nodo relacionado anterior; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#22;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_25.cpp)]  
  
##  <a name="a-namegetprevvisibleitema--ctreectrlgetprevvisibleitem"></a><a name="getprevvisibleitem"></a>CTreeCtrl::GetPrevVisibleItem  
 Llame a esta función para recuperar el elemento visible anterior de `hItem`.  
  
```  
HTREEITEM GetPrevVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento visible anterior; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFC_CTreeCtrl #](../../mfc/reference/codesnippet/cpp/ctreectrl-class_26.cpp)]  
  
##  <a name="a-namegetrootitema--ctreectrlgetrootitem"></a><a name="getrootitem"></a>CTreeCtrl::GetRootItem  
 Llame a esta función para recuperar el elemento raíz del control de vista de árbol.  
  
```  
HTREEITEM GetRootItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento raíz; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::EditLabel](#editlabel).  
  
##  <a name="a-namegetscrolltimea--ctreectrlgetscrolltime"></a><a name="getscrolltime"></a>CTreeCtrl::GetScrollTime  
 Llame a esta función miembro para recuperar el tiempo máximo de desplazamiento para el control de vista de árbol.  
  
```  
UINT GetScrollTime() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tiempo de desplazamiento máximo, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de win32 [TVM_GETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773625), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetselectedcounta--ctreectrlgetselectedcount"></a><a name="getselectedcount"></a>CTreeCtrl::GetSelectedCount  
 Recupera el número de elementos seleccionados en el control de vista de árbol actual.  
  
```  
UINT GetSelectedCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos seleccionados.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_GETSELECTEDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb773629) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetselecteditema--ctreectrlgetselecteditem"></a><a name="getselecteditem"></a>CTreeCtrl::GetSelectedItem  
 Llame a esta función para recuperar el elemento actualmente seleccionado del control de vista de árbol.  
  
```  
HTREEITEM GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento seleccionado; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#24;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_27.cpp)]  
  
##  <a name="a-namegettextcolora--ctreectrlgettextcolor"></a><a name="gettextcolor"></a>CTreeCtrl::GetTextColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773633), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa el color de texto actual. Si este valor es -1, el control está usando el color del sistema para el color del texto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="a-namegettooltipsa--ctreectrlgettooltips"></a><a name="gettooltips"></a>CTreeCtrl::GetToolTips  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773729), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que va a usar el control de árbol. Si el [crear](#create) función miembro utiliza el estilo **TVS_NOTOOLTIPS**, no hay información sobre herramientas se utiliza, y **NULL** se devuelve.  
  
### <a name="remarks"></a>Comentarios  
 La implementación de MFC de `GetToolTips` devuelve un `CToolTipCtrl` objeto, que se utiliza el control de árbol, en lugar de un identificador de un control de información sobre herramientas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#25;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_28.cpp)]  
  
##  <a name="a-namegetvisiblecounta--ctreectrlgetvisiblecount"></a><a name="getvisiblecount"></a>CTreeCtrl::GetVisibleCount  
 Llame a esta función para recuperar un recuento de los elementos visibles en un control de vista de árbol.  
  
```  
UINT GetVisibleCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos visibles en el control de vista de árbol; de lo contrario,-1.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetCheck](#setcheck).  
  
##  <a name="a-namehittesta--ctreectrlhittest"></a><a name="hittest"></a>CTreeCtrl::HitTest  
 Llame a esta función para determinar la ubicación del punto especificado con respecto al área cliente de un control de vista de árbol.  
  
```  
HTREEITEM HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
  
HTREEITEM HitTest(TVHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 Coordenadas de cliente del punto de probar.  
  
 `pFlags`  
 Puntero a un entero que recibe información sobre los resultados de la prueba de posicionamiento. Puede ser uno o varios de los valores enumeran en la **marcas** miembros en la sección Comentarios.  
  
 `pHitTestInfo`  
 Dirección de un [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) estructura que contiene la posición para visitar la prueba y que recibe información sobre los resultados de la prueba de posicionamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del elemento de vista de árbol que ocupa el punto especificado o **NULL** si no hay ningún elemento ocupa el punto.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a esta función, la `pt` parámetro especifica las coordenadas del punto de prueba. La función devuelve el identificador del elemento en el punto especificado o **NULL** si no hay ningún elemento ocupa el punto. Además, el `pFlags` parámetro contiene un valor que indica la ubicación del punto especificado. Los valores posibles son:  
  
|||  
|-|-|  
|Valor|Significado|  
|TVHT_ABOVE|Por encima del área de cliente.|  
|TVHT_BELOW|Debajo del área de cliente.|  
|TVHT_NOWHERE|En el área de cliente, pero por debajo del último elemento.|  
|TVHT_ONITEM|En el mapa de bits o una etiqueta asociada a un elemento.|  
|TVHT_ONITEMBUTTON|En el botón asociado al elemento.|  
|TVHT_ONITEMICON|En el mapa de bits asociado al elemento.|  
|TVHT_ONITEMINDENT|En la sangría asociada al elemento.|  
|TVHT_ONITEMLABEL|En la etiqueta (cadena) asociada al elemento.|  
|TVHT_ONITEMRIGHT|En el área a la derecha de un elemento.|  
|TVHT_ONITEMSTATEICON|En el icono de estado para un elemento de vista de árbol que se encuentra en un estado definido por el usuario.|  
|TVHT_TOLEFT|A la izquierda del área de cliente.|  
|TVHT_TORIGHT|A la derecha del área de cliente.|  
|||  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_CTreeCtrl #](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="a-nameinsertitema--ctreectrlinsertitem"></a><a name="insertitem"></a>CTreeCtrl::InsertItem  
 Llame a esta función para insertar un nuevo elemento en un control de vista de árbol.  
  
```  
HTREEITEM InsertItem(LPTVINSERTSTRUCT lpInsertStruct);

 
HTREEITEM InsertItem(
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    HTREEITEM hParent,  
    HTREEITEM hInsertAfter);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpInsertStruct*  
 Un puntero a un `TVINSERTSTRUCT` que especifica los atributos del elemento de vista de árbol va a insertar.  
  
 `nMask`  
 Entero que especifica qué atributos que se van a establecer. Consulte la `TVITEM` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lpszItem`  
 Dirección de una cadena que contiene el texto del elemento.  
  
 `nImage`  
 Índice de la imagen del elemento de lista de imágenes del control de vista de árbol.  
  
 `nSelectedImage`  
 Índice de la imagen del elemento seleccionado en la lista de imágenes del control de vista de árbol.  
  
 `nState`  
 Especifica los valores de los Estados del elemento. Vea árbol de Estados del elemento de Control de vista en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de Estados adecuados.  
  
 `nStateMask`  
 Especifica que los Estados que se van a establecer. Consulte la `TVITEM` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lParam`  
 Un valor específico de la aplicación de 32 bits asociado al elemento.  
  
 `hParent`  
 Identificador del elemento primario del elemento insertado.  
  
 *hInsertAfter*  
 Identificador del elemento después del cual se insertará el nuevo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del nuevo elemento si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El ejemplo muestra las situaciones en las que podría ser utilizar cada versión de la función cuando se inserta un elemento de control de árbol.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&27;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_30.cpp)]  
  
##  <a name="a-nameitemhaschildrena--ctreectrlitemhaschildren"></a><a name="itemhaschildren"></a>CTreeCtrl::ItemHasChildren  
 Use esta función para determinar si el elemento de árbol especificado por `hItem` tiene elementos secundarios.  
  
```  
BOOL ItemHasChildren(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el elemento de árbol especificado por `hItem` tiene elementos secundarios; 0 si no es así.  
  
### <a name="remarks"></a>Comentarios  
 Si es así, puede usar [CTreeCtrl::GetChildItem](#getchilditem) para recuperar dichos elementos secundarios.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetSelectedItem](#getselecteditem).  
  
##  <a name="a-namemapaccidtoitema--ctreectrlmapaccidtoitem"></a><a name="mapaccidtoitem"></a>CTreeCtrl::MapAccIdToItem  
 Asigna el identificador de accesibilidad especificadas para el identificador de un elemento de vista de árbol en el control de vista de árbol actual.  
  
```  
HTREEITEM MapAccIdToItem(UINT uAccId) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `uAccId`|Un identificador de accesibilidad de un elemento en el elemento de vista de árbol.|  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de un elemento de vista de árbol ( `HTREEITEM`) que corresponde a la `uAccId` parámetro. Para obtener más información, consulte el `hItem` miembro de la [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Las ayudas de accesibilidad son aplicaciones que ayudan a las personas con discapacidades utilizan los equipos. Se utiliza un identificador de accesibilidad mediante el `IAccessible` interfaz para especificar únicamente un elemento en una ventana. Para obtener más información acerca de los identificadores de accesibilidad, busque el tema "Acerca de la compatibilidad con Active Accessibility" en [Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322).  
  
 Este método envía el [TVM_MAPACCIDTOHTREEITEM](http://msdn.microsoft.com/library/windows/desktop/bb773734) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se utiliza un identificador de accesibilidad y la [CTreeCtrl::MapAccIdToItem](#mapaccidtoitem) método para obtener un identificador para el elemento de vista de árbol raíz. En el ejemplo se usa el identificador y el [CTreeCtrl::GetItemPartRect](#getitempartrect) método para dibujar un rectángulo 3D alrededor de ese elemento. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Usamos el [CTreeCtrl::MapItemToAccID](#mapitemtoaccid) para asociar el elemento de vista de árbol raíz con un identificador de accesibilidad.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;5](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="a-namemapitemtoaccida--ctreectrlmapitemtoaccid"></a><a name="mapitemtoaccid"></a>CTreeCtrl::MapItemToAccID  
 El identificador especificado de un elemento de vista de árbol en el control de vista de árbol actual se asigna a un identificador de accesibilidad.  
  
```  
UINT MapItemToAccID(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de vista de árbol en el control. Para obtener más información, consulte el `hItem` miembro de la [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de accesibilidad que corresponde a la `hItem` parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Las ayudas de accesibilidad son aplicaciones que ayudan a las personas con discapacidades utilizan los equipos. Se utiliza un identificador de accesibilidad mediante el `IAccessible` interfaz para especificar únicamente un elemento en una ventana. Para obtener más información acerca de los identificadores de accesibilidad, busque el tema "Acerca de la compatibilidad con Active Accessibility" en [Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322).  
  
 Este método envía el [TVM_MAPHTREEITEMTOACCID](http://msdn.microsoft.com/library/windows/desktop/bb773735) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se obtiene un número de identificación de un elemento de control de vista de árbol. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Este ejemplo de código obtiene un número de identificación único para el nodo de país o región de la raíz.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/ctreectrl-class_31.cpp)]  
  
##  <a name="a-nameselecta--ctreectrlselect"></a><a name="select"></a>CTreeCtrl::Select  
 Llame a esta función para seleccionar el elemento de vista de árbol determinado, desplazar el elemento en la vista o volver a dibujar el elemento en el estilo que se utiliza para indicar el destino de una operación de arrastrar y colocar.  
  
```  
BOOL Select(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
 `nCode`  
 El tipo de acción que se realizará. Este parámetro puede ser uno de los siguientes valores:  
  
- `TVGN_CARET`Establece la selección al elemento especificado.  
  
- `TVGN_DROPHILITE`Vuelve a dibujar el elemento especificado en el estilo utilizado para indicar el destino de una operación de arrastrar y colocar.  
  
- `TVGN_FIRSTVISIBLE`Se desplaza verticalmente a la vista de árbol para que el elemento especificado es el primer elemento visible.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si `nCode` contiene el valor `TVGN_CARET`, la ventana primaria recibe la **TVN_SELCHANGING** y **TVN_SELCHANGED** mensajes de notificación. Además, si el elemento especificado es el elemento secundario de un elemento primario contraído, la lista del elemento primario de los elementos secundarios se expande para mostrar el elemento especificado. En este caso, la ventana primaria recibe la **TVN_ITEMEXPANDING** y **TVN_ITEMEXPANDED** mensajes de notificación.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::HitTest](#hittest).  
  
##  <a name="a-nameselectdroptargeta--ctreectrlselectdroptarget"></a><a name="selectdroptarget"></a>CTreeCtrl::SelectDropTarget  
 Llame a esta función para volver a dibujar el elemento en el estilo que se utiliza para indicar el destino de una operación de arrastrar y colocar.  
  
```  
BOOL SelectDropTarget(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="a-nameselectitema--ctreectrlselectitem"></a><a name="selectitem"></a>CTreeCtrl::SelectItem  
 Llame a esta función para seleccionar el elemento de vista de árbol determinado.  
  
```  
BOOL SelectItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador de un elemento del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si `hItem` es **NULL**, a continuación, esta función selecciona ningún elemento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_CTreeCtrl #](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="a-nameselectsetfirstvisiblea--ctreectrlselectsetfirstvisible"></a><a name="selectsetfirstvisible"></a>CTreeCtrl::SelectSetFirstVisible  
 Llame a esta función para desplazarse verticalmente la vista de árbol para que el elemento especificado es el primer elemento visible.  
  
```  
BOOL SelectSetFirstVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento de árbol que se establecerá como el primer elemento visible.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La función envía un mensaje a la ventana con el `TVM_SELECTITEM` y `TVGN_FIRSTVISIBLE` parámetros del mensaje.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#28;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_32.cpp)]  
  
##  <a name="a-namesetautoscrollinfoa--ctreectrlsetautoscrollinfo"></a><a name="setautoscrollinfo"></a>CTreeCtrl::SetAutoscrollInfo  
 Establece la velocidad de desplazamiento automático del control de vista de árbol actual.  
  
```  
BOOL SetAutoscrollInfo(
    UINT uPixelsPerSec,   
    UINT uUpdateTime);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `uPixelsPerSec`|El número de píxeles por segundo para desplazarse.|  
|[in] `uUpdateTime`|El intervalo de tiempo entre actualizaciones del control.|  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `true`.  
  
### <a name="remarks"></a>Comentarios  
 Los parámetros de desplazamiento automático se utilizan para desplazar en la vista de un elemento que no está visible actualmente. Debe tener el control de vista de árbol del `TVS_EX_AUTOHSCROLL` estilo, que se describe en extendido [estilos extendidos de vista de árbol de Control](http://msdn.microsoft.com/library/windows/desktop/bb759981).  
  
 Este método envía el [TVM_SETAUTOSCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb773738) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el comportamiento de desplazamiento automático del control de vista de árbol actual. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Hemos hecho intencionadamente el control de vista de árbol estrecho para que debe desplazarse automáticamente para mostrar el elemento del árbol que tiene el foco. El ejemplo de código establece el control de vista de árbol para desplazarse automáticamente 30 píxeles por segundo cada 5 segundos hasta que el elemento del árbol de la vista.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1 Nº&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_33.cpp)]  
  
##  <a name="a-namesetbkcolora--ctreectrlsetbkcolor"></a><a name="setbkcolor"></a>CTreeCtrl::SetBkColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773741), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `clr`  
 Un **COLORREF** valor que contiene el nuevo color de fondo. Si este valor es -1, el control volverá a utilizar el color del sistema para el color de fondo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa el color de texto actual. Si este valor es -1, el control está usando el color del sistema para el color del texto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::SetTextColor](#settextcolor).  
  
##  <a name="a-namesetchecka--ctreectrlsetcheck"></a><a name="setcheck"></a>CTreeCtrl::SetCheck  
 Llame a esta función miembro para establecer el estado de activación de un elemento de control de árbol.  
  
```  
BOOL SetCheck(
    HTREEITEM hItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 El **HTREEITEM** para recibir el cambio de estado de comprobación.  
  
 `fCheck`  
 Indica si se pueden activar o desactivar el elemento del control de árbol. De forma predeterminada, `SetCheck` establece el elemento que se va a comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el elemento de control de árbol está activado ( `fCheck` establecido en **TRUE**), el elemento aparece con una marca de verificación adyacente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#29;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_34.cpp)]  
  
### <a name="example"></a>Ejemplo  
 Para utilizar las casillas de verificación, establezca TVS_CHECKBOXES antes de rellenar el control de árbol.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&30;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_35.cpp)]  
  
##  <a name="a-namesetextendedstylea--ctreectrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTreeCtrl::SetExtendedStyle  
 Establece los estilos extendidos para el control de vista de árbol actual.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,   
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwExMask`|Máscara de bits que especifica qué estilos en el control de vista de árbol actual se ven afectados por este método. Si este parámetro es cero, se omite y el valor de la `dwExStyles` parámetro se asigna al control de vista de árbol.<br /><br /> Especifique cero o una combinación bit a bit (OR) de estilos que se describe en [estilos extendidos de vista de árbol de Control](http://msdn.microsoft.com/library/windows/desktop/bb759981).|  
|[in] `dwExStyles`|Máscara de bits que especifica qué estilos en la vista de árbol actual de control para establecer o borrar.<br /><br /> Para establecer una combinación de estilos, especifique una combinación bit a bit (OR) de estilos que se describe en [estilos extendidos de vista de árbol de Control](http://msdn.microsoft.com/library/windows/desktop/bb759981). Para borrar un conjunto de estilos, especifique cero.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que contiene el anterior control estilos extendidos.  
  
### <a name="remarks"></a>Comentarios  
 Este método borra los estilos especificados en la `dwExMask` parámetro, a continuación, Establece los estilos especificados en la `dwExStyles` parámetro. Sólo los estilos extendidos que se corresponden con los bits de `dwExMask` cambiar.  
  
 Este método envía el [TVM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773744) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se agrega el `TVS_EX_AUTOHSCROLL` extendido de estilo para el control de vista de árbol actual. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Hemos hecho intencionadamente el control de vista de árbol estrecho para que debe desplazarse automáticamente para mostrar el elemento del árbol que tiene el foco.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_36.cpp)]  
  
##  <a name="a-namesetimagelista--ctreectrlsetimagelist"></a><a name="setimagelist"></a>CTreeCtrl::SetImageList  
 Llame a esta función para establecer el valor normal o lista de imágenes de estado para un árbol de control de la vista y volver a dibujar el control mediante las nuevas imágenes.  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>Parámetros  
 `pImageList`  
 Puntero a la lista de imágenes para asignar. Si `pImageList` es **NULL**, se quitan todas las imágenes desde el control de vista de árbol.  
  
 `nImageListType`  
 Tipo de lista de imágenes para establecer. La lista de imágenes puede ser uno de los siguientes valores:  
  
- `TVSIL_NORMAL`Establece la lista de imágenes normal, que contiene las imágenes seleccionadas y no seleccionadas para el elemento de vista de árbol. Debe utilizar este estado para imágenes superpuestas.  
  
- `TVSIL_STATE`Establece la lista de imágenes de estado, que contiene las imágenes para los elementos de vista de árbol que se encuentran en un estado definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la lista anterior de imagen, si lo hay; de lo contrario, **NULL**.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetImageList](#getimagelist).  
  
##  <a name="a-namesetindenta--ctreectrlsetindent"></a><a name="setindent"></a>CTreeCtrl::SetIndent  
 Llame a esta función para establecer el ancho de la sangría de un control de vista de árbol y volver a dibujar el control para reflejar el nuevo ancho.  
  
```  
void SetIndent(UINT nIndent);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndent`  
 Ancho, en píxeles, de la sangría. Si `nIndent` es menor que el ancho mínimo definido por el sistema, se establece el nuevo ancho en el mínimo definido por el sistema.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetIndent](#getindent).  
  
##  <a name="a-namesetinsertmarka--ctreectrlsetinsertmark"></a><a name="setinsertmark"></a>CTreeCtrl::SetInsertMark  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb773753), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
BOOL SetInsertMark(
    HTREEITEM hItem,  
    BOOL fAfter = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 **HTREEITEM** que especifica en qué elemento se colocará la marca de inserción. Si este argumento es **NULL**, se quita la marca de inserción.  
  
 *fAfter*  
 **BOOL** valor que especifica si la marca de inserción se coloca antes o después del elemento especificado. Si este argumento es distinto de cero, la marca de inserción se situará después del elemento. Si este argumento es cero, se colocará la marca de inserción antes del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#31;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_37.cpp)]  
  
##  <a name="a-namesetinsertmarkcolora--ctreectrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CTreeCtrl::SetInsertMarkColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773755), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrNew`  
 Un **COLORREF** valor que contiene el nuevo color de marca de inserción.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que contiene el color de la marca de inserción anterior.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor).  
  
##  <a name="a-namesetitema--ctreectrlsetitem"></a><a name="setitem"></a>CTreeCtrl::SetItem  
 Llame a esta función para establecer los atributos del elemento de vista de árbol especificado.  
  
```  
BOOL SetItem(TVITEM* pItem);

 
BOOL SetItem(
    HTREEITEM hItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `pItem`  
 Un puntero a un [estructura TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) atributos de estructura que contiene el nuevo elemento, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `hItem`  
 Identificador del elemento cuyos atributos que se van a establecer. Consulte la **hItem** miembro de la `TVITEM` estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `nMask`  
 Entero que especifica qué atributos que se van a establecer. Consulte la **máscara** miembro de la `TVITEM` estructura.  
  
 `lpszItem`  
 Dirección de una cadena que contiene el texto del elemento.  
  
 `nImage`  
 Índice de la imagen del elemento de lista de imágenes del control de vista de árbol. Consulte la `iImage` miembro de la `TVITEM` estructura.  
  
 `nSelectedImage`  
 Índice de la imagen del elemento seleccionado en la lista de imágenes del control de vista de árbol. Consulte la **iSelectedImage** miembro de la `TVITEM` estructura.  
  
 `nState`  
 Especifica los valores de los Estados del elemento. Consulte la **estado** miembro de la `TVITEM` estructura.  
  
 `nStateMask`  
 Especifica que los Estados que se van a establecer. Consulte la **stateMask** miembro de la `TVITEM` estructura.  
  
 `lParam`  
 Un valor específico de la aplicación de 32 bits asociado al elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 En el `TVITEM` estructura, el **hItem** miembro identifica el elemento y el **máscara** miembro especifica qué atributos que se van a establecer.  
  
 Si el **máscara** miembro o el `nMask` parámetro especifica la `TVIF_TEXT` valor, el **pszText** miembro o `lpszItem` es la dirección de una cadena terminada en null y el **cchTextMax** miembro se omite. Si **máscara** (o `nMask`) especifica la `TVIF_STATE` valor, el **stateMask** miembro o el `nStateMask` parámetro especifica el elemento que se indica para cambiar y **estado** miembro o `nState` parámetro contiene los valores de esos Estados.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#32;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_38.cpp)]  
  
##  <a name="a-namesetitemdataa--ctreectrlsetitemdata"></a><a name="setitemdata"></a>CTreeCtrl::SetItemData  
 Llame a esta función para establecer el valor de específicos de la aplicación de 32 bits asociado al elemento especificado.  
  
```  
BOOL SetItemData(
    HTREEITEM hItem,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyos datos se van a recuperar.  
  
 `dwData`  
 Un valor específico de la aplicación de 32 bits asociado con el elemento especificado por `hItem`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl Nº&33;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_39.cpp)]  
  
##  <a name="a-namesetitemexpandedimageindexa--ctreectrlsetitemexpandedimageindex"></a><a name="setitemexpandedimageindex"></a>CTreeCtrl::SetItemExpandedImageIndex  
 Establece el índice de la imagen que se muestra cuando el elemento especificado del control de vista de árbol actual está expandido.  
  
```  
BOOL SetItemExpandedImageIndex(
    HTREEITEM hItem,   
    int iExpandedImage);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de control de vista de árbol.|  
|[in] `iExpandedImage`|El índice de la imagen que se muestra cuando el elemento especificado está expandido.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Este método asigna la `iExpandedImage` parámetro para la `iExpandedImage` miembro de un [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura y, a continuación, usa esa estructura en el mensaje.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente es una prueba trivial para determinar si la [CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex) método devuelve el valor establecido por el [CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex) método. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s1 Nº&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_40.cpp)]  
  
##  <a name="a-namesetitemheighta--ctreectrlsetitemheight"></a><a name="setitemheight"></a>CTreeCtrl::SetItemHeight  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773761), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
SHORT SetItemHeight(SHORT cyHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `cyHeight`  
 Especifica el nuevo alto de cada elemento en la vista de árbol, en píxeles. Si este argumento es menor que el alto de las imágenes, se establecerá el alto de las imágenes. Si este argumento no es par, se redondeará hacia abajo hasta más próximo incluso valor. Si este argumento es -1, el control se revertirá para usar su alto del elemento predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Alto anterior de los elementos, en píxeles.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetItemHeight](#getitemheight).  
  
##  <a name="a-namesetitemimagea--ctreectrlsetitemimage"></a><a name="setitemimage"></a>CTreeCtrl::SetItemImage  
 Asocia imágenes con un elemento.  
  
```  
BOOL SetItemImage(
    HTREEITEM hItem,  
    int nImage,  
    int nSelectedImage);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuya imagen que se va a establecer.  
  
 `nImage`  
 Índice de la imagen del elemento de lista de imágenes del control de vista de árbol.  
  
 `nSelectedImage`  
 Índice de la imagen del elemento seleccionado en la lista de imágenes del control de vista de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Cada elemento en un control de vista de árbol puede tener un par de imágenes de mapa de bits asociado. Las imágenes aparecen en el lado izquierdo de la etiqueta de un elemento. Cuando se selecciona el elemento y la otra se muestra cuando el elemento no está seleccionado, se muestra una imagen. Por ejemplo, un elemento puede mostrar una carpeta abierta cuando se selecciona y una carpeta cerrada cuando no está seleccionada.  
  
 Llame a esta función para establecer el índice de la imagen del elemento y su imagen seleccionada en la lista de imágenes del control de vista de árbol.  
  
 Para obtener más información sobre las imágenes, consulte [CImageList](../../mfc/reference/cimagelist-class.md).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetItemImage](#getitemimage).  
  
##  <a name="a-namesetitemstatea--ctreectrlsetitemstate"></a><a name="setitemstate"></a>CTreeCtrl::SetItemState  
 Establece el estado del elemento especificado por `hItem`.  
  
```  
BOOL SetItemState(
    HTREEITEM hItem,  
    UINT nState,  
    UINT nStateMask);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyo estado se va a establecer.  
  
 `nState`  
 Especifica los Estados nuevo para el elemento.  
  
 `nStateMask`  
 Especifica qué estados se puede cambiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener información sobre los Estados, consulte [CTreeCtrl::GetItem](#getitem).  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetItemState](#getitemstate).  
  
##  <a name="a-namesetitemstateexa--ctreectrlsetitemstateex"></a><a name="setitemstateex"></a>CTreeCtrl::SetItemStateEx  
 Establece el estado extendido del elemento especificado en el control de vista de árbol actual.  
  
```  
BOOL SetItemStateEx(
    HTREEITEM hItem,   
    UINT uStateEx);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de control de vista de árbol.|  
|[in] `uStateEx`|El estado extendido del elemento. Para obtener más información, consulte el `uStateEx` miembro de la [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Este método asigna la `uStateEx` parámetro para la `uStateEx` miembro de un [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura y, a continuación, usa esa estructura en el mensaje.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define una variable, `m_treeCtrl`, que se utiliza para tener acceso al control de vista de árbol actual. El ejemplo de código también define varias variables HTREEITEM y un entero sin signo. Estas variables se utilizan en el ejemplo siguiente.  
  
 [!code-cpp[1 NVC_MFC_CTreeCtrl_s1](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece un elemento de vista de árbol en estado deshabilitado. En una sección anterior del ejemplo de código, que no se muestra, hemos creado una vista de árbol que consta de un nodo de país o región de la raíz de los Estados Unidos, subnodos para los Estados de Pensilvania y Washington y elementos del árbol de ciudades de esos Estados. Este ejemplo de código establece el nodo de Pensilvania en estado deshabilitado.  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;7](../../mfc/reference/codesnippet/cpp/ctreectrl-class_41.cpp)]  
  
##  <a name="a-namesetitemtexta--ctreectrlsetitemtext"></a><a name="setitemtext"></a>CTreeCtrl::SetItemText  
 Establece el texto del elemento especificado por `hItem`.  
  
```  
BOOL SetItemText(
    HTREEITEM hItem,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento cuyo texto se va a establecer.  
  
 `lpszItem`  
 Dirección de una cadena que contiene el texto del elemento nuevo  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#34;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_42.cpp)]  
  
##  <a name="a-namesetlinecolora--ctreectrlsetlinecolor"></a><a name="setlinecolor"></a>CTreeCtrl::SetLineColor  
 Llame a esta función miembro para establecer el color de línea actual para el control de vista de árbol.  
  
```  
COLORREF SetLineColor(COLORREF clrNew = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrNew`  
 El nuevo color de línea.  
  
### <a name="return-value"></a>Valor devuelto  
 Color de la línea anterior.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de win32 [TVM_SETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773764), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#35;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_43.cpp)]  
  
##  <a name="a-namesetscrolltimea--ctreectrlsetscrolltime"></a><a name="setscrolltime"></a>CTreeCtrl::SetScrollTime  
 Llame a esta función miembro para establecer el tiempo máximo de desplazamiento para el control de vista de árbol.  
  
```  
UINT SetScrollTime(UINT uScrollTime);
```  
  
### <a name="parameters"></a>Parámetros  
 *uScrollTime*  
 El nuevo tiempo de desplazamiento máximo, en milisegundos. Si este valor es menor que 100, será redondeado hasta 100.  
  
### <a name="return-value"></a>Valor devuelto  
 El tiempo máximo de desplazamiento anterior, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de win32 [TVM_SETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773767), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesettextcolora--ctreectrlsettextcolor"></a><a name="settextcolor"></a>CTreeCtrl::SetTextColor  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773769), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 `clr`  
 Un **COLORREF** valor que contiene el nuevo color de texto. Si este argumento es -1, el control volverá a utilizar el color del sistema para el color de texto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa el color del texto anterior. Si este valor es -1, el control estaba utilizando el color del sistema para el color del texto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#36;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_44.cpp)]  
  
##  <a name="a-namesettooltipsa--ctreectrlsettooltips"></a><a name="settooltips"></a>CTreeCtrl::SetToolTips  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [TVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773772), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWndTip`  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que utilice el control de árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md) objeto que contiene la información sobre herramientas usada previamente por el control o **NULL** si no hay información sobre herramientas se ha usado anteriormente.  
  
### <a name="remarks"></a>Comentarios  
 Para utilizar la información sobre herramientas, indicar la **TVS_NOTOOLTIPS** estilo cuando cree la `CTreeCtrl` objeto.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CTreeCtrl::GetToolTips](#gettooltips).  
  
##  <a name="a-nameshowinfotipa--ctreectrlshowinfotip"></a><a name="showinfotip"></a>CTreeCtrl::ShowInfoTip  
 Muestra el recuadro informativo para el elemento especificado en el control de vista de árbol actual.  
  
```  
void ShowInfoTip(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `hItem`|Identificador de un elemento de vista de árbol en el control. Para obtener más información, consulte el `hItem` miembro de la [TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459) estructura.|  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre la diferencia entre la información sobre herramientas y recuadros informativos, busque el tema "Información sobre herramientas y recuadros informativos" en [Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322).  
  
 Este método envía el [TVM_SHOWINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb773779) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesortchildrena--ctreectrlsortchildren"></a><a name="sortchildren"></a>CTreeCtrl::SortChildren  
 Llame a esta función para ordenar alfabéticamente los elementos secundarios del elemento primario dado en un control de vista de árbol.  
  
```  
BOOL SortChildren(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `hItem`  
 Identificador del elemento primario cuyos elementos secundarios son esté ordenada. Si `hItem` es **NULL**, la ordenación se llevará a cabo desde la raíz del árbol.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 `SortChildren`no se recorrer el árbol; sólo los elementos secundarios inmediatos de `hItem` se ordenará.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#37;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_45.cpp)]  
  
##  <a name="a-namesortchildrencba--ctreectrlsortchildrencb"></a><a name="sortchildrencb"></a>CTreeCtrl::SortChildrenCB  
 Llame a esta función para ordenar los elementos de vista de árbol mediante una función de devolución de llamada definida por la aplicación que compara los elementos.  
  
```  
BOOL SortChildrenCB(LPTVSORTCB pSort);
```  
  
### <a name="parameters"></a>Parámetros  
 *pSort*  
 Puntero a un [TVSORTCB](http://msdn.microsoft.com/library/windows/desktop/bb773462) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Función de comparación de la estructura, **lpfnCompare**, debe devolver un valor negativo si el primer elemento debería preceder el segundo, de valor positivo si el primer elemento debería seguir el segundo, o cero si los dos elementos son equivalentes.  
  
 El `lParam1` y `lParam2` parámetros corresponden a la **lParam** miembro de la [estructura TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) estructura de los dos elementos que se comparan. El `lParamSort` parámetro corresponde a la **lParam** miembro de la `TV_SORTCB` estructura.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CTreeCtrl&#38;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_46.cpp)]  
  
 [!code-cpp[NVC_MFC_CTreeCtrl&#39;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_47.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CImageList (clase)](../../mfc/reference/cimagelist-class.md)

