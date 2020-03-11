---
title: CTabCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875853"
---
# <a name="ctabctrl-class"></a>CTabCtrl (clase)

Proporciona la funcionalidad del control de pestaña común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabCtrl:: CTabCtrl](#ctabctrl)|Construye un objeto `CTabCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabCtrl:: AdjustRect](#adjustrect)|Calcula el área de presentación de un control de ficha dado un rectángulo de ventana o calcula el rectángulo de ventana que se correspondería con un área de presentación determinada.|
|[CTabCtrl:: Create](#create)|Crea un control de ficha y lo adjunta a una instancia de un objeto `CTabCtrl`.|
|[CTabCtrl:: CreateEx](#createex)|Crea un control de ficha con los estilos extendidos de Windows especificados y lo adjunta a una instancia de un objeto `CTabCtrl`.|
|[CTabCtrl::D eleteAllItems](#deleteallitems)|Quita todos los elementos de un control de ficha.|
|[CTabCtrl::D eleteItem](#deleteitem)|Quita un elemento de un control de ficha.|
|[CTabCtrl::D eselectAll](#deselectall)|Restablece los elementos de un control de ficha, borrando los que se presionaron.|
|[CTabCtrl::D rawItem](#drawitem)|Dibuja un elemento especificado de un control de ficha.|
|[CTabCtrl:: GetCurFocus](#getcurfocus)|Recupera la pestaña con el foco actual de un control de ficha.|
|[CTabCtrl:: GetCurSel](#getcursel)|Determina la pestaña seleccionada actualmente en un control de ficha.|
|[CTabCtrl:: GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están actualmente en uso para el control de ficha.|
|[CTabCtrl:: GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control de ficha.|
|[CTabCtrl:: GetItem](#getitem)|Recupera información sobre una pestaña de un control de ficha.|
|[CTabCtrl:: GetItemCount](#getitemcount)|Recupera el número de pestañas del control de pestaña.|
|[CTabCtrl:: GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de una pestaña en un control de ficha.|
|[CTabCtrl:: GetItemState](#getitemstate)|Recupera el estado del elemento de control de ficha indicado.|
|[CTabCtrl:: GetRowCount](#getrowcount)|Recupera el número actual de filas de las fichas de un control de ficha.|
|[CTabCtrl:: GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asociado a un control de ficha.|
|[CTabCtrl:: HighlightItem](#highlightitem)|Establece el estado de resaltado de un elemento de ficha.|
|[CTabCtrl:: HitTest](#hittest)|Determina qué pestaña, si la hay, está en la posición de pantalla especificada.|
|[CTabCtrl:: InsertItem](#insertitem)|Inserta una nueva pestaña en un control de ficha.|
|[CTabCtrl:: RemoveImage](#removeimage)|Quita una imagen de una lista de imágenes de un control de ficha.|
|[CTabCtrl:: SetCurFocus](#setcurfocus)|Establece el foco en una pestaña especificada de un control de ficha.|
|[CTabCtrl:: SetCurSel](#setcursel)|Selecciona una pestaña en un control de ficha.|
|[CTabCtrl:: SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para un control de ficha.|
|[CTabCtrl:: SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de ficha.|
|[CTabCtrl:: SetItem](#setitem)|Establece algunos o todos los atributos de una pestaña.|
|[CTabCtrl:: SetItemExtra](#setitemextra)|Establece el número de bytes por pestaña reservado para los datos definidos por la aplicación en un control de ficha.|
|[CTabCtrl:: SetItemSize](#setitemsize)|Establece el ancho y el alto de un elemento.|
|[CTabCtrl:: SetItemState](#setitemstate)|Establece el estado del elemento de control de ficha indicado.|
|[CTabCtrl:: SetMinTabWidth](#setmintabwidth)|Establece el ancho mínimo de los elementos de un control de ficha.|
|[CTabCtrl:: SetPadding](#setpadding)|Establece la cantidad de espacio (relleno) alrededor de la etiqueta y el icono de cada pestaña en un control de ficha.|
|[CTabCtrl:: SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control de ficha.|

## <a name="remarks"></a>Observaciones

Un "control de pestaña" es análogo a los divisores de un bloc de notas o las etiquetas de un archivo. cab. Mediante el uso de un control de ficha, una aplicación puede definir varias páginas para la misma área de un cuadro de diálogo o de una ventana. Cada página está formada por un conjunto de información o un grupo de controles que la aplicación muestra cuando el usuario selecciona la pestaña correspondiente. Un tipo especial de control de pestaña muestra las pestañas que se parecen a los botones. Hacer clic en un botón debe ejecutar inmediatamente un comando en lugar de mostrar una página.

Este control (y, por tanto, la clase `CTabCtrl`) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

Para obtener más información sobre el uso de `CTabCtrl`, vea [controles](../../mfc/controls-mfc.md) y [usar CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="adjustrect"></a>CTabCtrl:: AdjustRect

Calcula el área de presentación de un control de ficha dado un rectángulo de ventana o calcula el rectángulo de ventana que se correspondería con un área de presentación determinada.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*bLarger*<br/>
Indica la operación que se va a realizar. Si este parámetro es TRUE, *lpRect* especifica un rectángulo de presentación y recibe el rectángulo de ventana correspondiente. Si este parámetro es FALSE, *lpRect* especifica un rectángulo de ventana y recibe el rectángulo de presentación correspondiente.

*lpRect*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que especifica el rectángulo dado y recibe el rectángulo calculado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl:: Create

Crea un control de ficha y lo adjunta a una instancia de un objeto `CTabCtrl`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de pestaña. Aplique cualquier combinación de [estilos de control de pestaña](/windows/win32/Controls/tab-control-styles)que se describe en el Windows SDK. Vea la **sección Comentarios** para obtener una lista de estilos de ventana que también se pueden aplicar al control.

*Rect*<br/>
Especifica el tamaño y la posición del control de pestaña. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de pestaña, normalmente una `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de pestaña.

### <a name="return-value"></a>Valor devuelto

TRUE si la inicialización del objeto se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cree un objeto de `CTabCtrl` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de pestaña y lo adjunta al objeto `CTabCtrl`.

Además de los estilos de control de pestaña, puede aplicar los siguientes estilos de ventana a un control de ficha:

- WS_CHILD crea una ventana secundaria que representa el control de ficha. No se puede usar con el estilo WS_POPUP.

- WS_VISIBLE crea un control de ficha que está inicialmente visible.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente.

- WS_GROUP especifica el primer control de un grupo de controles en el que el usuario puede moverse de un control al siguiente con las teclas de dirección. Todos los controles definidos con el estilo de WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo de estilos e inicia el grupo siguiente (es decir, un grupo finaliza en el que comienza la siguiente).

- WS_TABSTOP especifica uno de los diversos controles a través de los cuales el usuario puede desplazarse mediante la tecla TAB. La tecla TAB mueve el usuario al siguiente control especificado por el estilo WS_TABSTOP.

Para crear un control de ficha con estilos de ventana extendidos, llame a [CTabCtrl:: CreateEx](#createex) en lugar de a `Create`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl:: CreateEx

Crea un control (una ventana secundaria) y lo asocia al objeto `CTabCtrl`.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de pestaña. Aplique cualquier combinación de [estilos de control de pestaña](/windows/win32/Controls/tab-control-styles)que se describe en el Windows SDK. Vea la **sección Comentarios** de [Create](#create) para obtener una lista de estilos de ventana que también se pueden aplicar al control.

*Rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es correcto; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

Use `CreateEx` en lugar de [Create](#create) para aplicar los estilos extendidos de Windows, especificados por el **WS_EX_** de prefacio de estilo extendido de Windows.

`CreateEx` crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Establecer estilos extendidos específicos de un control mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, utilice `CreateEx` para establecer tales estilos como WS_EX_CONTEXTHELP, pero use `SetExtendedStyle` para establecer tales estilos como TCS_EX_FLATSEPARATORS. Para obtener más información, consulte los estilos descritos en [control de pestaña estilos extendidos](/windows/win32/Controls/tab-control-extended-styles) en el Windows SDK.

##  <a name="ctabctrl"></a>CTabCtrl:: CTabCtrl

Construye un objeto `CTabCtrl`.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl::D eleteAllItems

Quita todos los elementos de un control de ficha.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="deleteitem"></a>CTabCtrl::D eleteItem

Quita el elemento especificado de un control de ficha.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Valor basado en cero del elemento que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl::D eselectAll

Restablece los elementos de un control de ficha, borrando los que se presionaron.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parámetros

*fExcludeFocus*<br/>
Marca que especifica el ámbito de la anulación de la selección del elemento. Si este parámetro se establece en FALSE, se restablecerán todos los botones de pestaña. Si se establece en TRUE, se restablecerán todos los elementos de ficha excepto el seleccionado actualmente.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), como se describe en el Windows SDK.

##  <a name="drawitem"></a>CTabCtrl::D rawItem

Lo llama el marco de trabajo cuando cambia el aspecto visual de un control de ficha dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que describe el elemento que se va a pintar.

### <a name="remarks"></a>Observaciones

El miembro `itemAction` de la estructura `DRAWITEMSTRUCT` define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro para implementar el dibujo de un objeto de `CTabCtrl` dibujado por el propietario.

La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que esta función miembro finalice.

##  <a name="getcurfocus"></a>CTabCtrl:: GetCurFocus

Recupera el índice de la pestaña con el foco actual.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña con el foco actual.

##  <a name="getcursel"></a>CTabCtrl:: GetCurSel

Recupera la pestaña seleccionada actualmente en un control de ficha.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña seleccionada si es correcta o-1 si no hay ninguna pestaña seleccionada.

##  <a name="getextendedstyle"></a>CTabCtrl:: GetExtendedStyle

Recupera los estilos extendidos que están actualmente en uso para el control de ficha.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valor devuelto

Representa los estilos extendidos actualmente en uso para el control de pestaña. Este valor es una combinación de [estilos extendidos de control de pestañas](/windows/win32/Controls/tab-control-extended-styles), como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="getimagelist"></a>CTabCtrl:: GetImageList

Recupera la lista de imágenes asociada a un control de pestaña.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, puntero a la lista de imágenes del control de pestaña; de lo contrario, NULL.

##  <a name="getitem"></a>CTabCtrl:: GetItem

Recupera información sobre una pestaña de un control de ficha.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero de la pestaña.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , que se usa para especificar la información que se va a recuperar. También se usa para recibir información acerca de la pestaña. Esta estructura se utiliza con las funciones miembro `InsertItem`, `GetItem`y `SetItem`.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto; De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando se envía el mensaje, el miembro `mask` especifica los atributos que se van a devolver. Si el miembro `mask` especifica el valor TCIF_TEXT, el miembro `pszText` debe contener la dirección del búfer que recibe el texto del elemento y el miembro `cchTextMax` debe especificar el tamaño del búfer.

- `mask`

   Valor que especifica el `TCITEM` miembros de estructura que se van a recuperar o establecer. Este miembro puede ser cero o una combinación de los siguientes valores:

   - TCIF_TEXT el miembro de `pszText` es válido.

   - TCIF_IMAGE el miembro de `iImage` es válido.

   - TCIF_PARAM el miembro de `lParam` es válido.

   - TCIF_RTLREADING el texto de `pszText` se muestra utilizando el orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.

   - TCIF_STATE el miembro de `dwState` es válido.

- `pszText`

   Puntero a una cadena terminada en null que contiene el texto de la pestaña si la estructura contiene información sobre una pestaña. Si la estructura está recibiendo información, este miembro especifica la dirección del búfer que recibe el texto de la pestaña.

- `cchTextMax`

   Tamaño del búfer al que apunta `pszText`. Este miembro se omite si la estructura no recibe información.

- `iImage` índice en la lista de imágenes del control de pestañas o-1 si no hay ninguna imagen para la pestaña.

- `lParam`

   Datos definidos por la aplicación asociados a la pestaña. Si hay más de cuatro bytes de datos definidos por la aplicación por pestaña, una aplicación debe definir una estructura y utilizarla en lugar de la estructura `TCITEM`. El primer miembro de la estructura definida por la aplicación debe ser una estructura [TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw). La estructura `TCITEMHEADER` es idéntica a la estructura `TCITEM`, pero sin el miembro `lParam`. La diferencia entre el tamaño de la estructura y el tamaño de la estructura de `TCITEMHEADER` debe ser igual al número de bytes adicionales por pestaña.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl:: GetItemCount

Recupera el número de pestañas del control de pestaña.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos del control de pestaña.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>CTabCtrl:: GetItemRect

Recupera el rectángulo delimitador de la pestaña especificada en un control de ficha.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento de ficha.

*lpRect*<br/>
Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibe el rectángulo delimitador de la pestaña. Estas coordenadas usan el modo de asignación actual de la ventanilla.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>CTabCtrl:: GetItemState

Recupera el estado del elemento de control de pestaña identificado por *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Número de índice de base cero del elemento para el que se va a recuperar información de estado.

*dwMask*<br/>
Máscara que especifica la marca de estado del elemento que se va a devolver. Para obtener una lista de valores, vea el miembro Mask de la estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Referencia a un valor DWORD que recibe la información de estado. Puede ser uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de pestaña.|
|TCIS_HIGHLIGHTED|Se resalta el elemento de control de pestaña y la pestaña y el texto se dibujan con el color de resaltado actual. Al usar el color de resaltado, se trata de una interpolación verdadera, no de un color interpolado.|

### <a name="remarks"></a>Observaciones

El estado de un elemento se especifica mediante el `dwState` miembro de la estructura de `TCITEM`.

##  <a name="getrowcount"></a>CTabCtrl:: GetRowCount

Recupera el número actual de filas de un control de ficha.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de filas de las fichas del control de pestaña.

### <a name="remarks"></a>Observaciones

Solo los controles de ficha que tienen el estilo de TCS_MULTILINE pueden tener varias filas de pestañas.

##  <a name="gettooltips"></a>CTabCtrl:: GetToolTips

Recupera el identificador del control de información sobre herramientas asociado a un control de ficha.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del control de información sobre herramientas si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Un control de ficha crea un control de información sobre herramientas si tiene el estilo TCS_TOOLTIPS. También puede asignar un control de información sobre herramientas a un control de ficha mediante la función miembro `SetToolTips`.

##  <a name="highlightitem"></a>CTabCtrl:: HighlightItem

Establece el estado de resaltado de un elemento de ficha.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parámetros

*idItem*<br/>
Índice de base cero de un elemento de control de ficha.

*fHighlight*<br/>
Valor que especifica el estado de resaltado que se va a establecer. Si este valor es TRUE, la pestaña se resalta; Si es FALSE, la pestaña se establece en su estado predeterminado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el [TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="hittest"></a>CTabCtrl:: HitTest

Determina qué pestaña, si la hay, está en la posición de pantalla especificada.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parámetros

*pHitTestInfo*<br/>
Puntero a una estructura [TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) , como se describe en el Windows SDK, que especifica la posición de la pantalla que se va a probar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice de base cero de la pestaña o-1 si no hay ninguna tabulación en la posición especificada.

##  <a name="insertitem"></a>CTabCtrl:: InsertItem

Inserta una nueva pestaña en un control de pestaña existente.

```
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam,
    DWORD dwState,
    DWORD dwStateMask);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero de la nueva pestaña.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) que especifica los atributos de la pestaña.

*lpszItem*<br/>
Dirección de una cadena terminada en null que contiene el texto de la pestaña.

*nImage*<br/>
Índice de base cero de una imagen que se va a insertar de una lista de imágenes.

*nMask*<br/>
Especifica los atributos de estructura `TCITEM` que se van a establecer. Puede ser cero o una combinación de los siguientes valores:

- TCIF_TEXT el miembro de `pszText` es válido.

- TCIF_IMAGE el miembro de `iImage` es válido.

- TCIF_PARAM el miembro *lParam* es válido.

- TCIF_RTLREADING el texto de `pszText` se muestra utilizando el orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.

- TCIF_STATE el miembro *dwState* es válido.

*lParam*<br/>
Datos definidos por la aplicación asociados a la pestaña.

*dwState*<br/>
Especifica valores para los Estados del elemento. Para obtener más información, vea [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) en el Windows SDK.

*dwStateMask*<br/>
Especifica los Estados que se van a establecer. Para obtener más información, vea [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la nueva pestaña si se realiza correctamente; de lo contrario,-1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl:: RemoveImage

Quita la imagen especificada de la lista de imágenes de un control de ficha.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen que se va a quitar.

### <a name="remarks"></a>Observaciones

El control de pestaña actualiza el índice de la imagen de cada pestaña para que cada pestaña permanezca asociada a la misma imagen.

##  <a name="setcurfocus"></a>CTabCtrl:: SetCurFocus

Establece el foco en una pestaña especificada de un control de ficha.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Especifica el índice de la pestaña que obtiene el foco.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setcursel"></a>CTabCtrl:: SetCurSel

Selecciona una pestaña en un control de ficha.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento que se va a seleccionar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña seleccionada anteriormente, si es correcto; de lo contrario,-1.

### <a name="remarks"></a>Observaciones

Un control de ficha no envía un mensaje de notificación TCN_SELCHANGING o TCN_SELCHANGE cuando se selecciona una ficha mediante esta función. Estas notificaciones se envían, utilizando WM_NOTIFY, cuando el usuario hace clic o usa el teclado para cambiar las pestañas.

##  <a name="setextendedstyle"></a>CTabCtrl:: SetExtendedStyle

Establece los estilos extendidos para un control de ficha.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwNewStyle*<br/>
Valor que especifica una combinación de estilos extendidos de control de pestaña.

*dwExMask*<br/>
Un valor DWORD que indica qué estilos de *dwNewStyle* se van a ver afectados. Solo se cambiarán los estilos extendidos de *dwExMask* . El resto de los estilos se conservarán tal y como están. Si este parámetro es cero, se verán afectados todos los estilos de *dwNewStyle* .

### <a name="return-value"></a>Valor devuelto

Valor DWORD que contiene los [estilos extendidos del control de pestaña](/windows/win32/Controls/tab-control-extended-styles)anterior, tal y como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setimagelist"></a>CTabCtrl:: SetImageList

Asigna una lista de imágenes a un control de ficha.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a la lista de imágenes que se va a asignar al control de ficha.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la lista de imágenes anterior o NULL si no hay ninguna lista de imágenes anterior.

##  <a name="setitem"></a>CTabCtrl:: SetItem

Establece algunos o todos los atributos de una pestaña.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) que contiene los nuevos atributos de elemento. El miembro `mask` especifica los atributos que se van a establecer. Si el miembro `mask` especifica el valor TCIF_TEXT, el miembro `pszText` es la dirección de una cadena terminada en NULL y se omite el miembro `cchTextMax`.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetItem](#getitem).

##  <a name="setitemextra"></a>CTabCtrl:: SetItemExtra

Establece el número de bytes por pestaña reservado para los datos definidos por la aplicación en un control de ficha.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
Número de bytes adicionales que se van a establecer.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setitemsize"></a>CTabCtrl:: SetItemSize

Establece el ancho y alto de los elementos de control de pestaña.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
El nuevo ancho y alto, en píxeles, de los elementos de control de pestaña.

### <a name="return-value"></a>Valor devuelto

Devuelve el ancho y el alto antiguos de los elementos de control de pestaña.

##  <a name="setitemstate"></a>CTabCtrl:: SetItemState

Establece el estado del elemento de control de pestaña identificado por *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Número de índice de base cero del elemento para el que se va a establecer información de estado.

*dwMask*<br/>
Máscara que especifica las marcas de estado del elemento que se van a establecer. Para obtener una lista de valores, vea el miembro Mask de la estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) , como se describe en el Windows SDK.

*dwState*<br/>
Referencia a un valor DWORD que contiene la información de estado. Puede ser uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de pestaña.|
|TCIS_HIGHLIGHTED|Se resalta el elemento de control de pestaña y la pestaña y el texto se dibujan con el color de resaltado actual. Al usar el color de resaltado, se trata de una interpolación verdadera, no de un color interpolado.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setmintabwidth"></a>CTabCtrl:: SetMinTabWidth

Establece el ancho mínimo de los elementos de un control de ficha.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parámetros

*serie*<br/>
Ancho mínimo que se va a establecer para un elemento de control de pestaña. Si este parámetro se establece en-1, el control usará el ancho de tabulación predeterminado.

### <a name="return-value"></a>Valor devuelto

El ancho mínimo de tabulación anterior.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del [TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)de mensajes de Win32, como se describe en el Windows SDK.

##  <a name="setpadding"></a>CTabCtrl:: SetPadding

Establece la cantidad de espacio (relleno) alrededor de la etiqueta y el icono de cada pestaña en un control de ficha.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Establece la cantidad de espacio (relleno) alrededor de la etiqueta y el icono de cada pestaña en un control de ficha.

##  <a name="settooltips"></a>CTabCtrl:: SetToolTips

Asigna un control de información sobre herramientas a un control de ficha.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Identificador del control de información sobre herramientas.

### <a name="remarks"></a>Observaciones

Puede obtener el control de información sobre herramientas asociado a un control de ficha realizando una llamada a `GetToolTips`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl (clase)](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
