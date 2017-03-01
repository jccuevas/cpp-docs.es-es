---
title: Clase CSplitterWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSplitterWnd
dev_langs:
- C++
helpviewer_keywords:
- static splitter windows
- multiple views
- splitter windows
- views, multiple per frame
- dynamic splitter windows
- CSplitterWnd class
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d015aa604c5394ccbe8c7471b70c84763cc00a5b
ms.lasthandoff: 02/24/2017

---
# <a name="csplitterwnd-class"></a>CSplitterWnd (clase)
Proporciona la funcionalidad de una ventana divisora, que es una ventana que contiene varios paneles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|Llamada a construir un `CSplitterWnd` objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|Ejecuta el comando panel siguiente o anterior.|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|Comprueba si el comando panel siguiente o panel anterior es actualmente posible.|  
|[CSplitterWnd:: Create](#create)|Llamada a crear una ventana divisora dinámica y adjuntarlo a la `CSplitterWnd` objeto.|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|Crea un control de barra de desplazamiento compartido.|  
|[CSplitterWnd:: CreateStatic](#createstatic)|Llamada a crear una ventana divisora estática y adjuntarlo a la `CSplitterWnd` objeto.|  
|[CSplitterWnd:: CreateView](#createview)|Llamada para crear un panel en una ventana divisora.|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|Elimina una columna de la ventana divisora.|  
|[CSplitterWnd::DeleteRow](#deleterow)|Elimina una fila de la ventana divisora.|  
|[CSplitterWnd::DeleteView](#deleteview)|Elimina una vista de la ventana divisora.|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|Realiza el teclado dividir el comando, normalmente "división de ventana".|  
|[CSplitterWnd::DoScroll](#doscroll)|Realiza el desplazamiento sincronizado de ventanas de división.|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|Desplaza ventanas divididas un número determinado de píxeles.|  
|[CSplitterWnd::GetActivePane](#getactivepane)|Determina el panel activo del foco o la vista activa en el marco.|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|Devuelve el número de columnas del panel actual.|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|Devuelve información sobre la columna especificada.|  
|[CSplitterWnd::GetPane](#getpane)|Devuelve el panel en la fila y columna especificadas.|  
|[CSplitterWnd::GetRowCount](#getrowcount)|Devuelve el recuento de filas del panel actual.|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|Devuelve información sobre la fila especificada.|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|Devuelve el estilo de barra de desplazamiento compartido.|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|Devuelve al elemento secundario Id. de la ventana del panel en la fila y columna especificadas.|  
|[CSplitterWnd::IsChildPane](#ischildpane)|Llamada para determinar si la ventana es actualmente un panel secundarios de esta ventana divisora.|  
|[CSplitterWnd::IsTracking](#istracking)|Determina si actualmente se está moviendo barra divisora.|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.|  
|[CSplitterWnd::SetActivePane](#setactivepane)|Establece un panel será el activo en el marco.|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|Llamada para establecer la información de la columna especificada.|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|Llamada para establecer la información de la fila especificada.|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|Especifica que el nuevo estilo de barra de desplazamiento de la ventana divisora compartido barras de desplazamiento.|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|Indica dónde se divide una ventana de marco verticalmente.|  
|[CSplitterWnd::SplitRow](#splitrow)|Indica que una ventana de marco se divide horizontalmente.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|Llamado por el marco para dibujar la ventana divisora.|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|Representa una imagen de una ventana dividida.|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|Presenta la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.|  
  
## <a name="remarks"></a>Comentarios  
 Un panel suele ser un objeto específico de la aplicación derivado de [CView](../../mfc/reference/cview-class.md), pero puede ser cualquier [CWnd](../../mfc/reference/cwnd-class.md) objeto que tiene el identificador de ventana de secundarios apropiados.  
  
 Un `CSplitterWnd` objeto normalmente está incrustado en un elemento primario [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto. Crear un `CSplitterWnd` objeto mediante los siguientes pasos:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.  
  
3.  Desde dentro de invalidado `OnCreateClient`, llame a la [crear](#create) o [CreateStatic](#createstatic) función miembro de `CSplitterWnd`.  
  
 Llame a la **crear** función de miembro para crear una ventana divisora dinámica. Normalmente, una ventana divisora dinámica se utiliza para crear y desplazarse a un número de paneles individuales o vistas del mismo documento. El marco de trabajo crea automáticamente un panel inicial del divisor; a continuación, el marco de trabajo crea, cambia el tamaño y elimina paneles adicionales de manera que el usuario los controles de la ventana divisora.  
  
 Cuando se llama a **crear**, especifique un mínimo de fila alto y ancho de columna que determinan cuándo los paneles son demasiado pequeños para mostrarse totalmente. Después de llamar a **crear**, puede ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro.  
  
 Utilice también el `SetColumnInfo` y `SetRowInfo` funciones miembro para establecer un ancho de una columna "ideal" y "ideal" alto de una fila. Cuando el marco de trabajo muestra una ventana divisora, muestra primero el marco primario, a continuación, en la ventana divisora. A continuación, el marco de trabajo presenta los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
 Todos los paneles en una ventana divisora dinámica deben ser de la misma clase. Aplicaciones conocidas que admiten ventanas divisoras dinámicas incluyen Microsoft Word y Microsoft Excel.  
  
 Utilice la `CreateStatic` función de miembro para crear una ventana divisora estática. El usuario puede cambiar sólo el tamaño de los paneles en un divisor estático, no su número o ventana orden.  
  
 Específicamente debe crear paneles de todos los divisora estática cuando se crea el divisor estático. Asegúrese de crear todos los paneles antes del marco primario `OnCreateClient` devuelve de la función de miembro o si el marco no se muestren correctamente la ventana.  
  
 El `CreateStatic` función miembro inicializa automáticamente un divisor estático con un mínimo de fila alto y ancho de columna de 0. Después de llamar a **crear**, ajustar estos mínimos mediante una llamada a la [SetColumnInfo](#setcolumninfo) y [SetRowInfo](#setrowinfo) funciones miembro. Usar `SetColumnInfo` y `SetRowInfo` después de llamar a `CreateStatic` para indicar deseada dimensiones del panel ideal.  
  
 Los paneles individuales de un divisor estático suelen pertenecen a diferentes clases. Para obtener ejemplos de ventanas divisoras estáticas, vea el editor de gráficos y el Administrador de archivos de Windows.  
  
 Una ventana divisora admite barras de desplazamiento especial (aparte de las barras de desplazamiento que pueden tener paneles). Estas barras de desplazamiento son elementos secundarios de la `CSplitterWnd` de objetos y se comparten con los paneles.  
  
 Crear estas barras de desplazamiento especial al crear la ventana divisora. Por ejemplo, un `CSplitterWnd` que tiene una fila, dos columnas y la **WS_VSCROLL** estilo mostrará una barra de desplazamiento vertical es compartida por los dos paneles. Cuando el usuario mueve la barra de desplazamiento `WM_VSCROLL` se envían mensajes a ambos paneles. Cuando los paneles establece la posición de la barra de desplazamiento, se establece la barra de desplazamiento compartido.  
  
 Para obtener más información sobre las ventanas divisoras, consulte:  
  
- [Nota técnica 29](../../mfc/tn029-splitter-windows.md)  
  
-   Artículo de Knowledge Base Q262024: HOWTO: CPropertySheet Use como un elemento secundario del objeto CSplitterWnd  
  
 Para obtener más información sobre cómo crear ventanas divisoras dinámicas, vea:  
  
-   Ejemplo de MFC [Scribble](../../visual-cpp-samples.md)  
  
-   Ejemplo de MFC [VIEWEX](../../visual-cpp-samples.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="a-nameactivatenexta--csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd::ActivateNext  
 Llamado por el marco de trabajo para realizar el comando panel siguiente o anterior.  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bPrev`  
 Indica qué ventana se active. **TRUE** para anterior; **FALSE** para el siguiente.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que usa el [CView](../../mfc/reference/cview-class.md) clase delegar a la `CSplitterWnd` implementación.  
  
##  <a name="a-namecanactivatenexta--csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd::CanActivateNext  
 Llamado por el marco de trabajo para comprobar si el comando panel siguiente o panel anterior es actualmente posible.  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bPrev`  
 Indica qué ventana se active. **TRUE** para anterior; **FALSE** para el siguiente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que usa el [CView](../../mfc/reference/cview-class.md) clase delegar a la `CSplitterWnd` implementación.  
  
##  <a name="a-namecreatea--csplitterwndcreate"></a><a name="create"></a>CSplitterWnd:: Create  
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
 `pParentWnd`  
 La ventana de marco principal de la ventana divisora.  
  
 *nMaxRows*  
 El número máximo de filas de la ventana divisora. Este valor no debe superar los 2.  
  
 *nMaxCols*  
 El número máximo de columnas de la ventana divisora. Este valor no debe superar los 2.  
  
 `sizeMin`  
 Especifica el tamaño mínimo en el que puede mostrarse un panel.  
  
 `pContext`  
 Un puntero a un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. En la mayoría de los casos, esto puede ser el `pContext` pasado a la ventana de marco principal.  
  
 `dwStyle`  
 Especifica el estilo de ventana.  
  
 `nID`  
 El identificador de ventana secundaria de la ventana. El identificador puede ser **AFX_IDW_PANE_FIRST** a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Puede incrustar un `CSplitterWnd` en una carpeta primaria [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto realizando los pasos siguientes:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro.  
  
3.  Llame a la **crear** función miembro dentro de invalidado `OnCreateClient`.  
  
 Cuando se crea una ventana divisora desde dentro de un marco primario, pasar el marco primario `pContext` parámetro a la ventana divisora. De lo contrario, este parámetro puede ser **NULL**.  
  
 Establecer el ancho de alto de columna y de fila mínimo inicial de una ventana divisora dinámica la `sizeMin` parámetro. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#125;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="a-namecreatescrollbarctrla--csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl  
 Llamado por el marco para crear un control de barra de desplazamiento compartido.  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo de ventana.  
  
 `nID`  
 El identificador de ventana secundaria de la ventana. El identificador puede ser **AFX_IDW_PANE_FIRST** a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar `CreateScrollBarCtrl` para incluir controles adicionales al lado de una barra de desplazamiento. El comportamiento predeterminado es crear controles de la barra de desplazamiento de Windows normales.  
  
##  <a name="a-namecreatestatica--csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd:: CreateStatic  
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
 `pParentWnd`  
 La ventana de marco principal de la ventana divisora.  
  
 `nRows`  
 Número de filas. Este valor no debe superar los 16.  
  
 *nCols*  
 Número de columnas. Este valor no debe superar los 16.  
  
 `dwStyle`  
 Especifica el estilo de ventana.  
  
 `nID`  
 El identificador de ventana secundaria de la ventana. El identificador puede ser **AFX_IDW_PANE_FIRST** a menos que la ventana divisora está anidada dentro de otra ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Un `CSplitterWnd` normalmente está incrustado en un elemento primario `CFrameWnd` o [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) objeto realizando los pasos siguientes:  
  
1.  Incrustar un `CSplitterWnd` variable miembro en el marco primario.  
  
2.  Invalidar el marco primario `OnCreateClient` función miembro.  
  
3.  Llame a la `CreateStatic` función miembro dentro de invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient).  
  
 Una ventana divisora estática contiene un número fijo de paneles, a menudo de diferentes clases.  
  
 Cuando se crea una ventana divisora estática, debe al mismo tiempo crear todos sus paneles. El [CreateView](#createview) función miembro se suele utilizar para este propósito, pero puede crear también otras clases nonview.  
  
 El mínimo de fila inicial alto y ancho de columna para una ventana divisora estática es 0. Estas cantidades mínimas, que determinan si un panel es demasiado pequeño para mostrarse en su totalidad, se pueden cambiar con el [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro.  
  
 Para agregar barras de desplazamiento a una ventana divisora estática, agregue el **WS_HSCROLL** y **WS_VSCROLL** estilos `dwStyle`.  
  
 Consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase para obtener más información sobre la ventana divisora estática.  
  
##  <a name="a-namecreateviewa--csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd:: CreateView  
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
 `row`  
 Especifica la fila de la ventana divisora donde desea colocar la nueva vista.  
  
 `col`  
 Especifica la columna de la ventana divisora donde desea colocar la nueva vista.  
  
 `pViewClass`  
 Especifica la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) de la nueva vista.  
  
 *sizeInit*  
 Especifica el tamaño inicial de la nueva vista.  
  
 `pContext`  
 Un puntero a un contexto de creación que se usa para crear la vista (normalmente la `pContext` pasado en el marco primario invalidado [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient) función miembro en el que se crea la ventana divisora).  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Todos los paneles de una ventana divisora estática deben crearse antes de que el marco de trabajo muestra el divisor.  
  
 El marco también llama a esta función miembro para crear paneles de nuevo cuando el usuario de una ventana divisora dinámica divide un panel, fila o columna.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&4;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="a-namecsplitterwnda--csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd  
 Llamada a construir un `CSplitterWnd` objeto.  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Construir un `CSplitterWnd` objeto en dos pasos. En primer lugar, llame al constructor, que crea el `CSplitterWnd` de objetos y, a continuación, llame a la [crear](#create) función miembro, que crea la ventana divisora y lo adjunta a la `CSplitterWnd` objeto.  
  
##  <a name="a-namedeletecolumna--csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd::DeleteColumn  
 Elimina una columna de la ventana divisora.  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 *colDelete*  
 Especifica la columna que desea eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene la **SPLS_DYNAMIC_SPLIT** estilo). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.  
  
##  <a name="a-namedeleterowa--csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd::DeleteRow  
 Elimina una fila de la ventana divisora.  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 *filaEliminar*  
 Especifica la fila que se va a eliminar.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene la **SPLS_DYNAMIC_SPLIT** estilo). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.  
  
##  <a name="a-namedeleteviewa--csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd::DeleteView  
 Elimina una vista de la ventana divisora.  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Especifica la fila de la ventana divisora en la que se va a eliminar la vista.  
  
 `col`  
 Especifica la columna de la ventana divisora en la que se va a eliminar la vista.  
  
### <a name="remarks"></a>Comentarios  
 Si se elimina la vista activa, se activará la vista siguiente. La implementación predeterminada supone automáticamente la vista de la eliminación en [PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy).  
  
 Esta función miembro se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene la **SPLS_DYNAMIC_SPLIT** estilo). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.  
  
##  <a name="a-namedokeyboardsplita--csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit  
 Realiza el teclado dividir el comando, normalmente "división de ventana".  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro es un comando de alto nivel que usa el [CView](../../mfc/reference/cview-class.md) clase delegar a la `CSplitterWnd` implementación.  
  
##  <a name="a-namedoscrolla--csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd::DoScroll  
 Realiza el desplazamiento sincronizado de ventanas de división.  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pViewFrom`  
 Puntero a la vista del que procede el mensaje de desplazamiento.  
  
 `nScrollCode`  
 Se desplaza en un código de barras de desplazamiento que indica al usuario la solicitud. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produzca horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produzca vertical:  
  
- **SB_BOTTOM** se desplaza hacia abajo.  
  
- **SB_LINEDOWN** se desplaza una línea hacia abajo.  
  
- **SB_LINEUP** sube una línea.  
  
- **SB_PAGEDOWN** se desplaza una página hacia abajo.  
  
- **SB_PAGEUP** desplaza una página hacia arriba.  
  
- **SB_TOP** se desplaza a la parte superior.  
  
 `bDoScroll`  
 Determina si se produce la acción de desplazamiento especificada. Si `bDoScroll` es **TRUE** (es decir, si existe una ventana secundaria y la división de windows tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si `bDoScroll` es **FALSE** (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen ningún intervalo de desplazamiento), no se produzca el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se produce el desplazamiento sincronizado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para realizar un desplazamiento sincronizado de división windows cuando la vista recibe un mensaje de desplazamiento. Invalidación para requerir una acción del usuario antes de que se permite el desplazamiento sincronizado.  
  
##  <a name="a-namedoscrollbya--csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd::DoScrollBy  
 Desplaza ventanas divididas un número determinado de píxeles.  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pViewFrom`  
 Puntero a la vista del que procede el mensaje de desplazamiento.  
  
 `sizeScroll`  
 Número de píxeles de desplazamiento horizontal y verticalmente.  
  
 bDoScroll  
 Determina si se produce la acción de desplazamiento especificada. Si `bDoScroll` es **TRUE** (es decir, si existe una ventana secundaria y la división de windows tienen un intervalo de desplazamiento), a continuación, la acción de desplazamiento especificada puede tener lugar; si `bDoScroll` es **FALSE** (es decir, si no existe ninguna ventana secundaria o las vistas divididas no tienen ningún intervalo de desplazamiento), no se produzca el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se produce el desplazamiento sincronizado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a esta función miembro por el marco de trabajo en respuesta a un mensaje de desplazamiento, para realizar la sincronización de desplazamiento de la división de windows por la cantidad, en píxeles, indicado por `sizeScroll`. Los valores positivos indican el desplazamiento hacia abajo y a la derecha. los valores negativos indican el desplazamiento hacia arriba y hacia la izquierda.  
  
 Invalidar para requerir la intervención del usuario antes de permitir el desplazamiento.  
  
##  <a name="a-namegetactivepanea--csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd::GetActivePane  
 Determina el panel activo del foco o la vista activa en el marco.  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pRow`  
 Un puntero a un **int** para recuperar el número de fila de la sección activa.  
  
 `pCol`  
 Un puntero a un **int** para recuperar el número de columna del panel activo.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero para el panel activo. **NULL** si no existe ningún panel activo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para determinar el panel activo en una ventana divisora. Invalidar para requerir la intervención del usuario antes de obtener el panel activo.  
  
##  <a name="a-namegetcolumncounta--csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd::GetColumnCount  
 Devuelve el número de columnas del panel actual.  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número actual de columnas en el divisor. Para un divisor estático, también será el número máximo de columnas.  
  
##  <a name="a-namegetcolumninfoa--csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo  
 Devuelve información sobre la columna especificada.  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `col`  
 Especifica una columna.  
  
 *cxCur*  
 Una referencia a un `int` se establece en el ancho actual de la columna.  
  
 `cxMin`  
 Una referencia a un `int` para establecer el ancho mínimo actual de la columna.  
  
##  <a name="a-namegetpanea--csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd::GetPane  
 Devuelve el panel en la fila y columna especificadas.  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Especifica una fila.  
  
 `col`  
 Especifica una columna.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el panel en la fila y columna especificadas. El panel devuelto es normalmente un [CView](../../mfc/reference/cview-class.md)-clase derivada.  
  
##  <a name="a-namegetrowcounta--csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd::GetRowCount  
 Devuelve el recuento de filas del panel actual.  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número actual de filas de la ventana divisora. Para una ventana divisora estática, también será el número máximo de filas.  
  
##  <a name="a-namegetrowinfoa--csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd::GetRowInfo  
 Devuelve información sobre la fila especificada.  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Especifica una fila.  
  
 `cyCur`  
 Referencia a `int` se establece en el alto actual de la fila en píxeles.  
  
 `cyMin`  
 Referencia a `int` se establece en el alto mínimo actual de la fila en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para obtener información acerca de la fila especificada. El `cyCur` parámetro se rellena con el alto actual de la fila especificada, y `cyMin` se rellena con el alto mínimo de la fila.  
  
##  <a name="a-namegetscrollstylea--csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle  
 Devuelve el estilo de barra de desplazamiento compartido de la ventana divisora.  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno o más de las siguientes ventanas de estilo indicadores, si se realiza correctamente:  
  
- **WS_HSCROLL** si el divisor actualmente administra las barras de desplazamiento horizontal compartida.  
  
- **WS_VSCROLL** si el divisor actualmente administra las barras de desplazamiento vertical compartido.  
  
 Si es cero, la ventana divisora no administra actualmente todas las barras de desplazamiento compartido.  
  
##  <a name="a-nameidfromrowcola--csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol  
 Obtiene al elemento secundario identificador de ventana para el panel en la fila y columna especificadas.  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Especifica la fila de la ventana divisora.  
  
 `col`  
 Especifica la columna de la ventana divisora.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de ventana secundaria para el panel.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se usa para crear nonviews como paneles y se puede llamar antes de que exista el panel.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#5;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="a-nameischildpanea--csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd::IsChildPane  
 Determina si `pWnd` es actualmente un panel secundarios de esta ventana divisora.  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWnd`  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto se va a probar.  
  
 `pRow`  
 Un puntero a un `int` para almacenar el número de fila.  
  
 `pCol`  
 Un puntero a un `int` para almacenar un número de columna.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es distinto de cero, `pWnd` actualmente es un panel secundarios de esta ventana divisora, y `pRow` y `pCol` se rellena con la posición del panel en la ventana divisora. Si `pWnd` no es un panel secundarios de esta ventana divisora, se devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 En versiones de Visual C++ anteriores a 6.0, esta función se define como  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 Esta versión ahora está obsoleta y no debe usarse.  
  
##  <a name="a-nameistrackinga--csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd::IsTracking  
 Llame a esta función miembro para determinar si la barra de división en la ventana se está moviendo actualmente.  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si una operación de divisor está en curso; en caso contrario, 0.  
  
##  <a name="a-nameondrawsplittera--csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter  
 Representa una imagen de una ventana dividida.  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero al contexto de dispositivo en el que se va a dibujar. Si `pDC` es **NULL**, a continuación, [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) se llama el marco de trabajo y sin división se dibuja la ventana.  
  
 `nType`  
 Un valor de la **enum ESplitType**, que puede ser uno de los siguientes:  
  
- **splitBox** el divisor arrastre el cuadro.  
  
- `splitBar`La barra que aparece entre las ventanas de la división de dos.  
  
- **splitIntersection** la intersección de la división de windows. Este elemento no se llamará cuando se ejecuta en Windows 95 ó 98.  
  
- **splitBorder** los bordes de la ventana de división.  
  
 `rect`  
 Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el tamaño y la forma de la división de windows.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para dibujar y especificar las características exactas de una ventana divisora. Reemplazar `OnDrawSplitter` para la personalización avanzada de las imágenes para los distintos componentes gráficos de una ventana divisora. Las imágenes de forma predeterminada es similar al divisor en Microsoft Works para Windows o Microsoft Windows 95 ó 98, en que se fusionen las intersecciones de las barras de división.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
##  <a name="a-nameoninverttrackera--csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker  
 Presenta la imagen de una ventana dividida para que tenga el mismo tamaño y forma que la ventana de marco.  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 `rect`  
 Hacer referencia a un `CRect` objeto que especifica el rectángulo de seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función miembro durante el cambio de tamaño de los separadores. Reemplazar `OnInvertTracker` para la personalización avanzada de las imágenes de la ventana divisora. Las imágenes de forma predeterminada es similar al divisor en Microsoft Works para Windows o Microsoft Windows 95 ó 98, en que se fusionen las intersecciones de las barras de división.  
  
 Para obtener más información sobre las ventanas divisoras dinámicas, consulte "Ventanas divisoras" en el artículo [varios tipos de documentos, vistas y ventanas de marco](../../mfc/multiple-document-types-views-and-frame-windows.md), [29 de nota técnica](../../mfc/tn029-splitter-windows.md)y el `CSplitterWnd` general sobre la clase.  
  
##  <a name="a-namerecalclayouta--csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd::RecalcLayout  
 Llamada a volver a mostrar la ventana divisora después de ajustar el tamaño de fila o columna.  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para volver a mostrar correctamente la ventana divisora después de ajustar los tamaños de fila y columna con la [SetRowInfo](#setrowinfo) y [SetColumnInfo](#setcolumninfo) funciones miembro. Si cambia los tamaños de fila y columna como parte del proceso de creación antes de la ventana divisora está visible, no es necesario llamar a esta función miembro.  
  
 El marco de trabajo llama a esta función miembro siempre que el usuario cambia el tamaño de la ventana divisora o mueve una división.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CSplitterWnd::SetColumnInfo](#setcolumninfo).  
  
##  <a name="a-namesetactivepanea--csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd::SetActivePane  
 Establece un panel será el activo en el marco.  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Si `pWnd` es **NULL**, especifica la fila en el panel que se encuentre activo.  
  
 `col`  
 Si `pWnd` es **NULL**, especifica la columna en el panel que se encuentre activo.  
  
 `pWnd`  
 Un puntero a un `CWnd` objeto. Si **NULL**, el panel especificado por `row` y `col` se establece en activo. Si no **NULL**, especifica el panel que se establece en activo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama el marco de trabajo para establecer un panel como activo cuando el usuario cambia el foco a un panel dentro de la ventana de marco. Se puede llamar explícitamente `SetActivePane` para cambiar el foco a la vista especificada.  
  
 Especificar panel proporcionando la fila y columna, **o** proporcionando `pWnd`.  
  
##  <a name="a-namesetcolumninfoa--csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo  
 Llamada para establecer la información de la columna especificada.  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>Parámetros  
 `col`  
 Especifica una columna de la ventana divisora.  
  
 *cxIdeal*  
 Especifica un ancho ideal de la columna de la ventana de divisor en píxeles.  
  
 `cxMin`  
 Especifica el ancho mínimo de la columna de la ventana de divisor en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para establecer un nuevo ancho mínimo y el ancho ideal de una columna. El valor mínimo de la columna determina si la columna será demasiado pequeña para mostrarse totalmente.  
  
 Cuando el marco de trabajo muestra la ventana divisora, presenta los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&6;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="a-namesetrowinfoa--csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd::SetRowInfo  
 Llamada para establecer la información de la fila especificada.  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>Parámetros  
 `row`  
 Especifica una fila de la ventana divisora.  
  
 *cyIdeal*  
 Especifica un alto ideal de la fila de la ventana de divisor en píxeles.  
  
 `cyMin`  
 Especifica un alto mínimo de la fila de la ventana de divisor en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función miembro para establecer un nuevo alto mínimo y alto ideal de una fila. El valor mínimo de fila determina cuándo será demasiado pequeña que se muestre la fila.  
  
 Cuando el marco de trabajo muestra la ventana divisora, presenta los paneles en columnas y filas según sus dimensiones ideales, trabajando desde la superior izquierda a la esquina inferior derecha del área de cliente de la ventana divisora.  
  
##  <a name="a-namesetscrollstylea--csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle  
 Especifica que el nuevo estilo de desplazamiento de la ventana divisora compartido barras de desplazamiento.  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 El nuevo estilo de desplazamiento de la ventana divisora compartidas de compatibilidad de la barra de desplazamiento, que puede ser uno de los siguientes valores:  
  
- **WS_HSCROLL** crear o mostrar horizontal compartida barras de desplazamiento.  
  
- **WS_VSCROLL** crear o mostrar vertical compartido barras de desplazamiento.  
  
### <a name="remarks"></a>Comentarios  
 Una vez creada una barra de desplazamiento no se destruirán aun cuando `SetScrollStyle` se llama sin ese estilo; en su lugar, se ocultan las barras de desplazamiento. Esto permite que las barras de desplazamiento conservar su estado, aunque están ocultos. Después de llamar a `SetScrollStyle` es necesario llamar a [RecalcLayout](#recalclayout) para todos los cambios surtan efecto.  
  
##  <a name="a-namesplitcolumna--csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd::SplitColumn  
 Indica dónde se divide una ventana de marco verticalmente.  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>Parámetros  
 *cxBefore*  
 La posición, en píxeles, antes de que se produce la división.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama cuando se crea una ventana divisora vertical. `SplitColumn`indica la ubicación predeterminada donde se produce la división.  
  
 `SplitColumn`se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene la **SPLS_DYNAMIC_SPLIT** estilo). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.  
  
##  <a name="a-namesplitrowa--csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd::SplitRow  
 Indica que una ventana de marco se divide horizontalmente.  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>Parámetros  
 *cyBefore*  
 La posición, en píxeles, antes de que se produce la división.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se llama cuando se crea una ventana divisora horizontal. `SplitRow`indica la ubicación predeterminada donde se produce la división.  
  
 `SplitRow`se llama el marco de trabajo para implementar la lógica de la ventana divisora dinámica (es decir, si la ventana divisora tiene la **SPLS_DYNAMIC_SPLIT** estilo). Se puede personalizar, junto con la función virtual [CreateView](#createview), para implementar los divisores dinámicos más avanzados.  
  
##  <a name="a-nameondrawa--csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd::OnDraw  
 Llamado por el marco para dibujar la ventana divisora.  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC VIEWEX](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CView (clase)](../../mfc/reference/cview-class.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)

