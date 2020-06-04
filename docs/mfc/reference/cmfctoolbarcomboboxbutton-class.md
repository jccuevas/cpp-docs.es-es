---
title: CMFCToolBarComboBoxButton (Clase)
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
ms.openlocfilehash: 995d7d0db55889130e1cad9585b8fc87285ffd27
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754016"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton (Clase)

Un botón de barra de herramientas que contiene un control de cuadro combinado ( [CComboBox (Clase)](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Sintaxis

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|Construye un objeto `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|Agrega un elemento al final de la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|Agrega un elemento a la lista de cuadros combinados. El orden de los elementos `Compare`de la lista se especifica mediante .|
|[CMFCToolBarComboBoxButton::Compare](#compare)|Compara dos elementos. Se llama para `AddSortedItems` ordenar los elementos que se agrega a la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|Crea un nuevo control de edición para el botón del cuadro combinado.|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|Elimina un elemento de la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|Devuelve el índice del elemento que contiene una cadena especificada.|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|Devuelve un puntero al botón del cuadro combinado con un identificador de comando especificado.|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|Devuelve un puntero al control de cuadro combinado que está incrustado en el botón de cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|Devuelve el número de elementos de la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Devuelve el número de elementos de la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|Devuelve el índice del elemento seleccionado en la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el índice del elemento seleccionado en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|Devuelve un puntero al control de edición incrustado en el botón del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|Devuelve la cadena asociada a un índice especificado en la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve la cadena asociada a un índice en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|Devuelve el valor de 32 bits asociado a un índice especificado en la lista de cuadros combinados.|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el valor de 32 bits asociado a un índice en la lista de cuadros combinados de ese botón.|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Recupera el valor de 32 bits que está asociado a un índice en la lista de cuadros combinados de ese botón y devuelve el valor de 32 bits como puntero.|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|Devuelve el texto del control de edición del cuadro combinado.|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado y devuelve el texto del control de edición de ese botón.|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|Determina si los botones del cuadro combinado de la aplicación están centrados o alineados con la parte superior de la barra de herramientas.|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|Determina si los botones del cuadro combinado de la aplicación tienen un aspecto plano.|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|Quita todos los elementos del cuadro de lista y edita el control del cuadro combinado.|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|Selecciona un elemento en el cuadro combinado según su índice, valor de 32 bits o cadena y notifica al control del cuadro combinado sobre la selección.|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|Busca el botón de cuadro combinado que tiene un identificador de comando especificado. Llamadas `SelectItem` para seleccionar un elemento en el cuadro combinado de ese botón según su cadena, índice o valor de 32 bits.|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|Especifica si los botones del cuadro combinado de la aplicación están centrados verticalmente o alineados con la parte superior de la barra de herramientas.|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|Establece la altura del cuadro de lista desplegable.|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|Especifica si los botones de cuadro combinado de la aplicación tienen un aspecto plano.|

## <a name="remarks"></a>Observaciones

Para agregar un botón de cuadro combinado a una barra de herramientas, siga estos pasos:

1. Reserve un id. de recurso ficticio para el botón en el recurso primario de la barra de herramientas.

2. Construir `CMFCToolBarComboBoxButton` un objeto.

3. En el controlador de mensajes que procesa el mensaje de AFX_WM_RESETTOOLBAR, reemplace el botón ficticio con el nuevo botón de cuadro combinado mediante [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Para obtener más información, vea [Tutorial: Colocar controles en barras](../../mfc/walkthrough-putting-controls-on-toolbars.md)de herramientas . Para obtener un ejemplo de un botón de barra de herramientas de cuadro combinado, vea el proyecto de ejemplo VisualStudioDemo.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCToolBarComboBoxButton` . En el ejemplo se muestra cómo habilitar los cuadros de edición y combinación, establecer la posición vertical de los botones del cuadro combinado en la aplicación, establecer la altura del cuadro de lista cuando se coloca hacia abajo, establecer la apariencia de estilo plano de los botones de cuadro combinado en la aplicación y establecer el texto en el cuadro de edición del botón de cuadro combinado. Este fragmento de código forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComboBoxButton::AddItem

Anexa un elemento único al cuadro de lista.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
[en] Texto del elemento que se va a agregar al cuadro de lista.

*dwData*<br/>
[en] Los datos asociados con el elemento que se va a agregar al cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El índice del último elemento del cuadro de lista.

### <a name="remarks"></a>Observaciones

No utilice este método cuando se ordene el estilo del cuadro de lista.

Si el texto del elemento ya está en el cuadro de lista, los nuevos datos se almacenan con el elemento existente. La búsqueda del elemento distingue mayúsculas de minúsculas.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

Agrega un elemento al cuadro de lista en el orden definido por el [Compare](#compare) método.

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
[en] Texto del elemento que se va a agregar al cuadro de lista.

*dwData*<br/>
[en] Los datos asociados con el elemento que se va a agregar al cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Indice del elemento que se agregó al cuadro de lista.

### <a name="remarks"></a>Observaciones

Utilice esta función para agregar elementos al cuadro de lista en un orden específico.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBestretched

Indica si el tamaño del botón del cuadro combinado puede cambiar.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

Construye un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objeto.

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
[en] El identificador de comando del nuevo botón.

*iImage*<br/>
[en] El índice de imagen de la imagen asociada con el nuevo botón.

*dwStyle*<br/>
[en] El estilo del nuevo botón.

*iWidth*<br/>
[en] El ancho, en píxeles, del nuevo botón.

### <a name="remarks"></a>Observaciones

El ancho predeterminado es de 150 píxeles.

Para obtener una lista de estilos de botón de barra de herramientas, consulte [ToolBar Control Styles](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

Elimina los datos definidos por el usuario.

```
virtual void ClearData();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método no hace nada. Invalide este método en una clase derivada si desea eliminar los datos definidos por el usuario.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComboBoxButton::Compare

Compara dos cadenas.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Parámetros

*lpszItem1*<br/>
[en] La primera cadena que se va a comparar.

*lpszItem2*<br/>
[en] La segunda cadena que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Valor que indica la relación lexicográfica que distingue mayúsculas de minúsculas entre las cadenas. En la tabla siguiente, se ofrecen los valores posibles:

|Value|Descripción|
|-----------|-----------------|
|\<0|La primera cadena es menor que la segunda.|
|0|La primera cadena es igual a la segunda.|
|>0|La primera cadena es mayor que la segunda.|

### <a name="remarks"></a>Observaciones

Invalide este método para cambiar la forma en que se ordenan los elementos en el cuadro de lista.

La comparación distingue mayúsculas de minúsculas.

Este método se llama solo desde el [AddSortedItem](#addsorteditem) método.

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarComboBoxButton::CopyFrom

Copia el estado del `CMFCToolBarComboBoxButton` objeto especificado en el objeto actual.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Parámetros

*src*<br/>
[en] El `CMFCToolBarComboBoxButton` objeto de origen.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComboBoxButton::CreateCombo

Crea un nuevo cuadro combinado para el botón del cuadro combinado.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la ventana primaria del botón.

*Rect*<br/>
[en] Rectángulo delimitador del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Un puntero al nuevo cuadro combinado si el método se realizó correctamente; de lo contrario, NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

Crea un nuevo cuadro de edición para el botón del cuadro combinado.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Un puntero a la ventana primaria del botón.

*Rect*<br/>
[en] Rectángulo delimitador del nuevo cuadro de edición.

*dwEditStyle*<br/>
[en] Estilo de control del nuevo cuadro de edición.

### <a name="return-value"></a>Valor devuelto

Un puntero al nuevo cuadro de edición si el método se realizó correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método cuando crea un nuevo cuadro de edición para un botón de cuadro combinado. Invalide este método para cambiar cómo se crea [CMFCToolBarComboBoxEdit.](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComboBoxButton::DeleteItem

Elimina un elemento especificado del cuadro de lista.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero del elemento que se va a eliminar.

*dwData*<br/>
[en] Los datos asociados con el elemento que se va a eliminar.

*lpszText*<br/>
[en] El texto del elemento que se va a eliminar. Si hay varios elementos con el mismo texto, se elimina el primer elemento.

### <a name="return-value"></a>Valor devuelto

TRUESi el elemento se ha localizado y eliminado correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComboBoxButton::DuplicateData

Duplica los datos definidos por el usuario.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método no hace nada. Invalide este método en una clase derivada si desea copiar los datos definidos por el usuario.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

Habilita o deshabilita los cuadros de edición y combinación.

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar los cuadros de edición y combinación; FALSE para deshabilitar los cuadros de edición y combinación.

### <a name="remarks"></a>Observaciones

Cuando se deshabilita, los controles no pueden activarse y no pueden aceptar la entrada del usuario.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

Copia una cadena de la tabla de cadenas de aplicación en el menú especificado mediante el identificador de comando de botón de cuadro combinado.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Parámetros

*menuButton*<br/>
[fuera] Referencia a un botón de menú.

### <a name="return-value"></a>Valor devuelto

Siempre TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

Devuelve el índice del primer elemento del cuadro de lista que contiene una cadena especificada.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[en] Texto para el que desea buscar en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El índice del elemento; o CB_ERR si no se encuentra el artículo.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

Obtiene un puntero al botón de cuadro combinado que tiene un identificador de comando especificado.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado.

*bIsFocus*<br/>
[en] TRUE para buscar solo botones enfocados; FALSE para buscar en todos los botones.

### <a name="return-value"></a>Valor devuelto

Un puntero a un botón de cuadro combinado; o NULL si no se encuentra el botón.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

Devuelve un puntero al cuadro combinado en el botón del cuadro combinado.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CComboBox clase](../../mfc/reference/ccombobox-class.md) objeto si el método se realizó correctamente; NULL.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

Obtiene el identificador de recurso del menú contextual para el botón de cuadro combinado.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Valor devuelto

El identificador de recurso del menú contextual.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComboBoxButton::GetCount

Devuelve el número de elementos del cuadro de lista.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del cuadro de lista.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

Obtiene el número de elementos del cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El número de elementos en el cuadro de lista; de lo contrario, CB_ERR si no se encuentra el botón del cuadro combinado.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

Obtiene el índice del elemento seleccionado actualmente en el cuadro de lista.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

El índice del elemento seleccionado actualmente en el cuadro de lista; o CB_ERR si no se selecciona ningún elemento.

### <a name="remarks"></a>Observaciones

El índice del cuadro de lista se basa en cero.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

Devuelve el índice del elemento seleccionado actualmente en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El índice del elemento seleccionado actualmente en el cuadro de lista; de lo contrario, CB_ERR si no se selecciona ningún elemento o no se encuentra un botón de cuadro combinado.

### <a name="remarks"></a>Observaciones

El índice del cuadro de lista se basa en cero.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

Devuelve un puntero al cuadro de edición en el botón del cuadro combinado.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al cuadro de edición si el método se realizó correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

Devuelve el identificador de ventana para el cuadro combinado.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Valor devuelto

El identificador de ventana, o NULL si el cuadro combinado no está asociado a un objeto de ventana.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComboBoxButton::GetItem

Devuelve la cadena asociada a un elemento en un índice especificado en el cuadro de lista.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Un puntero a la cadena que está asociada con el elemento; de lo contrario, NULL si el parámetro de índice no es válido, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro combinado.

### <a name="remarks"></a>Observaciones

Un parámetro de índice de -1 devuelve la cadena del elemento que está seleccionado actualmente.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

Devuelve la cadena asociada a un elemento en un índice especificado en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado.

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Un puntero a la cadena del elemento si el método se realizó correctamente; de lo contrario, NULL si el índice no es válido, no se encuentra un botón de cuadro combinado, o si index es -1 y no hay ningún elemento seleccionado en el cuadro combinado.

### <a name="remarks"></a>Observaciones

Un valor de índice de -1 devuelve la cadena del elemento que está seleccionado actualmente.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Los datos asociados con el elemento; o 0 si el elemento no existe.

### <a name="remarks"></a>Observaciones

Un parámetro de índice de -1 devuelve los datos asociados con el elemento seleccionado actualmente.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando específico.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado.

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Los datos asociados con el elemento si el método se realizó correctamente; de lo contrario, 0 si el índice especificado no es válido, o CB_ERR si no se encuentra el botón de cuadro combinado.

### <a name="remarks"></a>Observaciones

Un parámetro de índice de -1 devuelve los datos asociados con el elemento seleccionado actualmente.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

Devuelve los datos asociados a un elemento en un índice específico en el cuadro de lista de un botón de cuadro combinado que tiene un identificador de comando específico. Estos datos se devuelven como un puntero.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando del botón del cuadro combinado.

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Puntero asociado al elemento si el método se realizó correctamente; de lo contrario, -1 si se produce un error, o NULL si no se encuentra el botón de cuadro combinado.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

Devuelve la cadena de solicitud para el botón de cuadro combinado.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Valor devuelto

La cadena de solicitud.

### <a name="remarks"></a>Observaciones

Este método no está implementado actualmente.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComboBoxButton::GetText

Obtiene el texto del cuadro de edición.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Valor devuelto

El texto del cuadro de edición.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

Obtiene el texto del cuadro de edición de un botón de cuadro combinado que tiene un identificador de comando especificado.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Parámetros

*uiCmd*<br/>
[en] El identificador de comando de un botón de cuadro combinado específico.

### <a name="return-value"></a>Valor devuelto

El texto del cuadro de edición si el método se realizó correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

Indica si el cuadro combinado tiene actualmente el foco.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el cuadro combinado tiene actualmente el foco; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método también devuelve TRUE si cualquier ventana secundaria del cuadro combinado tiene actualmente el foco.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

Devuelve la posición vertical de los botones del cuadro combinado en la aplicación.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Valor devuelto

TRUESi los botones están centrados; FALSE si los botones están alineados en la parte superior.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

Devuelve la apariencia de estilo plano de los botones de cuadro combinado en la aplicación.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Valor devuelto

TRUESi los botones tienen un estilo plano; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El estilo plano predeterminado para los botones del cuadro combinado es FALSE.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

Indica si el identificador especificado está asociado con el botón de cuadro combinado o uno de sus elementos secundarios.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Parámetros

*Hwnd*<br/>
[en] Un asa de ventana.

### <a name="return-value"></a>Valor devuelto

TRUESi el identificador se asócated con el botón de cuadro combinado, o uno de sus elementos secundarios; de lo contrario, FALSE.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

Indica si el botón del cuadro combinado reside en un panel de la cinta de opciones.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Valor devuelto

Siempre FALSE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método siempre devuelve FALSE, lo que significa que el botón de cuadro combinado nunca se muestra en un panel de la cinta de opciones.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

Devuelve el estado de visibilidad del botón del cuadro combinado.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Valor devuelto

El estado de visibilidad del botón del cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

Indica si el botón del cuadro combinado procesa el mensaje.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Parámetros

*iNotifyCode*<br/>
[en] El mensaje de notificación asociado al comando.

### <a name="return-value"></a>Valor devuelto

Si el botón del cuadro combinado procesa el mensaje.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

Llamado por el marco de trabajo cuando el botón se agrega al **personalizar** cuadro de diálogo.

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarComboBoxButton::OnCalculateSize

Llamado por el marco de trabajo para calcular el tamaño del botón.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón del cuadro combinado.

*sizeDefault*<br/>
[en] El tamaño predeterminado del botón del cuadro combinado.

*bHorz*<br/>
[en] El estado de acoplamiento de la barra de herramientas principal. TRUECuando la barra de herramientas se acopla horizontalmente y FALSE cuando la barra de herramientas se acopla verticalmente.

### <a name="return-value"></a>Valor devuelto

Estructura `SIZE` que contiene las dimensiones del botón del cuadro combinado, en píxeles.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

Llamado por el marco de trabajo cuando el botón de cuadro combinado se inserta en una nueva barra de herramientas.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Puntero a la nueva barra de herramientas principal.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarComboBoxButton::OnClick

Llamado por el marco de trabajo cuando el usuario hace clic en el botón de cuadro combinado.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
[en] Puntero a la ventana principal del botón del cuadro combinado.

*bDelay*<br/>
[en] Reservado para su uso en una clase derivada.

### <a name="return-value"></a>Valor devuelto

TRUESi el método controla el evento; de lo contrario, FALSE.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

Llamado por el marco de trabajo cuando el usuario cambia el color de la barra de herramientas principal para establecer el color del botón del cuadro combinado.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón del cuadro combinado.

*nCtlColor*<br/>
[in] Sin utilizar.

### <a name="return-value"></a>Valor devuelto

Controle el pincel que utiliza el marco de trabajo para pintar el fondo del botón del cuadro combinado.

### <a name="remarks"></a>Observaciones

Este método también establece el color de texto del botón de cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarComboBoxButton::OnDraw

Llamado por el marco de trabajo para dibujar el botón de cuadro combinado mediante el uso de los estilos y opciones especificados.

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
[en] El contexto del dispositivo que muestra el botón.

*Rect*<br/>
[en] El rectángulo delimitador del botón.

*pImages*<br/>
[en] La colección de imágenes asociada al botón.

*bHorz*<br/>
[en] El estado de acoplamiento de la barra de herramientas principal. TRUECuando la barra de herramientas se acopla horizontalmente y FALSE cuando la barra de herramientas se acopla verticalmente.

*bCustomizeMode*<br/>
[en] Si la aplicación está en modo de personalización.

*bResaltar*<br/>
[en] Si desea dibujar el botón del cuadro combinado resaltado.

*bDrawBorder*<br/>
[en] Si desea dibujar el botón del cuadro combinado con un borde.

*bGrayDisabledButtons*<br/>
[en] TRUE para dibujar botones deshabilitados sombreados; FALSE para utilizar la colección de imágenes deshabilitadas.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

Llamado por el marco de trabajo para dibujar el botón del cuadro combinado en el **comandos** panel de la **personalizar** cuadro de diálogo.

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] El contexto del dispositivo que muestra el botón del cuadro combinado.

*Rect*<br/>
[en] El rectángulo delimitador del botón del cuadro combinado.

*bSeleccionado*<br/>
[en] TRUESi se selecciona el botón de cuadro combinado; de lo contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

El ancho, en píxeles, del botón del cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

Llamado por el marco de trabajo para establecer la fuente del botón del cuadro combinado cuando cambia la fuente de la aplicación.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

Llamado por el marco de trabajo para cambiar la ubicación del botón del cuadro combinado cuando se mueve la barra de herramientas principal.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

Llamado por el marco de trabajo cuando el botón del cuadro combinado está oculto o se muestra.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Parámetros

*bMostrar*<br/>
[en] Si desea ocultar o mostrar el botón del cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarComboBoxButton::OnSize

Llamado por el marco de trabajo para cambiar el tamaño del botón del cuadro combinado cuando la barra de herramientas principal cambia de tamaño.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Parámetros

*iSize*<br/>
[en] El nuevo ancho del botón del cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

Llamado por el marco de trabajo cuando el usuario cambia la información sobre herramientas para el botón de cuadro combinado.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Parámetros

*pWndParent*<br/>
[en] Puntero a la ventana primaria para el botón del cuadro combinado.

*iButtonIndex*<br/>
[en] ID del botón del cuadro combinado.

*wndToolTip*<br/>
[en] La información sobre herramientas que se va a asociar con el botón del cuadro combinado.

*Str*<br/>
[en] El texto de la información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

TRUESi el método controla el evento; de lo contrario, FALSE.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComboBoxButton::RemoveAllItems

Elimina todos los elementos de la lista y los cuadros de edición.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Observaciones

Quita todos los elementos del cuadro de lista y edita el control de un cuadro combinado.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComboBoxButton::SelectItem

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
[en] El índice de base cero de un elemento en el cuadro de lista.

*bNotificar*<br/>
[en] TRUE para notificar el botón del cuadro combinado de la selección; de lo contrario FALSO.

*dwData*<br/>
[en] Los datos asociados a un elemento en el cuadro de lista.

*lpszText*<br/>
[en] El texto de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

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
[en] El identificador de comando del botón de cuadro combinado que contiene el cuadro de lista.

*iIndex*<br/>
[en] El índice de base cero del elemento en el cuadro de lista. Un valor de -1 elimina cualquier selección actual en el cuadro de lista y borra el cuadro de edición.

*dwData*<br/>
[en] Los datos de un elemento en el cuadro de lista.

*lpszText*<br/>
[en] El texto de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComboBoxButton::Serialize

Lee este objeto de un archivo o lo escribe en un archivo.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*Ar*<br/>
[adentro, fuera] Objeto `CArchive` que se va a serializar.

### <a name="remarks"></a>Observaciones

La configuración `CArchive` del objeto determina si este método lee o escribe en el archivo.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComboBoxButton::SetACCData

Rellena el objeto `CAccessibilityData` especificado mediante los datos de accesibilidad del botón del cuadro combinado.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Parámetros

*pParent*<br/>
[en] La ventana principal del botón del cuadro combinado.

*datos*<br/>
[fuera] Objeto `CAccessibilityData` que recibe los datos de accesibilidad del botón del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

Establece la posición vertical de los botones del cuadro combinado en la aplicación.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Parámetros

*bCenterVert*<br/>
[en] TRUE para centrar el botón del cuadro combinado en la barra de herramientas; FALSE para alinear el botón del cuadro combinado con la parte superior de la barra de herramientas.

### <a name="remarks"></a>Observaciones

De forma predeterminada, los botones del cuadro combinado se alinean con la parte superior.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

Establece el identificador de recurso del menú contextual para el botón del cuadro combinado.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Parámetros

*uiResID*<br/>
[en] El identificador de recurso del menú contextual.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

Establece la altura del cuadro de lista cuando se deja caer.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parámetros

*nAltura*<br/>
[en] Altura, en píxeles, del cuadro de lista.

### <a name="remarks"></a>Observaciones

La altura predeterminada es de 150 píxeles.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

Establece la apariencia de estilo plano de los botones del cuadro combinado en la aplicación.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Parámetros

*bFlat*<br/>
[en] TRUE para una apariencia de estilo plano; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El estilo plano predeterminado para los botones del cuadro combinado es FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComboBoxButton::SetStyle

Establece el estilo especificado para el botón del cuadro combinado y vuelve a dibujar el control si no está deshabilitado.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
[en] Una combinación bit a bit (OR) de estilos de barra de herramientas.

### <a name="remarks"></a>Observaciones

Para obtener una lista de estilos de botón de barra de herramientas, consulte [ToolBar Control Styles](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComboBoxButton::SetText

Establece el texto en el cuadro de edición del botón del cuadro combinado.

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[en] Puntero a una cadena que contiene el texto del cuadro de edición.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton (clase)](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Tutorial: Poner controles en las barras de herramientas](../../mfc/walkthrough-putting-controls-on-toolbars.md)
