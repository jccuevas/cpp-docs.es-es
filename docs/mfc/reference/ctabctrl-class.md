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
ms.openlocfilehash: 7d4a478b560be686e4da6f6dea623d6058626562
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365963"
---
# <a name="ctabctrl-class"></a>CTabCtrl (clase)

Proporciona la funcionalidad del control de pestaña común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Construye un objeto `CTabCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Calcula el área de visualización de un control de ficha dado un rectángulo de ventana o calcula el rectángulo de ventana que correspondería a un área de visualización determinada.|
|[CTabCtrl::Crear](#create)|Crea un control de ficha y lo `CTabCtrl` adjunta a una instancia de un objeto.|
|[CTabCtrl::CreateEx](#createex)|Crea un control de ficha con los estilos extendidos `CTabCtrl` de Windows especificados y lo asocia a una instancia de un objeto.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Quita todos los elementos de un control de ficha.|
|[CTabCtrl::DeleteItem](#deleteitem)|Quita un elemento de un control de ficha.|
|[CTabCtrl::DeselectAll](#deselectall)|Restablece los elementos de un control de ficha, borrando los que se presionaron.|
|[CTabCtrl::DrawItem](#drawitem)|Dibuja un elemento especificado de un control de ficha.|
|[CTabCtrl::GetcurFocus](#getcurfocus)|Recupera la pestaña con el foco actual de un control de ficha.|
|[CTabCtrl::GetCurSel](#getcursel)|Determina la pestaña seleccionada actualmente en un control de ficha.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están actualmente en uso para el control de ficha.|
|[CTabCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control de ficha.|
|[CTabCtrl::GetItem](#getitem)|Recupera información sobre una pestaña en un control de ficha.|
|[CTabCtrl::GetItemCount](#getitemcount)|Recupera el número de pestañas en el control de ficha.|
|[CTabCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de una ficha en un control de ficha.|
|[CTabCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de ficha indicado.|
|[CTabCtrl::GetRowCount](#getrowcount)|Recupera el número actual de filas de pestañas en un control de ficha.|
|[CTabCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de información sobre herramientas asociado a un control de ficha.|
|[CTabCtrl::HighlightItem](#highlightitem)|Establece el estado de resaltado de un elemento de ficha.|
|[CTabCtrl::HitTest](#hittest)|Determina qué ficha, si existe, se encuentra en una posición de pantalla especificada.|
|[CTabCtrl::InsertItem](#insertitem)|Inserta una nueva pestaña en un control de ficha.|
|[CTabCtrl::RemoveImage](#removeimage)|Quita una imagen de la lista de imágenes de un control de ficha.|
|[CTabCtrl::SetcurFocus](#setcurfocus)|Establece el foco en una pestaña especificada en un control de ficha.|
|[CTabCtrl::SetCurSel](#setcursel)|Selecciona una pestaña en un control de ficha.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para un control de ficha.|
|[CTabCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de ficha.|
|[CTabCtrl::SetItem](#setitem)|Establece algunos o todos los atributos de una pestaña.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Establece el número de bytes por ficha reservados para los datos definidos por la aplicación en un control de ficha.|
|[CTabCtrl::SetItemSize](#setitemsize)|Establece el ancho y el alto de un elemento.|
|[CTabCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de ficha indicado.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Establece el ancho mínimo de los elementos en un control de ficha.|
|[CTabCtrl::SetPadding](#setpadding)|Establece la cantidad de espacio (relleno) alrededor del icono y la etiqueta de cada ficha en un control de ficha.|
|[CTabCtrl::SetToolTips](#settooltips)|Asigna un control de información sobre herramientas a un control de ficha.|

## <a name="remarks"></a>Observaciones

Un "control de pestañas" es análogo a los divisores de un bloc de notas o a las etiquetas de un archivador. Mediante el uso de un control de ficha, una aplicación puede definir varias páginas para la misma área de un cuadro de diálogo o de una ventana. Cada página consta de un conjunto de información o un grupo de controles que la aplicación muestra cuando el usuario selecciona la pestaña correspondiente. Un tipo especial de control de pestañas muestra pestañas que parecen botones. Al hacer clic en un botón debe realizar inmediatamente un comando en lugar de mostrar una página.

Este control (y, por lo tanto, la `CTabCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más `CTabCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CTabCtrl::AdjustRect

Calcula el área de visualización de un control de ficha dado un rectángulo de ventana o calcula el rectángulo de ventana que correspondería a un área de visualización determinada.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*bLarger*<br/>
Indica qué operación realizar. Si este parámetro es TRUE, *lpRect* especifica un rectángulo de visualización y recibe el rectángulo de ventana correspondiente. Si este parámetro es FALSE, *lpRect* especifica un rectángulo de ventana y recibe el rectángulo de visualización correspondiente.

*lpRect*<br/>
Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que especifica el rectángulo especificado y recibe el rectángulo calculado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::Crear

Crea un control de ficha y lo `CTabCtrl` adjunta a una instancia de un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de ficha. Aplique cualquier combinación de estilos de control de [pestañas,](/windows/win32/Controls/tab-control-styles)que se describe en el Windows SDK. Consulte **Comentarios** para obtener una lista de estilos de ventana que también puede aplicar al control.

*Rect*<br/>
Especifica el tamaño y la posición del control de ficha. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`de ficha, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de ficha.

