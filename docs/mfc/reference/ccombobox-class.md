---
title: Clase CComboBox
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
ms.openlocfilehash: b54a1913073ca0b23aeb17a57b16f589a074637b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424564"
---
# <a name="ccombobox-class"></a>Clase CComboBox

Proporciona la funcionalidad de un cuadro combinado de Windows.

## <a name="syntax"></a>Sintaxis

```
class CComboBox : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBox:: CComboBox](#ccombobox)|Construye un objeto `CComboBox`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|Agrega una cadena al final de la lista en el cuadro de lista de un cuadro combinado o en la posición ordenada de los cuadros de lista con el estilo de CBS_SORT.|
|[CComboBox:: Clear](#clear)|Elimina (borra) la selección actual, si la hay, en el control de edición.|
|[CComboBox:: CompareItem](#compareitem)|Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento de lista en un cuadro combinado dibujado por el propietario.|
|[CComboBox:: Copy](#copy)|Copia la selección actual, si existe, en el portapapeles en formato CF_TEXT.|
|[CComboBox:: Create](#create)|Crea el cuadro combinado y lo adjunta al objeto `CComboBox`.|
|[CComboBox:: Cut](#cut)|Elimina (corta) la selección actual, si la hay, en el control de edición y copia el texto eliminado en el portapapeles en CF_TEXT formato.|
|[CComboBox::D eleteItem](#deleteitem)|Lo llama el marco de trabajo cuando se elimina un elemento de lista de un cuadro combinado dibujado por el propietario.|
|[CComboBox::D eleteString](#deletestring)|Elimina una cadena del cuadro de lista de un cuadro combinado.|
|[CComboBox::D ir](#dir)|Agrega una lista de nombres de archivo al cuadro de lista de un cuadro combinado.|
|[CComboBox::D rawItem](#drawitem)|Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro combinado dibujado por el propietario.|
|[CComboBox:: FindString](#findstring)|Busca la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: FindExactString con](#findstringexact)|Busca la primera cadena de cuadro de lista (en un cuadro combinado) que coincida con la cadena especificada.|
|[CComboBox:: GetComboBoxInfo](#getcomboboxinfo)|Recupera información sobre el objeto de `CComboBox`.|
|[CComboBox:: GetCount](#getcount)|Recupera el número de elementos en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: GetCueBanner](#getcuebanner)|Obtiene el texto de la indicación que se muestra para un control de cuadro combinado.|
|[CComboBox:: GetCurSel](#getcursel)|Recupera el índice del elemento seleccionado actualmente, si existe, en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: GetDroppedControlRect](#getdroppedcontrolrect)|Recupera las coordenadas de pantalla del cuadro de lista visible (desplegado) de un cuadro combinado desplegable.|
|[CComboBox:: GetDroppedState](#getdroppedstate)|Determina si el cuadro de lista de un cuadro combinado desplegable está visible (desplegado).|
|[CComboBox:: GetDroppedWidth](#getdroppedwidth)|Recupera el ancho mínimo permitido para la parte de cuadro de lista desplegable de un cuadro combinado.|
|[CComboBox:: GetEditSel](#geteditsel)|Obtiene las posiciones de caracteres inicial y final de la selección actual en el control de edición de un cuadro combinado.|
|[CComboBox:: GetExtendedUI](#getextendedui)|Determina si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.|
|[CComboBox:: GetHorizontalExtent](#gethorizontalextent)|Devuelve el ancho en píxeles que la parte de cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|
|[CComboBox:: GetItemData](#getitemdata)|Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado.|
|[CComboBox:: GetItemDataPtr](#getitemdataptr)|Recupera el puntero de 32 bits proporcionado por la aplicación que está asociado al elemento de cuadro combinado especificado.|
|[CComboBox:: GetItemHeight](#getitemheight)|Recupera el alto de los elementos de lista de un cuadro combinado.|
|[CComboBox:: GetLBText](#getlbtext)|Obtiene una cadena del cuadro de lista de un cuadro combinado.|
|[CComboBox:: GetLBTextLen](#getlbtextlen)|Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: GetLocale](#getlocale)|Recupera el identificador de configuración regional de un cuadro combinado.|
|[CComboBox:: GetMinVisible](#getminvisible)|Obtiene el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|
|[CComboBox:: GetTopIndex](#gettopindex)|Devuelve el índice del primer elemento visible en la parte de cuadro de lista del cuadro combinado.|
|[CComboBox:: InitStorage](#initstorage)|Asigna previamente bloques de memoria para elementos y cadenas en la parte de cuadro de lista del cuadro combinado.|
|[CComboBox::InsertString](#insertstring)|Inserta una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: LimitText](#limittext)|Limita la longitud del texto que el usuario puede escribir en el control de edición de un cuadro combinado.|
|[CComboBox:: MeasureItem](#measureitem)|Lo llama el marco de trabajo para determinar las dimensiones del cuadro combinado cuando se crea un cuadro combinado dibujado por el propietario.|
|[CComboBox::P pegar](#paste)|Inserta los datos del portapapeles en el control de edición en la posición actual del cursor. Los datos se insertan solo si el Portapapeles contiene datos en formato CF_TEXT.|
|[CComboBox:: ResetContent](#resetcontent)|Quita todos los elementos del cuadro de lista y el control de edición de un cuadro combinado.|
|[CComboBox:: SelectString](#selectstring)|Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y copia la cadena en el control de edición.|
|[CComboBox:: SetCueBanner](#setcuebanner)|Establece el texto de indicación que se muestra para un control de cuadro combinado.|
|[CComboBox:: SetCurSel](#setcursel)|Selecciona una cadena en el cuadro de lista de un cuadro combinado.|
|[CComboBox:: SetDroppedWidth](#setdroppedwidth)|Establece el ancho mínimo permitido para la parte de cuadro de lista desplegable de un cuadro combinado.|
|[CComboBox:: SetEditSel](#seteditsel)|Selecciona caracteres en el control de edición de un cuadro combinado.|
|[CComboBox:: SetExtendedUI](#setextendedui)|Selecciona la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tenga el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.|
|[CComboBox:: SetHorizontalExtent](#sethorizontalextent)|Establece el ancho en píxeles que la parte de cuadro de lista del cuadro combinado se puede desplazar horizontalmente.|
|[CComboBox:: SetItemData](#setitemdata)|Establece el valor de 32 bits asociado al elemento especificado en un cuadro combinado.|
|[CComboBox:: SetItemDataPtr](#setitemdataptr)|Establece el puntero de 32 bits asociado al elemento especificado en un cuadro combinado.|
|[CComboBox:: SetItemHeight](#setitemheight)|Establece el alto de los elementos de lista en un cuadro combinado o el alto de la parte del control de edición (o texto estático) de un cuadro combinado.|
|[CComboBox:: SetLocale](#setlocale)|Establece el identificador de configuración regional de un cuadro combinado.|
|[CComboBox:: SetMinVisibleItems](#setminvisibleitems)|Establece el número mínimo de elementos visibles en la lista desplegable del cuadro combinado actual.|
|[CComboBox:: SetTopIndex](#settopindex)|Indica a la parte del cuadro de lista del cuadro combinado que muestre el elemento con el índice especificado en la parte superior.|
|[CComboBox:: ShowDropDown](#showdropdown)|Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.|

## <a name="remarks"></a>Observaciones

Un cuadro combinado consta de un cuadro de lista combinado con un control estático o un control de edición. La parte del cuadro de lista del control se puede mostrar en todo momento o solo puede desplegarse cuando el usuario selecciona la flecha desplegable situada junto al control.

El elemento seleccionado actualmente (si existe) en el cuadro de lista se muestra en el control estático o de edición. Además, si el cuadro combinado tiene el estilo de lista desplegable, el usuario puede escribir el carácter inicial de uno de los elementos de la lista y el cuadro de lista, si está visible, resaltará el elemento siguiente con ese carácter inicial.

En la tabla siguiente se comparan los tres [estilos](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)de cuadro combinado.

|Estilo|Cuando es visible el cuadro de lista|Control estático o de edición|
|-----------|-------------------------------|-----------------------------|
|Simple|Siempre|Editar|
|Drop-down|Cuando se quita|Editar|
|Lista desplegable|Cuando se quita|estática|

Puede crear un objeto `CComboBox` a partir de una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, llame primero al constructor `CComboBox` para construir el objeto `CComboBox`; a continuación, llame a la función miembro [Create](#create) para crear el control y adjuntarlo al objeto `CComboBox`.

Si desea controlar los mensajes de notificación de Windows enviados por un cuadro combinado a su elemento primario (normalmente una clase derivada de `CDialog`), agregue una entrada de mapa de mensajes y una función miembro de controlador de mensajes a la clase primaria para cada mensaje.

Cada entrada de mapa de mensajes tiene el siguiente formato:

**En\_** _notificación_ **(** _ID._ , _memberFxn_ **)**

donde `id` especifica el identificador de la ventana secundaria del control de cuadro combinado que envía la notificación y `memberFxn` es el nombre de la función miembro primaria que ha escrito para controlar la notificación.

El prototipo de función del elemento primario es el siguiente:

**afx_msg** `void` `memberFxn` **();**

No se puede predecir el orden en el que se enviarán determinadas notificaciones. En concreto, una notificación de CBN_SELCHANGE puede producirse antes o después de una notificación de CBN_CLOSEUP.

Las posibles entradas de mapa de mensajes son las siguientes:

- ON_CBN_CLOSEUP (Windows 3,1 y versiones posteriores). Se ha cerrado el cuadro de lista de un cuadro combinado. Este mensaje de notificación no se envía para un cuadro combinado que tenga el estilo [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- ON_CBN_DBLCLK el usuario hace doble clic en una cadena en el cuadro de lista de un cuadro combinado. Este mensaje de notificación solo se envía para un cuadro combinado con el estilo CBS_SIMPLE. En el caso de un cuadro combinado con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , no puede producirse un doble clic porque un solo clic oculta el cuadro de lista.

- ON_CBN_DROPDOWN el cuadro de lista de un cuadro combinado está a punto de desplegarse (se hace visible). Este mensaje de notificación solo puede aparecer para un cuadro combinado con el estilo CBS_DROPDOWN o CBS_DROPDOWNLIST.

- ON_CBN_EDITCHANGE el usuario ha realizado una acción que puede haber alterado el texto en la parte del control de edición de un cuadro combinado. A diferencia del mensaje de CBN_EDITUPDATE, este mensaje se envía después de que Windows actualice la pantalla. No se envía si el cuadro combinado tiene el estilo CBS_DROPDOWNLIST.

- ON_CBN_EDITUPDATE la parte del control de edición de un cuadro combinado está a punto de mostrar el texto modificado. Este mensaje de notificación se envía una vez que el control ha dado formato al texto, pero antes de que muestre el texto. No se envía si el cuadro combinado tiene el estilo CBS_DROPDOWNLIST.

- ON_CBN_ERRSPACE el cuadro combinado no puede asignar suficiente memoria para satisfacer una solicitud concreta.

- ON_CBN_SELENDCANCEL (Windows 3,1 y versiones posteriores). Indica que se debe cancelar la selección del usuario. El usuario hace clic en un elemento y, a continuación, hace clic en otra ventana o control para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes del mensaje de notificación de CBN_CLOSEUP para indicar que la selección del usuario debe omitirse. El mensaje de notificación de CBN_SELENDCANCEL o CBN_SELENDOK se envía aunque no se envíe el mensaje de notificación de CBN_CLOSEUP (como en el caso de un cuadro combinado con el estilo de CBS_SIMPLE).

- ON_CBN_SELENDOK el usuario selecciona un elemento y, después, presiona la tecla entrar o hace clic en la tecla de flecha abajo para ocultar el cuadro de lista de un cuadro combinado. Este mensaje de notificación se envía antes del mensaje de CBN_CLOSEUP para indicar que la selección del usuario debe considerarse válida. El mensaje de notificación de CBN_SELENDCANCEL o CBN_SELENDOK se envía aunque no se envíe el mensaje de notificación de CBN_CLOSEUP (como en el caso de un cuadro combinado con el estilo de CBS_SIMPLE).

- ON_CBN_KILLFOCUS el cuadro combinado está perdiendo el foco de entrada.

- ON_CBN_SELCHANGE la selección en el cuadro de lista de un cuadro combinado está a punto de cambiarse como resultado del usuario al hacer clic en el cuadro de lista o al cambiar la selección con las teclas de dirección. Al procesar este mensaje, el texto del control de edición del cuadro combinado solo se puede recuperar a través de `GetLBText` u otra función similar. no se puede usar `GetWindowText`.

- ON_CBN_SETFOCUS el cuadro combinado recibe el foco de entrada.

Si crea un objeto de `CComboBox` dentro de un cuadro de diálogo (a través de un recurso de cuadro de diálogo), el objeto de `CComboBox` se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.

Si incrusta un objeto de `CComboBox` dentro de otro objeto de ventana, no es necesario destruirlo. Si crea el objeto de `CComboBox` en la pila, se destruye automáticamente. Si crea el objeto de `CComboBox` en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo cuando se destruya el cuadro combinado de Windows.

**Nota:** Si desea controlar WM_KEYDOWN y WM_CHAR mensajes, tiene que subclaser los controles de cuadro de lista y edición del cuadro combinado, derivar clases de `CEdit` y `CListBox`y agregar controladores para esos mensajes a las clases derivadas. Para obtener más información, vea [CWnd:: SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="addstring"></a>CComboBox:: AddString

Agrega una cadena al cuadro de lista de un cuadro combinado.

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*lpszString*<br/>
Apunta a la cadena terminada en null que se va a agregar.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero de la cadena en el cuadro de lista. El valor devuelto es CB_ERR si se produce un error; el valor devuelto es CB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

Si el cuadro de lista no se creó con el estilo de [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , la cadena se agrega al final de la lista. De lo contrario, la cadena se inserta en la lista y la lista está ordenada.

> [!NOTE]
>  Esta función no es compatible con el control `ComboBoxEx` de Windows. Para obtener más información sobre este control, consulte [controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

Para insertar una cadena en una ubicación concreta de la lista, utilice la función miembro [InsertString](#insertstring) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>CComboBox:: CComboBox

Construye un objeto `CComboBox`.

```
CComboBox();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>CComboBox:: Clear

