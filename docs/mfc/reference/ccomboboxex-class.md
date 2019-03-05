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
ms.openlocfilehash: d7a39dd19a51bc5bab0f924d360d594bddf89b44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57265943"
---
# <a name="ccomboboxex-class"></a>CComboBoxEx (clase)

Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.

## <a name="syntax"></a>Sintaxis

```
class CComboBoxEx : public CComboBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Construye un objeto `CComboBoxEx`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComboBoxEx::Create](#create)|Crea el cuadro combinado y lo adjunta a la `CComboBoxEx` objeto.|
|[CComboBoxEx::CreateEx](#createex)|Crea un cuadro combinado con los estilos extendidos de Windows especificados y lo adjunta a un `ComboBoxEx` objeto.|
|[CComboBoxEx::DeleteItem](#deleteitem)|Quita un elemento de un `ComboBoxEx` control.|
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Recupera un puntero al control de cuadro combinado secundario.|
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Recupera el identificador de la parte del control de edición de un `ComboBoxEx` control.|
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que están en uso para un `ComboBoxEx` control.|
|[CComboBoxEx::GetImageList](#getimagelist)|Recupera un puntero a la lista de imágenes asignada a un `ComboBoxEx` control.|
|[CComboBoxEx::GetItem](#getitem)|Recupera información de artículos un determinado `ComboBoxEx` elemento.|
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Determina si el usuario ha cambiado el contenido de la `ComboBoxEx` editar control escribiendo.|
|[CComboBoxEx::InsertItem](#insertitem)|Inserta un nuevo elemento en un `ComboBoxEx` control.|
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos dentro de un `ComboBoxEx` control.|
|[CComboBoxEx::SetImageList](#setimagelist)|Establece una lista de imágenes para un `ComboBoxEx` control.|
|[CComboBoxEx::SetItem](#setitem)|Establece los atributos de un elemento en un `ComboBoxEx` control.|
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Establece el estilo visual de que el cuadro combinado extendido de control de cuadro.|

## <a name="remarks"></a>Comentarios

Mediante el uso de `CComboBoxEx` para crear los controles de cuadro de cuadro combinado, ya no necesita implementar su propia imagen de código de dibujo. En su lugar, use `CComboBoxEx` a las imágenes de acceso de una lista de imágenes.

## <a name="image-list-support"></a>Compatibilidad de la lista de imágenes

En un cuadro combinado estándar, el propietario del cuadro combinado es responsable de dibujar una imagen mediante la creación del cuadro combinado como un control dibujado por el propietario. Cuando usas `CComboBoxEx`, no es necesario establecer los estilos de dibujo CBS_OWNERDRAWFIXED y CBS_HASSTRINGS porque ya que están implícitas. En caso contrario, debe escribir código para realizar operaciones de dibujo. Un `CComboBoxEx` control es compatible con hasta tres imágenes por cada elemento: uno para un estado seleccionado, uno para un estado no seleccionado y otro para una imagen de superposición.

## <a name="styles"></a>Estilos

`CComboBoxEx` es compatible con los estilos CBS_SIMPLE, CBS_DROPDOWN, CBS_DROPDOWNLIST y WS_CHILD. Se omiten todos los demás estilos que se pasa al crear la ventana por el control. Después de crea la ventana, puede proporcionar estilos de cuadro otro combinado mediante una llamada a la `CComboBoxEx` función miembro [SetExtendedStyle](#setextendedstyle). Con estos estilos, puede:

- Conjunto de búsquedas de cadenas en la lista para distinguir mayúsculas de minúsculas.

- Crear un control de cuadro combinado que usa la barra diagonal ('/'), barra diagonal inversa ('\\') y el período ('. ') caracteres como delimitadores de palabras. Esto permite a los usuarios saltar palabras, con el método abreviado de teclado CTRL + FLECHA.

- Establezca al cuadro combinado del control de cuadro para mostrar o no una imagen. Si no se muestra ninguna imagen, el cuadro combinado puede quitar la sangría del texto que dé cabida a una imagen.

- Crear un control de cuadro combinado estrecha, incluido el ajuste de tamaño, por lo que recorta el cuadro combinado más amplio que contiene.

Estas marcas de estilo se describe más detalladamente en [usar CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="item-retention-and-callback-item-attributes"></a>Retención de los elementos y atributos del elemento de devolución de llamada

Información de elemento, como los índices para los elementos y las imágenes, los valores de sangría y cadenas de texto, se almacena en la estructura de Win32 [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema), tal y como se describe en el SDK de Windows. La estructura también contiene a miembros que corresponden a las marcas de devolución de llamada.

Para obtener información conceptual detallada, vea [usar CComboBoxEx](../../mfc/using-ccomboboxex.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

`CComboBoxEx`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="ccomboboxex"></a>  CComboBoxEx::CComboBoxEx

Llame a esta función miembro para crear un `CComboBoxEx` objeto.

```
CComboBoxEx();
```

##  <a name="create"></a>  CComboBoxEx::Create

Crea el cuadro combinado y lo adjunta a la `CComboBoxEx` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica la combinación de los estilos de cuadro combinado que se aplica al cuadro combinado. Consulte **comentarios** a continuación para obtener más información sobre los estilos.

*rect*<br/>
Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que es la posición y tamaño del cuadro combinado.

*pParentWnd*<br/>
Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del cuadro combinado (normalmente un `CDialog`). No debe ser NULL.

*nID*<br/>
Especifica el identificador del control. del cuadro combinado

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se creó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Crear un `CComboBoxEx` objeto en dos pasos:

1. Llame a [CComboBoxEx](#ccomboboxex) para construir un `CComboBoxEx` objeto.

1. Llame a esta función miembro, que crea el cuadro combinado de Windows extendido y lo adjunta a la `CComboBoxEx` objeto.

Cuando se llama a `Create`, MFC inicializa los controles comunes.

Cuando se crea el cuadro combinado, puede especificar alguno o todos de los siguientes estilos de cuadro combinado:

- CBS_SIMPLE

- CBS_DROPDOWN

- CBS_DROPDOWNLIST

- CBS_AUTOHSCROLL

- WS_CHILD

Se omiten todos los demás estilos que se pasa al crear la ventana. El `ComboBoxEx` control también es compatible con los estilos extendidos que proporcionan características adicionales. Estos estilos se describen en [ComboBoxEx controlar estilos extendidos](/windows/desktop/Controls/comboboxex-control-extended-styles), en el SDK de Windows. Establecer estos estilos mediante una llamada a [SetExtendedStyle](#setextendedstyle).

Si desea usar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de `Create`.

##  <a name="createex"></a>  CComboBoxEx::CreateEx

Llame a esta función para crear un control de cuadro combinado extendido (una ventana secundaria) y asócielo con el `CComboBoxEx` objeto.

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
Estilo del control de cuadro combinado. Consulte [crear](#create) para obtener una lista de estilos.

*rect*<br/>
Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de `Create` para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

`CreateEx` crea el control con los estilos extendidos de Windows especificados por *dwExStyle*. Debe establecer los estilos extendidos específicos para un control de cuadro combinado extendido mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, usar `CreateEx` para establecer estos estilos como WS_EX_CONTEXTHELP, pero usa `SetExtendedStyle` para establecer estos estilos como CBES_EX_CASESENSITIVE. Para obtener más información, vea los estilos que se describe en el tema [estilos extendidos ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) en el SDK de Windows.

##  <a name="deleteitem"></a>  CComboBoxEx::DeleteItem

Quita un elemento de un `ComboBoxEx` control.

```
int DeleteItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
Índice de base cero del elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

