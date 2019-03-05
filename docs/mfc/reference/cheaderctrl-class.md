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
ms.openlocfilehash: a683c877b67f4eae1a7411f5916987c9789b6817
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261354"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl (clase)

Proporciona la funcionalidad del control común de encabezado de Windows.

## <a name="syntax"></a>Sintaxis

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Construye un objeto `CHeaderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Borra todos los filtros de un control de encabezado.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Borra el filtro para un control de encabezado.|
|[CHeaderCtrl::Create](#create)|Crea un control de encabezado y lo adjunta a un `CHeaderCtrl` objeto.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crea una versión transparente de imagen de un elemento dentro de un control de encabezado.|
|[CHeaderCtrl::CreateEx](#createex)|Crea un control de encabezado con los estilos extendidos de Windows especificados y lo asocia a un `CListCtrl` objeto.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Elimina un elemento de un control de encabezado.|
|[CHeaderCtrl::DrawItem](#drawitem)|Dibuja el elemento especificado de un control de encabezado.|
|[CHeaderCtrl::EditFilter](#editfilter)|Empiece a modificar el filtro especificado de un control de encabezado.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Recupera el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtiene el identificador del elemento en el control de encabezado actual que tiene el foco.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Recupera el identificador de una lista de imágenes que se usa para dibujar elementos de encabezado en un control de encabezado.|
|[CHeaderCtrl::GetItem](#getitem)|Recupera información sobre un elemento en un control de encabezado.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Recupera un recuento de los elementos de un control de encabezado.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtiene la información del rectángulo delimitador para el botón de lista desplegable especificado en un control de encabezado.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador para un elemento determinado en un control de encabezado.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtiene el rectángulo delimitador del botón de desbordamiento para el control de encabezado actual.|
|[CHeaderCtrl::HitTest](#hittest)|Determina qué elemento de encabezado, si existe, se encuentra en un punto especificado.|
|[CHeaderCtrl::InsertItem](#insertitem)|Inserta un nuevo elemento en un control de encabezado.|
|[CHeaderCtrl::Layout](#layout)|Recupera el tamaño y posición de un control de encabezado dentro de un rectángulo determinado.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Recupera el valor de índice para un elemento basándose en su orden en el control de encabezado.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Establece el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Establece el intervalo de tiempo de espera entre el momento en que realiza un cambio en los atributos de filtro y el registro de un `HDN_FILTERCHANGE` notificación.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Establece el foco a un elemento de encabezado especificado en el control de encabezado actual.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Arrastre el divisor entre elementos de encabezado para indicar un manual de los cambios y soltar un elemento de encabezado.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de encabezado.|
|[CHeaderCtrl::SetItem](#setitem)|Establece los atributos del elemento especificado en un control de encabezado.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Establece el orden de izquierda a derecha de los elementos en un control de encabezado.|

## <a name="remarks"></a>Comentarios

Un control de encabezado es una ventana que normalmente se coloca sobre un conjunto de columnas de texto o números. Contiene un título para cada columna, y puede dividirse en partes. El usuario puede arrastrar los divisores que separan las partes para establecer el ancho de cada columna. Para ver una ilustración de un control de encabezado, vea [controles de encabezado](/windows/desktop/Controls/header-controls).

Este control (y, por tanto, la `CHeaderCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Funcionalidad agregada para controles comunes de Windows 95/Internet Explorer 4.0 incluye lo siguiente:

- Orden de personalizado del elemento de encabezado.

- Elemento de encabezado arrastrar y colocar, para la reordenación de elementos de encabezado. Usar HDS_DRAGDROP (estilo) al crear el `CHeaderCtrl` objeto.

- Texto de la columna de encabezado constantemente visible durante el cambio de tamaño de columna. Usar el estilo HDS_FULLDRAG cuando creas un `CHeaderCtrl` objeto.

- Encabezado seguimiento activo, que resalta el elemento de encabezado cuando el puntero se mantiene sobre él. Utilice el estilo HDS_HOTTRACK cuando se crea el `CHeaderCtrl` objeto.

- Compatibilidad con la lista de imágenes. Elementos de encabezado pueden contener imágenes almacenadas en un `CImageList` objeto o texto.

