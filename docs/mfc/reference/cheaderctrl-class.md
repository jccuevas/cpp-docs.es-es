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
ms.openlocfilehash: de1705d47c5692d3563bc7d9cb2646531819197a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750923"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl (clase)

Proporciona la funcionalidad del control común de encabezado de Windows.

## <a name="syntax"></a>Sintaxis

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|Construye un objeto `CHeaderCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|Borra todos los filtros de un control de encabezado.|
|[CHeaderCtrl::ClearFilter](#clearfilter)|Borra el filtro de un control de encabezado.|
|[CHeaderCtrl::Create](#create)|Crea un control de encabezado `CHeaderCtrl` y lo adjunta a un objeto.|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.|
|[CHeaderCtrl::CreateEx](#createex)|Crea un control de encabezado con los estilos `CListCtrl` extendidos de Windows especificados y lo asocia a un objeto.|
|[CHeaderCtrl::DeleteItem](#deleteitem)|Elimina un elemento de un control de encabezado.|
|[CHeaderCtrl::DrawItem](#drawitem)|Dibuja el elemento especificado de un control de encabezado.|
|[CHeaderCtrl::EditFilter](#editfilter)|Comienza a editar el filtro especificado de un control de encabezado.|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Recupera el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtiene el identificador del elemento en el control de encabezado actual que tiene el foco.|
|[CHeaderCtrl::GetImageList](#getimagelist)|Recupera el identificador de una lista de imágenes utilizada para dibujar elementos de encabezado en un control de encabezado.|
|[CHeaderCtrl::GetItem](#getitem)|Recupera información sobre un elemento en un control de encabezado.|
|[CHeaderCtrl::GetItemCount](#getitemcount)|Recupera un recuento de los elementos de un control de encabezado.|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtiene la información del rectángulo delimitador para el botón desplegable especificado en un control de encabezado.|
|[CHeaderCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador de un elemento determinado en un control de encabezado.|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|Recupera el orden de izquierda a derecha de los elementos en un control de encabezado.|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtiene el rectángulo delimitador del botón de desbordamiento para el control de encabezado actual.|
|[CHeaderCtrl::HitTest](#hittest)|Determina qué elemento de encabezado, si existe, se encuentra en un punto especificado.|
|[CHeaderCtrl::InsertItem](#insertitem)|Inserta un nuevo elemento en un control de encabezado.|
|[CHeaderCtrl::Layout](#layout)|Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Recupera el valor de índice de un elemento en función de su orden en el control de encabezado.|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Establece el ancho del margen de un mapa de bits en un control de encabezado.|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Establece el intervalo de tiempo de espera entre el momento `HDN_FILTERCHANGE` en que se produce un cambio en los atributos de filtro y la publicación de una notificación.|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Establece el foco en un elemento de encabezado especificado en el control de encabezado actual.|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Cambia el divisor entre los elementos de encabezado para indicar un arrastrar y colocar manualmente de un elemento de encabezado.|
|[CHeaderCtrl::SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de encabezado.|
|[CHeaderCtrl::SetItem](#setitem)|Establece los atributos del elemento especificado en un control de encabezado.|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|Establece el orden de izquierda a derecha de los elementos en un control de encabezado.|

## <a name="remarks"></a>Observaciones

Un control de encabezado es una ventana que normalmente se coloca encima de un conjunto de columnas de texto o números. Contiene un título para cada columna y se puede dividir en partes. El usuario puede arrastrar los divisores que separan las partes para establecer el ancho de cada columna. Para obtener una ilustración de un control de encabezado, vea [Controles de encabezado](/windows/win32/Controls/header-controls).

Este control (y, por lo tanto, la `CHeaderCtrl` clase) solo está disponible para los programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

La funcionalidad agregada para los controles comunes de Windows 95/Internet Explorer 4.0 incluye lo siguiente:

- Pedido personalizado del elemento de encabezado.

- Arrastrar y colocar elementos de encabezado, para reordenar los elementos de encabezado. Utilice el estilo HDS_DRAGDROP `CHeaderCtrl` al crear el objeto.

- Texto de columna de encabezado visible constantemente durante el cambio de tamaño de la columna. Utilice el estilo HDS_FULLDRAG `CHeaderCtrl` al crear un objeto.

- Seguimiento en caliente de encabezado, que resalta el elemento de encabezado cuando el puntero está pasando el cursor sobre él. Utilice el estilo HDS_HOTTRACK `CHeaderCtrl` al crear el objeto.

- Compatibilidad con la lista de imágenes. Los elementos de encabezado `CImageList` pueden contener imágenes almacenadas en un objeto o texto.

Para obtener más `CHeaderCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y [uso de CHeaderCtrl](../../mfc/using-cheaderctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl

Construye un objeto `CHeaderCtrl`.

```
CHeaderCtrl();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters

Borra todos los filtros de un control de encabezado.

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método implementa el comportamiento del [mensaje](/windows/win32/Controls/hdm-clearfilter) Win32 HDM_CLEARFILTER con un valor de columna de -1, como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>CHeaderCtrl::ClearFilter

Borra el filtro de un control de encabezado.

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>Parámetros

*nColumna*<br/>
Valor de columna que indica qué filtro se va a borrar.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método implementa el comportamiento del [mensaje](/windows/win32/Controls/hdm-clearfilter)Win32 HDM_CLEARFILTER , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>CHeaderCtrl::Create

Crea un control de encabezado `CHeaderCtrl` y lo adjunta a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [Estilos](/windows/win32/Controls/header-control-styles) de control de encabezado en el Windows SDK.

*Rect*<br/>
Especifica el tamaño y la posición del control de encabezado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`de encabezado, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de encabezado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario cero.

### <a name="remarks"></a>Observaciones

Construir un `CHeaderCtrl` objeto en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CHeaderCtrl` llame a , que crea el control de encabezado y lo adjunta al objeto.

Además de los estilos de control de encabezado, puede utilizar los siguientes estilos de control comunes para determinar cómo se posiciona el control de encabezado y se cambia el tamaño (consulte [Estilos](/windows/win32/Controls/common-control-styles) de control comunes para obtener más información):

- CCS_BOTTOM Hace que el control se posicione en la parte inferior del área de cliente de la ventana primaria y establece el ancho para que sea el mismo que el ancho de la ventana primaria.

- CCS_NODIVIDER Impide que se dibuje un resaltado de dos píxeles en la parte superior del control.

- CCS_NOMOVEY Hace que el control cambie de tamaño y se mueva horizontalmente, pero no verticalmente, en respuesta a un mensaje de WM_SIZE. Si se utiliza el estilo CCS_NORESIZE, este estilo no se aplica. Los controles de encabezado tienen este estilo de forma predeterminada.

- CCS_NOPARENTALIGN Impide que el control se mueva automáticamente a la parte superior o inferior de la ventana primaria. En su lugar, el control mantiene su posición dentro de la ventana primaria a pesar de los cambios en el tamaño de la ventana primaria. Si también se utiliza el estilo CCS_TOP o CCS_BOTTOM, la altura se ajusta al valor predeterminado, pero la posición y la anchura permanecen sin cambios.

- CCS_NORESIZE Impide que el control use el ancho y alto predeterminados al establecer su tamaño inicial o un nuevo tamaño. En su lugar, el control utiliza el ancho y el alto especificados en la solicitud de creación o tamaño.

- CCS_TOP Hace que el control se posicione en la parte superior del área de cliente de la ventana primaria y establece el ancho para que sea el mismo que el ancho de la ventana primaria.

También puede aplicar los siguientes estilos de ventana a un control de encabezado (consulte [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana para obtener más información):

- WS_CHILD Crea una ventana secundaria. No se puede utilizar con el estilo WS_POPUP.

- WS_VISIBLE Crea una ventana que está visible inicialmente.

- WS_DISABLED Crea una ventana que está deshabilitada inicialmente.

- WS_GROUP Especifica el primer control de un grupo de controles en el que el usuario puede pasar de un control al siguiente con las teclas de flecha. Todos los controles definidos con el estilo WS_GROUP después del primer control pertenecen al mismo grupo. El siguiente control con el estilo WS_GROUP finaliza el grupo de estilos e inicia el siguiente grupo (es decir, un grupo termina donde comienza el siguiente).

- WS_TABSTOP Especifica uno de los controles a través de los cuales el usuario puede mover mediante la tecla TAB. La tecla TAB mueve al usuario al siguiente control especificado por el estilo WS_TABSTOP.

Si desea utilizar estilos de ventanas extendidas `Create`con el control, llame a [CreateEx](#createex) en lugar de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>CHeaderCtrl::CreateEx

Crea un control (una ventana secundaria) `CHeaderCtrl` y lo asocia con el objeto.

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
Estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [Estilos](/windows/win32/Controls/header-control-styles) de control de encabezado en el Windows SDK. Consulte [Crear](#create) para obtener una lista de estilos adicionales.

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

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>CHeaderCtrl::CreateDragImage

Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del elemento dentro del control de encabezado. La imagen asignada a este elemento es la base de la imagen transparente.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto si se realiza correctamente; NULL. La lista devuelta contiene solo una imagen.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage), como se describe en el Windows SDK. Se proporciona para admitir el arrastrar y colocar elementos de encabezado.

El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderCtrl::DeleteItem

Elimina un elemento de un control de encabezado.

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica el índice de base cero del elemento que se va a eliminar.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>CHeaderCtrl::DrawItem

Llamado por el marco de trabajo cuando cambia un aspecto visual de un control de encabezado de dibujo por el propietario.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parámetros

*lpDrawItemStruct*<br/>
Puntero a una estructura [DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct) que describe el elemento que se va a pintar.

### <a name="remarks"></a>Observaciones

El `itemAction` miembro `DRAWITEMSTRUCT` de la estructura define la acción de dibujo que se va a realizar.

De forma predeterminada, esta función miembro no hace nada. Invalidar esta función miembro para implementar `CHeaderCtrl` el dibujo para un objeto de dibujo del propietario.

La aplicación debe restaurar todos los objetos de interfaz de dispositivo gráfico (GDI) seleccionados para el contexto de presentación proporcionado en *lpDrawItemStruct* antes de que finalice esta función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>CHeaderCtrl::EditFilter

Comienza a editar el filtro especificado de un control de encabezado.

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>Parámetros

*nColumna*<br/>
La columna que se va a editar.

*bDiscardChanges*<br/>
Valor que especifica cómo controlar los cambios de edición del usuario si el usuario está en el proceso de edición del filtro cuando se envía el mensaje [de HDM_EDITFILTER.](/windows/win32/Controls/hdm-editfilter)

Especifique TRUE para descartar los cambios realizados por el usuario o FALSE para aceptar los cambios realizados por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método implementa el comportamiento del [mensaje](/windows/win32/Controls/hdm-editfilter)Win32 HDM_EDITFILTER , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin

Recupera el ancho del margen de un mapa de bits en un control de encabezado.

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>Valor devuelto

El ancho del margen de mapa de bits en píxeles.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin), como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem

Obtiene el índice del elemento que tiene el foco en el control de encabezado actual.

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento de encabezado que tiene el foco.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje HDM_GETFOCUSEDITEM,](/windows/win32/Controls/hdm-getfocuseditem) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_headerCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `SetFocusedItem` `GetFocusedItem` código siguiente se muestran los métodos y. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columnas para que la columna no esté visible. En el ejemplo siguiente se establece y, a continuación, se confirma el último encabezado de columna como el elemento de foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>CHeaderCtrl::GetImageList

Recupera el identificador de una lista de imágenes utilizada para dibujar elementos de encabezado en un control de encabezado.

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/hdm-getimagelist)Win32 HDM_GETIMAGELIST , como se describe en el Windows SDK. El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>CHeaderCtrl::GetItem

Recupera información sobre un elemento de control de encabezado.

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Especifica el índice de base cero del elemento que se va a recuperar.

*pHeaderItem*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que recibe el nuevo elemento. Esta estructura se `InsertItem` utiliza `SetItem` con las funciones miembro y. Las marcas establecidas en el `mask` elemento garantizan que los valores de los elementos correspondientes se rellenan correctamente al devolverlos. Si `mask` el elemento se establece en cero, los valores de los demás elementos de estructura no tienen sentido.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>CHeaderCtrl::GetItemCount

Recupera un recuento de los elementos de un control de encabezado.

```
int GetItemCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos de control de encabezado si se realiza correctamente; de lo contrario - 1.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::DeleteItem](#deleteitem).

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect

Obtiene el rectángulo delimitador del botón desplegable para un elemento de encabezado en el control de encabezado actual.

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iItem*|[en] El índice de base cero de un elemento de encabezado cuyo estilo es HDF_SPLITBUTTON. Para obtener más `fmt` información, vea el miembro de la [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) estructura.|
|*lpRect*|[fuera] Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) para recibir la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUESi esta función se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) mensaje, que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_headerCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `GetItemDropDownRect` código siguiente se muestra el método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación en la primera columna que está reservado para el botón desplegable de encabezado.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>CHeaderCtrl::GetItemRect

