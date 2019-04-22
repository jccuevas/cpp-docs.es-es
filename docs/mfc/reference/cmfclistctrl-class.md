---
title: CMFCListCtrl (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: 4cd1bb7787f8797984bdce5f9a5b3080d69ea5f2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58767943"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl (clase)

El `CMFCListCtrl` clase extiende la funcionalidad de [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase proporcionando la funcionalidad de control avanzado de encabezado de la [clase CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).

## <a name="syntax"></a>Sintaxis

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Permite la capacidad de marcar una columna ordenada con un color de fondo diferente.|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita el modo de ordenación de varias.|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Devuelve una referencia al control de encabezado subrayado.|
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Comprueba si el control de lista está en modo de ordenación múltiple.|
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Lo llama el marco de trabajo cuando deben comparar dos elementos de control de lista.|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Lo llama el marco cuando debe determinar el color de fondo de una celda individual.|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Lo llama el marco de trabajo cuando debe obtener la fuente de la celda que se va a dibujar.|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Lo llama el marco cuando debe determinar el color del texto de una celda individual.|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Quita una columna de ordenación de la lista de columnas ordenadas.|
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Establece la columna ordenada actual y el criterio de ordenación.|
|[CMFCListCtrl::Sort](#sort)|Ordena el control de lista.|

## <a name="remarks"></a>Comentarios

`CMFCListCtrl` ofrece dos mejoras para [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase. En primer lugar, indica que la ordenación de columnas es una opción disponible dibujando automáticamente una flecha de ordenación en el encabezado. En segundo lugar, es compatible con los datos en varias columnas de ordenación al mismo tiempo.

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCListCtrl` . El ejemplo muestra cómo crear un control de lista, insertar columnas, insertar elementos, establezca el texto de un elemento y establezca la fuente del control de lista. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxlistctrl.h

##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn

Marca las columnas ordenadas con un color de fondo diferente.

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMark*<br/>
[in] Un parámetro booleano que determina si se debe habilitar un color de fondo diferente.

*bRedraw*<br/>
[in] Un parámetro booleano que determina si se debe dibujar el control inmediatamente.

### <a name="remarks"></a>Comentarios

`EnableMarkSortedColumn` usa el método `CDrawingManager::PixelAlpha` calcular el color que se utilizará para ordena las columnas. El color elegido se basa en el color de fondo normal.

##  <a name="enablemultiplesort"></a>  CMFCListCtrl::EnableMultipleSort

Permite ordenar las filas de datos en el control de lista por varias columnas.

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
[in] Valor booleano que especifica si se debe habilitar el modo de ordenación de varias columnas.

### <a name="remarks"></a>Comentarios

Al habilitar la ordenación según varias columnas, las columnas tienen una jerarquía. Las filas de datos se ordenarán primero por la columna principal. Los valores equivalentes, a continuación, se ordenan por cada columna subsiguientes según la prioridad.

##  <a name="getheaderctrl"></a>  CMFCListCtrl::GetHeaderCtrl

Devuelve una referencia al control de encabezado.

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>Valor devuelto

Una referencia subyacente [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objeto.

### <a name="remarks"></a>Comentarios

El control de encabezado para un control de lista es la ventana que contiene los títulos de las columnas. Normalmente, se coloca directamente encima de las columnas.

##  <a name="ismultiplesort"></a>  CMFCListCtrl::IsMultipleSort

Comprueba si el control de lista actualmente admite la ordenación en varias columnas.

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el control de lista admite a la ordenación de varias; FALSE en caso contrario.

### <a name="remarks"></a>Comentarios

Cuando un [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md) admite la ordenación de varias, el usuario puede ordenar los datos en el control de lista por varias columnas. Para habilitar la ordenación de varias, llame a [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).

##  <a name="oncompareitems"></a>  CMFCListCtrl::OnCompareItems

El marco llama a este método cuando compara dos elementos.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Parámetros

*lParam1*<br/>
[in] El primer elemento para comparar.

*lParam2*<br/>
[in] El segundo elemento para comparar.

*iColumn*<br/>
[in] El índice de la columna que se está ordenando este método.

### <a name="return-value"></a>Valor devuelto

Un entero que indica la posición relativa de los dos elementos. Un valor negativo indica que el primer elemento debería preceder al segundo, valor positivo indica que el primer elemento debería seguir al segundo, y cero significa que los dos elementos son equivalentes.

### <a name="remarks"></a>Comentarios

La implementación predeterminada siempre devuelve 0. Se debe reemplazar esta función para proporcionar un algoritmo de ordenación.

##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor

El marco llama a este método cuando debe determinar el color de fondo de una celda individual.

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
[in] La fila de la celda en cuestión.

*nColumn*<br/>
[in] La columna de la celda en cuestión.

### <a name="return-value"></a>Valor devuelto

Un valor COLOREF que especifica el color de fondo de la celda.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de `OnGetCellBkColor` no usa los parámetros de entrada proporcionados y en su lugar, simplemente llama a `GetBkColor`. Por lo tanto, de forma predeterminada, el control de lista todo tendrá el mismo color de fondo. Puede invalidar `OnGetCellBkColor` en una clase derivada para marcar las celdas individuales con un color de fondo independientes.

##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont

El marco llama a este método cuando obtiene la fuente de una celda individual.

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
[in] La fila de la celda en cuestión.

*nColumn*<br/>
[in] La columna de la celda en cuestión.

*dwData*<br/>
[in] Datos definidos por el usuario. La implementación predeterminada no utiliza este parámetro.

### <a name="return-value"></a>Valor devuelto

Identificador de la fuente que se usa para la celda actual.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método devuelve NULL. Todas las celdas de un control de lista tienen la misma fuente. Invalide este método con el fin de proporcionar distintas fuentes para celdas distintas.

##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor

El marco llama a este método cuando debe determinar el color del texto de una celda individual.

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>Parámetros

*nRow*<br/>
[in] La fila de la celda en cuestión.

*nColumn*<br/>
[in] La columna de la celda en cuestión.

### <a name="return-value"></a>Valor devuelto

Un valor COLOREF que especifica el color del texto de la celda.

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método llama a `GetTextColor` independientemente de los parámetros de entrada. El control de lista todo tendrá el mismo color de texto. Puede invalidar `OnGetCellTextColor` en una clase derivada para marcar las celdas individuales con un color de texto independiente.

##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn

Quita una columna de ordenación de la lista de columnas ordenadas.

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[in] Para quitar la columna.

### <a name="remarks"></a>Comentarios

Este método quita una columna de ordenación del control de encabezado. Llama a [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).

##  <a name="setsortcolumn"></a>  CMFCListCtrl::SetSortColumn

Establece la columna ordenada actual y el criterio de ordenación.

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[in] La columna para ordenar.

*bAscending*<br/>
[in] Un valor booleano que especifica el criterio de ordenación.

*bAdd*<br/>
[in] Un valor booleano que especifica si el método agrega la columna indicada por *iColumn* a la lista de columnas de ordenación.

### <a name="remarks"></a>Comentarios

Este método pasa los parámetros de entrada para el control de encabezado mediante el método [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).

##  <a name="sort"></a>  CMFCListCtrl::Sort

Ordena el control de lista.

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>Parámetros

*iColumn*<br/>
[in] La columna para ordenar.

*bAscending*<br/>
[in] Un valor booleano que especifica el criterio de ordenación.

*bAdd*<br/>
[in] Un valor booleano que especifica si este método agrega la columna indicada por *iColumn* a la lista de columnas de ordenación.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
