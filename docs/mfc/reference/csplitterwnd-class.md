---
title: Clase CSplitterWnd
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: a872854af1695b8b2b347b21d73165d259b3a986
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753064"
---
# <a name="csplitterwnd-class"></a>Clase CSplitterWnd

Proporciona la funcionalidad de una ventana divisora, que es una ventana que contiene varios paneles.

## <a name="syntax"></a>Sintaxis

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Llame para `CSplitterWnd` construir un objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Realiza el comando Panel siguiente o Panel anterior.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Comprueba si el comando Panel siguiente o Panel anterior es actualmente posible.|
|[CSplitterWnd::Crear](#create)|Llame para crear una ventana divisora `CSplitterWnd` dinámica y adjuntarla al objeto.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crea un control de barra de desplazamiento compartido.|
|[CSplitterWnd::CreateStatic](#createstatic)|Llame para crear una ventana divisora `CSplitterWnd` estática y adjuntarla al objeto.|
|[CSplitterWnd::CreateView](#createview)|Llame para crear un panel en una ventana divisora.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Elimina una columna de la ventana divisora.|
|[CSplitterWnd::DeleteRow](#deleterow)|Elimina una fila de la ventana divisora.|
|[CSplitterWnd::DeleteView](#deleteview)|Elimina una vista de la ventana divisora.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Realiza el comando de división de teclado, normalmente "Window Split."|
|[CSplitterWnd::DoScroll](#doscroll)|Realiza el desplazamiento sincronizado de ventanas divididas.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Los desplazamientos dividen las ventanas por un número determinado de píxeles.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Determina el panel activo desde el foco o la vista activa en el marco.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Devuelve el recuento de columnas del panel actual.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Devuelve información sobre la columna especificada.|
|[CSplitterWnd::GetPane](#getpane)|Devuelve el panel en la fila y columna especificadas.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Devuelve el recuento de filas del panel actual.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Devuelve información sobre la fila especificada.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Devuelve el estilo de barra de desplazamiento compartida.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Devuelve el identificador de ventana secundaria del panel en la fila y columna especificadas.|
|[CsplitterWnd::IsChildPane](#ischildpane)|Llame para determinar si la ventana es actualmente un panel secundario de esta ventana divisora.|
|[CSplitterWnd::IsTracking](#istracking)|Determina si la barra divisora se está moviendo actualmente.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Llame para volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Establece un panel para que sea el activo en el marco.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Llame para establecer la información de columna especificada.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Llame para establecer la información de fila especificada.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Especifica el nuevo estilo de barra de desplazamiento para la compatibilidad de la barra de desplazamiento compartida de la ventana divisora.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indica dónde se divide verticalmente una ventana de marco.|
|[CSplitterWnd::SplitRow](#splitrow)|Indica dónde se divide horizontalmente una ventana de marco.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CsplitterWnd::OnDraw](#ondraw)|Llamado por el marco de trabajo para dibujar la ventana divisora.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Representa una imagen de una ventana dividida.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Representa la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.|

## <a name="remarks"></a>Observaciones

Un panel suele ser un objeto específico de la aplicación derivado de [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier objeto [CWnd](../../mfc/reference/cwnd-class.md) que tenga el identificador de ventana secundario adecuado.

Normalmente, `CSplitterWnd` un objeto se incrusta en un objeto [Primario CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd.](../../mfc/reference/cmdichildwnd-class.md) Cree `CSplitterWnd` un objeto siguiendo estos pasos:

1. Incruste una `CSplitterWnd` variable miembro en el marco primario.

2. Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.

3. Desde dentro de `OnCreateClient`la invalidada , llame `CSplitterWnd`a la [Create](#create) o [CreateStatic](#createstatic) función miembro de .

Llame `Create` a la función miembro para crear una ventana divisora dinámica. Una ventana divisora dinámica normalmente se utiliza para crear y desplazar un número de paneles individuales, o vistas, del mismo documento. El marco de trabajo crea automáticamente un panel inicial para el divisor; a continuación, el marco de trabajo crea, cambia el tamaño y elimina paneles adicionales a medida que el usuario opera los controles de la ventana divisora.

Cuando se `Create`llama a , se especifica un alto de fila mínimo y un ancho de columna que determinan cuándo los paneles son demasiado pequeños para mostrarse completamente. Después `Create`de llamar , puede ajustar estos mínimos llamando a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro.

También utilice `SetColumnInfo` `SetRowInfo` las funciones miembro y para establecer un ancho "ideal" para una columna y un alto "ideal" para una fila. Cuando el marco de trabajo muestra una ventana divisora, primero muestra el marco primario y, a continuación, la ventana divisora. A continuación, el marco de trabajo establece los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

Todos los paneles de una ventana divisora dinámica deben ser de la misma clase. Las aplicaciones conocidas que admiten ventanas divisoras dinámicas incluyen Microsoft Word y Microsoft Excel.

Utilice `CreateStatic` la función miembro para crear una ventana divisora estática. El usuario puede cambiar solo el tamaño de los paneles en una ventana divisora estática, no su número o orden.

Debe crear específicamente todos los paneles del divisor estático al crear el divisor estático. Asegúrese de crear todos los paneles antes `OnCreateClient` de que se devuelva la función miembro del marco primario o el marco de trabajo no mostrará la ventana correctamente.

La `CreateStatic` función miembro inicializa automáticamente un divisor estático con un alto de fila mínimo y un ancho de columna de 0. Después `Create`de llamar , ajuste estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro. También `SetColumnInfo` utilice `SetRowInfo` y `CreateStatic` después de llamar para indicar las dimensiones de panel ideales deseadas.

Los paneles individuales de un divisor estático a menudo pertenecen a clases diferentes. Para ver ejemplos de ventanas divisoras estáticas, consulte el editor de gráficos y el Administrador de archivos de Windows.

Una ventana divisora admite barras de desplazamiento especiales (aparte de las barras de desplazamiento que pueden tener los paneles). Estas barras de desplazamiento `CSplitterWnd` son elementos secundarios del objeto y se comparten con los paneles.

Estas barras de desplazamiento especiales se crean al crear la ventana divisora. Por ejemplo, `CSplitterWnd` un que tiene una fila, dos columnas y el estilo WS_VSCROLL mostrará una barra de desplazamiento vertical compartida por los dos paneles. Cuando el usuario mueve la barra de desplazamiento, WM_VSCROLL los mensajes se envían a ambos paneles. Cuando los paneles establecen la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartida.

Para obtener más información sobre las ventanas divisoras, véase la [Nota técnica 29](../../mfc/tn029-splitter-windows.md).

Para obtener más información sobre cómo crear ventanas divisoras dinámicas, consulte:

- Ejemplo de MFC [Scribble](../../overview/visual-cpp-samples.md)

- Ejemplo de MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::ActivateNext

Llamado por el marco de trabajo para realizar el comando Panel siguiente o Panel anterior.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica qué ventana se va a activar. **TRUE** para anterior; **FALSE** para el siguiente.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que `CSplitterWnd` utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación.

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNext

Llamado por el marco de trabajo para comprobar si el comando Panel siguiente o Panel anterior es actualmente posible.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica qué ventana se va a activar. **TRUE** para anterior; **FALSE** para el siguiente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que `CSplitterWnd` utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación.

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd::Crear

Para crear una ventana divisora dinámica, llame a la `Create` función miembro.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
La ventana de marco principal de la ventana divisora.

*nMaxRows*<br/>
El número máximo de filas en la ventana divisora. Este valor no debe superar 2.

*nMaxCols*<br/>
El número máximo de columnas en la ventana divisora. Este valor no debe superar 2.

*sizeMin*<br/>
Especifica el tamaño mínimo en el que se puede mostrar un panel.

*pContext*<br/>
Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. En la mayoría de los casos, puede ser el *pContext* pasado a la ventana de marco primario.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El ID se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Puede incrustar `CSplitterWnd` un objeto [primario CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) siguiendo estos pasos:

1. Incruste una `CSplitterWnd` variable miembro en el marco primario.

1. Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.

1. Llame `Create` a la función `OnCreateClient`miembro desde dentro de la invalidada .

Cuando cree una ventana divisora desde dentro de un marco primario, pase el parámetro *pContext* del marco primario a la ventana divisora. De lo contrario, este parámetro puede ser NULL.

La altura de fila mínima inicial y el ancho de columna de una ventana divisora dinámica se establecen mediante el parámetro *sizeMin.* Estos mínimos, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.

Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas de splitter" `CSplitterWnd` en el artículo Varios tipos de [documento, vistas y ventanas](../../mfc/multiple-document-types-views-and-frame-windows.md)de marco , Nota técnica [29](../../mfc/tn029-splitter-windows.md)y información general sobre la clase.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl

Llamado por el marco de trabajo para crear un control de barra de desplazamiento compartido.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El ID se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Reemplazar `CreateScrollBarCtrl` para incluir controles adicionales junto a una barra de desplazamiento. El comportamiento predeterminado es crear controles normales de la barra de desplazamiento de Windows.

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd::CreateStatic

Para crear una ventana divisora estática, llame a la `CreateStatic` función miembro.

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
La ventana de marco principal de la ventana divisora.

*nRows*<br/>
El número de filas. Este valor no debe superar 16.

*nCols*<br/>
El número de columnas. Este valor no debe superar 16.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El ID se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

A `CSplitterWnd` se incrusta normalmente `CFrameWnd` en un objeto primario o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) siguiendo estos pasos:

1. Incruste una `CSplitterWnd` variable miembro en el marco primario.

1. Invalide la función miembro del `OnCreateClient` marco primario.

1. Llame `CreateStatic` a la función miembro desde dentro de la [invalidada CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Una ventana divisora estática contiene un número fijo de paneles, a menudo de diferentes clases.

Al crear una ventana divisora estática, debe crear al mismo tiempo todos sus paneles. El [CreateView](#createview) función miembro se utiliza normalmente para este propósito, pero también puede crear otras clases que no son de vista.

La altura mínima inicial de la fila y el ancho de columna para una ventana divisora estática es 0. Estos mínimos, que determinan cuándo un panel es demasiado pequeño para mostrarse en su totalidad, se puede cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.

Para agregar barras de desplazamiento a una ventana divisora estática, agregue los estilos WS_HSCROLL y WS_VSCROLL a *dwStyle*.

Consulte "Ventanas de splitter" en el artículo Varios tipos de [documento, vistas y ventanas](../../mfc/multiple-document-types-views-and-frame-windows.md)de marco , [Nota técnica 29](../../mfc/tn029-splitter-windows.md)y información general de la `CSplitterWnd` clase para obtener más información sobre las ventanas divisoras estáticas.

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd::CreateView

Crea los paneles para una ventana divisora estática.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica la fila de la ventana divisora en la que se colocará la nueva vista.

*col*<br/>
Especifica la columna de ventana divisora en la que se va a colocar la nueva vista.

*pViewClass*<br/>
Especifica el [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nueva vista.

*sizeInit*<br/>
Especifica el tamaño inicial de la nueva vista.

*pContext*<br/>
Puntero a un contexto de creación utilizado para crear la vista (normalmente el *pContext* pasado a la función miembro [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) invalidada del marco primario en la que se crea la ventana divisora).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Todos los paneles de una ventana divisora estática deben crearse antes de que el marco de trabajo muestre el divisor.

El marco de trabajo también llama a esta función miembro para crear nuevos paneles cuando el usuario de una ventana divisora dinámica divide un panel, fila o columna.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd

Llame para `CSplitterWnd` construir un objeto.

```
CSplitterWnd();
```

### <a name="remarks"></a>Observaciones

Construir `CSplitterWnd` un objeto en dos pasos. En primer lugar, llame `CSplitterWnd` al constructor, que crea el objeto y, a continuación, `CSplitterWnd` llame a la [Create](#create) función miembro, que crea la ventana divisora y lo adjunta al objeto.

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteColumn

Elimina una columna de la ventana divisora.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parámetros

*colDelete*<br/>
Especifica la columna que se va a eliminar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView,](#createview)para implementar divisores dinámicos más avanzados.

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow

Elimina una fila de la ventana divisora.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parámetros

*rowDelete*<br/>
Especifica la fila que se va a eliminar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView,](#createview)para implementar divisores dinámicos más avanzados.

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DeleteView

Elimina una vista de la ventana divisora.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica la fila de la ventana divisora en la que se va a eliminar la vista.

*col*<br/>
Especifica la columna de ventana divisora en la que se va a eliminar la vista.

### <a name="remarks"></a>Observaciones

Si se elimina la vista activa, la siguiente vista se activará. La implementación predeterminada supone que la vista se eliminará automáticamente en [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView,](#createview)para implementar divisores dinámicos más avanzados.

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit

Realiza el comando de división de teclado, normalmente "Window Split."

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que `CSplitterWnd` utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación.

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll

Realiza el desplazamiento sincronizado de ventanas divididas.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewFrom*<br/>
Puntero a la vista desde la que se origina el mensaje de desplazamiento.

*nScrollCode*<br/>
Un código de barra de desplazamiento que indica la solicitud de desplazamiento del usuario. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produce horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produce verticalmente:

- SB_BOTTOM Se desplaza hacia abajo.

- SB_LINEDOWN Desplaza una línea hacia abajo.

- SB_LINEUP Desplaza una línea.

- SB_PAGEDOWN Desplaza una página hacia abajo.

- SB_PAGEUP Desplaza una página hacia arriba.

- SB_TOP Se desplaza a la parte superior.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria y si las ventanas divididas tienen un intervalo de desplazamiento), puede tener lugar la acción de desplazamiento especificada; si *bDoScroll* es FALSE (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen ningún intervalo de desplazamiento), no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce el desplazamiento sincronizado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para realizar el desplazamiento sincronizado de ventanas divididas cuando la vista recibe un mensaje de desplazamiento. Invalidación para requerir una acción del usuario antes de que se permita el desplazamiento sincronizado.

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy

Los desplazamientos dividen las ventanas por un número determinado de píxeles.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewFrom*<br/>
Puntero a la vista desde la que se origina el mensaje de desplazamiento.

*sizeScroll*<br/>
Número de píxeles que se desplazarán horizontal y verticalmente.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria y si las ventanas divididas tienen un intervalo de desplazamiento), puede tener lugar la acción de desplazamiento especificada; si *bDoScroll* es FALSE (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen ningún intervalo de desplazamiento), no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce el desplazamiento sincronizado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro en respuesta a un mensaje de desplazamiento para realizar el desplazamiento sincronizado de las ventanas divididas por la cantidad, en píxeles, indicada por *sizeScroll*. Los valores positivos indican que se desplaza hacia abajo y hacia la derecha; los valores negativos indican desplazarse hacia arriba y hacia la izquierda.

Reemplazar para requerir una acción del usuario antes de permitir el desplazamiento.

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane

Determina el panel activo desde el foco o la vista activa en el marco.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parámetros

*pRow*<br/>
Puntero a un **int** para recuperar el número de fila del panel activo.

*pCol*<br/>
Puntero a un **int** para recuperar el número de columna del panel activo.

### <a name="return-value"></a>Valor devuelto

Puntero al panel activo. NULL si no existe ningún panel activo.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para determinar el panel activo en una ventana divisora. Reemplazar para requerir una acción del usuario antes de obtener el panel activo.

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount

Devuelve el recuento de columnas del panel actual.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de columnas en el divisor. Para un divisor estático, este también será el número máximo de columnas.

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo

Devuelve información sobre la columna especificada.

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parámetros

*col*<br/>
Especifica una columna.

*cxCur*<br/>
Una referencia a un **int** que se establecerá en el ancho actual de la columna.

*cxMin*<br/>
Una referencia a un **int** que se establecerá en el ancho mínimo actual de la columna.

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane

Devuelve el panel en la fila y columna especificadas.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica una fila.

*col*<br/>
Especifica una columna.

### <a name="return-value"></a>Valor devuelto

Devuelve el panel en la fila y columna especificadas. El panel devuelto suele ser una clase derivada de [CView.](../../mfc/reference/cview-class.md)

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount

Devuelve el recuento de filas del panel actual.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de filas en la ventana divisora. Para una ventana divisora estática, este también será el número máximo de filas.

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo

Devuelve información sobre la fila especificada.

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica una fila.

*cyCur*<br/>
Referencia a **int** que se establecerá en la altura actual de la fila en píxeles.

*cyMin*<br/>
Referencia a **int** que se establecerá en la altura mínima actual de la fila en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para obtener información sobre la fila especificada. El parámetro *cyCur* se rellena con la altura actual de la fila especificada y *cyMin* se rellena con la altura mínima de la fila.

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle

Devuelve el estilo de barra de desplazamiento compartida para la ventana divisora.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Uno o varios de los siguientes indicadores de estilo de windows, si se realiza correctamente:

- WS_HSCROLL Si el divisor administra actualmente las barras de desplazamiento horizontalcompartidas.

- WS_VSCROLL Si el divisor administra actualmente las barras de desplazamiento verticales compartidas.

Si es cero, la ventana divisora no administra actualmente ninguna barra de desplazamiento compartida.

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol

Obtiene el identificador de ventana secundaria para el panel en la fila y columna especificadas.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica la fila de la ventana divisora.

*col*<br/>
Especifica la columna de la ventana divisora.

### <a name="return-value"></a>Valor devuelto

El identificador de ventana secundaria para el panel.

### <a name="remarks"></a>Observaciones

Esta función miembro se utiliza para crear no vistas como paneles y se puede llamar antes de que exista el panel.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CsplitterWnd::IsChildPane

Determina si *pWnd* es actualmente un panel secundario de esta ventana divisora.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Puntero a un [cWnd](../../mfc/reference/cwnd-class.md) objeto que se va a probar.

*pRow*<br/>
Puntero a un **int** en el que se almacenará el número de fila.

*pCol*<br/>
Puntero a un **int** en el que se va a almacenar un número de columna.

### <a name="return-value"></a>Valor devuelto

Si es distinto de cero, *pWnd* es actualmente un panel secundario de esta ventana divisora y *pRow* y *pCol* se rellenan con la posición del panel en la ventana divisora. Si *pWnd* no es un panel secundario de esta ventana divisora, se devuelve 0.

### <a name="remarks"></a>Observaciones

En las versiones de Visual C++ anteriores a 6.0, esta función se definió como

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Esta versión ya está obsoleta y no debe utilizarse.

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::IsTracking

Llame a esta función miembro para determinar si la barra divisora en la ventana se está moviendo actualmente.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una operación de divisor está en curso; de lo contrario 0.

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter

Representa una imagen de una ventana dividida.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero al contexto del dispositivo en el que se desea dibujar. Si *pDC* es NULL, el marco de trabajo llama a [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) y no se dibuja ninguna ventana de división.

*nType*<br/>
Un valor `enum ESplitType`de la , que puede ser uno de los siguientes:

- `splitBox`El cuadro de arrastre del divisor.

- `splitBar`La barra que aparece entre las dos ventanas divididas.

- `splitIntersection`La intersección de las ventanas divididas. No se llamará a este elemento cuando se ejecute en Windows 95/98.

- `splitBorder`Los bordes de la ventana dividida.

*Rect*<br/>
Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el tamaño y la forma de las ventanas divididas.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para dibujar y especificar las características exactas de una ventana divisora. Reemplazar `OnDrawSplitter` para la personalización avanzada de las imágenes para los diversos componentes gráficos de una ventana divisora. Las imágenes predeterminadas son similares al divisor de Microsoft Works para Windows o Microsoft Windows 95/98, en que las intersecciones de las barras divisoras se mezclan.

Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas de splitter" `CSplitterWnd` en el artículo Varios tipos de [documento, vistas y ventanas](../../mfc/multiple-document-types-views-and-frame-windows.md)de marco , Nota técnica [29](../../mfc/tn029-splitter-windows.md)y información general sobre la clase.

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker

Representa la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Referencia a `CRect` un objeto que especifica el rectángulo de seguimiento.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro durante el cambio de tamaño de los divisores. Invalide `OnInvertTracker` para la personalización avanzada de las imágenes de la ventana divisora. Las imágenes predeterminadas son similares al divisor de Microsoft Works para Windows o Microsoft Windows 95/98, en que las intersecciones de las barras divisoras se mezclan.

Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas de splitter" `CSplitterWnd` en el artículo Varios tipos de [documento, vistas y ventanas](../../mfc/multiple-document-types-views-and-frame-windows.md)de marco , Nota técnica [29](../../mfc/tn029-splitter-windows.md)y información general sobre la clase.

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::RecalcLayout

Llame para volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para volver a mostrar correctamente la ventana divisora después de haber ajustado los tamaños de fila y columna con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro. Si cambia los tamaños de fila y columna como parte del proceso de creación antes de que la ventana divisora sea visible, no es necesario llamar a esta función miembro.

El marco de trabajo llama a esta función miembro cada vez que el usuario cambia el tamaño de la ventana divisora o mueve una división.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CSplitterWnd::SetColumnInfo](#setcolumninfo).

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane

Establece un panel para que sea el activo en el marco.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Si *pWnd* es NULL, especifica la fila en el panel que estará activa.

*col*<br/>
Si *pWnd* es NULL, especifica la columna en el panel que estará activa.

*pWnd*<br/>
Puntero a un objeto `CWnd` . Si NULL, el panel especificado por *row* y *col* se establece activo. Si no es NULL, especifica el panel que se establece activo.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para establecer un panel como activo cuando el usuario cambia el foco a un panel dentro de la ventana de marco. Puede llamar `SetActivePane` explícitamente para cambiar el foco a la vista especificada.

Especifique el panel proporcionando fila y **columna, o** proporcionando *pWnd*.

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo

Llame para establecer la información de columna especificada.

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parámetros

*col*<br/>
Especifica una columna de ventana divisora.

*cxIdeal*<br/>
Especifica un ancho ideal para la columna de la ventana divisora en píxeles.

*cxMin*<br/>
Especifica un ancho mínimo para la columna de la ventana divisora en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para establecer un nuevo ancho mínimo y ancho ideal para una columna. El valor mínimo de la columna determina cuándo la columna será demasiado pequeña para mostrarse completamente.

Cuando el marco de trabajo muestra la ventana divisora, establece los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo

Llame para establecer la información de fila especificada.

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parámetros

*Fila*<br/>
Especifica una fila de ventana divisora.

*cyIdeal*<br/>
Especifica una altura ideal para la fila de la ventana divisora en píxeles.

*cyMin*<br/>
Especifica una altura mínima para la fila de la ventana divisora en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para establecer una nueva altura mínima y altura ideal para una fila. El valor mínimo de fila determina cuándo la fila será demasiado pequeña para mostrarse completamente.

Cuando el marco de trabajo muestra la ventana divisora, establece los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle

Especifica el nuevo estilo de desplazamiento para la compatibilidad con la barra de desplazamiento compartida de la ventana divisora.

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
El nuevo estilo de desplazamiento para la compatibilidad con la barra de desplazamiento compartida de la ventana divisora, que puede ser uno de los siguientes valores:

- WS_HSCROLL Crear/mostrar barras de desplazamiento compartidas horizontales.

- WS_VSCROLL Crear/mostrar barras de desplazamiento compartidas verticales.

### <a name="remarks"></a>Observaciones

Una vez que se crea una barra `SetScrollStyle` de desplazamiento, no se destruirá aunque se llame sin ese estilo; en su lugar, esas barras de desplazamiento están ocultas. Esto permite que las barras de desplazamiento conserven su estado aunque estén ocultas. Después `SetScrollStyle` de llamar es necesario llamar a [RecalcLayout](#recalclayout) para que todos los cambios surtan efecto.

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn

Indica dónde se divide verticalmente una ventana de marco.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parámetros

*cxAntes*<br/>
La posición, en píxeles, antes de la cual se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro cuando se crea una ventana divisora vertical. `SplitColumn`indica la ubicación predeterminada donde se produce la división.

`SplitColumn`el marco de trabajo llama para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView,](#createview)para implementar divisores dinámicos más avanzados.

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow

Indica dónde se divide horizontalmente una ventana de marco.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parámetros

*cyBefore*<br/>
La posición, en píxeles, antes de la cual se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro cuando se crea una ventana divisora horizontal. `SplitRow`indica la ubicación predeterminada donde se produce la división.

`SplitRow`el marco de trabajo llama para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView,](#createview)para implementar divisores dinámicos más avanzados.

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CsplitterWnd::OnDraw

Llamado por el marco de trabajo para dibujar la ventana divisora.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Ejemplo de MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
