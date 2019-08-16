---
title: Clase CMFCToolBarComboBoxButton
ms.date: 11/04/2016
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
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915970"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Clase CMFCToolBarComboBoxButton

Un botón de la barra de herramientas que contiene un control de cuadro combinado ( [clase CComboBox](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Construye un objeto `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Agrega un elemento al final de la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Agrega un elemento a la lista de cuadros combinados. Especifica el orden de los elementos de la lista `Compare`.|
|[CMFCToolBarComboBoxButton::Compare](#compare)|Compara dos elementos. Se llama para ordenar los `AddSortedItems` elementos que se agregan a la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición para el botón de cuadro combinado.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Elimina un elemento de la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Devuelve el índice del elemento que contiene una cadena especificada.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Devuelve un puntero al botón del cuadro combinado con un identificador de comando especificado.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Devuelve un puntero al control de cuadro combinado que está incrustado en el botón del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Devuelve el número de elementos de la lista del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Devuelve el número de elementos de la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Devuelve el índice del elemento seleccionado en la lista del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el índice del elemento seleccionado en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Devuelve un puntero al control de edición que está incrustado en el botón del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Devuelve la cadena que está asociada a un índice especificado en la lista del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve la cadena asociada a un índice en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Devuelve el valor de 32 bits que está asociado a un índice especificado en la lista del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el valor de 32 bits que está asociado a un índice en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Recupera el valor de 32 bits que está asociado a un índice en la lista de cuadros combinados de ese botón y devuelve el valor de 32 bits como un puntero.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Devuelve el texto del control de edición del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el texto del control de edición de ese botón.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Determina si los botones de cuadro combinado de la aplicación están centrados o alineados con la parte superior de la barra de herramientas.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Determina si los botones de cuadro combinado de la aplicación tienen una apariencia plana.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Quita todos los elementos del cuadro de lista y el control de edición del cuadro combinado.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Selecciona un elemento del cuadro combinado según su índice, valor de 32 bits o cadena y notifica al control de cuadro combinado la selección.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Llama `SelectItem` a para seleccionar un elemento del cuadro combinado de ese botón en función de su valor de cadena, índice o 32 bits.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Especifica si los botones de cuadro combinado de la aplicación se centran verticalmente o se alinean con la parte superior de la barra de herramientas.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Establece el alto del cuadro de lista desplegable.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Especifica si los botones de cuadro combinado de la aplicación tienen una apariencia plana.|

## <a name="remarks"></a>Comentarios

Para agregar un botón de cuadro combinado a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Construya un `CMFCToolBarComboBoxButton` objeto.

3. En el controlador de mensajes que procesa el mensaje AFX_WM_RESETTOOLBAR, reemplace el botón ficticio por el botón nuevo cuadro combinado con [CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información, vea [Tutorial: Colocar controles en las barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas. Para obtener un ejemplo de un botón de barra de herramientas de cuadro combinado, vea el proyecto de ejemplo VisualStudioDemo.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarComboBoxButton` . En el ejemplo se muestra cómo habilitar los cuadros de edición y de combinación, establecer la posición vertical de los botones del cuadro combinado en la aplicación, establecer el alto del cuadro de lista cuando se suelta, establecer la apariencia de estilo plano de los botones del cuadro combinado en la aplicación. y establezca el texto en el cuadro de edición del botón de cuadro combinado. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarcomboboxbutton. h

##  <a name="additem"></a>  CMFCToolBarComboBoxButton::AddItem

Anexa un elemento único al cuadro de lista.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
de Texto del elemento que se va a agregar al cuadro de lista.

*dwData*<br/>
de Los datos asociados al elemento que se va a agregar al cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Índice del último elemento del cuadro de lista.

### <a name="remarks"></a>Comentarios

No utilice este método cuando el estilo de cuadro de lista esté ordenado.

Si el texto del elemento ya está en el cuadro de lista, los nuevos datos se almacenan con el elemento existente. La búsqueda del elemento distingue entre mayúsculas y minúsculas.

##  <a name="addsorteditem"></a>  CMFCToolBarComboBoxButton::AddSortedItem

Agrega un elemento al cuadro de lista en el orden definido por el método [Compare](#compare) .

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
de Texto del elemento que se va a agregar al cuadro de lista.

*dwData*<br/>
de Los datos asociados al elemento que se va a agregar al cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Índice del elemento que se ha agregado al cuadro de lista.

### <a name="remarks"></a>Comentarios

Utilice esta función para agregar elementos al cuadro de lista en un orden específico.

##  <a name="canbestretched"></a>  CMFCToolBarComboBoxButton::CanBeStretched

Indica si el tamaño del botón de cuadro combinado puede cambiar.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE.

##  <a name="cmfctoolbarcomboboxbutton"></a>  CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Construye un objeto [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
de IDENTIFICADOR de comando del botón nuevo.

*iImage*<br/>
de Índice de imagen de la imagen asociada al botón nuevo.

*dwStyle*<br/>
de Estilo del nuevo botón.

*iWidth*<br/>
de Ancho, en píxeles, del botón nuevo.

### <a name="remarks"></a>Comentarios

El ancho predeterminado es 150 píxeles.

Para obtener una lista de estilos de botón de la barra de herramientas, vea [estilos de control Toolbar](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>  CMFCToolBarComboBoxButton::ClearData

Elimina los datos definidos por el usuario.

```
virtual void ClearData();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada. Invalide este método en una clase derivada si desea eliminar los datos definidos por el usuario.

##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare

Compara dos cadenas.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parámetros

*lpszItem1*<br/>
de Primera cadena que se va a comparar.

*lpszItem2*<br/>
de Segunda cadena que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Valor que indica la relación de lexicográfico que distingue entre mayúsculas y minúsculas entre las cadenas. En la tabla siguiente se enumeran los valores posibles:

|Valor|DESCRIPCIÓN|
|-----------|-----------------|
|\<0|La primera cadena es menor que la segunda.|
|0|La primera cadena es igual a la segunda.|
|>0|La primera cadena es mayor que la segunda.|

### <a name="remarks"></a>Comentarios

Invalide este método para cambiar la forma en que los elementos se ordenan en el cuadro de lista.

La comparación distingue entre mayúsculas y minúsculas.

Solo se llama a este método desde el método [AddSortedItem](#addsorteditem) .

##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom

Copia el estado de la especificada `CMFCToolBarComboBoxButton` en el objeto actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
de Objeto de `CMFCToolBarComboBoxButton` origen.

##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo

Crea un nuevo cuadro combinado para el botón de cuadro combinado.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria del botón.

*rect*<br/>
de Rectángulo delimitador del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo cuadro combinado si el método se realizó correctamente; de lo contrario, es NULL.

##  <a name="createedit"></a>  CMFCToolBarComboBoxButton::CreateEdit

Crea un nuevo cuadro de edición para el botón de cuadro combinado.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria del botón.

*rect*<br/>
de Rectángulo delimitador del nuevo cuadro de edición.

*dwEditStyle*<br/>
de Estilo de control del nuevo cuadro de edición.

### <a name="return-value"></a>Valor devuelto

Puntero al nuevo cuadro de edición si el método se realizó correctamente; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando crea un nuevo cuadro de edición para un botón de cuadro combinado. Invalide este método para cambiar el modo en que se crea [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) .

##  <a name="deleteitem"></a>  CMFCToolBarComboBoxButton::DeleteItem

Elimina un elemento especificado del cuadro de lista.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero del elemento que se va a eliminar.

*dwData*<br/>
de Los datos asociados al elemento que se va a eliminar.

*lpszText*<br/>
de Texto del elemento que se va a eliminar. Si hay varios elementos con el mismo texto, se elimina el primer elemento.

### <a name="return-value"></a>Valor devuelto

TRUE si el elemento se encontró y eliminó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

Duplica los datos definidos por el usuario.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método no hace nada. Invalide este método en una clase derivada si desea copiar los datos definidos por el usuario.

##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow

Habilita o deshabilita los cuadros de edición y de combinación.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para habilitar los cuadros de edición y combinados; FALSE para deshabilitar los cuadros de edición y combinados.

### <a name="remarks"></a>Comentarios

Cuando está deshabilitado, los controles no pueden activarse y no pueden aceptar datos proporcionados por el usuario.

##  <a name="exporttomenubutton"></a>  CMFCToolBarComboBoxButton::ExportToMenuButton

Copia una cadena de la tabla de cadenas de aplicación en el menú especificado mediante el identificador de comando del botón de cuadro combinado.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
enuncia Referencia a un botón de menú.

### <a name="return-value"></a>Valor devuelto

Siempre es TRUE.

##  <a name="finditem"></a>  CMFCToolBarComboBoxButton::FindItem

Devuelve el índice del primer elemento del cuadro de lista que contiene una cadena especificada.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
de Texto que se va a buscar en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Índice del elemento; o CB_ERR si no se encuentra el elemento.

### <a name="remarks"></a>Comentarios

##  <a name="getbycmd"></a>  CMFCToolBarComboBoxButton::GetByCmd

Obtiene un puntero al botón del cuadro combinado que tiene un identificador de comando especificado.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado.

*bIsFocus*<br/>
de TRUE para buscar solo los botones centrados; FALSE para buscar en todos los botones.

### <a name="return-value"></a>Valor devuelto

Un puntero a un botón de cuadro combinado; o NULL si no se encuentra el botón.

### <a name="remarks"></a>Comentarios

##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox

Devuelve un puntero al cuadro combinado en el botón del cuadro combinado.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto de la [clase CComboBox](../../mfc/reference/ccombobox-class.md) si el método se realizó correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

##  <a name="getcontextmenuid"></a>  CMFCToolBarComboBoxButton::GetContextMenuID

Obtiene el identificador de recurso del menú contextual para el botón de cuadro combinado.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valor devuelto

IDENTIFICADOR de recurso del menú contextual.

##  <a name="getcount"></a>  CMFCToolBarComboBoxButton::GetCount

Devuelve el número de elementos del cuadro de lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del cuadro de lista.

### <a name="remarks"></a>Comentarios

##  <a name="getcountall"></a>  CMFCToolBarComboBoxButton::GetCountAll

Obtiene el número de elementos del cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Número de elementos del cuadro de lista; de lo contrario, CB_ERR si no se encuentra el botón del cuadro combinado.

### <a name="remarks"></a>Comentarios

##  <a name="getcursel"></a>  CMFCToolBarComboBoxButton::GetCurSel

Obtiene el índice del elemento actualmente seleccionado en el cuadro de lista.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

Índice del elemento seleccionado actualmente en el cuadro de lista; o CB_ERR si no hay ningún elemento seleccionado.

### <a name="remarks"></a>Comentarios

El índice del cuadro de lista está basado en cero.

##  <a name="getcurselall"></a>  CMFCToolBarComboBoxButton::GetCurSelAll

Devuelve el índice del elemento seleccionado actualmente en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Índice del elemento seleccionado actualmente en el cuadro de lista; de lo contrario, CB_ERR si no hay ningún elemento seleccionado o no se encuentra ningún botón de cuadro combinado.

### <a name="remarks"></a>Comentarios

El índice del cuadro de lista está basado en cero.

##  <a name="geteditctrl"></a>  CMFCToolBarComboBoxButton::GetEditCtrl

Devuelve un puntero al cuadro de edición en el botón del cuadro combinado.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valor devuelto

Puntero al cuadro de edición si el método se realizó correctamente; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

##  <a name="gethwnd"></a>  CMFCToolBarComboBoxButton::GetHwnd

Devuelve el identificador de ventana para el cuadro combinado.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

Identificador de ventana, o NULL si el cuadro combinado no está asociado a un objeto de ventana.

##  <a name="getitem"></a>  CMFCToolBarComboBoxButton::GetItem

Devuelve la cadena asociada a un elemento en el índice especificado del cuadro de lista.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Puntero a la cadena asociada al elemento. de lo contrario, es NULL si el parámetro de índice no es válido o si el parámetro de índice es-1 y no hay ningún elemento seleccionado en el cuadro combinado.

### <a name="remarks"></a>Comentarios

Un parámetro de índice de-1 devuelve la cadena del elemento seleccionado actualmente.

##  <a name="getitemall"></a>  CMFCToolBarComboBoxButton::GetItemAll

Devuelve la cadena asociada a un elemento en un índice especificado en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado.

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Un puntero a la cadena del elemento si el método se realizó correctamente; de lo contrario, es NULL si el índice no es válido, no se encuentra un botón de cuadro combinado o si el índice es-1 y no hay ningún elemento seleccionado en el cuadro combinado.

### <a name="remarks"></a>Comentarios

Un valor de índice de-1 devuelve la cadena del elemento seleccionado actualmente.

##  <a name="getitemdata"></a>  CMFCToolBarComboBoxButton::GetItemData

Devuelve los datos asociados a un elemento en un índice específico del cuadro de lista.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Los datos asociados al elemento; o 0 si el elemento no existe.

### <a name="remarks"></a>Comentarios

Un parámetro de índice de-1 devuelve los datos asociados al elemento actualmente seleccionado.

##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll

Devuelve los datos asociados a un elemento en un índice específico del cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando específico.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado.

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Los datos asociados al elemento si el método se realizó correctamente; de lo contrario, es 0 si el índice especificado no es válido, o CB_ERR si no se encuentra el botón del cuadro combinado.

### <a name="remarks"></a>Comentarios

Un parámetro de índice de-1 devuelve los datos asociados al elemento actualmente seleccionado.

##  <a name="getitemdataptrall"></a>  CMFCToolBarComboBoxButton::GetItemDataPtrAll

Devuelve los datos asociados a un elemento en un índice específico del cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando específico. Estos datos se devuelven como un puntero.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando del botón de cuadro combinado.

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Puntero asociado al elemento si el método se realizó correctamente; de lo contrario,-1 si se produce un error, o NULL si no se encuentra el botón del cuadro combinado.

### <a name="remarks"></a>Comentarios

##  <a name="getprompt"></a>  CMFCToolBarComboBoxButton::GetPrompt

Devuelve la cadena de mensaje para el botón de cuadro combinado.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena de solicitud.

### <a name="remarks"></a>Comentarios

Este método no está implementado actualmente.

##  <a name="gettext"></a>  CMFCToolBarComboBoxButton::GetText

Obtiene el texto del cuadro de edición.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Valor devuelto

Texto del cuadro de edición.

### <a name="remarks"></a>Comentarios

##  <a name="gettextall"></a>  CMFCToolBarComboBoxButton::GetTextAll

Obtiene el texto del cuadro de edición de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
de IDENTIFICADOR de comando de un botón de cuadro combinado específico.

### <a name="return-value"></a>Valor devuelto

Texto del cuadro de edición si el método se realizó correctamente; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

##  <a name="hasfocus"></a>  CMFCToolBarComboBoxButton::HasFocus

Indica si el cuadro combinado tiene actualmente el foco.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el cuadro combinado tiene actualmente el foco; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método también devuelve TRUE si cualquier ventana secundaria del cuadro combinado tiene actualmente el foco.

##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert

Devuelve la posición vertical de los botones de cuadro combinado en la aplicación.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Valor devuelto

TRUE si los botones están centrados; FALSE si los botones están alineados en la parte superior.

### <a name="remarks"></a>Comentarios

##  <a name="isflatmode"></a>  CMFCToolBarComboBoxButton::IsFlatMode

Devuelve la apariencia de estilo plano de los botones de cuadro combinado en la aplicación.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Valor devuelto

TRUE si los botones tienen un estilo plano; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El estilo plano predeterminado de los botones del cuadro combinado es FALSE.

##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf

Indica si el identificador especificado está asociado al botón de cuadro combinado o a uno de sus elementos secundarios.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
de Identificador de ventana.

### <a name="return-value"></a>Valor devuelto

TRUE si el identificador es asociadas con el botón de cuadro combinado o uno de sus elementos secundarios; en caso contrario, FALSE.

##  <a name="isribbonbutton"></a>  CMFCToolBarComboBoxButton::IsRibbonButton

Indica si el botón del cuadro combinado reside en un panel de la cinta de opciones.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre es FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método siempre devuelve FALSE, lo que significa que el botón de cuadro combinado nunca se muestra en un panel de la cinta.

##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible

Devuelve el estado de visibilidad del botón del cuadro combinado.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Valor devuelto

Estado de visibilidad del botón del cuadro combinado.

##  <a name="notifycommand"></a>  CMFCToolBarComboBoxButton::NotifyCommand

Indica si el botón de cuadro combinado procesa el mensaje.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
de Mensaje de notificación asociado al comando.

### <a name="return-value"></a>Valor devuelto

Si el botón de cuadro combinado procesa el mensaje.

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarComboBoxButton::OnAddToCustomizePage

Lo llama el marco de trabajo cuando el botón se agrega al cuadro de diálogo **personalizar** .

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize

Lo llama el marco de trabajo para calcular el tamaño del botón.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de El contexto de dispositivo que muestra el botón de cuadro combinado.

*sizeDefault*<br/>
de Tamaño predeterminado del botón del cuadro combinado.

*bHorz*<br/>
de Estado de acoplamiento de la barra de herramientas primaria. TRUE cuando la barra de herramientas está acoplada horizontalmente y FALSE cuando la barra de herramientas está acoplada verticalmente.

### <a name="return-value"></a>Valor devuelto

`SIZE` Estructura que contiene las dimensiones del botón de cuadro combinado, en píxeles.

##  <a name="onchangeparentwnd"></a>  CMFCToolBarComboBoxButton::OnChangeParentWnd

Lo llama el marco de trabajo cuando el botón del cuadro combinado se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la nueva barra de herramientas principal.

##  <a name="onclick"></a>  CMFCToolBarComboBoxButton::OnClick

Lo llama el marco de trabajo cuando el usuario hace clic en el botón del cuadro combinado.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Puntero a la ventana primaria del botón de cuadro combinado.

*bDelay*<br/>
de Reservado para su uso en una clase derivada.

### <a name="return-value"></a>Valor devuelto

TRUE si el método controla el evento; en caso contrario, FALSE.

##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor

Lo llama el marco de trabajo cuando el usuario cambia el color de la barra de herramientas primaria para establecer el color del botón del cuadro combinado.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de El contexto de dispositivo que muestra el botón de cuadro combinado.

*nCtlColor*<br/>
de Sin usar.

### <a name="return-value"></a>Valor devuelto

Identificador del pincel que el marco de trabajo usa para pintar el fondo del botón de cuadro combinado.

### <a name="remarks"></a>Comentarios

Este método también establece el color del texto del botón de cuadro combinado.

##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw

Lo llama el marco de trabajo para dibujar el botón de cuadro combinado usando los estilos y las opciones especificados.

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

*Pdc*<br/>
de Contexto de dispositivo que muestra el botón.

*rect*<br/>
de Rectángulo delimitador del botón.

*pImages*<br/>
de Colección de imágenes que está asociada al botón.

*bHorz*<br/>
de Estado de acoplamiento de la barra de herramientas primaria. TRUE cuando la barra de herramientas está acoplada horizontalmente y FALSE cuando la barra de herramientas está acoplada verticalmente.

*bCustomizeMode*<br/>
de Indica si la aplicación está en modo de personalización.

*bHighlight*<br/>
de Indica si se va a dibujar el botón de cuadro combinado resaltado.

*bDrawBorder*<br/>
de Indica si se va a dibujar el botón de cuadro combinado con un borde.

*bGrayDisabledButtons*<br/>
de TRUE para dibujar botones deshabilitados sombreados; FALSE para usar la colección de imágenes deshabilitadas.

##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Lo llama el marco de trabajo para dibujar el botón de cuadro combinado en el panel **comandos** del cuadro de diálogo **personalizar** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
de El contexto de dispositivo que muestra el botón de cuadro combinado.

*rect*<br/>
de Rectángulo delimitador del botón del cuadro combinado.

*bSelected*<br/>
de TRUE si el botón del cuadro combinado está seleccionado; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Ancho, en píxeles, del botón del cuadro combinado.

##  <a name="onglobalfontschanged"></a>  CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Lo llama el marco de trabajo para establecer la fuente del botón del cuadro combinado cuando cambia la fuente de la aplicación.

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>  CMFCToolBarComboBoxButton::OnMove

Lo llama el marco de trabajo para cambiar la ubicación del botón del cuadro combinado cuando se mueve la barra de herramientas primaria.

```
virtual void OnMove();
```

##  <a name="onshow"></a>  CMFCToolBarComboBoxButton::OnShow

Lo llama el marco de trabajo cuando se oculta o se muestra el botón del cuadro combinado.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bShow*<br/>
de Indica si se va a ocultar o mostrar el botón de cuadro combinado.

##  <a name="onsize"></a>  CMFCToolBarComboBoxButton::OnSize

Lo llama el marco de trabajo para cambiar el tamaño del botón del cuadro combinado cuando cambia el tamaño de la barra de herramientas primaria.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
de Nuevo ancho del botón del cuadro combinado.

##  <a name="onupdatetooltip"></a>  CMFCToolBarComboBoxButton::OnUpdateToolTip

Lo llama el marco de trabajo cuando el usuario cambia la información sobre herramientas para el botón de cuadro combinado.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
de Puntero a la ventana primaria del botón de cuadro combinado.

*iButtonIndex*<br/>
de IDENTIFICADOR del botón del cuadro combinado.

*wndToolTip*<br/>
de Información sobre herramientas que se va a asociar al botón de cuadro combinado.

*str*<br/>
de Texto de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

TRUE si el método controla el evento; en caso contrario, FALSE.

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

Elimina todos los elementos de los cuadros de lista y de edición.

```
void RemoveAllItems();
```

### <a name="remarks"></a>Comentarios

Quita todos los elementos del cuadro de lista y el control de edición de un cuadro combinado.

##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem

Selecciona un elemento en el cuadro de lista.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento del cuadro de lista.

*bNotify*<br/>
de TRUE para notificar al botón de cuadro combinado de la selección; en caso contrario, FALSE.

*dwData*<br/>
de Los datos asociados a un elemento en el cuadro de lista.

*lpszText*<br/>
de Texto de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll

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

*uiCmd*<br/>
de IDENTIFICADOR de comando del botón de cuadro combinado que contiene el cuadro de lista.

*iIndex*<br/>
de Índice de base cero del elemento en el cuadro de lista. Un valor de-1 quita cualquier selección actual del cuadro de lista y borra el cuadro de edición.

*dwData*<br/>
de Datos de un elemento del cuadro de lista.

*lpszText*<br/>
de Texto de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="serialize"></a>  CMFCToolBarComboBoxButton::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
[in, out] `CArchive` Objeto que se va a serializar.

### <a name="remarks"></a>Comentarios

La `CArchive` configuración del objeto determina si este método lee o escribe en el archivo.

##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData

Rellena el objeto especificado `CAccessibilityData` utilizando los datos de accesibilidad del botón de cuadro combinado.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
de Ventana primaria del botón de cuadro combinado.

*data*<br/>
enuncia `CAccessibilityData` Objeto que recibe los datos de accesibilidad del botón de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

##  <a name="setcentervert"></a>  CMFCToolBarComboBoxButton::SetCenterVert

Establece la posición vertical de los botones del cuadro combinado en la aplicación.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parámetros

*bCenterVert*<br/>
de TRUE para centrar el botón de cuadro combinado en la barra de herramientas; FALSE para alinear el botón de cuadro combinado en la parte superior de la barra de herramientas.

### <a name="remarks"></a>Comentarios

De forma predeterminada, los botones de cuadro combinado se alinean en la parte superior.

##  <a name="setcontextmenuid"></a>  CMFCToolBarComboBoxButton::SetContextMenuID

Establece el identificador de recurso del menú contextual para el botón de cuadro combinado.

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parámetros

*uiResID*<br/>
de IDENTIFICADOR de recurso del menú contextual.

##  <a name="setdropdownheight"></a>  CMFCToolBarComboBoxButton::SetDropDownHeight

Establece el alto del cuadro de lista cuando se suelta.

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parámetros

*nHeight*<br/>
de Alto, en píxeles, del cuadro de lista.

### <a name="remarks"></a>Comentarios

El alto predeterminado es 150 píxeles.

##  <a name="setflatmode"></a>  CMFCToolBarComboBoxButton::SetFlatMode

Establece la apariencia de estilo plano de los botones del cuadro combinado en la aplicación.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
de TRUE para una apariencia de estilo plano; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El estilo plano predeterminado de los botones del cuadro combinado es FALSE.

##  <a name="setstyle"></a>  CMFCToolBarComboBoxButton::SetStyle

Establece el estilo especificado para el botón de cuadro combinado y vuelve a dibujar el control si no se deshabilita.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
de Combinación bit a bit (o) de estilos de barra de herramientas.

### <a name="remarks"></a>Comentarios

Para obtener una lista de estilos de botón de la barra de herramientas, vea [estilos de control Toolbar](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>  CMFCToolBarComboBoxButton::SetText

Establece el texto en el cuadro de edición del botón de cuadro combinado.

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
de Puntero a una cadena que contiene el texto del cuadro de edición.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
