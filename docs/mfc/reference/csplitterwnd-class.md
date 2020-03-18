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
ms.openlocfilehash: bee6deed3052d6cc923e432e97ad9a7904060cb6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447438"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd (clase)

Proporciona la funcionalidad de una ventana divisora, que es una ventana que contiene varios paneles.

## <a name="syntax"></a>Sintaxis

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWnd:: CSplitterWnd](#csplitterwnd)|Llame a para construir un objeto de `CSplitterWnd`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWnd:: ActivateNext](#activatenext)|Ejecuta el comando panel siguiente o panel anterior.|
|[CSplitterWnd:: CanActivateNext](#canactivatenext)|Comprueba si el comando panel siguiente o panel anterior es posible actualmente.|
|[CSplitterWnd:: Create](#create)|Llame a para crear una ventana divisora dinámica y adjuntarla al objeto `CSplitterWnd`.|
|[CSplitterWnd:: CreateScrollBarCtrl](#createscrollbarctrl)|Crea un control de barra de desplazamiento compartido.|
|[CSplitterWnd:: CreateStatic](#createstatic)|Llame a para crear una ventana de divisor estática y adjuntarla al objeto `CSplitterWnd`.|
|[CSplitterWnd:: CreateView](#createview)|Llame a para crear un panel en una ventana divisora.|
|[CSplitterWnd::D eleteColumn](#deletecolumn)|Elimina una columna de la ventana divisora.|
|[CSplitterWnd::D eleteRow](#deleterow)|Elimina una fila de la ventana divisora.|
|[CSplitterWnd::D eleteView](#deleteview)|Elimina una vista de la ventana divisora.|
|[CSplitterWnd::D oKeyboardSplit](#dokeyboardsplit)|Ejecuta el comando de división del teclado, normalmente "división de la ventana".|
|[CSplitterWnd::D oScroll](#doscroll)|Realiza el desplazamiento sincronizado de ventanas divididas.|
|[CSplitterWnd::D oScrollBy](#doscrollby)|Desplaza las ventanas divididas por un número determinado de píxeles.|
|[CSplitterWnd:: GetActivePane](#getactivepane)|Determina el panel activo desde el foco o la vista activa del marco.|
|[CSplitterWnd:: GetColumnCount](#getcolumncount)|Devuelve el recuento de columnas del panel actual.|
|[CSplitterWnd:: GetColumnInfo](#getcolumninfo)|Devuelve información sobre la columna especificada.|
|[CSplitterWnd:: GetPane](#getpane)|Devuelve el panel de la fila y la columna especificadas.|
|[CSplitterWnd:: GetRowCount](#getrowcount)|Devuelve el recuento de filas del panel actual.|
|[CSplitterWnd:: GetRowInfo](#getrowinfo)|Devuelve información sobre la fila especificada.|
|[CSplitterWnd:: GetScrollStyle](#getscrollstyle)|Devuelve el estilo de barra de desplazamiento compartido.|
|[CSplitterWnd:: IdFromRowCol](#idfromrowcol)|Devuelve el identificador de la ventana secundaria del panel en la fila y la columna especificadas.|
|[CSplitterWnd:: IsChildPane](#ischildpane)|Llame a para determinar si la ventana es actualmente un panel secundario de esta ventana divisora.|
|[CSplitterWnd:: IsTracking](#istracking)|Determina si la barra de división se está moviendo actualmente.|
|[CSplitterWnd:: RecalcLayout](#recalclayout)|Llame a para volver a mostrar la ventana divisora después de ajustar el tamaño de la fila o de la columna.|
|[CSplitterWnd:: SetActivePane](#setactivepane)|Establece que un panel sea el activo en el marco.|
|[CSplitterWnd:: SetColumnInfo](#setcolumninfo)|Llame a para establecer la información de la columna especificada.|
|[CSplitterWnd:: SetRowInfo](#setrowinfo)|Llame a para establecer la información de fila especificada.|
|[CSplitterWnd:: SetScrollStyle](#setscrollstyle)|Especifica el nuevo estilo de barra de desplazamiento para la compatibilidad con la barra de desplazamiento compartida de la ventana divisora.|
|[CSplitterWnd:: SplitColumn](#splitcolumn)|Indica dónde se divide verticalmente una ventana de marco.|
|[CSplitterWnd:: SplitRow](#splitrow)|Indica dónde se divide horizontalmente una ventana de marco.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CSplitterWnd:: OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar la ventana divisora.|
|[CSplitterWnd:: OnDrawSplitter](#ondrawsplitter)|Representa una imagen de una ventana dividida.|
|[CSplitterWnd:: OnInvertTracker](#oninverttracker)|Representa la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.|

## <a name="remarks"></a>Observaciones

Un panel suele ser un objeto específico de la aplicación derivado de [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier objeto [CWnd](../../mfc/reference/cwnd-class.md) que tenga el identificador de la ventana secundaria adecuado.

Normalmente, un objeto `CSplitterWnd` se incrusta en un objeto primario [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) . Cree un objeto de `CSplitterWnd` siguiendo estos pasos:

1. Inserte una variable miembro de `CSplitterWnd` en el marco primario.

2. Invalide la función miembro [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) del marco primario.

3. En el `OnCreateClient`invalidado, llame a la función miembro [Create](#create) o [CreateStatic](#createstatic) de `CSplitterWnd`.

Llame a la función miembro `Create` para crear una ventana divisora dinámica. Normalmente, una ventana divisora dinámica se usa para crear y desplazar un número de paneles individuales, o vistas, del mismo documento. El marco de trabajo crea automáticamente un panel inicial para el divisor; a continuación, el marco de trabajo crea, cambia el tamaño y desecha paneles adicionales cuando el usuario trabaja con los controles de la ventana divisora.

Cuando se llama a `Create`, se especifica un alto de fila y un ancho de columna mínimos que determinan cuándo los paneles son demasiado pequeños para que se muestren por completo. Después de llamar a `Create`, puede ajustar estos mínimos llamando a las funciones miembro [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) .

Use también las funciones miembro `SetColumnInfo` y `SetRowInfo` para establecer un ancho "ideal" para una columna y el alto "ideal" para una fila. Cuando el marco de trabajo muestra una ventana divisora, primero muestra el marco primario y, a continuación, la ventana divisora. A continuación, el marco de trabajo diseña los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la parte superior izquierda hasta la esquina inferior derecha del área de cliente de la ventana divisora.

Todos los paneles de una ventana divisora dinámica deben ser de la misma clase. Entre las aplicaciones conocidas que admiten ventanas divisoras dinámicas se incluyen Microsoft Word y Microsoft Excel.

Utilice la función miembro `CreateStatic` para crear una ventana divisora estática. El usuario solo puede cambiar el tamaño de los paneles en una ventana divisora estática, no su número ni orden.

Debe crear específicamente todos los paneles del divisor estático al crear el divisor estático. Asegúrese de crear todos los paneles antes de que se devuelva la función miembro `OnCreateClient` del marco primario o el marco de trabajo no mostrará la ventana correctamente.

La función miembro `CreateStatic` inicializa automáticamente un divisor estático con un alto mínimo de fila y un ancho de columna de 0. Después de llamar a `Create`, ajuste estos mínimos llamando a las funciones miembro [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) . Use también `SetColumnInfo` y `SetRowInfo` después de llamar a `CreateStatic` para indicar las dimensiones de panel ideales deseadas.

Los paneles individuales de un divisor estático suelen pertenecer a clases diferentes. Para obtener ejemplos de ventanas divisoras estáticas, consulte el editor de gráficos y el administrador de archivos de Windows.

Una ventana divisora admite barras de desplazamiento especiales (aparte de las barras de desplazamiento que pueden tener los paneles). Estas barras de desplazamiento son elementos secundarios del objeto `CSplitterWnd` y se comparten con los paneles.

Estas barras de desplazamiento especiales se crean al crear la ventana divisora. Por ejemplo, un `CSplitterWnd` que tiene una fila, dos columnas y el estilo de WS_VSCROLL mostrará una barra de desplazamiento vertical compartida por los dos paneles. Cuando el usuario mueve la barra de desplazamiento, se envían WM_VSCROLL mensajes a ambos paneles. Cuando los paneles establecen la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartida.

Para obtener más información sobre las ventanas divisoras, vea la [Nota técnica 29](../../mfc/tn029-splitter-windows.md).

Para obtener más información sobre cómo crear ventanas divisoras dinámicas, consulte:

- [Scribble](../../overview/visual-cpp-samples.md) de ejemplo de MFC

- Ejemplo de MFC [VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxext. h

##  <a name="activatenext"></a>CSplitterWnd:: ActivateNext

Lo llama el marco de trabajo para ejecutar el siguiente panel o el comando del panel anterior.

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica la ventana que se va a activar. **True** para Previous; **False** para Next.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación de `CSplitterWnd`.

##  <a name="canactivatenext"></a>CSplitterWnd:: CanActivateNext

Lo llama el marco de trabajo para comprobar si el siguiente panel o el comando del panel anterior es posible actualmente.

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>Parámetros

*bPrev*<br/>
Indica la ventana que se va a activar. **True** para Previous; **False** para Next.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación de `CSplitterWnd`.

##  <a name="create"></a>CSplitterWnd:: Create

Para crear una ventana divisora dinámica, llame a la función miembro `Create`.

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
Ventana de marco primaria de la ventana divisora.

*nMaxRows*<br/>
Número máximo de filas de la ventana divisora. Este valor no debe ser superior a 2.

*nMaxCols*<br/>
Número máximo de columnas en la ventana divisora. Este valor no debe ser superior a 2.

*sizeMin*<br/>
Especifica el tamaño mínimo en el que se puede mostrar un panel.

*pContext*<br/>
Puntero a una estructura [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) . En la mayoría de los casos, puede ser el elemento *pContext* pasado a la ventana de marco principal.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la ventana. El identificador se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Puede incrustar una `CSplitterWnd` en un objeto de [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) primario realizando los pasos siguientes:

1. Inserte una variable miembro de `CSplitterWnd` en el marco primario.

1. Invalide la función miembro [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) del marco primario.

1. Llame a la función miembro `Create` desde dentro del `OnCreateClient`invalidado.

Cuando se crea una ventana divisora desde dentro de un marco primario, se pasa el parámetro *pContext* del marco primario a la ventana divisora. De lo contrario, este parámetro puede ser NULL.

El alto de fila y el ancho de columna mínimos de una ventana divisora dinámica se establecen mediante el parámetro *sizeMin* . Estos mínimos, que determinan si un panel es demasiado pequeño para que se muestre en su totalidad, se puede cambiar con las funciones miembro [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) .

Para obtener más información sobre las ventanas divisoras dinámicas, vea "ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [Nota técnica 29](../../mfc/tn029-splitter-windows.md)y la información general de la clase `CSplitterWnd`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>CSplitterWnd:: CreateScrollBarCtrl

Lo llama el marco de trabajo para crear un control de barra de desplazamiento compartido.

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la ventana. El identificador se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Invalide `CreateScrollBarCtrl` para incluir controles adicionales junto a una barra de desplazamiento. El comportamiento predeterminado es crear controles normales de la barra de desplazamiento de Windows.

##  <a name="createstatic"></a>CSplitterWnd:: CreateStatic

Para crear una ventana divisora estática, llame a la función miembro `CreateStatic`.

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
Ventana de marco primaria de la ventana divisora.

*nRows*<br/>
El número de filas. Este valor no debe ser superior a 16.

*nCols*<br/>
El número de columnas. Este valor no debe ser superior a 16.

*dwStyle*<br/>
Especifica el estilo de ventana.

*nID*<br/>
IDENTIFICADOR de la ventana secundaria de la ventana. El identificador se puede AFX_IDW_PANE_FIRST a menos que la ventana divisora esté anidada dentro de otra ventana divisora.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Normalmente, un `CSplitterWnd` se incrusta en un objeto `CFrameWnd` o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) primarios realizando los pasos siguientes:

1. Inserte una variable miembro de `CSplitterWnd` en el marco primario.

1. Invalide la función miembro `OnCreateClient` del marco primario.

1. Llame a la función miembro de `CreateStatic` desde el interior de [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)reemplazado.

Una ventana divisora estática contiene un número fijo de paneles, a menudo de clases diferentes.

Al crear una ventana divisora estática, debe crear al mismo tiempo todos los paneles. La función miembro [CreateView](#createview) se suele usar para este propósito, pero también puede crear otras clases no vistas.

El alto de fila y el ancho de columna mínimos iniciales para una ventana divisora estática es 0. Estos mínimos, que determinan cuándo un panel es demasiado pequeño para que se muestre en su totalidad, se pueden cambiar con las funciones miembro [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) .

Para agregar barras de desplazamiento a una ventana divisora estática, agregue los estilos WS_HSCROLL y WS_VSCROLL a *dwStyle*.

Vea "ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [Nota técnica 29](../../mfc/tn029-splitter-windows.md)y la información general sobre las clases de `CSplitterWnd` para obtener más información sobre las ventanas divisoras estáticas.

##  <a name="createview"></a>CSplitterWnd:: CreateView

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

*row*<br/>
Especifica la fila de la ventana divisora en la que se va a colocar la nueva vista.

*col*<br/>
Especifica la columna de la ventana divisora en la que se va a colocar la nueva vista.

*pViewClass*<br/>
Especifica el [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nueva vista.

*sizeInit*<br/>
Especifica el tamaño inicial de la nueva vista.

*pContext*<br/>
Puntero a un contexto de creación que se usa para crear la vista (normalmente, el elemento *pContext* pasado a la función miembro [CFrameWnd:: OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) reemplazada por el fotograma primario en el que se crea la ventana divisora).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Todos los paneles de una ventana divisora estática deben crearse antes de que el marco de trabajo muestre el divisor.

El marco de trabajo también llama a esta función miembro para crear paneles nuevos cuando el usuario de una ventana divisora dinámica divide un panel, una fila o una columna.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>CSplitterWnd:: CSplitterWnd

Llame a para construir un objeto de `CSplitterWnd`.

```
CSplitterWnd();
```

### <a name="remarks"></a>Observaciones

Construya un objeto `CSplitterWnd` en dos pasos. En primer lugar, llame al constructor, que crea el objeto `CSplitterWnd` y, a continuación, llame a la función miembro [Create](#create) , que crea la ventana divisora y la adjunta al objeto `CSplitterWnd`.

##  <a name="deletecolumn"></a>CSplitterWnd::D eleteColumn

Elimina una columna de la ventana divisora.

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>Parámetros

*colDelete*<br/>
Especifica la columna que se va a eliminar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar separadores dinámicos más avanzados.

##  <a name="deleterow"></a>CSplitterWnd::D eleteRow

Elimina una fila de la ventana divisora.

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>Parámetros

*rowDelete*<br/>
Especifica la fila que se va a eliminar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar separadores dinámicos más avanzados.

##  <a name="deleteview"></a>CSplitterWnd::D eleteView

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

### <a name="remarks"></a>Observaciones

Si se está eliminando la vista activa, la siguiente vista pasará a estar activa. La implementación predeterminada presupone que la vista se eliminará automáticamente en [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).

El marco de trabajo llama a esta función miembro para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar separadores dinámicos más avanzados.

##  <a name="dokeyboardsplit"></a>CSplitterWnd::D oKeyboardSplit

Ejecuta el comando de división del teclado, normalmente "división de la ventana".

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro es un comando de alto nivel que utiliza la clase [CView](../../mfc/reference/cview-class.md) para delegar en la implementación de `CSplitterWnd`.

##  <a name="doscroll"></a>CSplitterWnd::D oScroll

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
Código de barra de desplazamiento que indica la solicitud de desplazamiento del usuario. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produce horizontalmente y un byte de orden superior, que determina el tipo de desplazamiento que se produce verticalmente:

- SB_BOTTOM se desplaza hasta la parte inferior.

- SB_LINEDOWN desplaza una línea hacia abajo.

- SB_LINEUP desplaza una línea hacia arriba.

- SB_PAGEDOWN desplaza una página hacia abajo.

- SB_PAGEUP desplaza una página hacia arriba.

- SB_TOP se desplaza hasta la parte superior.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es true (es decir, si existe una ventana secundaria y las ventanas divididas tienen un intervalo de desplazamiento), la acción de desplazamiento especificada puede tener lugar. Si *bDoScroll* es false (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen intervalo de desplazamiento), no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce el desplazamiento sincronizado; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para realizar el desplazamiento sincronizado de ventanas divididas cuando la vista recibe un mensaje de desplazamiento. Invalide para requerir una acción por parte del usuario antes de que se permita el desplazamiento sincronizado.

##  <a name="doscrollby"></a>CSplitterWnd::D oScrollBy

Desplaza las ventanas divididas por un número determinado de píxeles.

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
Número de píxeles que se va a desplazar horizontal y verticalmente.

*bDoScroll*<br/>
Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es true (es decir, si existe una ventana secundaria y las ventanas divididas tienen un intervalo de desplazamiento), la acción de desplazamiento especificada puede tener lugar. Si *bDoScroll* es false (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen intervalo de desplazamiento), no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se produce el desplazamiento sincronizado; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro en respuesta a un mensaje de desplazamiento, para realizar el desplazamiento sincronizado de las ventanas divididas por la cantidad, en píxeles, indicada por *sizeScroll*. Los valores positivos indican desplazarse hacia abajo y hacia la derecha; los valores negativos indican desplazarse hacia arriba y hacia la izquierda.

Invalide para requerir una acción por parte del usuario antes de permitir el desplazamiento.

##  <a name="getactivepane"></a>CSplitterWnd:: GetActivePane

Determina el panel activo desde el foco o la vista activa del marco.

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>Parámetros

*pRow*<br/>
Un puntero a un **entero** para recuperar el número de fila del panel activo.

*pCol*<br/>
Un puntero a un **entero** para recuperar el número de columna del panel activo.

### <a name="return-value"></a>Valor devuelto

Puntero al panel activo. ES NULL si no existe ningún panel activo.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para determinar el panel activo en una ventana divisora. Invalide para requerir una acción por parte del usuario antes de obtener el panel activo.

##  <a name="getcolumncount"></a>CSplitterWnd:: GetColumnCount

Devuelve el recuento de columnas del panel actual.

```
int GetColumnCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de columnas en el divisor. En el caso de un divisor estático, este también será el número máximo de columnas.

##  <a name="getcolumninfo"></a>CSplitterWnd:: GetColumnInfo

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
Referencia a un valor **int** que se va a establecer en el ancho actual de la columna.

*cxMin*<br/>
Referencia a un valor **int** que se va a establecer en el ancho mínimo actual de la columna.

##  <a name="getpane"></a>CSplitterWnd:: GetPane

Devuelve el panel de la fila y la columna especificadas.

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

Devuelve el panel de la fila y la columna especificadas. El panel devuelto suele ser una clase derivada de [CView](../../mfc/reference/cview-class.md).

##  <a name="getrowcount"></a>CSplitterWnd:: GetRowCount

Devuelve el recuento de filas del panel actual.

```
int GetRowCount() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el número actual de filas de la ventana divisora. En el caso de una ventana divisora estática, este será también el número máximo de filas.

##  <a name="getrowinfo"></a>CSplitterWnd:: GetRowInfo

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
Referencia a **int** que se va a establecer en el alto actual de la fila, en píxeles.

*cyMin*<br/>
Referencia a **int** que se va a establecer en el alto mínimo actual de la fila, en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para obtener información acerca de la fila especificada. El parámetro *cyCur* se rellena con el alto actual de la fila especificada y *cyMin* se rellena con el alto mínimo de la fila.

##  <a name="getscrollstyle"></a>CSplitterWnd:: GetScrollStyle

Devuelve el estilo de barra de desplazamiento compartido de la ventana divisora.

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>Valor devuelto

Uno o varios de los siguientes marcadores de estilo de Windows, si es correcto:

- WS_HSCROLL si el divisor administra actualmente barras de desplazamiento horizontales compartidas.

- WS_VSCROLL si el divisor administra actualmente barras de desplazamiento vertical compartidas.

Si es cero, la ventana divisora no administra actualmente ninguna barra de desplazamiento compartida.

##  <a name="idfromrowcol"></a>CSplitterWnd:: IdFromRowCol

Obtiene el identificador de la ventana secundaria para el panel en la fila y la columna especificadas.

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

IDENTIFICADOR de la ventana secundaria del panel.

### <a name="remarks"></a>Observaciones

Esta función miembro se usa para crear las no vistas como paneles y se puede llamar antes de que el panel exista.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>CSplitterWnd:: IsChildPane

Determina si *PWND* es actualmente un panel secundario de esta ventana divisora.

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Un puntero a un objeto [CWnd](../../mfc/reference/cwnd-class.md) que se va a probar.

*pRow*<br/>
Un puntero a un **entero** en el que se va a almacenar el número de fila.

*pCol*<br/>
Un puntero a un **entero** en el que se va a almacenar un número de columna.

### <a name="return-value"></a>Valor devuelto

Si es distinto de cero, *PWND* es actualmente un panel secundario de esta ventana divisora y *pRow* y *pCol* se rellenan con la posición del panel en la ventana divisora. Si *PWND* no es un panel secundario de esta ventana divisora, se devuelve 0.

### <a name="remarks"></a>Observaciones

En las C++ versiones de Visual anteriores a 6,0, esta función se definió como

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

Esta versión está ahora obsoleta y no debe usarse.

##  <a name="istracking"></a>CSplitterWnd:: IsTracking

Llame a esta función miembro para determinar si la barra divisora de la ventana se está moviendo actualmente.

```
BOOL IsTracking();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si hay una operación de divisor en curso; de lo contrario, es 0.

##  <a name="ondrawsplitter"></a>CSplitterWnd:: OnDrawSplitter

Representa una imagen de una ventana dividida.

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo en el que se va a dibujar. Si *pDC* es null, el marco de trabajo llama a [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) y no se dibuja ninguna ventana dividida.

*nType*<br/>
Un valor de la `enum ESplitType`, que puede ser uno de los siguientes:

- `splitBox` el cuadro de arrastre del divisor.

- `splitBar` la barra que aparece entre las dos ventanas divididas.

- `splitIntersection` la intersección de las ventanas divididas. No se llamará a este elemento cuando se ejecute en Windows 95/98.

- `splitBorder` los bordes de la ventana dividida.

*Rect*<br/>
Referencia a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que especifica el tamaño y la forma de las ventanas divididas.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para dibujar y especificar las características exactas de una ventana divisora. Invalide `OnDrawSplitter` para la personalización avanzada de la imagen de los distintos componentes gráficos de una ventana divisora. La imagen predeterminada es similar al divisor de Microsoft Works para Windows o Microsoft Windows 95/98, en el que las intersecciones de las barras divisoras están combinadas.

Para obtener más información sobre las ventanas divisoras dinámicas, vea "ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [Nota técnica 29](../../mfc/tn029-splitter-windows.md)y la información general de la clase `CSplitterWnd`.

##  <a name="oninverttracker"></a>CSplitterWnd:: OnInvertTracker

Representa la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Referencia a un objeto `CRect` que especifica el rectángulo de seguimiento.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro durante el cambio de tamaño de los divisores. Invalide `OnInvertTracker` para la personalización avanzada de la imagen de la ventana divisora. La imagen predeterminada es similar al divisor de Microsoft Works para Windows o Microsoft Windows 95/98, en el que las intersecciones de las barras divisoras están combinadas.

Para obtener más información sobre las ventanas divisoras dinámicas, vea "ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [Nota técnica 29](../../mfc/tn029-splitter-windows.md)y la información general de la clase `CSplitterWnd`.

##  <a name="recalclayout"></a>CSplitterWnd:: RecalcLayout

Llame a para volver a mostrar la ventana divisora después de ajustar el tamaño de la fila o de la columna.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para volver a mostrar correctamente la ventana divisora después de ajustar los tamaños de fila y de columna con las funciones miembro [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) . Si cambia el tamaño de las filas y las columnas como parte del proceso de creación antes de que la ventana divisora esté visible, no es necesario llamar a esta función miembro.

El marco de trabajo llama a esta función miembro cada vez que el usuario cambia el tamaño de la ventana divisora o mueve una división.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CSplitterWnd:: SetColumnInfo](#setcolumninfo).

##  <a name="setactivepane"></a>CSplitterWnd:: SetActivePane

Establece que un panel sea el activo en el marco.

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*row*<br/>
Si *PWND* es null, especifica la fila del panel que estará activa.

*col*<br/>
Si *PWND* es null, especifica la columna del panel que estará activa.

*pWnd*<br/>
Puntero a un objeto `CWnd` . Si es NULL, el panel especificado por *Row* y *col* está establecido en activo. Si no es NULL, especifica el panel que está activado.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro para establecer un panel como activo cuando el usuario cambia el foco a un panel de la ventana de marco. Puede llamar explícitamente a `SetActivePane` para cambiar el foco a la vista especificada.

Especifique el panel proporcionando una fila y una columna, **o** bien proporcionando *PWND*.

##  <a name="setcolumninfo"></a>CSplitterWnd:: SetColumnInfo

Llame a para establecer la información de la columna especificada.

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
Especifica un ancho ideal para la columna de la ventana divisora en píxeles.

*cxMin*<br/>
Especifica un ancho mínimo para la columna de la ventana divisora en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para establecer un nuevo ancho mínimo y un ancho ideal para una columna. El valor mínimo de la columna determina si la columna será demasiado pequeña para mostrarse por completo.

Cuando el marco de trabajo muestra la ventana divisora, coloca los paneles en columnas y filas según sus dimensiones ideales, trabajando en la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>CSplitterWnd:: SetRowInfo

Llame a para establecer la información de fila especificada.

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
Especifica un alto ideal para la fila de la ventana divisora en píxeles.

*cyMin*<br/>
Especifica el alto mínimo de la fila de la ventana divisora en píxeles.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro para establecer un nuevo alto mínimo y un alto ideal para una fila. El valor mínimo de la fila determina si la fila será demasiado pequeña para mostrarse por completo.

Cuando el marco de trabajo muestra la ventana divisora, coloca los paneles en columnas y filas según sus dimensiones ideales, trabajando en la esquina superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.

##  <a name="setscrollstyle"></a>CSplitterWnd:: SetScrollStyle

Especifica el nuevo estilo de desplazamiento para la compatibilidad con la barra de desplazamiento compartida de la ventana divisora.

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Nuevo estilo de desplazamiento para la compatibilidad con la barra de desplazamiento compartida de la ventana divisora, que puede ser uno de los valores siguientes:

- WS_HSCROLL crear o Mostrar barras de desplazamiento compartidas horizontales.

- WS_VSCROLL crear o Mostrar barras de desplazamiento compartidas verticales.

### <a name="remarks"></a>Observaciones

Una vez que se crea una barra de desplazamiento, no se destruirá incluso si se llama a `SetScrollStyle` sin ese estilo; en su lugar, se ocultan las barras de desplazamiento. Esto permite que las barras de desplazamiento conserven su estado aunque estén ocultos. Después de llamar a `SetScrollStyle` es necesario llamar a [RecalcLayout](#recalclayout) para que todos los cambios surtan efecto.

##  <a name="splitcolumn"></a>CSplitterWnd:: SplitColumn

Indica dónde se divide verticalmente una ventana de marco.

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>Parámetros

*cxBefore*<br/>
Posición, en píxeles, antes de la que se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro cuando se crea una ventana divisora vertical. `SplitColumn` indica la ubicación predeterminada en la que se produce la división.

el marco de trabajo llama a `SplitColumn` para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo de SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar separadores dinámicos más avanzados.

##  <a name="splitrow"></a>CSplitterWnd:: SplitRow

Indica dónde se divide horizontalmente una ventana de marco.

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>Parámetros

*cyBefore*<br/>
Posición, en píxeles, antes de la que se produce la división.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se llama a esta función miembro cuando se crea una ventana divisora horizontal. `SplitRow` indica la ubicación predeterminada en la que se produce la división.

el marco de trabajo llama a `SplitRow` para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo de SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar separadores dinámicos más avanzados.

##  <a name="ondraw"></a>CSplitterWnd:: OnDraw

Lo llama el marco de trabajo para dibujar la ventana divisora.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
