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
ms.openlocfilehash: 0ebac4e18f65d789d5196266d57184744ad5ad28
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753628"
---
# <a name="cpanedivider-class"></a>Clase CPaneDivider

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

La `CPaneDivider` clase divide dos paneles, divide dos grupos de paneles o separa un grupo de paneles del área de cliente de la ventana de marco principal.

## <a name="syntax"></a>Sintaxis

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPaneDivider::CPaneDivider](#cpanedivider)||

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPaneDivider::AddPaneContainer](#addpanecontainer)||
|[CPaneDivider::AddPane](#addpane)||
|[CPaneDivider::AddRecentPane](#addrecentpane)||
|[CPaneDivider::CalcExpectedDockedRect](#calcexpecteddockedrect)||
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Reemplaza [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CPaneDivider::CheckVisibility](#checkvisibility)||
|[CPaneDivider::CreateEx](#createex)|(Reemplaza [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Reemplaza [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
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
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Reemplaza [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[CPaneDivider::IsDefault](#isdefault)||
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Reemplaza [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
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

|Nombre|Descripción|
|----------|-----------------|
|[CPaneDivider::GetPanes](#getpanes)|Devuelve la lista de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse solo para los divisores de panel predeterminados.|
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Devuelve la lista de divisores de panel que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse solo para los divisores de panel predeterminados.|

### <a name="data-members"></a>Miembros de datos

|Nombre|Descripción|
|----------|-----------------|
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Especifica el ancho predeterminado en píxeles de todos los divisores de panel de la aplicación.|
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Contiene un puntero a la información `CPaneDivider`de clase en tiempo de ejecución sobre un objeto derivado.|

## <a name="remarks"></a>Observaciones

El marco `CPaneDivider` de trabajo crea objetos automáticamente cuando se acopla un panel.

Hay dos tipos de divisores de panel:

- se crea un divisor de paneles predeterminado cuando un grupo de paneles se acopla a un lado de la ventana de marco principal. El divisor de paneles predeterminado contiene un puntero a la [Clase CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) y redirige la mayoría de las operaciones del grupo de paneles (como cambiar el tamaño de un panel o acoplar otro panel o contenedor) al administrador de contenedores. Cada panel de acoplamiento mantiene un puntero a su divisor de panel predeterminado.

- Un divisor de paneles normal solo divide dos paneles en un contenedor. Para obtener más información, vea [CPaneContainer (Clase)](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo obtener un objeto `CPaneDivider` desde un objeto `CWorkspaceBar`. Este fragmento de código forma parte del ejemplo de demostración de [pestañas MDI.](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[Cobject](../../mfc/reference/cobject-class.md)\
.&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CBasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[CPaneDivider](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxPaneDivider.h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider::SetAutoHideMode

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Parámetros

[en] *bMode*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Parámetros

[en] *p*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider::AddPane

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer

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

[en] *barContainerManager*<br/>
[en] *bOuterEdge*<br/>
[en] *pTargetBar*<br/>
[en] *dwAlignment*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider::AddRecentPane

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect

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

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout

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

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider::CheckVisibility

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider::CPaneDivider

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parámetros

[en] *bDefaultSlider*<br/>
[en] *pParent*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividercreateex"></a><a name="createex"></a>CPaneDivider::CreateEx

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

[en] *dwStyleEx*<br/>
[en] *dwStyle*<br/>
[en] *rect*<br/>
[en] *pParentWnd*<br/>
[en] *nID*<br/>
[en] *pContext*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider::DoesContainFloatingPane

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>
[en] *bLeftBar*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Parámetros

[en] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider::GetFirstPane

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider::GetPaneDividers

Devuelve la lista de divisores de panel que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse solo para los divisores de panel predeterminados.

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Parámetros

*lstSliders*<br/>
[fuera] Contiene la lista de divisores de panel que residen en el contenedor del panel.

### <a name="remarks"></a>Observaciones

Este método debe llamarse solo para los divisores de panel predeterminados. Un divisor de paneles predeterminado es un divisor que cambia el tamaño de todo el contenedor del panel.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider::GetPanes

Devuelve la lista de paneles que residen en la [clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse solo para recuperar los divisores de panel predeterminados.

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Parámetros

*lstBars*<br/>
[fuera] Contiene la lista de paneles que residen en el contenedor del panel.

### <a name="remarks"></a>Observaciones

Este método debe llamarse solo para los divisores de panel predeterminados. Un divisor de paneles predeterminado es un divisor que cambia el tamaño de todo el contenedor del panel.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider::GetWidth

```
int GetWidth() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerinit"></a><a name="init"></a>CPaneDivider::Init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Parámetros

[en] *bDefaultSlider*<br/>
[en] *pParent*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider::InsertPane

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

[en] *pBarToInsert*<br/>
[en] *pTargetBar*<br/>
[en] *dwAlignment*<br/>
[en] *lpRect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider::IsAutoHideMode

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider::IsDefault

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider::IsHorizontal

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth

Especifica el ancho predeterminado, en píxeles, de todos los divisores de panel de la aplicación.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a>CPaneDivider::Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *ptOffset*<br/>
[en] *bAdjustLayout*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC

Contiene un puntero a la `CPaneDivider`información de clase en tiempo de ejecución sobre un objeto derivado.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Observaciones

Establezca esta variable miembro si crea un divisor de panel personalizado. Esto permite que el marco de trabajo cree el divisor de paneles cuando se dibuja el panel.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente `m_pSliderRTC` se muestra cómo establecer la variable miembro:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Observaciones

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>
[en] *bMostrar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider::RemovePane

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider::ReplacePane

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Parámetros

[en] *pBarToReplace*<br/>
[en] *pBarToReplaceWith*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider::RepositionPanes

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Parámetros

[en] *rectNew*<br/>
[en] *hdwp*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider::Serialize

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

[en] *ar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider::ShowWindow

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Parámetros

[en] *nCmdShow*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Parámetros

[en] *pBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo

```cpp
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Parámetros

[en] *pDockingBar*<br/>
[en] *pTabbedBar*<br/>

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[Clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md)<br/>
[CDockingManager (clase)](../../mfc/reference/cdockingmanager-class.md)<br/>
[CBasePane (clase)](../../mfc/reference/cbasepane-class.md)
