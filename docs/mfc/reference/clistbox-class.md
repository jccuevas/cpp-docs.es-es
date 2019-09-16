---
title: CListBox (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: e47a580e786572b0741700721a9d1ba4ac925fcd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505686"
---
# <a name="clistbox-class"></a>CListBox (clase)

Proporciona la funcionalidad de un cuadro de lista de Windows.

## <a name="syntax"></a>Sintaxis

```
class CListBox : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CListBox::CListBox](#clistbox)|Construye un objeto `CListBox`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CListBox::AddString](#addstring)|Agrega una cadena a un cuadro de lista.|
|[CListBox::CharToItem](#chartoitem)|Invalide para proporcionar un control de WM_CHAR personalizado para los cuadros de lista dibujados por el propietario que no tienen cadenas.|
|[CListBox::CompareItem](#compareitem)|Lo llama el marco de trabajo para determinar la posición de un nuevo elemento en un cuadro de lista dibujado por el propietario ordenado.|
|[CListBox::Create](#create)|Crea el cuadro de lista de Windows y lo adjunta al `CListBox` objeto.|
|[CListBox::DeleteItem](#deleteitem)|Lo llama el marco de trabajo cuando el usuario elimina un elemento de un cuadro de lista dibujado por el propietario.|
|[CListBox::DeleteString](#deletestring)|Elimina una cadena de un cuadro de lista.|
|[CListBox::Dir](#dir)|Agrega nombres de archivo, unidades o ambos desde el directorio actual a un cuadro de lista.|
|[CListBox::DrawItem](#drawitem)|Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro de lista dibujado por el propietario.|
|[CListBox::FindString](#findstring)|Busca una cadena en un cuadro de lista.|
|[CListBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista que coincide con una cadena especificada.|
|[CListBox::GetAnchorIndex](#getanchorindex)|Recupera el índice de base cero del elemento de delimitador actual en un cuadro de lista.|
|[CListBox::GetCaretIndex](#getcaretindex)|Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.|
|[CListBox::GetCount](#getcount)|Devuelve el número de cadenas de un cuadro de lista.|
|[CListBox::GetCurSel](#getcursel)|Devuelve el índice de base cero de la cadena actualmente seleccionada en un cuadro de lista.|
|[CListBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|
|[CListBox::GetItemData](#getitemdata)|Devuelve un valor asociado al elemento de cuadro de lista.|
|[CListBox::GetItemDataPtr](#getitemdataptr)|Devuelve un puntero a un elemento de cuadro de lista.|
|[CListBox::GetItemHeight](#getitemheight)|Determina el alto de los elementos de un cuadro de lista.|
|[CListBox::GetItemRect](#getitemrect)|Devuelve el rectángulo delimitador del elemento de cuadro de lista tal como se muestra actualmente.|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|Recupera el número de elementos por columna.|
|[CListBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro de lista.|
|[CListBox::GetSel](#getsel)|Devuelve el estado de selección de un elemento de cuadro de lista.|
|[CListBox::GetSelCount](#getselcount)|Devuelve el número de cadenas seleccionadas actualmente en un cuadro de lista de selección múltiple.|
|[CListBox::GetSelItems](#getselitems)|Devuelve los índices de las cadenas actualmente seleccionadas en un cuadro de lista.|
|[CListBox::GetText](#gettext)|Copia un elemento de cuadro de lista en un búfer.|
|[CListBox::GetTextLen](#gettextlen)|Devuelve la longitud en bytes de un elemento de cuadro de lista.|
|[CListBox::GetTopIndex](#gettopindex)|Devuelve el índice de la primera cadena visible de un cuadro de lista.|
|[CListBox::InitStorage](#initstorage)|Asigna bloques de memoria previamente para los elementos de cuadro de lista y las cadenas.|
|[CListBox::InsertString](#insertstring)|Inserta una cadena en una ubicación específica de un cuadro de lista.|
|[CListBox::ItemFromPoint](#itemfrompoint)|Devuelve el índice del elemento de cuadro de lista más cercano a un punto.|
|[CListBox::MeasureItem](#measureitem)|Lo llama el marco de trabajo cuando se crea un cuadro de lista dibujado por el propietario para determinar las dimensiones del cuadro de lista.|
|[CListBox::ResetContent](#resetcontent)|Borra todas las entradas de un cuadro de lista.|
|[CListBox::SelectString](#selectstring)|Busca y selecciona una cadena en un cuadro de lista de selección única.|
|[CListBox::SelItemRange](#selitemrange)|Selecciona o anula la selección de un intervalo de cadenas en un cuadro de lista de selección múltiple.|
|[CListBox::SetAnchorIndex](#setanchorindex)|Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.|
|[CListBox::SetCaretIndex](#setcaretindex)|Establece el rectángulo de foco en el elemento en el índice especificado de un cuadro de lista de selección múltiple.|
|[CListBox::SetColumnWidth](#setcolumnwidth)|Establece el ancho de columna de un cuadro de lista de varias columnas.|
|[CListBox::SetCurSel](#setcursel)|Selecciona una cadena de cuadro de lista.|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que un cuadro de lista se puede desplazar horizontalmente.|
|[CListBox::SetItemData](#setitemdata)|Establece un valor asociado al elemento de cuadro de lista.|
|[CListBox::SetItemDataPtr](#setitemdataptr)|Establece un puntero al elemento de cuadro de lista.|
|[CListBox::SetItemHeight](#setitemheight)|Establece el alto de los elementos de un cuadro de lista.|
|[CListBox::SetLocale](#setlocale)|Establece el identificador de configuración regional de un cuadro de lista.|
|[CListBox::SetSel](#setsel)|Selecciona o anula la selección de un elemento de cuadro de lista en un cuadro de lista de selección múltiple.|
|[CListBox::SetTabStops](#settabstops)|Establece las posiciones de tabulación en un cuadro de lista.|
|[CListBox::SetTopIndex](#settopindex)|Establece el índice de base cero de la primera cadena visible en un cuadro de lista.|
|[CListBox::VKeyToItem](#vkeytoitem)|Invalide para proporcionar un control de WM_KEYDOWN personalizado para los cuadros de lista con el conjunto de estilos LBS_WANTKEYBOARDINPUT.|

## <a name="remarks"></a>Comentarios

Un cuadro de lista muestra una lista de elementos, como nombres de archivo, que el usuario puede ver y seleccionar.

En un cuadro de lista de selección única, el usuario puede seleccionar un solo elemento. En un cuadro de lista de selección múltiple, se puede seleccionar un intervalo de elementos. Cuando el usuario selecciona un elemento, se resalta y el cuadro de lista envía un mensaje de notificación a la ventana primaria.

Puede crear un cuadro de lista desde una plantilla de cuadro de diálogo o directamente en el código. Para crearlo directamente, construya el `CListBox` objeto y, a continuación, llame a la función miembro [Create](#create) para crear el control de cuadro de lista de `CListBox` Windows y adjuntarlo al objeto. Para usar un cuadro de lista en una plantilla de cuadro de diálogo, declare una variable de cuadro de lista en la `DDX_Control` clase de cuadro de diálogo y `DoDataExchange` , a continuación, use en la función de la clase de cuadro de diálogo para conectar la variable de miembro al control. (esto se hace automáticamente al agregar una variable de control a la clase de cuadro de diálogo).

La construcción puede ser un proceso de un solo paso en una clase `CListBox`derivada de. Escriba un constructor para la clase derivada y llame `Create` a desde dentro del constructor.

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro de lista a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el siguiente formato:

`ON_Notification( id, memberFxn )`

donde `id` especifica el identificador de la ventana secundaria del control de cuadro de lista que envía `memberFxn` la notificación y es el nombre de la función miembro primaria que ha escrito para controlar la notificación.

El prototipo de función del elemento primario es el siguiente:

`afx_msg void memberFxn( );`

A continuación se muestra una lista de posibles entradas de mapa de mensajes y una descripción de los casos en los que se enviarían a la primaria:

- ON_LBN_DBLCLK el usuario hace doble clic en una cadena de un cuadro de lista. Solo un cuadro de lista que tenga el estilo [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) enviará este mensaje de notificación.

- ON_LBN_ERRSPACE el cuadro de lista no puede asignar suficiente memoria para satisfacer la solicitud.

- ON_LBN_KILLFOCUS el cuadro de lista está perdiendo el foco de entrada.

- ON_LBN_SELCANCEL la selección de cuadro de lista actual está cancelada. Este mensaje solo se envía cuando un cuadro de lista tiene el estilo LBS_NOTIFY.

- ON_LBN_SELCHANGE la selección en el cuadro de lista ha cambiado. Esta notificación no se envía si la selección ha cambiado por la función miembro [CListBox:: SetCurSel](#setcursel) . Esta notificación se aplica solo a un cuadro de lista que tiene el estilo LBS_NOTIFY. El mensaje de notificación LBN_SELCHANGE se envía para un cuadro de lista de selección múltiple cada vez que el usuario presiona una tecla de dirección, incluso si la selección no cambia.

- ON_LBN_SETFOCUS el cuadro de lista está recibiendo el foco de entrada.

- ON_WM_CHARTOITEM un cuadro de lista dibujado por el propietario que no tiene ninguna cadena recibe un mensaje WM_CHAR.

- ON_WM_VKEYTOITEM un cuadro de lista con el estilo LBS_WANTKEYBOARDINPUT recibe un mensaje WM_KEYDOWN.

Si crea un `CListBox` objeto dentro de un cuadro de diálogo (a través de un recurso de `CListBox` cuadro de diálogo), el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si crea un `CListBox` objeto dentro de una ventana, puede que tenga que destruir el `CListBox` objeto. Si crea el `CListBox` objeto en la pila, se destruye automáticamente. Si crea el `CListBox` objeto en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando el usuario cierre la ventana primaria.

Si asigna memoria en el `CListBox` objeto, invalide el `CListBox` destructor para desechar la asignación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

Agrega una cadena a un cuadro de lista.

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
Apunta a la cadena terminada en null que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la cadena en el cuadro de lista. El valor devuelto es LB_ERR si se produce un error; el valor devuelto es LB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Comentarios

Si el cuadro de lista no se creó con el estilo [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista está ordenada. Si el cuadro de lista se ha creado con el estilo LBS_SORT pero no el estilo [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , el marco de trabajo ordena la lista por una o `CompareItem` varias llamadas a la función miembro.

Use [InsertString](#insertstring) para insertar una cadena en una ubicación concreta del cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>  CListBox::CharToItem

Lo llama el marco de trabajo cuando la ventana primaria del cuadro de lista recibe un mensaje WM_CHARTOITEM del cuadro de lista.

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nKey*<br/>
Código ANSI del carácter que el usuario ha escrito.

*nIndex*<br/>
La posición actual del símbolo de intercalación del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Devuelve-1 o-2 para ninguna acción más o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que realizar la acción predeterminada para la pulsación de tecla. La implementación predeterminada devuelve-1.

### <a name="remarks"></a>Comentarios

El cuadro de lista envía el mensaje WM_CHARTOITEM cuando recibe un mensaje WM_CHAR, pero solo si el cuadro de lista cumple todos estos criterios:

- Es un cuadro de lista dibujado por el propietario.

- No tiene establecido el estilo [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Tiene al menos un elemento.

No debe llamar nunca a esta función. Invalide esta función para proporcionar su propio control personalizado de los mensajes del teclado.

En la invalidación, debe devolver un valor para indicar a la plataforma la acción que ha realizado. Un valor devuelto de-1 o-2 indica que se administraron todos los aspectos de la selección del elemento y no requiere ninguna acción adicional por parte del cuadro de lista. Antes de devolver-1 o-2, puede establecer la selección o desplace el símbolo de intercalación o ambos. Para establecer la selección, use [SetCurSel](#setcursel) o [SetSel](#setsel). Para desplace el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).

Un valor devuelto de 0 o superior especifica el índice de un elemento del cuadro de lista e indica que el cuadro de lista debe realizar la acción predeterminada de la pulsación de tecla en el elemento determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox:: CListBox

Construye un objeto `CListBox`.

```
CListBox();
```

### <a name="remarks"></a>Comentarios

Un `CListBox` objeto se crea en dos pasos. En primer lugar, llame `ClistBox` al constructor y `Create`, a continuación, llame a, que inicializa el cuadro de lista de `CListBox`Windows y lo asocia a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>  CListBox::CompareItem

Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en un cuadro de lista dibujado por el propietario ordenado.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpCompareItemStruct*<br/>
Puntero largo a una `COMPAREITEMSTRUCT` estructura.

### <a name="return-value"></a>Valor devuelto

Indica la posición relativa de los dos elementos descritos en la estructura [compareitemstruct (](/windows/win32/api/winuser/ns-winuser-compareitemstruct) . Puede ser cualquiera de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|-1|El elemento 1 se ordena antes que el elemento 2.|
|0|Los elementos 1 y 2 ordenan el mismo.|
|1|El elemento 1 se ordena después del elemento 2.|

Vea [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener una descripción de `COMPAREITEMSTRUCT` la estructura.

### <a name="remarks"></a>Comentarios

De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro de lista dibujado por el propietario con el estilo LBS_SORT, debe invalidar esta función miembro para ayudar al marco a ordenar los nuevos elementos agregados al cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>CListBox:: Create

Crea el cuadro de lista de Windows y lo adjunta al `CListBox` objeto.

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

*rect*<br/>
Especifica el tamaño y la posición del cuadro de lista. Puede ser un `CRect` objeto o una `RECT` estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del cuadro de lista (normalmente `CDialog` un objeto). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un `CListBox` objeto se crea en dos pasos. En primer lugar, llame al constructor y `Create`, a continuación, llame a, que inicializa el cuadro de lista de `CListBox` Windows y lo adjunta al objeto.

Cuando `Create` se ejecuta, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al control de cuadro de lista.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [alcrear](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) en `CWnd` la clase base. Para extender el control de mensajes predeterminado, derive una clase `CListBox`de, agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensaje anteriores. Invalide `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro de lista.

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_VSCROLL para agregar una barra de desplazamiento vertical

- WS_HSCROLL para agregar una barra de desplazamiento horizontal

- WS_GROUP a controles de grupo

- WS_TABSTOP para permitir la tabulación a este control

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

Lo llama el marco de trabajo cuando el usuario elimina un elemento de un objeto dibujado `CListBox` por el propietario o destruye el cuadro de lista.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDeleteItemStruct*<br/>
Un puntero largo a una estructura [deleteitemstruct (](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) de Windows que contiene información sobre el elemento eliminado.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función no hace nada. Invalide esta función para volver a dibujar un cuadro de lista dibujado por el propietario según sea necesario.

Vea [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de `DELETEITEMSTRUCT` la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

Elimina el elemento en la posición *NINDEX* del cuadro de lista.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la cadena que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Recuento de las cadenas restantes de la lista. El valor devuelto es LB_ERR si *NINDEX* especifica un índice mayor que el número de elementos de la lista.

### <a name="remarks"></a>Comentarios

Ahora, todos los elementos que siguen a *NINDEX* bajan una posición. Por ejemplo, si un cuadro de lista contiene dos elementos, al eliminar el primer elemento, el elemento restante quedará ahora en la primera posición. *NINDEX*= 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox::D ir

Agrega una lista de nombres de archivo, unidades o ambos a un cuadro de lista.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parámetros

*attr*<br/>
Puede ser cualquier combinación de los valores de **enumeración** descritos en `CFile::GetStatu` [s](../../mfc/reference/cfile-class.md#getstatus)o cualquier combinación de los siguientes valores:

|Valor|Significado|
|-----------|-------------|
|0x0000|El archivo se puede leer o escribir en él.|
|0x0001|El archivo se puede leer pero no escribir en él.|
|0x0002|El archivo está oculto y no aparece en una lista de directorios.|
|0x0004|El archivo es un archivo del sistema.|
|0x0010|El nombre especificado por *lpszWildCard* especifica un directorio.|
|0x0020|El archivo se ha archivado.|
|0x4000|Incluye todas las unidades que coinciden con el nombre especificado por *lpszWildCard*.|
|0x8000|Marca exclusiva. Si se establece la marca Exclusive, solo se enumeran los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".|

*lpszWildCard*<br/>
Apunta a una cadena de especificación de archivo. La cadena puede contener caracteres comodín (por ejemplo, *.\*).

### <a name="return-value"></a>Valor devuelto

Índice de base cero del último nombre de archivo agregado a la lista. El valor devuelto es LB_ERR si se produce un error; el valor devuelto es LB_ERRSPACE si no hay suficiente espacio disponible para almacenar las nuevas cadenas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox::D rawItem

Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro de lista dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero largo a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Comentarios

Los `itemAction` miembros `itemState` y de la `DRAWITEMSTRUCT` estructura definen la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro para implementar el dibujo de un `CListBox` objeto dibujado por el propietario. La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que esta función miembro finalice.

Vea [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de `DRAWITEMSTRUCT` la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>  CListBox::FindString

Busca la primera cadena en un cuadro de lista que contiene el prefijo especificado sin cambiar la selección del cuadro de lista.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si *nStartAfter* es-1, se busca en el cuadro de lista completo desde el principio.

*lpszItem*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de las mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento coincidente, o LB_ERR si la búsqueda no se ha realizado correctamente.

### <a name="remarks"></a>Comentarios

Utilice la función miembro [SelectString](#selectstring) para buscar y seleccionar una cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>  CListBox::FindStringExact

Busca la primera cadena de cuadro de lista que coincide con la cadena especificada en *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parámetros

*nIndexStart*<br/>
Especifica el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nIndexStart*. Si *nIndexStart* es-1, se busca en el cuadro de lista completo desde el principio.

*lpszFind*<br/>
Apunta a la cadena terminada en null que se va a buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue entre mayúsculas y minúsculas, por lo que la cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Índice del elemento coincidente, o LB_ERR si la búsqueda no se ha realizado correctamente.

### <a name="remarks"></a>Comentarios

Si el cuadro de lista se creó con un estilo dibujado por el propietario pero sin el estilo [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles), la función miembro `FindStringExact` intenta hacer coincidir el valor palabra con el valor de *lpszFind*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

Recupera el índice de base cero del elemento de delimitador actual en el cuadro de lista.

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice del elemento de delimitador actual, si es correcto; de lo contrario, LB_ERR.

### <a name="remarks"></a>Comentarios

En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o el último elemento de un bloque de elementos seleccionados contiguos.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: SetAnchorIndex](#setanchorindex).

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

Determina el índice del elemento que tiene el rectángulo de foco en un cuadro de lista de selección múltiple.

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento que tiene el rectángulo de foco en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es el índice del elemento seleccionado, si existe.

### <a name="remarks"></a>Comentarios

El elemento puede estar o no seleccionado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: SetCaretIndex](#setcaretindex).

##  <a name="getcount"></a>  CListBox::GetCount

Recupera el número de elementos de un cuadro de lista.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos en el cuadro de lista o LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

El recuento devuelto es uno mayor que el valor de índice del último elemento (el índice está basado en cero).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

Recupera el índice de base cero del elemento actualmente seleccionado, si existe, en un cuadro de lista de selección única.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento actualmente seleccionado si es un cuadro de lista de selección única. Es LB_ERR si no hay ningún elemento seleccionado actualmente.

En un cuadro de lista de selección múltiple, el índice del elemento que tiene el foco.

### <a name="remarks"></a>Comentarios

No llame a `GetCurSel` para un cuadro de lista de selección múltiple. Use [CListBox:: GetSelItems](#getselitems) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox:: GetHorizontalExtent

Recupera del cuadro de lista el ancho, en píxeles, que se puede desplazar horizontalmente.

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho desplazable del cuadro de lista, en píxeles.

### <a name="remarks"></a>Comentarios

Esto solo es aplicable si el cuadro de lista tiene una barra de desplazamiento horizontal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

Recupera el valor de palabra proporcionado por la aplicación asociado al elemento de cuadro de lista especificado.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El valor asociado al elemento o LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

El valor de palabra era el parámetro *dwItemData* de una llamada a [SetItemData](#setitemdata) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro de lista especificado como un puntero (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Recupera un puntero o-1 si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>  CListBox::GetItemHeight

Determina el alto de los elementos de un cuadro de lista.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro solo se usa si el cuadro de lista tiene el estilo LBS_OWNERDRAWVARIABLE; de lo contrario, debe establecerse en 0.

### <a name="return-value"></a>Valor devuelto

Alto, en píxeles, de los elementos del cuadro de lista. Si el cuadro de lista tiene el estilo [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , el valor devuelto es el alto del elemento especificado por *NINDEX*. Si se produce un error, el valor devuelto es LB_ERR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

Recupera las dimensiones del rectángulo que delimita un elemento de cuadro de lista tal como se muestra actualmente en la ventana de cuadro de lista.

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

*lpRect*<br/>
Especifica un puntero largo a una [estructura Rect](/windows/win32/api/windef/ns-windef-rect) que recibe las coordenadas de cliente de cuadro de lista del elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

Recupera el número de elementos por columna.

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos por columna del `CListBox` objeto.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del mensaje [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo) , tal y como se describe en el Windows SDK.

##  <a name="getlocale"></a>  CListBox::GetLocale

Recupera la configuración regional utilizada por el cuadro de lista.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) de las cadenas en el cuadro de lista.

### <a name="remarks"></a>Comentarios

La configuración regional se usa, por ejemplo, para determinar el criterio de ordenación de las cadenas en un cuadro de lista ordenado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: setlocale](#setlocale).

##  <a name="getsel"></a>  CListBox::GetSel

Recupera el estado de selección de un elemento.

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento.

### <a name="return-value"></a>Valor devuelto

Un número positivo si el elemento especificado está seleccionado; de lo contrario, es 0. El valor devuelto es LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Esta función miembro funciona con cuadros de lista de selección única y múltiple.

Para recuperar el índice del elemento de cuadro de lista seleccionado actualmente, use [CListBox:: GetCurSel](#getcursel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

Recupera el número total de elementos seleccionados en un cuadro de lista de selección múltiple.

```
int GetSelCount() const;
```

### <a name="return-value"></a>Valor devuelto

Recuento de los elementos seleccionados en un cuadro de lista. Si el cuadro de lista es un cuadro de lista de selección única, el valor devuelto es LB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: GetSelItems](#getselitems).

##  <a name="getselitems"></a>  CListBox::GetSelItems

Rellena un búfer con una matriz de enteros que especifica el número de elemento de los elementos seleccionados en un cuadro de lista de selección múltiple.

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>Parámetros

*nMaxItems*<br/>
Especifica el número máximo de elementos seleccionados cuyos números de elemento se van a colocar en el búfer.

*rgIndex*<br/>
Especifica un puntero a un búfer lo suficientemente grande como para el número de enteros especificado por *nMaxItems*.

### <a name="return-value"></a>Valor devuelto

Número real de elementos colocados en el búfer. Si el cuadro de lista es un cuadro de lista de selección única, el valor `LB_ERR`devuelto es.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

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
Apunta al búfer que recibe la cadena. El búfer debe tener espacio suficiente para la cadena y un carácter nulo de terminación. El tamaño de la cadena se puede determinar con anterioridad mediante una llamada `GetTextLen` a la función miembro.

*rString*<br/>
Referencia a un objeto `CString`.

### <a name="return-value"></a>Valor devuelto

La longitud (en bytes) de la cadena, sin incluir el carácter nulo de terminación. Si *NINDEX* no especifica un índice válido, el valor devuelto es LB_ERR.

### <a name="remarks"></a>Comentarios

La segunda forma de esta función miembro rellena un `CString` objeto con el texto de la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

Obtiene la longitud de una cadena en un elemento de cuadro de lista.

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la cadena.

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena en caracteres, sin incluir el carácter nulo de terminación. Si *NINDEX* no especifica un índice válido, el valor devuelto es LB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: gettext](#gettext).

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

Recupera el índice de base cero del primer elemento visible de un cuadro de lista.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del primer elemento visible de un cuadro de lista si se realiza correctamente, de lo contrario, LB_ERR.

### <a name="remarks"></a>Comentarios

Inicialmente, el elemento 0 está en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, es posible que haya otro elemento en la parte superior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>CListBox:: InitStorage

Asigna memoria para almacenar los elementos de cuadro de lista.

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>Parámetros

*nItems*<br/>
Especifica el número de elementos que se van a agregar.

*nBytes*<br/>
Especifica la cantidad de memoria, en bytes, que se va a asignar para las cadenas de elementos.

### <a name="return-value"></a>Valor devuelto

Si es correcto, el número máximo de elementos que puede almacenar el cuadro de lista antes de que se necesite una reasignación de memoria, de lo contrario, LB_ERRSPACE, lo que significa que no hay suficiente memoria disponible.

### <a name="remarks"></a>Comentarios

Llame a esta función antes de agregar un gran número de elementos `CListBox`a un.

Esta función ayuda a acelerar la inicialización de cuadros de lista que tienen un gran número de elementos (más de 100). Asigna previamente la cantidad de memoria especificada para que las siguientes funciones de [addString](#addstring), [InsertString](#insertstring)y [dir](#dir) tarden el menor tiempo posible. Puede usar estimaciones para los parámetros. Si sobrestima, se asignará una memoria adicional; Si se subestima, se usa la asignación normal para los elementos que superan la cantidad preasignada.

Solo Windows 95/98: El parámetro *nItems* está limitado a valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista solo está limitado por la memoria disponible.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>CListBox:: InsertString

Inserta una cadena en el cuadro de lista.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero de la posición en la que se va a insertar la cadena. Si este parámetro es-1, la cadena se agrega al final de la lista.

*lpszItem*<br/>
Apunta a la cadena terminada en null que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es LB_ERR si se produce un error; el valor devuelto es LB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Comentarios

A diferencia de la función miembro [AddString](#addstring), `InsertString` no hace que se ordene una lista con el estilo [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

Determina el elemento de cuadro de lista más cercano al punto especificado en *PT*.

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Punto en el que se va a buscar el elemento más cercano, especificado en relación con la esquina superior izquierda del área cliente del cuadro de lista.

*bOutside*<br/>
Referencia a una variable BOOL que se establecerá en TRUE si *PT* está fuera del área cliente del elemento de cuadro de lista más próximo, false si *PT* está dentro del área cliente del elemento de cuadro de lista más próximo.

### <a name="return-value"></a>Valor devuelto

Índice del elemento más próximo al punto especificado en *PT*.

### <a name="remarks"></a>Comentarios

Puede usar esta función para determinar en qué elemento de cuadro de lista se mueve el cursor del mouse.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CListBox:: SetAnchorIndex](#setanchorindex).

##  <a name="measureitem"></a>  CListBox::MeasureItem

Lo llama el marco de trabajo cuando se crea un cuadro de lista con un estilo dibujado por el propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Puntero largo a una estructura [measureitemstruct (](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Comentarios

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro y rellene la `MEASUREITEMSTRUCT` estructura para informar a las ventanas de las dimensiones del cuadro de lista. Si el cuadro de lista se crea con el estilo [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , el marco de trabajo llama a esta función miembro para cada elemento del cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

Para obtener más información sobre cómo usar el estilo [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) en un cuadro de lista dibujado por el `SubclassDlgItem` propietario creado con `CWnd`la función miembro de, vea la explicación en la [Nota técnica 14](../../mfc/tn014-custom-controls.md).

Vea [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de `MEASUREITEMSTRUCT` la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

Quita todos los elementos de un cuadro de lista.

```
void ResetContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>CListBox:: SelectString

Busca un elemento de cuadro de lista que coincida con la cadena especificada y, si se encuentra un elemento coincidente, selecciona el elemento.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si *nStartAfter* es-1, se busca en el cuadro de lista completo desde el principio.

*lpszItem*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de las mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Índice del elemento seleccionado si la búsqueda se realizó correctamente. Si la búsqueda no se realizó correctamente, el valor devuelto es LB_ERR y no se cambia la selección actual.

### <a name="remarks"></a>Comentarios

Si es necesario, el cuadro de lista se desplaza para que el elemento seleccionado se muestre en la vista.

Esta función miembro no se puede usar con un cuadro de lista que tenga el estilo [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

Un elemento se selecciona solo si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena especificada por *lpszItem*.

Utilice la `FindString` función miembro para buscar una cadena sin seleccionar el elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

Selecciona varios elementos consecutivos en un cuadro de lista de selección múltiple.

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>Parámetros

*bSelect*<br/>
Especifica cómo establecer la selección. Si *bSelect* es true, la cadena se selecciona y se resalta; Si es FALSE, se quita el resaltado y ya no se selecciona la cadena.

*nFirstItem*<br/>
Especifica el índice de base cero del primer elemento que se va a establecer.

*nLastItem*<br/>
Especifica el índice de base cero del último elemento que se va a establecer.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Use esta función miembro solo con cuadros de lista de selección múltiple. Si solo tiene que seleccionar un elemento en un cuadro de lista de selección múltiple, es decir, si *nFirstItem* es igual a *nLastItem* , llame a la función miembro [SetSel](#setsel) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

Establece el delimitador de un cuadro de lista de selección múltiple para comenzar una selección extendida.

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista que será el delimitador.

### <a name="remarks"></a>Comentarios

En un cuadro de lista de selección múltiple, el elemento delimitador es el primer o el último elemento de un bloque de elementos seleccionados contiguos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

Establece el rectángulo de foco en el elemento en el índice especificado de un cuadro de lista de selección múltiple.

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento que va a recibir el rectángulo de foco en el cuadro de lista.

*bScroll*<br/>
Si este valor es 0, el elemento se desplaza hasta que esté totalmente visible. Si este valor no es 0, el elemento se desplaza hasta que esté al menos parcialmente visible.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Si el elemento no está visible, se desplaza a la vista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>  CListBox::SetColumnWidth

Establece el ancho en píxeles de todas las columnas de un cuadro de lista de varias columnas (creado con el estilo [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) ).

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>Parámetros

*cxWidth*<br/>
Especifica el ancho en píxeles de todas las columnas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

Selecciona una cadena y la desplaza a la vista, si es necesario.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parámetros

*nSelect*<br/>
Especifica el índice de base cero de la cadena que se va a seleccionar. Si *nSeleccione* es-1, el cuadro de lista se establece para que no tenga ninguna selección.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Cuando se selecciona la nueva cadena, el cuadro de lista quita el resaltado de la cadena seleccionada anteriormente.

Use esta función miembro solo con cuadros de lista de selección única.

Para establecer o quitar una selección de un cuadro de lista de selección múltiple, use [CListBox:: SetSel](#setsel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox:: SetHorizontalExtent

Establece el ancho, en píxeles, por el que se puede desplazar un cuadro de lista horizontalmente.

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>Parámetros

*cxExtent*<br/>
Especifica el número de píxeles que se puede desplazar horizontalmente el cuadro de lista.

### <a name="remarks"></a>Comentarios

Si el tamaño del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente los elementos del cuadro de lista. Si el cuadro de lista es tan grande o mayor que este valor, se oculta la barra de desplazamiento horizontal.

Para responder a una llamada a `SetHorizontalExtent`, el cuadro de lista se debe haber definido con el estilo [WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles) .

Esta función miembro no es útil para los cuadros de lista de varias columnas. En el caso de los cuadros de lista `SetColumnWidth` de varias columnas, llame a la función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>  CListBox::SetItemData

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
Especifica el valor que se va a asociar al elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>  CListBox::SetItemDataPtr

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
Especifica el puntero que se va a asociar al elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Este puntero sigue siendo válido mientras dure el cuadro de lista, aunque la posición relativa del elemento en el cuadro de lista puede cambiar a medida que se agregan o quitan elementos. Por lo tanto, el índice del elemento en el cuadro puede cambiar, pero el puntero sigue siendo confiable.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>  CListBox::SetItemHeight

Establece el alto de los elementos de un cuadro de lista.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento en el cuadro de lista. Este parámetro solo se usa si el cuadro de lista tiene el estilo LBS_OWNERDRAWVARIABLE; de lo contrario, debe establecerse en 0.

*cyItemHeight*<br/>
Especifica el alto, en píxeles, del elemento.

### <a name="return-value"></a>Valor devuelto

LB_ERR si el índice o el alto no son válidos.

### <a name="remarks"></a>Comentarios

Si el cuadro de lista tiene el estilo [LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) , esta función establece el alto del elemento especificado por *NINDEX*. De lo contrario, esta función establece el alto de todos los elementos del cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

Establece el identificador de configuración regional para este cuadro de lista.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parámetros

*nNewLocale*<br/>
Nuevo valor de identificador de configuración regional (LCID) que se va a establecer para el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) anterior para este cuadro de lista.

### <a name="remarks"></a>Comentarios

Si `SetLocale` no se llama a, la configuración regional predeterminada se obtiene del sistema. Se puede modificar la configuración regional predeterminada del sistema mediante la aplicación regional (o internacional) del panel de control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox:: SetSel

Selecciona una cadena en un cuadro de lista de selección múltiple.

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la cadena que se va a establecer. Si es-1, la selección se agrega o se quita de todas las cadenas, dependiendo del valor de *bSelect*.

*bSelect*<br/>
Especifica cómo establecer la selección. Si *bSelect* es true, la cadena se selecciona y se resalta; Si es FALSE, se quita el resaltado y ya no se selecciona la cadena. La cadena especificada está seleccionada y resaltada de forma predeterminada.

### <a name="return-value"></a>Valor devuelto

LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

Use esta función miembro solo con cuadros de lista de selección múltiple.

Para seleccionar un elemento de un cuadro de lista de selección única, use [CListBox:: SetCurSel](#setcursel).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox:: SetTabStops

Establece las posiciones de tabulación en un cuadro de lista.

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>Parámetros

*cxEachStop*<br/>
Las tabulaciones se establecen en cada unidad de cuadro de diálogo *cxEachStop* . Consulte *rgTabStops* para obtener una descripción de una unidad de cuadro de diálogo.

*nTabStops*<br/>
Especifica el número de paradas de tabulación que se van a tener en el cuadro de lista.

*rgTabStops*<br/>
Apunta al primer miembro de una matriz de enteros que contiene las posiciones de tabulación en las unidades de cuadro de diálogo. Una unidad de cuadro de diálogo es una distancia horizontal o vertical. Una unidad de cuadro de diálogo horizontal es igual a una cuarta parte de la unidad de ancho base del cuadro de diálogo actual y una unidad de cuadro de diálogo vertical es igual a una octava parte de la unidad de alto de cuadro de diálogo actual. Las unidades base de cuadro de diálogo se calculan en función del alto y el ancho de la fuente actual del sistema. La `GetDialogBaseUnits` función de Windows devuelve las unidades base de diálogo actuales en píxeles. Las tabulaciones se deben ordenar en orden ascendente; no se permiten las pestañas atrás.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se han establecido todas las pestañas; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Para establecer el tamaño predeterminado de 2 unidades de cuadro de diálogo para las tabulaciones, llame a la versión sin parámetros de esta función miembro. Para establecer las tabulaciones en un tamaño distinto de 2, llame a la versión con el argumento *cxEachStop* .

Para establecer las tabulaciones en una matriz de tamaños, use la versión con los argumentos *rgTabStops* y *nTabStops* . Se establecerá una detención de tabulación para cada valor de *rgTabStops*, hasta el número especificado por *nTabStops*.

Para responder a una llamada a la `SetTabStops` función miembro, el cuadro de lista se debe haber creado con el estilo [LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

Garantiza que un determinado elemento de cuadro de lista está visible.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Cero si es correcto, o LB_ERR si se produce un error.

### <a name="remarks"></a>Comentarios

El sistema desplaza el cuadro de lista hasta que el elemento especificado por *NINDEX* aparezca en la parte superior del cuadro de lista o hasta que se alcance el intervalo de desplazamiento máximo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>  CListBox::VKeyToItem

Lo llama el marco de trabajo cuando la ventana primaria del cuadro de lista recibe un mensaje WM_VKEYTOITEM del cuadro de lista.

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nKey*<br/>
Código de tecla virtual de la tecla que el usuario presionó. Para obtener una lista de códigos de tecla virtual estándar, vea Winuser. h

*nIndex*<br/>
La posición actual del símbolo de intercalación del cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Devuelve-2 para ninguna acción más,-1 para la acción predeterminada o un número no negativo para especificar un índice de un elemento de cuadro de lista en el que realizar la acción predeterminada para la pulsación de tecla.

### <a name="remarks"></a>Comentarios

El cuadro de lista envía el mensaje WM_VKEYTOITEM cuando recibe un mensaje WM_KEYDOWN, pero solo si el cuadro de lista cumple los dos elementos siguientes:

- Tiene establecido el estilo [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) .

- Tiene al menos un elemento.

No debe llamar nunca a esta función. Invalide esta función para proporcionar su propio control personalizado de los mensajes del teclado.

Debe devolver un valor para indicar al marco de trabajo qué acción ha realizado la invalidación. Un valor devuelto de-2 indica que la aplicación controló todos los aspectos de la selección del elemento y no requiere ninguna acción adicional por parte del cuadro de lista. Antes de devolver-2, puede establecer la selección o desplace el símbolo de intercalación o ambos. Para establecer la selección, use [SetCurSel](#setcursel) o [SetSel](#setsel). Para desplace el símbolo de intercalación, use [SetCaretIndex](#setcaretindex).

Un valor devuelto de-1 indica que el cuadro de lista debe realizar la acción predeterminada en respuesta a la pulsación de tecla. La implementación predeterminada devuelve-1.

Un valor devuelto de 0 o superior especifica el índice de un elemento del cuadro de lista e indica que el cuadro de lista debe realizar la acción predeterminada de la pulsación de tecla en el elemento determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit (clase)](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic (clase)](../../mfc/reference/cstatic-class.md)