Para obtener más información sobre el uso de `CHeaderCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CHeaderCtrl](../../mfc/using-cheaderctrl.md).

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

Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter) con un valor de columna de -1, como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

Borra el filtro para un control de encabezado.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parámetros

*nColumn*<br/>
Que indica que se filtran para borrar el valor de columna.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](/windows/desktop/Controls/hdm-clearfilter), tal y como se describe en el SDK de Windows.

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
Especifica el estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de Control de encabezado](/windows/desktop/Controls/header-control-styles) en el SDK de Windows.

*rect*<br/>
Especifica el tamaño y la posición del control de encabezado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.

*pParentWnd*<br/>
Especifica la ventana control de encabezado principal, normalmente un `CDialog`. No debe ser NULL.

*nID*<br/>
Especifica el identificador. del control de encabezado

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; en caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Construir un `CHeaderCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a `Create`, que crea el control de encabezado y lo adjunta a la `CHeaderCtrl` objeto.

Además de los estilos de control de encabezado, puede usar los siguientes estilos de control comunes para determinar cómo el control de encabezado coloca y cambia de tamaño (vea [estilos de Control comunes](/windows/desktop/Controls/common-control-styles) para obtener más información):

- CCS_BOTTOM hace que el control se coloque en la parte inferior del área de cliente de la ventana primaria y establece el ancho sea el mismo que el elemento primario de ancho de la ventana.

- CCS_NODIVIDER impide que un píxel de dos resaltar desde que se va a dibujar en la parte superior del control.

- CCS_NOMOVEY hace que el control cambiar el tamaño y moverse horizontalmente, pero no verticalmente, en respuesta a un mensaje WM_SIZE. Si se usa el estilo CCS_NORESIZE, no se aplica este estilo. Controles de encabezado tienen este estilo de forma predeterminada.

- CCS_NOPARENTALIGN impide que el control consiste en mover automáticamente a la parte superior o inferior de la ventana primaria. En su lugar, el control mantiene su posición dentro de la ventana primaria a pesar de los cambios en el tamaño de la ventana primaria. Si también se usa el estilo CCS_TOP o CCS_BOTTOM, se ajusta el alto en el valor predeterminado, pero la posición y el ancho permanecen sin cambios.

- CCS_NORESIZE impide que el control utilizando el ancho y alto predeterminados al establecer su tamaño inicial o un nuevo tamaño. En su lugar, el control utiliza el ancho y alto especificados en la solicitud de creación o cambio de tamaño.

- CCS_TOP hace que el control se coloque en la parte superior del área de cliente de la ventana primaria y establece el ancho sea el mismo que el elemento primario de ancho de la ventana.

También puede aplicar los siguientes estilos de ventana para un control de encabezado (consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) para obtener más información):

- WS_CHILD crea una ventana secundaria. No se puede usar con el estilo WS_POPUP.

- WS_VISIBLE crea una ventana que está visible inicialmente.

- WS_DISABLED crea una ventana que está deshabilitada inicialmente.

- WS_GROUP especifica el primer control de un grupo de controles en el que el usuario puede mover de un control a la siguiente con las teclas de dirección. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El control siguiente con el estilo WS_GROUP finaliza el grupo estilo e inicia el grupo siguiente (es decir, un grupo termina donde comienza el siguiente).

- Especifica WS_TABSTOP uno de cualquier número de controles a través del cual el usuario puede mover mediante la tecla TAB. La tecla TAB mueve el usuario en el control siguiente especificado por el estilo WS_TABSTOP.

Si desea usar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de `Create`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>  CHeaderCtrl::CreateEx

Crea un control (una ventana secundaria) y asócielo con el `CHeaderCtrl` objeto.

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
Estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de Control de encabezado](/windows/desktop/Controls/header-control-styles) en el SDK de Windows. Consulte [crear](#create) para obtener una lista de estilos adicionales.

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

##  <a name="createdragimage"></a>  CHeaderCtrl::CreateDragImage

Crea una versión transparente de imagen de un elemento dentro de un control de encabezado.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento dentro del control de encabezado. La imagen asignada a este elemento es la base para la imagen transparente.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto si es correcto; de lo contrario, NULL. La lista devuelta contiene solo una imagen.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_CREATEDRAGIMAGE](/windows/desktop/Controls/hdm-createdragimage), tal y como se describe en el SDK de Windows. Se proporciona para admitir el encabezado elemento arrastrar y colocar.

La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

Elimina un elemento de un control de encabezado.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Especifica el índice de base cero del elemento que desea eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>  CHeaderCtrl::DrawItem

Lo llama el marco cuando un aspecto visual de un cambios de control de encabezado dibujados por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Un puntero a un [DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct) estructura que describe el elemento que se pinta.

### <a name="remarks"></a>Comentarios

El `itemAction` miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que se realiza.

De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar un dibujado por el propietario del dibujo `CHeaderCtrl` objeto.

La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en *lpDrawItemStruct* antes de este miembro de la función termina.

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
Para editar la columna.

*bDiscardChanges*<br/>
Un valor que especifica cómo tratar el usuario de edición del cambios si el usuario está en proceso de editar el filtro cuando la [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter) se envía el mensaje.

