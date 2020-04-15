---
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 0a6b0cf39861ba995acff71fc40cf44ae5114642
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367457"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

La `CMFCHeaderCtrl` clase admite ordenar varias columnas en un control de encabezado.

## <a name="syntax"></a>Sintaxis

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Construye un objeto `CMFCHeaderCtrl`.|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita o deshabilita el modo de *ordenación* de varias columnas para el control de encabezado actual.|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indica si una columna no está ordenada o está ordenada en orden ascendente o descendente.|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Recupera el índice de base cero de la primera columna ordenada en el control de encabezado.|
|`CMFCHeaderCtrl::GetThisClass`|Utilizado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indica si alguna columna del control de encabezado se ordena en orden ascendente.|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indica si la ventana primaria del control de encabezado actual es un cuadro de diálogo.|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indica si el control de encabezado actual está en modo de ordenación de *varias columnas.*|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Quita la columna especificada de la lista de columnas de ordenación.|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Establece el criterio de ordenación de una columna especificada en un control de encabezado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Llamado por el marco de trabajo para dibujar una columna de control de encabezado.|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Llamado por el marco de trabajo para dibujar la flecha de ordenación.|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Llamado por el marco de trabajo para rellenar el fondo de una columna de control de encabezado.|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCHeaderCtrl` cómo construir un objeto de la clase y cómo habilitar el modo de *ordenación* de varias columnas para el control de encabezado actual.

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Observaciones

La `CMFCHeaderCtrl` clase dibuja una flecha de ordenación en una columna de control de encabezado para indicar que la columna está ordenada. Utilice el modo de *ordenación* de varias columnas si un conjunto de columnas en el control de lista primario ( [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md)se puede ordenar al mismo tiempo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxheaderctrl.h

## <a name="cmfcheaderctrlcmfcheaderctrl"></a><a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl

Construye un objeto `CMFCHeaderCtrl`.

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Observaciones

Este constructor inicializa las siguientes variables miembro en los valores especificados:

|Variable miembro|Value|
|---------------------|-----------|
|`m_bIsMousePressed`|FALSE|
|`m_bMultipleSort`|FALSE|
|`m_bAscending`|TRUE|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|FALSE|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

## <a name="cmfcheaderctrlenablemultiplesort"></a><a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort

Habilita o deshabilita el modo de *ordenación* de varias columnas para el control de encabezado actual.

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar el modo de ordenación de varias columnas; FALSE para deshabilitar el modo de ordenación de varias columnas y quitar las columnas de la lista de columnas ordenadas. El valor predeterminado es TRUE.

### <a name="remarks"></a>Observaciones

Utilice este método para habilitar o deshabilitar el modo de ordenación de varias columnas. Dos o más columnas pueden participar en una ordenación si el control de encabezado está en modo de ordenación de varias columnas.

## <a name="cmfcheaderctrlgetcolumnstate"></a><a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState

Indica si una columna no está ordenada o está ordenada en orden ascendente o descendente.

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[en] El índice de base cero de una columna.

### <a name="return-value"></a>Valor devuelto

Valor que indica el estado de ordenación de la columna especificada. En la tabla siguiente, se ofrecen los valores posibles:

|Value|Descripción|
|-----------|-----------------|
|-1|Ordenado en orden descendente.|
|0|No ordenado.|
|1|Ordenado en orden ascendente.|

### <a name="remarks"></a>Observaciones

## <a name="cmfcheaderctrlgetsortcolumn"></a><a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn

Recupera el índice de base cero de la primera columna ordenada en el control de encabezado.

```
int GetSortColumn() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de una columna ordenada, o -1 si no se encuentra ninguna columna ordenada.

### <a name="remarks"></a>Observaciones

Si el control de encabezado está en modo de *ordenación* de varias columnas y compiló la aplicación en modo de depuración, este método afirma y le aconseja que utilice el [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) método en su lugar. Si el control de encabezado está en modo de ordenación de varias columnas y ha compilado la aplicación en modo comercial, este método devuelve -1.

