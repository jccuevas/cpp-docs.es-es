---
title: Clase CMFCListCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCListCtrl class
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: 29
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
ms.openlocfilehash: 3a4c67b2d7ea2a5356f7c053403edf414319a928
ms.lasthandoff: 02/24/2017

---
# <a name="cmfclistctrl-class"></a>Clase CMFCListCtrl
El `CMFCListCtrl` clase extiende la funcionalidad de [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase admitiendo la funcionalidad de control avanzado de encabezado de la [CMFCHeaderCtrl clase](../../mfc/reference/cmfcheaderctrl-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|Habilita la capacidad marcar una columna ordenada con un color de fondo diferente.|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita el modo de ordenación de varias.|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|Devuelve una referencia al control de encabezado subrayado.|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|Comprueba si el control de lista está en modo de ordenación múltiple.|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|Llamado por el marco de trabajo cuando deben comparar dos elementos de control de lista.|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|Llamado por el marco de trabajo cuando se debe determinar el color de fondo de una celda individual.|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|Llamado por el marco de trabajo cuando se debe obtener la fuente de la celda que se va a dibujar.|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|Llamado por el marco de trabajo cuando se debe determinar el color del texto de una celda individual.|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|Quita una columna de ordenación de la lista de columnas ordenadas.|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|Establece la columna ordenada actual y el criterio de ordenación.|  
|[CMFCListCtrl::Sort](#sort)|Ordena el control de lista.|  
  
## <a name="remarks"></a>Comentarios  
 `CMFCListCtrl`ofrece dos mejoras en [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md) clase. En primer lugar, indica que la ordenación de columnas es una opción disponible dibujando automáticamente una flecha de ordenación en el encabezado. En segundo lugar, admite datos ordenar varias columnas al mismo tiempo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCListCtrl` clase. En el ejemplo se muestra cómo crear un control de lista, insertar columnas, insertar elementos, establecer el texto de un elemento y establecer la fuente del control de lista. Este fragmento de código forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo&#25;](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]  
[!code-cpp[26 de NVC_MFC_VisualStudioDemo #](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]  
  
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
 Parámetro booleano que determina si se debe habilitar un color de fondo diferente.  
  
 [in] `bRedraw`  
 Parámetro booleano que determina si se va a dibujar el control inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 `EnableMarkSortedColumn`usa el método `CDrawingManager::PixelAlpha` calcular el color que se utilizará para ordena las columnas. El color seleccionado se basa en el color de fondo normal.  
  
##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort  
 Permite ordenar las filas de datos en el control de lista por varias columnas.  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Valor booleano que especifica si se habilita el modo de ordenación de varias columnas.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita la ordenación según varias columnas, las columnas tienen una jerarquía. Las filas de datos se ordenarán primero por la columna principal. Los valores equivalentes se ordenan por cada columna subsiguientes según su prioridad.  
  
##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl  
 Devuelve una referencia al control de encabezado.  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la base de [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 El control de encabezado de un control de lista es la ventana que contiene los títulos de las columnas. Normalmente se coloca directamente encima de las columnas.  
  
##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort  
 Comprueba si el control de lista admite actualmente la ordenación en varias columnas.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de lista admite a la ordenación de varias; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un [CMFCListCtrl clase](../../mfc/reference/cmfclistctrl-class.md) admite la ordenación de varias, el usuario puede ordenar los datos en el control de lista por varias columnas. Para habilitar la ordenación de varias, llame a [CMFCListCtrl::EnableMultipleSort](#enablemultiplesort).  
  
##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems  
 El marco de trabajo llama a este método cuando compara dos elementos.  
  
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
 La implementación predeterminada siempre devuelve 0. Debe reemplazar esta función para proporcionar un algoritmo de ordenación.  
  
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
 La implementación predeterminada de `OnGetCellBkColor` no usa los parámetros de entrada proporcionados y en su lugar, simplemente llama a `GetBkColor`. Por lo tanto, de forma predeterminada, el control de toda la lista tendrá el mismo color de fondo. Puede invalidar `OnGetCellBkColor` en una clase derivada para marcar las celdas individuales con un color de fondo.  
  
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
 De forma predeterminada, este método devuelve `NULL`. Todas las celdas de un control de lista tienen la misma fuente. Invalide este método para proporcionar distintas fuentes para celdas distintas.  
  
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
 La columna que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Este método quita una columna de ordenación desde el control de encabezado. Llama a [CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn).  
  
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
 Valor booleano que especifica el criterio de ordenación.  
  
 [in] `bAdd`  
 Un valor booleano que especifica si el método agrega la columna indicada por `iColumn` a la lista de columnas de ordenación.  
  
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
 Valor booleano que especifica el criterio de ordenación.  
  
 [in] `bAdd`  
 Un valor booleano que especifica si este método agrega la columna indicada por `iColumn` a la lista de columnas de ordenación.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CListCtrl (clase)](../../mfc/reference/clistctrl-class.md)