Recupera el rectángulo delimitador de un elemento determinado en un control de encabezado.

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
El índice de base cero del elemento de control de encabezado.

*lpRect*<br/>
Puntero a la dirección de una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que recibe la información del rectángulo delimitador.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Este método implementa el comportamiento del [mensaje](/windows/win32/Controls/hdm-getitemrect)de Win32 HDM_GETITEMRECT , como se describe en el Windows SDK.

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>CHeaderCtrl::GetOrderArray

Recupera el orden de izquierda a derecha de los elementos en un control de encabezado.

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>Parámetros

*piArray*<br/>
Puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.

*iCount*<br/>
El número de elementos de control de encabezado. Debe ser no negativo.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/hdm-getorderarray)Win32 HDM_GETORDERARRAY , como se describe en el Windows SDK. Se proporciona para admitir el pedido de artículos de encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect

Obtiene el rectángulo delimitador del botón de desbordamiento del control de encabezado actual.

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*lpRect*|[fuera] Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que recibe la información del rectángulo delimitador.|

### <a name="return-value"></a>Valor devuelto

TRUESi esta función se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si el control de encabezado contiene más elementos de los que se pueden mostrar simultáneamente, el control puede mostrar un botón de desbordamiento que se desplaza a los elementos que no están visibles. El control de encabezado debe tener los estilos HDS_OVERFLOW y HDF_SPLITBUTTON para mostrar el botón de desbordamiento. El rectángulo delimitador encierra el botón de desbordamiento y solo existe cuando se muestra el botón de desbordamiento. Para obtener más información, consulte [Estilos](/windows/win32/Controls/header-control-styles)de control de encabezado .