El número de elementos que quedan en el control. Si *iÍndice* es válido, la función devuelve CB_ERR.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa la funcionalidad del mensaje [CBEM_DELETEITEM](/windows/desktop/Controls/cbem-deleteitem), tal y como se describe en el SDK de Windows. Cuando se llama a DeleteItem, un [WM_NOTIFY](/windows/desktop/controls/wm-notify) se enviará el mensaje de notificación CBEN_DELETEITEM a la ventana primaria.

##  <a name="getcomboboxctrl"></a>  CComboBoxEx::GetComboBoxCtrl

Llame a esta función miembro para obtener un puntero a un control de cuadro combinado en un `CComboBoxEx` objeto.

```
CComboBox* GetComboBoxCtrl();
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto `CComboBox` .

### <a name="remarks"></a>Comentarios

El `CComboBoxEx` control consta de una ventana primaria, que encapsula un `CComboBox`.

La `CComboBox` objeto al que señala el valor devuelto es un objeto temporal y se destruyen durante la próxima vez que el procesamiento inactivo.

##  <a name="geteditctrl"></a>  CComboBoxEx::GetEditCtrl

Llame a esta función miembro para obtener un puntero al control de edición de un cuadro combinado.

```
CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CEdit](../../mfc/reference/cedit-class.md) objeto.

### <a name="remarks"></a>Comentarios

Un `CComboBoxEx` control utiliza un cuadro de edición cuando se crea con el estilo CBS_DROPDOWN.

La `CEdit` objeto al que señala el valor devuelto es un objeto temporal y se destruyen durante la próxima vez que el procesamiento inactivo.

##  <a name="getextendedstyle"></a>  CComboBoxEx::GetExtendedStyle

Llame a esta función miembro para obtener los estilos extendidos utilizados para un `CComboBoxEx` control.

```
DWORD GetExtendedStyle() const;
```

### <a name="return-value"></a>Valor devuelto

El valor DWORD que contiene los estilos extendidos que se usan para el control de cuadro combinado.

### <a name="remarks"></a>Comentarios

Consulte [estilos extendidos ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) en el SDK de Windows para obtener más información acerca de estos estilos.

##  <a name="getimagelist"></a>  CComboBoxEx::GetImageList

Llame a esta función miembro para obtener un puntero a la lista de imágenes usa un `CComboBoxEx` control.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto. Si se produce un error, esta función miembro devuelve NULL.

### <a name="remarks"></a>Comentarios

