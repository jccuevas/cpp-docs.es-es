---
title: CHeaderCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741526"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl (clase)

Proporciona la funcionalidad del control común de encabezado de Windows.

## <a name="syntax"></a>Sintaxis

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Construye un objeto `CHeaderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Borra todos los filtros de un control de encabezado.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Borra el filtro de un control de encabezado.|
|[CHeaderCtrl::Create](#create)|Crea un control de encabezado y lo adjunta a un `CHeaderCtrl` objeto.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.|
|[CHeaderCtrl::CreateEx](#createex)|Crea un control de encabezado con los estilos extendidos de Windows especificados y lo `CListCtrl` adjunta a un objeto.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Elimina un elemento de un control de encabezado.|
|[CHeaderCtrl::DrawItem](#drawitem)|Dibuja el elemento especificado de un control de encabezado.|
|[CHeaderCtrl::EditFilter](#editfilter)|Comienza a editar el filtro especificado de un control de encabezado.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Recupera el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtiene el identificador del elemento en el control de encabezado actual que tiene el foco.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Recupera el identificador de una lista de imágenes utilizada para dibujar los elementos de encabezado en un control de encabezado.|
|[CHeaderCtrl::GetItem](#getitem)|Recupera información sobre un elemento en un control de encabezado.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Recupera un recuento de los elementos de un control de encabezado.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtiene la información del rectángulo delimitador para el botón desplegable especificado de un control de encabezado.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de un elemento determinado en un control de encabezado.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtiene el rectángulo delimitador del botón de desbordamiento para el control de encabezado actual.|
|[CHeaderCtrl::HitTest](#hittest)|Determina qué elemento de encabezado se encuentra en un punto especificado, si existe.|
|[CHeaderCtrl::InsertItem](#insertitem)|Inserta un nuevo elemento en un control de encabezado.|
|[CHeaderCtrl::Layout](#layout)|Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Recupera el valor de índice de un elemento en función de su orden en el control de encabezado.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Establece el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Establece el intervalo de tiempo de espera entre el momento en que se realiza un cambio en los atributos de `HDN_FILTERCHANGE` filtro y el envío de una notificación.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Establece el foco en un elemento de encabezado especificado en el control de encabezado actual.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Cambia el divisor entre los elementos de encabezado para indicar una función de arrastrar y colocar manual de un elemento de encabezado.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de encabezado.|
|[CHeaderCtrl::SetItem](#setitem)|Establece los atributos del elemento especificado en un control de encabezado.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Establece el orden de izquierda a derecha de los elementos de un control de encabezado.|

## <a name="remarks"></a>Comentarios

Un control de encabezado es una ventana que normalmente se coloca sobre un conjunto de columnas de texto o números. Contiene un título para cada columna y puede dividirse en partes. El usuario puede arrastrar los divisores que separan los elementos para establecer el ancho de cada columna. Para ver una ilustración de un control de encabezado, vea [controles de encabezado](/windows/win32/Controls/header-controls).

Este control (y, por `CHeaderCtrl` lo tanto, la clase) solo está disponible para los programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

La funcionalidad agregada para los controles comunes de Windows 95/Internet Explorer 4,0 incluye lo siguiente:

- Ordenación personalizada del elemento de encabezado.

- Arrastrar y colocar elementos de encabezado, para reordenar los elementos de encabezado. Use el estilo HDS_DRAGDROP al crear el `CHeaderCtrl` objeto.

- El texto de la columna de encabezado es visible constantemente durante el cambio de tamaño de la columna. Use el estilo HDS_FULLDRAG al crear un `CHeaderCtrl` objeto.

- Seguimiento activo de encabezado, que resalta el elemento de encabezado cuando el puntero se mantiene sobre él. Use el estilo HDS_HOTTRACK al crear el `CHeaderCtrl` objeto.

- Compatibilidad con la lista de imágenes. Los elementos de encabezado pueden contener imágenes almacenadas en un `CImageList` objeto o texto.

Para obtener más información sobre `CHeaderCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl

