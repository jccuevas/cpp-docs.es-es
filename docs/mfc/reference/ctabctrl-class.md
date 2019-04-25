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
ms.openlocfilehash: ccf35c7a036a69487d5138baf8c017f9c5995bef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323718"
---
# <a name="ctabctrl-class"></a>CTabCtrl (clase)

Proporciona la funcionalidad del control de pestaña común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CTabCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CTabCtrl::CTabCtrl](#ctabctrl)|Construye un objeto `CTabCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTabCtrl::AdjustRect](#adjustrect)|Calcula el área de presentación de un control de ficha dado un rectángulo de la ventana, o calcula el rectángulo de ventana que corresponde a un área de presentación determinado.|
|[CTabCtrl::Create](#create)|Crea un control de ficha y lo asocia a una instancia de un `CTabCtrl` objeto.|
|[CTabCtrl::CreateEx](#createex)|Crea un control de ficha con los estilos extendidos de Windows especificados y lo asocia a una instancia de un `CTabCtrl` objeto.|
|[CTabCtrl::DeleteAllItems](#deleteallitems)|Quita todos los elementos de un control de ficha.|
|[CTabCtrl::DeleteItem](#deleteitem)|Quita un elemento de un control de ficha.|
|[CTabCtrl::DeselectAll](#deselectall)|Restablece los elementos de un control de ficha, desactivación que se presionaron.|
|[CTabCtrl::DrawItem](#drawitem)|Dibuja un elemento especificado de un control de ficha.|
|[CTabCtrl::GetCurFocus](#getcurfocus)|Recupera la ficha con el foco actual de un control de ficha.|
|[CTabCtrl::GetCurSel](#getcursel)|Determina la pestaña seleccionada actualmente en un control de ficha.|
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están actualmente en uso para el control de ficha.|
|[CTabCtrl::GetImageList](#getimagelist)|Recupera la lista de imágenes asociada a un control de ficha.|
|[CTabCtrl::GetItem](#getitem)|Recupera información sobre una pestaña en un control de ficha.|
|[CTabCtrl::GetItemCount](#getitemcount)|Recupera el número de fichas del control de ficha.|
|[CTabCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador para una pestaña en un control de ficha.|
|[CTabCtrl::GetItemState](#getitemstate)|Recupera el estado del elemento de control de ficha indicado.|
|[CTabCtrl::GetRowCount](#getrowcount)|Recupera el número actual de filas de pestañas en un control de ficha.|
|[CTabCtrl::GetToolTips](#gettooltips)|Recupera el identificador del control de sugerencia de herramienta asociado a un control de ficha.|
|[CTabCtrl::HighlightItem](#highlightitem)|Establece el estado de resaltado de un elemento de ficha.|
|[CTabCtrl::HitTest](#hittest)|Determina qué ficha, si existe, está en una posición de pantalla especificada.|
|[CTabCtrl::InsertItem](#insertitem)|Inserta una nueva pestaña en un control de ficha.|
|[CTabCtrl::RemoveImage](#removeimage)|Quita una imagen de la lista de imágenes de un control de ficha.|
|[CTabCtrl::SetCurFocus](#setcurfocus)|Establece el foco en una pestaña especificada en un control de ficha.|
|[CTabCtrl::SetCurSel](#setcursel)|Selecciona una ficha en un control de ficha.|
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos para un control de ficha.|
|[CTabCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de ficha.|
|[CTabCtrl::SetItem](#setitem)|Establece algunos o todos los atributos de la ficha.|
|[CTabCtrl::SetItemExtra](#setitemextra)|Establece el número de bytes por ficha reservado para los datos definidos por la aplicación en un control de ficha.|
|[CTabCtrl::SetItemSize](#setitemsize)|Establece el ancho y alto de un elemento.|
|[CTabCtrl::SetItemState](#setitemstate)|Establece el estado del elemento de control de ficha indicado.|
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|Establece el ancho mínimo de elementos en un control de ficha.|
|[CTabCtrl::SetPadding](#setpadding)|Establece la cantidad de espacio (relleno) alrededor de cada ficha icono y una etiqueta en un control de ficha.|
|[CTabCtrl::SetToolTips](#settooltips)|Asigna un control a un control de ficha.|

## <a name="remarks"></a>Comentarios

Un "control de ficha" es análogo a los divisores de un bloc de notas o las etiquetas de un archivador. Mediante el uso de un control de ficha, una aplicación puede definir varias páginas para la misma área de un cuadro de diálogo o de una ventana. Cada página consta de un conjunto de información o un grupo de controles que la aplicación se muestra cuando el usuario selecciona la pestaña correspondiente. Un tipo especial de control de ficha muestra las pestañas que se parecen a los botones. Al hacer clic en un botón debe realizar inmediatamente un comando en lugar de mostrar una página.

Este control (y, por tanto, la `CTabCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para obtener más información sobre el uso de `CTabCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CTabCtrl](../../mfc/using-ctabctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect

Calcula el área de presentación de un control de ficha dado un rectángulo de la ventana, o calcula el rectángulo de ventana que corresponde a un área de presentación determinado.

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*bLarger*<br/>
Indica qué operación debe realizarse. Si este parámetro es TRUE, *lpRect* especifica un rectángulo de presentación y recibe el rectángulo de la ventana correspondiente. Si este parámetro es FALSE, *lpRect* especifica un rectángulo de la ventana y recibe el rectángulo de presentación correspondiente.

*lpRect*<br/>
Puntero a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que especifica el rectángulo especificado y recibe el rectángulo calculado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>  CTabCtrl::Create

Crea un control de ficha y lo asocia a una instancia de un `CTabCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de ficha. Aplicar cualquier combinación de [estilos de control de pestaña](/windows/desktop/Controls/tab-control-styles), que se describen en el SDK de Windows. Consulte **comentarios** para obtener una lista de estilos de ventana que también se pueden aplicar al control.

*rect*<br/>
Especifica el tamaño y la posición del control de ficha. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control de ficha, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de ficha

### <a name="return-value"></a>Valor devuelto

TRUE si la inicialización del objeto se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Construir un `CTabCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de pestaña y lo adjunta a la `CTabCtrl` objeto.

Además de los estilos de control de ficha, puede aplicar los siguientes estilos de ventana para un control de ficha:

- WS_CHILD crea una ventana secundaria que representa el control de ficha. No se puede usar con el estilo WS_POPUP.

- WS_VISIBLE crea un control de ficha que se muestra inicialmente.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente.

- WS_GROUP especifica el primer control de un grupo de controles en el que el usuario puede mover de un control a la siguiente con las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El control siguiente con el estilo WS_GROUP finaliza el grupo estilo e inicia el grupo siguiente (es decir, un grupo termina donde comienza el siguiente).

- Especifica WS_TABSTOP uno de cualquier número de controles a través del cual el usuario puede mover mediante la tecla TAB. La tecla TAB mueve el usuario en el control siguiente especificado por el estilo WS_TABSTOP.

Para crear un control de ficha con estilos de ventana extendidos, llame a [CTabCtrl::CreateEx](#createex) en lugar de `Create`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>  CTabCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia a la `CTabCtrl` objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Especifica el estilo del control de ficha. Aplicar cualquier combinación de [estilos de control de pestaña](/windows/desktop/Controls/tab-control-styles), que se describen en el SDK de Windows. Consulte **comentarios** en [crear](#create) para obtener una lista de estilos de ventana que también se pueden aplicar al control.

*rect*<br/>
Una referencia a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

0 en caso contrario, es distinto de cero si se realiza correctamente.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

`CreateEx` crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Conjunto específico de un control mediante estilos extendidos [SetExtendedStyle](#setextendedstyle). Por ejemplo, usar `CreateEx` para establecer estos estilos como WS_EX_CONTEXTHELP, pero usa `SetExtendedStyle` para establecer estos estilos como TCS_EX_FLATSEPARATORS. Para obtener más información, vea los estilos que se describe en [estilos extendidos de Control de ficha](/windows/desktop/Controls/tab-control-extended-styles) en el SDK de Windows.

##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl

Construye un objeto `CTabCtrl`.

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems

Quita todos los elementos de un control de ficha.

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem

Quita el elemento especificado de un control de ficha.

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Valor de base cero del elemento que desea eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>  CTabCtrl::DeselectAll

Restablece los elementos de un control de ficha, desactivación que se presionaron.

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>Parámetros

*fExcludeFocus*<br/>
Marca que especifica el ámbito de la desactivación del elemento. Si este parámetro se establece en FALSE, se restablecerán todos los botones de ficha. Si se establece en TRUE, a continuación, la pestaña todos los elementos excepto actualmente seleccionada se restablecerá.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32, [TCM_DESELECTALL](/windows/desktop/Controls/tcm-deselectall), tal y como se describe en el SDK de Windows.

##  <a name="drawitem"></a>  CTabCtrl::DrawItem

Lo llama el marco cuando un aspecto visual de un cambios de control de ficha dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) estructura que describe el elemento que se pinta.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.

De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujado por el propietario del dibujo `CTabCtrl` objeto.

La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de este miembro de la función termina.

##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus

Recupera el índice de la pestaña con el foco actual.

```
int GetCurFocus() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña con el foco actual.

##  <a name="getcursel"></a>  CTabCtrl::GetCurSel

Recupera la pestaña seleccionada actualmente en un control de ficha.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña seleccionada si es correcto o - 1 si no se selecciona ninguna pestaña.

##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle

Recupera los estilos extendidos que están actualmente en uso para el control de ficha.

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>Valor devuelto

Representa los estilos extendidos actualmente en uso para el control de ficha. Este valor es una combinación de [estilos extendidos de control de pestaña](/windows/desktop/Controls/tab-control-extended-styles), tal y como se describe en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_GETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-getextendedstyle), tal y como se describe en el SDK de Windows.

##  <a name="getimagelist"></a>  CTabCtrl::GetImageList

Recupera la lista de imágenes asociada a un control de pestaña.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, un puntero a la lista de imágenes de la pestaña de control; en caso contrario, es NULL.

##  <a name="getitem"></a>  CTabCtrl::GetItem

Recupera información sobre una pestaña en un control de ficha.

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero de la pestaña.

*pTabCtrlItem*<br/>
Puntero a un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura que se utiliza para especificar la información para recuperar. También se usa para recibir información acerca de la pestaña. Esta estructura se usa con el `InsertItem`, `GetItem`, y `SetItem` funciones miembro.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se realiza correctamente; FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Cuando se envía el mensaje, el `mask` miembro especifica qué atributos se devolverán. Si el `mask` miembro especifica el valor de TCIF_TEXT el `pszText` miembro debe contener la dirección del búfer que recibe el texto del elemento y el `cchTextMax` miembro debe especificar el tamaño del búfer.

- `mask`

   Valor que especifica qué `TCITEM` estructurar los miembros para recuperar o establecer. Este miembro puede ser cero o una combinación de los siguientes valores:

   - TCIF_TEXT el `pszText` miembro es válido.

   - TCIF_IMAGE el `iImage` miembro es válido.

   - TCIF_PARAM el `lParam` miembro es válido.

   - TCIF_RTLREADING el texto de `pszText` se muestra con orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.

   - TCIF_STATE el `dwState` miembro es válido.

- `pszText`

   Puntero a una cadena terminada en null que contiene el texto de ficha si la estructura contiene información sobre una pestaña. Si está recibiendo información de la estructura, este miembro especifica la dirección del búfer que recibe el texto de ficha.

- `cchTextMax`

   Tamaño del búfer señalado por `pszText`. Este miembro se omite si la estructura no está recibiendo información.

- `iImage` Índice en el control de pestaña lista de imágenes, o - 1 si no hay ninguna imagen de la pestaña.

- `lParam`

   Datos definido por la aplicación asociados a la pestaña. Si hay más de cuatro bytes de datos definido por la aplicación por tabulación, una aplicación debe definir una estructura y, en lugar de usar el `TCITEM` estructura. El primer miembro de la estructura definida por la aplicación debe ser un [TCITEMHEADER](/windows/desktop/api/commctrl/ns-commctrl-tagtcitemheadera)estructura. El `TCITEMHEADER` estructura es idéntica a la `TCITEM` estructura, pero sin la `lParam` miembro. La diferencia entre el tamaño de la estructura y el tamaño de la `TCITEMHEADER` estructura es igual al número de bytes adicionales por ficha.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount

Recupera el número de fichas del control de ficha.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos en el control de ficha.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect

Recupera el rectángulo delimitador de la ficha especificada en un control de ficha.

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento de ficha.

*lpRect*<br/>
Puntero a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura que recibe el rectángulo delimitador de la pestaña. Estas coordenadas Usar modo de asignación de la ventanilla actual.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="getitemstate"></a>  CTabCtrl::GetItemState

Recupera el estado del elemento de control de ficha identificado por *nItem*.

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El número de índice de base cero del elemento para el que se va a recuperar la información de estado.

*dwMask*<br/>
Máscara que especifica qué del estado del elemento de marcas para devolver. Para obtener una lista de valores, vea el miembro de la máscara de la [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura, como se describe en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Una referencia a un valor DWORD de recibir la información de estado. Puede presentar uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de ficha.|
|TCIS_HIGHLIGHTED|Se resalta el elemento de control de ficha y la pestaña y el texto se dibujan utilizando el color de resaltado actuales. Cuando se usa el color de resaltado, se trata de una interpolación es true, no un color interpolado.|

### <a name="remarks"></a>Comentarios

Estado de un elemento especificado por el `dwState` miembro de la `TCITEM` estructura.

##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount

Recupera el número actual de filas de un control de ficha.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de filas de pestañas en el control de ficha.

### <a name="remarks"></a>Comentarios

Controles de ficha que tienen el estilo TCS_MULTILINE pueden tener varias filas de pestañas.

##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips

Recupera el identificador del control de sugerencia de herramienta asociado a un control de ficha.

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del control de información sobre herramientas si se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Un control de ficha crea un control si tiene el estilo TCS_TOOLTIPS. También puede asignar un control a un control de ficha mediante el `SetToolTips` función miembro.

##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem

Establece el estado de resaltado de un elemento de ficha.

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>Parámetros

*idItem*<br/>
Índice de base cero de un elemento de control de ficha.

*fHighlight*<br/>
Valor que especifica el estado de resaltado debe establecerse. Si este valor es TRUE, se resalta la pestaña; Si es FALSE, la ficha se establece en su estado predeterminado.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el mensaje de Win32 [TCM_HIGHLIGHTITEM](/windows/desktop/Controls/tcm-highlightitem), tal y como se describe en el SDK de Windows.

##  <a name="hittest"></a>  CTabCtrl::HitTest

Determina qué ficha, si existe, está en la posición de pantalla especificada.

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>Parámetros

*pHitTestInfo*<br/>
Puntero a un [TCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtchittestinfo) estructura, como se describe en el SDK de Windows, que especifica la posición de la pantalla para probar.

### <a name="return-value"></a>Valor devuelto

Devuelve el índice de base cero de la ficha o - 1 si no hay pestaña está en la posición especificada.

##  <a name="insertitem"></a>  CTabCtrl::InsertItem

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
Índice de base cero de la nueva pestaña.

*pTabCtrlItem*<br/>
Puntero a un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura que especifica los atributos de la pestaña.

*lpszItem*<br/>
Dirección de una cadena terminada en null que contiene el texto de la pestaña.

*nImage*<br/>
Índice de base cero de una imagen que se va a insertar en una lista de imágenes.

*nMask*<br/>
Especifica qué `TCITEM` estructura atributos van a establecer. Puede ser cero o una combinación de los siguientes valores:

- TCIF_TEXT el `pszText` miembro es válido.

- TCIF_IMAGE el `iImage` miembro es válido.

- TCIF_PARAM el *lParam* miembro es válido.

- TCIF_RTLREADING el texto de `pszText` se muestra con orden de lectura de derecha a izquierda en los sistemas hebreo o árabe.

- TCIF_STATE el *"_mfc_CTabCtrl.3a3a.GetItem"* miembro es válido.

*lParam*<br/>
Datos definido por la aplicación asociados a la pestaña.

*dwState*<br/>
Especifica los valores de los Estados del elemento. Para obtener más información, consulte [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) en el SDK de Windows.

*dwStateMask*<br/>
Especifica que los Estados que se van a establecer. Para obtener más información, consulte [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la nueva ficha si se realiza correctamente; en caso contrario, - 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>  CTabCtrl::RemoveImage

Quita la imagen especificada de la lista de imágenes de un control de ficha.

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>Parámetros

*nImage*<br/>
Índice de base cero de la imagen para quitar.

### <a name="remarks"></a>Comentarios

El control de ficha actualiza el índice de imagen de cada pestaña para que permanezca asociado con la misma imagen de cada pestaña.

##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus

Establece el foco en una pestaña especificada en un control de ficha.

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Especifica el índice de la pestaña que recibe el foco.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETCURFOCUS](/windows/desktop/Controls/tcm-setcurfocus), tal y como se describe en el SDK de Windows.

##  <a name="setcursel"></a>  CTabCtrl::SetCurSel

Selecciona una ficha en un control de ficha.

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento que se seleccionen.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la pestaña seleccionada anteriormente, si es correcto, en caso contrario, - 1.

### <a name="remarks"></a>Comentarios

Un control de ficha no envía un mensaje de notificación TCN_SELCHANGING o TCN_SELCHANGE cuando se selecciona una ficha utilizando esta función. Estas notificaciones se envían mediante WM_NOTIFY, cuando el usuario hace clic o usa el teclado para cambiar las fichas.

##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle

Establece los estilos extendidos para un control de ficha.

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>Parámetros

*dwNewStyle*<br/>
Valor que especifica una combinación de la pestaña de control estilos extendidos.

*dwExMask*<br/>
Un valor DWORD que indica qué estilos en *dwNewStyle* son se vea afectado. Solo los estilos extendidos en *dwExMask* se cambiará. Todos los demás estilos se conservará tal cual. Si este parámetro es cero, entonces todos los estilos en *dwNewStyle* se verán afectados.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene el texto anterior [estilos extendidos de control de pestaña](/windows/desktop/Controls/tab-control-extended-styles), tal y como se describe en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-setextendedstyle), tal y como se describe en el SDK de Windows.

##  <a name="setimagelist"></a>  CTabCtrl::SetImageList

Asigna una lista de imágenes a un control de ficha.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a la lista de imágenes que se asignará al control de ficha.

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero a la lista de imágenes anteriores o NULL si no hay ninguna lista de la imagen anterior.

##  <a name="setitem"></a>  CTabCtrl::SetItem

Establece algunos o todos los atributos de la ficha.

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del elemento.

*pTabCtrlItem*<br/>
Puntero a un [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura que contiene los atributos del elemento nuevo. El `mask` miembro especifica qué atributos que se van a establecer. Si el `mask` miembro especifica el valor de TCIF_TEXT el `pszText` miembro es la dirección de una cadena terminada en null y el `cchTextMax` miembro se omite.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [GetItem](#getitem).

##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra

Establece el número de bytes por ficha reservado para los datos definidos por la aplicación en un control de ficha.

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>Parámetros

*nBytes*<br/>
El número de bytes adicionales para establecer.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETITEMEXTRA](/windows/desktop/Controls/tcm-setitemextra), tal y como se describe en el SDK de Windows.

##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize

Establece el ancho y alto de los elementos de control de pestaña.

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
El nuevo ancho y alto, en píxeles, de los elementos de control de pestaña.

### <a name="return-value"></a>Valor devuelto

Devuelve el ancho y el alto antiguos de los elementos de control de pestaña.

##  <a name="setitemstate"></a>  CTabCtrl::SetItemState

Establece el estado del elemento de control de ficha identificado por *nItem*.

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
El número de índice de base cero del elemento para el que se va a establecer información de estado.

*dwMask*<br/>
Especifica qué del estado del elemento de marcas para establecer la máscara. Para obtener una lista de valores, vea el miembro de la máscara de la [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura, como se describe en el SDK de Windows.

*dwState*<br/>
Una referencia a un valor DWORD que contiene la información de estado. Puede presentar uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|Se selecciona el elemento de control de ficha.|
|TCIS_HIGHLIGHTED|Se resalta el elemento de control de ficha y la pestaña y el texto se dibujan utilizando el color de resaltado actuales. Cuando se usa el color de resaltado, se trata de una interpolación es true, no un color interpolado.|

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth

Establece el ancho mínimo de elementos en un control de ficha.

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>Parámetros

*cx*<br/>
Ancho mínimo debe establecerse para un elemento de control de ficha. Si este parámetro se establece en -1, el control utilizará el ancho de tabulación predeterminada.

### <a name="return-value"></a>Valor devuelto

El ancho mínimo de pestaña anterior.

### <a name="return-value"></a>Valor devuelto

Esta función miembro implementa el comportamiento del mensaje de Win32 [TCM_SETMINTABWIDTH](/windows/desktop/Controls/tcm-setmintabwidth), tal y como se describe en el SDK de Windows.

##  <a name="setpadding"></a>  CTabCtrl::SetPadding

Establece la cantidad de espacio (relleno) alrededor de cada ficha icono y una etiqueta en un control de ficha.

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Establece la cantidad de espacio (relleno) alrededor de cada ficha icono y una etiqueta en un control de ficha.

##  <a name="settooltips"></a>  CTabCtrl::SetToolTips

Asigna un control a un control de ficha.

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>Parámetros

*pWndTip*<br/>
Identificador del control de información sobre herramientas.

### <a name="remarks"></a>Comentarios

Puede obtener el control de información sobre herramientas asociado con un control de ficha mediante una llamada a `GetToolTips`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl (clase)](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