## <a name="cmfcheaderctrlisascending"></a><a name="isascending"></a>CMFCHeaderCtrl::IsAscending

Indica si alguna columna del control de encabezado se ordena en orden ascendente.

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi cualquier columna del control de encabezado se ordena en orden ascendente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El valor que devuelve este método se utiliza para mostrar la flecha de ordenación adecuada en el elemento de control de encabezado. Utilice el [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) método para establecer el criterio de ordenación.

## <a name="cmfcheaderctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl

Indica si la ventana primaria del control de encabezado actual es un cuadro de diálogo.

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana primaria del control de encabezado actual es un cuadro de diálogo; de lo contrario, FALSE.

## <a name="cmfcheaderctrlismultiplesort"></a><a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort

Indica si el control de encabezado actual está en modo de ordenación de *varias columnas.*

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el modo de ordenación de varias columnas está habilitado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Utilice el [método CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) para habilitar o deshabilitar el modo de ordenación de varias columnas. Dos o más columnas pueden participar en una ordenación si el control de encabezado está en modo de ordenación de varias columnas.

## <a name="cmfcheaderctrlondrawitem"></a><a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem

Llamado por el marco de trabajo para dibujar una columna de control de encabezado.

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*iItem*<br/>
[en] El índice de base cero del elemento que se va a dibujar.

*Rect*<br/>
[en] El rectángulo delimitador del elemento que se va a dibujar.

*bIsPressed*<br/>
[en] TRUE para dibujar el elemento en estado presionado; de lo contrario, FALSE.

*bIsHighlighted*<br/>
[en] TRUE para dibujar el elemento en estado resaltado; de lo contrario, FALSE.

## <a name="cmfcheaderctrlondrawsortarrow"></a><a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow

Llamado por el marco de trabajo para dibujar la flecha de ordenación.

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*rectArrow*<br/>
[en] El rectángulo delimitador de la flecha de ordenación.

## <a name="cmfcheaderctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground

Llamado por el marco de trabajo para rellenar el fondo de una columna de control de encabezado.

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

### <a name="remarks"></a>Observaciones

## <a name="cmfcheaderctrlremovesortcolumn"></a><a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn

Quita la columna especificada de la lista de columnas de ordenación.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[en] El índice de base cero de la columna que se va a quitar.

## <a name="cmfcheaderctrlsetsortcolumn"></a><a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn

Establece el criterio de ordenación de una columna especificada en un control de encabezado.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[en] El índice de base cero de una columna de control de encabezado. Si este parámetro es menor que cero, este método quita todas las columnas de la lista de columnas de ordenación.

*bAscending*<br/>
[en] Especifica el criterio de ordenación de la columna que especifica el parámetro *iColumn.* TRUE para establecer el orden ascendente; FALSE para establecer el orden descendente. El valor predeterminado es TRUE.

*Bagregar*<br/>
[en] TRUE para establecer el criterio de ordenación de la columna que especifica el parámetro *iColumn.*

Si el control de encabezado actual está en modo de ordenación de *varias columnas,* este método agrega la columna especificada a la lista de columnas de ordenación. Utilice [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) para establecer el modo de ordenación de varias columnas.

Si no se establece el modo de ordenación de varias columnas y este método se compila en modo de depuración, este método afirma. Si no se establece el modo de ordenación de varias columnas y este método se compila en modo comercial, este método quita primero todas las columnas de la lista de columnas de ordenación y, a continuación, agrega la columna especificada a la lista.

FALSE para quitar primero todas las columnas de la lista de columnas de ordenación y, a continuación, agregue la columna especificada a la lista. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

Utilice este método para establecer el criterio de ordenación de una columna. Si es necesario, este método agrega la columna a la lista de columnas de ordenación. El control de encabezado utiliza el criterio de ordenación para dibujar una flecha de ordenación que apunta hacia arriba o hacia abajo.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)
