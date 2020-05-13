---
title: CMFCVisualManagerVS2005 (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetDockingTabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetMDITabsBordersSize
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetPropertyGridGroupColor
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::GetTabFrameColors
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawCaptionButton
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawPaneCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawSeparator
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawTab
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnDrawToolBoxFrame
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnEraseTabsArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillHighlightedArea
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnFillMiniFrameCaption
- AFXVISUALMANAGERVS2005/CMFCVisualManagerVS2005::OnUpdateSystemColors
helpviewer_keywords:
- CMFCVisualManagerVS2005 [MFC], GetDockingTabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetMDITabsBordersSize
- CMFCVisualManagerVS2005 [MFC], GetPropertyGridGroupColor
- CMFCVisualManagerVS2005 [MFC], GetTabFrameColors
- CMFCVisualManagerVS2005 [MFC], HasOverlappedAutoHideButtons
- CMFCVisualManagerVS2005 [MFC], OnDrawAutoHideButtonBorder
- CMFCVisualManagerVS2005 [MFC], OnDrawCaptionButton
- CMFCVisualManagerVS2005 [MFC], OnDrawPaneCaption
- CMFCVisualManagerVS2005 [MFC], OnDrawSeparator
- CMFCVisualManagerVS2005 [MFC], OnDrawTab
- CMFCVisualManagerVS2005 [MFC], OnDrawToolBoxFrame
- CMFCVisualManagerVS2005 [MFC], OnEraseTabsArea
- CMFCVisualManagerVS2005 [MFC], OnFillAutoHideButtonBackground
- CMFCVisualManagerVS2005 [MFC], OnFillHighlightedArea
- CMFCVisualManagerVS2005 [MFC], OnFillMiniFrameCaption
- CMFCVisualManagerVS2005 [MFC], OnUpdateSystemColors
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
ms.openlocfilehash: b92077ecf4670dd5395296327c767ee3c7b848ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319901"
---
# <a name="cmfcvisualmanagervs2005-class"></a>CMFCVisualManagerVS2005 (clase)

`CMFCVisualManagerVS2005`da a una aplicación una apariencia de Microsoft Visual Studio 2005.

## <a name="syntax"></a>Sintaxis

```
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](#getdockingtabsborderssize)|El marco de trabajo llama a este método cuando dibuja un panel que está acoplado y con pestañas. (Reemplaza [CMFCVisualManager::GetDockingTabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getdockingtabsborderssize).)|
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](#getmditabsborderssize)|El marco de trabajo llama a este método para determinar el tamaño de borde de una ventana MDITabs antes de dibujar la ventana. (Reemplaza [CMFCVisualManager::GetMDITabsBordersSize](../../mfc/reference/cmfcvisualmanager-class.md#getmditabsborderssize).)|
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|(Reemplaza [CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#getpropertygridgroupcolor).)|
|[CMFCVisualManagerVS2005::GetTabFrameColors](#gettabframecolors)|(Reemplaza [CMFCVisualManagerOffice2003::GetTabFrameColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#gettabframecolors).)|
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](#hasoverlappedautohidebuttons)|Devuelve si los botones de ocultación automática se superponen en el administrador visual actual. (Reemplaza [CMFCVisualManager::HasOverlappedAutoHideButtons](../../mfc/reference/cmfcvisualmanager-class.md#hasoverlappedautohidebuttons).)|
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|(Reemplaza [CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawautohidebuttonborder).)|
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](#ondrawcaptionbutton)|(Invalida `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`).|
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](#ondrawpanecaption)|(Reemplaza [CMFCVisualManagerOffice2003::OnDrawPaneCaption](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawpanecaption).)|
|[CMFCVisualManagerVS2005::OnDrawSeparator](#ondrawseparator)|(Reemplaza [CMFCVisualManagerOffice2003::OnDrawSeparator](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawseparator).)|
|[CMFCVisualManagerVS2005::OnDrawTab](#ondrawtab)|(Reemplaza [CMFCVisualManagerOffice2003::OnDrawTab](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#ondrawtab).)|
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](#ondrawtoolboxframe)|(Reemplaza [CMFCVisualManager::OnDrawToolBoxFrame](../../mfc/reference/cmfcvisualmanager-class.md#ondrawtoolboxframe).)|
|[CMFCVisualManagerVS2005::OnEraseTabsArea](#onerasetabsarea)|(Reemplaza [CMFCVisualManagerOffice2003::OnEraseTabsArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onerasetabsarea).)|
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|(Reemplaza [CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillautohidebuttonbackground).)|
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](#onfillhighlightedarea)|(Reemplaza [CMFCVisualManagerOffice2003::OnFillHighlightedArea](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onfillhighlightedarea).)|
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](#onfillminiframecaption)|(Invalida `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`).|
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](#onupdatesystemcolors)|(Reemplaza [CMFCVisualManagerOffice2003::OnUpdateSystemColors](../../mfc/reference/cmfcvisualmanageroffice2003-class.md#onupdatesystemcolors).)|

## <a name="remarks"></a>Observaciones

Utilice la cMFCVisualManagerVS2005 clase para cambiar el aspecto visual de la aplicación para parecerse a la de Microsoft Visual Studio 2005.

Todos los miembros de esta clase son funciones virtuales que se derivan del antecesor de esta clase, [CMFCVisualManager (Clase).](../../mfc/reference/cmfcvisualmanager-class.md)

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar el administrador visual VS 2005. Este fragmento de código forma parte del [ejemplo Demostración de alertas](../../overview/visual-cpp-samples.md)de escritorio.

[!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/cpp/cmfcvisualmanagervs2005-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

[CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)

[CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)

[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)

[CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxvisualmanagervs2005.h

## <a name="cmfcvisualmanagervs2005getdockingtabsborderssize"></a><a name="getdockingtabsborderssize"></a>CMFCVisualManagerVS2005::GetDockingTabsBordersSize

```
virtual int GetDockingTabsBordersSize();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005getmditabsborderssize"></a><a name="getmditabsborderssize"></a>CMFCVisualManagerVS2005::GetMDITabsBordersSize

```
virtual int GetMDITabsBordersSize();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManagerVS2005::GetPropertyGridGroupColor

```
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```

### <a name="parameters"></a>Parámetros

[en] *pPropList*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005gettabframecolors"></a><a name="gettabframecolors"></a>CMFCVisualManagerVS2005::GetTabFrameColors

```
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,
    COLORREF& clrDark,
    COLORREF& clrBlack,
    COLORREF& clrHighlight,
    COLORREF& clrFace,
    COLORREF& clrDarkShadow,
    COLORREF& clrLight,
    CBrush*& pbrFace,
    CBrush*& pbrBlack);
