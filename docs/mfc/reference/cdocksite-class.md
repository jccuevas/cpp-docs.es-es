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
ms.openlocfilehash: 471d68ead1bc5a11ace29f572647c4a7f2406b4e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753272"
---
# <a name="cdocksite-class"></a>CDockSite Class

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

Proporciona la funcionalidad para organizar los paneles que se derivan de [CPane Class](../../mfc/reference/cpane-class.md) en conjuntos de filas.

## <a name="syntax"></a>Sintaxis

```
class CDockSite: public CBasePane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Reemplaza [CBasePane::AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|
|[CDockSite::AdjustLayout](#adjustlayout)|(Reemplaza [CBasePane::AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|
|[CDockSite::AlignDockSite](#aligndocksite)||
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Reemplaza [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CDockSite::CanAcceptPane](#canacceptpane)|(Reemplaza [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|
|[CDockSite::CreateEx](#createex)|(Reemplaza [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CDockSite::CreateRow](#createrow)||
|[CDockSite::DockPane](#dockpane)|(Reemplaza [CBasePane::DockPane](../../mfc/reference/cbasepane-class.md#dockpane).)|
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Reemplaza [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite::GetDockSiteID](#getdocksiteid)||
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Invalida `CBasePane::IsAccessibilityCompatible`).|
|[CDockSite::IsDragMode](#isdragmode)||
|[CDockSite::IsLastRow](#islastrow)||
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite::IsResizable](#isresizable)|(Reemplaza [CBasePane::IsResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|
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

## <a name="remarks"></a>Observaciones

El marco `CDockSite` de trabajo crea objetos automáticamente cuando se llama a [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Las ventanas del sitio de vinculación están colocadas en el borde del área de cliente de la ventana de marco principal.

Normalmente no es necesario llamar a los servicios proporcionados por el sitio de acoplamiento porque [CFrameWndEx clase](../../mfc/reference/cframewndex-class.md) controla estos servicios.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CDockSite`.

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cobject](../../mfc/reference/cobject-class.md)\
.&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDockSite.h

## <a name="cdocksiteaddrow"></a><a name="addrow"></a>CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>Parámetros

[en] *pos*<br/>

[en] *nAltura*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteadjustdockinglayout"></a><a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteadjustlayout"></a><a name="adjustlayout"></a>CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocksitealigndocksite"></a><a name="aligndocksite"></a>CDockSite::AlignDockSite

