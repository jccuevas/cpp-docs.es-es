---
title: Clase CMultiPaneFrameWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMultiPaneFrameWnd
dev_langs:
- C++
helpviewer_keywords:
- CMultiPaneFrameWnd class
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
caps.latest.revision: 36
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
ms.openlocfilehash: 4332533097b6e2463c21065ef361969397cacf5e
ms.lasthandoff: 02/24/2017

---
# <a name="cmultipaneframewnd-class"></a>Clase CMultiPaneFrameWnd
El `CMultiPaneFrameWnd` amplía la clase [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md). Puede admitir varios paneles. En lugar de un único identificador incrustado para una barra de controles, `CMultiPaneFrameWnd` contiene un [CPaneContainerManager clase](../../mfc/reference/cpanecontainermanager-class.md) objeto que permite al usuario acoplar un `CMultiPaneFrameWnd` a otro y dinámicamente crear varias ventanas flotantes con pestañas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMultiPaneFrameWnd::AddPane](#addpane)|Agrega un panel. (Invalida [CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane).)|  
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||  
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajusta el diseño de la ventana de marco reducido. (Invalida [CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout).)|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(Invalida [CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes).)|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada. (Invalida [CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect).)|  
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|Determina si puede acoplar el panel actual a otra ventana de panel o marco. (Invalida [CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached).)|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Determina si la ventana de marco reducido puede acoplar un panel. (Invalida [CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane).)|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(Invalida [CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility).)|  
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|(Invalida `CPaneFrameWnd::CloseMiniFrame`).|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte el panel en un documento con pestañas. (Invalida [CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument).)|  
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||  
|[CMultiPaneFrameWnd::DockPane](#dockpane)|Acopla el panel. (Invalida [CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane).)|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||  
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|Devuelve el texto del título. (Invalida [CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext).)|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|Devuelve una referencia al objeto de administrador de contenedor interna.|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Devuelve el primer panel visible que se encuentra en una ventana de marco reducido. (Invalida [CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane).)|  
|[CMultiPaneFrameWnd::GetPane](#getpane)|Devuelve un panel que se encuentra en la ventana de marco reducido. (Invalida [CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane).)|  
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|Devuelve el número de paneles que se encuentran en una ventana de marco reducido. (Invalida [CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount).)|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido. (Invalida [CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount).)|  
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||  
|[CMultiPaneFrameWnd::LoadState](#loadstate)|Carga el estado del panel desde el registro. (Invalida [CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate).)|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Acopla la ventana de marco reducido en su posición más reciente. (Invalida [CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos).)|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Detiene el temporizador de despliegue. (Invalida [CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer).)|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Ajusta el diseño de un panel dentro de una ventana de marco reducido. (Invalida [CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout).)|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Establece el temporizador de despliegue. (Invalida [CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer).)|  
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido. (Invalida [CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane).)|  
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido. (Invalida [CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint).)|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Llamado por el marco de trabajo para quitar los paneles no válidos. (Invalida [CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes).)|  
|[CMultiPaneFrameWnd::RemovePane](#removepane)|Quita un panel de la ventana de marco reducido. (Invalida [CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane).)|  
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|Reemplaza un panel con otro. (Invalida [CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane).)|  
|[CMultiPaneFrameWnd::SaveState](#savestate)|Guarda el estado del panel en el registro. (Invalida [CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate).)|  
|[CMultiPaneFrameWnd::Serialize](#serialize)|(Invalida `CPaneFrameWnd::Serialize`).|  
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|Establece el estado de acoplamiento. (Invalida [CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate).)|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||  
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|Establece el estado predocking. (Invalida [CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate).)|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(Invalida [CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo).)|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(Invalida [CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo).)|  
  
## <a name="remarks"></a>Comentarios  
 La mayoría de los métodos de esta clase reemplazan los métodos de la [CPaneFrameWnd clase](../../mfc/reference/cpaneframewnd-class.md) clase.  
  
 Si usa un panel de la `AFX_CBRS_AUTO_ROLLUP` estilo y el usuario acopla ese panel en una ventana de marco de varios paneles, el usuario puede resumir de la ventana, independientemente de la configuración de estilo de los otros paneles acoplados.  
  
 El marco de trabajo crea automáticamente un `CMultiPaneFrameWnd` objeto cuando el usuario desplaza un panel que usa el `CBRS_FLOAT_MULTI` estilo.  
  
 Para obtener información acerca de cómo derivar una clase de la `CPaneFrameWnd` clase y crear dinámicamente, consulte [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar un puntero a un `CMultiPaneFrameWnd` objeto. Este fragmento de código forma parte de la [ejemplo establece el tamaño del panel](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_SetPaneSize Nº&4;](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxMultiPaneFrameWnd.h  
  
##  <a name="a-nameaddpanea--cmultipaneframewndaddpane"></a><a name="addpane"></a>CMultiPaneFrameWnd::AddPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddrecentpanea--cmultipaneframewndaddrecentpane"></a><a name="addrecentpane"></a>CMultiPaneFrameWnd::AddRecentPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AddRecentPane(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameadjustlayouta--cmultipaneframewndadjustlayout"></a><a name="adjustlayout"></a>CMultiPaneFrameWnd::AdjustLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameadjustpaneframesa--cmultipaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CMultiPaneFrameWnd::AdjustPaneFrames  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcexpecteddockedrecta--cmultipaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CMultiPaneFrameWnd::CalcExpectedDockedRect  
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
  
##  <a name="a-namecanbeattacheda--cmultipaneframewndcanbeattached"></a><a name="canbeattached"></a>CMultiPaneFrameWnd::CanBeAttached  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecanbedockedtopanea--cmultipaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CMultiPaneFrameWnd::CanBeDockedToPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockingBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecheckgrippervisibilitya--cmultipaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CMultiPaneFrameWnd::CheckGripperVisibility  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecloseminiframea--cmultipaneframewndcloseminiframe"></a><a name="closeminiframe"></a>CMultiPaneFrameWnd::CloseMiniFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CloseMiniFrame();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameconverttotabbeddocumenta--cmultipaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CMultiPaneFrameWnd::ConvertToTabbedDocument  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedockframea--cmultipaneframewnddockframe"></a><a name="dockframe"></a>CMultiPaneFrameWnd::DockFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockedFrame`  
 [in] `dockMethod`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedockpanea--cmultipaneframewnddockpane"></a><a name="dockpane"></a>CMultiPaneFrameWnd::DockPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DockPane(CDockablePane* pDockedBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockedBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedockrecentpanetomainframea--cmultipaneframewnddockrecentpanetomainframe"></a><a name="dockrecentpanetomainframe"></a>CMultiPaneFrameWnd::DockRecentPaneToMainFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcaptiontexta--cmultipaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CMultiPaneFrameWnd::GetCaptionText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetfirstvisiblepanea--cmultipaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CMultiPaneFrameWnd::GetFirstVisiblePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanea--cmultipaneframewndgetpane"></a><a name="getpane"></a>CMultiPaneFrameWnd::GetPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanecontainermanagera--cmultipaneframewndgetpanecontainermanager"></a><a name="getpanecontainermanager"></a>CMultiPaneFrameWnd::GetPaneContainerManager  
 Devuelve una referencia al objeto de administrador de contenedor interna.  
  
```  
CPaneContainerManager& GetPaneContainerManager();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al objeto de administrador de contenedor interna.  
  
### <a name="remarks"></a>Comentarios  
 Este método puede utilizarse para tener acceso a la información interna [CPaneContainerManager clase](../../mfc/reference/cpanecontainermanager-class.md) objeto.  
  
##  <a name="a-namegetpanecounta--cmultipaneframewndgetpanecount"></a><a name="getpanecount"></a>CMultiPaneFrameWnd::GetPaneCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetvisiblepanecounta--cmultipaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CMultiPaneFrameWnd::GetVisiblePaneCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinsertpanea--cmultipaneframewndinsertpane"></a><a name="insertpane"></a>CMultiPaneFrameWnd::InsertPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pControlBar`  
 [in] `pTarget`  
 [in] `bAfter`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameloadstatea--cmultipaneframewndloadstate"></a><a name="loadstate"></a>CMultiPaneFrameWnd::LoadState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 [in] `uiID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondocktorecentposa--cmultipaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CMultiPaneFrameWnd::OnDockToRecentPos  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDockToRecentPos();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonkillrolluptimera--cmultipaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CMultiPaneFrameWnd::OnKillRollUpTimer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnKillRollUpTimer();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonpanerecalclayouta--cmultipaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CMultiPaneFrameWnd::OnPaneRecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsetrolluptimera--cmultipaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CMultiPaneFrameWnd::OnSetRollUpTimer  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnSetRollUpTimer();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonshowpanea--cmultipaneframewndonshowpane"></a><a name="onshowpane"></a>CMultiPaneFrameWnd::OnShowPane  
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
  
##  <a name="a-namepanefrompointa--cmultipaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CMultiPaneFrameWnd::PaneFromPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 [in] `nSensitivity`  
 [in] `bCheckVisibility`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremovenonvalidpanesa--cmultipaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CMultiPaneFrameWnd::RemoveNonValidPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RemoveNonValidPanes();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremovepanea--cmultipaneframewndremovepane"></a><a name="removepane"></a>CMultiPaneFrameWnd::RemovePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RemovePane(
    CBasePane* pBar,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 [in] `bDestroy`  
 [in] `bNoDelayedDestroy`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namereplacepanea--cmultipaneframewndreplacepane"></a><a name="replacepane"></a>CMultiPaneFrameWnd::ReplacePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarOrg`  
 [in] `pBarReplaceWith`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesavestatea--cmultipaneframewndsavestate"></a><a name="savestate"></a>CMultiPaneFrameWnd::SaveState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 [in] `uiID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameserializea--cmultipaneframewndserialize"></a><a name="serialize"></a>CMultiPaneFrameWnd::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdockstatea--cmultipaneframewndsetdockstate"></a><a name="setdockstate"></a>CMultiPaneFrameWnd::SetDockState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockManager`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetlastfocusedpanea--cmultipaneframewndsetlastfocusedpane"></a><a name="setlastfocusedpane"></a>CMultiPaneFrameWnd::SetLastFocusedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetLastFocusedPane(HWND hwnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hwnd`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpredockstatea--cmultipaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CMultiPaneFrameWnd::SetPreDockState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `preDockState`  
 [in] `pBarToDock`  
 [in] `dockMethod`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestorerecentdocksiteinfoa--cmultipaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CMultiPaneFrameWnd::StoreRecentDockSiteInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestorerecenttabrelatedinfoa--cmultipaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CMultiPaneFrameWnd::StoreRecentTabRelatedInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreRecentTabRelatedInfo(
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
 [Clase CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

