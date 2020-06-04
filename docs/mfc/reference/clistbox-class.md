---
title: CListBox (clase)
description: Una descripción de la MFC CListBox clase y sus funciones miembro.
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 171038ebaaed815aa687c200fe3210bde8000be3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753583"
---
# <a name="clistbox-class"></a>CListBox (clase)

Proporciona la funcionalidad de un cuadro de lista de Windows.

## <a name="syntax"></a>Sintaxis

```
class CListBox : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Construye un objeto `CListBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Agrega una cadena a un cuadro de lista.|
|[CListBox::CharToItem](#chartoitem)|Reemplazar para proporcionar control de WM_CHAR personalizado para cuadros de lista dibujados por el propietario que no tienen cadenas.|
|[CListBox::CompareItem](#compareitem)|Llamado por el marco de trabajo para determinar la posición de un nuevo elemento en un cuadro de lista ordenado dibujada por el propietario.|
|[CListBox::Crear](#create)|Crea el cuadro de lista de `CListBox` Windows y lo adjunta al objeto.|
|[CListBox::DeleteItem](#deleteitem)|Llamado por el marco de trabajo cuando el usuario elimina un elemento de un cuadro de lista dibujada por el propietario.|
|[CListBox::DeleteString](#deletestring)|Elimina una cadena de un cuadro de lista.|
|[CListBox::Dir](#dir)|Agrega nombres de archivo, unidades o ambos desde el directorio actual a un cuadro de lista.|
|[CListBox::DrawItem](#drawitem)|Llamado por el marco de trabajo cuando cambia un aspecto visual de un cuadro de lista de dibujo del propietario.|
|[CListBox::FindString](#findstring)|Busca una cadena en un cuadro de lista.|
|[CListBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista que coincide con una cadena especificada.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Recupera el índice de base cero del elemento de anclaje actual en un cuadro de lista.|
|[CListBox::GetCaretIndex](#getcaretindex)|Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.|
|[CListBox::GetCount](#getcount)|Devuelve el número de cadenas de un cuadro de lista.|
|[CListBox::GetCurSel](#getcursel)|Devuelve el índice de base cero de la cadena seleccionada actualmente en un cuadro de lista.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|
|[CListBox::GetItemData](#getitemdata)|Devuelve un valor asociado al elemento de cuadro de lista.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Devuelve un puntero a un elemento de cuadro de lista.|
|[CListBox::GetItemHeight](#getitemheight)|Determina la altura de los elementos de un cuadro de lista.|
|[CListBox::GetItemRect](#getitemrect)|Devuelve el rectángulo delimitador del elemento de cuadro de lista tal como se muestra actualmente.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Recupera el número de elementos por columna.|
|[CListBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro de lista.|
|[CListBox::GetSel](#getsel)|Devuelve el estado de selección de un elemento de cuadro de lista.|
|[CListBox::GetSelCount](#getselcount)|Devuelve el número de cadenas seleccionadas actualmente en un cuadro de lista de selección múltiple.|
|[CListBox::GetSelItems](#getselitems)|Devuelve los índices de las cadenas seleccionadas actualmente en un cuadro de lista.|
|[CListBox::GetText](#gettext)|Copia un elemento de cuadro de lista en un búfer.|
|[CListBox::GetTextLen](#gettextlen)|Devuelve la longitud en bytes de un elemento de cuadro de lista.|
|[CListBox::GetTopIndex](#gettopindex)|Devuelve el índice de la primera cadena visible en un cuadro de lista.|
|[CListBox::InitStorage](#initstorage)|Preasigna bloques de memoria para los elementos y cadenas del cuadro de lista.|
|[CListBox::InsertString](#insertstring)|Inserta una cadena en una ubicación específica de un cuadro de lista.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Devuelve el índice del elemento de cuadro de lista más cercano a un punto.|
|[CListBox::MeasureItem](#measureitem)|Llamado por el marco de trabajo cuando se crea un cuadro de lista de dibujo del propietario para determinar las dimensiones del cuadro de lista.|
|[CListBox::ResetContent](#resetcontent)|Borra todas las entradas de un cuadro de lista.|
|[CListBox::SelectString](#selectstring)|Busca y selecciona una cadena en un cuadro de lista de selección única.|
|[CListBox::SelItemRange](#selitemrange)|Selecciona o anula la selección de un rango de cadenas en un cuadro de lista de selección múltiple.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Establece el delimitador en un cuadro de lista de selección múltiple para comenzar una selección extendida.|
|[CListBox::SetCaretIndex](#setcaretindex)|Establece el rectángulo de foco en el elemento en el índice especificado en un cuadro de lista de selección múltiple.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Establece el ancho de columna de un cuadro de lista de varias columnas.|
|[CListBox::SetCurSel](#setcursel)|Selecciona una cadena de cuadro de lista.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|
|[CListBox::SetItemData](#setitemdata)|Establece un valor asociado al elemento de cuadro de lista.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Establece un puntero al elemento de cuadro de lista.|
|[CListBox::SetItemHeight](#setitemheight)|Establece la altura de los elementos de un cuadro de lista.|
|[CListBox::SetLocale](#setlocale)|Establece el identificador de configuración regional de un cuadro de lista.|
|[CListBox::SetSel](#setsel)|Selecciona o anula la selección de un elemento de cuadro de lista en un cuadro de lista de selección múltiple.|
|[CListBox::SetTabStops](#settabstops)|Establece las posiciones de tabulación en un cuadro de lista.|
|[CListBox::SetTopIndex](#settopindex)|Establece el índice de base cero de la primera cadena visible en un cuadro de lista.|
|[CListBox::VKeyToItem](#vkeytoitem)|Reemplazar para proporcionar un control de WM_KEYDOWN personalizado para cuadros de lista con el conjunto de estilos LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Observaciones

Un cuadro de lista muestra una lista de elementos, como nombres de archivo, que el usuario puede ver y seleccionar.

En un cuadro de lista de selección única, el usuario solo puede seleccionar un elemento. En un cuadro de lista de selección múltiple, se puede seleccionar un rango de elementos. Cuando el usuario selecciona un elemento, se resalta y el cuadro de lista envía un mensaje de notificación a la ventana primaria.

Puede crear un cuadro de lista a partir de una plantilla de cuadro de diálogo o directamente en el código. Para crearlo directamente, construya el `CListBox` objeto y, a continuación, llame a la [create](#create) función miembro para crear el control de cuadro de lista de Windows y adjuntarlo al `CListBox` objeto. Para usar un cuadro de lista en una plantilla de cuadro de `DDX_Control` diálogo, declare una `DoDataExchange` variable de cuadro de lista en la clase de cuadro de diálogo y, a continuación, utilice la función de la clase de cuadro de diálogo para conectar la variable miembro al control. (esto se hace automáticamente cuando se agrega una variable de control a la clase de cuadro de diálogo.)

La construcción puede ser un proceso de `CListBox`un solo paso en una clase derivada de . Escriba un constructor para la `Create` clase derivada y llame desde dentro del constructor.

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y la función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes adopta la siguiente forma:

`ON_Notification( id, memberFxn )`

donde `id` especifica el identificador de ventana secundaria del control `memberFxn` de cuadro de lista que envía la notificación y es el nombre de la función miembro principal que ha escrito para controlar la notificación.

El prototipo de función del padre es el siguiente:

`afx_msg void memberFxn( );`

A continuación se muestra una lista de posibles entradas de mapa de mensajes y una descripción de los casos en los que se enviarían al padre:

- ON_LBN_DBLCLK El usuario hace doble clic en una cadena de un cuadro de lista. Solo un cuadro de lista que tenga el estilo [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) enviará este mensaje de notificación.

- ON_LBN_ERRSPACE El cuadro de lista no puede asignar suficiente memoria para satisfacer la solicitud.

- ON_LBN_KILLFOCUS El cuadro de lista está perdiendo el foco de entrada.

- ON_LBN_SELCANCEL Se cancela la selección actual del cuadro de lista. Este mensaje solo se envía cuando un cuadro de lista tiene el estilo LBS_NOTIFY.

- ON_LBN_SELCHANGE La selección del cuadro de lista ha cambiado. Esta notificación no se envía si la selección se cambia mediante el [CListBox::SetCurSel](#setcursel) función miembro. Esta notificación solo se aplica a un cuadro de lista que tiene el estilo LBS_NOTIFY. El LBN_SELCHANGE mensaje de notificación se envía para un cuadro de lista de selección múltiple cada vez que el usuario presiona una tecla de flecha, incluso si la selección no cambia.

- ON_LBN_SETFOCUS El cuadro de lista recibe el foco de entrada.

- ON_WM_CHARTOITEM Un cuadro de lista de dibujo sácelo que no tiene cadenas recibe un mensaje de WM_CHAR.

- ON_WM_VKEYTOITEM Un cuadro de lista con el estilo LBS_WANTKEYBOARDINPUT recibe un mensaje WM_KEYDOWN.

Si crea `CListBox` un objeto dentro de un cuadro `CListBox` de diálogo (a través de un recurso de cuadro de diálogo), el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea `CListBox` un objeto dentro de una ventana, es posible que deba destruir el `CListBox` objeto. Si crea `CListBox` el objeto en la pila, se destruye automáticamente. Si crea `CListBox` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando el usuario cierre la ventana primaria.

Si asigna memoria en `CListBox` el objeto, reemplace el `CListBox` destructor para eliminar la asignación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox::AddString

Agrega una cadena a un cuadro de lista.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
Apunta a la cadena terminada en null que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la cadena en el cuadro de lista. El valor devuelto se LB_ERR si se produce un error; el valor devuelto se LB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

Si el cuadro de lista no se creó con el estilo [LBS_SORT,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista se ordena. Si el cuadro de lista se creó con el estilo LBS_SORT pero no con `CompareItem` el [estilo LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) el marco de trabajo ordena la lista por una o varias llamadas a la función miembro.

Use [InsertString](#insertstring) para insertar una cadena en una ubicación específica dentro del cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox::CharToItem

Llamado por el marco de trabajo cuando la ventana primaria del cuadro de lista recibe un mensaje WM_CHARTOITEM del cuadro de lista.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nKey*<br/>
El código ANSI del carácter que el usuario escribió.

*nIndex*<br/>
La posición actual del intercalador de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Devuelve - 1 o - 2 para ninguna acción adicional o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que realizar la acción predeterminada para la pulsación de tecla. La implementación predeterminada devuelve - 1.

### <a name="remarks"></a>Observaciones

El WM_CHARTOITEM mensaje es enviado por el cuadro de lista cuando recibe un mensaje de WM_CHAR, pero solo si el cuadro de lista cumple todos estos criterios:

- Es un cuadro de lista de dibujo del propietario.

- No tiene el [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo establecido.

- Tiene al menos un elemento.

Nunca debe llamar a esta función usted mismo. Reemplace esta función para proporcionar su propio control personalizado de los mensajes de teclado.

En la invalidación, debe devolver un valor para indicar al marco de trabajo qué acción realizó. Un valor devuelto de - 1 o - 2 indica que ha manejado todos los aspectos de la selección del elemento y no requiere ninguna acción adicional por parte del cuadro de lista. Antes de volver - 1 o - 2, puede establecer la selección o mover el intercalador o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [SetSel](#setsel). Para mover el intercalador, utilice [SetCaretIndex](#setcaretindex).

Un valor devuelto de 0 o superior especifica el índice de un elemento en el cuadro de lista e indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox::CListBox

Construye un objeto `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Observaciones

Construir un `CListBox` objeto en dos pasos. En primer lugar, llame al constructor `ClistBox` y, a continuación, llame a `Create`, que inicializa el cuadro de lista de Windows y lo adjunta al `CListBox`archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox::CompareItem

Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento en un cuadro de lista ordenado dibujada por el propietario.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpCompareItemStruct*<br/>
Un puntero largo `COMPAREITEMSTRUCT` a una estructura.

### <a name="return-value"></a>Valor devuelto

Indica la posición relativa de los dos elementos descritos en la estructura [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct) Puede ser cualquiera de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|-1|El elemento 1 se ordena antes del elemento 2.|
|0|El artículo 1 y el elemento 2 se ordenan de la misma manera.|
|1|El elemento 1 se ordena después del elemento 2.|

Vea [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener `COMPAREITEMSTRUCT` una descripción de la estructura.

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro de lista dibujada por el propietario con el estilo LBS_SORT, debe invalidar esta función miembro para ayudar al marco de trabajo a ordenar los nuevos elementos agregados al cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox::Crear

Crea el cuadro de lista de `CListBox` Windows y lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del cuadro de lista. Aplique cualquier combinación de [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) al cuadro.

*Rect*<br/>
Especifica el tamaño y la posición del cuadro de lista. Puede ser `CRect` un objeto `RECT` o una estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del cuadro `CDialog` de lista (normalmente un objeto). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir un `CListBox` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, llame `CListBox` a , que inicializa el cuadro de lista de Windows y lo adjunta al objeto.

Cuando `Create` se ejecuta, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al control de cuadro de lista.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) de la `CWnd` clase base. Para extender el control de mensajes `CListBox`predeterminado, derive una clase de , agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control de cuadro de lista.

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_VSCROLL Para añadir una barra de desplazamiento vertical

- WS_HSCROLL Para añadir una barra de desplazamiento horizontal

- WS_GROUP Para agrupar controles

- WS_TABSTOP Para permitir la tabulación de este control

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox::DeleteItem

Llamado por el marco de trabajo cuando el `CListBox` usuario elimina un elemento de un objeto dibujada por el propietario o destruye el cuadro de lista.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDeleteItemStruct*<br/>
Puntero largo a una estructura [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) de Windows que contiene información sobre el elemento eliminado.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Reemplace esta función para volver a dibujar un cuadro de lista de dibujo del propietario según sea necesario.

Vea [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener `DELETEITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox::DeleteString

Elimina el elemento en la posición *nIndex* del cuadro de lista.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la cadena que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Un recuento de las cadenas restantes en la lista. El valor devuelto se LB_ERR si *nIndex* especifica un índice mayor que el número de elementos de la lista.

### <a name="remarks"></a>Observaciones

Todos los elementos que siguen *a nIndex* ahora se mueven hacia abajo una posición. Por ejemplo, si un cuadro de lista contiene dos elementos, eliminar el primer elemento hará que el elemento restante esté ahora en la primera posición. *nIndex*n.o 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox::Dir

Agrega una lista de nombres de archivo, unidades o ambos a un cuadro de lista.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parámetros

*Attr*<br/>
Puede ser cualquier combinación de `CFile::GetStatu`los valores **de enumeración** descritos en [s](../../mfc/reference/cfile-class.md#getstatus), o cualquier combinación de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|0x0000|El archivo se puede leer o escribir en.|
|0x0001|El archivo se puede leer pero no se escribe en.|
|0x0002|El archivo está oculto y no aparece en una lista de directorios.|
|0x0004|El archivo es un archivo del sistema.|
|0x0010|El nombre especificado por *lpszWildCard* especifica un directorio.|
|0x0020|El archivo ha sido archivado.|
|0x4000|Incluya todas las unidades que coincidan con el nombre especificado por *lpszWildCard*.|
|0x8000|Bandera exclusiva. Si se establece la marca exclusiva, solo se muestran los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".|

*lpszWildCard*<br/>
Apunta a una cadena de especificación de archivo. La cadena puede contener comodines\*(por ejemplo, *. ).

### <a name="return-value"></a>Valor devuelto

El índice de base cero del último nombre de archivo agregado a la lista. El valor devuelto se LB_ERR si se produce un error; el valor devuelto se LB_ERRSPACE si no hay suficiente espacio disponible para almacenar las nuevas cadenas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un cuadro de lista de dibujo del propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

Los `itemAction` `itemState` miembros `DRAWITEMSTRUCT` y de la estructura definen la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalidar esta función miembro para implementar `CListBox` el dibujo para un objeto de dibujo del propietario. La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que finalice esta función miembro.

Vea [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener `DRAWITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox::FindString

Busca la primera cadena en un cuadro de lista que contiene el prefijo especificado sin cambiar la selección del cuadro de lista.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si *nStartAfter* es -1, se busca en todo el cuadro de lista desde el principio.

*lpszItem*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento coincidente o LB_ERR si la búsqueda no se realizó correctamente.

### <a name="remarks"></a>Observaciones

Utilice la [SelectString](#selectstring) función miembro para buscar y seleccionar una cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox::FindStringExact

Busca la primera cadena de cuadro de lista que coincide con la cadena especificada en *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parámetros

*nIndexStart*<br/>
Especifica el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nIndexStart*. Si *nIndexStart* es -1, se busca en todo el cuadro de lista desde el principio.

*lpszFind*<br/>
Apunta a la cadena terminada en null que se va a buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue mayúsculas de minúsculas, por lo que la cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

El índice del elemento coincidente o LB_ERR si la búsqueda no se realizó correctamente.

### <a name="remarks"></a>Observaciones

Si el cuadro de lista se creó con un `FindStringExact` estilo de dibujo del propietario pero sin el estilo de [LBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) la función miembro intenta hacer coincidir el valor de doubleword con el valor de *lpszFind*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox::GetAnchorIndex

Recupera el índice de base cero del elemento de anclaje actual en el cuadro de lista.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice del elemento delimitador actual, si se realiza correctamente; LB_ERR de lo contrario.

### <a name="remarks"></a>Observaciones

En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o último elemento de un bloque de elementos seleccionados contiguos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox::GetCaretIndex

Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento que tiene el rectángulo de foco en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es el índice del elemento seleccionado, si existe.

### <a name="remarks"></a>Observaciones

El elemento puede o no ser seleccionado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::SetCaretIndex](#setcaretindex).

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox::GetCount

Recupera el número de elementos de un cuadro de lista.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del cuadro de lista o LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El recuento devuelto es uno mayor que el valor de índice del último elemento (el índice es de base cero).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox::GetCurSel

Recupera el índice de base cero del elemento seleccionado actualmente, si existe, en un cuadro de lista de selección única.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento seleccionado actualmente si es un cuadro de lista de selección única. Se LB_ERR si no hay ningún elemento seleccionado actualmente.

En un cuadro de lista de selección múltiple, el índice del elemento que tiene el foco.

### <a name="remarks"></a>Observaciones

No llame `GetCurSel` para un cuadro de lista de selección múltiple. Utilice [CListBox::GetSelItems](#getselitems) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox::GetHorizontalExtent

Recupera del cuadro de lista el ancho en píxeles por el que se puede desplazar horizontalmente.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho desplazable del cuadro de lista, en píxeles.

### <a name="remarks"></a>Observaciones

Esto solo es aplicable si el cuadro de lista tiene una barra de desplazamiento horizontal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox::GetItemData

Recupera el valor de doble palabra proporcionado por la aplicación asociado al elemento de cuadro de lista especificado.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El valor asociado al elemento o LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El valor doubleword era el parámetro *dwItemData* de una llamada [SetItemData.](#setitemdata)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox::GetItemDataPtr

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro de lista especificado como un puntero (**void** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Recupera un puntero o -1 si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox::GetItemHeight

Determina la altura de los elementos de un cuadro de lista.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro solo se utiliza si el cuadro de lista tiene el estilo LBS_OWNERDRAWVARIABLE; de lo contrario, debe establecerse en 0.

### <a name="return-value"></a>Valor devuelto

Altura, en píxeles, de los elementos del cuadro de lista. Si el cuadro de lista tiene el estilo [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) el valor devuelto es el alto del elemento especificado por *nIndex*. Si se produce un error, el valor devuelto se LB_ERR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox::GetItemRect

Recupera las dimensiones del rectángulo que limita un elemento de cuadro de lista tal como se muestra actualmente en la ventana del cuadro de lista.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

*lpRect*<br/>
Especifica un puntero largo a una [estructura RECT](/windows/win32/api/windef/ns-windef-rect) que recibe las coordenadas de cliente de cuadro de lista del elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox::GetListBoxInfo

Recupera el número de elementos por columna.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos `CListBox` por columna del objeto.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje LB_GETLISTBOXINFO,](/windows/win32/Controls/lb-getlistboxinfo) como se describe en el Windows SDK.

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox::GetLocale

Recupera la configuración regional utilizada por el cuadro de lista.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) para las cadenas del cuadro de lista.

### <a name="remarks"></a>Observaciones

La configuración regional se utiliza, por ejemplo, para determinar el criterio de ordenación de las cadenas en un cuadro de lista ordenado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::SetLocale](#setlocale).

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox::GetSel

Recupera el estado de selección de un elemento.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

### <a name="return-value"></a>Valor devuelto

Un número positivo si se selecciona el elemento especificado; de lo contrario, es 0. El valor devuelto se LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Esta función miembro funciona con cuadros de lista de selección única y múltiple.

Para recuperar el índice del elemento de cuadro de lista seleccionado actualmente, utilice [CListBox::GetCurSel](#getcursel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox::GetSelCount

Recupera el número total de elementos seleccionados en un cuadro de lista de selección múltiple.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Valor devuelto

El recuento de elementos seleccionados en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es LB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::GetSelItems](#getselitems).

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox::GetSelItems

Rellena un búfer con una matriz de enteros que especifica los números de elemento de los elementos seleccionados en un cuadro de lista de selección múltiple.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parámetros

*nMaxItems*<br/>
Especifica el número máximo de elementos seleccionados cuyos números de artículo se van a colocar en el búfer.

*rgIndex*<br/>
Especifica un puntero a un búfer lo suficientemente grande para el número de enteros especificado por *nMaxItems*.

### <a name="return-value"></a>Valor devuelto

El número real de elementos colocados en el búfer. Si el cuadro de lista es un cuadro `LB_ERR`de lista de selección única, el valor devuelto es .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox::GetText

Obtiene una cadena de un cuadro de lista.

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la cadena que se va a recuperar.

*lpszBuffer*<br/>
Apunta al búfer que recibe la cadena. El búfer debe tener suficiente espacio para la cadena y un carácter nulo de terminación. El tamaño de la cadena se puede `GetTextLen` determinar con antelación llamando a la función miembro.

*rString*<br/>
Referencia a un objeto `CString`.

### <a name="return-value"></a>Valor devuelto

La longitud (en bytes) de la cadena, excluyendo el carácter nulo de terminación. Si *nIndex* no especifica un índice válido, el valor devuelto se LB_ERR.

### <a name="remarks"></a>Observaciones

La segunda forma de esta `CString` función miembro rellena un objeto con el texto de cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox::GetTextLen

Obtiene la longitud de una cadena en un elemento de cuadro de lista.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la cadena.

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena en caracteres, excluyendo el carácter nulo de terminación. Si *nIndex* no especifica un índice válido, el valor devuelto se LB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::GetText](#gettext).

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox::GetTopIndex

Recupera el índice de base cero del primer elemento visible de un cuadro de lista.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del primer elemento visible en un cuadro de lista si se realiza correctamente, LB_ERR lo contrario.

### <a name="remarks"></a>Observaciones

Inicialmente, el elemento 0 está en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, otro elemento puede estar en la parte superior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox::InitStorage

Asigna memoria para almacenar elementos de cuadro de lista.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parámetros

*nArtículos*<br/>
Especifica el número de elementos que se va a agregar.

*nBytes*<br/>
Especifica la cantidad de memoria, en bytes, que se va a asignar para las cadenas de elemento.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el número máximo de elementos que el cuadro de lista puede almacenar antes de que se necesite una reasignación de memoria, de lo contrario LB_ERRSPACE, lo que significa que no hay suficiente memoria disponible.

### <a name="remarks"></a>Observaciones

Llame a esta función antes de `CListBox`agregar un gran número de elementos a un archivo .

Esta función ayuda a acelerar la inicialización de cuadros de lista que tienen un gran número de elementos (más de 100). Preasigna la cantidad especificada de memoria para que las funciones [AddString](#addstring), [InsertString](#insertstring)y [Dir](#dir) posteriores tomen el menor tiempo posible. Puede utilizar estimaciones para los parámetros. Si sobreestima, se asigna algo de memoria adicional; si subestima, la asignación normal se utiliza para los artículos que superan el importe preasignado.

Solo Windows 95/98: el parámetro *nItems* está limitado a valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista está limitado solo por la memoria disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox::InsertString

Inserta una cadena en el cuadro de lista.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la posición para insertar la cadena. Si este parámetro es -1, la cadena se agrega al final de la lista.

*lpszItem*<br/>
Apunta a la cadena terminada en null que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la posición donde se insertó la cadena. El valor devuelto se LB_ERR si se produce un error; el valor devuelto se LB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

A diferencia de la `InsertString` [AddString](#addstring) función miembro, no hace que una lista con el estilo [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) se ordene.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox::ItemFromPoint

Determina el elemento de cuadro de lista más cercano al punto especificado en *pt*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
Punto para el que se va a encontrar el elemento más cercano, especificado en relación con la esquina superior izquierda del área de cliente del cuadro de lista.

*bOutside*<br/>
Referencia a una variable BOOL que se establecerá en TRUE si *pt* está fuera del área de cliente del cuadro de lista, FALSE si *pt* está dentro del área de cliente del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El índice del elemento más cercano al punto especificado en *pt*.

### <a name="remarks"></a>Observaciones

Puede utilizar esta función para determinar qué elemento de cuadro de lista se mueve el cursor del mouse.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox::SetAnchorIndex](#setanchorindex).

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox::MeasureItem

Llamado por el marco de trabajo cuando se crea un cuadro de lista con un estilo de dibujo por el propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero largo a una estructura [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función `MEASUREITEMSTRUCT` miembro y rellene la estructura para informar a Windows de las dimensiones del cuadro de lista. Si el cuadro de lista se crea con el [estilo LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

Para obtener más [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) información sobre el uso del estilo `SubclassDlgItem` LBS_OWNERDRAWFIXED en `CWnd`un cuadro de lista de dibujo del propietario creado con la función miembro de , consulte la discusión en la [Nota técnica 14](../../mfc/tn014-custom-controls.md).

Vea [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener `MEASUREITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox::ResetContent

Quita todos los elementos de un cuadro de lista.

```cpp
void ResetContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox::SelectString

Busca un elemento de cuadro de lista que coincida con la cadena especificada y, si se encuentra un elemento coincidente, selecciona el elemento.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si *nStartAfter* es -1, se busca en todo el cuadro de lista desde el principio.

*lpszItem*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

El índice del elemento seleccionado si la búsqueda se realizó correctamente. Si la búsqueda no se realizó correctamente, el valor devuelto se LB_ERR y no se cambia la selección actual.

### <a name="remarks"></a>Observaciones

El cuadro de lista se desplaza, si es necesario, para ver el elemento seleccionado.

Esta función miembro no se puede utilizar con un cuadro de lista que tiene el estilo [de LBS_MULTIPLESEL.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

Un elemento solo se selecciona si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena especificada por *lpszItem*.

Utilice `FindString` la función miembro para buscar una cadena sin seleccionar el elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox::SelItemRange

Selecciona varios elementos consecutivos en un cuadro de lista de selección múltiple.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parámetros

*bSeleccionar*<br/>
Especifica cómo establecer la selección. Si *bSelect* es TRUE, la cadena se selecciona y resalta; si FALSE, se quita el resaltado y la cadena ya no está seleccionada.

*nFirstItem*<br/>
Especifica el índice de base cero del primer elemento que se va a establecer.

*nLastItem*<br/>
Especifica el índice de base cero del último elemento que se va a establecer.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo con cuadros de lista de selección múltiple. Si necesita seleccionar solo un elemento en un cuadro de lista de selección múltiple, es decir, si *nFirstItem* es igual a *nLastItem,* llame a la [SetSel](#setsel) función miembro en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox::SetAnchorIndex

Establece el delimitador en un cuadro de lista de selección múltiple para comenzar una selección extendida.

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista que será el delimitador.

### <a name="remarks"></a>Observaciones

En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o último elemento de un bloque de elementos seleccionados contiguos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox::SetCaretIndex

Establece el rectángulo de foco en el elemento en el índice especificado en un cuadro de lista de selección múltiple.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento para recibir el rectángulo de foco en el cuadro de lista.

*bScroll*<br/>
Si este valor es 0, el elemento se desplaza hasta que esté completamente visible. Si este valor no es 0, el elemento se desplaza hasta que sea al menos parcialmente visible.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Si el elemento no está visible, se desplaza a la vista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox::SetColumnWidth

Establece el ancho en píxeles de todas las columnas en un cuadro de lista de varias columnas (creado con el [estilo LBS_MULTICOLUMN).](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parámetros

*cxWidth*<br/>
Especifica el ancho en píxeles de todas las columnas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox::SetCurSel

Selecciona una cadena y la desplaza a la vista, si es necesario.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parámetros

*nSeleccionar*<br/>
Especifica el índice de base cero de la cadena que se va a seleccionar. Si *nSelect* es -1, el cuadro de lista está configurado para que no tenga ninguna selección.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Cuando se selecciona la nueva cadena, el cuadro de lista quita el resaltado de la cadena seleccionada anteriormente.

Utilice esta función miembro solo con cuadros de lista de selección única.

Para establecer o quitar una selección en un cuadro de lista de selección múltiple, utilice [CListBox::SetSel](#setsel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox::SetHorizontalExtent

Establece el ancho, en píxeles, por el que se puede desplazar horizontalmente un cuadro de lista.

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parámetros

*cxExtent*<br/>
Especifica el número de píxeles por los que se puede desplazar horizontalmente el cuadro de lista.

### <a name="remarks"></a>Observaciones

Si el tamaño del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente los elementos del cuadro de lista. Si el cuadro de lista es tan grande o mayor que este valor, la barra de desplazamiento horizontal está oculta.

Para responder a `SetHorizontalExtent`una llamada a , el cuadro de lista debe haberse definido con el [estilo WS_HSCROLL.](../../mfc/reference/styles-used-by-mfc.md#window-styles)

Esta función miembro no es útil para cuadros de lista de varias columnas. Para cuadros de lista `SetColumnWidth` de varias columnas, llame a la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox::SetItemData

Establece un valor asociado al elemento especificado en un cuadro de lista.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

*dwItemData*<br/>
Especifica el valor que se asociará al elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox::SetItemDataPtr

Establece el valor de 32 bits asociado al elemento especificado en un cuadro de lista para que sea el puntero especificado ( **void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

*pData*<br/>
Especifica el puntero que se asociará al elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Este puntero sigue siendo válido durante la vida del cuadro de lista, aunque la posición relativa del elemento dentro del cuadro de lista puede cambiar a medida que se agregan o quitan elementos. Por lo tanto, el índice del elemento dentro del cuadro puede cambiar, pero el puntero sigue siendo confiable.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox::SetItemHeight

Establece la altura de los elementos de un cuadro de lista.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro solo se utiliza si el cuadro de lista tiene el estilo LBS_OWNERDRAWVARIABLE; de lo contrario, debe establecerse en 0.

*cyItemHeight*<br/>
Especifica la altura, en píxeles, del elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si el índice o la altura no son válidos.

### <a name="remarks"></a>Observaciones

Si el cuadro de lista tiene el estilo [LBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) esta función establece el alto del elemento especificado por *nIndex*. De lo contrario, esta función establece la altura de todos los elementos del cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox::SetLocale

Establece el identificador de configuración regional para este cuadro de lista.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parámetros

*nNewLocale*<br/>
El nuevo valor de identificador de configuración regional (LCID) que se va a establecer para el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El valor de identificador de configuración regional (LCID) anterior para este cuadro de lista.

### <a name="remarks"></a>Observaciones

Si `SetLocale` no se llama, la configuración regional predeterminada se obtiene del sistema. Esta configuración regional predeterminada del sistema se puede modificar mediante la aplicación Regional (o Internacional) del Panel de control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox::SetSel

Selecciona una cadena en un cuadro de lista de selección múltiple.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la cadena que se va a establecer. Si -1, la selección se agrega o elimina de todas las cadenas, dependiendo del valor de *bSelect*.

*bSeleccionar*<br/>
Especifica cómo establecer la selección. Si *bSelect* es TRUE, la cadena se selecciona y resalta; si FALSE, se quita el resaltado y la cadena ya no está seleccionada. La cadena especificada se selecciona y resalta de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro solo con cuadros de lista de selección múltiple.

Para seleccionar un elemento de un cuadro de lista de selección única, utilice [CListBox::SetCurSel](#setcursel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox::SetTabStops

Establece las posiciones de tabulación en un cuadro de lista.

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parámetros

*cxEachStop*<br/>
Las tabulaciones se establecen en todas las unidades de diálogo *cxEachStop.* Consulte *rgTabStops* para obtener una descripción de una unidad de diálogo.

*nTabStops*<br/>
Especifica el número de tabulaciones que se deben tener en el cuadro de lista.

*rgTabStops*<br/>
Apunta al primer miembro de una matriz de enteros que contiene las posiciones de tabulación en unidades de diálogo. Una unidad de diálogo es una distancia horizontal o vertical. Una unidad de diálogo horizontal es igual a una cuarta parte de la unidad de anchura base del cuadro de diálogo actual, y una unidad de diálogo vertical es igual a una octava parte de la unidad de altura base del cuadro de diálogo actual. Las unidades base del cuadro de diálogo se calculan en función de la altura y la anchura de la fuente del sistema actual. La `GetDialogBaseUnits` función Windows devuelve las unidades base del cuadro de diálogo actual en píxeles. Las tabulaciones deben ordenarse en orden creciente; no se permiten pestañas traseras.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se establecieron todas las pestañas; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para establecer tabulaciones al tamaño predeterminado de 2 unidades de cuadro de diálogo, llame a la versión sin parámetros de esta función miembro. Para establecer tabulaciones en un tamaño distinto de 2, llame a la versión con el *cxEachStop* argumento.

Para establecer tabulaciones en una matriz de tamaños, utilice la versión con los argumentos *rgTabStops* y *nTabStops.* Se establecerá una tabulación para cada valor en *rgTabStops*, hasta el número especificado por *nTabStops*.

Para responder a una `SetTabStops` llamada a la función miembro, el cuadro de lista debe haberse creado con el [estilo LBS_USETABSTOPS.](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox::SetTopIndex

Garantiza que un elemento de cuadro de lista determinado esté visible.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente o LB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El sistema desplaza el cuadro de lista hasta que el elemento especificado por *nIndex* aparece en la parte superior del cuadro de lista o se ha alcanzado el intervalo de desplazamiento máximo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox::VKeyToItem

Llamado por el marco de trabajo cuando la ventana primaria del cuadro de lista recibe un mensaje WM_VKEYTOITEM del cuadro de lista.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nKey*<br/>
El código de tecla virtual de la tecla que el usuario presionó. Para obtener una lista de códigos de clave virtuales estándar, consulte Winuser.h

*nIndex*<br/>
La posición actual del intercalador de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Devuelve - 2 para ninguna acción adicional, - 1 para la acción predeterminada o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que realizar la acción predeterminada para la pulsación de tecla.

### <a name="remarks"></a>Observaciones

El WM_VKEYTOITEM mensaje se envía mediante el cuadro de lista cuando recibe un mensaje de WM_KEYDOWN, pero solo si el cuadro de lista cumple con ambos de los siguientes elementos:

- Tiene el [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) estilo establecido.

- Tiene al menos un elemento.

Nunca debe llamar a esta función usted mismo. Reemplace esta función para proporcionar su propio control personalizado de los mensajes de teclado.

Debe devolver un valor para indicar al marco de trabajo qué acción realizó la invalidación. Un valor devuelto de - 2 indica que la aplicación controló todos los aspectos de la selección del elemento y no requiere ninguna acción adicional por parte del cuadro de lista. Antes de volver - 2, puede establecer la selección o mover el intercalador o ambos. Para establecer la selección, utilice [SetCurSel](#setcursel) o [SetSel](#setsel). Para mover el intercalador, utilice [SetCaretIndex](#setcaretindex).

Un valor devuelto de - 1 indica que el cuadro de lista debe realizar la acción predeterminada en respuesta a la pulsación de tecla. La implementación predeterminada devuelve - 1.

Un valor devuelto de 0 o superior especifica el índice de un elemento en el cuadro de lista e indica que el cuadro de lista debe realizar la acción predeterminada para la pulsación de tecla en el elemento especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Consulte también

[EJEMPLO de MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[Clase CStatic](../../mfc/reference/cstatic-class.md)
