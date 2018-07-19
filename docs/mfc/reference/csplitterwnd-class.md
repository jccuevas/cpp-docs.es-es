---
title: Clase CSplitterWnd | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b3d2b44c4e854a27bcc753c1403ea058b03906a8
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37123154"
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
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Llamada a construir un `CSplitterWnd` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|Ejecuta el comando panel siguiente o anterior.|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Comprueba si el comando panel siguiente o panel anterior actualmente es posible.|  
|[CSplitterWnd:: Create](#create)|Llamada a crear una ventana divisora dinámica y conectarla a la `CSplitterWnd` objeto.|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crea un control de barra de desplazamiento compartido.|  
|[CSplitterWnd:: CreateStatic](#createstatic)|Llamada a crear una ventana divisora estática y conectarla a la `CSplitterWnd` objeto.|  
|[CSplitterWnd:: CreateView](#createview)|La llamada para crear un panel en una ventana divisora.|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Elimina una columna de la ventana divisora.|  
|[CSplitterWnd::DeleteRow](#deleterow)|Elimina una fila de la ventana divisora.|  
|[CSplitterWnd::DeleteView](#deleteview)|Elimina una vista de la ventana divisora.|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Realiza el teclado dividir comando, normalmente "división de ventana".|  
|[CSplitterWnd::DoScroll](#doscroll)|Realiza el desplazamiento sincronizado de ventanas de división.|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|Desplaza ventanas divididas un número determinado de píxeles.|  
|[CSplitterWnd::GetActivePane](#getactivepane)|Determina el panel activo del foco o la vista activa en el marco.|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Devuelve el número de columnas del panel actual.|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Devuelve información sobre la columna especificada.|  
|[CSplitterWnd::GetPane](#getpane)|Devuelve el panel, en la fila y columna especificadas.|  
|[CSplitterWnd::GetRowCount](#getrowcount)|Devuelve el recuento de filas del panel actual.|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Devuelve información sobre la fila especificada.|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Devuelve el estilo de barra de desplazamiento compartido.|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Devuelve al elemento secundario Id. de la ventana del panel en la fila y columna especificadas.|  
|[CSplitterWnd::IsChildPane](#ischildpane)|La llamada para determinar si la ventana es actualmente un panel secundario de esta ventana divisora.|  
|[CSplitterWnd::IsTracking](#istracking)|Determina si actualmente se está moviendo barra divisora.|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.|  
|[CSplitterWnd::SetActivePane](#setactivepane)|Establece un panel que se van a los activos en el marco.|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|La llamada para establecer la información de la columna especificada.|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|La llamada para establecer la información de la fila especificada.|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Especifica que el nuevo estilo de barra de desplazamiento de la ventana divisora compartido soporte técnico de la barra de desplazamiento.|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indica dónde se divide verticalmente una ventana de marco.|  
|[CSplitterWnd::SplitRow](#splitrow)|Indica dónde se divide horizontalmente una ventana de marco.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|Lo llama el marco de trabajo para dibujar la ventana divisora.|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Representa una imagen de una ventana dividida.|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Representa la imagen de una ventana dividida para que tenga el mismo tamaño y la misma forma que la ventana de marco.|  
  
## <a name="remarks"></a>Comentarios  
 Un panel suele ser un objeto específico de la aplicación derivado de [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier [CWnd](../../mfc/reference/cwnd-class.md) objeto que tiene el identificador de ventana de secundario correspondiente.  
  
 A `CSplitterWnd` objeto normalmente está incrustado en una carpeta primaria [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto. Crear un `CSplitterWnd` objeto siguiendo estos pasos:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.  
  
3.  Desde dentro el invalidado `OnCreateClient`, llame a la [crear](#create) o [CreateStatic](#createstatic) función miembro de `CSplitterWnd`.  
  
 Llame a la `Create` función de miembro para crear una ventana divisora dinámica. Una ventana divisora dinámica normalmente se usa para crear y desplazar un número de paneles individuales o vistas del mismo documento. El marco de trabajo crea automáticamente un panel inicial del divisor; a continuación, el marco de trabajo crea, cambia el tamaño y se deshace de los paneles adicionales como el usuario opera controles de la ventana divisora.  
  
 Cuando se llama a `Create`, especifique un mínimo de la fila alto y ancho de columna que determinan si los paneles están demasiado pequeños para mostrarse por completo. Después de llamar a `Create`, puede ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro.  
  
 Usar el `SetColumnInfo` y `SetRowInfo` funciones de miembro para establecer un ancho de una columna "ideal" y "ideal" alto de una fila. Cuando el marco de trabajo muestra una ventana divisora, primero se muestra el marco primario, a continuación, en la ventana divisora. El marco de trabajo, a continuación, distribuye los paneles en columnas y filas según sus dimensiones ideales, trabajan en la parte superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
 Todos los paneles en una ventana divisora dinámica deben ser de la misma clase. Aplicaciones conocidas que admiten las ventanas divisoras dinámicas incluyen Microsoft Word y Microsoft Excel.  
  
 Use la `CreateStatic` función de miembro para crear una ventana divisora estática. El usuario puede cambiar sólo el tamaño de los paneles de un divisor estático ventana, no su número o el orden.  
  
 Específicamente debe crear paneles del todos los divisoras estáticas cuando se crea el divisor estático. Asegúrese de crear todos los paneles antes el marco primario `OnCreateClient` valores devueltos de función miembro o el marco de trabajo mostrará no la ventana correctamente.  
  
 El `CreateStatic` función miembro inicializa automáticamente un divisor estático con un mínimo de la fila alto y ancho de columna de 0. Después de llamar a `Create`, ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro. Usar `SetColumnInfo` y `SetRowInfo` después de llamar a `CreateStatic` para indicar deseada dimensiones del panel ideal.  
  
 Los paneles individuales de un divisor estático suelen pertenecen a clases diferentes. Para obtener ejemplos de las ventanas divisoras estáticas, vea el editor de gráficos y el Administrador de archivos de Windows.  
  
 Una ventana divisora admite barras de desplazamiento especial (aparte de las barras de desplazamiento que pueden tener paneles). Estas barras de desplazamiento son elementos secundarios de la `CSplitterWnd` del objeto y se comparten con los paneles.  
  
 Cree estas barras de desplazamiento especial cuando se crea la ventana divisora. Por ejemplo, un `CSplitterWnd` que contiene una fila, dos columnas y el estilo WS_VSCROLL mostrará una barra de desplazamiento vertical que se comparte entre los dos paneles. Cuando el usuario mueve la barra de desplazamiento, se envían mensajes WM_VSCROLL a dos paneles. Cuando los paneles establece la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartido.  
  
 Para obtener más información sobre las ventanas divisoras, vea:  
  
- [Nota técnica 29](../../mfc/tn029-splitter-windows.md)  
  
-   El artículo de Knowledge Base Q262024: HOWTO: CPropertySheet Use como un elemento secundario del objeto CSplitterWnd  
  
 Para obtener más información sobre cómo crear ventanas divisoras dinámicas, vea:  
  
-   Ejemplo MFC [Scribble](../../visual-cpp-samples.md)  
  
-   Ejemplo MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext  
 Lo llama el marco de trabajo para realizar el comando panel siguiente o anterior.  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPrev*  
 Indica qué ventana para activar. **TRUE** para anterior; **FALSE** siguiente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que se usa por la [CView](../../mfc/reference/cview-class.md) clase delegar en el `CSplitterWnd` implementación.  
  
##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext  
 Lo llama el marco de trabajo para comprobar si el comando panel siguiente o panel anterior actualmente es posible.  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bPrev*  
 Indica qué ventana para activar. **TRUE** para anterior; **FALSE** siguiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que se usa por la [CView](../../mfc/reference/cview-class.md) clase delegar en el `CSplitterWnd` implementación.  
  
##  <a name="create"></a>  CSplitterWnd:: Create  
 Para crear una ventana divisora dinámica, llame a la **crear** función miembro.  
  
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
 *pParentWnd*  
 La ventana de marco principal de la ventana divisora.  
  
 *nMaxRows*  
 El número máximo de filas de la ventana divisora. Este valor no debe superar los 2.  
  
 *nMaxCols*  
 El número máximo de columnas en la ventana divisora. Este valor no debe superar los 2.  
  
 *sizeMin*  
 Especifica el tamaño mínimo en el que se puede mostrar un panel de.  
  
 *pContext*  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. En la mayoría de los casos, esto puede ser el *pContext* pasa a la ventana de marco principal.  
  
 *dwStyle*  
 Especifica el estilo de ventana.  
  
 *nID*  
 El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Puede incrustar un `CSplitterWnd` en una carpeta primaria [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto realizando los pasos siguientes:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.  
  
3.  Llame a la `Create` función miembro dentro de la invalidado `OnCreateClient`.  
  
 Cuando se crea una ventana divisora desde dentro de un marco primario, pasar el marco primario *pContext* parámetro a la ventana divisora. En caso contrario, este parámetro puede ser NULL.  
  
 Establece el ancho mínimo de la fila inicial de alto y la columna de una ventana divisora dinámica la *sizeMin* parámetro. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
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
 *dwStyle*  
 Especifica el estilo de ventana.  
  
 *nID*  
 El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Invalidar `CreateScrollBarCtrl` para incluir controles adicionales al lado de una barra de desplazamiento. El comportamiento predeterminado consiste en crear controles de barra de desplazamiento de Windows normales.  
  
##  <a name="createstatic"></a>  CSplitterWnd:: CreateStatic  
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
 *pParentWnd*  
 La ventana de marco principal de la ventana divisora.  
  
 *nRows*  
 Número de filas. Este valor no debe ser superior a 16.  
  
 *nCols*  
 Número de columnas. Este valor no debe ser superior a 16.  
  
 *dwStyle*  
 Especifica el estilo de ventana.  
  
 *nID*  
 El identificador de ventana secundaria de la ventana. El identificador puede ser AFX_IDW_PANE_FIRST a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 A `CSplitterWnd` normalmente está incrustado en una carpeta primaria `CFrameWnd` o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto realizando los pasos siguientes:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario `OnCreateClient` función miembro.  
  
3.  Llame a la `CreateStatic` función miembro dentro de la invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).  
  
 Una ventana divisora estática contiene un número fijo de paneles, a menudo a partir de clases diferentes.  
  
 Cuando se crea una ventana divisora estática, deben al mismo tiempo crear todos sus paneles. El [CreateView](#createview) normalmente se utiliza la función miembro para este propósito, pero puede crear otras clases de nonview también.  
  
 El mínimo de la fila inicial alto y ancho de columna para una ventana divisora estática es 0. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño que se mostrará en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.  
  
 Para agregar barras de desplazamiento a una ventana divisora estática, agregar los estilos WS_HSCROLL y WS_VSCROLL a *dwStyle*.  
  
 Consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase para obtener más información sobre las ventanas divisoras estáticas.  
  
##  <a name="createview"></a>  CSplitterWnd:: CreateView  
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
 *Fila*  
 Especifica la fila de la ventana divisora en la que se va a colocar la nueva vista.  
  
 *Col.*  
 Especifica la columna de la ventana divisora en el que se va a colocar la nueva vista.  
  
 *pViewClass*  
 Especifica la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nueva vista.  
  
 *sizeInit*  
 Especifica el tamaño inicial de la nueva vista.  
  
 *pContext*  
 Un puntero a un contexto de creación que se usa para crear la vista (normalmente el *pContext* pasado en el marco primario invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro en el que es la ventana divisora que se va a crear).  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Todos los paneles de una ventana divisora estática deben crearse antes de que el marco de trabajo muestra el divisor.  
  
 El marco de trabajo también llama a esta función miembro para crear paneles de nuevo cuando el usuario de una ventana divisora dinámica divide un panel, fila o columna.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd  
 Llamada a construir un `CSplitterWnd` objeto.  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CSplitterWnd` objeto en dos pasos. En primer lugar, llame al constructor, que crea el `CSplitterWnd` objeto y, a continuación, llame a la [crear](#create) función de miembro, que crea la ventana divisora y lo adjunta a la `CSplitterWnd` objeto.  
  
##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn  
 Elimina una columna de la ventana divisora.  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 *colDelete*  
 Especifica la columna que se va a eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview)para implementar divisores dinámicas más avanzadas.  
  
##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow  
 Elimina una fila de la ventana divisora.  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 *filaEliminar*  
 Especifica la fila que se va a eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview)para implementar divisores dinámicas más avanzadas.  
  
##  <a name="deleteview"></a>  CSplitterWnd::DeleteView  
 Elimina una vista de la ventana divisora.  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>Parámetros  
 *Fila*  
 Especifica la fila de la ventana divisora en la que se va a eliminar la vista.  
  
 *Col.*  
 Especifica la columna de la ventana divisora en el que se va a eliminar la vista.  
  
### <a name="remarks"></a>Comentarios  
 Si se elimina la vista activa, se activará la siguiente vista. La implementación predeterminada supone automáticamente la vista eliminar en [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).  
  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview)para implementar divisores dinámicas más avanzadas.  
  
##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit  
 Realiza el teclado dividir comando, normalmente "división de ventana".  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que se usa por la [CView](../../mfc/reference/cview-class.md) clase delegar en el `CSplitterWnd` implementación.  
  
##  <a name="doscroll"></a>  CSplitterWnd::DoScroll  
 Realiza el desplazamiento sincronizado de ventanas de división.  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pViewFrom*  
 Un puntero a la vista desde el que se origina el mensaje de desplazamiento.  
  
 *nScrollCode*  
 Se desplaza en un código de barras de desplazamiento que indica al usuario la solicitud. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produzca horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produzca verticalmente:  
  
- SB_BOTTOM se desplaza hacia abajo.  
  
- Una línea de SB_LINEDOWN se desplaza hacia abajo.  
  
- Una línea de SB_LINEUP desplaza hacia arriba.  
  
- Una página de SB_PAGEDOWN se desplaza hacia abajo.  
  
- Una página de SB_PAGEUP se desplaza hacia arriba.  
  
- Se desplaza hacia la SB_TOP al principio.  
  
 *bDoScroll*  
 Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria, y si las ventanas de división tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si *bDoScroll* es FALSE (es decir, si no hay ninguna ventana secundaria existe, o las vistas divididas no tienen ningún intervalo de desplazamiento), a continuación, el desplazamiento no se produce.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se produce el desplazamiento sincronizado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para realizar un desplazamiento sincronizado de división windows cuando la vista recibe un mensaje de desplazamiento. Reemplace este valor para requerir una acción del usuario antes de que se permite el desplazamiento sincronizado.  
  
##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy  
 Desplaza ventanas divididas un número determinado de píxeles.  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pViewFrom*  
 Un puntero a la vista desde el que se origina el mensaje de desplazamiento.  
  
 *sizeScroll*  
 Número de píxeles que se puede desplazar horizontalmente y verticalmente.  
  
 *bDoScroll*  
 Determina si se produce la acción de desplazamiento especificada. Si *bDoScroll* es TRUE (es decir, si existe una ventana secundaria, y si las ventanas de división tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si *bDoScroll* es FALSE (es decir, si no hay ninguna ventana secundaria existe, o las vistas divididas no tienen ningún intervalo de desplazamiento), a continuación, el desplazamiento no se produce.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se produce el desplazamiento sincronizado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo en respuesta a un mensaje de desplazamiento, para realizar la sincronización de desplazarse por las ventanas de división por la cantidad, en píxeles, indicado por *sizeScroll*. Los valores positivos indican el desplazamiento hacia abajo y a la derecha; los valores negativos indican el desplazamiento hacia arriba y hacia la izquierda.  
  
 Invalidar para requerir la intervención del usuario antes de permitir el desplazamiento.  
  
##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane  
 Determina el panel activo del foco o la vista activa en el marco.  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pRow*  
 Un puntero a un **int** para recuperar el número de fila de la sección activa.  
  
 *pCol*  
 Un puntero a un **int** para recuperar el número de columna del panel activo.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero para el panel activo. NULL si no existe ningún panel activo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para determinar el panel activo en una ventana divisora. Invalidar para requerir la intervención del usuario antes de obtener el panel activo.  
  
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
 *Col.*  
 Especifica una columna.  
  
 *cxCur*  
 Una referencia a un **int** se establezca en el ancho actual de la columna.  
  
 *cxMin*  
 Una referencia a un **int** se establezca en el ancho mínimo actual de la columna.  
  
##  <a name="getpane"></a>  CSplitterWnd::GetPane  
 Devuelve el panel, en la fila y columna especificadas.  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *Fila*  
 Especifica una fila.  
  
 *Col.*  
 Especifica una columna.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el panel, en la fila y columna especificadas. El panel devuelto es normalmente un [CView](../../mfc/reference/cview-class.md)-clase derivada.  
  
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
 *Fila*  
 Especifica una fila.  
  
 *cyCur*  
 Referencia a **int** se establezca en el alto actual de la fila en píxeles.  
  
 *cyMin*  
 Referencia a **int** se establezca en el alto mínimo actual de la fila en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para obtener información acerca de la fila especificada. El *cyCur* parámetro se rellena con el alto actual de la fila especificada, y *cyMin* se rellena con el alto mínimo de la fila.  
  
##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle  
 Devuelve el estilo de barra de desplazamiento compartido para la ventana divisora.  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una o varias de las siguientes ventanas de estilo marcas, si se realiza correctamente:  
  
- WS_HSCROLL si que actualmente administra el divisor compartido barras de desplazamiento horizontal.  
  
- WS_VSCROLL si que actualmente administra el divisor compartido barras de desplazamiento vertical.  
  
 Si es cero, la ventana divisora no administra actualmente las barras de desplazamiento compartido.  
  
##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol  
 Obtiene al elemento secundario Id. de ventana para el panel en la fila y columna especificadas.  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *Fila*  
 Especifica la fila de la ventana divisora.  
  
 *Col.*  
 Especifica la columna de la ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de ventana secundaria para el panel.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se usa para crear nonviews como paneles y se puede llamar antes de que exista el panel.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane  
 Determina si *pWnd* actualmente es un panel secundario de esta ventana divisora.  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>Parámetros  
 *pWnd*  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto va a probar.  
  
 *pRow*  
 Un puntero a un **int** en el que se va a almacenar el número de fila.  
  
 *pCol*  
 Un puntero a un **int** en el que se va a almacenar un número de columna.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es distinto de cero, *pWnd* actualmente es un panel secundario de esta ventana divisora, y *pRow* y *pCol* se rellena con la posición del panel en la ventana divisora. Si *pWnd* no es un panel secundario de esta ventana divisora, se devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 En las versiones de Visual C++ anteriores a 6.0, esta función se define como  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 Esta versión ahora está obsoleta y no debe usarse.  
  
##  <a name="istracking"></a>  CSplitterWnd::IsTracking  
 Llame a esta función miembro para determinar si actualmente se está moviendo la barra de división en la ventana.  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si una operación de división está en curso; en caso contrario es 0.  
  
##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter  
 Representa una imagen de una ventana dividida.  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Un puntero al contexto de dispositivo en el que se va a dibujar. Si *pDC* es NULL, a continuación, [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) se llama el marco de trabajo y sin división se dibuja la ventana.  
  
 *nLas*  
 Un valor de la `enum ESplitType`, que puede ser uno de los siguientes:  
  
- `splitBox` El cuadro de arrastrar divisor.  
  
- `splitBar` La barra que aparece entre las ventanas de la división de dos.  
  
- `splitIntersection` La intersección de las ventanas de división. Este elemento no se llamará cuando se ejecuta en Windows 95 ó 98.  
  
- `splitBorder` Los bordes de ventana de la división.  
  
 *Rect*  
 Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el tamaño y la forma de las ventanas de división.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para dibujar y especificar las características exactas de una ventana divisora. Invalidar `OnDrawSplitter` para la personalización avanzada de las imágenes de los distintos componentes gráficos de una ventana divisora. Las imágenes de forma predeterminada es similar a la división en Microsoft Works para Windows o Microsoft Windows 95 o Windows 98, en que se fusionen las intersecciones de las barras de división.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker  
 Representa la imagen de una ventana dividida para que tenga el mismo tamaño y la misma forma que la ventana de marco.  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 *Rect*  
 Referencia a un `CRect` objeto que especifica el rectángulo de seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro durante el cambio de tamaño de los separadores. Invalidar `OnInvertTracker` para la personalización avanzada de las imágenes de la ventana divisora. Las imágenes de forma predeterminada es similar a la división en Microsoft Works para Windows o Microsoft Windows 95 o Windows 98, en que se fusionen las intersecciones de las barras de división.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout  
 Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para correctamente volver a mostrar la ventana divisora después de ajustar los tamaños de filas y columnas con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro. Si cambia los tamaños de fila y columna como parte del proceso de creación antes de la ventana divisora está visible, no es necesario llamar a esta función miembro.  
  
 El marco de trabajo llama a esta función miembro siempre que el usuario cambia el tamaño de la ventana divisora o mueve una división.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CSplitterWnd::SetColumnInfo](#setcolumninfo).  
  
##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane  
 Establece un panel que se van a los activos en el marco.  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *Fila*  
 Si *pWnd* es NULL, especifica la fila en el panel que va a estar activo.  
  
 *Col.*  
 Si *pWnd* es NULL, especifica la columna en el panel que va a estar activo.  
  
 *pWnd*  
 Un puntero a un `CWnd` objeto. Si es NULL, el panel especificado por *fila* y *col* se establece en activo. Si no es NULL, especifica el panel que está definido activo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para establecer un panel como activo cuando el usuario cambia el foco a un panel en la ventana de marco. Se puede llamar explícitamente `SetActivePane` para cambiar el foco a la vista especificada.  
  
 Especificar panel proporcionando la fila y columna, **o** proporcionando *pWnd*.  
  
##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo  
 La llamada para establecer la información de la columna especificada.  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>Parámetros  
 *Col.*  
 Especifica una columna de la ventana divisora.  
  
 *cxIdeal*  
 Especifica un ancho ideal de la columna de la ventana de divisor en píxeles.  
  
 *cxMin*  
 Especifica un ancho mínimo de la columna de la ventana de divisor en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para establecer un nuevo ancho mínimo y el ancho ideal para una columna. El valor mínimo de la columna determina si la columna será demasiado pequeña para mostrarse por completo.  
  
 Cuando el marco de trabajo muestra la ventana divisora, distribuye los paneles en columnas y filas según sus dimensiones ideales, trabajan en la parte superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo  
 La llamada para establecer la información de la fila especificada.  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>Parámetros  
 *Fila*  
 Especifica una fila de la ventana divisora.  
  
 *cyIdeal*  
 Especifica un alto ideal de la fila de la ventana de divisor en píxeles.  
  
 *cyMin*  
 Especifica un alto mínimo de la fila de la ventana de divisor en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para establecer un nuevo alto mínimo y el alto ideal para una fila. El valor mínimo de fila determina cuando la fila será demasiado pequeña para mostrarse por completo.  
  
 Cuando el marco de trabajo muestra la ventana divisora, distribuye los paneles en columnas y filas según sus dimensiones ideales, trabajan en la parte superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle  
 Especifica que el nuevo estilo de desplazamiento de la ventana divisora compartido soporte técnico de la barra de desplazamiento.  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwStyle*  
 El nuevo estilo de desplazamiento de la ventana divisora compartidas de soporte técnico de la barra de desplazamiento, que puede ser uno de los siguientes valores:  
  
- WS_HSCROLL crear/mostrar horizontal compartida barras de desplazamiento.  
  
- WS_VSCROLL crear/mostrar vertical compartido barras de desplazamiento.  
  
### <a name="remarks"></a>Comentarios  
 Una vez que se crea una barra de desplazamiento no se destruirán aun cuando `SetScrollStyle` se llama sin ese estilo; en su lugar, se ocultan las barras de desplazamiento. Esto permite que las barras de desplazamiento conservar su estado, incluso si están ocultos. Después de llamar a `SetScrollStyle` es necesario llamar a [RecalcLayout](#recalclayout) para todos los cambios surtan efecto.  
  
##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn  
 Indica dónde se divide verticalmente una ventana de marco.  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>Parámetros  
 *cxBefore*  
 La posición, en píxeles, antes de que se produce la división.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama cuando se crea una ventana divisora vertical. `SplitColumn` indica la ubicación predeterminada donde se produce la división.  
  
 `SplitColumn` se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview)para implementar divisores dinámicas más avanzadas.  
  
##  <a name="splitrow"></a>  CSplitterWnd::SplitRow  
 Indica dónde se divide horizontalmente una ventana de marco.  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>Parámetros  
 *cyBefore*  
 La posición, en píxeles, antes de que se produce la división.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama cuando se crea una ventana divisora horizontal. `SplitRow` indica la ubicación predeterminada donde se produce la división.  
  
 `SplitRow` se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene el estilo SPLS_DYNAMIC_SPLIT). Se puede personalizar, junto con la función virtual [CreateView](#createview)para implementar divisores dinámicas más avanzadas.  
  
##  <a name="ondraw"></a>  CSplitterWnd::OnDraw  
 Lo llama el marco de trabajo para dibujar la ventana divisora.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo VIEWEX de MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)
