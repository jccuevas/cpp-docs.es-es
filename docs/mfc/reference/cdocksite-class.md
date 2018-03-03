---
title: Clase CDockSite | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e2492738914062be692c1ddd02fd04bc461cd6b6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdocksite-class"></a>CDockSite Class
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Proporciona la funcionalidad para organizar los paneles que se derivan de [CPane Class](../../mfc/reference/cpane-class.md) en conjuntos de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDockSite: public CBasePane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDockSite::AddRow](#addrow)||  
|[CDockSite::AdjustDockingLayout](#adjustdockinglayout)|(Invalida [cbasepane:: Adjustdockinglayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout).)|  
|[CDockSite::AdjustLayout](#adjustlayout)|(Invalida [cbasepane:: Adjustlayout](../../mfc/reference/cbasepane-class.md#adjustlayout).)|  
|[CDockSite::AlignDockSite](#aligndocksite)||  
|[CDockSite::CalcFixedLayout](#calcfixedlayout)|(Invalida [cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CDockSite::CanAcceptPane](#canacceptpane)|(Invalida [cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane).)|  
|[CDockSite::CreateEx](#createex)|(Invalida [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|  
|[CDockSite::CreateRow](#createrow)||  
|[CDockSite::DockPane](#dockpane)|(Invalida [cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#dockpane).)|  
|[CDockSite::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Invalida [cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CDockSite::FindRowIndex](#findrowindex)||  
|[CDockSite::FixupVirtualRects](#fixupvirtualrects)||  
|[CDockSite::GetDockSiteID](#getdocksiteid)||  
|[CDockSite::GetDockSiteRowsList](#getdocksiterowslist)||  
|[CDockSite::IsAccessibilityCompatible](#isaccessibilitycompatible)|(Invalida `CBasePane::IsAccessibilityCompatible`).|  
|[CDockSite::IsDragMode](#isdragmode)||  
|[CDockSite::IsLastRow](#islastrow)||  
|[CDockSite::IsRectWithinDockSite](#isrectwithindocksite)||  
|[CDockSite::IsResizable](#isresizable)|(Invalida [cbasepane:: isResizable](../../mfc/reference/cbasepane-class.md#isresizable).)|  
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
 El marco de trabajo crea `CDockSite` objetos automáticamente cuando se llama a [cframewndex:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Las ventanas del sitio de vinculación están colocadas en el borde del área de cliente de la ventana de marco principal.  
  
 Normalmente no es necesario llamar a los servicios proporcionados por el sitio de vinculación porque [CFrameWndEx clase](../../mfc/reference/cframewndex-class.md) controla estos servicios.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo crear un objeto de la clase `CDockSite`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CDockSite](../../mfc/reference/cdocksite-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxDockSite.h  
  
##  <a name="addrow"></a>CDockSite::AddRow  

  
```  
CDockingPanesRow* AddRow(
    POSITION pos,  
    int nHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pos`  
 [in] `nHeight`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="adjustdockinglayout"></a>CDockSite::AdjustDockingLayout  

  
```  
virtual void AdjustDockingLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="adjustlayout"></a>CDockSite::AdjustLayout  

  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="aligndocksite"></a>CDockSite::AlignDockSite  

  
```  
void AlignDockSite(
    const CRect& rectToAlignBy,  
    CRect& rectResult,  
    BOOL bMoveImmediately);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectToAlignBy`  
 [in] `rectResult`  
 [in] `bMoveImmediately`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="calcfixedlayout"></a>CDockSite::CalcFixedLayout  

  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bStretch`  
 [in] `bHorz`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="canacceptpane"></a>CDockSite::CanAcceptPane  

  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="createex"></a>CDockSite::CreateEx  

  
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
 [in] `dwStyleEx`  
 [in] `dwStyle`  
 [in] `rect`  
 [in] `pParentWnd`  
 [in] `dwControlBarStyle`  
 [in] `pContext`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="createrow"></a>CDockSite::CreateRow  

  
```  
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,  
    int nOffset,  
    int nRowHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentDockBar`  
 [in] `nOffset`  
 [in] `nRowHeight`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dockpane"></a>CDockSite::DockPane  

  
```  
virtual void DockPane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `dockMethod`  
 [in] `lpRect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="dockpaneleftof"></a>CDockSite::DockPaneLeftOf  
 Acopla un panel a la izquierda de otro panel.  
  
```  
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,  
    CPane* pTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBarToDock`  
 Un puntero al panel quede acoplado a la izquierda del `pTargetBar`.  
  
 [in] [out]`pTargetBar`  
 Un puntero al panel de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel está acoplado correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="doesallowdyninsertbefore"></a>CDockSite::DoesAllowDynInsertBefore  

  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findpanebyid"></a>CDockSite::FindPaneByID  
 Devuelve el panel con el identificador especificado.  
  
```  
CPane* FindPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 El identificador de comando del panel se encuentre.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel con el identificador de comando especificado, o `NULL` si no se encuentra el panel.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="findrowindex"></a>CDockSite::FindRowIndex  

  
```  
int FindRowIndex(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRow`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="fixupvirtualrects"></a>CDockSite::FixupVirtualRects  

  
```  
virtual void FixupVirtualRects();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdocksiteid"></a>CDockSite::GetDockSiteID  

  
```  
virtual UINT GetDockSiteID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdocksiterowslist"></a>CDockSite::GetDockSiteRowsList  

  
```  
const CObList& GetDockSiteRowsList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpanelist"></a>CDockSite::GetPaneList  
 Devuelve una lista de paneles acoplados en el sitio de vinculación.  
  
```  
const CObList& GetPaneList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia de sólo lectura a la lista de paneles acoplados actualmente en la barra de acoplamiento.  
  
##  <a name="isaccessibilitycompatible"></a>CDockSite::IsAccessibilityCompatible  

  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdragmode"></a>CDockSite::IsDragMode  

  
```  
virtual BOOL IsDragMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="islastrow"></a>CDockSite::IsLastRow  

  
```  
bool IsLastRow(CDockingPanesRow* pRow) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRow`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isrectwithindocksite"></a>CDockSite::IsRectWithinDockSite  

  
```  
BOOL IsRectWithinDockSite(
    CRect rect,  
    CPoint& ptDelta);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 [in] `ptDelta`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isresizable"></a>CDockSite::IsResizable  

  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="movepane"></a>CDockSite::MovePane  

  
```  
virtual BOOL MovePane(
    CPane* pWnd,  
    UINT nFlags,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `nFlags`  
 [in] `ptOffset`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="oninsertrow"></a>CDockSite::OnInsertRow  

  
```  
virtual void OnInsertRow(POSITION pos);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pos`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onremoverow"></a>CDockSite::OnRemoveRow  

  
```  
virtual void OnRemoveRow(
    POSITION pos,  
    BOOL bByShow = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pos`  
 [in] `bByShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onresizerow"></a>CDockSite::OnResizeRow  

  
```  
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,  
    int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRowToResize`  
 [in] `nOffset`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsizeparent"></a>CDockSite::OnSizeParent  

  
```  
virtual void OnSizeParent(
    CRect& rectAvailable,  
    UINT nSide,  
    BOOL bExpand,  
    int nOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectAvailable`  
 [in] `nSide`  
 [in] `bExpand`  
 [in] `nOffset`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsetwindowpos"></a>CDockSite::OnSetWindowPos  

  
```  
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,  
    const CRect& rectWnd,  
    UINT nFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndInsertAfter`  
 [in] `rectWnd`  
 [in] `nFlags`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onshowrow"></a>CDockSite::OnShowRow  

  
```  
virtual void OnShowRow(
    POSITION pos,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pos`  
 [in] `bShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="panefrompoint"></a>CDockSite::PaneFromPoint  
 Devuelve un panel que está acoplado en el sitio de vinculación en el punto especificado por el parámetro dado.  
  
```  
virtual CPane* PaneFromPoint(CPoint pt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Un punto, en coordenadas de pantalla para el panel recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al panel situado en el punto especificado o `NULL` si ningún panel estaba presente en el punto especificado.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="rectsidefrompoint"></a>CDockSite::RectSideFromPoint  

  
```  
static int __stdcall RectSideFromPoint(
    const CRect& rect,  
    const CPoint& point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
 [in] `point`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removepane"></a>CDockSite::RemovePane  

  
```  
virtual void RemovePane(
    CPane* pWnd,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `dockMethod`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removerow"></a>CDockSite::RemoveRow  

  
```  
void RemoveRow(CDockingPanesRow* pRow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="replacepane"></a>CDockSite::ReplacePane  

  
```  
BOOL ReplacePane(
    CPane* pOldBar,  
    CPane* pNewBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pOldBar`  
 [in] `pNewBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="repositionpanes"></a>CDockSite::RepositionPanes  

  
```  
virtual void RepositionPanes(CRect& rectNewClientArea);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectNewClientArea`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="resizedocksite"></a>CDockSite::ResizeDockSite  

  
```  
void ResizeDockSite(
    int nNewWidth,  
    int nNewHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nNewWidth`  
 [in] `nNewHeight`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="resizerow"></a>CDockSite::ResizeRow  

  
```  
int ResizeRow(
    CDockingPanesRow* pRow,  
    int nNewSize,  
    BOOL bAdjustLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRow`  
 [in] `nNewSize`  
 [in] `bAdjustLayout`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="showpane"></a>CDockSite::ShowPane  
 Muestra el panel.  
  
```  
virtual BOOL ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] [out]`pBar`  
 Un puntero al panel para mostrar u ocultar.  
  
 [in] `bShow`  
 `TRUE`para especificar que el panel se mostrará; `FALSE` para especificar que se oculta el panel.  
  
 [in] `bDelay`  
 `TRUE`para especificar que el diseño del panel debe retrasarse hasta después de que se muestra el panel; en caso contrario, `FALSE`.  
  
 [in] `bActivate`  
 Este parámetro no se utiliza.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se mostrarse u ocultarse correctamente. `FALSE`Si el panel especificado no pertenece a este sitio de vinculación.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para mostrar u ocultar paneles acoplados. Normalmente, no es necesario llamar a `CDockSite::ShowPane` directamente, porque se llama por la ventana de marco primaria o el panel de base.  
  
##  <a name="showrow"></a>CDockSite::ShowRow  

  
```  
void ShowRow(
    CDockingPanesRow* pRow,  
    BOOL bShow,  
    BOOL bAdjustLayout);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRow`  
 [in] `bShow`  
 [in] `bAdjustLayout`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="swaprows"></a>CDockSite::SwapRows  

  
```  
void SwapRows(
    CDockingPanesRow* pFirstRow,  
    CDockingPanesRow* pSecondRow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFirstRow`  
 [in] `pSecondRow`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
