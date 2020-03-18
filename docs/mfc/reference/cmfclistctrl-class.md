---
title: Clase CMFCListCtrl
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425824"
---
# <a name="cmfclistctrl-class"></a>Clase CMFCListCtrl

La clase `CMFCListCtrl` amplía la funcionalidad de la clase de [clase CListCtrl](../../mfc/reference/clistctrl-class.md) al admitir la funcionalidad de control de encabezado avanzado de la [clase CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Sintaxis

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Habilita la capacidad de marcar una columna ordenada con un color de fondo diferente.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita el modo de ordenación múltiple.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Devuelve una referencia al control de encabezado subrayado.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Comprueba si el control de lista está en modo de ordenación múltiple.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Lo llama el marco de trabajo cuando debe comparar dos elementos de control de lista.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Lo llama el marco de trabajo cuando debe determinar el color de fondo de una celda individual.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Lo llama el marco de trabajo cuando debe obtener la fuente para la celda que se está dibujando.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Lo llama el marco de trabajo cuando debe determinar el color del texto de una celda individual.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Quita una columna de ordenación de la lista de columnas ordenadas.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Establece la columna ordenada actual y el criterio de ordenación.|
|[CMFCListCtrl:: Sort](#sort)|Ordena el control de lista.|

## <a name="remarks"></a>Observaciones

`CMFCListCtrl` ofrece dos mejoras a la clase [CListCtrl](../../mfc/reference/clistctrl-class.md) . En primer lugar, indica que la ordenación de las columnas es una opción disponible dibujando automáticamente una flecha de ordenación en el encabezado. En segundo lugar, admite la ordenación de datos en varias columnas al mismo tiempo.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCListCtrl` . En el ejemplo se muestra cómo se crea un control de lista, se insertan columnas, se insertan elementos, se establece el texto de un elemento y se establece la fuente del control de lista. Este fragmento de código forma parte del [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxlistctrl. h

##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn

Marca las columnas ordenadas con un color de fondo diferente.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMark*<br/>
de Parámetro booleano que determina si se va a habilitar un color de fondo diferente.

*bRedraw*<br/>
de Parámetro booleano que determina si se debe volver a dibujar el control inmediatamente.

### <a name="remarks"></a>Observaciones

`EnableMarkSortedColumn` utiliza el método `CDrawingManager::PixelAlpha` para calcular el color que se va a usar para las columnas ordenadas. El color seleccionado se basa en el color de fondo normal.

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

Permite ordenar las filas de datos del control de lista por varias columnas.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de Valor booleano que especifica si se va a habilitar el modo de ordenación de varias columnas.

### <a name="remarks"></a>Observaciones

Al habilitar la ordenación basada en varias columnas, las columnas tienen una jerarquía. Las filas de datos se ordenarán primero por la columna principal. Después, los valores equivalentes se ordenan por cada columna subsiguiente según la prioridad.

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

Devuelve una referencia al control de encabezado.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Valor devuelto

Referencia al objeto [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) subyacente.

### <a name="remarks"></a>Observaciones

El control de encabezado de un control de lista es la ventana que contiene los títulos de las columnas. Normalmente se coloca directamente encima de las columnas.

##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort

Comprueba si el control de lista admite actualmente la ordenación en varias columnas.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control de lista admite la ordenación múltiple; De lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Cuando una [clase CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md) admite varias ordenaciones, el usuario puede ordenar los datos del control de lista por varias columnas. Para habilitar la ordenación múltiple, llame a [CMFCListCtrl:: EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems

El marco de trabajo llama a este método cuando compara dos elementos.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parámetros

*lParam1*<br/>
de Primer elemento que se va a comparar.

*lParam2*<br/>
de Segundo elemento que se va a comparar.

*iColumn*<br/>
de Índice de la columna que este método está ordenando.

### <a name="return-value"></a>Valor devuelto

Entero que indica la posición relativa de los dos elementos. Un valor negativo indica que el primer elemento debe preceder al segundo, un valor positivo indica que el primer elemento debe seguir al segundo y cero significa que los dos elementos son equivalentes.

### <a name="remarks"></a>Observaciones

La implementación predeterminada siempre devuelve 0. Invalide esta función para proporcionar su propio algoritmo de ordenación.

##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor

El marco de trabajo llama a este método cuando debe determinar el color de fondo de una celda individual.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
de Fila de la celda en cuestión.

*nColumn*<br/>
de Columna de la celda en cuestión.

### <a name="return-value"></a>Valor devuelto

Valor COLOREF que especifica el color de fondo de la celda.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de `OnGetCellBkColor` no utiliza los parámetros de entrada proporcionados y, en su lugar, simplemente llama a `GetBkColor`. Por lo tanto, de forma predeterminada, todo el control de lista tendrá el mismo color de fondo. Puede invalidar `OnGetCellBkColor` en una clase derivada para marcar celdas individuales con un color de fondo independiente.

##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont

El marco de trabajo llama a este método cuando obtiene la fuente para una celda individual.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
de Fila de la celda en cuestión.

*nColumn*<br/>
de Columna de la celda en cuestión.

*dwData*<br/>
de Datos definidos por el usuario. La implementación predeterminada no usa este parámetro.

### <a name="return-value"></a>Valor devuelto

Identificador de la fuente que se utiliza para la celda actual.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método devuelve NULL. Todas las celdas de un control de lista tienen la misma fuente. Invalide este método para proporcionar fuentes diferentes para las distintas celdas.

##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor

El marco de trabajo llama a este método cuando debe determinar el color de texto de una celda individual.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
de Fila de la celda en cuestión.

*nColumn*<br/>
de Columna de la celda en cuestión.

### <a name="return-value"></a>Valor devuelto

Valor COLOREF que especifica el color del texto de la celda.

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método llama a `GetTextColor` independientemente de los parámetros de entrada. Todo el control de lista tendrá el mismo color de texto. Puede invalidar `OnGetCellTextColor` en una clase derivada para marcar celdas individuales con un color de texto independiente.

##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn

Quita una columna de ordenación de la lista de columnas ordenadas.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
de Columna que se va a quitar.

### <a name="remarks"></a>Observaciones

Este método quita una columna de ordenación del control de encabezado. Llama a [CMFCHeaderCtrl:: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn

Establece la columna ordenada actual y el criterio de ordenación.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
de Columna que se va a ordenar.

*bAscending*<br/>
de Valor booleano que especifica el criterio de ordenación.

*bAgregar*<br/>
de Un valor booleano que especifica si el método agrega la columna indicada por *iColumn* a la lista de columnas de ordenación.

### <a name="remarks"></a>Observaciones

Este método pasa los parámetros de entrada al control de encabezado usando el método [CMFCHeaderCtrl:: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>CMFCListCtrl:: Sort

Ordena el control de lista.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
de Columna que se va a ordenar.

*bAscending*<br/>
de Valor booleano que especifica el criterio de ordenación.

*bAgregar*<br/>
de Un valor booleano que especifica si este método agrega la columna indicada por *iColumn* a la lista de columnas de ordenación.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