Construye un objeto `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters

Borra todos los filtros de un control de encabezado.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) con un valor de columna de-1, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

Borra el filtro de un control de encabezado.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parámetros

*nColumn*<br/>
Valor de columna que indica qué filtro se va a borrar.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

Crea un control de encabezado y lo adjunta a un `CHeaderCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de control de encabezado](/windows/win32/Controls/header-control-styles) en el Windows SDK.

*rect*<br/>
Especifica el tamaño y la posición del control de encabezado. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de encabezado, normalmente `CDialog`una. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de encabezado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario, es cero.

### <a name="remarks"></a>Comentarios

Un `CHeaderCtrl` objeto se crea en dos pasos. En primer lugar, llame al constructor y `Create`, a continuación, llame `CHeaderCtrl` a, que crea el control de encabezado y lo adjunta al objeto.

Además de los estilos de control de encabezado, puede usar los siguientes estilos de control comunes para determinar cómo se sitúa el control de encabezado y cambiar su tamaño (vea [estilos de control comunes](/windows/win32/Controls/common-control-styles) para obtener más información):

- CCS_BOTTOM hace que el control se coloque en la parte inferior del área de cliente de la ventana primaria y establezca el ancho en el mismo que el ancho de la ventana primaria.

- CCS_NODIVIDER evita que se dibuje un resaltado de dos píxeles en la parte superior del control.

- CCS_NOMOVEY hace que el control cambie de tamaño y se mueva horizontalmente, pero no verticalmente, en respuesta a un mensaje WM_SIZE. Si se usa el estilo CCS_NORESIZE, este estilo no se aplica. De forma predeterminada, los controles de encabezado tienen este estilo.

- CCS_NOPARENTALIGN impide que el control se mueva automáticamente a la parte superior o inferior de la ventana primaria. En su lugar, el control mantiene su posición dentro de la ventana primaria a pesar de los cambios en el tamaño de la ventana primaria. Si también se usa el estilo CCS_TOP o CCS_BOTTOM, el alto se ajusta al valor predeterminado, pero la posición y el ancho permanecen inalterados.

- CCS_NORESIZE impide que el control use el ancho y el alto predeterminados al establecer su tamaño inicial o un nuevo tamaño. En su lugar, el control usa el ancho y el alto especificados en la solicitud de creación o ajuste de tamaño.

- CCS_TOP hace que el control se coloque en la parte superior del área de cliente de la ventana primaria y establece el ancho en el mismo que el ancho de la ventana primaria.

También puede aplicar los siguientes estilos de ventana a un control de encabezado (consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) para obtener más información):

- WS_CHILD crea una ventana secundaria. No se puede usar con el estilo WS_POPUP.

- WS_VISIBLE crea una ventana que está inicialmente visible.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente.

- WS_GROUP especifica el primer control de un grupo de controles en el que el usuario puede moverse de un control al siguiente con las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo de estilos e inicia el grupo siguiente (es decir, un grupo finaliza en el que comienza la siguiente).

- WS_TABSTOP especifica uno de los diversos controles a través de los cuales el usuario puede desplazarse mediante la tecla TAB. La tecla TAB mueve el usuario al siguiente control especificado por el estilo WS_TABSTOP.

Si desea utilizar estilos extendidos de Windows con el control, llame a [CreateEx](#createex) en lugar `Create`de a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CHeaderCtrl` objeto.

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
Estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de control de encabezado](/windows/win32/Controls/header-control-styles) en el Windows SDK. Vea [crear](#create) para obtener una lista de estilos adicionales.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de `Create` para aplicar los estilos extendidos de Windows, especificados por el **WS_EX_** de estilo extendido de Windows.

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento dentro del control de encabezado. La imagen asignada a este elemento es la base de la imagen transparente.

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) si se realiza correctamente; de lo contrario, NULL. La lista devuelta contiene una sola imagen.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage), tal y como se describe en el Windows SDK. Se proporciona para admitir arrastrar y colocar elementos de encabezado.

El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento en tiempo de inactividad.

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

Elimina un elemento de un control de encabezado.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica el índice de base cero del elemento que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