### <a name="return-value"></a>Valor devuelto

TRUESi la inicialización del objeto se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Construir un `CTabCtrl` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CTabCtrl` llame a , que crea el control de ficha y lo adjunta al objeto.

Además de los estilos de control de ficha, puede aplicar los siguientes estilos de ventana a un control de ficha:

- WS_CHILD Crea una ventana secundaria que representa el control de ficha. No se puede utilizar con el estilo WS_POPUP.

- WS_VISIBLE Crea un control de ficha que está visible inicialmente.

- WS_DISABLED Crea una ventana que está deshabilitada inicialmente.

- WS_GROUP Especifica el primer control de un grupo de controles en el que el usuario puede pasar de un control al siguiente con las teclas de flecha. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo de estilos e inicia el siguiente grupo (es decir, un grupo termina donde comienza el siguiente).

- WS_TABSTOP Especifica uno de los controles a través de los cuales el usuario puede mover mediante la tecla TAB. La tecla TAB mueve al usuario al siguiente control especificado por el estilo WS_TABSTOP.

Para crear un control de ficha con estilos de ventana `Create`extendidos, llame a [CTabCtrl::CreateEx](#createex) en lugar de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::CreateEx

Crea un control (una ventana secundaria) `CTabCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de ficha. Aplique cualquier combinación de estilos de control de [pestañas,](/windows/win32/Controls/tab-control-styles)que se describe en el Windows SDK. Consulte **Comentarios** en [Crear](#create) para obtener una lista de estilos de ventana que también puede aplicar al control.

*Rect*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente 0.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

`CreateEx`crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Establezca estilos extendidos específicos de un control mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, `CreateEx` se utiliza para establecer `SetExtendedStyle` estilos como WS_EX_CONTEXTHELP, pero se usa para establecer estilos como TCS_EX_FLATSEPARATORS. Para obtener más información, vea los estilos descritos en [Estilos extendidos](/windows/win32/Controls/tab-control-extended-styles) de control de ficha en el Windows SDK.

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CTabCtrl::CTabCtrl

Construye un objeto `CTabCtrl`.

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAllItems

Quita todos los elementos de un control de ficha.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::DeleteItem

Quita el elemento especificado de un control de ficha.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Valor de base cero del elemento que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::DeselectAll

Restablece los elementos de un control de ficha, borrando los que se presionaron.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parámetros

*fExcludeFocus*<br/>
Marcador que especifica el ámbito de la deselección del elemento. Si este parámetro se establece en FALSE, se restablecerán todos los botones de tabulación. Si se establece en TRUE, se restablecerán todos los elementos de ficha excepto el seleccionado actualmente.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32, [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall), como se describe en el Windows SDK.

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CTabCtrl::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un control de ficha dibujada por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que describe el elemento que se va a pintar.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalidar esta función miembro para implementar `CTabCtrl` el dibujo para un objeto de dibujo del propietario.

La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que finalice esta función miembro.

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CTabCtrl::GetcurFocus

Recupera el índice de la pestaña con el foco actual.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la pestaña con el foco actual.

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CTabCtrl::GetCurSel

Recupera la pestaña seleccionada actualmente en un control de ficha.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la pestaña seleccionada si se realiza correctamente o - 1 si no se selecciona ninguna ficha.

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTabCtrl::GetExtendedStyle

Recupera los estilos extendidos que están actualmente en uso para el control de ficha.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valor devuelto

Representa los estilos extendidos actualmente en uso para el control de ficha. Este valor es una combinación de [estilos extendidos](/windows/win32/Controls/tab-control-extended-styles)de control de ficha, como se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle), como se describe en el Windows SDK.

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl::GetImageList

