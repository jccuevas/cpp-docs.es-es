---
title: CMultiPaneFrameWnd Clase
ms.date: 11/04/2016
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
ms.openlocfilehash: db5f0b3c6b48a3704803d77242904e25e053b7ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363393"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd Clase

La `CMultiPaneFrameWnd` clase extiende [CPaneFrameWnd (Clase).](../../mfc/reference/cpaneframewnd-class.md) Puede admitir varios paneles. En lugar de un único identificador `CMultiPaneFrameWnd` incrustado en una barra de control, contiene `CMultiPaneFrameWnd` un [CPaneContainerManager clase](../../mfc/reference/cpanecontainermanager-class.md) objeto que permite al usuario acoplar uno a otro y crear dinámicamente varias ventanas flotantes con pestañas.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMultiPaneFrameWnd::AddPane](#addpane)|Agrega un panel. (Reemplaza [CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane).)|
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajusta el diseño de la ventana de marco reducido. (Reemplaza [CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(Reemplaza [CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes).)|
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada. (Reemplaza [CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect).)|
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|Determina si el panel actual puede acoplarse a otro panel o ventana de marco. (Reemplaza [CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Determina si la ventana de marco pequeño puede acoplarse a un panel. (Reemplaza [CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(Reemplaza [CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|(Invalida `CPaneFrameWnd::CloseMiniFrame`).|
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte el panel en un documento con pestañas. (Reemplaza [CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||
|[CMultiPaneFrameWnd::DockPane](#dockpane)|Acopla el panel. (Reemplaza [CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|Devuelve el texto del título. (Reemplaza [CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|Devuelve una referencia al objeto de administrador de contenedores interno.|
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Devuelve el primer panel visible que se encuentra en una ventana de marco reducido. (Reemplaza [CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane).)|
|[CMultiPaneFrameWnd::GetPane](#getpane)|Devuelve un panel que se encuentra en la ventana de marco reducido. (Reemplaza [CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|Devuelve el número de paneles que se encuentran en una ventana de marco reducido. (Reemplaza [CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido. (Reemplaza [CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount).)|
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||
|[CMultiPaneFrameWnd::LoadState](#loadstate)|Carga el estado del panel desde el registro. (Reemplaza [CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Acopla la ventana de marco reducido en su posición más reciente. (Reemplaza [CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos).)|
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Detiene el temporizador de despliegue. (Reemplaza [CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer).)|
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Ajusta el diseño de un panel dentro de una ventana de marco pequeño. (Reemplaza [CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Establece el temporizador de despliegue. (Reemplaza [CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido. (Reemplaza [CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido. (Reemplaza [CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint).)|
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Llamado por el marco de trabajo para quitar los paneles no válidos. (Reemplaza [CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes).)|
|[CMultiPaneFrameWnd::RemovePane](#removepane)|Quita un panel de la ventana de marco reducido. (Reemplaza [CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane).)|
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|Reemplaza un panel con otro. (Reemplaza [CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|
|[CMultiPaneFrameWnd::SaveState](#savestate)|Guarda el estado del panel en el registro. (Reemplaza [CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate).)|
|[CMultiPaneFrameWnd::Serialize](#serialize)|(Invalida `CPaneFrameWnd::Serialize`).|
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|Establece el estado de acoplamiento. (Reemplaza [CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|Establece el estado de preacoplamiento. (Reemplaza [CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(Reemplaza [CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(Reemplaza [CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|

## <a name="remarks"></a>Observaciones

La mayoría de los métodos de esta clase invalidar métodos en el [CPaneFrameWnd clase.](../../mfc/reference/cpaneframewnd-class.md)

Si un panel utiliza el estilo AFX_CBRS_AUTO_ROLLUP y el usuario acopla ese panel a una ventana de marco de varios paneles, el usuario puede enrollar la ventana independientemente de la configuración de estilo de los otros paneles acoplados.

El marco de `CMultiPaneFrameWnd` trabajo crea automáticamente un objeto cuando el usuario flota un panel que usa el estilo CBRS_FLOAT_MULTI.

Para obtener información sobre cómo `CPaneFrameWnd` derivar una clase de la clase y crearla dinámicamente, vea [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMultiPaneFrameWnd` cómo recuperar un puntero a un objeto. Este fragmento de código forma parte del [ejemplo Establecer tamaño](../../overview/visual-cpp-samples.md)de panel .

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxMultiPaneFrameWnd.h

## <a name="cmultipaneframewndaddpane"></a><a name="addpane"></a>CMultiPaneFrameWnd::AddPane

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parámetros

[en] *pWnd*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndaddrecentpane"></a><a name="addrecentpane"></a>CMultiPaneFrameWnd::AddRecentPane

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndadjustlayout"></a><a name="adjustlayout"></a>CMultiPaneFrameWnd::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CMultiPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CMultiPaneFrameWnd::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parámetros

[en] *pWndToDock*<br/>
[en] *ptMouse*<br/>
[en] *rectResult*<br/>
[en] *bDrawTab*<br/>
[en] *ppTargetBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndcanbeattached"></a><a name="canbeattached"></a>CMultiPaneFrameWnd::CanBeAttached

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CMultiPaneFrameWnd::CanBeDockedToPane

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parámetros

[en] *pDockingBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CMultiPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndcloseminiframe"></a><a name="closeminiframe"></a>CMultiPaneFrameWnd::CloseMiniFrame

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CMultiPaneFrameWnd::ConvertToTabbedDocument

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewnddockframe"></a><a name="dockframe"></a>CMultiPaneFrameWnd::DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>Parámetros

[en] *pDockedFrame*<br/>
[en] *dockMethod*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewnddockpane"></a><a name="dockpane"></a>CMultiPaneFrameWnd::DockPane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>Parámetros

[en] *pDockedBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewnddockrecentpanetomainframe"></a><a name="dockrecentpanetomainframe"></a>CMultiPaneFrameWnd::DockRecentPaneToMainFrame

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CMultiPaneFrameWnd::GetCaptionText

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CMultiPaneFrameWnd::GetFirstVisiblePane

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndgetpane"></a><a name="getpane"></a>CMultiPaneFrameWnd::GetPane

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndgetpanecontainermanager"></a><a name="getpanecontainermanager"></a>CMultiPaneFrameWnd::GetPaneContainerManager

Devuelve una referencia al objeto de administrador de contenedores interno.

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al objeto de administrador de contenedores interno.

### <a name="remarks"></a>Observaciones

Este método se puede utilizar para tener acceso a la [interna CPaneContainerManager (clase)](../../mfc/reference/cpanecontainermanager-class.md) objeto.

## <a name="cmultipaneframewndgetpanecount"></a><a name="getpanecount"></a>CMultiPaneFrameWnd::GetPaneCount

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CMultiPaneFrameWnd::GetVisiblePaneCount

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndinsertpane"></a><a name="insertpane"></a>CMultiPaneFrameWnd::InsertPane

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>Parámetros

[en] *pControlBar*<br/>
[en] *pTarget*<br/>
[en] *bDespués*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndloadstate"></a><a name="loadstate"></a>CMultiPaneFrameWnd::LoadState

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

[en] *lpszProfileName*<br/>
[en] *uiID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CMultiPaneFrameWnd::OnDockToRecentPos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CMultiPaneFrameWnd::OnKillRollUpTimer

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CMultiPaneFrameWnd::OnPaneRecalcLayout

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CMultiPaneFrameWnd::OnSetRollUpTimer

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndonshowpane"></a><a name="onshowpane"></a>CMultiPaneFrameWnd::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>
[en] *bMostrar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CMultiPaneFrameWnd::PaneFromPoint

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>Parámetros

[en] *punto*<br/>
[en] *nSensibilidad*<br/>
[en] *bCheckVisibility*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CMultiPaneFrameWnd::RemoveNonValidPanes

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndremovepane"></a><a name="removepane"></a>CMultiPaneFrameWnd::RemovePane

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>
[en] *bDestroy*<br/>
[en] *bNoDelayedDestroy*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndreplacepane"></a><a name="replacepane"></a>CMultiPaneFrameWnd::ReplacePane

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parámetros

[en] *pBarOrg*<br/>
[en] *pBarReplaceWith*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndsavestate"></a><a name="savestate"></a>CMultiPaneFrameWnd::SaveState

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

[en] *lpszProfileName*<br/>
[en] *uiID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndserialize"></a><a name="serialize"></a>CMultiPaneFrameWnd::Serialize

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

[en] *ar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndsetdockstate"></a><a name="setdockstate"></a>CMultiPaneFrameWnd::SetDockState

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parámetros

[en] *pDockManager*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndsetlastfocusedpane"></a><a name="setlastfocusedpane"></a>CMultiPaneFrameWnd::SetLastFocusedPane

```
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>Parámetros

[en] *hwnd*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CMultiPaneFrameWnd::SetPreDockState

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>Parámetros

[en] *preDockState*<br/>
[en] *pBarToDock*<br/>
[en] *dockMethod*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CMultiPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmultipaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CMultiPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parámetros

[en] *pDockingBar*<br/>
[en] *pTabbedBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd (clase)](../../mfc/reference/cpaneframewnd-class.md)
