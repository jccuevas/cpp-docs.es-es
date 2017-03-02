---
title: Clase CPaneFrameWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CPaneFrameWnd.Serialize
- CPaneFrameWnd.PreTranslateMessage
- CPaneFrameWnd
- CPaneFrameWnd::Serialize
- PreTranslateMessage
- CPaneFrameWnd::PreTranslateMessage
- Serialize
dev_langs:
- C++
helpviewer_keywords:
- CPaneFrameWnd class
- Serialize method
- PreTranslateMessage method
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
caps.latest.revision: 28
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a8609643a9e64127af1d8035c496cedab4b1b1e9
ms.lasthandoff: 02/24/2017

---
# <a name="cpaneframewnd-class"></a>Clase CPaneFrameWnd
[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 Implementa una ventana de marco reducido que contiene un panel. El panel rellena el área cliente de la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::AddPane](#addpane)|Agrega un panel.|  
|[CPaneFrameWnd::AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|Agrega o quita un panel de la lista global.|  
|[CPaneFrameWnd::AdjustLayout](#adjustlayout)|Ajusta el diseño de la ventana de marco reducido.|  
|[CPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)||  
|[CPaneFrameWnd::CalcBorderSize](#calcbordersize)|Calcula el tamaño de los bordes de una ventana de marco reducido.|  
|[CPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|Calcula el rectángulo esperado de una ventana acoplada.|  
|[CPaneFrameWnd::CanBeAttached](#canbeattached)|Determina si se puede acoplar el panel actual a otro panel o ventana de marco.|  
|[CPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|Determina si se puede acoplar la ventana de marco reducido a un panel.|  
|[CPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)||  
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|Convierte el panel en un documento con pestañas.|  
|[CPaneFrameWnd::Create](#create)|Crea una ventana de marco reducido y la adjunta al objeto `CPaneFrameWnd`.|  
|[CPaneFrameWnd::CreateEx](#createex)|Crea una ventana de marco reducido y la adjunta al objeto `CPaneFrameWnd`.|  
|[CPaneFrameWnd::DockPane](#dockpane)|Acopla el panel.|  
|[CPaneFrameWnd::FindFloatingPaneByID](#findfloatingpanebyid)|Busca un panel con el identificador del control especificado en la lista global de paneles flotantes.|  
|[CPaneFrameWnd::FrameFromPoint](#framefrompoint)|Busca la ventana de marco reducido que contiene un punto proporcionado por el usuario.|  
|[CPaneFrameWnd::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título de la ventana de marco reducido.|  
|[CPaneFrameWnd::GetCaptionRect](#getcaptionrect)|Calcula el rectángulo delimitador del título de una ventana de marco reducido.|  
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|Devuelve el texto del título.|  
|[CPaneFrameWnd::GetDockingManager](#getdockingmanager)||  
|[CPaneFrameWnd::GetDockingMode](#getdockingmode)|Devuelve el modo de acoplamiento.|  
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|Devuelve el primer panel visible que se encuentra en una ventana de marco reducido.|  
|[CPaneFrameWnd::GetHotPoint](#gethotpoint)||  
|[CPaneFrameWnd::GetPane](#getpane)|Devuelve un panel que se encuentra en la ventana de marco reducido.|  
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|Devuelve el número de paneles que se encuentran en una ventana de marco reducido.|  
|[CPaneFrameWnd::GetParent](#getparent)||  
|[CPaneFrameWnd::GetPinState](#getpinstate)||  
|[CPaneFrameWnd::GetRecentFloatingRect](#getrecentfloatingrect)||  
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido.|  
|[CPaneFrameWnd::HitTest](#hittest)|Determina qué parte de una ventana de marco reducido es en un momento dado.|  
|[CPaneFrameWnd::IsCaptured](#iscaptured)||  
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||  
|[CPaneFrameWnd::IsRollDown](#isrolldown)|Determina si se debe retraer una ventana de marco reducido.|  
|[CPaneFrameWnd::IsRollUp](#isrollup)|Determina si se debe desplegar una ventana de marco reducido.|  
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|Detiene el temporizador de acoplamiento.|  
|[CPaneFrameWnd::LoadState](#loadstate)|Carga el estado del panel desde el registro.|  
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|Determina si es posible el acoplamiento.|  
|[CPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|Acopla la ventana de marco reducido en su posición más reciente.|  
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|Detiene el temporizador de despliegue.|  
|[CPaneFrameWnd::OnMovePane](#onmovepane)|Mueve la ventana de marco reducido a una distancia especificada.|  
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|Ajusta el diseño de un panel de contenido.|  
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|Establece el temporizador de despliegue.|  
|[CPaneFrameWnd::OnShowPane](#onshowpane)|Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido.|  
|[CPaneFrameWnd::PaneFromPoint](#panefrompoint)|Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido.|  
|[CPaneFrameWnd::Pin](#pin)||  
|`CPaneFrameWnd::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows.|  
|[CPaneFrameWnd::RedrawAll](#redrawall)|Vuelve a dibujar todas las ventanas de marco reducido.|  
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|Llamado por el marco de trabajo para quitar los paneles no válidos.|  
|[CPaneFrameWnd::RemovePane](#removepane)|Quita un panel de la ventana de marco reducido.|  
|[CPaneFrameWnd::ReplacePane](#replacepane)|Reemplaza un panel con otro.|  
|[CPaneFrameWnd::SaveState](#savestate)|Guarda el estado del panel en el registro.|  
|`CPaneFrameWnd::Serialize`|Lee o escribe este objeto de o en un archivo.|  
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|Establece botones del título.|  
|[CPaneFrameWnd::SetDelayShow](#setdelayshow)||  
|[CPaneFrameWnd::SetDockingManager](#setdockingmanager)||  
|[CPaneFrameWnd::SetDockingTimer](#setdockingtimer)|Establece el temporizador de acoplamiento.|  
|[CPaneFrameWnd::SetDockState](#setdockstate)|Establece el estado de acoplamiento.|  
|[CPaneFrameWnd::SetHotPoint](#sethotpoint)||  
|[CPaneFrameWnd::SetPreDockState](#setpredockstate)|Llamado por el marco para establecer el estado previo al acoplamiento.|  
|[CPaneFrameWnd::SizeToContent](#sizetocontent)|Ajusta el tamaño de una ventana de marco reducido para que tenga un tamaño equivalente al de un panel de contenido.|  
|[CPaneFrameWnd::StartTearOff](#starttearoff)|Desgaja un menú.|  
|[CPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||  
|[CPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Determina si se debe desplegar o retraer una ventana de marco reducido.|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Dibuja los bordes de una ventana de marco reducido.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Especifica si se debe registrar la clase de ventana con el estilo de clase `CS_SAVEBITS`.|  
  
## <a name="remarks"></a>Comentarios  
 El marco crea automáticamente un objeto `CPaneFrameWnd` cuando se cambia un panel de un estado acoplado a un estado flotante.  
  
 Se puede arrastrar una ventana de marco reducido con su contenido visible (acoplamiento inmediato) o mediante un rectángulo de arrastre (acoplamiento estándar). El modo de acoplamiento del panel contenedor del marco reducido determina el comportamiento del marco reducido al arrastrarlo. Para obtener más información, consulte [CBasePane::GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
 Una ventana de marco reducido muestra botones en el título de acuerdo con el estilo del panel contenido. Si se puede cerrar el panel ( [CBasePane::CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), se muestra un botón Cerrar. Si el panel tiene el estilo `AFX_CBRS_AUTO_ROLLUP`, muestra una chincheta.  
  
 Si se deriva una clase de `CPaneFrameWnd`, se debe indicar al marco cómo crearla. Cree la clase reemplazando [CPane::CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), o establecer el `CPane::m_pMiniFrameRTC` miembro de modo que apunte a la información de clase en tiempo de ejecución para la clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxPaneFrameWnd.h  
  
##  <a name="a-nameaddpanea--cpaneframewndaddpane"></a><a name="addpane"></a>CPaneFrameWnd::AddPane  
 Agrega un panel.  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Panel para agregar.  
  
##  <a name="a-nameaddremovepanefromgloballista--cpaneframewndaddremovepanefromgloballist"></a><a name="addremovepanefromgloballist"></a>CPaneFrameWnd::AddRemovePaneFromGlobalList  
 Agrega o quita un panel de la lista global.  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 El panel para agregar o quitar.  
  
 [in] `bAdd`  
 Si es distinto de cero, agregar el panel. Si es 0, quite el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, 0.  
  
##  <a name="a-nameadjustlayouta--cpaneframewndadjustlayout"></a><a name="adjustlayout"></a>CPaneFrameWnd::AdjustLayout  
 Ajusta el diseño de la ventana de marco reducido.  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="a-nameadjustpaneframesa--cpaneframewndadjustpaneframes"></a><a name="adjustpaneframes"></a>CPaneFrameWnd::AdjustPaneFrames  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcbordersizea--cpaneframewndcalcbordersize"></a><a name="calcbordersize"></a>CPaneFrameWnd::CalcBorderSize  
 Calcula el tamaño de los bordes de una ventana de marco reducido.  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectBorderSize`  
 Contiene el tamaño, en píxeles, del borde de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para calcular el tamaño del borde de una ventana de marco reducido. El tamaño devuelto depende de si una ventana de marco reducido contiene una barra de herramientas o un [CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
##  <a name="a-namecalcexpecteddockedrecta--cpaneframewndcalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a>CPaneFrameWnd::CalcExpectedDockedRect  
 Calcula el rectángulo esperado de una ventana acoplada.  
  
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
 Puntero a la ventana para acoplar.  
  
 [in] `ptMouse`  
 La ubicación del mouse.  
  
 [out] `rectResult`  
 Rectángulo calculado.  
  
 [out] `bDrawTab`  
 Si `TRUE`, dibuje una pestaña. Si `FALSE`, no se dibujan una pestaña.  
  
 [out] `ppTargetBar`  
 Un puntero al panel de destino.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el rectángulo que ocuparía una ventana si un usuario arrastra la ventana para el punto especificado por `ptMouse` y acoplado no existe.  
  
##  <a name="a-namecanbeattacheda--cpaneframewndcanbeattached"></a><a name="canbeattached"></a>CPaneFrameWnd::CanBeAttached  
 Determina si se puede acoplar el panel actual a otro panel o ventana de marco.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel se puede acoplar a otro panel o ventana de marco; de lo contrario, `FALSE`.  
  
##  <a name="a-namecanbedockedtopanea--cpaneframewndcanbedockedtopane"></a><a name="canbedockedtopane"></a>CPaneFrameWnd::CanBeDockedToPane  
 Determina si se puede acoplar la ventana de marco reducido a un panel.  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockingBar`  
 Un panel.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el marco reducido que se puede acoplar a `pDockingBar`; de lo contrario, 0.  
  
##  <a name="a-namecheckgrippervisibilitya--cpaneframewndcheckgrippervisibility"></a><a name="checkgrippervisibility"></a>CPaneFrameWnd::CheckGripperVisibility  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameconverttotabbeddocumenta--cpaneframewndconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CPaneFrameWnd::ConvertToTabbedDocument  
 Convierte el panel en un documento con pestañas.  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="a-namecreatea--cpaneframewndcreate"></a><a name="create"></a>CPaneFrameWnd::Create  
 Crea una ventana de marco reducido y lo adjunta a la [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszWindowName`  
 Especifica el texto para mostrar en la ventana de marco reducido.  
  
 [in] `dwStyle`  
 Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la ventana de marco reducido.  
  
 [in] [out]`pParentWnd`  
 Especifica el marco principal de la ventana de marco reducido. Este valor no debe ser `NULL`.  
  
 [in] [out]`pContext`  
 Especifica el contexto definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Se crea una ventana de marco reducido en dos pasos. En primer lugar, el marco de trabajo crea un `CPaneFrameWnd` objeto. En segundo lugar, llama a `Create` para crear la ventana de marco reducido de Windows y adjuntarlo a la `CPaneFrameWnd` objeto.  
  
##  <a name="a-namecreateexa--cpaneframewndcreateex"></a><a name="createex"></a>CPaneFrameWnd::CreateEx  
 Crea una ventana de marco reducido y lo adjunta a la [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwStyleEx`  
 Especifica el estilo de ventana extendidos. Para obtener más información, consulte [estilos de ventana extendidos](../../mfc/reference/extended-window-styles.md)  
  
 [in] `lpszWindowName`  
 Especifica el texto para mostrar en la ventana de marco reducido.  
  
 [in] `dwStyle`  
 Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `rect`  
 Especifica el tamaño inicial y la posición de la ventana de marco reducido.  
  
 [in] [out]`pParentWnd`  
 Especifica el marco principal de la ventana de marco reducido. Este valor no debe ser `NULL`.  
  
 [in] [out]`pContext`  
 Especifica el contexto definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana se creó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Se crea una ventana de marco reducido en dos pasos. En primer lugar, el marco de trabajo crea un `CPaneFrameWnd` objeto. En segundo lugar, llama a `Create` para crear la ventana de marco reducido de Windows y adjuntarlo a la `CPaneFrameWnd` objeto.  
  
##  <a name="a-namedockpanea--cpaneframewnddockpane"></a><a name="dockpane"></a>CPaneFrameWnd::DockPane  
 Acopla el panel.  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `bWasDocked`  
 `TRUE`Si ya se ha acoplado el panel; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la operación se realizó correctamente, el `CDockablePane` que el panel se acopla a; de lo contrario `NULL`.  
  
##  <a name="a-namefindfloatingpanebyida--cpaneframewndfindfloatingpanebyid"></a><a name="findfloatingpanebyid"></a>CPaneFrameWnd::FindFloatingPaneByID  
 Busca un panel con el identificador del control especificado en la lista global de paneles flotantes.  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 Representa el identificador del control del panel para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 El panel con el identificador del control especificado; de lo contrario, `NULL`, si ningún panel tiene el identificador del control especificado.  
  
##  <a name="a-nameframefrompointa--cpaneframewndframefrompoint"></a><a name="framefrompoint"></a>CPaneFrameWnd::FrameFromPoint  
 Busca la ventana de marco reducido que contiene el punto especificado.  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 El punto, en coordenadas de pantalla.  
  
 [in] `nSensitivity`  
 Aumentar el área de búsqueda de la ventana de marco reducido por este tamaño. Una ventana de marco reducido satisface los criterios de búsqueda si el punto especificado se encuentra en el área de aumento.  
  
 [in] `pFrameToExclude`  
 Especifica una ventana de marco reducido para excluir de la búsqueda.  
  
 [in] `bFloatMultiOnly`  
 Si `TRUE`, sólo buscará en las ventanas de marco reducido que tienen la `CBRS_FLOAT_MULTI` estilo. Si `FALSE`, buscar todas las ventanas de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco reducido que contiene `pt`; en caso contrario `NULL`.  
  
##  <a name="a-namegetcaptionheighta--cpaneframewndgetcaptionheight"></a><a name="getcaptionheight"></a>CPaneFrameWnd::GetCaptionHeight  
 Devuelve el alto del título de la ventana de marco reducido.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Alto, en píxeles, de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar el alto de una ventana de marco reducido. De forma predeterminada, el alto se establece en `SM_CYSMCAPTION`. Para obtener más información, consulte [función GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385).  
  
##  <a name="a-namegetcaptionrecta--cpaneframewndgetcaptionrect"></a><a name="getcaptionrect"></a>CPaneFrameWnd::GetCaptionRect  
 Calcula el rectángulo delimitador del título de una ventana de marco reducido.  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectCaption`  
 Contiene el tamaño y la posición del título de la ventana de marco reducido, en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para calcular el rectángulo delimitador de un título de ventana de marco reducido.  
  
##  <a name="a-namegetcaptiontexta--cpaneframewndgetcaptiontext"></a><a name="getcaptiontext"></a>CPaneFrameWnd::GetCaptionText  
 Devuelve el texto del título.  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto del título de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando se muestra el texto del título.  
  
##  <a name="a-namegetdockingmanagera--cpaneframewndgetdockingmanager"></a><a name="getdockingmanager"></a>CPaneFrameWnd::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdockingmodea--cpaneframewndgetdockingmode"></a><a name="getdockingmode"></a>CPaneFrameWnd::GetDockingMode  
 Devuelve el modo de acoplamiento.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de acoplamiento. Uno de los siguientes valores:  
  
- `DT_STANDARD`  
  
- `DT_IMMEDIATE`  
  
- `DT_SMART`  
  
##  <a name="a-namegetfirstvisiblepanea--cpaneframewndgetfirstvisiblepane"></a><a name="getfirstvisiblepane"></a>CPaneFrameWnd::GetFirstVisiblePane  
 Devuelve el primer panel visible que se encuentra en una ventana de marco reducido.  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer panel en la ventana de marco reducido, o `NULL` si la ventana de marco reducido no contiene ningún paneles.  
  
##  <a name="a-namegethotpointa--cpaneframewndgethotpoint"></a><a name="gethotpoint"></a>CPaneFrameWnd::GetHotPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanea--cpaneframewndgetpane"></a><a name="getpane"></a>CPaneFrameWnd::GetPane  
 Devuelve un panel que se encuentra en la ventana de marco reducido.  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El panel de contenido en el marco reducido, o `NULL` si la ventana de marco reducido no contiene ningún paneles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanecounta--cpaneframewndgetpanecount"></a><a name="getpanecount"></a>CPaneFrameWnd::GetPaneCount  
 Devuelve el número de paneles que se encuentran en una ventana de marco reducido.  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles de la ventana de marco reducido. Este valor puede ser cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparenta--cpaneframewndgetparent"></a><a name="getparent"></a>CPaneFrameWnd::GetParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpinstatea--cpaneframewndgetpinstate"></a><a name="getpinstate"></a>CPaneFrameWnd::GetPinState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetrecentfloatingrecta--cpaneframewndgetrecentfloatingrect"></a><a name="getrecentfloatingrect"></a>CPaneFrameWnd::GetRecentFloatingRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetvisiblepanecounta--cpaneframewndgetvisiblepanecount"></a><a name="getvisiblepanecount"></a>CPaneFrameWnd::GetVisiblePaneCount  
 Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido.  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles visibles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehittesta--cpaneframewndhittest"></a><a name="hittest"></a>CPaneFrameWnd::HitTest  
 Determina qué parte de una ventana de marco reducido es en un momento dado.  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto de prueba.  
  
 [in] `bDetectCaption`  
 Si `TRUE`, compruebe el punto en el título. Si `FALSE`, omitir el título.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`HTNOWHERE`|El punto está fuera de la ventana de marco reducido.|  
|`HTCLIENT`|Es el punto en el área de cliente.|  
|`HTCAPTION`|Es el punto en el título.|  
|`HTTOP`|El punto está en la parte superior.|  
|`HTTOPLEFT`|El punto está en la parte superior izquierda.|  
|`HTTOPRIGHT`|El punto está en la parte superior derecha.|  
|`HTLEFT`|El punto está a la izquierda.|  
|`HTRIGHT`|El punto está a la derecha.|  
|`HTBOTTOM`|El punto está en la parte inferior.|  
|`HTBOTTOMLEFT`|El punto está en la parte inferior izquierda.|  
|`HTBOTTOMRIGHT`|El punto está en la esquina inferior derecha.|  
  
##  <a name="a-nameiscaptureda--cpaneframewndiscaptured"></a><a name="iscaptured"></a>CPaneFrameWnd::IsCaptured  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdelayshowa--cpaneframewndisdelayshow"></a><a name="isdelayshow"></a>CPaneFrameWnd::IsDelayShow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisrolldowna--cpaneframewndisrolldown"></a><a name="isrolldown"></a>CPaneFrameWnd::IsRollDown  
 Determina si se debe retraer una ventana de marco reducido.  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si debe aplicarse en la ventana de marco reducido; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debe propagar una ventana de marco reducido. La característica de acumulación/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel con el `AFX_CBRS_AUTO_ROLLUP` marca. Este indicador se establece cuando se crea un panel. Para obtener más información, consulte [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está dentro del rectángulo delimitador de ventana de marco reducido para determinar si la ventana tiene que se propagará. Puede invalidar este comportamiento en una clase derivada.  
  
##  <a name="a-nameisrollupa--cpaneframewndisrollup"></a><a name="isrollup"></a>CPaneFrameWnd::IsRollUp  
 Determina si se debe desplegar una ventana de marco reducido.  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana de marco reducido debe restaurarse. de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debe acumular una ventana de marco reducido. La característica de acumulación/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel con el `AFX_CBRS_AUTO_ROLLUP` marca. Este indicador se establece cuando se crea un panel. Para obtener más información, consulte [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está en el rectángulo delimitador de ventana de marco reducido para determinar si la ventana tiene resumida. Puede invalidar este comportamiento en una clase derivada.  
  
##  <a name="a-namekilldockingtimera--cpaneframewndkilldockingtimer"></a><a name="killdockingtimer"></a>CPaneFrameWnd::KillDockingTimer  
 Detiene el temporizador de acoplamiento.  
  
```  
void KillDockingTimer();
```  
  
##  <a name="a-nameloadstatea--cpaneframewndloadstate"></a><a name="loadstate"></a>CPaneFrameWnd::LoadState  
 Carga el estado del panel desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 El nombre del perfil.  
  
 [in] `uiID`  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado del panel se ha cargado correctamente; de lo contrario, `FALSE`.  
  
##  <a name="a-namembusesavebitsa--cpaneframewndmbusesavebits"></a><a name="m_busesavebits"></a>CPaneFrameWnd::m_bUseSaveBits  
 Especifica si se debe registrar la clase de ventana que tiene el `CS_SAVEBITS` estilo de clase.  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer este miembro estático `TRUE` para registrar la clase de ventana de marco reducido que tiene el `CS_SAVEBITS` estilo. Esto puede ayudar a reducir el parpadeo cuando un usuario arrastra la ventana de marco reducido.  
  
##  <a name="a-nameonbeforedocka--cpaneframewndonbeforedock"></a><a name="onbeforedock"></a>CPaneFrameWnd::OnBeforeDock  
 Determina si es posible el acoplamiento.  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el acoplamiento es posible; de lo contrario, `FALSE`.  
  
##  <a name="a-nameoncheckrollstatea--cpaneframewndoncheckrollstate"></a><a name="oncheckrollstate"></a>CPaneFrameWnd::OnCheckRollState  
 Determina si se debe desplegar o retraer una ventana de marco reducido.  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debería revertir una ventana de marco reducido hacia arriba o hacia abajo.  
  
 De forma predeterminada, el marco llama a [CPaneFrameWnd::IsRollUp](#isrollup) y [CPaneFrameWnd::IsRollDown](#isrolldown) y se expande o se restaura la ventana de marco reducido. Puede invalidar este método en una clase derivada para utilizar un efecto visual diferente.  
  
##  <a name="a-nameondocktorecentposa--cpaneframewndondocktorecentpos"></a><a name="ondocktorecentpos"></a>CPaneFrameWnd::OnDockToRecentPos  
 Acopla la ventana de marco reducido en su posición más reciente.  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="a-nameondrawbordera--cpaneframewndondrawborder"></a><a name="ondrawborder"></a>CPaneFrameWnd::OnDrawBorder  
 Dibuja los bordes de una ventana de marco reducido.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dispositivo utilizado para dibujar el borde.  
  
### <a name="remarks"></a>Comentarios  
 Este método es llamado por el marco para dibujar los bordes de la ventana de marco reducido.  
  
##  <a name="a-nameonkillrolluptimera--cpaneframewndonkillrolluptimer"></a><a name="onkillrolluptimer"></a>CPaneFrameWnd::OnKillRollUpTimer  
 Detiene el temporizador de despliegue.  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="a-nameonmovepanea--cpaneframewndonmovepane"></a><a name="onmovepane"></a>CPaneFrameWnd::OnMovePane  
 Mueve la ventana de marco reducido a una distancia especificada.  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a un panel (pasa por alto).  
  
 [in] `ptOffset`  
 El desplazamiento de la que se va a mover el panel.  
  
##  <a name="a-nameonpanerecalclayouta--cpaneframewndonpanerecalclayout"></a><a name="onpanerecalclayout"></a>CPaneFrameWnd::OnPaneRecalcLayout  
 Ajusta el diseño de un panel dentro de una ventana de marco reducido.  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método cuando debe ajustar el diseño de un panel dentro de la ventana de marco reducido.  
  
 De manera predeterminada, el panel se sitúa para cubrir el área de cliente completo de la ventana de marco reducido.  
  
##  <a name="a-nameonsetrolluptimera--cpaneframewndonsetrolluptimer"></a><a name="onsetrolluptimer"></a>CPaneFrameWnd::OnSetRollUpTimer  
 Establece el temporizador de despliegue.  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="a-nameonshowpanea--cpaneframewndonshowpane"></a><a name="onshowpane"></a>CPaneFrameWnd::OnShowPane  
 Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido.  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 El panel que se va a mostrar u ocultar.  
  
 [in] `bShow`  
 `TRUE`Si se muestra el panel; `FALSE` si se va a ocultar el panel.  
  
### <a name="remarks"></a>Comentarios  
 Llamado por el marco cuando se muestra u oculto un panel en la ventana de marco reducido. La implementación predeterminada no hace nada.  
  
##  <a name="a-namepina--cpaneframewndpin"></a><a name="pin"></a>CPaneFrameWnd::Pin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bPin`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepanefrompointa--cpaneframewndpanefrompoint"></a><a name="panefrompoint"></a>CPaneFrameWnd::PaneFromPoint  
 Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto de que el usuario hizo clic, en coordenadas de pantalla.  
  
 [in] `nSensitivity`  
 Este parámetro no se utiliza.  
  
 [in] `bCheckVisibility`  
 `TRUE`para especificar que se deben devolver sólo los paneles visibles; de lo contrario, `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El panel que hizo clic el usuario, o `NULL` si no existe ningún panel en esa ubicación.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para obtener un panel que contiene el punto especificado.  
  
##  <a name="a-nameredrawalla--cpaneframewndredrawall"></a><a name="redrawall"></a>CPaneFrameWnd::RedrawAll  
 Vuelve a dibujar todas las ventanas de marco reducido.  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza todas las ventanas de marco reducido llamando a [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) para cada ventana.  
  
##  <a name="a-nameremovenonvalidpanesa--cpaneframewndremovenonvalidpanes"></a><a name="removenonvalidpanes"></a>CPaneFrameWnd::RemoveNonValidPanes  
 Llamado por el marco de trabajo para quitar los paneles no válidos.  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="a-nameremovepanea--cpaneframewndremovepane"></a><a name="removepane"></a>CPaneFrameWnd::RemovePane  
 Quita un panel de la ventana de marco reducido.  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero al panel para quitar.  
  
 [in] `bDestroy`  
 Especifica lo que ocurre en la ventana de marco reducido. Si `bDestroy` es `TRUE`, este método destruye la ventana de marco reducido inmediatamente. Si es `FALSE`, este método destruye la ventana de marco reducido después de un retraso determinado.  
  
 [in] `bNoDelayedDestroy`  
 Si `TRUE`, diferida destrucción está deshabilitada. Si `FALSE`, diferida está habilitada la destrucción.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo puede destruir ventanas de marco reducido o inmediatamente después de un retardo. Si desea aplazar la destrucción de ventanas de marco reducido, pasar `FALSE` en el `bNoDelayedDestroy` parámetro. Destrucción diferida se produce cuando el marco de trabajo procesa el `AFX_WM_CHECKEMPTYMINIFRAME` mensaje.  
  
##  <a name="a-namereplacepanea--cpaneframewndreplacepane"></a><a name="replacepane"></a>CPaneFrameWnd::ReplacePane  
 Reemplaza un panel con otro.  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBarOrg`  
 Un puntero al panel original.  
  
 [in] `pBarReplaceWith`  
 Un puntero al panel que reemplaza el panel original.  
  
##  <a name="a-namesavestatea--cpaneframewndsavestate"></a><a name="savestate"></a>CPaneFrameWnd::SaveState  
 Guarda el estado del panel en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 El nombre del perfil.  
  
 [in] `uiID`  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el estado del panel se ha guardado correctamente; de lo contrario, `FALSE`.  
  
##  <a name="a-namesetcaptionbuttonsa--cpaneframewndsetcaptionbuttons"></a><a name="setcaptionbuttons"></a>CPaneFrameWnd::SetCaptionButtons  
 Establece botones del título.  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwButtons`  
 Combinación OR bit a bit de los valores siguientes:  
  
- `AFX_CAPTION_BTN_CLOSE`  
  
- `AFX_CAPTION_BTN_PIN`  
  
- `AFX_CAPTION_BTN_MENU`  
  
- `AFX_CAPTION_BTN_CUSTOMIZE`  
  
##  <a name="a-namesetdelayshowa--cpaneframewndsetdelayshow"></a><a name="setdelayshow"></a>CPaneFrameWnd::SetDelayShow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDelayShow`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdockingmanagera--cpaneframewndsetdockingmanager"></a><a name="setdockingmanager"></a>CPaneFrameWnd::SetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pManager`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdockingtimera--cpaneframewndsetdockingtimer"></a><a name="setdockingtimer"></a>CPaneFrameWnd::SetDockingTimer  
 Establece el temporizador de acoplamiento.  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTimeOut`  
 Valor de tiempo de espera en milisegundos.  
  
##  <a name="a-namesetdockstatea--cpaneframewndsetdockstate"></a><a name="setdockstate"></a>CPaneFrameWnd::SetDockState  
 Establece el estado de acoplamiento.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDockManager`  
 Puntero a un administrador de acoplamiento.  
  
##  <a name="a-namesethotpointa--cpaneframewndsethotpoint"></a><a name="sethotpoint"></a>CPaneFrameWnd::SetHotPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptNew`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpredockstatea--cpaneframewndsetpredockstate"></a><a name="setpredockstate"></a>CPaneFrameWnd::SetPreDockState  
 Llamado por el marco para establecer el estado previo al acoplamiento.  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `preDockState`  
 Valores posibles:  
  
- `PDS_NOTHING`,  
  
- `PDS_DOCK_REGULAR`,  
  
- `PDS_DOCK_TO_TAB`  
  
 [in] `pBarToDock`  
 Un puntero al panel para acoplar.  
  
 [in] `dockMethod`  
 El método de acoplamiento. (Este parámetro se omite).  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ventana de marco reducido está desacoplada; `FALSE` , si está acoplada.  
  
##  <a name="a-namesizetocontenta--cpaneframewndsizetocontent"></a><a name="sizetocontent"></a>CPaneFrameWnd::SizeToContent  
 Ajusta el tamaño de una ventana de marco reducido para que sea equivalente a un panel de contenido.  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para ajustar el tamaño de una ventana de marco reducido que el tamaño de un panel de contenido.  
  
##  <a name="a-namestarttearoffa--cpaneframewndstarttearoff"></a><a name="starttearoff"></a>CPaneFrameWnd::StartTearOff  
 Desgaja un menú.  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenu`  
 Puntero a un menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Es `TRUE` si el método es correcto; en caso contrario, es `FALSE`.  
  
##  <a name="a-namestorerecentdocksiteinfoa--cpaneframewndstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a>CPaneFrameWnd::StoreRecentDockSiteInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namestorerecenttabrelatedinfoa--cpaneframewndstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd::StoreRecentTabRelatedInfo  
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
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)