Recupera la lista de imágenes asociada a un control de pestaña.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, puntero a la lista de imágenes del control de pestaña; de lo contrario, NULL.

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl::GetItem

Recupera información sobre una pestaña en un control de ficha.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El índice de base cero de la pestaña.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) que se utiliza para especificar la información que se va a recuperar. También se utiliza para recibir información sobre la pestaña. Esta estructura se `InsertItem`utiliza `GetItem`con `SetItem` las funciones , , y miembro.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE en caso contrario.

### <a name="remarks"></a>Observaciones

Cuando se envía el `mask` mensaje, el miembro especifica los atributos que se devolverán. Si `mask` el miembro especifica el `pszText` TCIF_TEXT valor, el miembro debe contener la dirección `cchTextMax` del búfer que recibe el texto del elemento y el miembro debe especificar el tamaño del búfer.

- `mask`

   Valor que `TCITEM` especifica qué miembros de estructura se van a recuperar o establecer. Este miembro puede ser cero o una combinación de los siguientes valores:

  - TCIF_TEXT `pszText` El miembro es válido.

  - TCIF_IMAGE `iImage` El miembro es válido.

  - TCIF_PARAM `lParam` El miembro es válido.

  - TCIF_RTLREADING El `pszText` texto de se muestra utilizando el orden de lectura de derecha a izquierda en sistemas hebreos o árabes.

  - TCIF_STATE `dwState` El miembro es válido.

- `pszText`

   Puntero a una cadena terminada en null que contiene el texto de la ficha si la estructura contiene información sobre una ficha. Si la estructura está recibiendo información, este miembro especifica la dirección del búfer que recibe el texto de la ficha.

- `cchTextMax`

   Tamaño del búfer al `pszText`que apunta . Este miembro se omite si la estructura no está recibiendo información.

- `iImage`Indexe en la lista de imágenes del control de pestañas o - 1 si no hay ninguna imagen para la pestaña.

- `lParam`

   Datos definidos por la aplicación asociados a la pestaña. Si hay más de cuatro bytes de datos definidos por la aplicación por `TCITEM` ficha, una aplicación debe definir una estructura y usarla en lugar de la estructura. El primer miembro de la estructura definida por la aplicación debe ser una estructura [TCITEMHEADER.](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw) La `TCITEMHEADER` estructura es `TCITEM` idéntica a la `lParam` estructura, pero sin el miembro. La diferencia entre el tamaño de la `TCITEMHEADER` estructura y el tamaño de la estructura debe ser igual al número de bytes adicionales por pestaña.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::GetItemCount

Recupera el número de pestañas en el control de ficha.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos en el control de ficha.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::GetItemRect

Recupera el rectángulo delimitador de la pestaña especificada en un control de ficha.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El índice de base cero del elemento de ficha.

*lpRect*<br/>
Puntero a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que recibe el rectángulo delimitador de la pestaña. Estas coordenadas utilizan el modo de asignación actual de la ventana gráfica.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::GetItemState

Recupera el estado del elemento de control de ficha identificado por *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El número de índice de base cero del elemento para el que se va a recuperar información de estado.

