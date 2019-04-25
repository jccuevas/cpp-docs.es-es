---
title: CSplitterWnd (clase)
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
ms.openlocfilehash: 065735c13a3e763208142eb6bc989d3a496221f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323822"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd (clase)

Proporciona la funcionalidad de una ventana divisora, que es una ventana que contiene varios paneles.

## <a name="syntax"></a>Sintaxis

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Llamada a construir una `CSplitterWnd` objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|Ejecuta el comando panel siguiente o panel anterior.|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Comprueba si el comando panel siguiente o panel anterior es actualmente posible.|
|[CSplitterWnd::Create](#create)|Llamada a crear una ventana divisora dinámica y asociarlo a la `CSplitterWnd` objeto.|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crea un control de barra de desplazamiento compartido.|
|[CSplitterWnd::CreateStatic](#createstatic)|Llamada a crear una ventana divisora estática y asociarlo a la `CSplitterWnd` objeto.|
|[CSplitterWnd::CreateView](#createview)|Se llama para crear un panel en una ventana divisora.|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Elimina una columna de la ventana divisora.|
|[CSplitterWnd::DeleteRow](#deleterow)|Elimina una fila de la ventana divisora.|
|[CSplitterWnd::DeleteView](#deleteview)|Elimina una vista de la ventana divisora.|
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Realiza el teclado dividir el comando, normalmente "división de ventana".|
|[CSplitterWnd::DoScroll](#doscroll)|Realiza el desplazamiento sincronizada de ventanas divididas.|
|[CSplitterWnd::DoScrollBy](#doscrollby)|Desplaza ventanas divididas un número determinado de píxeles.|
|[CSplitterWnd::GetActivePane](#getactivepane)|Determina el panel activo del foco o la vista activa en el marco.|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Devuelve el número de columnas del panel actual.|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Devuelve información sobre la columna especificada.|
|[CSplitterWnd::GetPane](#getpane)|Devuelve el panel en la fila y columna especificadas.|
|[CSplitterWnd::GetRowCount](#getrowcount)|Devuelve el recuento de filas del panel actual.|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Devuelve información sobre la fila especificada.|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Devuelve el estilo de barra de desplazamiento compartido.|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Devuelve al elemento secundario Id. de la ventana del panel en la fila y columna especificadas.|
|[CSplitterWnd::IsChildPane](#ischildpane)|Llamada para determinar si la ventana actualmente es un panel secundario de esta ventana divisora.|
|[CSplitterWnd::IsTracking](#istracking)|Determina si actualmente se está moviendo barra divisora.|
|[CSplitterWnd::RecalcLayout](#recalclayout)|Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.|
|[CSplitterWnd::SetActivePane](#setactivepane)|Establece un panel será el activo en el marco.|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Llamada para establecer la información de la columna especificada.|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Llamada para establecer la información de la fila especificada.|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Especifica que el nuevo estilo de barra de desplazamiento de la ventana divisora compartido compatibilidad de la barra de desplazamiento.|
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indica que una ventana de marco se divide verticalmente.|
|[CSplitterWnd::SplitRow](#splitrow)|Indica que una ventana de marco se divide horizontalmente.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar la ventana divisora.|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Presenta una imagen de una ventana dividida.|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Presenta la imagen de una ventana dividida para ser el mismo tamaño y forma que la ventana de marco.|

## <a name="remarks"></a>Comentarios

Un panel suele ser un objeto específico de la aplicación que se deriva [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier [CWnd](../../mfc/reference/cwnd-class.md) objeto que tiene el identificador de ventana de secundario correspondiente.

Un `CSplitterWnd` objeto normalmente se incrusta en un elemento primario [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto. Crear un `CSplitterWnd` objeto mediante los siguientes pasos:

1. Incrustar un `CSplitterWnd` variable miembro en el marco primario.

2. Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.

3. Desde dentro de invalidado `OnCreateClient`, llame a la [crear](#create) o [CreateStatic](#createstatic) función miembro de `CSplitterWnd`.

Llame a la `Create` la función miembro para crear una ventana divisora dinámica. Una ventana divisora dinámica normalmente se usa para crear y desplazarse por un número de paneles individuales o vistas del mismo documento. El marco crea automáticamente un panel inicial para el separador; a continuación, el marco de trabajo crea, cambia el tamaño y desecha de paneles adicionales como el usuario funciona los controles de la ventana divisora.

Cuando se llama a `Create`, especifique un mínimo de la fila alto y ancho de columna que determinan cuándo los paneles son demasiado pequeños para mostrarse por completo. Después de llamar a `Create`, puede ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro.

Use también el `SetColumnInfo` y `SetRowInfo` las funciones miembro para establecer un ancho "ideal" para una columna y el alto de "ideal" para una fila. Cuando el marco de trabajo muestra una ventana divisora, primero se muestra el marco primario, a continuación, en la ventana divisora. Los paneles en las columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora, a continuación, presenta el marco de trabajo.

Todos los paneles en una ventana divisora dinámica deben ser de la misma clase. Aplicaciones conocidas que admiten ventanas divisoras dinámicas incluyen Microsoft Word y Microsoft Excel.

Use el `CreateStatic` función miembro para crear una ventana divisora estática. El usuario puede cambiar sólo el tamaño de los paneles en un divisor estático ventana, no su número o el orden.

Específicamente debe crear paneles de todas las divisora estática cuando se crea el divisora estática. Asegúrese de crear todos los paneles antes del marco primario `OnCreateClient` función miembro devuelve o si el marco de trabajo no se muestren correctamente la ventana.

El `CreateStatic` función miembro inicializa automáticamente un divisora estática con un ancho mínimo de la fila del alto de columna y de 0. Después de llamar a `Create`, ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro. También usar `SetColumnInfo` y `SetRowInfo` después de llamar a `CreateStatic` para indicar deseada dimensiones del panel ideal.

Los paneles individuales de un divisor estático a menudo pertenecen a diferentes clases. Para obtener ejemplos de las ventanas divisoras estáticas, consulte el editor de gráficos y el Administrador de archivos de Windows.

Una ventana divisora es compatible con las barras de desplazamiento especial (aparte de las barras de desplazamiento que pueden tener paneles). Estas barras de desplazamiento son elementos secundarios de la `CSplitterWnd` de objetos y se comparten con los paneles.

Cree estas barras de desplazamiento especial al crear la ventana divisora. Por ejemplo, un `CSplitterWnd` que contiene una fila, dos columnas y el estilo WS_VSCROLL mostrará una barra de desplazamiento vertical que se comparte entre los dos paneles. Cuando el usuario mueve la barra de desplazamiento, se envían mensajes WM_VSCROLL a ambos paneles. Cuando los paneles establece la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartido.

Para obtener más información sobre las ventanas divisoras, consulte [29 de nota técnica](../../mfc/tn029-splitter-windows.md).

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

##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext

Lo llama el marco de trabajo para realizar el comando panel siguiente o panel anterior.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica qué ventana se active. **TRUE** para anterior; **FALSE** para el siguiente.

### <a name="remarks"></a>Comentarios

Esta función miembro es un comando de alto nivel que está usando el [CView](../../mfc/reference/cview-class.md) clase delegar a los `CSplitterWnd` implementación.

##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext

Lo llama el marco de trabajo para comprobar si el comando panel siguiente o panel anterior es actualmente posible.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica qué ventana se active. **TRUE** para anterior; **FALSE** para el siguiente.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro es un comando de alto nivel que está usando el [CView](../../mfc/reference/cview-class.md) clase delegar a los `CSplitterWnd` implementación.

##  <a name="create"></a>  CSplitterWnd::Create

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
El número máximo de filas de la ventana divisora. Este valor no debe superar los 2.

*nMaxCols*<br/>
El número máximo de columnas en la ventana divisora. Este valor no debe superar los 2.

*sizeMin*<br/>
Especifica el tamaño mínimo en el que puede aparecer un panel.

*pContext*<br/>
Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. En la mayoría de los casos, esto puede ser el *pContext* pasa a la ventana de marco principal.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana del divisor.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Puede incrustar un `CSplitterWnd` en un elemento primario [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto mediante los pasos siguientes:

1. Incrustar un `CSplitterWnd` variable miembro en el marco primario.

1. Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.

1. Llame a la `Create` función miembro dentro de invalidado `OnCreateClient`.

Cuando se crea una ventana divisora desde dentro de un marco primario, pase el marco primario *pContext* parámetro a la ventana divisora. En caso contrario, este parámetro puede ser NULL.

Establece el ancho de columna y de alto mínimo inicial de la fila de una ventana divisora dinámica la *sizeMin* parámetro. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.

Para más información sobre las ventanas divisoras dinámicas, vea "Divisor Windows" en el artículo [varios tipos de documentos, vistas y marco Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` información general de clases.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl

Lo llama el marco para crear un control de barra de desplazamiento compartido.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana del divisor.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Invalidar `CreateScrollBarCtrl` para incluir controles adicionales al lado de una barra de desplazamiento. El comportamiento predeterminado es crear controles de barra de desplazamiento de Windows normales.

##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic

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
Número de filas. Este valor no debe superar los 16.

*nCols*<br/>
Número de columnas. Este valor no debe superar los 16.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana del divisor.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Un `CSplitterWnd` normalmente está incrustado en un elemento primario `CFrameWnd` o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto mediante los pasos siguientes:

1. Incrustar un `CSplitterWnd` variable miembro en el marco primario.

1. Invalidar el marco primario `OnCreateClient` función miembro.

1. Llame a la `CreateStatic` función miembro dentro de invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).

Una ventana divisora estática contiene un número fijo de paneles, a menudo a partir de clases diferentes.

Cuando se crea una ventana divisora estática, deben al mismo tiempo crear todos sus paneles. El [CreateView](#createview) normalmente se utiliza la función miembro para este propósito, pero puede crear otras clases nonview también.

El mínimo de la fila inicial alto y ancho de columna para una ventana divisora estática es 0. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.

Para agregar barras de desplazamiento a una ventana divisora estática, agregar los estilos WS_HSCROLL y WS_VSCROLL a *dwStyle*.

Vea "Divisor Windows" en el artículo [varios tipos de documentos, vistas y marco Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` información general de clases para obtener más información sobre las ventanas divisoras estáticas.

##  <a name="createview"></a>  CSplitterWnd::CreateView

Crea los paneles de una ventana divisora estática.

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica la fila de la ventana divisora donde desea colocar la nueva vista.

*col*<br/>
Especifica la columna de la ventana divisora donde desea colocar la nueva vista.

*pViewClass*<br/>
Especifica el [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nueva vista.

*sizeInit*<br/>
Especifica el tamaño inicial de la nueva vista.

*pContext*<br/>
Un puntero a un contexto de creación usado para crear la vista (normalmente el *pContext* pasado en el marco primario invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro en el que es la ventana divisora que se va a crear).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Todos los paneles de una ventana divisora estática deben crearse antes de que el marco de trabajo muestra el separador.

El marco de trabajo también llama a esta función miembro para crear paneles de nuevo cuando el usuario de una ventana divisora dinámica divide un panel, fila o columna.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd

Llamada a construir una `CSplitterWnd` objeto.

```
CSplitterWnd();
```

### <a name="remarks"></a>Comentarios

Construir un `CSplitterWnd` objeto en dos pasos. En primer lugar, llame al constructor, que crea el `CSplitterWnd` objeto y, a continuación, llame a la [crear](#create) función miembro, que crea la ventana divisora y lo adjunta a la `CSplitterWnd` objeto.

##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn

Elimina una columna de la ventana divisora.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parámetros

*colDelete*<br/>
Especifica la columna que se va a eliminar.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.

##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow

Elimina una fila de la ventana divisora.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parámetros

*rowDelete*<br/>
Especifica la fila que se va a eliminar.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.

##  <a name="deleteview"></a>  CSplitterWnd::DeleteView

Elimina una vista de la ventana divisora.

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica la fila de la ventana divisora en la que se va a eliminar la vista.

*col*<br/>
Especifica la columna de la ventana divisora en la que se va a eliminar la vista.

### <a name="remarks"></a>Comentarios

Si se elimina la vista activa, se activará la siguiente vista. La implementación predeterminada supone automáticamente la vista de eliminación en [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.

##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit

Realiza el teclado dividir el comando, normalmente "división de ventana".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro es un comando de alto nivel que está usando el [CView](../../mfc/reference/cview-class.md) clase delegar a los `CSplitterWnd` implementación.

##  <a name="doscroll"></a>  CSplitterWnd::DoScroll

Realiza el desplazamiento sincronizada de ventanas divididas.

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewFrom*<br/>
Un puntero a la vista de donde procede el mensaje de desplazamiento.

*nScrollCode*<br/>
Código de barras de desplazamiento que indica que el usuario desplaza en la solicitud. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produzca horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produzca verticalmente:

    - SB_BOTTOM se desplaza hacia abajo.

    - Una línea de desplaza SB_LINEDOWN hacia abajo.

    - Una línea de desplaza SB_LINEUP hacia arriba.

    - Una página de SB_PAGEDOWN se desplaza hacia abajo.

    - Una página de SB_PAGEUP se desplaza hacia arriba.

    - SB_TOP se desplaza hacia arriba.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria, y si la división de windows tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si *bDoScroll* es FALSE (es decir, si no hay ninguna ventana secundaria existe, o las vistas divididas no tienen ningún intervalo de desplazamiento), a continuación, el desplazamiento no se produce.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce desplazamiento sincronizado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para realizar un desplazamiento sincronizada de la división windows cuando la vista recibe un mensaje de desplazamiento. Invalidación para requerir una acción por parte del usuario antes de que se permite el desplazamiento sincronizado.

##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy

Desplaza ventanas divididas un número determinado de píxeles.

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pViewFrom*<br/>
Un puntero a la vista de donde procede el mensaje de desplazamiento.

*sizeScroll*<br/>
Número de píxeles que se puede desplazar horizontalmente y verticalmente.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria, y si la división de windows tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si *bDoScroll* es FALSE (es decir, si no hay ninguna ventana secundaria existe, o las vistas divididas no tienen ningún intervalo de desplazamiento), a continuación, el desplazamiento no se produce.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce desplazamiento sincronizado; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo en respuesta a un mensaje de desplazamiento, para realizar la sincronización de desplazamiento de la división de windows por la cantidad, en píxeles, indicado por *sizeScroll*. Los valores positivos indican el desplazamiento hacia abajo y a la derecha; los valores negativos indican el desplazamiento hacia arriba y hacia la izquierda.

Invalidar para requerir una acción del usuario antes de permitir el desplazamiento.

##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane

Determina el panel activo del foco o la vista activa en el marco.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parámetros

*pRow*<br/>
Un puntero a un **int** para recuperar el número de fila del panel activo.

*pCol*<br/>
Un puntero a un **int** para recuperar el número de columna del panel activo.

### <a name="return-value"></a>Valor devuelto

Puntero en el panel activo. NULL si no existe ningún panel activo.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para determinar el panel activo en una ventana divisora. Invalidar para requerir una acción del usuario antes de entrar en el panel activo.

##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount

Devuelve el número de columnas del panel actual.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de columnas en el divisor. Para un divisoras estáticas, también será el número máximo de columnas.

##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo

Devuelve información sobre la columna especificada.

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>Parámetros

*col*<br/>
Especifica una columna.

*cxCur*<br/>
Una referencia a un **int** debe establecerse en el ancho actual de la columna.

*cxMin*<br/>
Una referencia a un **int** debe establecerse el ancho mínimo actual de la columna.

##  <a name="getpane"></a>  CSplitterWnd::GetPane

Devuelve el panel en la fila y columna especificadas.

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica una fila.

*col*<br/>
Especifica una columna.

### <a name="return-value"></a>Valor devuelto

Devuelve el panel en la fila y columna especificadas. El panel devuelto es normalmente un [CView](../../mfc/reference/cview-class.md)-clase derivada.

##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount

Devuelve el recuento de filas del panel actual.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de filas en la ventana divisora. Para una ventana divisora estática, también será el número máximo de filas.

##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo

Devuelve información sobre la fila especificada.

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica una fila.

*cyCur*<br/>
Referencia a **int** debe establecerse en el alto actual de la fila en píxeles.

*cyMin*<br/>
Referencia a **int** debe establecerse para el alto mínimo actual de la fila en píxeles.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para obtener información acerca de la fila especificada. El *cyCur* parámetro se rellena con el alto actual de la fila especificada, y *cyMin* se rellena con el alto mínimo de la fila.

##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle

Devuelve el estilo de barra de desplazamiento compartido para la ventana divisora.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Una o varias de las siguientes ventanas de estilo marcadores, si se realiza correctamente:

    - WS_HSCROLL si que actualmente administra el divisor comparte las barras de desplazamiento horizontal.

    - WS_VSCROLL si que actualmente administra el divisor comparte las barras de desplazamiento vertical.

Si es cero, la ventana divisora no administra actualmente todas las barras de desplazamiento compartido.

##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol

Obtiene al elemento secundario Id. de ventana para el panel situado en la fila y columna especificadas.

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica la fila de la ventana divisora.

*col*<br/>
Especifica la columna de la ventana divisora.

### <a name="return-value"></a>Valor devuelto

El identificador de ventana secundaria para el panel.

### <a name="remarks"></a>Comentarios

Esta función miembro se usa para crear nonviews como paneles y se puede llamar antes de que exista el panel.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane

Determina si *conquistado* actualmente es un panel secundario de esta ventana divisora.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que va a probarse.

*pRow*<br/>
Un puntero a un **int** en el que se va a almacenar el número de fila.

*pCol*<br/>
Un puntero a un **int** en el que se va a almacenar un número de columna.

### <a name="return-value"></a>Valor devuelto

Si es distinto de cero, *conquistado* actualmente es un panel secundario de esta ventana divisora, y *pRow* y *pCol* se rellena con la posición del panel en la ventana divisora. Si *conquistado* no es un panel secundario de esta ventana divisora, se devuelve 0.

### <a name="remarks"></a>Comentarios

En las versiones de Visual C++ anteriores a 6.0, esta función se define como

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Esta versión ahora está obsoleta y no debe usarse.

##  <a name="istracking"></a>  CSplitterWnd::IsTracking

Llame a esta función miembro para determinar si la barra de división en la ventana se está moviendo actualmente.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si una operación de divisor está en curso; en caso contrario, es 0.

##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter

Presenta una imagen de una ventana dividida.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Un puntero al contexto de dispositivo en el que se va a dibujar. Si *pDC* es NULL, a continuación, [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) es llamado por el marco de trabajo y no división se dibuja la ventana.

*nType*<br/>
Un valor de la `enum ESplitType`, que puede ser uno de los siguientes:

    - `splitBox` El cuadro de arrastre del divisor.

    - `splitBar` La barra que aparece entre las ventanas de la división de dos.

    - `splitIntersection` La intersección de las ventanas de división. Este elemento no se llamará cuando se ejecuta en Windows 95 ó 98.

    - `splitBorder` Los bordes de ventana dividida.

*rect*<br/>
Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el tamaño y la forma de la división de windows.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para dibujar y especifique las características exactas de una ventana divisora. Invalidar `OnDrawSplitter` para la personalización avanzada de las imágenes para los distintos componentes gráficos de una ventana divisora. Las imágenes de forma predeterminada es similar al divisor en Microsoft Works para Windows o Microsoft Windows 95/98, en el sentido de las intersecciones de las barras de división se fusionan.

Para más información sobre las ventanas divisoras dinámicas, vea "Divisor Windows" en el artículo [varios tipos de documentos, vistas y marco Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` información general de clases.

##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker

Presenta la imagen de una ventana dividida para ser el mismo tamaño y forma que la ventana de marco.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*rect*<br/>
Hacer referencia a un `CRect` objeto que especifica el rectángulo de seguimiento.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo durante el cambio de tamaño de los separadores. Invalidar `OnInvertTracker` para la personalización avanzada de las imágenes de la ventana divisora. Las imágenes de forma predeterminada es similar al divisor en Microsoft Works para Windows o Microsoft Windows 95/98, en el sentido de las intersecciones de las barras de división se fusionan.

Para más información sobre las ventanas divisoras dinámicas, vea "Divisor Windows" en el artículo [varios tipos de documentos, vistas y marco Windows](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` información general de clases.

##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout

Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para volver correctamente a la ventana divisora después de ajustar los tamaños de fila y columna con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro. Si cambia los tamaños de fila y columna como parte del proceso de creación antes de la ventana divisora está visible, no es necesario llamar a esta función miembro.

El marco de trabajo llama a esta función miembro siempre que el usuario cambia el tamaño de la ventana divisora o mueve una división.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CSplitterWnd::SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane

Establece un panel será el activo en el marco.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Si *conquistado* es NULL, que especifica la fila en el panel que estará activo.

*col*<br/>
Si *conquistado* es NULL, que especifica la columna en el panel que estará activo.

*pWnd*<br/>
Puntero a un objeto `CWnd` . Si es NULL, el panel especificado por *fila* y *col* está establecido en activo. Si no es NULL, especifica el panel que se establece en activo.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo para establecer un panel como activo cuando el usuario cambia el foco a un panel dentro de la ventana de marco. Puede llamar explícitamente a `SetActivePane` para cambiar el foco a la vista especificada.

Especifique panel proporcionando la fila y columna, **o** proporcionando *conquistado*.

##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo

Llamada para establecer la información de la columna especificada.

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>Parámetros

*col*<br/>
Especifica una columna de la ventana divisora.

*cxIdeal*<br/>
Especifica un ancho ideal para la columna de la ventana de divisor en píxeles.

*cxMin*<br/>
Especifica un ancho mínimo de la columna de la ventana de divisor en píxeles.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para establecer un ancho ideal para una columna y el nuevo ancho mínimo. El valor mínimo de columna determina si la columna se demasiado pequeña para mostrarse por completo.

Cuando el marco de trabajo muestra la ventana divisora, presenta los paneles en las columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo

Llamada para establecer la información de la fila especificada.

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Especifica una fila de la ventana divisora.

*cyIdeal*<br/>
Especifica un alto ideal de la fila de la ventana de divisor en píxeles.

*cyMin*<br/>
Especifica una altura mínima para la fila de la ventana de divisor en píxeles.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro para establecer un nuevo alto mínimo y alto ideal para una fila. El valor mínimo de fila determina cuando la fila será demasiado pequeña para mostrarse por completo.

Cuando el marco de trabajo muestra la ventana divisora, presenta los paneles en las columnas y filas según sus dimensiones ideales, trabajando desde la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle

Especifica que el nuevo estilo de desplazamiento de la ventana divisora compartido compatibilidad de la barra de desplazamiento.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
El nuevo estilo de desplazamiento de la ventana divisora compartidas de compatibilidad de la barra de desplazamiento, que puede ser uno de los siguientes valores:

- WS_HSCROLL Create/mostrar horizontal compartida barras de desplazamiento.

- WS_VSCROLL crear/mostrar vertical compartido barras de desplazamiento.

### <a name="remarks"></a>Comentarios

Una vez que se crea una barra de desplazamiento no se destruirá aunque `SetScrollStyle` se llama sin ese estilo; en su lugar, se ocultan las barras de desplazamiento. Esto permite que las barras de desplazamiento conservar su estado, aunque están ocultos. Después de llamar a `SetScrollStyle` es necesario llamar a [RecalcLayout](#recalclayout) para todos los cambios surtan efecto.

##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn

Indica que una ventana de marco se divide verticalmente.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parámetros

*cxBefore*<br/>
La posición, en píxeles, antes de que se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama cuando se crea una ventana divisora vertical. `SplitColumn` indica la ubicación predeterminada donde se produce la división.

`SplitColumn` se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.

##  <a name="splitrow"></a>  CSplitterWnd::SplitRow

Indica que una ventana de marco se divide horizontalmente.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parámetros

*cyBefore*<br/>
La posición, en píxeles, antes de que se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama cuando se crea una ventana divisora horizontal. `SplitRow` indica la ubicación predeterminada donde se produce la división.

`SplitRow` se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.

##  <a name="ondraw"></a>  CSplitterWnd::OnDraw

Lo llama el marco de trabajo para dibujar la ventana divisora.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Ejemplo VIEWEX de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
