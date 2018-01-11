---
title: Clase CMFCToolBarComboBoxButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
dev_langs: C++
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c7732d58c8e37683f670f6f13bb4df5f49e4ef24
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Clase CMFCToolBarComboBoxButton
Un botón de barra de herramientas que contiene un control de cuadro combinado ( [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCToolBarComboBoxButton : public CMFCToolBarButton  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Construye un objeto `CMFCToolBarComboBoxButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Agrega un elemento al final de la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Agrega un elemento a la lista del cuadro combinado. El orden de los elementos de la lista se especifica por `Compare`.|  
|[CMFCToolBarComboBoxButton::Compare](#compare)|Compara dos elementos. Llamado ordenar los elementos que `AddSortedItems` agrega a la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición para el botón de cuadro combinado.|  
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Elimina un elemento de la lista del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Devuelve el índice del elemento que contiene una cadena especificada.|  
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Devuelve un puntero al botón de cuadro combinado con un identificador de comando especificado.|  
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Devuelve un puntero para el control de cuadro combinado que está incrustado en el botón de cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Devuelve al número de elementos en el cuadro combinado de lista del cuadro.|  
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado. Devuelve al número de elementos en el cuadro combinado de lista del cuadro de ese botón.|  
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Devuelve el índice del elemento seleccionado en el cuadro combinado de lista del cuadro.|  
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado y devuelve el índice del elemento seleccionado en el cuadro combinado de lista del cuadro de ese botón.|  
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Devuelve un puntero para el control de edición que está incrustado en el botón de cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Devuelve la cadena que está asociada con un índice especificado en el cuadro combinado de lista del cuadro.|  
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado y devuelve la cadena que está asociada con un índice en la lista del cuadro combinado de ese botón.|  
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Devuelve el valor de 32 bits que está asociado con un índice especificado en el cuadro combinado de lista del cuadro.|  
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado y devuelve el valor de 32 bits que está asociado con un índice en la lista del cuadro combinado de ese botón.|  
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado. Recupera el valor de 32 bits que está asociado un índice en la lista del cuadro combinado de ese botón y devuelve un valor de 32 bits como un puntero.|  
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Devuelve el texto que contiene el control de edición del cuadro combinado.|  
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado y devuelve el texto del control de edición de ese botón.|  
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Determina si los botones del cuadro combinado en la aplicación se centrado o alineados con la parte superior de la barra de herramientas.|  
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro combinado en la aplicación tienen un aspecto sin relieve.|  
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Quita todos los elementos de la lista cuadro y control del cuadro combinado de edición.|  
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Selecciona un elemento en el cuadro combinado según su índice, el valor de 32 bits o la cadena y notifica al control de cuadro combinado acerca de la selección.|  
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Busca al cuadro combinado del botón de cuadro que tiene un identificador de comando especificado. Llamadas `SelectItem` para seleccionar un elemento en el cuadro combinado de ese botón según su cadena, un índice o un valor de 32 bits.|  
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Especifica si los botones del cuadro combinado en la aplicación se debe centrar verticalmente o alineados con la parte superior de la barra de herramientas.|  
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Establece el alto del cuadro de lista desplegable.|  
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Especifica si los botones del cuadro combinado en la aplicación tienen un aspecto sin relieve.|  
  
## <a name="remarks"></a>Comentarios  
 Para agregar un botón del cuadro combinado a una barra de herramientas, siga estos pasos:  
  
 1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.  
  
 2. Construir un `CMFCToolBarComboBoxButton` objeto.  
  
 3. En el controlador de mensajes que procesa el `AFX_WM_RESETTOOLBAR` de mensajes, reemplazar el botón ficticio con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).  
  
 Para obtener más información, consulte [Tutorial: poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md). Para obtener un ejemplo de un botón de barra de herramientas del cuadro combinado, vea el proyecto de ejemplo VisualStudioDemo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCToolBarComboBoxButton` clase. En el ejemplo se muestra cómo habilitar los cuadros de edición y combinado, establecer la posición vertical combinado de botones del cuadro de la aplicación, establezca la altura del cuadro de lista cuando se coloca, establecer el aspecto de estilo plano de botones del cuadro combinado en la aplicación y establecer el texto en el cuadro de edición del cuadro combinado del botón del cuadro. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)  
  
 [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtoolbarcomboboxbutton.h  
  
##  <a name="additem"></a>CMFCToolBarComboBoxButton::AddItem  
 Anexa un elemento único en el cuadro de lista.  
  
```  
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszItem`  
 El texto del elemento que se va a agregar al cuadro de lista.  
  
 [in] `dwData`  
 Los datos asociados con el elemento que se agrega al cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del último elemento en el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 No utilice este método cuando el estilo de cuadro de lista está ordenado.  
  
 Si el texto del elemento ya está en el cuadro de lista, los nuevos datos se almacenan con el elemento de trabajo. La búsqueda del elemento distingue entre mayúsculas y minúsculas.  
  
##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem  
 Agrega un elemento al cuadro de lista en el orden en que se define mediante la [comparar](#compare) método.  
  
```  
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,  
    DWORD_PTR dwData=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszItem`  
 El texto del elemento que se va a agregar al cuadro de lista.  
  
 [in] `dwData`  
 Los datos asociados con el elemento que se agrega al cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice del elemento que se ha agregado al cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para agregar elementos al cuadro de lista en un orden específico.  
  
##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched  
 Indica si se puede cambiar el tamaño del botón de cuadro combinado.  
  
```  
virtual BOOL CanBeStretched() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE`.  
  
##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton  
 Construye un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objeto.  
  
```  
CMFCToolBarComboBoxButton(
    UINT uiID,  
    int iImage,  
    DWORD dwStyle=CBS_DROPDOWNLIST,  
    int iWidth=0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 El identificador de comando del botón nuevo.  
  
 [in] `iImage`  
 El índice de imagen de la imagen asociada con el botón nuevo.  
  
 [in] `dwStyle`  
 El estilo del botón nuevo.  
  
 [in] `iWidth`  
 El ancho, en píxeles, del botón nuevo.  
  
### <a name="remarks"></a>Comentarios  
 El ancho predeterminado es 150 píxeles.  
  
 Para obtener una lista de estilos de botón de barra de herramientas Ver [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData  
 Elimina los datos definidos por el usuario.  
  
```  
virtual void ClearData();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método en una clase derivada si desea eliminar los datos definidos por el usuario.  
  
##  <a name="compare"></a>CMFCToolBarComboBoxButton::Compare  
 Compara dos cadenas.  
  
```  
virtual int Compare(
    LPCTSTR lpszItem1,  
    LPCTSTR lpszItem2);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszItem1`  
 Primera cadena que se va a comparar.  
  
 [in] `lpszItem2`  
 Segunda cadena que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indica la relación entre mayúsculas y minúsculas lexicográfica entre las cadenas. En la tabla siguiente se enumera los valores posibles:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|\<0|La primera cadena es menor que el segundo.|  
|0|La primera cadena es igual a la segunda.|  
|>0|La primera cadena es mayor que el segundo.|  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para cambiar cómo se ordenan los elementos en el cuadro de lista.  
  
 La comparación distingue entre mayúsculas y minúsculas.  
  
 Este método solo se llama desde el [AddSortedItem](#addsorteditem) método.  
  
##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom  
 Copia el estado del elemento especificado `CMFCToolBarComboBoxButton` al objeto actual.  
  
```  
virtual void CopyFrom(const CMFCToolBarButton& src);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `src`  
 Objeto `CMFCToolBarComboBoxButton` de origen.  
  
##  <a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo  
 Crea un nuevo cuadro combinado para el botón de cuadro combinado.  
  
```  
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Un puntero a la ventana primaria del botón.  
  
 [in] `rect`  
 Rectángulo delimitador del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al cuadro combinado nuevo si el método se realizó correctamente; en caso contrario, `NULL`.  
  
##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit  
 Crea un nuevo cuadro de edición para el botón de cuadro combinado.  
  
```  
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,  
    const CRect& rect,  
    DWORD dwEditStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Un puntero a la ventana primaria del botón.  
  
 [in] `rect`  
 Rectángulo delimitador del nuevo cuadro de edición.  
  
 [in] `dwEditStyle`  
 Estilo del control del cuadro de edición nueva.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al nuevo cuadro de edición si el método se realizó correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando crea un nuevo cuadro de edición para un botón del cuadro combinado. Invalide este método para cambiar cómo [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) se crea.  
  
##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem  
 Elimina un elemento especificado en el cuadro de lista.  
  
```  
BOOL DeleteItem(int iIndex);  
BOOL DeleteItem(DWORD_PTR dwData);  
  BOOL DeleteItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero del elemento que se va a eliminar.  
  
 [in] `dwData`  
 Los datos asociados con el elemento que se va a eliminar.  
  
 [in] `lpszText`  
 El texto del elemento que se va a eliminar. Si hay varios elementos con el mismo texto, se elimina el primer elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento se encuentra y se eliminó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData  
 Datos definidos por el usuario de duplicados.  
  
```  
virtual void DuplicateData();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada este método no hace nada. Invalide este método en una clase derivada si van a copiar los datos definidos por el usuario.  
  
##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow  
 Habilita o deshabilita los cuadros de edición y combinado.  
  
```  
virtual void EnableWindow(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar los cuadros de edición y combinados; `FALSE` para deshabilitar los cuadros de edición y combinado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando está deshabilitado, los controles no se activan y no pueden aceptar la entrada del usuario.  
  
##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton  
 Identificador de una cadena a partir de la tabla de cadenas de la aplicación en el menú especificado con el comando de botón de cuadro combinado de copias.  
  
```  
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `menuButton`  
 Referencia a un botón de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem  
 Devuelve el índice del primer elemento en el cuadro de lista que contiene una cadena especificada.  
  
```  
int FindItem(LPCTSTR lpszText) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 El texto que se busca en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento; o `CB_ERR` si no se encuentra el elemento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd  
 Obtiene un puntero al botón de cuadro combinado que tiene un identificador de comando especificado.  
  
```  
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,  
    BOOL bIsFocus=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón del cuadro combinado.  
  
 [in] `bIsFocus`  
 `TRUE`para buscar sólo centrado botones; `FALSE` para buscar todos los botones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un botón del cuadro combinado; o `NULL` si no se encuentra el botón.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox  
 Devuelve un puntero al cuadro combinado en el cuadro combinado del botón del cuadro.  
  
```  
CComboBox* GetComboBox() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CComboBox (clase)](../../mfc/reference/ccombobox-class.md) objeto si el método es correcto; en caso contrario `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID  
 Obtiene el identificador de recurso de menú contextual para el botón de cuadro combinado.  
  
```  
UINT GetContextMenuID();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de recurso de menú contextual.  
  
##  <a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount  
 Devuelve el número de elementos en el cuadro de lista.  
  
```  
INT_PTR GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll  
 Obtiene el número de elementos en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.  
  
```  
static int GetCountAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el cuadro de lista; en caso contrario, `CB_ERR` si no se encuentra el botón del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel  
 Obtiene el índice del elemento actualmente seleccionado en el cuadro de lista.  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento actualmente seleccionado en el cuadro de lista; o `CB_ERR` si se selecciona ningún elemento.  
  
### <a name="remarks"></a>Comentarios  
 El índice del cuadro de lista está basado en cero.  
  
##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll  
 Devuelve el índice del elemento actualmente seleccionado en el cuadro de lista de un combinado botón del cuadro que tiene un identificador de comando especificado.  
  
```  
static int GetCurSelAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento actualmente seleccionado en el cuadro de lista; en caso contrario, `CB_ERR` si se selecciona ningún elemento o no se encuentra un botón del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 El índice del cuadro de lista está basado en cero.  
  
##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl  
 Devuelve un puntero al cuadro de edición en el cuadro combinado del botón del cuadro.  
  
```  
virtual CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al cuadro de edición si el método se realizó correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd  
 Devuelve el identificador de ventana para el cuadro combinado.  
  
```  
virtual HWND GetHwnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de ventana o `NULL` si el cuadro combinado no está asociado a un objeto de ventana.  
  
##  <a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem  
 Devuelve la cadena asociada a un elemento en el índice especificado en el cuadro de lista.  
  
```  
LPCTSTR GetItem(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la cadena que está asociado con el elemento; en caso contrario, `NULL` si el parámetro de índice no es válido, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Un parámetro de índice de -1 devuelve la cadena del elemento que está seleccionado actualmente.  
  
##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll  
 Devuelve la cadena asociada a un elemento en el índice especificado en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.  
  
```  
static LPCTSTR GetItemAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón del cuadro combinado.  
  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la cadena del elemento si el método se realizó correctamente; en caso contrario, `NULL` si el índice no es válido, no es un botón del cuadro combinado se encuentra, o si el índice es -1 y no hay ningún elemento seleccionado en el cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Un valor de índice de -1 devuelve la cadena del elemento que está seleccionado actualmente.  
  
##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData  
 Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista.  
  
```  
DWORD_PTR GetItemData(int iIndex=-1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos asociados con el elemento; o bien 0 si el elemento no existe.  
  
### <a name="remarks"></a>Comentarios  
 Un parámetro de índice de -1 devuelve los datos asociados con el elemento actualmente seleccionado.  
  
##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll  
 Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando concreto.  
  
```  
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón del cuadro combinado.  
  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Los datos asociados con el elemento si el método se realizó correctamente; en caso contrario, 0 si el índice especificado no es válido o no se encuentra CB_ERR si el cuadro combinado del cuadro de botón.  
  
### <a name="remarks"></a>Comentarios  
 Un parámetro de índice de -1 devuelve los datos asociados con el elemento actualmente seleccionado.  
  
##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll  
 Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando concreto. Estos datos se devuelven como un puntero.  
  
```  
static void* GetItemDataPtrAll(
    UINT uiCmd,  
    int iIndex=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón de cuadro combinado.  
  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero asociado con el elemento si el método se realizó correctamente; en caso contrario, -1 si se produce un error, o `NULL` si no se encuentra el botón del cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt  
 Devuelve la cadena de mensaje para el cuadro combinado del botón del cuadro.  
  
```  
virtual CString GetPrompt() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La cadena del mensaje.  
  
### <a name="remarks"></a>Comentarios  
 Este método no está implementado actualmente.  
  
##  <a name="gettext"></a>CMFCToolBarComboBoxButton::GetText  
 Obtiene el texto en el cuadro de edición.  
  
```  
LPCTSTR GetText() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto en el cuadro de edición.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll  
 Obtiene el texto en el cuadro de edición de un botón de cuadro combinado que tiene un identificador de comando especificado.  
  
```  
static LPCTSTR GetTextAll(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de un botón de cuadro combinado específico.  
  
### <a name="return-value"></a>Valor devuelto  
 El texto en el cuadro de edición si el método se realizó correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus  
 Indica si el cuadro combinado tiene actualmente el foco.  
  
```  
virtual BOOL HasFocus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el cuadro combinado tiene actualmente el foco; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método también devuelve `TRUE` si cualquier ventana secundaria de un cuadro combinado tiene actualmente el foco.  
  
##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert  
 Devuelve la posición vertical de botones del cuadro combinado en la aplicación.  
  
```  
static BOOL IsCenterVert();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los botones se centran; `FALSE` si se alinean los botones en la parte superior.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode  
 Devuelve la apariencia de estilo plano de botones del cuadro combinado de la aplicación.  
  
```  
static BOOL IsFlatMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si los botones tienen un estilo plano; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Es el estilo plano predeterminado de botones del cuadro combinado`FALSE.`  
  
##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf  
 Indica si el identificador especificado está asociado con el botón del cuadro combinado, o uno de sus elementos secundarios.  
  
```  
virtual BOOL IsOwnerOf(HWND hwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hwnd`  
 Un identificador de ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el identificador está asociado con el botón del cuadro combinado, o uno de sus elementos secundarios; en caso contrario, `FALSE`.  
  
##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton  
 Indica si el botón de cuadro combinado reside en un panel de cinta de opciones.  
  
```  
BOOL IsRibbonButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método devuelve siempre `FALSE`, lo que no significa que el cuadro combinado del botón del cuadro nunca se muestra en un panel de cinta de opciones.  
  
##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible  
 Devuelve el estado de visibilidad del cuadro combinado del botón del cuadro.  
  
```  
virtual BOOL IsWindowVisible();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado de visibilidad del botón de cuadro combinado.  
  
##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand  
 Indica si el botón de cuadro combinado procesa el mensaje.  
  
```  
virtual BOOL NotifyCommand(int iNotifyCode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iNotifyCode`  
 El mensaje de notificación que está asociado con el comando.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el botón de cuadro combinado procesa el mensaje.  
  
##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage  
 Lo llama el marco cuando el botón se agrega a la **personalizar** cuadro de diálogo.  
  
```  
virtual void OnAddToCustomizePage();
```  
  
##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize  
 Lo llama el marco de trabajo para calcular el tamaño del botón.  
  
```  
virtual SIZE OnCalculateSize(
    CDC* pDC,  
    const CSize& sizeDefault,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo que muestra el botón de cuadro combinado.  
  
 [in] `sizeDefault`  
 El tamaño predeterminado del botón de cuadro combinado.  
  
 [in] `bHorz`  
 El estado de acoplamiento de la barra de herramientas primario. `TRUE`Cuando la barra de herramientas está acoplado horizontalmente y `FALSE` cuando se acopla la barra de herramientas verticalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `SIZE` estructura que contiene las dimensiones del botón de cuadro combinado, en píxeles.  
  
##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd  
 Lo llama el marco cuando el botón de cuadro combinado se inserta en una nueva barra de herramientas.  
  
```  
virtual void OnChangeParentWnd(CWnd* pWndParent);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Puntero a la nueva barra de herramientas primario.  
  
##  <a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick  
 Lo llama el marco cuando el usuario hace clic en el botón de cuadro combinado.  
  
```  
virtual BOOL OnClick(
    CWnd* pWnd,  
    BOOL bDelay = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana principal del botón de cuadro combinado.  
  
 [in] `bDelay`  
 Reservado para uso en una clase derivada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método controla el evento; en caso contrario, `FALSE`.  
  
##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor  
 Lo llama el marco cuando el usuario cambia el color de la barra de herramientas principal para establecer al cuadro combinado del color del botón de cuadro.  
  
```  
virtual HBRUSH OnCtlColor(
    CDC* pDC,  
    UINT nCtlColor);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo que muestra el botón de cuadro combinado.  
  
 [in] `nCtlColor`  
 Sin usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del pincel que el marco de trabajo que se usa para pintar el fondo del botón de cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Este método también establece el color de texto del botón de cuadro combinado.  
  
##  <a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw  
 Lo llama el marco de trabajo para dibujar el botón de cuadro combinado con los estilos especificados y las opciones.  
  
```  
virtual void OnDraw(
    CDC* pDC,  
    const CRect& rect,  
    CMFCToolBarImages* pImages,  
    BOOL bHorz = TRUE,  
    BOOL bCustomizeMode = FALSE,  
    BOOL bHighlight = FALSE,  
    BOOL bDrawBorder = TRUE,  
    BOOL bGrayDisabledButtons = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Pdc`  
 El contexto de dispositivo que muestra el botón.  
  
 [in] `rect`  
 El rectángulo delimitador del botón.  
  
 [in] `pImages`  
 La colección de imágenes que está asociada con el botón.  
  
 [in] `bHorz`  
 El estado de acoplamiento de la barra de herramientas primario. `TRUE`Cuando la barra de herramientas está acoplado horizontalmente y `FALSE` cuando se acopla la barra de herramientas verticalmente.  
  
 [in] `bCustomizeMode`  
 Si la aplicación está en modo de personalización.  
  
 [in] `bHighlight`  
 Si se va a dibujar el botón de cuadro combinado resaltado.  
  
 [in] `bDrawBorder`  
 Si se va a dibujar el botón de cuadro combinado con un borde.  
  
 [in] `bGrayDisabledButtons`  
 `TRUE`para dibujar los botones deshabilitados sombreados; `FALSE` usar el deshabilitado imágenes de colección.  
  
##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList  
 Lo llama el marco para dibujar el botón de cuadro combinado el **comandos** panel de la **personalizar** cuadro de diálogo.  
  
```  
virtual int OnDrawOnCustomizeList(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo que muestra el botón de cuadro combinado.  
  
 [in] `rect`  
 El rectángulo delimitador del botón de cuadro combinado.  
  
 [in] `bSelected`  
 `TRUE`Si el cuadro combinado del cuadro botón está seleccionado; en caso contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho, en píxeles, del botón de cuadro combinado.  
  
##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged  
 Lo llama el marco para establecer al cuadro combinado de fuente del cuadro de botón cuando cambia la fuente de la aplicación.  
  
```  
virtual void OnGlobalFontsChanged();
```  
  
##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove  
 Lo llama el marco de trabajo para cambiar la ubicación del botón de cuadro combinado cuando se mueve la barra de herramientas primario.  
  
```  
virtual void OnMove();
```  
  
##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow  
 Lo llama el marco de trabajo cuando se oculta o se muestra el botón de cuadro combinado.  
  
```  
virtual void OnShow(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 Si desea ocultar o mostrar el botón de cuadro combinado.  
  
##  <a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize  
 Lo llama el marco para cambiar el tamaño del botón de cuadro combinado cuando la barra de herramientas primario cambia de tamaño.  
  
```  
virtual void OnSize(int iSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iSize`  
 El nuevo ancho del botón de cuadro combinado.  
  
##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip  
 Lo llama el marco cuando el usuario cambia la información sobre herramientas para el botón de cuadro combinado.  
  
```  
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,  
    int iButtonIndex,  
    CToolTipCtrl& wndToolTip,  
    CString& str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 Puntero a la ventana primaria para el botón de cuadro combinado.  
  
 [in] `iButtonIndex`  
 Id. del botón de cuadro combinado.  
  
 [in] `wndToolTip`  
 La información sobre las herramientas para asociar con el botón de cuadro combinado.  
  
 [in] `str`  
 El texto de información sobre herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método controla el evento; en caso contrario, `FALSE`.  
  
##  <a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems  
 Elimina todos los elementos de los cuadros de lista y edición.  
  
```  
void RemoveAllItems();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita todos los elementos de la lista cuadro y control de un cuadro combinado de edición.  
  
##  <a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem  
 Selecciona un elemento en el cuadro de lista.  
  
```  
BOOL SelectItem(
    int iIndex,  
    BOOL bNotify=TRUE);  
  
BOOL SelectItem(DWORD_PTR dwData);  
BOOL SelectItem(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento en el cuadro de lista.  
  
 [in] `bNotify`  
 `TRUE`para notificar el botón del cuadro combinado de la selección; en caso contrario, `FALSE`.  
  
 [in] `dwData`  
 Los datos asociados a un elemento en el cuadro de lista.  
  
 [in] `lpszText`  
 El texto de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll  
 Selecciona un elemento en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.  
  
```  
static BOOL SelectItemAll(
    UINT uiCmd,  
    int iIndex);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    DWORD_PTR dwData);

 
static BOOL SelectItemAll(
    UINT uiCmd,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando del botón de cuadro combinado que contiene el cuadro de lista.  
  
 [in] `iIndex`  
 Índice de base cero del elemento en el cuadro de lista. Un valor de -1 quita cualquier selección actual en el cuadro de lista y borra el cuadro de edición.  
  
 [in] `dwData`  
 Los datos de un elemento en el cuadro de lista.  
  
 [in] `lpszText`  
 El texto de un elemento en el cuadro de lista.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize  
 Lee este objeto desde un archivo o lo escribe en un archivo.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `ar`  
 La `CArchive` objeto que se va a serializar.  
  
### <a name="remarks"></a>Comentarios  
 Configuración de la `CArchive` objeto determinar si este método lee o escribe en el archivo.  
  
##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData  
 Rellena especificado `CAccessibilityData` objeto mediante el uso de datos de accesibilidad en el botón de cuadro combinado.  
  
```  
virtual BOOL SetACCData(
    CWnd* pParent,  
    CAccessibilityData& data);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParent`  
 La ventana principal del botón de cuadro combinado.  
  
 [out] `data`  
 Un `CAccessibilityData` objeto que recibe los datos de accesibilidad en el botón de cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; en caso contrario, `FALSE`.  
  
##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert  
 Establece la posición vertical de botones del cuadro combinado en la aplicación.  
  
```  
static void SetCenterVert(BOOL bCenterVert=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bCenterVert`  
 `TRUE`Para centrar el botón del cuadro combinado en la barra de herramientas; `FALSE` para alinear el botón del cuadro combinado a la parte superior de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones del cuadro combinado se alinean a la parte superior.  
  
##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID  
 Establece el identificador de recurso de menú contextual para el cuadro combinado del botón del cuadro.  
  
```  
void SetContextMenuID(UINT uiResID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResID`  
 El identificador de recurso de menú contextual.  
  
##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight  
 Establece el alto del cuadro de lista cuando se coloca hacia abajo.  
  
```  
void SetDropDownHeight(int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHeight`  
 El alto, en píxeles, del cuadro de lista.  
  
### <a name="remarks"></a>Comentarios  
 El alto predeterminado es 150 píxeles.  
  
##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode  
 Establece la apariencia de estilo plano de botones del cuadro combinado en la aplicación.  
  
```  
static void SetFlatMode(BOOL bFlat=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bFlat`  
 `TRUE`para una apariencia de estilo plano; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El estilo plano predeterminado para los botones del cuadro combinado es `FALSE`.  
  
##  <a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle  
 Establece el estilo especificado para el cuadro combinado del botón del cuadro y vuelve a dibujarse el control si no se deshabilita.  
  
```  
virtual void SetStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nStyle`  
 Una combinación bit a bit (OR) de los estilos de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una lista de estilos de botón de barra de herramientas Ver [estilos de Control de barra de herramientas](../../mfc/reference/toolbar-control-styles.md)  
  
##  <a name="settext"></a>CMFCToolBarComboBoxButton::SetText  
 Establece el texto en el cuadro de edición del cuadro combinado del botón del cuadro.  
  
```  
void SetText(LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszText`  
 Puntero a una cadena que contiene el texto para el cuadro de edición.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)   
 [Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)