La `CImageList` objeto al que señala el valor devuelto es un objeto temporal y se destruyen durante la próxima vez que el procesamiento inactivo.

##  <a name="getitem"></a>  CComboBoxEx::GetItem

Recupera información de artículos un determinado `ComboBoxEx` elemento.

```
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Un puntero a un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) estructura que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa la funcionalidad del mensaje [CBEM_GETITEM](/windows/desktop/Controls/cbem-getitem), tal y como se describe en el SDK de Windows.

##  <a name="haseditchanged"></a>  CComboBoxEx::HasEditChanged

Determina si el usuario ha cambiado el contenido de la `ComboBoxEx` editar control escribiendo.

```
BOOL HasEditChanged();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ha escrito en el cuadro de edición del control; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa la funcionalidad del mensaje [CBEM_HASEDITCHANGED](/windows/desktop/Controls/cbem-haseditchanged), tal y como se describe en el SDK de Windows.

##  <a name="insertitem"></a>  CComboBoxEx::InsertItem

Inserta un nuevo elemento en un `ComboBoxEx` control.

```
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Un puntero a un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) estructura que recibirá la información del elemento. Esta estructura contiene valores de indicador de devolución de llamada para el elemento.

### <a name="return-value"></a>Valor devuelto

El índice donde se insertó el nuevo elemento si es correcto; en caso contrario,-1.

### <a name="remarks"></a>Comentarios

Cuando se llama a `InsertItem`, un [WM_NOTIFY](/windows/desktop/controls/wm-notify) de mensajes con [CBEN_INSERTITEM](/windows/desktop/Controls/cben-insertitem) se enviará una notificación a la ventana primaria.

##  <a name="setextendedstyle"></a>  CComboBoxEx::SetExtendedStyle

Llame a esta función miembro para establecer los estilos extendidos utilizados para un cuadro combinado extendido el control.

```
DWORD SetExtendedStyle(
    DWORD dwExMask,
    DWORD dwExStyles);
```

### <a name="parameters"></a>Parámetros

*dwExMask*<br/>
Un valor DWORD que indica qué estilos en *dwExStyles* son se vea afectado. Solo los estilos extendidos en *dwExMask* se cambiará. Todos los demás estilos se conservará tal cual. Si este parámetro es cero, entonces todos los estilos en *dwExStyles* se verán afectados.

*dwExStyles*<br/>
Un valor DWORD que contiene el control de cuadro combinado extendido estilos que se va a establecer para el control.

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene los estilos extendidos utilizados anteriormente para el control.

### <a name="remarks"></a>Comentarios

Consulte [estilos extendidos ComboBoxEx](/windows/desktop/Controls/comboboxex-control-extended-styles) en el SDK de Windows para obtener más información acerca de estos estilos.

Para crear un cuadro combinado extendido el control con los estilos extendidos de windows, use [CreateEx](#createex).

##  <a name="setimagelist"></a>  CComboBoxEx::SetImageList

Establece una lista de imágenes para un `ComboBoxEx` control.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Un puntero a un `CImageList` objeto que contiene las imágenes que puede usar con el `CComboBoxEx` control.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que contiene las imágenes utilizadas previamente por el `CComboBoxEx` control. Es NULL si anteriormente no se estableció ninguna lista de imágenes.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa la funcionalidad del mensaje [CBEM_SETIMAGELIST](/windows/desktop/Controls/cbem-setimagelist), tal y como se describe en el SDK de Windows. Si cambia el alto del control de edición de forma predeterminada, llame a la función de Win32 [SetWindowPos](/windows/desktop/api/winuser/nf-winuser-setwindowpos) para cambiar el tamaño de su control después de llamar a `SetImageList`, o no se mostrarán correctamente.

La `CImageList` objeto al que señala el valor devuelto es un objeto temporal y se destruyen durante la próxima vez que el procesamiento inactivo.

##  <a name="setitem"></a>  CComboBoxEx::SetItem

Establece los atributos de un elemento en un `ComboBoxEx` control.

```
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```

### <a name="parameters"></a>Parámetros

*pCBItem*<br/>
Un puntero a un [COMBOBOXEXITEM](/windows/desktop/api/commctrl/ns-commctrl-tagcomboboxexitema) estructura que recibirá la información del elemento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa la funcionalidad del mensaje [CBEM_SETITEM](/windows/desktop/Controls/cbem-setitem), tal y como se describe en el SDK de Windows.

##  <a name="setwindowtheme"></a>  CComboBoxEx::SetWindowTheme

Establece el estilo visual de que el cuadro combinado extendido de control de cuadro.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parámetros

*pszSubAppName*<br/>
Un puntero a una cadena Unicode que contiene el estilo visual del cuadro combinado extendido para establecer.

### <a name="return-value"></a>Valor devuelto

No se utiliza el valor devuelto.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad de la [CBEM_SETWINDOWTHEME](/windows/desktop/Controls/cbem-setwindowtheme) del mensaje, como se describe en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Ejemplo MFCIE de MFC](../../visual-cpp-samples.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CComboBox (clase)](../../mfc/reference/ccombobox-class.md)
