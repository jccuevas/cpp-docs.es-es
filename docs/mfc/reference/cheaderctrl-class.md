---
title: CHeaderCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "24"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b839096e87feee970491e393998eb4049df820af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
|[CHeaderCtrl::ClearFilter](#clearfilter)|Borra el filtro para un control de encabezado.|  
|[CHeaderCtrl:: Create](#create)|Crea un control de encabezado y lo adjunta a un `CHeaderCtrl` objeto.|  
|[CHeaderCtrl::CreateDragImage](#createdragimage)|Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.|  
|[CHeaderCtrl::CreateEx](#createex)|Crea un control de encabezado con los estilos extendidos de Windows especificados y lo adjunta a un `CListCtrl` objeto.|  
|[CHeaderCtrl::DeleteItem](#deleteitem)|Elimina un elemento de un control de encabezado.|  
|[CHeaderCtrl::DrawItem](#drawitem)|Dibuja el elemento especificado de un control de encabezado.|  
|[CHeaderCtrl::EditFilter](#editfilter)|Empieza a editar el filtro especificado de un control de encabezado.|  
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|Recupera el ancho del margen de un mapa de bits en un control de encabezado.|  
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|Obtiene el identificador del elemento en el control de encabezado actual que tiene el foco.|  
|[CHeaderCtrl::GetImageList](#getimagelist)|Recupera el identificador de una lista de imágenes que se utiliza para dibujar elementos de encabezado en un control de encabezado.|  
|[CHeaderCtrl:: GetItem](#getitem)|Recupera información sobre un elemento en un control de encabezado.|  
|[CHeaderCtrl::GetItemCount](#getitemcount)|Recupera un recuento de los elementos de un control de encabezado.|  
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|Obtiene la información del rectángulo delimitador para el botón de lista desplegable especificado en un control de encabezado.|  
|[CHeaderCtrl::GetItemRect](#getitemrect)|Recupera el rectángulo delimitador para un elemento determinado en un control de encabezado.|  
|[CHeaderCtrl:: GetOrderArray](#getorderarray)|Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.|  
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|Obtiene el rectángulo delimitador del botón de desbordamiento para el control de encabezado actual.|  
|[CHeaderCtrl::HitTest](#hittest)|Determina qué elemento de encabezado, si los hay, se encuentra en un punto especificado.|  
|[:: InsertItem](#insertitem)|Inserta un nuevo elemento en un control de encabezado.|  
|[CHeaderCtrl:: Layout](#layout)|Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.|  
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|Recupera el valor de índice de un elemento basándose en su orden en el control de encabezado.|  
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|Establece el ancho del margen de un mapa de bits en un control de encabezado.|  
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|Establece el intervalo de tiempo de espera entre el momento en que un cambio realiza en los atributos de filtro y el registro de un `HDN_FILTERCHANGE` notificación.|  
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|Establece el foco a un elemento de encabezado especificado en el control de encabezado actual.|  
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|Arrastre el divisor entre elementos de encabezado para indicar un manual de cambios y eliminación de un elemento de encabezado.|  
|[CHeaderCtrl:: SetImageList](#setimagelist)|Asigna una lista de imágenes a un control de encabezado.|  
|[CHeaderCtrl:: SetItem](#setitem)|Establece los atributos del elemento especificado en un control de encabezado.|  
|[CHeaderCtrl:: SetOrderArray](#setorderarray)|Establece el orden de izquierda a derecha de los elementos en un control de encabezado.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de encabezado es una ventana que normalmente se sitúa por encima de un conjunto de columnas de texto o números. Contiene un título para cada columna, y puede dividirse en partes. El usuario puede arrastrar los divisores que separan las partes para establecer el ancho de cada columna. Para ver una ilustración de un control de encabezado, vea [controles de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238).  
  
 Este control (y, por tanto, la `CHeaderCtrl` clase) está disponible solo para programas que se ejecutan en Windows 95 ó 98 y Windows NT versión 3.51 y posteriores.  
  
 Funcionalidad agregada para los controles comunes de Windows 95 o Internet Explorer 4.0 incluye lo siguiente:  
  
-   Orden de personalizado del elemento de encabezado.  
  
-   Elemento de encabezado arrastrar y colocar, para la reordenación de elementos de encabezado. Use la `HDS_DRAGDROP` aplicar estilo al crear el `CHeaderCtrl` objeto.  
  
-   Texto de la columna de encabezado constantemente visible durante el cambio de tamaño de columna. Use la `HDS_FULLDRAG` estilo cuando se crea un `CHeaderCtrl` objeto.  
  
-   Encabezado seguimiento activo, que resalta el elemento de encabezado cuando se mantiene el puntero sobre él. Use la `HDS_HOTTRACK` aplicar estilo al crear el `CHeaderCtrl` objeto.  
  
-   Compatibilidad con la lista de imágenes. Elementos de encabezado pueden contener imágenes almacenadas en un `CImageList` objeto o texto.  
  
 Para obtener más información sobre el uso de `CHeaderCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CHeaderCtrl](../../mfc/using-cheaderctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CHeaderCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="cheaderctrl"></a>CHeaderCtrl::CHeaderCtrl  
 Construye un objeto `CHeaderCtrl`.  
  
```  
CHeaderCtrl();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]  
  
##  <a name="clearallfilters"></a>CHeaderCtrl::ClearAllFilters  
 Borra todos los filtros de un control de encabezado.  
  
```  
BOOL ClearAllFilters();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306) con un valor de columna de -1, como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]  
  
##  <a name="clearfilter"></a>CHeaderCtrl::ClearFilter  
 Borra el filtro para un control de encabezado.  
  
```  
BOOL ClearFilter(int nColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 `nColumn`  
 Valor de la columna que indica que se filtran para borrar.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método implementa el comportamiento del mensaje de Win32 [HDM_CLEARFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775306), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]  
  
##  <a name="create"></a>CHeaderCtrl:: Create  
 Crea un control de encabezado y lo adjunta a un `CHeaderCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775241) del SDK de Windows.  
  
 `rect`  
 Especifica el tamaño y la posición del control de encabezado. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.  
  
 `pParentWnd`  
 Especifica la ventana control de encabezado principal, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control de encabezado  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización se realizó correctamente; cero en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CHeaderCtrl` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de encabezado y lo adjunta a la `CHeaderCtrl` objeto.  
  
 Además de los estilos de control de encabezado, puede usar los siguientes estilos de control comunes para determinar cómo el control de encabezado se coloca y cambia de tamaño (vea [estilos de Control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498) para obtener más información):  
  
- `CCS_BOTTOM`Hace que el control se coloque en la parte inferior del área de cliente de la ventana primaria y establece el ancho para ser el mismo que el elemento primario de ancho de la ventana.  
  
- `CCS_NODIVIDER`Impide que un resaltado dos píxeles que se va a dibujar en la parte superior del control.  
  
- `CCS_NOMOVEY`Hace que el control cambiar el tamaño y mover propio horizontalmente, pero no verticalmente, en respuesta a un `WM_SIZE` mensaje. Si el `CCS_NORESIZE` estilo se utiliza, no se aplica este estilo. Controles de encabezado tienen este estilo de forma predeterminada.  
  
- `CCS_NOPARENTALIGN`Impide que el control consiste en mover automáticamente a la parte superior o inferior de la ventana primaria. En su lugar, el control mantiene su posición dentro de la ventana primaria a pesar de los cambios en el tamaño de la ventana primaria. Si el `CCS_TOP` o `CCS_BOTTOM` también se utiliza el estilo, el alto se ajusta a la predeterminada, pero la posición y el ancho permanecen sin cambios.  
  
- `CCS_NORESIZE`Impide que usen el ancho y alto predeterminados al establecer su tamaño inicial o un nuevo tamaño del control. En su lugar, el control utiliza el ancho y alto que se especificó en la solicitud de creación o cambio de tamaño.  
  
- `CCS_TOP`Hace que el control se coloque en la parte superior del área de cliente de la ventana primaria y establece el ancho para ser el mismo que el elemento primario de ancho de la ventana.  
  
 También puede aplicar los estilos de ventana siguiente a un control de encabezado (vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) para obtener más información):  
  
- **WS_CHILD** crea una ventana secundaria. No se puede usar con el `WS_POPUP` estilo.  
  
- **WS_VISIBLE** crea una ventana que esté visible inicialmente.  
  
- **WS_DISABLED** crea una ventana que está inicialmente deshabilitada.  
  
- **WS_GROUP** especifica el primer control de un grupo de controles en el que el usuario puede pasar de un control a la siguiente con las teclas de dirección. Todos los controles definidos con el **WS_GROUP** después de que el primer control pertenecen al mismo grupo de estilo. El siguiente control con el **WS_GROUP** estilo finaliza el grupo de estilo e inicia el grupo siguiente (es decir, termina un grupo donde comienza la siguiente).  
  
- **WS_TABSTOP** especifica uno de cualquier número de controles a través del cual el usuario puede mover mediante la tecla TAB. La tecla TAB mueve el usuario al siguiente control especificado por la **WS_TABSTOP** estilo.  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de **crear**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]  
  
##  <a name="createex"></a>CHeaderCtrl::CreateEx  
 Crea un control (una ventana secundaria) y asociarlo con el `CHeaderCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `dwStyle`  
 Estilo del control de encabezado. Para obtener una descripción de los estilos de control de encabezado, vea [estilos de Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775241) del SDK de Windows. Vea [crear](#create) para obtener una lista de estilos adicionales.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente de `pParentWnd`.  
  
 `pParentWnd`  
 Un puntero a la ventana que es primario del control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de **crear** para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="createdragimage"></a>CHeaderCtrl::CreateDragImage  
 Crea una versión transparente de la imagen de un elemento dentro de un control de encabezado.  
  
```  
CImageList* CreateDragImage(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del elemento dentro del control de encabezado. La imagen asignada a este elemento es la base para la imagen transparente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto si es correcto; en caso contrario **NULL**. La lista devuelta contiene solamente una imagen.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_CREATEDRAGIMAGE](http://msdn.microsoft.com/library/windows/desktop/bb775308), tal y como se describe en el SDK de Windows. Se proporciona para admitir el elemento de encabezado, arrastrar y colocar.  
  
 La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.  
  
##  <a name="deleteitem"></a>CHeaderCtrl::DeleteItem  
 Elimina un elemento de un control de encabezado.  
  
```  
BOOL DeleteItem(int nPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica el índice de base cero del elemento que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]  
  
##  <a name="drawitem"></a>CHeaderCtrl::DrawItem  
 Lo llama el marco cuando un aspecto visual de un cambios de control de encabezado dibujados por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero a un [DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802) estructura que describe el elemento que se va a pintar.  
  
### <a name="remarks"></a>Comentarios  
 El **itemAction** miembro de la `DRAWITEMSTRUCT` estructura define la acción de dibujo que va a realizarse.  
  
 De forma predeterminada, esta función miembro no hace nada. Reemplace esta función miembro para implementar el dibujo de un dibujado por el propietario `CHeaderCtrl` objeto.  
  
 La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en `lpDrawItemStruct` antes de este miembro de la función finaliza.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]  
  
##  <a name="editfilter"></a>CHeaderCtrl::EditFilter  
 Empieza a editar el filtro especificado de un control de encabezado.  
  
```  
BOOL EditFilter(
    int nColumn,  
    BOOL bDiscardChanges);
```  
  
### <a name="parameters"></a>Parámetros  
 `nColumn`  
 La columna para editar.  
  
 `bDiscardChanges`  
 Un valor que especifica cómo tratar el usuario de la edición de cambios si el usuario está en proceso de editar el filtro cuando el [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312) se envía el mensaje.  
  
 Especifique `true` para descartar los cambios realizados por el usuario, o `false` para aceptar los cambios realizados por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método implementa el comportamiento del mensaje de Win32 [HDM_EDITFILTER](http://msdn.microsoft.com/library/windows/desktop/bb775312), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]  
  
##  <a name="getbitmapmargin"></a>CHeaderCtrl::GetBitmapMargin  
 Recupera el ancho del margen de un mapa de bits en un control de encabezado.  
  
```  
int GetBitmapMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del margen de mapa de bits en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775314), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]  
  
##  <a name="getfocuseditem"></a>CHeaderCtrl::GetFocusedItem  
 Obtiene el índice del elemento que tiene el foco en el control de encabezado actual.  
  
```  
int GetFocusedItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento de encabezado que tiene el foco.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [HDM_GETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775330) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra la `SetFocusedItem` y `GetFocusedItem` métodos. En una sección anterior del código, se crea un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no es visible. En el ejemplo siguiente se establece y, a continuación, confirma el último encabezado de columna como el elemento de foco.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="getimagelist"></a>CHeaderCtrl::GetImageList  
 Recupera el identificador de una lista de imágenes que se utiliza para dibujar elementos de encabezado en un control de encabezado.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775332), tal y como se describe en el SDK de Windows. La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]  
  
##  <a name="getitem"></a>CHeaderCtrl:: GetItem  
 Recupera información sobre un elemento de control de encabezado.  
  
```  
BOOL GetItem(
    int nPos,  
    HDITEM* pHeaderItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Especifica el índice de base cero del elemento que se va a recuperar.  
  
 `pHeaderItem`  
 Puntero a un [DITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) estructura que recibe el nuevo elemento. Esta estructura se usa con la `InsertItem` y `SetItem` funciones miembro. Las marcas se establecen los **máscara** elemento asegurarse de que los valores de los elementos correspondientes se rellenan correctamente tras la devolución. Si el **máscara** elemento se establece en cero, valores de los otros elementos de estructura no tienen sentidos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]  
  
##  <a name="getitemcount"></a>CHeaderCtrl::GetItemCount  
 Recupera un recuento de los elementos de un control de encabezado.  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos de control de encabezado si se realiza correctamente; en caso contrario, - 1.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CHeaderCtrl::DeleteItem](#deleteitem).  
  
##  <a name="getitemdropdownrect"></a>CHeaderCtrl::GetItemDropDownRect  
 Obtiene el rectángulo delimitador del botón de lista desplegable de un elemento de encabezado en el control de encabezado actual.  
  
```  
BOOL GetItemDropDownRect(
    int iItem,   
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iItem`|Índice de base cero de un elemento de encabezado cuyo estilo es `HDF_SPLITBUTTON`. Para obtener más información, consulte el `fmt` miembro de la [DITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) estructura.|  
|[out] `lpRect`|Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura para recibir la información del rectángulo delimitador.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si esta función se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [HDM_GETITEMDROPDOWNRECT](http://msdn.microsoft.com/library/windows/desktop/bb775339) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `GetItemDropDownRect` método. En una sección anterior del código, se crea un control de encabezado con cinco columnas. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación en la primera columna que se reserva para el botón de lista desplegable del encabezado.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]  
  
##  <a name="getitemrect"></a>CHeaderCtrl::GetItemRect  
 Recupera el rectángulo delimitador para un elemento determinado en un control de encabezado.  
  
```  
BOOL GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del elemento de control de encabezado.  
  
 `lpRect`  
 Un puntero a la dirección de un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe la información del rectángulo delimitador.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Este método implementa el comportamiento del mensaje de Win32 [HDM_GETITEMRECT](http://msdn.microsoft.com/library/windows/desktop/bb775341), tal y como se describe en el SDK de Windows.  
  
##  <a name="getorderarray"></a>CHeaderCtrl:: GetOrderArray  
 Recupera el orden de izquierda a derecha de los elementos de un control de encabezado.  
  
```  
BOOL GetOrderArray(
    LPINT piArray,  
    int iCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `piArray`  
 Un puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.  
  
 `iCount`  
 El número de elementos de control de encabezado. Debe ser no negativo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_GETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775343), tal y como se describe en el SDK de Windows. Se proporciona para permitir la ordenación de elemento de encabezado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]  
  
##  <a name="getoverflowrect"></a>CHeaderCtrl::GetOverflowRect  
 Obtiene el rectángulo delimitador del botón de desbordamiento del control de encabezado actual.  
  
```  
BOOL GetOverflowRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `lpRect`|Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibe la información del rectángulo delimitador.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si esta función se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si el control de encabezado contiene más elementos que se pueden mostrar simultáneamente, el control puede mostrar un botón de desbordamiento se desplaza a elementos que no están visibles. El control de encabezado debe tener la `HDS_OVERFLOW` y `HDF_SPLITBUTTON` estilos para mostrar el botón de desbordamiento. El rectángulo delimitador adjunta el botón de desbordamiento y existe únicamente cuando se muestra el botón de desbordamiento. Para obtener más información, consulte [estilos de Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775241).  
  
 Este método envía el [HDM_GETOVERFLOWRECT](http://msdn.microsoft.com/library/windows/desktop/bb775345) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `GetOverflowRect` método. En una sección anterior del código, se crea un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no es visible. Si algunas columnas no están visibles, el control de encabezado dibuja un botón de desbordamiento. En el ejemplo de código siguiente se dibuja un rectángulo 3D alrededor de la ubicación del botón de desbordamiento.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]  
  
##  <a name="hittest"></a>CHeaderCtrl::HitTest  
 Determina qué elemento de encabezado, si los hay, se encuentra en un punto especificado.  
  
```  
int HitTest(LPHDHITTESTINFO* phdhti);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in, out] `phdhti`|Puntero a un [HDHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb775245) estructura que especifica el punto de prueba y recibe los resultados de la prueba.|  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero del elemento de encabezado, si procede, en la posición especificada; en caso contrario, devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [HDM_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb775349) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `HitTest` método. En una sección anterior de este ejemplo de código, se crea un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no es visible. Este ejemplo devuelve el índice de la columna si está visible y -1 si la columna no está visible.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]  
  
##  <a name="insertitem"></a>:: InsertItem  
 Inserta un nuevo elemento en un control de encabezado en el índice especificado.  
  
```  
int InsertItem(
    int nPos,  
    HDITEM* phdi);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Índice de base cero del elemento que se va a insertar. Si el valor es cero, el elemento se inserta al principio del control de encabezado. Si el valor es mayor que el valor máximo, el elemento se inserta al final del control de encabezado.  
  
 *phdi*  
 Puntero a un [DITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) estructura que contiene información sobre el elemento que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice del nuevo elemento si se realiza correctamente; en caso contrario, - 1.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]  
  
##  <a name="layout"></a>CHeaderCtrl:: Layout  
 Recupera el tamaño y la posición de un control de encabezado dentro de un rectángulo determinado.  
  
```  
BOOL Layout(HDLAYOUT* pHeaderLayout);
```  
  
### <a name="parameters"></a>Parámetros  
 *pHeaderLayout*  
 Puntero a un [HDLAYOUT](http://msdn.microsoft.com/library/windows/desktop/bb775249) estructura que contiene información utilizada para establecer el tamaño y la posición de un control de encabezado.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se utiliza para determinar las dimensiones adecuadas para un nuevo control de encabezado que se ocupan del rectángulo especificado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]  
  
##  <a name="ordertoindex"></a>CHeaderCtrl::OrderToIndex  
 Recupera el valor de índice de un elemento basándose en su orden en el control de encabezado.  
  
```  
int OrderToIndex(int nOrder) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *nOrder*  
 El orden basado en cero en el que el elemento aparece en el control de encabezado, de izquierda a derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del elemento, basándose en su orden en el control de encabezado. El índice de la cuenta de izquierda a derecha, comenzando por 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_ORDERTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb775355), tal y como se describe en el SDK de Windows. Se proporciona para permitir la ordenación de elemento de encabezado.  
  
##  <a name="setbitmapmargin"></a>CHeaderCtrl::SetBitmapMargin  
 Establece el ancho del margen de un mapa de bits en un control de encabezado.  
  
```  
int SetBitmapMargin(int nWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `nWidth`  
 Ancho, especificado en píxeles, del margen que rodea a un mapa de bits dentro de un control de encabezado existente.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del margen de mapa de bits en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETBITMAPMARGIN](http://msdn.microsoft.com/library/windows/desktop/bb775357), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]  
  
##  <a name="setfilterchangetimeout"></a>CHeaderCtrl::SetFilterChangeTimeout  
 Establece el intervalo de tiempo de espera entre el momento en que un cambio realiza en los atributos de filtro y el registro de un [HDN_FILTERCHANGE](http://msdn.microsoft.com/library/windows/desktop/bb775277) notificación.  
  
```  
int SetFilterChangeTimeout(DWORD dwTimeOut);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwTimeOut*  
 Valor de tiempo de espera, en milisegundos.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del control de filtro que se está modificando.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETFILTERCHANGETIMEOUT](http://msdn.microsoft.com/library/windows/desktop/bb775359), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]  
  
##  <a name="setfocuseditem"></a>CHeaderCtrl::SetFocusedItem  
 Establece el foco a un elemento de encabezado especificado en el control de encabezado actual.  
  
```  
BOOL SetFocusedItem(int iItem);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iItem`|Índice de base cero de un elemento de encabezado.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [HDM_SETFOCUSEDITEM](http://msdn.microsoft.com/library/windows/desktop/bb775361) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_headerCtrl`, que se usa para tener acceso al control de encabezado actual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra la `SetFocusedItem` y `GetFocusedItem` métodos. En una sección anterior del código, se crea un control de encabezado con cinco columnas. Sin embargo, puede arrastrar un separador de columna para que la columna no es visible. En el ejemplo siguiente se establece y, a continuación, confirma el último encabezado de columna como el elemento de foco.  
  
 [!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]  
  
##  <a name="sethotdivider"></a>CHeaderCtrl::SetHotDivider  
 Arrastre el divisor entre elementos de encabezado para indicar un manual de cambios y eliminación de un elemento de encabezado.  
  
```  
int SetHotDivider(CPoint pt);  
int SetHotDivider(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 La posición del puntero. El control de encabezado resalta el divisor adecuado en función de la posición del puntero.  
  
 `nIndex`  
 El índice del divisor de resaltado.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del divisor de resaltado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETHOTDIVIDER](http://msdn.microsoft.com/library/windows/desktop/bb775363), tal y como se describe en el SDK de Windows. Se proporciona para admitir el elemento de encabezado, arrastrar y colocar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]  
  
##  <a name="setimagelist"></a>CHeaderCtrl:: SetImageList  
 Asigna una lista de imágenes a un control de encabezado.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `pImageList`  
 Un puntero a un `CImageList` objeto que contiene la lista de imágenes que se asignará al control de encabezado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CImageList](../../mfc/reference/cimagelist-class.md) objeto previamente asignado al control de encabezado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [HDM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775365), tal y como se describe en el SDK de Windows. La `CImageList` objeto al que señala el puntero devuelto es un objeto temporal y se elimina en el siguiente procesamiento de tiempo de inactividad.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CHeaderCtrl::GetImageList](#getimagelist).  
  
##  <a name="setitem"></a>CHeaderCtrl:: SetItem  
 Establece los atributos del elemento especificado en un control de encabezado.  
  
```  
BOOL SetItem(
    int nPos,  
    HDITEM* pHeaderItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Índice de base cero del elemento para su manipulación.  
  
 `pHeaderItem`  
 Puntero a un [DITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) estructura que contiene información sobre el nuevo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CHeaderCtrl:: GetItem](#getitem).  
  
##  <a name="setorderarray"></a>CHeaderCtrl:: SetOrderArray  
 Establece el orden de izquierda a derecha de los elementos en un control de encabezado.  
  
```  
BOOL SetOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `iCount`  
 El número de elementos de control de encabezado.  
  
 `piArray`  
 Un puntero a la dirección de un búfer que recibe los valores de índice de los elementos en el control de encabezado, en el orden en que aparecen de izquierda a derecha.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento de la macro de Win32 [HDM_SETORDERARRAY](http://msdn.microsoft.com/library/windows/desktop/bb775369), tal y como se describe en el SDK de Windows. Se proporciona para permitir la ordenación de elemento de encabezado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CHeaderCtrl:: GetOrderArray](#getorderarray).  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CTabCtrl (clase)](../../mfc/reference/ctabctrl-class.md)   
 [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)   
 [CImageList (clase)](../../mfc/reference/cimagelist-class.md)