Elimina (borra) la selección actual, si la hay, en el control de edición del cuadro combinado.

```
void Clear();
```

### <a name="remarks"></a>Observaciones

Para eliminar la selección actual y colocar el contenido eliminado en el portapapeles, utilice la función miembro [CUT](#cut) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>CComboBox:: CompareItem

Lo llama el marco de trabajo para determinar la posición relativa de un nuevo elemento en la parte de cuadro de lista de un cuadro combinado dibujado por el propietario.

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpCompareItemStruct*<br/>
Puntero largo a una estructura [compareitemstruct (](/windows/win32/api/winuser/ns-winuser-compareitemstruct) .

### <a name="return-value"></a>Valor devuelto

Indica la posición relativa de los dos elementos descritos en la estructura de `COMPAREITEMSTRUCT`. Puede ser cualquiera de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|- 1|El elemento 1 se ordena antes que el elemento 2.|
|0|Los elementos 1 y 2 ordenan el mismo.|
|1|El elemento 1 se ordena después del elemento 2.|

Vea [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) para obtener una descripción de `COMPAREITEMSTRUCT`.

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Si crea un cuadro combinado dibujado por el propietario con el estilo LBS_SORT, debe invalidar esta función miembro para ayudar al marco a ordenar los nuevos elementos agregados al cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>CComboBox:: Copy

Copia la selección actual, si existe, en el control de edición del cuadro combinado en el portapapeles en CF_TEXT formato.

```
void Copy();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>CComboBox:: Create

Crea el cuadro combinado y lo adjunta al objeto `CComboBox`.

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
Apunta a la posición y el tamaño del cuadro combinado. Puede ser una [estructura Rect](/windows/win32/api/windef/ns-windef-rect) o un objeto `CRect`.

*pParentWnd*<br/>
Especifica la ventana primaria del cuadro combinado (normalmente una `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Cree un objeto de `CComboBox` en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el cuadro combinado de Windows y lo adjunta al objeto `CComboBox`.

Cuando se ejecuta `Create`, Windows envía los mensajes [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) al cuadro combinado.

Estos mensajes se controlan de forma predeterminada mediante las funciones miembro [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [alcrear](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) en la clase base `CWnd`. Para extender el control de mensajes predeterminado, derive una clase de `CComboBox`, agregue un mapa de mensajes a la nueva clase e invalide las funciones miembro de controlador de mensaje anteriores. Invalide `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de cuadro combinado. :

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

- WS_VSCROLL para agregar el desplazamiento vertical para el cuadro de lista del cuadro combinado

- WS_HSCROLL para agregar el desplazamiento horizontal para el cuadro de lista del cuadro combinado

- WS_GROUP a controles de grupo

- WS_TABSTOP para incluir el cuadro combinado en el orden de tabulación

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>CComboBox:: Cut

Elimina (corta) la selección actual, si la hay, en el control de edición de cuadro combinado y copia el texto eliminado en el portapapeles en CF_TEXT formato.

```
void Cut();
```

### <a name="remarks"></a>Observaciones

Para eliminar la selección actual sin colocar el texto eliminado en el portapapeles, llame a la función miembro [Clear](#clear) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>CComboBox::D eleteItem

Lo llama el marco de trabajo cuando el usuario elimina un elemento de un objeto de `CComboBox` dibujado por el propietario o destruye el cuadro combinado.

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDeleteItemStruct*<br/>
Un puntero largo a una estructura [deleteitemstruct (](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) de Windows que contiene información sobre el elemento eliminado. Vea [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) para obtener una descripción de esta estructura.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Reemplace esta función para volver a dibujar el cuadro combinado según sea necesario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>CComboBox::D eleteString

Elimina el elemento en la posición *NINDEX* del cuadro combinado.

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de la cadena que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es un recuento de las cadenas restantes de la lista. El valor devuelto es CB_ERR si *NINDEX* especifica un índice mayor que el número de elementos de la lista.

### <a name="remarks"></a>Observaciones

Ahora, todos los elementos que siguen a *NINDEX* bajan una posición. Por ejemplo, si un cuadro combinado contiene dos elementos, al eliminar el primer elemento, el elemento restante quedará ahora en la primera posición. *NINDEX*= 0 para el elemento en la primera posición.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>CComboBox::D ir

Agrega una lista de nombres de archivo o unidades al cuadro de lista de un cuadro combinado.

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>Parámetros

*Attr*<br/>
Puede ser cualquier combinación de los valores de **enumeración** descritos en [CFile:: getStatus](../../mfc/reference/cfile-class.md#getstatus) o cualquier combinación de los siguientes valores:

- DDL_READWRITE archivo se puede leer o escribir en él.

- DDL_READONLY archivo se puede leer pero no escribir en él.

- DDL_HIDDEN archivo está oculto y no aparece en una lista de directorios.

- DDL_SYSTEM archivo es un archivo del sistema.

- DDL_DIRECTORY el nombre especificado por *lpszWildCard* especifica un directorio.

- DDL_ARCHIVE archivo se ha archivado.

- DDL_DRIVES incluyen todas las unidades que coinciden con el nombre especificado por *lpszWildCard*.

- DDL_EXCLUSIVE marca exclusiva. Si se establece la marca Exclusive, solo se enumeran los archivos del tipo especificado. De lo contrario, los archivos del tipo especificado se enumeran además de los archivos "normales".

*lpszWildCard*<br/>
Apunta a una cadena de especificación de archivo. La cadena puede contener caracteres comodín (por ejemplo, *.\*).

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero del último nombre de archivo que se ha agregado a la lista. El valor devuelto es CB_ERR si se produce un error; el valor devuelto es CB_ERRSPACE si no hay suficiente espacio disponible para almacenar las nuevas cadenas.

### <a name="remarks"></a>Observaciones

Esta función no es compatible con el control `ComboBoxEx` de Windows. Para obtener más información sobre este control, consulte [controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>CComboBox::D rawItem

Lo llama el marco de trabajo cuando cambia el aspecto visual de un cuadro combinado dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que contiene información sobre el tipo de dibujo necesario.

### <a name="remarks"></a>Observaciones

El miembro `itemAction` de la estructura `DRAWITEMSTRUCT` define la acción de dibujo que se va a realizar. Vea [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) para obtener una descripción de esta estructura.

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro para implementar el dibujo de un objeto de `CComboBox` dibujado por el propietario. Antes de que finalice esta función miembro, la aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>CComboBox:: FindString

Busca, pero no selecciona, la primera cadena que contiene el prefijo especificado en el cuadro de lista de un cuadro combinado.

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si es-1, se busca en el cuadro de lista completo desde el principio.

*lpszString*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de las mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Si el valor devuelto es mayor o igual que 0, es el índice de base cero del elemento coincidente. Es CB_ERR si la búsqueda no se ha realizado correctamente.

### <a name="remarks"></a>Observaciones

Esta función no es compatible con el control `ComboBoxEx` de Windows. Para obtener más información sobre este control, consulte [controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>CComboBox:: FindExactString con

Llame a la función miembro `FindStringExact` para buscar la primera cadena de cuadro de lista (en un cuadro combinado) que coincida con la cadena especificada en *lpszFind*.

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>Parámetros

*nIndexStart*<br/>
Especifica el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nIndexStart*. Si *nIndexStart* es-1, se busca en el cuadro de lista completo desde el principio.

*lpszFind*<br/>
Apunta a la cadena terminada en null que se va a buscar. Esta cadena puede contener un nombre de archivo completo, incluida la extensión. La búsqueda no distingue entre mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento coincidente, o CB_ERR si la búsqueda no se ha realizado correctamente.

### <a name="remarks"></a>Observaciones

Si el cuadro combinado se creó con un estilo de dibujo de propietario pero sin el estilo de [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , `FindStringExact` intenta hacer coincidir el valor de palabra con el valor de *lpszFind*.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>CComboBox:: GetComboBoxInfo

Recupera información para el objeto `CComboBox`.

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>Parámetros

*pcbi*<br/>
Puntero a la estructura [COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo) .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje de [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) , como se describe en el Windows SDK.

##  <a name="getcount"></a>CComboBox:: GetCount

Llame a esta función miembro para recuperar el número de elementos de la parte de cuadro de lista de un cuadro combinado.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos. El recuento devuelto es uno mayor que el valor de índice del último elemento (el índice está basado en cero). Es CB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>CComboBox:: GetCueBanner

Obtiene el texto de la indicación que se muestra para un control de cuadro combinado.

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszText*|enuncia Puntero a un búfer que recibe el texto del titular de indicación.|
|*cchText*|de Tamaño del búfer al que apunta el parámetro *lpszText* .|

### <a name="return-value"></a>Valor devuelto

En la primera sobrecarga, un objeto [CString](../../atl-mfc-shared/using-cstring.md) que contiene el texto del titular de indicación si existe; de lo contrario, un objeto `CString` que tenga longitud cero.

O bien

En la segunda sobrecarga, es TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

El texto de indicación es un mensaje que se muestra en el área de entrada del control de cuadro combinado. El texto de la indicación se muestra hasta que el usuario proporciona datos.

Este método envía el mensaje de [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) , que se describe en el Windows SDK.

##  <a name="getcursel"></a>CComboBox:: GetCurSel

Llame a esta función miembro para determinar qué elemento del cuadro combinado está seleccionado.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento seleccionado actualmente en el cuadro de lista de un cuadro combinado, o CB_ERR si no se selecciona ningún elemento.

### <a name="remarks"></a>Observaciones

`GetCurSel` devuelve un índice en la lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>CComboBox:: GetDroppedControlRect

Llame a la función miembro `GetDroppedControlRect` para recuperar las coordenadas de pantalla del cuadro de lista visible (desplegable) de un cuadro combinado desplegable.

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>Parámetros

*lprect*<br/>
Apunta a la [estructura Rect](/windows/win32/api/windef/ns-windef-rect) que va a recibir las coordenadas.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>CComboBox:: GetDroppedState

Llame a la función miembro `GetDroppedState` para determinar si el cuadro de lista de un cuadro combinado desplegable está visible (desplegado).

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro de lista está visible; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>CComboBox:: GetDroppedWidth

Llame a esta función para recuperar el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, el ancho mínimo permitido, en píxeles; de lo contrario, CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función solo se aplica a los cuadros combinados con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. El ancho mínimo permitido se puede establecer mediante una llamada a [SetDroppedWidth](#setdroppedwidth). Cuando se muestra la parte de cuadro de lista del cuadro combinado, su ancho es el mayor del ancho mínimo permitido o el ancho del cuadro combinado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [SetDroppedWidth](#setdroppedwidth).

##  <a name="geteditsel"></a>CComboBox:: GetEditSel

Obtiene las posiciones de caracteres inicial y final de la selección actual en el control de edición de un cuadro combinado.

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>Valor devuelto

Valor de 32 bits que contiene la posición inicial en la palabra de orden inferior y la posición del primer carácter no seleccionado después del final de la selección en la palabra de orden superior. Si se utiliza esta función en un cuadro combinado sin un control de edición, se devuelve CB_ERR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>CComboBox:: GetExtendedUI

Llame a la función miembro `GetExtendedUI` para determinar si un cuadro combinado tiene la interfaz de usuario predeterminada o la interfaz de usuario extendida.

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el cuadro combinado tiene la interfaz de usuario extendida; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La interfaz de usuario extendida se puede identificar de las siguientes maneras:

- Al hacer clic en el control estático solo se muestra el cuadro de lista para los cuadros combinados con el estilo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

- Al presionar la tecla flecha abajo, se muestra el cuadro de lista (F4 está deshabilitado).

El desplazamiento en el control estático está deshabilitado cuando la lista de elementos no está visible (las teclas de dirección están deshabilitadas).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>CComboBox:: GetHorizontalExtent

Recupera del cuadro combinado el ancho en píxeles por el que se puede desplazar horizontalmente la parte del cuadro de lista del cuadro combinado.

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho desplazable de la parte del cuadro de lista del cuadro combinado, en píxeles.

### <a name="remarks"></a>Observaciones

Esto solo es aplicable si la parte de cuadro de lista del cuadro combinado tiene una barra de desplazamiento horizontal.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>CComboBox:: GetItemData

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado.

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de un elemento del cuadro de lista del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Valor de 32 bits asociado al elemento o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El valor de 32 bits se puede establecer con el parámetro *dwItemData* de una llamada de función miembro [SetItemData](#setitemdata) . Utilice la función miembro `GetItemDataPtr` si el valor de bit 32 que se va a recuperar es un puntero (**void** <strong>\*</strong>).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>CComboBox:: GetItemDataPtr

Recupera el valor de 32 bits proporcionado por la aplicación asociado al elemento de cuadro combinado especificado como un puntero (**void** <strong>\*</strong>).

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de un elemento del cuadro de lista del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Recupera un puntero o-1 si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>CComboBox:: GetItemHeight

Llame a la función miembro `GetItemHeight` para recuperar el alto de los elementos de lista de un cuadro combinado.

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el componente del cuadro combinado cuyo alto se va a recuperar. Si el parámetro *NINDEX* es-1, se recupera el alto de la parte del control de edición (o texto estático) del cuadro combinado. Si el cuadro combinado tiene el estilo de [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *NINDEX* especifica el índice de base cero del elemento de lista cuyo alto se va a recuperar. De lo contrario, *NINDEX* debe establecerse en 0.

### <a name="return-value"></a>Valor devuelto

Alto, en píxeles, del elemento especificado en un cuadro combinado. El valor devuelto es CB_ERR si se produce un error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>CComboBox:: GetLBText

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
Apunta a un búfer que va a recibir la cadena. El búfer debe tener espacio suficiente para la cadena y un carácter nulo de terminación.

*rString*<br/>
Referencia a un `CString`.

### <a name="return-value"></a>Valor devuelto

La longitud (en bytes) de la cadena, sin incluir el carácter nulo de terminación. Si *NINDEX* no especifica un índice válido, el valor devuelto es CB_ERR.

### <a name="remarks"></a>Observaciones

La segunda forma de esta función miembro rellena un objeto `CString` con el texto del elemento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>CComboBox:: GetLBTextLen

Obtiene la longitud de una cadena en el cuadro de lista de un cuadro combinado.

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la cadena de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Longitud de la cadena en bytes, sin incluir el carácter nulo de terminación. Si *NINDEX* no especifica un índice válido, el valor devuelto es CB_ERR.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox:: GetLBText](#getlbtext).

##  <a name="getlocale"></a>CComboBox:: GetLocale

Recupera la configuración regional utilizada por el cuadro combinado.

```
LCID GetLocale() const;
```

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) de las cadenas en el cuadro combinado.

### <a name="remarks"></a>Observaciones

La configuración regional se usa, por ejemplo, para determinar el criterio de ordenación de las cadenas en un cuadro combinado ordenado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox:: setlocale](#setlocale).

##  <a name="getminvisible"></a>CComboBox:: GetMinVisible

Obtiene el número mínimo de elementos visibles en la lista desplegable del control de cuadro combinado actual.

```
int GetMinVisible() const;
```

### <a name="return-value"></a>Valor devuelto

Número mínimo de elementos visibles en la lista desplegable actual.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , que se describe en el Windows SDK.

##  <a name="gettopindex"></a>CComboBox:: GetTopIndex

Recupera el índice de base cero del primer elemento visible en la parte de cuadro de lista del cuadro combinado.

```
int GetTopIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del primer elemento visible en la parte de cuadro de lista del cuadro combinado si es correcto, de lo contrario CB_ERR.

### <a name="remarks"></a>Observaciones

Inicialmente, el elemento 0 está en la parte superior del cuadro de lista, pero si se desplaza el cuadro de lista, es posible que haya otro elemento en la parte superior.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>CComboBox:: InitStorage

Asigna memoria para almacenar los elementos del cuadro de lista en la parte de cuadro de lista del cuadro combinado.

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

Si es correcto, el número máximo de elementos que la parte de cuadro de lista del cuadro combinado puede almacenar antes de que se necesite una reasignación de memoria, de lo contrario CB_ERRSPACE, lo que significa que no hay suficiente memoria disponible.

### <a name="remarks"></a>Observaciones

Llame a esta función antes de agregar un gran número de elementos a la parte de cuadro de lista del `CComboBox`.

Solo Windows 95/98: el parámetro *wParam* está limitado a valores de 16 bits. Esto significa que los cuadros de lista no pueden contener más de 32.767 elementos. Aunque el número de elementos está restringido, el tamaño total de los elementos de un cuadro de lista solo está limitado por la memoria disponible.

Esta función ayuda a acelerar la inicialización de cuadros de lista que tienen un gran número de elementos (más de 100). Asigna previamente la cantidad de memoria especificada para que las siguientes funciones de [addString](#addstring), [InsertString](#insertstring)y [dir](#dir) tarden el menor tiempo posible. Puede usar estimaciones para los parámetros. Si sobrestima, se asignará una memoria adicional; Si se subestima, se usa la asignación normal para los elementos que superan la cantidad preasignada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>CComboBox:: InsertString

Inserta una cadena en el cuadro de lista de un cuadro combinado.

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Contiene el índice de base cero de la posición en el cuadro de lista que recibirá la cadena. Si este parámetro es-1, la cadena se agrega al final de la lista.

*lpszString*<br/>
Apunta a la cadena terminada en null que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la posición donde se insertó la cadena. El valor devuelto es CB_ERR si se produce un error. El valor devuelto es CB_ERRSPACE si no hay suficiente espacio disponible para almacenar la nueva cadena.

### <a name="remarks"></a>Observaciones

A diferencia de la función miembro [AddString](#addstring) , la función miembro `InsertString` no provoca una lista con el estilo [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) que se va a ordenar.

> [!NOTE]
>  Esta función no es compatible con el control `ComboBoxEx` de Windows. Para obtener más información sobre este control, consulte [controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>CComboBox:: LimitText

Limita la longitud en bytes del texto que el usuario puede escribir en el control de edición de un cuadro combinado.

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>Parámetros

*nMaxChars*<br/>
Especifica la longitud (en bytes) del texto que el usuario puede escribir. Si este parámetro es 0, la longitud del texto se establece en 65.535 bytes.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente. Si se llama para un cuadro combinado con el estilo [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o para un cuadro combinado sin un control de edición, el valor devuelto es CB_ERR.

### <a name="remarks"></a>Observaciones

Si el cuadro combinado no tiene el estilo [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles), establecer el límite de texto en un valor mayor que el tamaño del control de edición no tendrá ningún efecto.

`LimitText` solo limita el texto que el usuario puede escribir. No tiene ningún efecto en ningún texto que ya esté en el control de edición cuando se envía el mensaje, ni afecta a la longitud del texto copiado en el control de edición cuando se selecciona una cadena en el cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>CComboBox:: MeasureItem

Lo llama el marco de trabajo cuando se crea un cuadro combinado con un estilo dibujado por el propietario.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpMeasureItemStruct*<br/>
Puntero largo a una estructura [measureitemstruct (](/windows/win32/api/winuser/ns-winuser-measureitemstruct) .

### <a name="remarks"></a>Observaciones

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro y rellene la estructura `MEASUREITEMSTRUCT` para informar a las ventanas de las dimensiones del cuadro de lista del cuadro combinado. Si el cuadro combinado se crea con el estilo [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , el marco de trabajo llama a esta función miembro para cada elemento del cuadro de lista. De lo contrario, se llama a este miembro solo una vez.

El uso del estilo de CBS_OWNERDRAWFIXED en un cuadro combinado dibujado por el propietario creado con la función miembro [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) de `CWnd` implica otras consideraciones de programación. Vea la explicación en la [Nota técnica 14](../../mfc/tn014-custom-controls.md).

Vea [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) para obtener una descripción de la estructura `MEASUREITEMSTRUCT`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>CComboBox::P pegar

Inserta los datos del portapapeles en el control de edición del cuadro combinado en la posición actual del cursor.

```
void Paste();
```

### <a name="remarks"></a>Observaciones

Los datos se insertan solo si el Portapapeles contiene datos en formato CF_TEXT.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>CComboBox:: ResetContent

Quita todos los elementos del cuadro de lista y el control de edición de un cuadro combinado.

```
void ResetContent();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>CComboBox:: SelectString

Busca una cadena en el cuadro de lista de un cuadro combinado y, si se encuentra la cadena, selecciona la cadena en el cuadro de lista y la copia en el control de edición.

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parámetros

*nStartAfter*<br/>
Contiene el índice de base cero del elemento antes del primer elemento que se va a buscar. Cuando la búsqueda alcanza la parte inferior del cuadro de lista, continúa desde la parte superior del cuadro de lista hasta el elemento especificado por *nStartAfter*. Si es-1, se busca en el cuadro de lista completo desde el principio.

*lpszString*<br/>
Apunta a la cadena terminada en null que contiene el prefijo que se va a buscar. La búsqueda es independiente de las mayúsculas y minúsculas, por lo que esta cadena puede contener cualquier combinación de mayúsculas y minúsculas.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento seleccionado si se encontró la cadena. Si la búsqueda no se realizó correctamente, el valor devuelto es CB_ERR y no se cambia la selección actual.

### <a name="remarks"></a>Observaciones

Solo se selecciona una cadena si sus caracteres iniciales (desde el punto inicial) coinciden con los caracteres de la cadena de prefijo.

Tenga en cuenta que las funciones miembro `SelectString` y `FindString` encuentran una cadena, pero la función miembro `SelectString` también selecciona la cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>CComboBox:: SetCueBanner

Establece el texto de indicación que se muestra para un control de cuadro combinado.

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpszText*|de Puntero a un búfer terminado en null que contiene el texto de la indicación.|

### <a name="return-value"></a>Valor devuelto

TRUE si el método es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

El texto de indicación es un mensaje que se muestra en el área de entrada del control de cuadro combinado. El texto de la indicación se muestra hasta que el usuario proporciona datos.

Este método envía el mensaje de [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_combobox*, que se usa para tener acceso mediante programación al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se establece el titular de indicación para el control de cuadro combinado.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>CComboBox:: SetCurSel

Selecciona una cadena en el cuadro de lista de un cuadro combinado.

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>Parámetros

*nSeleccione*<br/>
Especifica el índice de base cero de la cadena que se va a seleccionar. Si es-1, se quita cualquier selección actual del cuadro de lista y se borra el control de edición.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento seleccionado si el mensaje se realiza correctamente. El valor devuelto es CB_ERR *si el* valor de devuelto es mayor que el número de elementos de la lista o si la opción *nSeleccione* está establecida en-1, lo que borra la selección.

### <a name="remarks"></a>Observaciones

Si es necesario, el cuadro de lista desplaza la cadena en la vista (si el cuadro de lista está visible). El texto del control de edición del cuadro combinado se cambia para reflejar la nueva selección. Se quita cualquier selección anterior en el cuadro de lista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>CComboBox:: SetDroppedWidth

Llame a esta función para establecer el ancho mínimo permitido, en píxeles, del cuadro de lista de un cuadro combinado.

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
El ancho mínimo permitido de la parte del cuadro de lista del cuadro combinado, en píxeles.

### <a name="return-value"></a>Valor devuelto

Si es correcto, el nuevo ancho del cuadro de lista, de lo contrario CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función solo se aplica a los cuadros combinados con el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

De forma predeterminada, el ancho mínimo permitido del cuadro de lista desplegable es 0. Cuando se muestra la parte de cuadro de lista del cuadro combinado, su ancho es el mayor del ancho mínimo permitido o el ancho del cuadro combinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>CComboBox:: SetEditSel

Selecciona caracteres en el control de edición de un cuadro combinado.

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>Parámetros

*nStartChar*<br/>
Especifica la posición inicial. Si la posición inicial se establece en-1, se quita cualquier selección existente.

*nEndChar*<br/>
Especifica la posición final. Si la posición final se establece en-1, se seleccionará todo el texto desde la posición inicial hasta el último carácter del control de edición.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función miembro es correcta; de lo contrario, es 0. Es CB_ERR si `CComboBox` tiene el estilo de [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o no tiene un cuadro de lista.

### <a name="remarks"></a>Observaciones

Las posiciones son de base cero. Para seleccionar el primer carácter del control de edición, especifique una posición inicial de 0. La posición final es para el carácter situado justo después del último carácter que se va a seleccionar. Por ejemplo, para seleccionar los cuatro primeros caracteres del control de edición, usaría una posición inicial de 0 y una posición final de 4.

> [!NOTE]
>  Esta función no es compatible con el control `ComboBoxEx` de Windows. Para obtener más información sobre este control, consulte [controles ComboBoxEx](/windows/win32/Controls/comboboxex-controls) en el Windows SDK.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox:: GetEditSel](#geteditsel).

##  <a name="setextendedui"></a>CComboBox:: SetExtendedUI

Llame a la función miembro `SetExtendedUI` para seleccionar la interfaz de usuario predeterminada o la interfaz de usuario extendida para un cuadro combinado que tenga el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>Parámetros

*Bel*<br/>
Especifica si el cuadro combinado debe usar la interfaz de usuario extendida o la interfaz de usuario predeterminada. Un valor de TRUE selecciona la interfaz de usuario extendida; un valor FALSE selecciona la interfaz de usuario estándar.

### <a name="return-value"></a>Valor devuelto

CB_OKAY si la operación se realiza correctamente o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

La interfaz de usuario extendida se puede identificar de las siguientes maneras:

- Al hacer clic en el control estático solo se muestra el cuadro de lista para los cuadros combinados con el estilo CBS_DROPDOWNLIST.

- Al presionar la tecla flecha abajo, se muestra el cuadro de lista (F4 está deshabilitado).

El desplazamiento en el control estático está deshabilitado cuando la lista de elementos no está visible (las teclas de dirección están deshabilitadas).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox:: GetExtendedUI](#getextendedui).

##  <a name="sethorizontalextent"></a>CComboBox:: SetHorizontalExtent

Establece el ancho, en píxeles, por el que se puede desplazar horizontalmente la parte de cuadro de lista del cuadro combinado.

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>Parámetros

*nExtent*<br/>
Especifica el número de píxeles que se puede desplazar horizontalmente la parte de cuadro de lista del cuadro combinado.

### <a name="remarks"></a>Observaciones

Si el ancho del cuadro de lista es menor que este valor, la barra de desplazamiento horizontal desplazará horizontalmente los elementos del cuadro de lista. Si el ancho del cuadro de lista es igual o mayor que este valor, la barra de desplazamiento horizontal está oculta o, si el cuadro combinado tiene el estilo de [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , deshabilitado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>CComboBox:: SetItemData

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

Utilice la función miembro `SetItemDataPtr` si el elemento de 32 bits va a ser un puntero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>CComboBox:: SetItemDataPtr

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

Este puntero sigue siendo válido mientras dure el cuadro combinado, aunque la posición relativa del elemento en el cuadro combinado puede cambiar a medida que se agregan o quitan elementos. Por lo tanto, el índice del elemento en el cuadro puede cambiar, pero el puntero sigue siendo confiable.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>CComboBox:: SetItemHeight

Llame a la función miembro `SetItemHeight` para establecer el alto de los elementos de lista en un cuadro combinado o el alto de la parte del control de edición (o texto estático) de un cuadro combinado.

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica si está establecida la altura de los elementos de lista o el alto de la parte de control de edición (o texto estático) del cuadro combinado.

Si el cuadro combinado tiene el estilo de [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) , *NINDEX* especifica el índice de base cero del elemento de lista cuyo alto se va a establecer; de lo contrario, *NINDEX* debe ser 0 y se establecerá el alto de todos los elementos de lista.

Si *NINDEX* es-1, se establecerá el alto de la parte de texto estático o de control de edición del cuadro combinado.

*cyItemHeight*<br/>
Especifica el alto, en píxeles, del componente de cuadro combinado identificado por *NINDEX*.

### <a name="return-value"></a>Valor devuelto

CB_ERR si el índice o el alto no son válidos; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El alto de la parte del control de edición (o texto estático) del cuadro combinado se establece independientemente del alto de los elementos de la lista. Una aplicación debe asegurarse de que el alto de la parte del control de edición (o texto estático) no es menor que el alto de un elemento de cuadro de lista determinado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>CComboBox:: SetLocale

Establece el identificador de configuración regional de este cuadro combinado.

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>Parámetros

*nNewLocale*<br/>
Nuevo valor de identificador de configuración regional (LCID) que se va a establecer para el cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El valor del identificador de configuración regional (LCID) anterior de este cuadro combinado.

### <a name="remarks"></a>Observaciones

Si no se llama a `SetLocale`, la configuración regional predeterminada se obtiene del sistema. Se puede modificar la configuración regional predeterminada del sistema mediante la aplicación regional (o internacional) del panel de control.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>CComboBox:: SetMinVisibleItems

Establece el número mínimo de elementos visibles en la lista desplegable del control de cuadro combinado actual.

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*invisible*|de Especifica el número mínimo de elementos visibles.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el mensaje de [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define la variable, *m_combobox*, que se usa para tener acceso mediante programación al control de cuadro combinado. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se insertan 20 elementos en la lista desplegable de un control de cuadro combinado. A continuación, especifica que se muestre un mínimo de 10 elementos cuando un usuario presione la flecha desplegable.

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>CComboBox:: SetTopIndex

Garantiza que un elemento determinado esté visible en la parte de cuadro de lista del cuadro combinado.

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Especifica el índice de base cero del elemento de cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Cero si se realiza correctamente o CB_ERR si se produce un error.

### <a name="remarks"></a>Observaciones

El sistema desplaza el cuadro de lista hasta que el elemento especificado por *NINDEX* aparezca en la parte superior del cuadro de lista o hasta que se alcance el intervalo de desplazamiento máximo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>CComboBox:: ShowDropDown

Muestra u oculta el cuadro de lista de un cuadro combinado que tiene el estilo [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) o [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShowIt*<br/>
Especifica si se va a mostrar u ocultar el cuadro de lista desplegable. Un valor de TRUE muestra el cuadro de lista. Un valor de FALSE oculta el cuadro de lista.

### <a name="remarks"></a>Observaciones

De forma predeterminada, un cuadro combinado de este estilo mostrará el cuadro de lista.

Esta función miembro no tiene ningún efecto en un cuadro combinado creado con el estilo [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CComboBox:: GetDroppedState](#getdroppedstate).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CButton (clase)](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar (clase)](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic (clase)](../../mfc/reference/cstatic-class.md)<br/>
[CDialog (clase)](../../mfc/reference/cdialog-class.md)