```

### <a name="parameters"></a>Parámetros

[en] *pTabWnd*<br/>
[en] *clrDark*<br/>
[en] *clrBlack*<br/>
[en] *clrHighlight*<br/>
[en] *clrFace*<br/>
[en] *clrDarkShadow*<br/>
[en] *clrLight*<br/>
[en] *pbrFace*<br/>
[en] *pbrBlack*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005hasoverlappedautohidebuttons"></a><a name="hasoverlappedautohidebuttons"></a>CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons

```
virtual BOOL HasOverlappedAutoHideButtons() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder

```
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,
    CRect rectBounds,
    CRect rectBorderSize,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rectBounds*<br/>
[en] *rectBorderSize*<br/>
[en] *pButton*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawcaptionbutton"></a><a name="ondrawcaptionbutton"></a>CMFCVisualManagerVS2005::OnDrawCaptionButton

```
virtual void OnDrawCaptionButton(
    CDC* pDC,
    CMFCCaptionButton* pButton,
    BOOL bActive,
    BOOL bHorz,
    BOOL bMaximized,
    BOOL bDisabled,
    int nImageID = -1);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *pButton*<br/>
[en] *bActive*<br/>
[en] *bHorz*<br/>
[en] *bMaximized*<br/>
[en] *bDiscapacitados*<br/>
[en] *nImageID*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManagerVS2005::OnDrawPaneCaption

```
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,
    CDockablePane* pBar,
    BOOL bActive,
    CRect rectCaption,
    CRect rectButtons);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *pBar*<br/>
[en] *bActive*<br/>
[en] *rectCaption*<br/>
[en] *rectButtons*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManagerVS2005::OnDrawSeparator

```
virtual void OnDrawSeparator(
    CDC* pDC,
    CBasePane* pBar,
    CRect rect,
    BOOL bIsHoriz);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *pBar*<br/>
[en] *rect*<br/>
[en] *bIsHoriz*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManagerVS2005::OnDrawTab

```
virtual void OnDrawTab(
    CDC* pDC,
    CRect rectTab,
    int iTab,
    BOOL bIsActive,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rectTab*<br/>
[en] *iTab*<br/>
[en] *bIsActive*<br/>
[en] *pTabWnd*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005ondrawtoolboxframe"></a><a name="ondrawtoolboxframe"></a>CMFCVisualManagerVS2005::OnDrawToolBoxFrame

```
virtual void OnDrawToolBoxFrame(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rect*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005onerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManagerVS2005::OnEraseTabsArea

```
virtual void OnEraseTabsArea(
    CDC* pDC,
    CRect rect,
    const CMFCBaseTabCtrl* pTabWnd);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rect*<br/>
[en] *pTabWnd*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground

```
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,
    CRect rect,
    CMFCAutoHideButton* pButton);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rect*<br/>
[en] *pButton*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a>CMFCVisualManagerVS2005::OnFillHighlightedArea

```
virtual void OnFillHighlightedArea(
    CDC* pDC,
    CRect rect,
    CBrush* pBrush,
    CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rect*<br/>
[en] *pBrush*<br/>
[en] *pButton*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005onfillminiframecaption"></a><a name="onfillminiframecaption"></a>CMFCVisualManagerVS2005::OnFillMiniFrameCaption

```
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,
    CRect rectCaption,
    CPaneFrameWnd* pFrameWnd,
    BOOL bActive);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>
[en] *rectCaption*<br/>
[en] *pFrameWnd*<br/>
[en] *bActive*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcvisualmanagervs2005onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManagerVS2005::OnUpdateSystemColors

```
virtual void OnUpdateSystemColors();
```

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager (Clase)](../../mfc/reference/cmfcvisualmanager-class.md)<br/>
[Clase CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)<br/>
[CMFCVisualManagerWindows (Clase)](../../mfc/reference/cmfcvisualmanagerwindows-class.md)<br/>
[Clase CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)
