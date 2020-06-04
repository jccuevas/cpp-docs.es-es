---
title: CComboBox (clase)
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: dc803fb4ce137b256f4197afaec7bc3327e1e85a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754836"
---
# <a name="ccombobox-class"></a>CComboBox (clase)

Proporciona la funcionalidad de un cuadro combinado de Windows.

## <a name="syntax"></a>Sintaxis

```
class CComboBox : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBox::CComboBox](#ccombobox)|Construye un objeto `CComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Agrega una cadena al final de la lista en el cuadro de lista de un cuadro combinado o en la posición ordenada de los cuadros de lista con el estilo CBS_SORT.|
|[CComboBox::Clear](#clear)|Elimina (borra) la selección actual, si existe, en el control de edición.|
|[CComboBox::CompareItem](#compareitem)|Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento de lista en un cuadro combinado ordenado dibujado por el propietario.|
|[CComboBox::Copiar](#copy)|Copia la selección actual, si existe, en el Portapapeles en formato CF_TEXT.|
|[CComboBox::Crear](#create)|Crea el cuadro combinado y `CComboBox` lo adjunta al objeto.|
|[CComboBox::Corte](#cut)|Elimina (corta) la selección actual, si existe, en el control de edición y copia el texto eliminado en el Portapapeles en formato CF_TEXT.|
|[CComboBox::DeleteItem](#deleteitem)|Llamado por el marco de trabajo cuando se elimina un elemento de lista de un cuadro combinado dibujado por el propietario.|
|[CComboBox::DeleteString](#deletestring)|Elimina una cadena del cuadro de lista de un cuadro combinado.|
|[CComboBox::Dir](#dir)|Agrega una lista de nombres de archivo al cuadro de lista de un cuadro combinado.|
|[CComboBox::DrawItem](#drawitem)|Llamado por el marco de trabajo cuando cambia un aspecto visual de un cuadro combinado dibujado por el propietario.|
|[CComboBox::FindString](#findstring)|Busca la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.|
|[CComboBox::FindStringExact](#findstringexact)|Busca la primera cadena de cuadro de lista (en un cuadro combinado) que coincide con la cadena especificada.|
|[CComboBox::GetComboBoxInfo](#getcomboboxinfo)|Recupera información sobre `CComboBox` el objeto.|
|[CComboBox::GetCount](#getcount)|Recupera el número de elementos del cuadro de lista de un cuadro combinado.|
|[CComboBox::GetCueBanner](#getcuebanner)|Obtiene el texto de referencia que se muestra para un control de cuadro combinado.|
|[CComboBox::GetCurSel](#getcursel)|Recupera el índice del elemento seleccionado actualmente, si existe, en el cuadro de lista de un cuadro combinado.|
|[CComboBox::GetDroppedControlRect](#getdroppedcontrolrect)|Recupera las coordenadas de pantalla del cuadro de lista visible (abajo) de un cuadro combinado desplegable.|
|[CComboBox::GetDroppedState](#getdroppedstate)|Determina si el cuadro de lista de un cuadro combinado desplegable está visible (abajo).|
|[CComboBox::GetDroppedWidth](#getdroppedwidth)|Recupera el ancho mínimo permitido para la parte del cuadro de lista desplegable de un cuadro combinado.|
|[CComboBox::GetEditSel](#geteditsel)|Obtiene las posiciones de carácter inicial y final de la selección actual en el control de edición de un cuadro combinado.|
|[CComboBox::GetExtendedUI](#getextendedui)|Determina si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.|
|[CComboBox::GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que la parte del cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|
|[CComboBox::GetItemData](#getitemdata)|Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado.|
|[CComboBox::GetItemDataPtr](#getitemdataptr)|Recupera el puntero de 32 bits proporcionado por la aplicación que está asociado con el elemento de cuadro combinado especificado.|
|[CComboBox::GetItemHeight](#getitemheight)|Recupera el alto de los elementos de lista en un cuadro combinado.|
|[CComboBox::GetLBText](#getlbtext)|Obtiene una cadena del cuadro de lista de un cuadro combinado.|
|[CComboBox::GetLBTextLen](#getlbtextlen)|Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox::GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro combinado.|
|[CComboBox::GetMinVisible](#getminvisible)|Obtiene el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|
|[CComboBox::GetTopIndex](#gettopindex)|Devuelve el índice del primer elemento visible en la parte del cuadro de lista del cuadro combinado.|
|[CComboBox::InitStorage](#initstorage)|Preasigna bloques de memoria para elementos y cadenas en la parte del cuadro de lista del cuadro combinado.|
|[CComboBox::InsertString](#insertstring)|Inserta una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox::LimitText](#limittext)|Limita la longitud del texto que el usuario puede introducir en el control de edición de un cuadro combinado.|
|[CComboBox::MeasureItem](#measureitem)|Llamado por el marco de trabajo para determinar las dimensiones del cuadro combinado cuando se crea un cuadro combinado dibujado por el propietario.|
|[CComboBox::Paste](#paste)|Inserta los datos del Portapapeles en el control de edición en la posición actual del cursor. Los datos solo se insertan si el Portapapeles contiene datos en formato CF_TEXT.|
|[CComboBox::ResetContent](#resetcontent)|Quita todos los elementos del cuadro de lista y edita el control de un cuadro combinado.|
|[CComboBox::SelectString](#selectstring)|Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y copia la cadena en el control de edición.|
|[CComboBox::SetCueBanner](#setcuebanner)|Establece el texto de referencia que se muestra para un control de cuadro combinado.|
|[CComboBox::SetCurSel](#setcursel)|Selecciona una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox::SetDroppedWidth](#setdroppedwidth)|Establece el ancho mínimo permitido para la parte del cuadro de lista desplegable de un cuadro combinado.|
|[CComboBox::SetEditSel](#seteditsel)|Selecciona caracteres en el control de edición de un cuadro combinado.|
|[CComboBox::SetExtendedUI](#setextendedui)|Selecciona la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tiene el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.|
|[CComboBox::SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que la parte del cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|
|[CComboBox::SetItemData](#setitemdata)|Establece el valor de 32 bits asociado al elemento especificado en un cuadro combinado.|
|[CComboBox::SetItemDataPtr](#setitemdataptr)|Establece el puntero de 32 bits asociado al elemento especificado en un cuadro combinado.|
|[CComboBox::SetItemHeight](#setitemheight)|Establece el alto de los elementos de lista en un cuadro combinado o el alto de la parte de control de edición (o texto estático) de un cuadro combinado.|
|[CComboBox::SetLocale](#setlocale)|Establece el identificador de configuración regional de un cuadro combinado.|
|[CComboBox::SetMinVisibleItems](#setminvisibleitems)|Establece el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|
|[CComboBox::SetTopIndex](#settopindex)|Indica la parte del cuadro de lista del cuadro combinado para mostrar el elemento con el índice especificado en la parte superior.|
|[CComboBox::ShowDropDown](#showdropdown)|Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Observaciones

Un cuadro combinado consta de un cuadro de lista combinado con un control estático o un control de edición. La parte del cuadro de lista del control se puede mostrar en todo momento o solo puede aparecer cuando el usuario selecciona la flecha desplegable junto al control.

El elemento seleccionado actualmente (si existe) en el cuadro de lista se muestra en el control estático o de edición. Además, si el cuadro combinado tiene el estilo de lista desplegable, el usuario puede escribir el carácter inicial de uno de los elementos de la lista y el cuadro de lista, si está visible, resaltará el siguiente elemento con ese carácter inicial.

En la tabla siguiente se comparan los tres [estilos](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)de cuadro combinado.

|Estilo|Cuándo está visible el cuadro de lista|Control estático o de edición|
|-----------|-------------------------------|-----------------------------|
|Simple|Siempre|Editar|
|Drop-down|Cuando se cae|Editar|
|Lista desplegable|Cuando se cae|estática|

Puede crear `CComboBox` un objeto a partir de una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, primero `CComboBox` llame `CComboBox` al constructor para construir el objeto; a continuación, llame a la [create](#create) función `CComboBox` miembro para crear el control y adjuntarlo al objeto.

Si desea controlar los mensajes de notificación de Windows enviados por `CDialog`un cuadro combinado a su elemento primario (normalmente una clase derivada de ), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes adopta la siguiente forma:

**ON\_**_Notificación_ **(** _id_, _memberFxn_ **)**

donde `id` especifica el identificador de ventana secundaria del control `memberFxn` de cuadro combinado que envía la notificación y es el nombre de la función miembro principal que ha escrito para controlar la notificación.

El prototipo de función del padre es el siguiente:

**afx_msg** `void` afx_msg `memberFxn` **( );**

No se puede predecir el orden en el que se enviarán determinadas notificaciones. En particular, puede producirse una notificación CBN_SELCHANGE antes o después de una notificación CBN_CLOSEUP.

Las posibles entradas de mapa de mensajes son las siguientes:

- ON_CBN_CLOSEUP (Windows 3.1 y versiones posteriores.) El cuadro de lista de un cuadro combinado se ha cerrado. Este mensaje de notificación no se envía para un cuadro combinado que tiene el estilo [CBS_SIMPLE.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

- ON_CBN_DBLCLK El usuario hace doble clic en una cadena en el cuadro de lista de un cuadro combinado. Este mensaje de notificación solo se envía para un cuadro combinado con el estilo CBS_SIMPLE. Para un cuadro combinado con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) no se puede hacer doble clic porque un solo clic oculta el cuadro de lista.

- ON_CBN_DROPDOWN El cuadro de lista de un cuadro combinado está a punto de soltarse (hacerse visible). Este mensaje de notificación solo puede producirse para un cuadro combinado con el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE El usuario ha realizado una acción que puede haber alterado el texto en la parte de control de edición de un cuadro combinado. A diferencia del mensaje CBN_EDITUPDATE, este mensaje se envía después de que Windows actualiza la pantalla. No se envía si el cuadro combinado tiene el estilo CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE La parte de control de edición de un cuadro combinado está a punto de mostrar texto alterado. Este mensaje de notificación se envía después de que el control haya formateado el texto, pero antes de que muestre el texto. No se envía si el cuadro combinado tiene el estilo CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE El cuadro combinado no puede asignar suficiente memoria para satisfacer una solicitud específica.

- ON_CBN_SELENDCANCEL (Windows 3.1 y versiones posteriores.) Indica que la selección del usuario debe cancelarse. El usuario hace clic en un elemento y, a continuación, hace clic en otra ventana o control para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes del mensaje de notificación CBN_CLOSEUP para indicar que se debe omitir la selección del usuario. El CBN_SELENDCANCEL o CBN_SELENDOK mensaje de notificación se envía incluso si no se envía el mensaje de notificación CBN_CLOSEUP (como en el caso de un cuadro combinado con el estilo CBS_SIMPLE).

- ON_CBN_SELENDOK El usuario selecciona un elemento y, a continuación, presiona la tecla ENTRAR o hace clic en la tecla FLECHA ABAJO para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes del mensaje CBN_CLOSEUP para indicar que la selección del usuario debe considerarse válida. El CBN_SELENDCANCEL o CBN_SELENDOK mensaje de notificación se envía incluso si no se envía el mensaje de notificación CBN_CLOSEUP (como en el caso de un cuadro combinado con el estilo CBS_SIMPLE).

- ON_CBN_KILLFOCUS El cuadro combinado está perdiendo el foco de entrada.

- ON_CBN_SELCHANGE La selección en el cuadro de lista de un cuadro combinado está a punto de cambiarse como resultado de que el usuario haga clic en el cuadro de lista o cambie la selección mediante las teclas de flecha. Al procesar este mensaje, el texto del control de edición `GetLBText` del cuadro combinado solo se puede recuperar a través de u otra función similar. `GetWindowText`no se puede utilizar.

- ON_CBN_SETFOCUS El cuadro combinado recibe el foco de entrada.

Si crea `CComboBox` un objeto dentro de un cuadro `CComboBox` de diálogo (a través de un recurso de cuadro de diálogo), el objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si incrusta `CComboBox` un objeto dentro de otro objeto de ventana, no es necesario destruirlo. Si crea `CComboBox` el objeto en la pila, se destruye automáticamente. Si crea `CComboBox` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo cuando se destruye el cuadro combinado de Windows.

**Nota** Si desea controlar WM_KEYDOWN y WM_CHAR mensajes, debe subclase de los controles de cuadro `CEdit` `CListBox`de edición y lista del cuadro combinado, derivar clases de y , y agregar controladores para esos mensajes a las clases derivadas. Para obtener más información, vea [CWnd::SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox::AddString

Agrega una cadena al cuadro de lista de un cuadro combinado.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
Apunta a la cadena terminada en null que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero de la cadena en el cuadro de lista. El valor devuelto se CB_ERR si se produce un error; el valor devuelto se CB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

Si el cuadro de lista no se creó con el [estilo CBS_SORT,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista se ordena.

> [!NOTE]
> Esta función no es `ComboBoxEx` compatible con el control de Windows. Para obtener más información sobre este control, vea [Controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

Para insertar una cadena en una ubicación específica dentro de la lista, utilice el [InsertString](#insertstring) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox::CComboBox

Construye un objeto `CComboBox`.

```
CComboBox();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox::Clear

Elimina (borra) la selección actual, si existe, en el control de edición del cuadro combinado.

```cpp
void Clear();
```

### <a name="remarks"></a>Observaciones

Para eliminar la selección actual y colocar el contenido eliminado en el Portapapeles, utilice la función miembro [Cortar.](#cut)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox::CompareItem

Llamado por el marco de trabajo para determinar la posición relativa de un nuevo elemento en la parte del cuadro de lista de un cuadro combinado ordenado dibujada por el propietario.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpCompareItemStruct*<br/>
Un puntero largo a una estructura [COMPAREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-compareitemstruct)

### <a name="return-value"></a>Valor devuelto

Indica la posición relativa de los `COMPAREITEMSTRUCT` dos elementos descritos en la estructura. Puede ser cualquiera de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|- 1|El elemento 1 se ordena antes del elemento 2.|
|0|El artículo 1 y el elemento 2 se ordenan de la misma manera.|
|1|El elemento 1 se ordena después del elemento 2.|

Vea [CWnd::OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para `COMPAREITEMSTRUCT`obtener una descripción de .

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro combinado dibujada por el propietario con el estilo LBS_SORT, debe invalidar esta función miembro para ayudar al marco de trabajo a ordenar los nuevos elementos agregados al cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox::Copiar

Copia la selección actual, si existe, en el control de edición del cuadro combinado en el Portapapeles en formato CF_TEXT.

```cpp
void Copy();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox::Crear

Crea el cuadro combinado y `CComboBox` lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del cuadro combinado. Aplique cualquier combinación de [estilos de cuadro combinado](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) al cuadro.

*Rect*<br/>
Apunta a la posición y el tamaño del cuadro combinado. Puede ser una estructura `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o un objeto.

*pParentWnd*<br/>
Especifica la ventana primaria del cuadro `CDialog`combinado (normalmente un ). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Construir un `CComboBox` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CComboBox` llame a , que crea el cuadro combinado de Windows y lo adjunta al objeto.

Cuando `Create` se ejecuta, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al cuadro combinado.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) de la `CWnd` clase base. Para extender el control de mensajes `CComboBox`predeterminado, derive una clase de , agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control de cuadro combinado. :

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

- WS_VSCROLL Para agregar desplazamiento vertical para el cuadro de lista en el cuadro combinado

- WS_HSCROLL Para agregar desplazamiento horizontal para el cuadro de lista en el cuadro combinado

- WS_GROUP Para agrupar controles

- WS_TABSTOP Para incluir el cuadro combinado en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox::Corte

Elimina (corta) la selección actual, si existe, en el control de edición de cuadro combinado y copia el texto eliminado en el Portapapeles en formato CF_TEXT.

```cpp
void Cut();
```

### <a name="remarks"></a>Observaciones

Para eliminar la selección actual sin colocar el texto eliminado en el Portapapeles, llame a la [Clear](#clear) función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::DeleteItem

Llamado por el marco de trabajo cuando el `CComboBox` usuario elimina un elemento de un objeto dibujado por el propietario o destruye el cuadro combinado.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDeleteItemStruct*<br/>
Puntero largo a una estructura [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) de Windows que contiene información sobre el elemento eliminado. Vea [CWnd::OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de esta estructura.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Reemplace esta función para volver a dibujar el cuadro combinado según sea necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString

Elimina el elemento en la posición *nIndex* del cuadro combinado.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de la cadena que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es un recuento de las cadenas restantes de la lista. El valor devuelto se CB_ERR si *nIndex* especifica un índice mayor que el número de elementos de la lista.

### <a name="remarks"></a>Observaciones

Todos los elementos que siguen *a nIndex* ahora se mueven hacia abajo una posición. Por ejemplo, si un cuadro combinado contiene dos elementos, eliminar el primer elemento hará que el elemento restante esté ahora en la primera posición. *nIndex*n.o 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir

Agrega una lista de nombres de archivo o unidades al cuadro de lista de un cuadro combinado.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parámetros

*Attr*<br/>
Puede ser cualquier combinación de los valores **de enumeración** descritos en [CFile::GetStatus](../../mfc/reference/cfile-class.md#getstatus) o cualquier combinación de los siguientes valores:

- DDL_READWRITE archivo se puede leer o escribir en.

- DDL_READONLY archivo se puede leer desde pero no se escribe en.

- DDL_HIDDEN archivo está oculto y no aparece en una lista de directorios.

- DDL_SYSTEM File es un archivo de sistema.

- DDL_DIRECTORY El nombre especificado por *lpszWildCard* especifica un directorio.

- DDL_ARCHIVE archivo se ha archivado.

- DDL_DRIVES Incluir todas las unidades que coincidan con el nombre especificado por *lpszWildCard*.

- DDL_EXCLUSIVE bandera Exclusiva. Si se establece la marca exclusiva, solo se muestran los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".

*lpszWildCard*<br/>
Apunta a una cadena de especificación de archivo. La cadena puede contener comodines\*(por ejemplo, *. ).

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero del último nombre de archivo agregado a la lista. El valor devuelto se CB_ERR si se produce un error; el valor devuelto se CB_ERRSPACE si no hay suficiente espacio disponible para almacenar las nuevas cadenas.

### <a name="remarks"></a>Observaciones

Esta función no es `ComboBoxEx` compatible con el control de Windows. Para obtener más información sobre este control, vea [Controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un cuadro combinado de dibujo del propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar. Vea [CWnd::OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de esta estructura.

De forma predeterminada, esta función miembro no hace nada. Invalidar esta función miembro para implementar `CComboBox` el dibujo para un objeto de dibujo del propietario. Antes de que finalice esta función miembro, la aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de visualización proporcionado en *lpDrawItemStruct*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::FindString

Busca, pero no selecciona, la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si es -1, todo el cuadro de lista se busca desde el principio.

*lpszString*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero del elemento coincidente. Es CB_ERR si la búsqueda no se realizó correctamente.

### <a name="remarks"></a>Observaciones

Esta función no es `ComboBoxEx` compatible con el control de Windows. Para obtener más información sobre este control, vea [Controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::FindStringExact

Llame `FindStringExact` a la función miembro para buscar la primera cadena de cuadro de lista (en un cuadro combinado) que coincida con la cadena especificada en *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parámetros

*nIndexStart*<br/>
Especifica el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nIndexStart*. Si *nIndexStart* es -1, se busca en todo el cuadro de lista desde el principio.

*lpszFind*<br/>
Apunta a la cadena terminada en null que se va a buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue mayúsculas de minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento coincidente o CB_ERR si la búsqueda no se realizó correctamente.

### <a name="remarks"></a>Observaciones

Si el cuadro combinado se creó con un estilo `FindStringExact` de dibujo del propietario pero sin el estilo [CBS_HASSTRINGS,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) intenta hacer coincidir el valor de doubleword con el valor de *lpszFind*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox::GetComboBoxInfo

Recupera información para `CComboBox` el objeto.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parámetros

*pcbi*<br/>
Un puntero a la [estructura COMBOBOXINFO.](/windows/win32/api/winuser/ns-winuser-comboboxinfo)

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje de CB_GETCOMBOBOXINFO,](/windows/win32/Controls/cb-getcomboboxinfo) como se describe en el Windows SDK.

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox::GetCount

Llame a esta función miembro para recuperar el número de elementos de la parte de cuadro de lista de un cuadro combinado.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos. El recuento devuelto es uno mayor que el valor de índice del último elemento (el índice es de base cero). Se CB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox::GetCueBanner

Obtiene el texto de referencia que se muestra para un control de cuadro combinado.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszText*|[fuera] Puntero a un búfer que recibe el texto del banner cue.|
|*cchText*|[en] Tamaño del búfer al que apunta el parámetro *lpszText.*|

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) objeto que contiene el texto del banner de referencia si existe; de lo `CString` contrario, un objeto que tiene longitud cero.

o bien

En la segunda sobrecarga, TRUE si este método es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cue texto es un mensaje que se muestra en el área de entrada del control de cuadro combinado. El texto de la cue se muestra hasta que el usuario proporciona la entrada.

Este método envía el [mensaje CB_GETCUEBANNER,](/windows/win32/Controls/cb-getcuebanner) que se describe en el Windows SDK.

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox::GetCurSel

Llame a esta función miembro para determinar qué elemento del cuadro combinado está seleccionado.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento seleccionado actualmente en el cuadro de lista de un cuadro combinado o CB_ERR si no se selecciona ningún elemento.

### <a name="remarks"></a>Observaciones

`GetCurSel`devuelve un índice en la lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox::GetDroppedControlRect

Llame `GetDroppedControlRect` a la función miembro para recuperar las coordenadas de pantalla del cuadro de lista visible (abajo) de un cuadro combinado desplegable.

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parámetros

*lprect*<br/>
Apunta a la [estructura RECT](/windows/win32/api/windef/ns-windef-rect) que va a recibir las coordenadas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox::GetDroppedState

Llame `GetDroppedState` a la función miembro para determinar si el cuadro de lista de un cuadro combinado desplegable es visible (descartado).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro de lista está visible; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox::GetDroppedWidth

Llame a esta función para recuperar el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el ancho mínimo permitido, en píxeles; de lo contrario, CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función solo se aplica a los cuadros combinados con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. El ancho mínimo permitido se puede establecer llamando a [SetDroppedWidth](#setdroppedwidth). Cuando se muestra la parte del cuadro de lista del cuadro combinado, su ancho es el mayor del ancho mínimo permitido o el ancho del cuadro combinado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo [de SetDroppedWidth](#setdroppedwidth).

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox::GetEditSel

Obtiene las posiciones de carácter inicial y final de la selección actual en el control de edición de un cuadro combinado.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de 32 bits que contiene la posición inicial en la palabra de orden bajo y la posición del primer carácter no seleccionado después del final de la selección en la palabra de orden superior. Si esta función se utiliza en un cuadro combinado sin un control de edición, se devuelve CB_ERR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox::GetExtendedUI

Llame `GetExtendedUI` a la función miembro para determinar si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro combinado tiene la interfaz de usuario extendida; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La interfaz de usuario extendida se puede identificar de las siguientes maneras:

- Al hacer clic en el control estático se muestra el cuadro de lista solo para cuadros combinados con el estilo [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

- Al pulsar la tecla FLECHA ABAJO se muestra el cuadro de lista (F4 está desactivado).

El desplazamiento en el control estático está deshabilitado cuando la lista de elementos no está visible (las teclas de flecha están deshabilitadas).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox::GetHorizontalExtent

Recupera del cuadro combinado el ancho en píxeles por el que se puede desplazar horizontalmente la parte del cuadro de lista del cuadro combinado.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho desplazable de la parte del cuadro de lista del cuadro combinado, en píxeles.

### <a name="remarks"></a>Observaciones

Esto solo es aplicable si la parte del cuadro de lista del cuadro combinado tiene una barra de desplazamiento horizontal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox::GetItemData

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de un elemento en el cuadro de lista del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El valor de 32 bits asociado al elemento o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El valor de 32 bits se puede establecer con el *dwItemData* parámetro de un [SetItemData](#setitemdata) llamada a la función miembro. Utilice `GetItemDataPtr` la función miembro si el valor de 32 bits que se va a recuperar es un puntero (**void** <strong>\*</strong>).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox::GetItemDataPtr

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado como un puntero (**void** <strong>\*</strong>).

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de un elemento en el cuadro de lista del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Recupera un puntero o -1 si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox::GetItemHeight

Llame `GetItemHeight` a la función miembro para recuperar el alto de los elementos de lista en un cuadro combinado.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el componente del cuadro combinado cuya altura se va a recuperar. Si el *nIndex* parámetro es -1, se recupera el alto de la parte de control de edición (o texto estático) del cuadro combinado. Si el cuadro combinado tiene el estilo [CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) *nIndex* especifica el índice de base cero del elemento de lista cuyo alto se va a recuperar. De lo contrario, *nIndex* debe establecerse en 0.

### <a name="return-value"></a>Valor devuelto

Altura, en píxeles, del elemento especificado en un cuadro combinado. El valor devuelto es CB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox::GetLBText

Obtiene una cadena del cuadro de lista de un cuadro combinado.

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la cadena de cuadro de lista que se va a copiar.

*lpszText*<br/>
Apunta a un búfer que va a recibir la cadena. El búfer debe tener suficiente espacio para la cadena y un carácter nulo de terminación.

*rString*<br/>
Referencia a un objeto `CString`.

### <a name="return-value"></a>Valor devuelto

La longitud (en bytes) de la cadena, excluyendo el carácter nulo de terminación. Si *nIndex* no especifica un índice válido, el valor devuelto se CB_ERR.

### <a name="remarks"></a>Observaciones

La segunda forma de esta `CString` función miembro rellena un objeto con el texto del elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox::GetLBTextLen

Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la cadena de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

La longitud de la cadena en bytes, excluyendo el carácter nulo de terminación. Si *nIndex* no especifica un índice válido, el valor devuelto se CB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox::GetLBText](#getlbtext).

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox::GetLocale

Recupera la configuración regional utilizada por el cuadro combinado.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) para las cadenas del cuadro combinado.

### <a name="remarks"></a>Observaciones

La configuración regional se utiliza, por ejemplo, para determinar el criterio de ordenación de las cadenas en un cuadro combinado ordenado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox::SetLocale](#setlocale).

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox::GetMinVisible

Obtiene el número mínimo de elementos visibles en la lista desplegable del control de cuadro combinado actual.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Valor devuelto

El número mínimo de elementos visibles en la lista desplegable actual.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje CB_GETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) que se describe en el Windows SDK.

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox::GetTopIndex

Recupera el índice de base cero del primer elemento visible en la parte del cuadro de lista del cuadro combinado.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del primer elemento visible en la parte del cuadro de lista del cuadro combinado si se realiza correctamente, CB_ERR lo contrario.

### <a name="remarks"></a>Observaciones

Inicialmente, el elemento 0 está en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, otro elemento puede estar en la parte superior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::InitStorage

Asigna memoria para almacenar elementos de cuadro de lista en la parte del cuadro de lista del cuadro combinado.

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

Si se realiza correctamente, el número máximo de elementos que la parte del cuadro de lista del cuadro combinado puede almacenar antes de que se necesite una reasignación de memoria, de lo contrario CB_ERRSPACE, lo que significa que no hay suficiente memoria disponible.

### <a name="remarks"></a>Observaciones

Llame a esta función antes de agregar un gran `CComboBox`número de elementos a la parte del cuadro de lista del archivo .

Solo Windows 95/98: el parámetro *wParam* está limitado a valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista está limitado solo por la memoria disponible.

Esta función ayuda a acelerar la inicialización de cuadros de lista que tienen un gran número de elementos (más de 100). Preasigna la cantidad especificada de memoria para que las funciones [AddString](#addstring), [InsertString](#insertstring)y [Dir](#dir) posteriores tomen el menor tiempo posible. Puede utilizar estimaciones para los parámetros. Si sobreestima, se asigna algo de memoria adicional; si subestima, la asignación normal se utiliza para los artículos que superan el importe preasignado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox::InsertString

Inserta una cadena en el cuadro de lista de un cuadro combinado.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la posición en el cuadro de lista que recibirá la cadena. Si este parámetro es -1, la cadena se agrega al final de la lista.

*lpszString*<br/>
Apunta a la cadena terminada en null que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es CB_ERR si se produce un error. El valor devuelto es CB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

A diferencia de la función miembro [AddString](#addstring) , la función miembro `InsertString` no provoca una lista con el estilo [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) que se va a ordenar.

> [!NOTE]
> Esta función no es `ComboBoxEx` compatible con el control de Windows. Para obtener más información sobre este control, vea [Controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox::LimitText

Limita la longitud en bytes del texto que el usuario puede introducir en el control de edición de un cuadro combinado.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parámetros

*nMaxChars*<br/>
Especifica la longitud (en bytes) del texto que el usuario puede escribir. Si este parámetro es 0, la longitud del texto se establece en 65.535 bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente. Si se llama para un cuadro combinado con el estilo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o para un cuadro combinado sin un control de edición, el valor devuelto es CB_ERR.

### <a name="remarks"></a>Observaciones

Si el cuadro combinado no tiene el estilo [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), establecer el límite de texto para que sea mayor que el tamaño del control de edición no tendrá ningún efecto.

`LimitText`sólo limita el texto que el usuario puede introducir. No tiene ningún efecto en ningún texto que ya esté en el control de edición cuando se envía el mensaje, ni afecta a la longitud del texto copiado en el control de edición cuando se selecciona una cadena en el cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox::MeasureItem

Llamado por el marco de trabajo cuando se crea un cuadro combinado con un estilo de dibujo por el propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Un puntero largo a una estructura [MEASUREITEMSTRUCT.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función `MEASUREITEMSTRUCT` miembro y rellene la estructura para informar a Windows de las dimensiones del cuadro de lista en el cuadro combinado. Si el cuadro combinado se crea con el [estilo CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) el marco de trabajo llama a esta función miembro para cada elemento en el cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

El uso del estilo CBS_OWNERDRAWFIXED en un cuadro combinado de dibujo `CWnd` por el propietario creado con el [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) función miembro de implica consideraciones de programación adicionales. Véase la discusión en la [Nota Técnica 14](../../mfc/tn014-custom-controls.md).

Vea [CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener `MEASUREITEMSTRUCT` una descripción de la estructura.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste

Inserta los datos del Portapapeles en el control de edición del cuadro combinado en la posición actual del cursor.

```cpp
void Paste();
```

### <a name="remarks"></a>Observaciones

Los datos solo se insertan si el Portapapeles contiene datos en formato CF_TEXT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox::ResetContent

Quita todos los elementos del cuadro de lista y edita el control de un cuadro combinado.

```cpp
void ResetContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox::SelectString

Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y la copia en el control de edición.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda llega a la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si es -1, todo el cuadro de lista se busca desde el principio.

*lpszString*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de letras mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento seleccionado si se encontró la cadena. Si la búsqueda no se realizó correctamente, el valor devuelto se CB_ERR y no se cambia la selección actual.

### <a name="remarks"></a>Observaciones

Una cadena solo se selecciona si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena de prefijo.

Tenga en `SelectString` `FindString` cuenta que las funciones `SelectString` miembro y encuentran una cadena, pero la función miembro también selecciona la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner

Establece el texto de referencia que se muestra para un control de cuadro combinado.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszText*|[en] Puntero a un búfer terminado en null que contiene el texto cue.|

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cue texto es un mensaje que se muestra en el área de entrada del control de cuadro combinado. El texto de la cue se muestra hasta que el usuario proporciona la entrada.

Este método envía el [mensaje CB_SETCUEBANNER,](/windows/win32/Controls/cb-setcuebanner) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_combobox*, que se usa para tener acceso mediante programación al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el banner cue para el control de cuadro combinado.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel

Selecciona una cadena en el cuadro de lista de un cuadro combinado.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parámetros

*nSeleccionar*<br/>
Especifica el índice de base cero de la cadena que se va a seleccionar. Si -1, se elimina cualquier selección actual en el cuadro de lista y se desactiva el control de edición.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento seleccionado si el mensaje se realiza correctamente. El valor devuelto se CB_ERR si *nSelect* es mayor que el número de elementos de la lista o si *nSelect* se establece en -1, lo que borra la selección.

### <a name="remarks"></a>Observaciones

Si es necesario, el cuadro de lista desplaza la cadena a la vista (si el cuadro de lista está visible). El texto del control de edición del cuadro combinado se cambia para reflejar la nueva selección. Se elimina cualquier selección anterior en el cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::SetDroppedWidth

Llame a esta función para establecer el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
El ancho mínimo permitido de la parte del cuadro de lista del cuadro combinado, en píxeles.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el nuevo ancho del cuadro de lista, de lo contrario CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función solo se aplica a los cuadros combinados con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. Cuando se muestra la parte del cuadro de lista del cuadro combinado, su ancho es el mayor del ancho mínimo permitido o el ancho del cuadro combinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox::SetEditSel

Selecciona caracteres en el control de edición de un cuadro combinado.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parámetros

*nStartChar*<br/>
Especifica la posición inicial. Si la posición inicial se establece en -1, se elimina cualquier selección existente.

*nEndChar*<br/>
Especifica la posición final. Si la posición final se establece en -1, se selecciona todo el texto desde la posición inicial hasta el último carácter del control de edición.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función miembro es correcta; de lo contrario 0. Es CB_ERR `CComboBox` si tiene el estilo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o no tiene un cuadro de lista.

### <a name="remarks"></a>Observaciones

Las posiciones se basan en cero. Para seleccionar el primer carácter del control de edición, especifique una posición inicial de 0. La posición final es para el carácter justo después del último carácter que se va a seleccionar. Por ejemplo, para seleccionar los primeros cuatro caracteres del control de edición, usaría una posición inicial de 0 y una posición final de 4.

> [!NOTE]
> Esta función no es `ComboBoxEx` compatible con el control de Windows. Para obtener más información sobre este control, vea [Controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox::GetEditSel](#geteditsel).

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::SetExtendedUI

Llame `SetExtendedUI` a la función miembro para seleccionar la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tiene el [estilo CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parámetros

*bExtendido*<br/>
Especifica si el cuadro combinado debe utilizar la interfaz de usuario extendida o la interfaz de usuario predeterminada. Un valor de TRUE selecciona la interfaz de usuario extendida; un valor de FALSE selecciona la interfaz de usuario estándar.

### <a name="return-value"></a>Valor devuelto

CB_OKAY si la operación se realiza correctamente o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

La interfaz de usuario extendida se puede identificar de las siguientes maneras:

- Al hacer clic en el control estático se muestra el cuadro de lista solo para cuadros combinados con el estilo CBS_DROPDOWNLIST.

- Al pulsar la tecla FLECHA ABAJO se muestra el cuadro de lista (F4 está desactivado).

El desplazamiento en el control estático está deshabilitado cuando la lista de elementos no está visible (las teclas de flecha están deshabilitadas).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox::GetExtendedUI](#getextendedui).

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::SetHorizontalExtent

Establece el ancho, en píxeles, por el que la parte del cuadro de lista del cuadro combinado se puede desplazar horizontalmente.

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parámetros

*nExtent*<br/>
Especifica el número de píxeles por el que se puede desplazar horizontalmente la parte del cuadro de lista del cuadro combinado.

### <a name="remarks"></a>Observaciones

Si el ancho del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente los elementos del cuadro de lista. Si el ancho del cuadro de lista es igual o mayor que este valor, la barra de desplazamiento horizontal está oculta o, si el cuadro combinado tiene el estilo [CBS_DISABLENOSCROLL,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) deshabilitado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::SetItemData

Establece el valor de 32 bits asociado al elemento especificado en un cuadro combinado.

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene un índice de base cero para el elemento que se va a establecer.

*dwItemData*<br/>
Contiene el nuevo valor que se va a asociar al elemento.

### <a name="return-value"></a>Valor devuelto

CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Utilice `SetItemDataPtr` la función miembro si el elemento de 32 bits va a ser un puntero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::SetItemDataPtr

Establece el valor de 32 bits asociado al elemento especificado en un cuadro combinado para que sea el puntero especificado (**void** <strong>\*</strong>).

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene un índice de base cero para el elemento.

*pData*<br/>
Contiene el puntero que se va a asociar al elemento.

### <a name="return-value"></a>Valor devuelto

CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

Este puntero sigue siendo válido durante la vida del cuadro combinado, aunque la posición relativa del elemento dentro del cuadro combinado puede cambiar a medida que se agregan o quitan elementos. Por lo tanto, el índice del elemento dentro del cuadro puede cambiar, pero el puntero sigue siendo confiable.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::SetItemHeight

Llame `SetItemHeight` a la función miembro para establecer el alto de los elementos de lista en un cuadro combinado o el alto de la parte de control de edición (o texto estático) de un cuadro combinado.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica si se establece el alto de los elementos de lista o la altura de la parte de control de edición (o texto estático) del cuadro combinado.

Si el cuadro combinado tiene el estilo [CBS_OWNERDRAWVARIABLE,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) *nIndex* especifica el índice de base cero del elemento de lista cuyo alto se va a establecer; de lo contrario, *nIndex* debe ser 0 y se establecerá el alto de todos los elementos de lista.

Si *nIndex* es -1, se debe establecer el alto de la parte de control de edición o texto estático del cuadro combinado.

*cyItemHeight*<br/>
Especifica el alto, en píxeles, del componente de cuadro combinado identificado por *nIndex*.

### <a name="return-value"></a>Valor devuelto

CB_ERR si el índice o la altura no son válidos; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La altura de la parte de control de edición (o texto estático) del cuadro combinado se establece independientemente de la altura de los elementos de lista. Una aplicación debe asegurarse de que el alto de la parte de control de edición (o texto estático) no es menor que el alto de un elemento de cuadro de lista determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::SetLocale

Establece el identificador de configuración regional para este cuadro combinado.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parámetros

*nNewLocale*<br/>
El nuevo valor de identificador de configuración regional (LCID) que se va a establecer para el cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El valor de identificador de configuración regional (LCID) anterior para este cuadro combinado.

### <a name="remarks"></a>Observaciones

Si `SetLocale` no se llama, la configuración regional predeterminada se obtiene del sistema. Esta configuración regional predeterminada del sistema se puede modificar mediante la aplicación Regional (o Internacional) del Panel de control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox::SetMinVisibleItems

Establece el número mínimo de elementos visibles en la lista desplegable del control de cuadro combinado actual.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iMinVisible*|[en] Especifica el número mínimo de elementos visibles.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje CB_SETMINVISIBLE,](/windows/win32/Controls/cb-setminvisible) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_combobox*, que se usa para tener acceso mediante programación al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se insertan 20 elementos en la lista desplegable de un control de cuadro combinado. A continuación, especifica que se mostrará un mínimo de 10 elementos cuando un usuario presiona la flecha desplegable.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex

Garantiza que un elemento determinado esté visible en la parte del cuadro de lista del cuadro combinado.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El sistema desplaza el cuadro de lista hasta que el elemento especificado por *nIndex* aparece en la parte superior del cuadro de lista o se ha alcanzado el intervalo de desplazamiento máximo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::ShowDropDown

Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShowIt*<br/>
Especifica si el cuadro de lista desplegable debe mostrarse u ocultarse. Un valor de TRUE muestra el cuadro de lista. Un valor de FALSE oculta el cuadro de lista.

### <a name="remarks"></a>Observaciones

De forma predeterminada, un cuadro combinado de este estilo mostrará el cuadro de lista.

Esta función miembro no tiene ningún efecto en un cuadro combinado creado con el [estilo CBS_SIMPLE.](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox::GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Vea también

[CTRLBARS de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[Clase CStatic](../../mfc/reference/cstatic-class.md)<br/>
[Clase CDialog](../../mfc/reference/cdialog-class.md)