Este método envía el [mensaje HDM_GETOVERFLOWRECT,](/windows/win32/Controls/hdm-getoverflowrect) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_headerCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `GetOverflowRect` código siguiente se muestra el método. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columnas para que la columna no esté visible. Si algunas columnas no están visibles, el control de encabezado dibuja un botón de desbordamiento. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación del botón de desbordamiento.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>CHeaderCtrl::HitTest

Determina qué elemento de encabezado, si existe, se encuentra en un punto especificado.

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*phdhti*|[adentro, fuera] Puntero a una estructura [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) que especifica el punto que se va a probar y recibe los resultados de la prueba.|

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento de encabezado, si existe, en la posición especificada; de lo contrario, -1.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje HDM_HITTEST,](/windows/win32/Controls/hdm-hittest) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_headerCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `HitTest` código siguiente se muestra el método. En una sección anterior de este ejemplo de código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columnas para que la columna no esté visible. En este ejemplo se notifica el índice de la columna si está visible y -1 si la columna no está visible.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>CHeaderCtrl::InsertItem

Inserta un nuevo elemento en un control de encabezado en el índice especificado.

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Índice de base cero del elemento que se va a insertar. Si el valor es cero, el elemento se inserta al principio del control de encabezado. Si el valor es mayor que el valor máximo, el elemento se inserta al final del control de encabezado.