Especifique TRUE para descartar los cambios realizados por el usuario, o FALSE para aceptar los cambios realizados por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_EDITFILTER](/windows/desktop/Controls/hdm-editfilter), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

Recupera el ancho del margen de un mapa de bits en un control de encabezado.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho del margen de mapa de bits en píxeles.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETBITMAPMARGIN](/windows/desktop/Controls/hdm-getbitmapmargin), tal y como se describe en el SDK de Windows.

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

Este método envía el [HDM_GETFOCUSEDITEM](/windows/desktop/Controls/hdm-getfocuseditem) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra el `SetFocusedItem` y `GetFocusedItem` métodos. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no está visible. El ejemplo siguiente se establece y, a continuación, confirma el último encabezado de columna como el elemento con foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

Recupera el identificador de una lista de imágenes que se usa para dibujar elementos de encabezado en un control de encabezado.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETIMAGELIST](/windows/desktop/Controls/hdm-getimagelist), tal y como se describe en el SDK de Windows. La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

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
Puntero a un [DITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) estructura que recibe el nuevo elemento. Esta estructura se usa con el `InsertItem` y `SetItem` funciones miembro. Establecen las marcas en el `mask` elemento asegurarse de que los valores de los elementos correspondientes se rellenan correctamente tras la devolución. Si el `mask` elemento está establecido en cero, los valores de los demás elementos de estructura tienen sentidos.

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

Número de elementos de control de encabezado si se realiza correctamente; en caso contrario, - 1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::DeleteItem](#deleteitem).

##  <a name="getitemdropdownrect"></a>  CHeaderCtrl::GetItemDropDownRect

Obtiene el rectángulo delimitador del botón desplegable de un elemento de encabezado en el control de encabezado actual.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iItem*|[in] Índice de base cero de un elemento de encabezado cuyo estilo es HDF_SPLITBUTTON. Para obtener más información, consulte el `fmt` miembro de la [DITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) estructura.|
|*lpRect*|[out] Puntero a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura para recibir la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si esta función se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [HDM_GETITEMDROPDOWNRECT](/windows/desktop/Controls/hdm-getitemdropdownrect) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra el `GetItemDropDownRect` método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. En el ejemplo de código siguiente se dibuja un rectángulo 3D en torno a la ubicación en la primera columna que está reservada para el botón de lista desplegable del encabezado.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

Recupera el rectángulo delimitador para un elemento determinado en un control de encabezado.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
Índice de base cero del elemento de control de encabezado.

*lpRect*<br/>
Un puntero a la dirección de un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe la información del rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Este método implementa el comportamiento del mensaje de Win32 [HDM_GETITEMRECT](/windows/desktop/Controls/hdm-getitemrect), tal y como se describe en el SDK de Windows.

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parámetros

*piArray*<br/>
Un puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.

*iCount*<br/>
El número de elementos de control de encabezado. Debe ser no negativo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETORDERARRAY](/windows/desktop/Controls/hdm-getorderarray), tal y como se describe en el SDK de Windows. Se proporciona para admitir la ordenación de elementos de encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

Obtiene el rectángulo delimitador del botón de desbordamiento del control de encabezado actual.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpRect*|[out] Puntero a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUE si esta función se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si el control de encabezado contiene más elementos que se pueden mostrar al mismo tiempo, el control puede mostrar un botón de desbordamiento se desplaza a los elementos que no están visibles. El control de encabezado debe tener los estilos HDS_OVERFLOW y HDF_SPLITBUTTON para mostrar el botón de desbordamiento. El rectángulo delimitador adjunta el botón de desbordamiento y sólo existe cuando se muestra el botón de desbordamiento. Para obtener más información, consulte [estilos de Control de encabezado](/windows/desktop/Controls/header-control-styles).

Este método envía el [HDM_GETOVERFLOWRECT](/windows/desktop/Controls/hdm-getoverflowrect) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra el `GetOverflowRect` método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no está visible. Si algunas columnas no están visibles, el control de encabezado dibuja un botón de desbordamiento. En el ejemplo de código siguiente se dibuja un rectángulo 3D en torno a la ubicación del botón de desbordamiento.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

Determina qué elemento de encabezado, si existe, se encuentra en un punto especificado.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*phdhti*|[in, out] Puntero a un [HDHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-_hd_hittestinfo) estructura que especifica el punto de prueba y recibe los resultados de la prueba.|

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento de encabezado, si hay alguno, en la posición especificada; en caso contrario, es -1.

### <a name="remarks"></a>Comentarios

