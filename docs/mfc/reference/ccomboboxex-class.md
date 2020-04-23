---
title: Clase CComboBoxEx
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
ms.openlocfilehash: a948d54be17103fa83848ff5f0e86dd2c522f0a3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754823"
---
# <a name="ccomboboxex-class"></a>Clase CComboBoxEx

Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Construye un objeto `CComboBoxEx`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComboBoxEx::Crear](#create)|Crea el cuadro combinado y `CComboBoxEx` lo adjunta al objeto.|
|[CComboBoxEx::CreateEx](#createex)|Crea un cuadro combinado con los estilos extendidos `ComboBoxEx` de Windows especificados y lo asocia a un objeto.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Quita un elemento `ComboBoxEx` de un control.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Recupera un puntero al control de cuadro combinado secundario.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Recupera el identificador de la parte `ComboBoxEx` del control de edición de un control.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que `ComboBoxEx` están en uso para un control.|
|[CComboBoxEx::GetImageList](#getimagelist)|Recupera un puntero a la lista `ComboBoxEx` de imágenes asignada a un control.|
|[CComboBoxEx::GetItem](#getitem)|Recupera información de elemento `ComboBoxEx` para un elemento determinado.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Determina si el usuario ha cambiado `ComboBoxEx` el contenido del control de edición escribiendo.|
|[CComboBoxEx::InsertItem](#insertitem)|Inserta un nuevo elemento `ComboBoxEx` en un control.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Establece estilos `ComboBoxEx` extendidos dentro de un control.|
|[CComboBoxEx::SetImageList](#setimagelist)|Establece una lista `ComboBoxEx` de imágenes para un control.|
|[CComboBoxEx::SetItem](#setitem)|Establece los atributos de `ComboBoxEx` un elemento de un control.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Establece el estilo visual del control de cuadro combinado extendido.|

## <a name="remarks"></a>Observaciones

Mediante `CComboBoxEx` el uso de la creación de controles de cuadro combinado, ya no es necesario implementar su propio código de dibujo de imagen. En su `CComboBoxEx` lugar, utilícelo para acceder a las imágenes desde una lista de imágenes.

## <a name="image-list-support"></a>Soporte de lista de imágenes

En un cuadro combinado estándar, el propietario del cuadro combinado es responsable de dibujar una imagen mediante la creación del cuadro combinado como un control de dibujo del propietario. Cuando se `CComboBoxEx`utiliza , no es necesario establecer los estilos de dibujo CBS_OWNERDRAWFIXED y CBS_HASSTRINGS porque están implícitos. De lo contrario, debe escribir código para realizar operaciones de dibujo. Un `CComboBoxEx` control admite hasta tres imágenes por elemento: una para un estado seleccionado, otra para un estado no seleccionado y otra para una imagen de superposición.

## <a name="styles"></a>Estilos

`CComboBoxEx`admite los estilos CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST y WS_CHILD. El control omite todos los demás estilos pasados al crear la ventana. Después de crear la ventana, puede proporcionar `CComboBoxEx` otros estilos de cuadro combinado llamando a la función miembro [SetExtendedStyle](#setextendedstyle). Con estos estilos, puede:

- Establezca las búsquedas de cadenas en la lista para que distinden entre mayúsculas y minúsculas.

- Cree un control de cuadro combinado que use los\\caracteres de barra diagonal ('/'), barra diagonal inversa (' ') y punto ('.') como delimitadores de palabras. Esto permite a los usuarios saltar de palabra en palabra, utilizando el método abreviado de teclado CTRL+ FLECHA.

- Establezca el control de cuadro combinado para mostrar o no una imagen. Si no se muestra ninguna imagen, el cuadro combinado puede eliminar la sangría de texto que acomoda una imagen.

- Cree un control de cuadro combinado estrecho, incluido el tamaño para que recorta el cuadro combinado más amplio que contiene.

Estos indicadores de estilo se describen más adelante en Uso de [CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Atributos de elementode retención y devolución de llamada de elementos

La información de elementos, como índices de elementos e imágenes, valores de sangría y cadenas de texto, se almacena en la estructura de Win32 [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw), como se describe en el Windows SDK. La estructura también contiene miembros que corresponden a marcas de devolución de llamada.

Para obtener una explicación detallada y conceptual, consulte Uso de [CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="ccomboboxexccomboboxex"></a><a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx

Llame a esta función miembro para crear un `CComboBoxEx` objeto.

```
CComboBoxEx();
```

## <a name="ccomboboxexcreate"></a><a name="create"></a>CComboBoxEx::Crear

Crea el cuadro combinado y `CComboBoxEx` lo adjunta al objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de estilos de cuadro combinado aplicados al cuadro combinado. Consulte **Comentarios** a continuación para obtener más información sobre los estilos.

*Rect*<br/>
Una referencia a un [Objeto CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [RECT,](/windows/win32/api/windef/ns-windef-rect) que es la posición y el tamaño del cuadro combinado.

*pParentWnd*<br/>
Puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que es la ventana `CDialog`primaria del cuadro combinado (normalmente un archivo ). No debe ser NULL.

*nID*<br/>
Especifica el identificador de control del cuadro combinado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se creó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Cree `CComboBoxEx` un objeto en dos pasos:

1. Llame a [CComboBoxEx](#ccomboboxex) para construir un `CComboBoxEx` objeto.

1. Llame a esta función miembro, que crea el `CComboBoxEx` cuadro combinado de Windows extendido y lo adjunta al objeto.

Cuando se `Create`llama a , MFC inicializa los controles comunes.

Al crear el cuadro combinado, puede especificar cualquiera o todos los siguientes estilos de cuadro combinado:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Todos los demás estilos pasados al crear la ventana se omiten. El `ComboBoxEx` control también admite estilos extendidos que proporcionan características adicionales. Estos estilos se describen en [ComboBoxEx control de estilos extendidos,](/windows/win32/Controls/comboboxex-control-extended-styles)en el Windows SDK. Establezca estos estilos llamando a [SetExtendedStyle](#setextendedstyle).

Si desea utilizar estilos de ventanas extendidas `Create`con el control, llame a [CreateEx](#createex) en lugar de .

## <a name="ccomboboxexcreateex"></a><a name="createex"></a>CComboBoxEx::CreateEx

Llame a esta función para crear un control de cuadro `CComboBoxEx` combinado extendido (una ventana secundaria) y asociarlo con el objeto.

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
El estilo del control de cuadro combinado. Consulte [Crear](#create) para obtener una lista de estilos.

*Rect*<br/>
Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa `Create` en lugar de aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

`CreateEx`crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Debe establecer estilos extendidos específicos de un control de cuadro combinado extendido mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, `CreateEx` se utiliza para establecer `SetExtendedStyle` estilos como WS_EX_CONTEXTHELP, pero se usa para establecer estilos como CBES_EX_CASESENSITIVE. Para obtener más información, vea los estilos descritos en el tema [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK.

## <a name="ccomboboxexdeleteitem"></a><a name="deleteitem"></a>CComboBoxEx::DeleteItem

Quita un elemento `ComboBoxEx` de un control.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
El índice de base cero del elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

El número de elementos restantes en el control. Si *iIndex* no es válido, la función devuelve CB_ERR.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad del [mensaje CBEM_DELETEITEM](/windows/win32/Controls/cbem-deleteitem), como se describe en el Windows SDK. Al llamar a DeleteItem, se enviará un mensaje [de WM_NOTIFY](/windows/win32/controls/wm-notify) con CBEN_DELETEITEM notificación a la ventana primaria.

## <a name="ccomboboxexgetcomboboxctrl"></a><a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl

Llame a esta función miembro para obtener `CComboBoxEx` un puntero a un control de cuadro combinado dentro de un objeto.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CComboBox` .

### <a name="remarks"></a>Observaciones

El `CComboBoxEx` control consta de una ventana `CComboBox`primaria, que encapsula un archivo .

El `CComboBox` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

## <a name="ccomboboxexgeteditctrl"></a><a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl

Llame a esta función miembro para obtener un puntero al control de edición para un cuadro combinado.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CEdit](../../mfc/reference/cedit-class.md) objeto.

### <a name="remarks"></a>Observaciones

Un `CComboBoxEx` control utiliza un cuadro de edición cuando se crea con el estilo CBS_DROPDOWN.

El `CEdit` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

## <a name="ccomboboxexgetextendedstyle"></a><a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle

Llame a esta función miembro para `CComboBoxEx` obtener los estilos extendidos utilizados para un control.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valor devuelto

El valor DWORD que contiene los estilos extendidos que se usan para el control de cuadro combinado.

### <a name="remarks"></a>Observaciones

Consulte [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK para obtener más información acerca de estos estilos.

## <a name="ccomboboxexgetimagelist"></a><a name="getimagelist"></a>CComboBoxEx::GetImageList

Llame a esta función miembro para obtener `CComboBoxEx` un puntero a la lista de imágenes utilizada por un control.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto. Si se produce un error, esta función miembro devuelve NULL.

### <a name="remarks"></a>Observaciones

El `CImageList` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

## <a name="ccomboboxexgetitem"></a><a name="getitem"></a>CComboBoxEx::GetItem

Recupera información de elemento `ComboBoxEx` para un elemento determinado.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad del [mensaje CBEM_GETITEM](/windows/win32/Controls/cbem-getitem), como se describe en el Windows SDK.

## <a name="ccomboboxexhaseditchanged"></a><a name="haseditchanged"></a>CComboBoxEx::HasEditChanged

Determina si el usuario ha cambiado `ComboBoxEx` el contenido del control de edición escribiendo.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha escrito en el cuadro de edición del control; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad del [mensaje CBEM_HASEDITCHANGED](/windows/win32/Controls/cbem-haseditchanged), como se describe en el Windows SDK.

## <a name="ccomboboxexinsertitem"></a><a name="insertitem"></a>CComboBoxEx::InsertItem

Inserta un nuevo elemento `ComboBoxEx` en un control.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento. Esta estructura contiene valores de marca de devolución de llamada para el elemento.

### <a name="return-value"></a>Valor devuelto

El índice en el que se insertó el nuevo elemento si se realizó correctamente; de lo contrario -1.

### <a name="remarks"></a>Observaciones

Cuando llame `InsertItem`a , se enviará un mensaje [WM_NOTIFY](/windows/win32/controls/wm-notify) con [CBEN_INSERTITEM](/windows/win32/Controls/cben-insertitem) notificación a la ventana primaria.

## <a name="ccomboboxexsetextendedstyle"></a><a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle

Llame a esta función miembro para establecer los estilos extendidos utilizados para un control extendido de cuadro combinado.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parámetros

*dwExMask*<br/>
Un valor DWORD que indica qué estilos de *dwExStyles* se van a ver afectados. Solo se cambiarán los estilos extendidos en *dwExMask.* Todos los demás estilos se mantendrán tal como está. Si este parámetro es cero, todos los estilos de *dwExStyles* se verán afectados.

*dwExStyles*<br/>
Un valor DWORD que contiene el control de cuadro combinado estilos extendidos para establecer para el control.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene los estilos extendidos utilizados anteriormente para el control.

### <a name="remarks"></a>Observaciones

Consulte [ComboBoxEx Control Extended Styles](/windows/win32/Controls/comboboxex-control-extended-styles) en el Windows SDK para obtener más información acerca de estos estilos.

Para crear un control extendido de cuadro combinado con estilos de ventanas extendidas, utilice [CreateEx](#createex).

## <a name="ccomboboxexsetimagelist"></a><a name="setimagelist"></a>CComboBoxEx::SetImageList

Establece una lista `ComboBoxEx` de imágenes para un control.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a `CImageList` un objeto que contiene `CComboBoxEx` las imágenes que se va a utilizar con el control.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que `CComboBoxEx` contiene las imágenes utilizadas anteriormente por el control. NULL si no se ha establecido previamente ninguna lista de imágenes.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad del [mensaje CBEM_SETIMAGELIST](/windows/win32/Controls/cbem-setimagelist), como se describe en el Windows SDK. Si cambia el alto del control de edición predeterminado, llame a la función de Win32 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos) para cambiar el tamaño del control después de llamar `SetImageList`a , o no se mostrará correctamente.

El `CImageList` objeto al que apunta el valor devuelto es un objeto temporal y se destruye durante el siguiente tiempo de procesamiento inactivo.

## <a name="ccomboboxexsetitem"></a><a name="setitem"></a>CComboBoxEx::SetItem

Establece los atributos de `ComboBoxEx` un elemento de un control.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Puntero a una estructura [COMBOBOXEXITEM](/windows/win32/api/commctrl/ns-commctrl-comboboxexitemw) que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa la funcionalidad del [mensaje CBEM_SETITEM](/windows/win32/Controls/cbem-setitem), como se describe en el Windows SDK.

## <a name="ccomboboxexsetwindowtheme"></a><a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme

Establece el estilo visual del control de cuadro combinado extendido.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Puntero a una cadena Unicode que contiene el estilo visual de cuadro combinado extendido que se va a establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad del [mensaje de CBEM_SETWINDOWTHEME,](/windows/win32/Controls/cbem-setwindowtheme) como se describe en el Windows SDK.

## <a name="see-also"></a>Vea también

[Ejemplo MFCIE de MFC](../../overview/visual-cpp-samples.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)
