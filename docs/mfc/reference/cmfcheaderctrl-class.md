---
title: CMFCHeaderCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36817eba04d630ea4e56140af582bf49fa6f54ce
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718125"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class
La `CMFCHeaderCtrl` clase admite la ordenación de varias columnas en un control de encabezado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|Construye un objeto `CMFCHeaderCtrl`.|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|Habilita o deshabilita *ordenación de varias columnas* modo para el control de encabezado actual.|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|Indica si una columna no está ordenada, o si se ordena en orden ascendente o descendente.|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|Recupera el índice de base cero de la primera columna ordenada en el control de encabezado.|  
|`CMFCHeaderCtrl::GetThisClass`|Usa el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado con este tipo de clase.|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|Indica si cualquier columna del control de encabezado se ordena en orden ascendente.|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|Indica si la ventana primaria del control de encabezado actual es un cuadro de diálogo.|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|Indica si el control de encabezado actual está en *ordenación de varias columnas* modo.|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|Quita la columna especificada de la lista de columnas de ordenación.|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|Establece el criterio de ordenación de una columna especificada en un control de encabezado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|Lo llama el marco de trabajo para dibujar una columna del control de encabezado.|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|Lo llama el marco de trabajo para dibujar la flecha de ordenación.|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|Lo llama el marco de trabajo para rellenar el fondo de una columna del control de encabezado.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCHeaderCtrl` clase y cómo habilitar *ordenación de varias columnas* modo para el control de encabezado actual.  
  
 [!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCHeaderCtrl` clase dibuja una flecha de ordenación en una columna del control de encabezado para indicar que la columna está ordenada. Use *ordenación de varias columnas* modo si un conjunto de columnas en el control de lista primario ( [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md)) se pueden ordenar al mismo tiempo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl  
 Construye un objeto `CMFCHeaderCtrl`.  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>Comentarios  
 Este constructor inicializa las variables de miembro siguientes en los valores especificados:  
  
|Variable de miembro|Valor|  
|---------------------|-----------|  
|`m_bIsMousePressed`|false|  
|`m_bMultipleSort`|false|  
|`m_bAscending`|true|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|false|  
|`m_bIsDlgControl`|FALSE|  
|`m_hFont`|NULL|  
  
##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort  
 Habilita o deshabilita *ordenación de varias columnas* modo para el control de encabezado actual.  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
*bHabilitar el*<br/>
[in] TRUE para habilitar el modo de ordenación de varias columnas; FALSE para deshabilitar el modo de ordenación de varias columnas y quite todas las columnas de la lista de columnas ordenadas. El valor predeterminado es TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para habilitar o deshabilitar el modo de ordenación de varias columnas. Dos o más columnas pueden participar en un criterio de ordenación, si el control de encabezado está en modo de ordenación de varias columnas.  
  
##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState  
 Indica si una columna está ordenada o se ordena en orden ascendente o descendente.  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*iColumn*<br/>
[in] Índice de base cero de una columna.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor que indican el estado de ordenación de la columna especificada. En la tabla siguiente se enumera los valores posibles:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|-1|Ordenar en orden descendente.|  
|0|No se ordenan.|  
|1|Ordenar en orden ascendente.|  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn  
 Recupera el índice de base cero de la primera columna ordenada en el control de encabezado.  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de una columna ordenada o -1 si se encuentra ninguna columna ordenada.  
  
### <a name="remarks"></a>Comentarios  
 Si el control de encabezado está en *ordenación de varias columnas* modo y se compila la aplicación en modo de depuración, este método valida y le informa de que se va a usar el [CMFCHeaderCtrl::GetColumnState](#getcolumnstate) método en su lugar. Si el control de encabezado está en modo de ordenación de varias columnas y ha compilado la aplicación en modo de venta directa, este método devuelve -1.  
  
##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending  
 Indica si cualquier columna del control de encabezado se ordena en orden ascendente.  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si cualquier columna en el control de encabezado se ordena en orden ascendente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 El valor que devuelve este método se utiliza para mostrar la flecha de ordenación adecuado en el elemento de control de encabezado. Use la [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn) método para establecer el criterio de ordenación.  
  
##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl  
 Indica si la ventana primaria del control de encabezado actual es un cuadro de diálogo.  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es TRUE si la ventana primaria del control de encabezado actual es un cuadro de diálogo; en caso contrario, FALSE.  
  
##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort  
 Indica si el control de encabezado actual está en *ordenación de varias columnas* modo.  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitado el modo de ordenación de varias columnas; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) método para habilitar o deshabilitar el modo de ordenación de varias columnas. Dos o más columnas pueden participar en un criterio de ordenación, si el control de encabezado está en modo de ordenación de varias columnas.  
  
##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem  
 Lo llama el marco de trabajo para dibujar una columna del control de encabezado.  
  
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
[in] Un puntero a un contexto de dispositivo.  
  
*iItem*<br/>
[in] Índice de base cero del elemento que se va a dibujar.  
  
*Rect*<br/>
[in] El rectángulo delimitador del elemento que se va a dibujar.  
  
*bIsPressed*<br/>
[in] TRUE para dibujar el elemento en estado presionado; en caso contrario, FALSE.  
  
*bIsHighlighted*<br/>
[in] TRUE para dibujar el elemento en el estado resaltado; en caso contrario, FALSE.  
  
##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow  
 Lo llama el marco de trabajo para dibujar la flecha de ordenación.  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.  
  
*rectArrow*<br/>
[in] El rectángulo delimitador de la flecha de ordenación.  
  
##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground  
 Lo llama el marco de trabajo para rellenar el fondo de una columna del control de encabezado.  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn  
 Quita la columna especificada de la lista de columnas de ordenación.  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>Parámetros  
*iColumn*<br/>
[in] Índice de base cero de la columna que se va a quitar.  
  
##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn  
 Establece el criterio de ordenación de una columna especificada en un control de encabezado.  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
*iColumn*<br/>
[in] Índice de base cero de una columna del control de encabezado. Si este parámetro es menor que cero, este método quita todas las columnas de la lista de columnas de ordenación.  
  
*bAscending*<br/>
[in] Especifica el criterio de ordenación de la columna que la *iColumn* especifica el parámetro. TRUE para establecer el orden ascendente; FALSE para establecer el orden descendente. El valor predeterminado es TRUE.  
  
*bAgregar*<br/>
[in] True para establecer el criterio de ordenación de la columna que la *iColumn* especifica el parámetro.  
  
 Si el control de encabezado actual está en *ordenación de varias columnas* modo, este método agrega la columna especificada a la lista de columnas de orden. Use [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort) para establecer el modo de ordenación de varias columnas.  
  
 Si no se establece el modo de ordenación de varias columnas y este método está compilado en modo de depuración, se declara este método. Si no se establece el modo de ordenación de varias columnas y este método está compilado en modo de venta directa, este método quita primero todas las columnas de la lista de columnas de ordenación y, a continuación, agrega la columna especificada a la lista.  
  
 FALSE para quitar primero todas las columnas de la lista de columnas de ordenación y, a continuación, agregue la columna especificada a la lista. El valor predeterminado es FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer el criterio de ordenación de una columna. Si es necesario, este método agrega la columna a la lista de columnas de ordenación. El control de encabezado utiliza el criterio de ordenación para dibujar una flecha de ordenación que señala hacia arriba o hacia abajo.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl (clase)](../../mfc/reference/cmfclistctrl-class.md)