Lo llama el marco de trabajo cuando cambia un aspecto visual de un control de encabezado dibujado por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [drawitemstruct (](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que describe el elemento que se va a pintar.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalide esta función miembro para implementar el dibujo de un `CHeaderCtrl` objeto dibujado por el propietario.

La aplicación debe restaurar todos los objetos de la interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que esta función miembro finalice.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

Comienza a editar el filtro especificado de un control de encabezado.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parámetros

*nColumn*<br/>
Columna que se va a editar.

*bDiscardChanges*<br/>
Valor que especifica cómo controlar los cambios de edición del usuario si el usuario está en el proceso de edición del filtro cuando se envía el mensaje [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) .

Especifique TRUE para descartar los cambios realizados por el usuario o FALSE para aceptar los cambios realizados por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

Recupera el ancho del margen de un mapa de bits en un control de encabezado.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho del margen del mapa de bits en píxeles.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

Obtiene el índice del elemento que tiene el foco en el control de encabezado actual.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento de encabezado que tiene el foco.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_headerCtrl`la variable,, que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `SetFocusedItem` se `GetFocusedItem` muestran los métodos y. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no sea visible. En el ejemplo siguiente se establece y, a continuación, se confirma el encabezado de la última columna como elemento de foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

Recupera el identificador de una lista de imágenes utilizada para dibujar los elementos de encabezado en un control de encabezado.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un objeto [CImageList](../../mfc/reference/cimagelist-class.md) .

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist), tal y como se describe en el Windows SDK. El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento en tiempo de inactividad.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>  CHeaderCtrl::GetItem

Recupera información sobre un elemento de control de encabezado.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica el índice de base cero del elemento que se va a recuperar.

*pHeaderItem*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que recibe el nuevo elemento. Esta estructura se utiliza con las `InsertItem` funciones `SetItem` miembro y. Cualquier marca establecida en el `mask` elemento garantiza que los valores de los elementos correspondientes se rellenan correctamente después de la devolución. Si el `mask` elemento se establece en cero, los valores de los otros elementos de la estructura no tienen sentido.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

Recupera un recuento de los elementos de un control de encabezado.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de control de encabezado si se realiza correctamente; de lo contrario,-1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::D eleteitem](#deleteitem).

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

Obtiene el rectángulo delimitador del botón desplegable de un elemento de encabezado en el control de encabezado actual.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iItem*|de Índice de base cero de un elemento de encabezado cuyo estilo es HDF_SPLITBUTTON. Para obtener más información, vea `fmt` el miembro de la estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .|
|*lpRect*|enuncia Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) para recibir la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si esta función se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_headerCtrl`la variable,, que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetItemDropDownRect` se muestra el método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación de la primera columna reservada para el botón desplegable de encabezado.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

Recupera el rectángulo delimitador de un elemento determinado en un control de encabezado.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento de control de encabezado.

*lpRect*<br/>
Puntero a la dirección de una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibe la información del rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect), tal y como se describe en el Windows SDK.

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parámetros

*piArray*<br/>
Puntero a la dirección de un búfer que recibe los valores de índice de los elementos del control de encabezado, en el orden en el que aparecen de izquierda a derecha.

*iCount*<br/>
Número de elementos de control de encabezado. No debe ser negativo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray), tal y como se describe en el Windows SDK. Se proporciona para admitir el orden de los elementos de encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

Obtiene el rectángulo delimitador del botón de desbordamiento del control de encabezado actual.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*lpRect*|enuncia Puntero a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que recibe la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si esta función se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el control de encabezado contiene más elementos de los que se pueden mostrar simultáneamente, el control puede mostrar un botón de desbordamiento que se desplaza a los elementos que no están visibles. El control de encabezado debe tener los estilos HDS_OVERFLOW y HDF_SPLITBUTTON para mostrar el botón de desbordamiento. El rectángulo delimitador incluye el botón de desbordamiento y solo existe cuando se muestra el botón de desbordamiento. Para obtener más información, vea [estilos de control de encabezado](/windows/win32/Controls/header-control-styles).

Este método envía el mensaje [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_headerCtrl`la variable,, que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `GetOverflowRect` se muestra el método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no sea visible. Si algunas columnas no están visibles, el control de encabezado dibuja un botón de desbordamiento. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación del botón de desbordamiento.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

Determina qué elemento de encabezado se encuentra en un punto especificado, si existe.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*phdhti*|[in, out] Puntero a una estructura [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) que especifica el punto que se va a probar y recibe los resultados de la prueba.|

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento de encabezado, si existe, en la posición especificada; de lo contrario,-1.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_headerCtrl`la variable,, que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `HitTest` se muestra el método. En una sección anterior de este ejemplo de código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no sea visible. En este ejemplo se notifica el índice de la columna si es visible y-1 si la columna no está visible.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem

Inserta un nuevo elemento en un control de encabezado en el índice especificado.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Índice de base cero del elemento que se va a insertar. Si el valor es cero, el elemento se inserta al principio del control de encabezado. Si el valor es mayor que el valor máximo, el elemento se inserta al final del control de encabezado.

*phdi*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que contiene información sobre el elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice del nuevo elemento si se realiza correctamente; de lo contrario,-1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parámetros

*pHeaderLayout*<br/>
Puntero a una estructura [HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout) , que contiene información que se usa para establecer el tamaño y la posición de un control de encabezado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función se usa para determinar las dimensiones adecuadas para un nuevo control de encabezado que va a ocupar el rectángulo especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

Recupera el valor de índice de un elemento en función de su orden en el control de encabezado.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parámetros

*nOrder*<br/>
El orden basado en cero en el que aparece el elemento en el control de encabezado, de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Índice del elemento, en función de su orden en el control de encabezado. El índice cuenta de izquierda a derecha, empezando por 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex), tal y como se describe en el Windows SDK. Se proporciona para admitir el orden de los elementos de encabezado.

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

Establece el ancho del margen de un mapa de bits en un control de encabezado.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
Ancho, especificado en píxeles, del margen que rodea un mapa de bits dentro de un control de encabezado existente.

### <a name="return-value"></a>Valor devuelto

Ancho del margen del mapa de bits en píxeles.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

Establece el intervalo de tiempo de espera entre el momento en que se produce un cambio en los atributos de filtro y el registro de una notificación de [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) .

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Valor de tiempo de espera, en milisegundos.

### <a name="return-value"></a>Valor devuelto

Índice del control de filtro que se va a modificar.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout), tal y como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

Establece el foco en un elemento de encabezado especificado en el control de encabezado actual.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*iItem*|de Índice de base cero de un elemento de encabezado.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) , que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se define `m_headerCtrl`la variable,, que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente `SetFocusedItem` se `GetFocusedItem` muestran los métodos y. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no sea visible. En el ejemplo siguiente se establece y, a continuación, se confirma el encabezado de la última columna como elemento de foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

Cambia el divisor entre los elementos de encabezado para indicar una función de arrastrar y colocar manual de un elemento de encabezado.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Posición del puntero. El control de encabezado resalta el divisor adecuado en función de la posición del puntero.

*nIndex*<br/>
Índice del divisor resaltado.

### <a name="return-value"></a>Valor devuelto

Índice del divisor resaltado.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider), tal y como se describe en el Windows SDK. Se proporciona para admitir arrastrar y colocar elementos de encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

Asigna una lista de imágenes a un control de encabezado.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Un puntero a un `CImageList` objeto que contiene la lista de imágenes que se va a asignar al control de encabezado.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto [CImageList](../../mfc/reference/cimagelist-class.md) previamente asignado al control de encabezado.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist), tal y como se describe en el Windows SDK. El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento en tiempo de inactividad.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl:: GetImageList](#getimagelist).

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

Establece los atributos del elemento especificado en un control de encabezado.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Índice de base cero del elemento que se va a manipular.

*pHeaderItem*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que contiene información sobre el nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl:: GetItem](#getitem).

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

Establece el orden de izquierda a derecha de los elementos de un control de encabezado.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parámetros

*iCount*<br/>
Número de elementos de control de encabezado.

*piArray*<br/>
Puntero a la dirección de un búfer que recibe los valores de índice de los elementos del control de encabezado, en el orden en el que aparecen de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray), tal y como se describe en el Windows SDK. Se proporciona para admitir el orden de los elementos de encabezado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl:: GetOrderArray](#getorderarray).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList (clase)](../../mfc/reference/cimagelist-class.md)
