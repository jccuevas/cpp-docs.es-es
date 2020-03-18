---
title: CComboBoxEx (clase)
ms.date: 11/04/2016
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
helpviewer_keywords:
- CComboBoxEx [MFC], CComboBoxEx
- CComboBoxEx [MFC], Create
- CComboBoxEx [MFC], CreateEx
- CComboBoxEx [MFC], DeleteItem
- CComboBoxEx [MFC], GetComboBoxCtrl
- CComboBoxEx [MFC], GetEditCtrl
- CComboBoxEx [MFC], GetExtendedStyle
- CComboBoxEx [MFC], GetImageList
- CComboBoxEx [MFC], GetItem
- CComboBoxEx [MFC], HasEditChanged
- CComboBoxEx [MFC], InsertItem
- CComboBoxEx [MFC], SetExtendedStyle
- CComboBoxEx [MFC], SetImageList
- CComboBoxEx [MFC], SetItem
- CComboBoxEx [MFC], SetWindowTheme
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
ms.openlocfilehash: 7d46f175a62cda7f1ff08327830f1dffe2967727
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425992"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx (clase)

Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBoxEx:: CComboBoxEx](#ccomboboxex)|Construye un objeto `CComboBoxEx`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBoxEx:: Create](#create)|Crea el cuadro combinado y lo adjunta al objeto `CComboBoxEx`.|
|[CComboBoxEx:: CreateEx](#createex)|Crea un cuadro combinado con los estilos extendidos de Windows especificados y lo adjunta a un objeto `ComboBoxEx`.|
|[CComboBoxEx::D eleteItem](#deleteitem)|Quita un elemento de un control de `ComboBoxEx`.|
|[CComboBoxEx:: GetComboBoxCtrl](#getcomboboxctrl)|Recupera un puntero al control de cuadro combinado secundario.|
|[CComboBoxEx:: GetEditCtrl](#geteditctrl)|Recupera el identificador de la parte del control de edición de un control de `ComboBoxEx`.|
|[CComboBoxEx:: GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están en uso para un control `ComboBoxEx`.|
|[CComboBoxEx:: GetImageList](#getimagelist)|Recupera un puntero a la lista de imágenes asignada a un control de `ComboBoxEx`.|
|[CComboBoxEx:: GetItem](#getitem)|Recupera la información de un elemento de `ComboBoxEx` determinado.|
|[CComboBoxEx:: HasEditChanged](#haseditchanged)|Determina si el usuario ha cambiado el contenido de la `ComboBoxEx` control de edición escribiendo.|
|[CComboBoxEx:: InsertItem](#insertitem)|Inserta un nuevo elemento en un control de `ComboBoxEx`.|
|[CComboBoxEx:: SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos dentro de un control `ComboBoxEx`.|
|[CComboBoxEx:: SetImageList](#setimagelist)|Establece una lista de imágenes para un control `ComboBoxEx`.|
|[CComboBoxEx:: SetItem](#setitem)|Establece los atributos de un elemento en un control de `ComboBoxEx`.|
|[CComboBoxEx:: SetWindowTheme](#setwindowtheme)|Establece el estilo visual del control de cuadro combinado extendido.|

## <a name="remarks"></a>Observaciones

Al usar `CComboBoxEx` para crear controles de cuadro combinado, ya no es necesario implementar su propio código de dibujo de imagen. En su lugar, use `CComboBoxEx` para tener acceso a las imágenes de una lista de imágenes.

## <a name="image-list-support"></a>Compatibilidad con la lista de imágenes

En un cuadro combinado estándar, el propietario del cuadro combinado es responsable de dibujar una imagen creando el cuadro combinado como un control dibujado por el propietario. Cuando se usa `CComboBoxEx`, no es necesario establecer los estilos de dibujo CBS_OWNERDRAWFIXED y CBS_HASSTRINGS porque están implícitos. De lo contrario, debe escribir código para realizar operaciones de dibujo. Un control `CComboBoxEx` admite hasta tres imágenes por elemento: una para un estado seleccionado, una para un estado no seleccionado y otra para una imagen superpuesta.

## <a name="styles"></a>Estilos

`CComboBoxEx` admite los estilos CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST y WS_CHILD. El control omite todos los demás estilos que se pasan al crear la ventana. Una vez creada la ventana, puede proporcionar otros estilos de cuadro combinado llamando a la función miembro `CComboBoxEx` [SetExtendedStyle](#setextendedstyle). Con estos estilos, puede:

- Establezca búsquedas de cadena en la lista para distinguir entre mayúsculas y minúsculas.

- Cree un control de cuadro combinado que use los caracteres de barra diagonal ('/'), barra diagonal inversa ('\\') y punto ('. ') como delimitadores de palabras. Esto permite a los usuarios saltar de Word a Word con el método abreviado de teclado CTRL + flecha.

- Establezca el control de cuadro combinado para mostrar o no mostrar una imagen. Si no se muestra ninguna imagen, el cuadro combinado puede quitar la sangría de texto que contenga una imagen.

- Cree un control de cuadro combinado estrecho, incluido su tamaño, de modo que recorte el cuadro combinado más amplio que contiene.

Estas marcas de estilo se describen con más detalle en el [uso de CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Atributos de elementos de devolución de llamada y retención de elemento

La información del elemento, como los índices de elementos e imágenes, los valores de sangría y las cadenas de texto, se almacena en la estructura de Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), tal y como se describe en el Windows SDK. La estructura también contiene los miembros que corresponden a las marcas de devolución de llamada.

Para obtener una explicación detallada conceptual, vea [usar CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="ccomboboxex"></a>CComboBoxEx:: CComboBoxEx

Llame a esta función miembro para crear un objeto de `CComboBoxEx`.

```
CComboBoxEx();
```

##  <a name="create"></a>CComboBoxEx:: Create

Crea el cuadro combinado y lo adjunta al objeto `CComboBoxEx`.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de cuadro combinado aplicada al cuadro combinado. Vea la **sección Comentarios** a continuación para obtener más información sobre los estilos.

*Rect*<br/>
Referencia a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) , que es la posición y el tamaño del cuadro combinado.

*pParentWnd*<br/>
Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana primaria del cuadro combinado (normalmente `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se creó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Cree un objeto de `CComboBoxEx` en dos pasos:

1. Llame a [CComboBoxEx](#ccomboboxex) para construir un objeto de `CComboBoxEx`.

1. Llame a esta función miembro, que crea el cuadro combinado de Windows extendido y lo adjunta al objeto `CComboBoxEx`.

Cuando se llama a `Create`, MFC inicializa los controles comunes.

Al crear el cuadro combinado, puede especificar cualquiera de los siguientes estilos de cuadro combinado o todos ellos:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Se omiten todos los demás estilos que se pasan al crear la ventana. El control `ComboBoxEx` también admite estilos extendidos que proporcionan características adicionales. Estos estilos se describen en [ComboBoxEx control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles), en el Windows SDK. Establezca estos estilos mediante una llamada a [SetExtendedStyle](#setextendedstyle).

Si desea utilizar estilos extendidos de Windows con el control, llame a [CreateEx](#createex) en lugar de a `Create`.

##  <a name="createex"></a>CComboBoxEx:: CreateEx

Llame a esta función para crear un control de cuadro combinado extendido (una ventana secundaria) y asociarlo al objeto `CComboBoxEx`.

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
Estilo del control de cuadro combinado. Vea [crear](#create) para obtener una lista de estilos.

*Rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Utilice `CreateEx` en lugar de `Create` para aplicar los estilos extendidos de Windows, especificados por el **WS_EX_** de prefacio de estilo extendido de Windows.

`CreateEx` crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Debe establecer los estilos extendidos específicos de un control de cuadro combinado extendido mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, utilice `CreateEx` para establecer tales estilos como WS_EX_CONTEXTHELP, pero use `SetExtendedStyle` para establecer tales estilos como CBES_EX_CASESENSITIVE. Para obtener más información, vea los estilos descritos en el tema [ComboBoxEx control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK.

##  <a name="deleteitem"></a>CComboBoxEx::D eleteItem

Quita un elemento de un control de `ComboBoxEx`.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
Índice de base cero del elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Número de elementos que quedan en el control. Si *iIndex* no es válido, la función devuelve CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad de la [CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem)de mensajes, tal y como se describe en el Windows SDK. Cuando llame a DeleteItem, se enviará un mensaje de [WM_NOTIFY](/windows/win32/controls/wm-notify) con CBEN_DELETEITEM notificación a la ventana primaria.

##  <a name="getcomboboxctrl"></a>CComboBoxEx:: GetComboBoxCtrl

Llame a esta función miembro para obtener un puntero a un control de cuadro combinado dentro de un objeto `CComboBoxEx`.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CComboBox` .

### <a name="remarks"></a>Observaciones

El control `CComboBoxEx` consta de una ventana primaria, que encapsula un `CComboBox`.

El `CComboBox` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

##  <a name="geteditctrl"></a>CComboBoxEx:: GetEditCtrl

Llame a esta función miembro para obtener un puntero al control de edición de un cuadro combinado.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CEDIT](../../mfc/reference/cedit-class.md) .

### <a name="remarks"></a>Observaciones

Un control `CComboBoxEx` usa un cuadro de edición cuando se crea con el estilo CBS_DROPDOWN.

El `CEdit` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

##  <a name="getextendedstyle"></a>CComboBoxEx:: GetExtendedStyle

Llame a esta función miembro para obtener los estilos extendidos utilizados para un control de `CComboBoxEx`.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Valor DWORD que contiene los estilos extendidos que se usan para el control de cuadro combinado.

### <a name="remarks"></a>Observaciones

Vea [ComboBoxEx control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK para obtener más información acerca de estos estilos.

##  <a name="getimagelist"></a>CComboBoxEx:: GetImageList

Llame a esta función miembro para obtener un puntero a la lista de imágenes utilizada por un control de `CComboBoxEx`.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) . Si se produce un error, esta función miembro devuelve NULL.

### <a name="remarks"></a>Observaciones

El `CImageList` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

##  <a name="getitem"></a>CComboBoxEx:: GetItem

Recupera la información de un elemento de `ComboBoxEx` determinado.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad de la [CBEM_GETITEM](/windows/win32/Controls/cbem-getitem)de mensajes, tal y como se describe en el Windows SDK.

##  <a name="haseditchanged"></a>CComboBoxEx:: HasEditChanged

Determina si el usuario ha cambiado el contenido de la `ComboBoxEx` control de edición escribiendo.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha escrito en el cuadro de edición del control; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad de la [CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged)de mensajes, tal y como se describe en el Windows SDK.

##  <a name="insertitem"></a>CComboBoxEx:: InsertItem

Inserta un nuevo elemento en un control de `ComboBoxEx`.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento. Esta estructura contiene valores de marca de devolución de llamada para el elemento.

### <a name="return-value"></a>Valor devuelto

Índice en el que se insertó el nuevo elemento si se realiza correctamente; de lo contrario,-1.

### <a name="remarks"></a>Observaciones

Cuando se llama a `InsertItem`, se enviará un mensaje de [WM_NOTIFY](/windows/win32/controls/wm-notify) con [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) notificación a la ventana primaria.

##  <a name="setextendedstyle"></a>CComboBoxEx:: SetExtendedStyle

Llame a esta función miembro para establecer los estilos extendidos usados para un control extendido de cuadro combinado.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parámetros

*dwExMask*<br/>
Un valor DWORD que indica qué estilos de *dwExStyles* se van a ver afectados. Solo se cambiarán los estilos extendidos de *dwExMask* . El resto de los estilos se conservarán tal y como están. Si este parámetro es cero, se verán afectados todos los estilos de *dwExStyles* .

*dwExStyles*<br/>
Valor DWORD que contiene los estilos extendidos del control de cuadro combinado que se van a establecer para el control.

### <a name="return-value"></a>Valor devuelto

Valor DWORD que contiene los estilos extendidos utilizados previamente para el control.

### <a name="remarks"></a>Observaciones

Vea [ComboBoxEx control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK para obtener más información acerca de estos estilos.

Para crear un control extendido de cuadro combinado con estilos extendidos de Windows, use [CreateEx](#createex).

##  <a name="setimagelist"></a>CComboBoxEx:: SetImageList

Establece una lista de imágenes para un control `ComboBoxEx`.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a un objeto `CImageList` que contiene las imágenes que se van a utilizar con el control `CComboBoxEx`.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) que contiene las imágenes utilizadas previamente por el control `CComboBoxEx`. ES NULL si no se ha establecido previamente ninguna lista de imágenes.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad de la [CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist)de mensajes, tal y como se describe en el Windows SDK. Si cambia el alto del control de edición predeterminado, llame a la función de Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) para cambiar el tamaño del control después de llamar a `SetImageList`, o no se mostrará correctamente.

El `CImageList` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

##  <a name="setitem"></a>CComboBoxEx:: SetItem

Establece los atributos de un elemento en un control de `ComboBoxEx`.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad de la [CBEM_SETITEM](/windows/win32/Controls/cbem-setitem)de mensajes, tal y como se describe en el Windows SDK.

##  <a name="setwindowtheme"></a>CComboBoxEx:: SetWindowTheme

Establece el estilo visual del control de cuadro combinado extendido.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Puntero a una cadena Unicode que contiene el estilo visual del cuadro combinado extendido que se va a establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del mensaje de [CBEM_SETWINDOWTHEME](/windows/win32/Controls/cbem-setwindowtheme) , como se describe en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo MFCIE de MFC](../../overview/visual-cpp-samples.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)
