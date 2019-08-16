---
title: CDockSite Class
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: 9c154fe621fb88a6dc96a9835fae95c4b86763de
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866192"
---
# <a name="cdocksite-class"></a>CDockSite Class

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

Proporciona la funcionalidad para organizar los paneles que se derivan de [CPane Class](../../mfc/reference/cpane-class.md) en conjuntos de filas.

## <a name="syntax"></a>Sintaxis

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Invalida [a cbasepane:: AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)).|
|[CDockSite::AdjustLayout](#adjustlayout)|(Invalida [a cbasepane:: AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout)).|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Invalida [a cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)).|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Invalida [a cbasepane:: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)).|
|[CDockSite::CreateEx](#createex)|(Invalida [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)).|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Invalida [a cbasepane::D ockpane](../../mfc/reference/cbasepane-class.md#dockpane)).|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Invalida [a cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)).|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Invalida `CBasePane::IsAccessibilityCompatible`).|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Invalida [a cbasepane:: IsResizable](../../mfc/reference/cbasepane-class.md#isresizable)).|
|[CDockSite::MovePane](#movepane)||
|[CDockSite::OnInsertRow](#oninsertrow)||
|[CDockSite::OnRemoveRow](#onremoverow)||
|[CDockSite::OnResizeRow](#onresizerow)||
|[CDockSite::OnSetWindowPos](#onsetwindowpos)||
|[CDockSite::OnShowRow](#onshowrow)||
|[CDockSite::OnSizeParent](#onsizeparent)||
|[CDockSite::PaneFromPoint](#panefrompoint)|Devuelve un panel que está acoplado en el sitio de vinculación en el punto especificado por el parámetro dado.|
|[CDockSite::DockPaneLeftOf](#dockpaneleftof)|Acopla un panel a la izquierda de otro panel.|
|[CDockSite::FindPaneByID](#findpanebyid)|Devuelve el panel identificado por el identificador especificado.|
|[CDockSite::GetPaneList](#getpanelist)|Devuelve una lista de paneles acoplados en el sitio de vinculación.|
|[CDockSite::RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite::RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite::ReplacePane](#replacepane)||
|[CDockSite::RepositionPanes](#repositionpanes)||
|[CDockSite::ResizeDockSite](#resizedocksite)||
|[CDockSite::ResizeRow](#resizerow)||
|[CDockSite::ShowPane](#showpane)|Muestra el panel.|
|[CDockSite::ShowRow](#showrow)||
|[CDockSite::SwapRows](#swaprows)||

## <a name="remarks"></a>Comentarios

El marco de `CDockSite` trabajo crea objetos automáticamente al llamar a [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Las ventanas del sitio de vinculación están colocadas en el borde del área de cliente de la ventana de marco principal.

Normalmente no es necesario llamar a los servicios que proporciona el sitio de Dock porque la [clase CFrameWndEx](../../mfc/reference/cframewndex-class.md) controla estos servicios.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CDockSite`.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[A cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockSite. h

##  <a name="addrow"></a>  CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

de *PDV* de<br/>

de *nHeight*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Comentarios

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Comentarios

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parámetros

de *rectToAlignBy*<br/>

de *rectResult*<br/>

de *bMoveImmediately*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

de *bStretch*<br/>

de *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="canacceptpane"></a>  CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="createex"></a>  CDockSite::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

de *dwStyleEx*<br/>

de *dwStyle*<br/>

de *rectángulo*<br/>

de *pParentWnd*<br/>

de *dwControlBarStyle*<br/>

de *pContext*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="createrow"></a>  CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parámetros

de *pParentDockBar*<br/>

de *nOffset*<br/>

de *nRowHeight*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="dockpane"></a>  CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

de *PWND*<br/>

de *dockMethod*<br/>

de *lpRect*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="dockpaneleftof"></a>  CDockSite::DockPaneLeftOf

Acopla un panel a la izquierda de otro panel.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parámetros

*pBarToDock*<br/>
[in, out] Puntero al panel que se va a acoplar a la izquierda de *pTargetBar*.

*pTargetBar*<br/>
[in, out] Puntero al panel de destino.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel está acoplado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="findpanebyid"></a>  CDockSite::FindPaneByID

Devuelve el panel con el identificador especificado.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de IDENTIFICADOR de comando del panel que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Un puntero al panel con el identificador de comando especificado, o NULL si no se encuentra el panel.

### <a name="remarks"></a>Comentarios

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parámetros

de *pRow*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Comentarios

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

Devuelve una lista de paneles que están acoplados en el sitio de acoplamiento.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valor devuelto

Referencia de solo lectura a la lista de paneles acoplados actualmente en la barra de acoplamiento.

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isdragmode"></a>  CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="islastrow"></a>  CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parámetros

de *pRow*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parámetros

de *rectángulo*<br/>

de *ptDelta*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isresizable"></a>  CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="movepane"></a>  CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parámetros

de *PWND*<br/>

de *nFlags*<br/>

[in] *ptOffset*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parámetros

de *PDV* de<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parámetros

de *PDV* de<br/>

de *bByShow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onresizerow"></a>  CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parámetros

de *pRowToResize*<br/>

de *nOffset*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onsizeparent"></a>  CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parámetros

de *rectAvailable*<br/>

de *nSide*<br/>

de *bExpand*<br/>

de *nOffset*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="onsetwindowpos"></a>  CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

de *pWndInsertAfter*<br/>

de *rectWnd*<br/>

de *nFlags*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onshowrow"></a>  CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

de *PDV* de<br/>

de *bShow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="panefrompoint"></a>  CDockSite::PaneFromPoint

Devuelve un panel que está acoplado en el sitio de vinculación en el punto especificado por el parámetro dado.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
de Punto, en coordenadas de la pantalla, del panel que se va a recuperar.

### <a name="return-value"></a>Valor devuelto

Puntero al panel situado en el punto especificado o NULL si no hay ningún panel presente en el punto especificado.

### <a name="remarks"></a>Comentarios

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parámetros

de *rectángulo*<br/>

de *punto* de<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="removepane"></a>  CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parámetros

de *PWND*<br/>

de *dockMethod*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="removerow"></a>  CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parámetros

de *pRow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="replacepane"></a>  CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parámetros

de *pOldBar*<br/>

de *pNewBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="repositionpanes"></a>  CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parámetros

de *rectNewClientArea*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parámetros

de *nNewWidth*<br/>

de *nNewHeight*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="resizerow"></a>  CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parámetros

de *pRow*<br/>

de *nNewSize*<br/>

de *bAdjustLayout*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="showpane"></a>  CDockSite::ShowPane

Muestra el panel.

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parámetros

*pBar*<br/>
[in, out] Puntero al panel que se va a mostrar u ocultar.

*bShow*<br/>
de TRUE para especificar que se va a mostrar el panel; FALSE para especificar que el panel se va a ocultar.

*bDelay*<br/>
de TRUE para especificar que el diseño del panel debe retrasarse hasta que se muestre el panel; en caso contrario, FALSE.

*bActivate*<br/>
de Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se mostró u ocultó correctamente. FALSE si el panel especificado no pertenece a este sitio de Docker.

### <a name="remarks"></a>Comentarios

Llame a este método para mostrar u ocultar los paneles acoplados. Normalmente, no es necesario llamar `CDockSite::ShowPane` directamente a porque lo llama la ventana marco primaria o el panel base.

##  <a name="showrow"></a>  CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parámetros

de *pRow*<br/>

de *bShow*<br/>

de *bAdjustLayout*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="swaprows"></a>  CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parámetros

de *pFirstRow*<br/>

de *pSecondRow*<br/>

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
