---
title: Clase CMFCListCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c8b4172167a60425603bb25acff5670a5901c307
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cmfclistctrl-class"></a>Clase CMFCListCtrl
El `CMFCListCtrl` clase extiende la funcionalidad de [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase ya que admite la funcionalidad de control avanzado de encabezado de la [clase CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Habilita la funcionalidad para marcar una columna ordenada con un color de fondo diferente.|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita el modo de ordenación de varias.|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Devuelve una referencia al control de encabezado subrayado.|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Comprueba si el control de lista está en modo de ordenación múltiple.|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Llamado por el marco de trabajo cuando deben comparar dos elementos de control de lista.|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Llamado por el marco de trabajo cuando debe determinar el color de fondo de una celda individual.|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Llamado por el marco de trabajo cuando debe obtener la fuente de la celda que se va a dibujar.|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Llamado por el marco de trabajo cuando debe determinar el color del texto de una celda individual.|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Quita una columna de ordenación de la lista de columnas ordenadas.|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Establece la columna ordenada actual y el criterio de ordenación.|  
|[CMFCListCtrl::Sort](#sort)|Ordena el control de lista.|  
  
## <a name="remarks"></a>Comentarios  
 `CMFCListCtrl`ofrece dos mejoras en [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase. En primer lugar, indica que la ordenación de columnas es una opción disponible dibujando automáticamente una flecha de ordenación en el encabezado. En segundo lugar, admite la ordenación según varias columnas al mismo tiempo de los datos.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCListCtrl` clase. En el ejemplo se muestra cómo crear un control de lista, columnas de inserción, insertar elementos, establecer el texto de un elemento y establecer la fuente del control de lista. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
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
  
##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn  
 Marca las columnas ordenadas con un color de fondo diferente.  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMark`  
 Un parámetro booleano que determina si se debe habilitar un color de fondo diferente.  
  
 [in] `bRedraw`  
 Un parámetro booleano que determina si se debe volver a dibujar el control inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 `EnableMarkSortedColumn`usa el método `CDrawingManager::PixelAlpha` calcular el color que se utilizará para ordena las columnas. El color seleccionado se basa en el color de fondo normal.  
  
##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort  
 Permite ordenar las filas de datos en el control de lista por varias columnas.  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Un valor booleano que especifica si se debe habilitar el modo de ordenación de varias columnas.  
  
### <a name="remarks"></a>Comentarios  
 Al habilitar la ordenación según varias columnas, las columnas tienen una jerarquía. Las filas de datos se ordenarán primero por la columna principal. Los valores equivalentes, a continuación, se ordenan por cada columna siguiente según su prioridad.  
  
##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl  
 Devuelve una referencia al control de encabezado.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a subyacente [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El control de encabezado para un control de lista es la ventana que contiene los títulos de las columnas. Normalmente se coloca directamente encima de las columnas.  
  
##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort  
 Comprueba si el control de lista admite actualmente la ordenación de varias columnas.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de lista admite a la ordenación de varias; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un [CMFCListCtrl clase](../../mfc/reference/cmfclistctrl-class.md) admite la ordenación de varias, el usuario puede ordenar los datos en el control de lista por varias columnas. Para habilitar la ordenación de varias, llame a [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).  
  
##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems  
 El marco de trabajo llama a este método cuando comparan dos elementos.  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lParam1`  
 Primer elemento que comparar.  
  
 [in] `lParam2`  
 Segundo elemento que comparar.  
  
 [in] `iColumn`  
 El índice de la columna que se está ordenando este método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que indica la posición relativa de los dos elementos. Un valor negativo indica que el primer elemento debería preceder al segundo, un valor positivo indica que el primer elemento debería seguir al segundo, y cero significa que los dos elementos son equivalentes.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada siempre devuelve 0. Se debe reemplazar esta función para proporcionar un algoritmo de ordenación.  
  
##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor  
 El marco de trabajo llama a este método cuando debe determinar el color de fondo de una celda individual.  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRow`  
 La fila de la celda en cuestión.  
  
 [in] `nColumn`  
 La columna de la celda en cuestión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COLOREF` valor que especifica el color de fondo de la celda.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de `OnGetCellBkColor` no usa los parámetros de entrada proporcionados y en su lugar, simplemente llama `GetBkColor`. Por lo tanto, de forma predeterminada, el control de toda la lista tendrá el mismo color de fondo. Puede invalidar `OnGetCellBkColor` en una clase derivada para marcar las celdas individuales con un color de fondo diferente.  
  
##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont  
 El marco de trabajo llama a este método cuando obtiene la fuente de una celda individual.  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRow`  
 La fila de la celda en cuestión.  
  
 [in] `nColumn`  
 La columna de la celda en cuestión.  
  
 [in] `dwData`  
 Datos definidos por el usuario. La implementación predeterminada no utiliza este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de la fuente que se utiliza para la celda actual.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método devuelve `NULL`. Todas las celdas de un control de lista tienen la misma fuente. Invalide este método para proporcionar diferentes fuentes de celdas distintas.  
  
##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor  
 El marco de trabajo llama a este método cuando debe determinar el color del texto de una celda individual.  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nRow`  
 La fila de la celda en cuestión.  
  
 [in] `nColumn`  
 La columna de la celda en cuestión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `COLOREF` valor que especifica el color del texto de la celda.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método llama a `GetTextColor` , independientemente de los parámetros de entrada. El control de toda la lista tendrá el mismo color del texto. Puede invalidar `OnGetCellTextColor` en una clase derivada para marcar las celdas individuales con un color de texto independiente.  
  
##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn  
 Quita una columna de ordenación de la lista de columnas ordenadas.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iColumn`  
 Columna que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita una columna de ordenación del control de encabezado. Llama [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).  
  
##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn  
 Establece la columna ordenada actual y el criterio de ordenación.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iColumn`  
 La columna para ordenar.  
  
 [in] `bAscending`  
 Un valor booleano que especifica el criterio de ordenación.  
  
 [in] `bAdd`  
 Un valor booleano que especifica si el método agrega la columna indicada por `iColumn` a la lista de columnas de orden.  
  
### <a name="remarks"></a>Comentarios  
 Este método pasa los parámetros de entrada para el control de encabezado mediante el método [CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn).  
  
##  <a name="sort"></a>CMFCListCtrl::Sort  
 Ordena el control de lista.  
  
```  
virtual void Sort(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iColumn`  
 La columna para ordenar.  
  
 [in] `bAscending`  
 Un valor booleano que especifica el criterio de ordenación.  
  
 [in] `bAdd`  
 Un valor booleano que especifica si este método agrega la columna indicada por `iColumn` a la lista de columnas de orden.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)