Este método envía el [HDM_HITTEST](/windows/desktop/Controls/hdm-hittest) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra el `HitTest` método. En una sección anterior de este ejemplo de código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no está visible. En este ejemplo devuelve el índice de la columna si está visible y -1 si la columna no está visible.

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
Puntero a un [DITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) estructura que contiene información sobre el elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Índice del nuevo elemento si es correcto; en caso contrario, - 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

Recupera el tamaño y posición de un control de encabezado dentro de un rectángulo determinado.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parámetros

*pHeaderLayout*<br/>
Puntero a un [HDLAYOUT](/windows/desktop/api/commctrl/ns-commctrl-_hd_layout) estructura que contiene información utilizada para establecer el tamaño y posición de un control de encabezado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función se utiliza para determinar las dimensiones adecuadas para un nuevo control de encabezado que se ocupan del rectángulo especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

Recupera el valor de índice para un elemento basándose en su orden en el control de encabezado.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parámetros

*nOrder*<br/>
El orden basado en cero en el que el elemento aparece en el control de encabezado, de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

El índice del elemento, según su orden en el control de encabezado. El índice de la cuenta de izquierda a derecha, comenzando por 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_ORDERTOINDEX](https://msdn.microsoft.com/library/windows/desktop/bb775355), tal y como se describe en el SDK de Windows. Se proporciona para admitir la ordenación de elementos de encabezado.

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

Establece el ancho del margen de un mapa de bits en un control de encabezado.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parámetros

*nWidth*<br/>
Ancho, especificado en píxeles, del margen que rodea a un mapa de bits dentro de un control de encabezado existente.

### <a name="return-value"></a>Valor devuelto

El ancho del margen de mapa de bits en píxeles.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETBITMAPMARGIN](/windows/desktop/Controls/hdm-setbitmapmargin), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

Establece el intervalo de tiempo de espera entre el momento en que realiza un cambio en los atributos de filtro y el registro de un [HDN_FILTERCHANGE](/windows/desktop/Controls/hdn-filterchange) notificación.

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Valor de tiempo de espera, en milisegundos.

### <a name="return-value"></a>Valor devuelto

El índice del control de filtro que se está modificando.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETFILTERCHANGETIMEOUT](/windows/desktop/Controls/hdm-setfilterchangetimeout), tal y como se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

Establece el foco a un elemento de encabezado especificado en el control de encabezado actual.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iItem*|[in] Índice de base cero de un elemento de encabezado.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el [HDM_SETFOCUSEDITEM](/windows/desktop/Controls/hdm-setfocuseditem) mensaje, que se describe en el SDK de Windows.

### <a name="example"></a>Ejemplo

El ejemplo de código siguiente define la variable, `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de código siguiente se muestra el `SetFocusedItem` y `GetFocusedItem` métodos. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no está visible. El ejemplo siguiente se establece y, a continuación, confirma el último encabezado de columna como el elemento con foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

Arrastre el divisor entre elementos de encabezado para indicar un manual de los cambios y soltar un elemento de encabezado.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
La posición del puntero. El control de encabezado resalta el divisor adecuado según la posición del puntero.

*nIndex*<br/>
El índice del divisor de resaltado.

### <a name="return-value"></a>Valor devuelto

El índice del divisor de resaltado.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETHOTDIVIDER](/windows/desktop/Controls/hdm-sethotdivider), tal y como se describe en el SDK de Windows. Se proporciona para admitir el encabezado elemento arrastrar y colocar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

Asigna una lista de imágenes a un control de encabezado.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Un puntero a un `CImageList` objeto que contiene la lista de imágenes que se asignará al control de encabezado.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CImageList](../../mfc/reference/cimagelist-class.md) objeto anteriormente asignado al control de encabezado.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETIMAGELIST](/windows/desktop/Controls/hdm-setimagelist), tal y como se describe en el SDK de Windows. La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::GetImageList](#getimagelist).

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

Establece los atributos del elemento especificado en un control de encabezado.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Índice de base cero del elemento que se pueden manipular.

*pHeaderItem*<br/>
Puntero a un [DITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) estructura que contiene información sobre el nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl:: GetItem](#getitem).

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

Establece el orden de izquierda a derecha de los elementos en un control de encabezado.

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>Parámetros

*iCount*<br/>
El número de elementos de control de encabezado.

*piArray*<br/>
Un puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_SETORDERARRAY](/windows/desktop/Controls/hdm-setorderarray), tal y como se describe en el SDK de Windows. Se proporciona para admitir la ordenación de elementos de encabezado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl:: GetOrderArray](#getorderarray).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList (clase)](../../mfc/reference/cimagelist-class.md)