*phdi*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que contiene información sobre el elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Indice del nuevo elemento si se realiza correctamente; de lo contrario - 1.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>CHeaderCtrl::Layout

Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>Parámetros

*pHeaderLayout*<br/>
Puntero a una estructura [HDLAYOUT,](/windows/win32/api/commctrl/ns-commctrl-hdlayout) que contiene información utilizada para establecer el tamaño y la posición de un control de encabezado.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función se utiliza para determinar las dimensiones adecuadas para un nuevo control de encabezado que va a ocupar el rectángulo especificado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>CHeaderCtrl::OrderToIndex

Recupera el valor de índice de un elemento en función de su orden en el control de encabezado.

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>Parámetros

*Norder*<br/>
El orden de base cero que el elemento aparece en el control de encabezado, de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

El índice del elemento, en función de su orden en el control de encabezado. El índice cuenta de izquierda a derecha, empezando por 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [macro de](/windows/win32/controls/hdm-ordertoindex)Win32 HDM_ORDERTOINDEX , como se describe en el Windows SDK. Se proporciona para admitir el pedido de artículos de encabezado.

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin

Establece el ancho del margen de un mapa de bits en un control de encabezado.

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>Parámetros

*nAncho*<br/>
Ancho, especificado en píxeles, del margen que rodea un mapa de bits dentro de un control de encabezado existente.

