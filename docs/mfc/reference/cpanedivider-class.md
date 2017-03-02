---
title: Clase CPaneDivider | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneDivider
dev_langs:
- C++
helpviewer_keywords:
- CPaneDivider class
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
caps.latest.revision: 25
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
ms.openlocfilehash: b1c6b8b608deb2c81a2a646345ee4020c27820e7
ms.lasthandoff: 02/24/2017

---
# <a name="cpanedivider-class"></a>Clase CPaneDivider
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 La `CPaneDivider` clase divide dos paneles, dos grupos de paneles o separa un grupo de paneles del área de cliente de la ventana de marco principal.  
  
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
|[CPaneDivider::CalcFixedLayout](#calcfixedlayout)|(Invalida [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CPaneDivider::CheckVisibility](#checkvisibility)||  
|[CPaneDivider::CreateEx](#createex)|(Invalida [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).)|  
|[CPaneDivider::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|(Invalida [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
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
|[CPaneDivider::IsAutoHideMode](#isautohidemode)|(Invalida [CBasePane::IsAutoHideMode](../../mfc/reference/cbasepane-class.md#isautohidemode).)|  
|[CPaneDivider::IsDefault](#isdefault)||  
|[CPaneDivider::IsHorizontal](#ishorizontal)|(Invalida [CBasePane::IsHorizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|  
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
|[CPaneDivider::GetPanes](#getpanes)|Devuelve la lista de paneles que residen en el [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse únicamente para los divisores de los paneles de forma predeterminada.|  
|[CPaneDivider::GetPaneDividers](#getpanedividers)|Devuelve la lista de los divisores de los paneles que residen en el [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse únicamente para los divisores de los paneles de forma predeterminada.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaneDivider::m_nDefaultWidth](#m_ndefaultwidth)|Especifica el ancho predeterminado en píxeles de todos los divisores de los paneles de la aplicación.|  
|[CPaneDivider::m_pSliderRTC](#m_psliderrtc)|Contiene un puntero a la información de clase en tiempo de ejecución sobre un `CPaneDivider`-objeto derivado.|  
  
## <a name="remarks"></a>Comentarios  
 El marco de trabajo crea `CPaneDivider` objetos automáticamente cuando se acopla a un panel.  
  
 Hay dos tipos de divisores de:  
  
-   se crea un divisor de forma predeterminada cuando un grupo de paneles se acopla a un lado de la ventana de marco principal. El divisor de paneles predeterminada contiene un puntero a la [CPaneContainerManager clase](../../mfc/reference/cpanecontainermanager-class.md) y redirige la mayoría de las operaciones en el grupo de paneles (como cambiar el tamaño de un panel o acoplamiento otro panel o contenedor) al administrador de contenedor. Cada panel acoplable mantiene un puntero a su panel divisor de forma predeterminada.  
  
-   Un divisor regular simplemente divide dos paneles en un contenedor. Para obtener más información, consulte [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo obtener un objeto `CPaneDivider` desde un objeto `CWorkspaceBar`. Este fragmento de código forma parte de la [ejemplo de demostración de las fichas de MDI](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MDITabsDemo&#5;](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxPaneDivider.h  
  
##  <a name="a-namesetautohidemodea--cpanedividersetautohidemode"></a><a name="setautohidemode"></a>CPaneDivider::SetAutoHideMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetAutoHideMode(BOOL bMode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMode`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpanecontainermanagera--cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a>CPaneDivider::SetPaneContainerManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPaneContainerManager(CPaneContainerManager* p);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `p`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddpanea--cpanedivideraddpane"></a><a name="addpane"></a>CPaneDivider::AddPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AddPane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddpanecontainera--cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a>CPaneDivider::AddPaneContainer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
 [in] `barContainerManager`  
 [in] `bOuterEdge`  
 [in] `pTargetBar`  
 [in] `dwAlignment`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddrecentpanea--cpanedivideraddrecentpane"></a><a name="addrecentpane"></a>CPaneDivider::AddRecentPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcexpecteddockedrecta--cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneDivider::CalcExpectedDockedRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,  
    CPoint ptMouse,  
    CRect& rectResult,  
    BOOL& bDrawTab,  
    CDockablePane** ppTargetBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndToDock`  
 [in] `ptMouse`  
 [in] `rectResult`  
 [in] `bDrawTab`  
 [in] `ppTargetBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcfixedlayouta--cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a>CPaneDivider::CalcFixedLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
  
##  <a name="a-namecheckvisibilitya--cpanedividercheckvisibility"></a><a name="checkvisibility"></a>CPaneDivider::CheckVisibility  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CheckVisibility();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecpanedividera--cpanedividercpanedivider"></a><a name="cpanedivider"></a>CPaneDivider::CPaneDivider  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPaneDivider();

 
CPaneDivider(
    BOOL bDefaultSlider,  
    CWnd* pParent = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDefaultSlider`  
 [in] `pParent`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreateexa--cpanedividercreateex"></a><a name="createex"></a>CPaneDivider::CreateEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
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
 [in] `dwStyleEx`  
 [in] `dwStyle`  
 [in] `rect`  
 [in] `pParentWnd`  
 [in] `nID`  
 [in] `pContext`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedoesallowdyninsertbeforea--cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CPaneDivider::DoesAllowDynInsertBefore  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedoescontainfloatingpanea--cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a>CPaneDivider::DoesContainFloatingPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DoesContainFloatingPane();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindpanecontainera--cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a>CPaneDivider::FindPaneContainer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,  
    BOOL& bLeftBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 [in] `bLeftBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindtabbedpanea--cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a>CPaneDivider::FindTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockablePane* FindTabbedPane(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdefaultwidtha--cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a>CPaneDivider::GetDefaultWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static int __stdcall GetDefaultWidth();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetfirstpanea--cpanedividergetfirstpane"></a><a name="getfirstpane"></a>CPaneDivider::GetFirstPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
const CBasePane* GetFirstPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanedividersa--cpanedividergetpanedividers"></a><a name="getpanedividers"></a>CPaneDivider::GetPaneDividers  
 Devuelve la lista de los divisores de los paneles que residen en el [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md). Este método debe llamarse únicamente para los divisores de los paneles de forma predeterminada.  
  
```  
void GetPaneDividers(CObList& lstSliders);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lstSliders`  
 Contiene la lista de los divisores de los paneles que residen en el contenedor del panel.  
  
### <a name="remarks"></a>Comentarios  
 Este método debe llamarse para divisores de paneles predeterminada solo. Un divisor de paneles predeterminada es un divisor que cambia el tamaño del contenedor de panel completo.  
  
##  <a name="a-namegetpanedividerstylea--cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a>CPaneDivider::GetPaneDividerStyle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
DWORD GetPaneDividerStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanesa--cpanedividergetpanes"></a><a name="getpanes"></a>CPaneDivider::GetPanes  
 Devuelve la lista de paneles que residen en el [CPaneContainer clase](../../mfc/reference/cpanecontainer-class.md). Debe llamar a este método para recuperar los divisores de los paneles de forma predeterminada.  
  
```  
void GetPanes(CObList& lstBars);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `lstBars`  
 Contiene la lista de paneles que residen en el contenedor del panel.  
  
### <a name="remarks"></a>Comentarios  
 Este método debe llamarse para divisores de paneles predeterminada solo. Un divisor de paneles predeterminada es un divisor que cambia el tamaño del contenedor de panel completo.  
  
##  <a name="a-namegetrootcontainerrecta--cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a>CPaneDivider::GetRootContainerRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetRootContainerRect();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetwidtha--cpanedividergetwidth"></a><a name="getwidth"></a>CPaneDivider::GetWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinita--cpanedividerinit"></a><a name="init"></a>CPaneDivider::Init  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Init(
    BOOL bDefaultSlider = FALSE,  
    CWnd* pParent = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDefaultSlider`  
 [in] `pParent`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinsertpanea--cpanedividerinsertpane"></a><a name="insertpane"></a>CPaneDivider::InsertPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,  
    CDockablePane* pTargetBar,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToInsert`  
 [in] `pTargetBar`  
 [in] `dwAlignment`  
 [in] `lpRect`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisautohidemodea--cpanedividerisautohidemode"></a><a name="isautohidemode"></a>CPaneDivider::IsAutoHideMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdefaulta--cpanedividerisdefault"></a><a name="isdefault"></a>CPaneDivider::IsDefault  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDefault() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameishorizontala--cpanedividerishorizontal"></a><a name="ishorizontal"></a>CPaneDivider::IsHorizontal  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namemndefaultwidtha--cpanedividermndefaultwidth"></a><a name="m_ndefaultwidth"></a>CPaneDivider::m_nDefaultWidth  
 Especifica el ancho predeterminado, en píxeles, de todos los divisores de los paneles de la aplicación.  
  
```  
AFX_IMPORT_DATA static int m_nDefaultWidth;  
```  
  
##  <a name="a-namemovea--cpanedividermove"></a><a name="move"></a>CPaneDivider::Move  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Move(
    CPoint& ptOffset,  
    BOOL bAdjustLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptOffset`  
 [in] `bAdjustLayout`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namempsliderrtca--cpanedividermpsliderrtc"></a><a name="m_psliderrtc"></a>CPaneDivider::m_pSliderRTC  
 Contiene un puntero a la información de clase en tiempo de ejecución sobre un `CPaneDivider`-objeto derivado.  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si se crea un divisor de paneles personalizados, establecer esta variable miembro. Esto permite al marco crear su panel divisor cuando se dibuja el panel.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo establecer el `m_pSliderRTC` variable miembro:  
  
```  
class CMySplitter : public CPaneDivider  
{  
...  
};  
 
CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```  
  
##  <a name="a-namenotifyaboutreleasea--cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a>CPaneDivider::NotifyAboutRelease  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void NotifyAboutRelease();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonshowpanea--cpanedivideronshowpane"></a><a name="onshowpane"></a>CPaneDivider::OnShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 [in] `bShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namereleaseemptypanecontainersa--cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a>CPaneDivider::ReleaseEmptyPaneContainers  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ReleaseEmptyPaneContainers();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremovepanea--cpanedividerremovepane"></a><a name="removepane"></a>CPaneDivider::RemovePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RemovePane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namereplacepanea--cpanedividerreplacepane"></a><a name="replacepane"></a>CPaneDivider::ReplacePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,  
    CDockablePane* pBarToReplaceWith);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarToReplace`  
 [in] `pBarToReplaceWith`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerepositionpanesa--cpanedividerrepositionpanes"></a><a name="repositionpanes"></a>CPaneDivider::RepositionPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RepositionPanes(
    CRect& rectNew,  
    HDWP& hdwp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectNew`  
 [in] `hdwp`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameserializea--cpanedividerserialize"></a><a name="serialize"></a>CPaneDivider::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameshowwindowa--cpanedividershowwindow"></a><a name="showwindow"></a>CPaneDivider::ShowWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ShowWindow(int nCmdShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCmdShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestorerecentdocksiteinfoa--cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneDivider::StoreRecentDockSiteInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestorerecenttabrelatedinfoa--cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneDivider::StoreRecentTabRelatedInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockingBar`  
 [in] `pTabbedBar`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)   
 [Clase CPaneContainer](../../mfc/reference/cpanecontainer-class.md)   
 [Clase CDockingManager](../../mfc/reference/cdockingmanager-class.md)   
 [Clase CBasePane](../../mfc/reference/cbasepane-class.md)