*dwMask*<br/>
Máscara que especifica cuál de los indicadores de estado del elemento se va a devolver. Para obtener una lista de valores, vea el miembro de máscara de la estructura [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Una referencia a un valor DWORD que recibe la información de estado. Puede ser uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de ficha.|
|TCIS_HIGHLIGHTED|El elemento de control de ficha se resalta y la pestaña y el texto se dibujan con el color de resaltado actual. Cuando se utiliza el color de resaltado, esto será una interpolación verdadera, no un color tramado.|

### <a name="remarks"></a>Observaciones

El estado de un elemento `dwState` lo especifica `TCITEM` el miembro de la estructura.

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CTabCtrl::GetRowCount

Recupera el número actual de filas en un control de ficha.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de filas de pestañas en el control de ficha.

### <a name="remarks"></a>Observaciones

Solo los controles de ficha que tienen el estilo TCS_MULTILINE pueden tener varias filas de pestañas.

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl::GetToolTips

Recupera el identificador del control de información sobre herramientas asociado a un control de ficha.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Mango del control de información sobre herramientas si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Un control de ficha crea un control de información sobre herramientas si tiene el estilo de TCS_TOOLTIPS. También puede asignar un control de información sobre `SetToolTips` herramientas a un control de ficha mediante la función miembro.

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::HighlightItem

Establece el estado de resaltado de un elemento de ficha.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parámetros

*idItem*<br/>
El índice de base cero de un elemento de control de ficha.

*fHighlight*<br/>
Valor que especifica el estado de resaltado que se va a establecer. Si este valor es TRUE, se resalta la pestaña; si FALSE, la pestaña se establece en su estado predeterminado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el [mensaje Win32 TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem), como se describe en el Windows SDK.

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CTabCtrl::HitTest

Determina qué ficha, si existe, se encuentra en la posición de pantalla especificada.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parámetros

*pHitTestInfo*<br/>
Puntero a una estructura [TCHITTESTINFO,](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo) como se describe en el Windows SDK, que especifica la posición de pantalla que se va a probar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice de base cero de la ficha o - 1 si no hay ninguna ficha en la posición especificada.

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::InsertItem

Inserta una nueva pestaña en un control de ficha existente.

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
El índice de base cero de la nueva pestaña.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) que especifica los atributos de la ficha.

*lpszItem*<br/>
Dirección de una cadena terminada en null que contiene el texto de la pestaña.

*nImage*<br/>
El índice de base cero de una imagen que se va a insertar en una lista de imágenes.

*nMask*<br/>
Especifica los `TCITEM` atributos de estructura que se deben establecer. Puede ser cero o una combinación de los siguientes valores:

- TCIF_TEXT `pszText` El miembro es válido.

- TCIF_IMAGE `iImage` El miembro es válido.

- TCIF_PARAM El *lParam* miembro es válido.

- TCIF_RTLREADING El `pszText` texto de se muestra utilizando el orden de lectura de derecha a izquierda en sistemas hebreos o árabes.

- TCIF_STATE El miembro *dwState* es válido.

*lParam*<br/>
Datos definidos por la aplicación asociados a la pestaña.

*dwState*<br/>
Especifica los valores de los estados del elemento. Para obtener más información, consulte [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) en el Windows SDK.

*dwStateMask*<br/>
Especifica qué estados se deben establecer. Para obtener más información, consulte [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la nueva pestaña si se realiza correctamente; de lo contrario - 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::RemoveImage

Quita la imagen especificada de la lista de imágenes de un control de ficha.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
El índice de base cero de la imagen que se va a eliminar.

### <a name="remarks"></a>Observaciones

El control de ficha actualiza el índice de imagen de cada ficha para que cada ficha permanezca asociada a la misma imagen.

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CTabCtrl::SetcurFocus

Establece el foco en una pestaña especificada en un control de ficha.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Especifica el índice de la pestaña que obtiene el foco.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus), como se describe en el Windows SDK.

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CTabCtrl::SetCurSel

Selecciona una pestaña en un control de ficha.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El índice de base cero del elemento que se va a seleccionar.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la pestaña seleccionada anteriormente si se realiza correctamente, de lo contrario - 1.

### <a name="remarks"></a>Observaciones

