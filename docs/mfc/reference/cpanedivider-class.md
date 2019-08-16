---
title: Clase CPaneDivider
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: d4888fbf2a95652b0a38adc8ecd059a7515636cb
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866113"
---
# <a name="cpanedivider-class"></a>Clase CPaneDivider

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

La `CPaneDivider` clase divide dos paneles, divide dos grupos de paneles o separa un grupo de paneles del área cliente de la ventana de marco principal.

## <a name="syntax"></a>Sintaxis

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Invalida [a cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)).|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Invalida [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)).|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Invalida [a cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)).|
|[CPaneDivider::DoesContainFloatingPane](#doescontainfloatingpane)||
|[CPaneDivider::FindPaneContainer](#findpanecontainer)||
|[CPaneDivider::FindTabbedPane](#findtabbedpane)||
|[CPaneDivider::GetDefaultWidth](#getdefaultwidth)||
|[CPaneDivider::GetFirstPane](#getfirstpane)||
|[CPaneDivider::GetPaneDividerStyle](#getpanedividerstyle)||
|[CPaneDivider::GetRootContainerRect](#getrootcontainerrect)||
|[CPaneDivider::GetWidth](#getwidth)||
|[CPaneDivider::Init](#init)||
|[CPaneDivider::InsertPane](#insertpane)||
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Invalida [a cbasepane:: IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode)).|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Invalida [a cbasepane:: IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal)).|
|[CPaneDivider::Move](#move)||
|[CPaneDivider::NotifyAboutRelease](#notifyaboutrelease)||
|[CPaneDivider::OnShowPane](#onshowpane)||
|[CPaneDivider::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)||
|[CPaneDivider::RemovePane](#removepane)||
|[CPaneDivider::ReplacePane](#replacepane)||
|[CPaneDivider::RepositionPanes](#repositionpanes)||
|[CPaneDivider::Serialize](#serialize)|(Invalida `CBasePane::Serialize`).|
|[CPaneDivider::SetAutoHideMode](#setautohidemode)||
|[CPaneDivider::SetPaneContainerManager](#setpanecontainermanager)||
|[CPaneDivider::ShowWindow](#showwindow)||
|[CPaneDivider::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneDivider::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Devuelve la lista de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Solo se debe llamar a este método para los divisores de paneles predeterminados.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Devuelve la lista de divisores de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Solo se debe llamar a este método para los divisores de paneles predeterminados.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Especifica el ancho predeterminado, en píxeles, de todos los divisores de paneles de la aplicación.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Contiene un puntero a la información de clase en tiempo `CPaneDivider`de ejecución sobre un objeto derivado de.|

## <a name="remarks"></a>Comentarios

El marco de `CPaneDivider` trabajo crea objetos automáticamente cuando se acopla un panel.

Hay dos tipos de divisores de paneles:

- Cuando un grupo de paneles está acoplado a un lado de la ventana de marco principal, se crea un divisor de panel predeterminado. El divisor del panel predeterminado contiene un puntero a la [clase CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) y redirige la mayoría de las operaciones en el grupo de paneles (como el cambio de tamaño de un panel o el acoplamiento de otro panel o contenedor) al administrador de contenedores. Cada panel de acoplamiento mantiene un puntero a su divisor de panel predeterminado.

- Un divisor de panel normal solo divide dos paneles en un contenedor. Para obtener más información, consulte [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo obtener un objeto `CPaneDivider` desde un objeto `CWorkspaceBar`. Este fragmento de código forma parte del [ejemplo de demostración de pestañas MDI](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[A cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxPaneDivider. h

##  <a name="setautohidemode"></a>  CPaneDivider::SetAutoHideMode

```
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parámetros

de *bMode*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setpanecontainermanager"></a>  CPaneDivider::SetPaneContainerManager

```
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parámetros

[in] *p*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="addpane"></a>  CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="addpanecontainer"></a>  CPaneDivider::AddPaneContainer

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Parámetros

de *barContainerManager*<br/>
de *bOuterEdge*<br/>
de *pTargetBar*<br/>
de *dwAlignment*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="addrecentpane"></a>  CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="calcexpecteddockedrect"></a>  CPaneDivider::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Parámetros

de *pWndToDock*<br/>
de *ptMouse*<br/>
de *rectResult*<br/>
de *bDrawTab*<br/>
de *ppTargetBar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="calcfixedlayout"></a>  CPaneDivider::CalcFixedLayout

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

##  <a name="checkvisibility"></a>  CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="cpanedivider"></a>  CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parámetros

de *bDefaultSlider*<br/>
de *pParent*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="createex"></a>  CPaneDivider::CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Parámetros

de *dwStyleEx*<br/>
de *dwStyle*<br/>
de *rectángulo*<br/>
de *pParentWnd*<br/>
[in] *nID*<br/>
de *pContext*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="doesallowdyninsertbefore"></a>  CPaneDivider::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="doescontainfloatingpane"></a>  CPaneDivider::DoesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="findpanecontainer"></a>  CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>
de *bLeftBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="findtabbedpane"></a>  CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parámetros

[in] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getdefaultwidth"></a>  CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getfirstpane"></a>  CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanedividers"></a>  CPaneDivider::GetPaneDividers

Devuelve la lista de divisores de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Solo se debe llamar a este método para los divisores de paneles predeterminados.

```
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parámetros

*lstSliders*<br/>
enuncia Contiene la lista de divisores de paneles que residen en el contenedor del panel.

### <a name="remarks"></a>Comentarios

Solo se debe llamar a este método para los divisores de panel predeterminados. Un divisor de panel predeterminado es un divisor que cambia el tamaño del contenedor del panel completo.

##  <a name="getpanedividerstyle"></a>  CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getpanes"></a>  CPaneDivider::GetPanes

Devuelve la lista de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Solo se debe llamar a este método para recuperar los divisores de paneles predeterminados.

```
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parámetros

*lstBars*<br/>
enuncia Contiene la lista de paneles que residen en el contenedor del panel.

### <a name="remarks"></a>Comentarios

Solo se debe llamar a este método para los divisores de panel predeterminados. Un divisor de panel predeterminado es un divisor que cambia el tamaño del contenedor del panel completo.

##  <a name="getrootcontainerrect"></a>  CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getwidth"></a>  CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="init"></a>  CPaneDivider::Init

```
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parámetros

de *bDefaultSlider*<br/>
de *pParent*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="insertpane"></a>  CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

de *pBarToInsert*<br/>
de *pTargetBar*<br/>
de *dwAlignment*<br/>
de *lpRect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isautohidemode"></a>  CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="isdefault"></a>  CPaneDivider::IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ishorizontal"></a>  CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="m_ndefaultwidth"></a>  CPaneDivider::m_nDefaultWidth

Especifica el ancho predeterminado, en píxeles, de todos los divisores de paneles de la aplicación.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

##  <a name="move"></a>  CPaneDivider::Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parámetros

[in] *ptOffset*<br/>
de *bAdjustLayout*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="m_psliderrtc"></a>  CPaneDivider::m_pSliderRTC

Contiene un puntero a información de clase en tiempo `CPaneDivider`de ejecución sobre un objeto derivado de.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Comentarios

Establezca esta variable miembro si crea un divisor del panel personalizado. Esto permite al marco de trabajo crear el divisor del panel cuando se dibuja el panel.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer `m_pSliderRTC` la variable miembro:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

##  <a name="notifyaboutrelease"></a>  CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Comentarios

##  <a name="onshowpane"></a>  CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>
de *bShow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="releaseemptypanecontainers"></a>  CPaneDivider::ReleaseEmptyPaneContainers

```
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Comentarios

##  <a name="removepane"></a>  CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="replacepane"></a>  CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parámetros

de *pBarToReplace*<br/>
de *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="repositionpanes"></a>  CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parámetros

de *rectNew*<br/>
[in] *hdwp*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="serialize"></a>  CPaneDivider::Serialize

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

de *ar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="showwindow"></a>CPaneDivider:: ShowWindow

```
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parámetros

de *nCmdShow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="storerecentdocksiteinfo"></a>  CPaneDivider::StoreRecentDockSiteInfo

```
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="storerecenttabrelatedinfo"></a>  CPaneDivider::StoreRecentTabRelatedInfo

```
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parámetros

de *pDockingBar*<br/>
de *pTabbedBar*<br/>

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPaneContainerManager (clase)](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[CPaneContainer (clase)](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager (clase)](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
