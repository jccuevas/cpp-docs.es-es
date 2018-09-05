---
title: CPaneFrameWnd (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
dev_langs:
- C++
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe0d8b5b0679e8770bda715d3d0da0eaa3b5cce3
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682861"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd (clase)
Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
  
 Implementa una ventana de marco reducido que contiene un panel. El panel rellena el área cliente de la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CPaneFrameWnd : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
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
|`CPaneFrameWnd::PreTranslateMessage`|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de enviarlos a la [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funciones de Windows.|  
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Determina si se debe desplegar o retraer una ventana de marco reducido.|  
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Dibuja los bordes de una ventana de marco reducido.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Especifica si se debe registrar la clase de ventana con el estilo de clase CS_SAVEBITS.|  
  
## <a name="remarks"></a>Comentarios  
 El marco crea automáticamente un objeto `CPaneFrameWnd` cuando se cambia un panel de un estado acoplado a un estado flotante.  
  
 Se puede arrastrar una ventana de marco reducido con su contenido visible (acoplamiento inmediato) o mediante un rectángulo de arrastre (acoplamiento estándar). El modo de acoplamiento del panel contenedor del marco reducido determina el comportamiento del marco reducido al arrastrarlo. Para obtener más información, consulte [cbasepane:: Getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode).  
  
 Una ventana de marco reducido muestra botones en el título de acuerdo con el estilo del panel contenido. Si se puede cerrar el panel ( [cbasepane:: Canbeclosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), muestra un botón Cerrar. Si el panel tiene el estilo AFX_CBRS_AUTO_ROLLUP, muestra un pin.  
  
 Si se deriva una clase de `CPaneFrameWnd`, se debe indicar al marco cómo crearla. Cree la clase invalidando [Createdefaultminiframe](../../mfc/reference/cpane-class.md#createdefaultminiframe), o establecer el `CPane::m_pMiniFrameRTC` miembro de modo que apunte a la información de clase en tiempo de ejecución para la clase.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPaneFrameWnd`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxPaneFrameWnd.h  
  
##  <a name="addpane"></a>  CPaneFrameWnd::AddPane  
 Agrega un panel.  
  
```  
virtual void AddPane(CBasePane* pWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *conquistado*  
 El panel para agregar.  
  
##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList  
 Agrega o quita un panel de la lista global.  
  
```  
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,  
    BOOL bAdd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *conquistado*  
 El panel para agregar o quitar.  
  
 [in] *bAgregar*  
 Si es distinto de cero, agregar el panel. Si es 0, quite el panel.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método se realizó correctamente; en caso contrario, es 0.  
  
##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout  
 Ajusta el diseño de la ventana de marco reducido.  
  
```  
virtual void AdjustLayout();
```  
  
##  <a name="adjustpaneframes"></a>  CPaneFrameWnd::AdjustPaneFrames  

  
```  
virtual void AdjustPaneFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="calcbordersize"></a>  CPaneFrameWnd::CalcBorderSize  
 Calcula el tamaño de los bordes de una ventana de marco reducido.  
  
```  
virtual void CalcBorderSize(CRect& rectBorderSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *rectBorderSize*  
 Contiene el tamaño, en píxeles, del borde de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para calcular el tamaño del borde de una ventana de marco reducido. El tamaño devuelto depende de si una ventana de marco reducido contiene una barra de herramientas o una [CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
##  <a name="calcexpecteddockedrect"></a>  CPaneFrameWnd::CalcExpectedDockedRect  
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
 [in] *pWndToDock*  
 Un puntero a la ventana de acoplamiento.  
  
 [in] *ptMouse*  
 La ubicación del mouse.  
  
 [out] *rectResult*  
 Rectángulo calculado.  
  
 [out] *bDrawTab*  
 Si es TRUE, dibuje una pestaña. Si es FALSE, no se dibujan una pestaña.  
  
 [out] *ppTargetBar*  
 Un puntero al panel de destino.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula el rectángulo que ocuparía una ventana si un usuario arrastra la ventana para el punto especificado por *ptMouse* y ancló no existe.  
  
##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached  
 Determina si se puede acoplar el panel actual a otro panel o ventana de marco.  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se puede acoplar el panel a otro panel o ventana de marco; en caso contrario, FALSE.  
  
##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane  
 Determina si se puede acoplar la ventana de marco reducido a un panel.  
  
```  
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDockingBar*  
 Un panel.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se puede acoplar el marco reducido a *pDockingBar*; de lo contrario, 0.  
  
##  <a name="checkgrippervisibility"></a>  CPaneFrameWnd::CheckGripperVisibility  

  
```  
virtual void CheckGripperVisibility();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument  
 Convierte el panel en un documento con pestañas.  
  
```  
virtual void ConvertToTabbedDocument();
```  
  
##  <a name="create"></a>  CPaneFrameWnd::Create  
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
 [in] *lpszWindowName*  
 Especifica el texto que se muestra en la ventana de marco reducido.  
  
 [in] *dwStyle*  
 Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *rect*  
 Especifica el tamaño inicial y la posición de la ventana de marco reducido.  
  
 [in] [out] *pParentWnd*  
 Especifica el marco principal de la ventana de marco reducido. Este valor no debe ser NULL.  
  
 [in] [out] *pContext*  
 Especifica el contexto definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana se creó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Se crea una ventana de marco reducido en dos pasos. En primer lugar, el marco crea un `CPaneFrameWnd` objeto. En segundo lugar, llama a `Create` para crear la ventana de marco reducido de Windows y adjuntarlo a la `CPaneFrameWnd` objeto.  
  
##  <a name="createex"></a>  CPaneFrameWnd::CreateEx  
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
 [in] *dwStyleEx*  
 Especifica el estilo extendido de ventana. Para obtener más información, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)  
  
 [in] *lpszWindowName*  
 Especifica el texto que se muestra en la ventana de marco reducido.  
  
 [in] *dwStyle*  
 Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] *rect*  
 Especifica el tamaño inicial y la posición de la ventana de marco reducido.  
  
 [in] [out] *pParentWnd*  
 Especifica el marco principal de la ventana de marco reducido. Este valor no debe ser NULL.  
  
 [in] [out] *pContext*  
 Especifica el contexto definido por el usuario.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana se creó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Se crea una ventana de marco reducido en dos pasos. En primer lugar, el marco crea un `CPaneFrameWnd` objeto. En segundo lugar, llama a `Create` para crear la ventana de marco reducido de Windows y adjuntarlo a la `CPaneFrameWnd` objeto.  
  
##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane  
 Acopla el panel.  
  
```  
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *bWasDocked*  
 TRUE si el panel ya se ha acoplado; en caso contrario, FALSE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la operación fue correcta, el `CDockablePane` que el panel se ha acoplado a; de lo contrario, NULL.  
  
##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID  
 Busca un panel con el identificador del control especificado en la lista global de paneles flotantes.  
  
```  
static CBasePane* FindFloatingPaneByID(UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nID*  
 Representa el identificador de control del panel para buscar.  
  
### <a name="return-value"></a>Valor devuelto  
 El panel con el identificador del control especificado; en caso contrario, NULL, si ningún panel tiene el identificador de control especificado.  
  
##  <a name="framefrompoint"></a>  CPaneFrameWnd::FrameFromPoint  
 Busca la ventana de marco reducido que contiene el punto especificado.  
  
```  
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,  
    int nSensitivity,  
    CPaneFrameWnd* pFrameToExclude = NULL,  
    BOOL bFloatMultiOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pt*  
 El punto en coordenadas de pantalla.  
  
 [in] *nSensitivity*  
 Aumentar el área de búsqueda de la ventana de marco reducido por este tamaño. Una ventana de marco reducido satisface los criterios de búsqueda si el punto especificado se encuentra en el área de mayor.  
  
 [in] *pFrameToExclude*  
 Especifica una ventana de marco reducido para excluir de la búsqueda.  
  
 [in] *bFloatMultiOnly*  
 Si es TRUE, solo buscará en las ventanas de marco reducido que tienen el estilo CBRS_FLOAT_MULTI. Si es FALSE, buscar todas las ventanas de marco reducido.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco reducido que contiene *pt*; de lo contrario, NULL.  
  
##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight  
 Devuelve el alto del título de la ventana de marco reducido.  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto, en píxeles, de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para determinar el alto de una ventana de marco reducido. De forma predeterminada, se establece el alto en SM_CYSMCAPTION. Para obtener más información, consulte [función GetSystemMetrics](/windows/desktop/api/winuser/nf-winuser-getsystemmetrics).  
  
##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect  
 Calcula el rectángulo delimitador del título de una ventana de marco reducido.  
  
```  
virtual void GetCaptionRect(CRect& rectCaption) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] *rectCaption*  
 Contiene el tamaño y posición del título de ventana de marco reducido, en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para calcular el rectángulo delimitador de un título de ventana de marco reducido.  
  
##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText  
 Devuelve el texto del título.  
  
```  
virtual CString GetCaptionText();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El texto del título de la ventana de marco reducido.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo cuando se muestre el texto del título.  
  
##  <a name="getdockingmanager"></a>  CPaneFrameWnd::GetDockingManager  

  
```  
CDockingManager* GetDockingManager() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode  
 Devuelve el modo de acoplamiento.  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de acoplamiento. Uno de los siguientes valores:  
  
- DT_STANDARD  
  
- DT_IMMEDIATE  
  
- DT_SMART  
  
##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane  
 Devuelve el primer panel visible que se encuentra en una ventana de marco reducido.  
  
```  
virtual CWnd* GetFirstVisiblePane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer panel en la ventana de marco reducido, o NULL si la ventana de marco reducido no contiene ningún paneles.  
  
##  <a name="gethotpoint"></a>  CPaneFrameWnd::GetHotPoint  

  
```  
CPoint GetHotPoint() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpane"></a>  CPaneFrameWnd::GetPane  
 Devuelve un panel que se encuentra en la ventana de marco reducido.  
  
```  
virtual CWnd* GetPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El panel que se encuentra en el marco reducido, o NULL si la ventana de marco reducido no contiene ningún paneles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount  
 Devuelve el número de paneles que se encuentran en una ventana de marco reducido.  
  
```  
virtual int GetPaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles en la ventana de marco reducido. Este valor puede ser cero.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getparent"></a>  CPaneFrameWnd::GetParent  

  
```  
CWnd* GetParent();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState  

  
```  
BOOL GetPinState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getrecentfloatingrect"></a>  CPaneFrameWnd::GetRecentFloatingRect  

  
```  
CRect GetRecentFloatingRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount  
 Devuelve el número de paneles visibles que se encuentran en una ventana de marco reducido.  
  
```  
virtual int GetVisiblePaneCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles visibles.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hittest"></a>  CPaneFrameWnd::HitTest  
 Determina qué parte de una ventana de marco reducido es en un momento dado.  
  
```  
virtual LRESULT HitTest(
    CPoint point,  
    BOOL bDetectCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 El punto de prueba.  
  
 [in] *bDetectCaption*  
 Si es TRUE, compruebe el punto en el título. Si es FALSE, omita el título.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|HTNOWHERE|El punto está fuera de la ventana de marco reducido.|  
|HTCLIENT|El punto está en el área de cliente.|  
|HTCAPTION|El punto está en la leyenda.|  
|HTTOP|El punto está en la parte superior.|  
|HTTOPLEFT|El punto está en la esquina superior izquierda.|  
|HTTOPRIGHT|El punto está en la esquina superior derecha.|  
|HTLEFT|El punto está en la izquierda.|  
|HTRIGHT|El punto está en la derecha.|  
|HTBOTTOM|El punto está en la parte inferior.|  
|HTBOTTOMLEFT|El punto está en la parte inferior izquierda.|  
|HTBOTTOMRIGHT|El punto está en la esquina inferior derecha.|  
  
##  <a name="iscaptured"></a>  CPaneFrameWnd::IsCaptured  

  
```  
BOOL IsCaptured() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow  

  
```  
BOOL IsDelayShow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown  
 Determina si se debe retraer una ventana de marco reducido.  
  
```  
virtual BOOL IsRollDown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si debe aplicarse en la ventana de marco reducido; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debe retraer una ventana de marco reducido. La característica de acumulación/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel que tiene la marca AFX_CBRS_AUTO_ROLLUP. Esta marca se establece cuando se crea un panel. Para obtener más información, consulte [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está dentro del rectángulo delimitador de ventana de marco reducido para determinar si la ventana tiene que se propagará. Puede invalidar este comportamiento en una clase derivada.  
  
##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp  
 Determina si se debe desplegar una ventana de marco reducido.  
  
```  
virtual BOOL IsRollUp() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de marco reducido debe estar resumida; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debe desplegar una ventana de marco reducido. La característica de acumulación/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel que tiene la marca AFX_CBRS_AUTO_ROLLUP. Esta marca se establece cuando se crea un panel. Para obtener más información, consulte [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).  
  
 De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está dentro el rectángulo delimitador de ventana de marco reducido para determinar si la ventana tiene acumularse. Puede invalidar este comportamiento en una clase derivada.  
  
##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer  
 Detiene el temporizador de acoplamiento.  
  
```  
void KillDockingTimer();
```  
  
##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState  
 Carga el estado del panel desde el registro.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszProfileName*  
 El nombre del perfil.  
  
 [in] *uiID*  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el estado del panel se ha cargado correctamente; en caso contrario, FALSE.  
  
##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits  
 Especifica si se debe registrar la clase de ventana que tiene el estilo de clase CS_SAVEBITS.  
  
```  
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;  
```  
  
### <a name="remarks"></a>Comentarios  
 Establecer a este miembro estático en True si desea registrar la clase de ventana de marco reducido que tiene el estilo CS_SAVEBITS. Esto puede ayudar a reducir el parpadeo cuando un usuario arrastra la ventana de marco reducido.  
  
##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock  
 Determina si es posible el acoplamiento.  
  
```  
virtual BOOL OnBeforeDock();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el acoplamiento es posible; en caso contrario, FALSE.  
  
##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState  
 Determina si se debe desplegar o retraer una ventana de marco reducido.  
  
```  
virtual void OnCheckRollState();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para determinar si se debe retraer una ventana de marco reducido arriba o hacia abajo.  
  
 De forma predeterminada, el marco llama a [CPaneFrameWnd::IsRollUp](#isrollup) y [CPaneFrameWnd::IsRollDown](#isrolldown) y se expande o se restaura la ventana de marco reducido. Puede invalidar este método en una clase derivada para utilizar un efecto visual diferente.  
  
##  <a name="ondocktorecentpos"></a>  CPaneFrameWnd::OnDockToRecentPos  
 Acopla la ventana de marco reducido en su posición más reciente.  
  
```  
virtual void OnDockToRecentPos();
```  
  
##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder  
 Dibuja los bordes de una ventana de marco reducido.  
  
```  
virtual void OnDrawBorder(CDC* pDC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDC*  
 El contexto de dispositivo que se usa para dibujar el borde.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama el marco de trabajo para dibujar los bordes de la ventana de marco reducido.  
  
##  <a name="onkillrolluptimer"></a>  CPaneFrameWnd::OnKillRollUpTimer  
 Detiene el temporizador de despliegue.  
  
```  
virtual void OnKillRollUpTimer();
```  
  
##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane  
 Mueve la ventana de marco reducido a una distancia especificada.  
  
```  
virtual void OnMovePane(
    CPane* pBar,  
    CPoint ptOffset);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 Un puntero a un panel (se omite).  
  
 [in] *ptOffset*  
 El desplazamiento por el que se va a mover el panel.  
  
##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout  
 Ajusta el diseño de un panel dentro de una ventana de marco reducido.  
  
```  
virtual void OnPaneRecalcLayout();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco llama a este método cuando debe ajustar el diseño de un panel dentro de la ventana de marco reducido.  
  
 De forma predeterminada, se sitúa el panel para cubrir el área de cliente completa de la ventana de marco reducido.  
  
##  <a name="onsetrolluptimer"></a>  CPaneFrameWnd::OnSetRollUpTimer  
 Establece el temporizador de despliegue.  
  
```  
virtual void OnSetRollUpTimer();
```  
  
##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane  
 Llamado por el marco de trabajo cuando se oculta o se muestra un panel de la ventana de marco reducido.  
  
```  
virtual void OnShowPane(
    CDockablePane* pBar,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
 El panel que se va a mostrar u ocultar.  
  
 [in] *bMostrar*  
 TRUE si se muestra el panel; FALSE si se va a ocultar el panel.  
  
### <a name="remarks"></a>Comentarios  
 Lo llama el marco de trabajo cuando es mostrar u ocultar un panel en la ventana de marco reducido. La implementación predeterminada no hace nada.  
  
##  <a name="pin"></a>  CPaneFrameWnd::Pin  

  
```  
void Pin(BOOL bPin = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bPin*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="panefrompoint"></a>  CPaneFrameWnd::PaneFromPoint  
 Devuelve un panel si contiene un punto proporcionado por el usuario dentro de una ventana de marco reducido.  
  
```  
virtual CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    BOOL bCheckVisibility);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 El punto de que el usuario hizo clic, en coordenadas de pantalla.  
  
 [in] *nSensitivity*  
 Este parámetro no se utiliza.  
  
 [in] *bCheckVisibility*  
 TRUE para especificar que se deben devolver solo los paneles visibles; en caso contrario, FALSE.  
  
### <a name="return-value"></a>Valor devuelto  
 El panel que el usuario hizo clic, o NULL si no existe ningún panel en esa ubicación.  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para obtener un panel que contiene el punto especificado.  
  
##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll  
 Vuelve a dibujar todas las ventanas de marco reducido.  
  
```  
static void RedrawAll();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método actualiza todas las ventanas de marco reducido mediante una llamada a [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) para cada ventana.  
  
##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes  
 Llamado por el marco de trabajo para quitar los paneles no válidos.  
  
```  
virtual void RemoveNonValidPanes();
```  
  
##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane  
 Quita un panel de la ventana de marco reducido.  
  
```  
virtual void RemovePane(
    CBasePane* pWnd,  
    BOOL bDestroy = FALSE,  
    BOOL bNoDelayedDestroy = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *conquistado*  
 Un puntero al panel para quitar.  
  
 [in] *bDestroy*  
 Especifica lo que ocurre en la ventana de marco reducido. Si *bDestroy* es TRUE, este método destruye la ventana de marco reducido inmediatamente. Si es FALSE, este método destruye la ventana de marco reducido después de un retraso determinado.  
  
 [in] *bNoDelayedDestroy*  
 Si es TRUE, la destrucción diferida está deshabilitada. Si es FALSE, la destrucción diferida está habilitada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo puede destruir ventanas de marco reducido inmediatamente o tras un retraso determinado. Si desea retrasar la destrucción de ventanas de marco reducido, pasar el valor FALSE en el *bNoDelayedDestroy* parámetro. Destrucción diferida se produce cuando el marco de trabajo procesa el mensaje AFX_WM_CHECKEMPTYMINIFRAME.  
  
##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane  
 Reemplaza un panel con otro.  
  
```  
virtual void ReplacePane(
    CBasePane* pBarOrg,  
    CBasePane* pBarReplaceWith);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBarOrg*  
 Un puntero en el panel original.  
  
 [in] *pBarReplaceWith*  
 Un puntero al panel que reemplaza el panel original.  
  
##  <a name="savestate"></a>  CPaneFrameWnd::SaveState  
 Guarda el estado del panel en el registro.  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,  
    UINT uiID = (UINT) -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszProfileName*  
 El nombre del perfil.  
  
 [in] *uiID*  
 El identificador del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el estado del panel se ha guardado correctamente; en caso contrario, FALSE.  
  
##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons  
 Establece botones del título.  
  
```  
virtual void SetCaptionButtons(DWORD dwButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *dwButtons*  
 Combinación OR bit a bit de los valores siguientes:  
  
- AFX_CAPTION_BTN_CLOSE  
  
- AFX_CAPTION_BTN_PIN  
  
- AFX_CAPTION_BTN_MENU  
  
- AFX_CAPTION_BTN_CUSTOMIZE  
  
##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow  

  
```  
void SetDelayShow(BOOL bDelayShow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bDelayShow*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager  

  
```  
void SetDockingManager(CDockingManager* pManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pManager*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer  
 Establece el temporizador de acoplamiento.  
  
```  
void SetDockingTimer(UINT nTimeOut);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *nTimeOut*  
 Valor de tiempo de espera en milisegundos.  
  
##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState  
 Establece el estado de acoplamiento.  
  
```  
virtual void SetDockState(CDockingManager* pDockManager);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDockManager*  
 Un puntero a un administrador de acoplamiento.  
  
##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint  

  
```  
void SetHotPoint(CPoint& ptNew);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *ptNew*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setpredockstate"></a>  CPaneFrameWnd::SetPreDockState  
 Llamado por el marco para establecer el estado previo al acoplamiento.  
  
```  
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,  
    CBasePane* pBarToDock = NULL,  
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *preDockState*  
 Valores posibles:  
  
- PDS_NOTHING,  
  
- PDS_DOCK_REGULAR,  
  
- PDS_DOCK_TO_TAB  
  
 [in] *pBarToDock*  
 Un puntero al panel para acoplar.  
  
 [in] *dockMethod*  
 El método de acoplamiento. (Este parámetro se omite).  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la ventana de marco reducido está desacoplada; FALSE si está acoplada.  
  
##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent  
 Ajusta el tamaño de una ventana de marco reducido para que sea equivalente a un panel de contenido.  
  
```  
virtual void SizeToContent();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a este método para ajustar el tamaño de una ventana de marco reducido el tamaño de un panel de contenido.  
  
##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff  
 Desgaja un menú.  
  
```  
BOOL StartTearOff(CMFCPopu* pMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMenu*  
 Un puntero a un menú.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo  

  
```  
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pBar*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo  

  
```  
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,  
    CDockablePane* pTabbedBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pDockingBar*  
 [in] *pTabbedBar*  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)