Un control de ficha no envía un TCN_SELCHANGING o TCN_SELCHANGE mensaje de notificación cuando se selecciona una ficha mediante esta función. Estas notificaciones se envían, mediante WM_NOTIFY, cuando el usuario hace clic o utiliza el teclado para cambiar las pestañas.

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTabCtrl::SetExtendedStyle

Establece los estilos extendidos para un control de ficha.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwNewStyle*<br/>
Valor que especifica una combinación de estilos extendidos de control de ficha.

*dwExMask*<br/>
Un valor DWORD que indica qué estilos de *dwNewStyle* se van a ver afectados. Solo se cambiarán los estilos extendidos en *dwExMask.* Todos los demás estilos se mantendrán tal como está. Si este parámetro es cero, todos los estilos de *dwNewStyle* se verán afectados.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene los [estilos extendidos](/windows/win32/Controls/tab-control-extended-styles)de control de ficha anterior, como se describe en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle), como se describe en el Windows SDK.

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::SetImageList

Asigna una lista de imágenes a un control de ficha.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a la lista de imágenes que se asignará al control de ficha.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la lista de imágenes anterior o NULL si no hay ninguna lista de imágenes anterior.

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::SetItem

Establece algunos o todos los atributos de una pestaña.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El índice de base cero del elemento.

*pTabCtrlItem*<br/>
Puntero a una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) que contiene los nuevos atributos de elemento. El `mask` miembro especifica los atributos que se deben establecer. Si `mask` el miembro especifica el `pszText` valor TCIF_TEXT, el miembro es la `cchTextMax` dirección de una cadena terminada en null y se omite el miembro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetItem](#getitem).

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::SetItemExtra

Establece el número de bytes por ficha reservados para los datos definidos por la aplicación en un control de ficha.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
El número de bytes adicionales que se van a establecer.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/tcm-setitemextra)Win32 TCM_SETITEMEXTRA , como se describe en el Windows SDK.

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::SetItemSize

Establece el ancho y alto de los elementos de control de pestaña.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
El nuevo ancho y alto, en píxeles, de los elementos de control de pestaña.

### <a name="return-value"></a>Valor devuelto

Devuelve el ancho y el alto antiguos de los elementos de control de pestaña.

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::SetItemState

Establece el estado del elemento de control de ficha identificado por *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El número de índice de base cero del elemento para el que se va a establecer la información de estado.

*dwMask*<br/>
Máscara que especifica cuál de los indicadores de estado del elemento se va a establecer. Para obtener una lista de valores, vea el miembro de máscara de la estructura [TCITEM,](/windows/win32/api/commctrl/ns-commctrl-tcitemw) como se describe en el Windows SDK.

*dwState*<br/>
Una referencia a un valor DWORD que contiene la información de estado. Puede ser uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de ficha.|
|TCIS_HIGHLIGHTED|El elemento de control de ficha se resalta y la pestaña y el texto se dibujan con el color de resaltado actual. Cuando se utiliza el color de resaltado, esto será una interpolación verdadera, no un color tramado.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::SetMinTabWidth

Establece el ancho mínimo de los elementos en un control de ficha.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parámetros

*Cx*<br/>
Ancho mínimo que se establecerá para un elemento de control de ficha. Si este parámetro se establece en -1, el control usará el ancho de tabulación predeterminado.

### <a name="return-value"></a>Valor devuelto

El ancho de tabulación mínimo anterior.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/tcm-setmintabwidth)Win32 TCM_SETMINTABWIDTH , como se describe en el Windows SDK.

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::SetPadding

Establece la cantidad de espacio (relleno) alrededor del icono y la etiqueta de cada ficha en un control de ficha.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
Establece la cantidad de espacio (relleno) alrededor del icono y la etiqueta de cada ficha en un control de ficha.

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::SetToolTips

Asigna un control de información sobre herramientas a un control de ficha.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Mango del control de la punta de la herramienta.

### <a name="remarks"></a>Observaciones

Puede obtener el control de información sobre herramientas asociado `GetToolTips`a un control de ficha realizando una llamada a .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Consulte también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl (clase)](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