```cpp
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>Parámetros

[en] *rectToAlignBy*<br/>

[en] *rectResult*<br/>

[en] *bMoveImmediately*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksitecalcfixedlayout"></a><a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

[en] *bStretch*<br/>

[en] *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitecanacceptpane"></a><a name="canacceptpane"></a>CDockSite::CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitecreateex"></a><a name="createex"></a>CDockSite::CreateEx

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

[en] *dwStyleEx*<br/>

[en] *dwStyle*<br/>

[en] *rect*<br/>

[en] *pParentWnd*<br/>

[en] *dwControlBarStyle*<br/>

[en] *pContext*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitecreaterow"></a><a name="createrow"></a>CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>Parámetros

[en] *pParentDockBar*<br/>

[en] *nOffset*<br/>

[en] *nRowHeight*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitedockpane"></a><a name="dockpane"></a>CDockSite::DockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

[en] *pWnd*<br/>

[en] *dockMethod*<br/>

[en] *lpRect*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksitedockpaneleftof"></a><a name="dockpaneleftof"></a>CDockSite::DockPaneLeftOf

Acopla un panel a la izquierda de otro panel.

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>Parámetros

*pBarToDock*<br/>
[adentro, fuera] Puntero al panel que se va a acoplar a la izquierda de *pTargetBar*.

*pTargetBar*<br/>
[adentro, fuera] Un puntero al panel de destino.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel se acopla correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cdocksitedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitefindpanebyid"></a><a name="findpanebyid"></a>CDockSite::FindPaneByID

Devuelve el panel con el identificador especificado.

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] El identificador de comando del panel que se va a encontrar.

### <a name="return-value"></a>Valor devuelto

Un puntero al panel con el identificador de comando especificado, o NULL si no se encuentra el panel.

### <a name="remarks"></a>Observaciones

## <a name="cdocksitefindrowindex"></a><a name="findrowindex"></a>CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parámetros

[en] *pRow*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitefixupvirtualrects"></a><a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Observaciones

## <a name="cdocksitegetdocksiteid"></a><a name="getdocksiteid"></a>CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitegetdocksiterowslist"></a><a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitegetpanelist"></a><a name="getpanelist"></a>CDockSite::GetPaneList

Devuelve una lista de paneles acoplados en el sitio de acoplamiento.

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia de solo lectura a la lista de paneles acoplados actualmente en la barra de acoplamiento.

## <a name="cdocksiteisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteisdragmode"></a><a name="isdragmode"></a>CDockSite::IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteislastrow"></a><a name="islastrow"></a>CdockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>Parámetros

[en] *pRow*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteisrectwithindocksite"></a><a name="isrectwithindocksite"></a>CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>Parámetros

[en] *rect*<br/>

[en] *ptDelta*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteisresizable"></a><a name="isresizable"></a>CDockSite::IsResizable

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksitemovepane"></a><a name="movepane"></a>CDockSite::MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>Parámetros

[en] *pWnd*<br/>

[en] *nFlags*<br/>

[en] *ptOffset*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteoninsertrow"></a><a name="oninsertrow"></a>CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>Parámetros

[en] *pos*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteonremoverow"></a><a name="onremoverow"></a>CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>Parámetros

[en] *pos*<br/>

[en] *bByShow*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteonresizerow"></a><a name="onresizerow"></a>CDockSite::OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>Parámetros

[en] *pRowToResize*<br/>

[en] *nOffset*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteonsizeparent"></a><a name="onsizeparent"></a>CDockSite::OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>Parámetros

[en] *rectAvailable*<br/>

[en] *nSide*<br/>

[en] *bExpandir*<br/>

[en] *nOffset*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteonsetwindowpos"></a><a name="onsetwindowpos"></a>CDockSite::OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>Parámetros

[en] *pWndInsertAfter*<br/>

[en] *rectWnd*<br/>

[en] *nFlags*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteonshowrow"></a><a name="onshowrow"></a>CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

[en] *pos*<br/>

[en] *bMostrar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksitepanefrompoint"></a><a name="panefrompoint"></a>CDockSite::PaneFromPoint

Devuelve un panel que está acoplado en el sitio de vinculación en el punto especificado por el parámetro dado.

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*Pt*<br/>
[en] Un punto, en coordenadas de pantalla, para que el panel se recupere.

### <a name="return-value"></a>Valor devuelto

Puntero al panel situado en el punto especificado o NULL si no había ningún panel en el punto especificado.

### <a name="remarks"></a>Observaciones

## <a name="cdocksiterectsidefrompoint"></a><a name="rectsidefrompoint"></a>CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>Parámetros

[en] *rect*<br/>

[en] *punto*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteremovepane"></a><a name="removepane"></a>CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parámetros

[en] *pWnd*<br/>

[en] *dockMethod*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteremoverow"></a><a name="removerow"></a>CDockSite::RemoveRow

```cpp
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>Parámetros

[en] *pRow*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksitereplacepane"></a><a name="replacepane"></a>CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>Parámetros

[en] *pOldBar*<br/>

[en] *pNewBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiterepositionpanes"></a><a name="repositionpanes"></a>CDockSite::RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>Parámetros

[en] *rectNewClientArea*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteresizedocksite"></a><a name="resizedocksite"></a>CDockSite::ResizeDockSite

```cpp
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>Parámetros

[en] *nNewWidth*<br/>

[en] *nNewHeight*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteresizerow"></a><a name="resizerow"></a>CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *pRow*<br/>

[en] *nNewSize*<br/>

[en] *bAdjustLayout*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteshowpane"></a><a name="showpane"></a>CDockSite::ShowPane

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
[adentro, fuera] Puntero al panel que se va a mostrar u ocultar.

*bMostrar*<br/>
[en] TRUE para especificar que se va a mostrar el panel; FALSE para especificar que el panel se va a ocultar.

*bDelay*<br/>
[en] TRUE para especificar que el diseño del panel debe retrasarse hasta después de mostrar el panel; de lo contrario, FALSE.

*bActivar*<br/>
[en] Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

TRUESi el panel se ha mostrado u ocultado correctamente. FALSE si el panel especificado no pertenece a este sitio de acoplamiento.

### <a name="remarks"></a>Observaciones

Llame a este método para mostrar u ocultar los paneles acoplados. Normalmente, no es `CDockSite::ShowPane` necesario llamar directamente, porque lo llama la ventana de marco principal o el panel base.

## <a name="cdocksiteshowrow"></a><a name="showrow"></a>CDockSite::ShowRow

```cpp
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>Parámetros

[en] *pRow*<br/>

[en] *bMostrar*<br/>

[en] *bAdjustLayout*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cdocksiteswaprows"></a><a name="swaprows"></a>CDockSite::SwapRows

```cpp
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>Parámetros

[en] *pFirstRow*<br/>

[en] *pSecondRow*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