### <a name="return-value"></a>Valor devuelto

El ancho del margen de mapa de bits en píxeles.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)de mensaje de Win32 , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout

Establece el intervalo de tiempo de espera entre el momento en que se produce un cambio en los atributos de filtro y el registro de una notificación [de HDN_FILTERCHANGE.](/windows/win32/Controls/hdn-filterchange)

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>Parámetros

*dwTimeOut*<br/>
Valor de tiempo de espera, en milisegundos.

### <a name="return-value"></a>Valor devuelto

El índice del control de filtro que se va a modificar.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)de mensaje de Win32 , como se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem

Establece el foco en un elemento de encabezado especificado en el control de encabezado actual.

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*iItem*|[en] El índice de base cero de un elemento de encabezado.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje HDM_SETFOCUSEDITEM,](/windows/win32/Controls/hdm-setfocuseditem) que se describe en el Windows SDK.

### <a name="example"></a>Ejemplo

En el ejemplo de `m_headerCtrl`código siguiente se define la variable, , que se utiliza para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>Ejemplo

En el ejemplo de `SetFocusedItem` `GetFocusedItem` código siguiente se muestran los métodos y. En una sección anterior del código, creamos un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columnas para que la columna no esté visible. En el ejemplo siguiente se establece y, a continuación, se confirma el último encabezado de columna como el elemento de foco.

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider

Cambia el divisor entre los elementos de encabezado para indicar un arrastrar y colocar manualmente de un elemento de encabezado.

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
La posición del puntero. El control de encabezado resalta el divisor adecuado en función de la posición del puntero.

*nIndex*<br/>
El índice del divisor resaltado.

### <a name="return-value"></a>Valor devuelto

El índice del divisor resaltado.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider), como se describe en el Windows SDK. Se proporciona para admitir el arrastrar y colocar elementos de encabezado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>CHeaderCtrl::SetImageList

Asigna una lista de imágenes a un control de encabezado.

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>Parámetros

*pImageList*<br/>
Puntero a `CImageList` un objeto que contiene la lista de imágenes que se asignará al control de encabezado.

### <a name="return-value"></a>Valor devuelto

Un puntero a la [CImageList](../../mfc/reference/cimagelist-class.md) objeto asignado previamente al control de encabezado.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)de mensaje de Win32 , como se describe en el Windows SDK. El `CImageList` objeto al que apunta el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::GetImageList](#getimagelist).

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>CHeaderCtrl::SetItem

Establece los atributos del elemento especificado en un control de encabezado.

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
El índice de base cero del elemento que se va a manipular.

*pHeaderItem*<br/>
Puntero a una estructura [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) que contiene información sobre el nuevo elemento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::GetItem](#getitem).

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>CHeaderCtrl::SetOrderArray

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
Puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [macro win32 HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray), como se describe en el Windows SDK. Se proporciona para admitir el pedido de artículos de encabezado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CHeaderCtrl::GetOrderArray](#getorderarray).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList (clase)](../../mfc/reference/cimagelist-class.md)
