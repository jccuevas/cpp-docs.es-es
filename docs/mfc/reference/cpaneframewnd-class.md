---
title: Clase CPaneFrameWnd
ms.date: 11/04/2016
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
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502972"
---
# <a name="cpaneframewnd-class"></a>Clase CPaneFrameWnd

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

Implementa una ventana de marco reducido que contiene un panel. El panel rellena el área cliente de la ventana.

## <a name="syntax"></a>Sintaxis

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
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
|`CPaneFrameWnd::PreTranslateMessage`|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) .|
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

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneFrameWnd::OnCheckRollState](#oncheckrollstate)|Determina si se debe desplegar o retraer una ventana de marco reducido.|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|Dibuja los bordes de una ventana de marco reducido.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaneFrameWnd::m_bUseSaveBits](#m_busesavebits)|Especifica si se debe registrar la clase de ventana con el estilo de clase CS_SAVEBITS.|

## <a name="remarks"></a>Comentarios

El marco crea automáticamente un objeto `CPaneFrameWnd` cuando se cambia un panel de un estado acoplado a un estado flotante.

Se puede arrastrar una ventana de marco reducido con su contenido visible (acoplamiento inmediato) o mediante un rectángulo de arrastre (acoplamiento estándar). El modo de acoplamiento del panel contenedor del marco reducido determina el comportamiento del marco reducido al arrastrarlo. Para obtener más información, vea [a cbasepane:: GetDockingMode](../../mfc/reference/cbasepane-class.md#getdockingmode).

Una ventana de marco reducido muestra botones en el título de acuerdo con el estilo del panel contenido. Si el panel se puede cerrar ( [a cbasepane:: CanBeClosed](../../mfc/reference/cbasepane-class.md#canbeclosed)), muestra un botón Cerrar. Si el panel tiene el estilo AFX_CBRS_AUTO_ROLLUP, muestra un PIN.

Si se deriva una clase de `CPaneFrameWnd`, se debe indicar al marco cómo crearla. Cree la clase invalidando [CPane:: CreateDefaultMiniframe](../../mfc/reference/cpane-class.md#createdefaultminiframe)o establezca el `CPane::m_pMiniFrameRTC` miembro para que apunte a la información de clase en tiempo de ejecución para la clase.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxPaneFrameWnd. h

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

Agrega un panel.

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Panel que se va a agregar.

##  <a name="addremovepanefromgloballist"></a>  CPaneFrameWnd::AddRemovePaneFromGlobalList

Agrega o quita un panel de la lista global.

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Panel que se va a agregar o quitar.

*bAdd*<br/>
de Si es distinto de cero, agregue el panel. Si es 0, quite el panel.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método se realizó correctamente; de lo contrario, es 0.

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

Calcula el tamaño de los bordes de una ventana de Miniframe.

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>Parámetros

*rectBorderSize*<br/>
enuncia Contiene el tamaño, en píxeles, del borde de la ventana Miniframe.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para calcular el tamaño del borde de una ventana de Miniframe. El tamaño devuelto depende de si una ventana de Miniframe contiene una barra de herramientas o un [CDockablePane](../../mfc/reference/cdockablepane-class.md).

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

*pWndToDock*<br/>
de Puntero a la ventana que se va a acoplar.

*ptMouse*<br/>
de La ubicación del mouse.

*rectResult*<br/>
enuncia Rectángulo calculado.

*bDrawTab*<br/>
enuncia Si es TRUE, dibuje una pestaña. Si es FALSE, no dibuje una pestaña.

*ppTargetBar*<br/>
enuncia Puntero al panel de destino.

### <a name="remarks"></a>Comentarios

Este método calcula el rectángulo que ocuparía una ventana si un usuario arrastrase la ventana hasta el punto especificado por *ptMouse* y lo acoplaba allí.

##  <a name="canbeattached"></a>  CPaneFrameWnd::CanBeAttached

Determina si se puede acoplar el panel actual a otro panel o ventana de marco.

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el panel se puede acoplar a otro panel o ventana de marco; en caso contrario, FALSE.

##  <a name="canbedockedtopane"></a>  CPaneFrameWnd::CanBeDockedToPane

Determina si se puede acoplar la ventana de marco reducido a un panel.

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>Parámetros

*pDockingBar*<br/>
de Un panel.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el marco mínimo se puede acoplar a *pDockingBar*; de lo contrario, es 0.

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

Crea una ventana de Miniframe y la adjunta al objeto [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszWindowName*<br/>
de Especifica el texto que se va a mostrar en la ventana de Miniframe.

*dwStyle*<br/>
de Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*rect*<br/>
de Especifica el tamaño y la posición iniciales de la ventana de Miniframe.

*pParentWnd*<br/>
[in, out] Especifica el marco primario de la ventana Miniframe. Este valor no debe ser NULL.

*pContext*<br/>
[in, out] Especifica el contexto definido por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se creó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Una ventana de Miniframe se crea en dos pasos. En primer lugar, el marco `CPaneFrameWnd` de trabajo crea un objeto. En segundo lugar, `Create` llama a para crear la ventana de Windows Miniframe y adjuntarla `CPaneFrameWnd` al objeto.

##  <a name="createex"></a>  CPaneFrameWnd::CreateEx

Crea una ventana de Miniframe y la adjunta al objeto [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md) .

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

*dwStyleEx*<br/>
de Especifica el estilo de ventana extendido. Para obtener más información, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

*lpszWindowName*<br/>
de Especifica el texto que se va a mostrar en la ventana de Miniframe.

*dwStyle*<br/>
de Especifica el estilo de ventana. Para obtener más información, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*rect*<br/>
de Especifica el tamaño y la posición iniciales de la ventana de Miniframe.

*pParentWnd*<br/>
[in, out] Especifica el marco primario de la ventana Miniframe. Este valor no debe ser NULL.

*pContext*<br/>
[in, out] Especifica el contexto definido por el usuario.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana se creó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Una ventana de Miniframe se crea en dos pasos. En primer lugar, el marco `CPaneFrameWnd` de trabajo crea un objeto. En segundo lugar, `Create` llama a para crear la ventana de Windows Miniframe y adjuntarla `CPaneFrameWnd` al objeto.

##  <a name="dockpane"></a>  CPaneFrameWnd::DockPane

Acopla el panel.

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>Parámetros

*bWasDocked*<br/>
enuncia TRUE si el panel ya estaba acoplado; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Si la operación se realizó correctamente, `CDockablePane` el al que estaba acoplado el panel; de lo contrario, es NULL.

##  <a name="findfloatingpanebyid"></a>  CPaneFrameWnd::FindFloatingPaneByID

Busca un panel con el identificador del control especificado en la lista global de paneles flotantes.

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
de Representa el identificador de control del panel que se va a buscar.

### <a name="return-value"></a>Valor devuelto

Panel con el identificador de control especificado; de lo contrario, es NULL si ningún panel tiene el identificador de control especificado.

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

*pt*<br/>
de Punto, en coordenadas de la pantalla.

*nSensitivity*<br/>
de Aumente el área de búsqueda de la ventana de marco reducido por este tamaño. Una ventana de marco reducido cumple los criterios de búsqueda si el punto especificado cae en el área aumentada.

*pFrameToExclude*<br/>
de Especifica una ventana de marco reducido que se va a excluir de la búsqueda.

*bFloatMultiOnly*<br/>
de Si es TRUE, solo busca en ventanas de marco reducido que tengan el estilo CBRS_FLOAT_MULTI. Si es FALSE, busque en todas las ventanas de marco reducido.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana de marco reducido que contiene *PT*; de lo contrario, NULL.

##  <a name="getcaptionheight"></a>  CPaneFrameWnd::GetCaptionHeight

Devuelve el alto del título de la ventana de marco reducido.

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>Valor devuelto

Alto, en píxeles, de la ventana de marco reducido.

### <a name="remarks"></a>Comentarios

Llame a este método para determinar el alto de una ventana de marco reducido. De forma predeterminada, el alto se establece en SM_CYSMCAPTION. Para obtener más información, consulte [función GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics).

##  <a name="getcaptionrect"></a>  CPaneFrameWnd::GetCaptionRect

Calcula el rectángulo delimitador del título de una ventana de marco reducido.

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>Parámetros

*rectCaption*<br/>
enuncia Contiene el tamaño y la posición del título de la ventana de marco reducido, en coordenadas de pantalla.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para calcular el rectángulo delimitador de un título de la ventana de marco reducido.

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

Devuelve el texto del título.

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>Valor devuelto

Texto del título de la ventana de marco reducido.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando muestra el texto del título.

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

Modo de acoplamiento. Uno de los siguientes valores:

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>  CPaneFrameWnd::GetFirstVisiblePane

Devuelve el primer panel visible que se encuentra en una ventana de marco reducido.

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>Valor devuelto

Primer panel de la ventana de marco reducido, o NULL si la ventana de marco reducido no contiene paneles.

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

Panel que se encuentra en el marco reducido, o NULL si la ventana de marco reducido no contiene paneles.

### <a name="remarks"></a>Comentarios

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

Devuelve el número de paneles que se encuentran en una ventana de marco reducido.

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de paneles de la ventana de marco reducido. Este valor puede ser cero.

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

Número de paneles visibles.

### <a name="remarks"></a>Comentarios

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

Determina qué parte de una ventana de marco reducido es en un momento dado.

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>Parámetros

*point*<br/>
de Punto que se va a probar.

*bDetectCaption*<br/>
de Si es TRUE, compruebe el punto con el título. Si es FALSE, omita el título.

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes valores:

|Value|Significado|
|-----------|-------------|
|HTNOWHERE|El punto está fuera de la ventana de marco reducido.|
|HTCLIENT|El punto se encuentra en el área cliente.|
|HTCAPTION|El punto está en el título.|
|HTTOP|El punto está en la parte superior.|
|HTTOPLEFT|El punto está en la parte superior izquierda.|
|HTTOPRIGHT|El punto está en la parte superior derecha.|
|HTLEFT|El punto está a la izquierda.|
|HTRIGHT|El punto está a la derecha.|
|HTBOTTOM|El punto está en la parte inferior.|
|HTBOTTOMLEFT|El punto está en la parte inferior izquierda.|
|HTBOTTOMRIGHT|El punto está en la parte inferior derecha.|

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

TRUE si la ventana de marco reducido debe resumirse; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para determinar si se debe resumir una ventana de marco reducido. La característica Rollup/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel con la marca AFX_CBRS_AUTO_ROLLUP. Esta marca se establece cuando se crea un panel. Para obtener más información, vea [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está dentro del rectángulo delimitador de la ventana de marco reducido para determinar si se debe resumir la ventana. Este comportamiento se puede invalidar en una clase derivada.

##  <a name="isrollup"></a>  CPaneFrameWnd::IsRollUp

Determina si se debe desplegar una ventana de marco reducido.

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se debe acumular la ventana de marco reducido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para determinar si se debe acumular una ventana de marco reducido. La característica Rollup/propagación está habilitada para una ventana de marco reducido si contiene al menos un panel con la marca AFX_CBRS_AUTO_ROLLUP. Esta marca se establece cuando se crea un panel. Para obtener más información, vea [a cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex).

De forma predeterminada, el marco de trabajo comprueba si el puntero del mouse está dentro del rectángulo delimitador de la ventana de marco reducido para determinar si se debe acumular la ventana. Este comportamiento se puede invalidar en una clase derivada.

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

*lpszProfileName*<br/>
de Nombre del perfil.

*uiID*<br/>
de IDENTIFICADOR del panel.

### <a name="return-value"></a>Valor devuelto

TRUE si el estado del panel se cargó correctamente; en caso contrario, FALSE.

##  <a name="m_busesavebits"></a>  CPaneFrameWnd::m_bUseSaveBits

Especifica si se va a registrar la clase de ventana que tiene el estilo de clase CS_SAVEBITS.

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Comentarios

Establezca este miembro estático en TRUE para registrar la clase de ventana de marco reducido que tiene el estilo CS_SAVEBITS. Esto puede ayudar a reducir el parpadeo cuando un usuario arrastra la ventana de marco reducido.

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

Determina si es posible el acoplamiento.

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es posible el acoplamiento; en caso contrario, FALSE.

##  <a name="oncheckrollstate"></a>  CPaneFrameWnd::OnCheckRollState

Determina si se debe desplegar o retraer una ventana de marco reducido.

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para determinar si se debe acumular o bajar una ventana de marco reducido.

De forma predeterminada, el marco de trabajo llama a [CPaneFrameWnd:: IsRollUp](#isrollup) y [CPaneFrameWnd:: IsRollDown](#isrolldown) y solo ajusta o restaura la ventana de marco reducido. Puede invalidar este método en una clase derivada para usar un efecto visual diferente.

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

*pDC*<br/>
de Contexto de dispositivo que se usa para dibujar el borde.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método para dibujar los bordes de la ventana de marco reducido.

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

*pBar*<br/>
de Un puntero a un panel (omitido).

*ptOffset*<br/>
de Desplazamiento por el que se va a desplazar el panel.

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

Ajusta el diseño de un panel dentro de una ventana de marco reducido.

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a este método cuando debe ajustar el diseño de un panel dentro de la ventana de marco reducido.

De forma predeterminada, el panel se coloca para cubrir el área de cliente completa de la ventana de marco reducido.

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

*pBar*<br/>
de Panel que se va a mostrar u ocultar.

*bShow*<br/>
de TRUE si se muestra el panel; FALSE si se oculta el panel.

### <a name="remarks"></a>Comentarios

Lo llama el marco de trabajo cuando se muestra u oculta un panel de la ventana de marco reducido. La implementación predeterminada no hace nada.

##  <a name="pin"></a>  CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>Parámetros

de *bPin*<br/>

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

*point*<br/>
de Punto en el que el usuario hizo clic, en coordenadas de la pantalla.

*nSensitivity*<br/>
de Este parámetro no se utiliza.

*bCheckVisibility*<br/>
de TRUE para especificar que solo se deben devolver los paneles visibles; en caso contrario, FALSE.

### <a name="return-value"></a>Valor devuelto

Panel en el que el usuario hizo clic, o NULL si no existe ningún panel en esa ubicación.

### <a name="remarks"></a>Comentarios

Llame a este método para obtener un panel que contenga el punto especificado.

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

Vuelve a dibujar todas las ventanas de marco reducido.

```
static void RedrawAll();
```

### <a name="remarks"></a>Comentarios

Este método actualiza todas las ventanas de marco reducido mediante una llamada a [CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) para cada ventana.

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

*pWnd*<br/>
de Puntero al panel que se va a quitar.

*bDestroy*<br/>
de Especifica lo que ocurre en la ventana de marco reducido. Si *bDestroy* es true, este método destruye la ventana de marco reducido inmediatamente. Si es FALSE, este método destruye la ventana de marco reducido después de un retraso determinado.

*bNoDelayedDestroy*<br/>
de Si es TRUE, la destrucción diferida está deshabilitada. Si es FALSE, la destrucción diferida está habilitada.

### <a name="remarks"></a>Comentarios

El marco de trabajo puede destruir ventanas de marco reducido inmediatamente o después de un retraso determinado. Si desea retrasar la destrucción de ventanas de marco reducido, pase FALSE en el parámetro *bNoDelayedDestroy* . La destrucción diferida se produce cuando el marco de trabajo procesa el mensaje AFX_WM_CHECKEMPTYMINIFRAME.

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

Reemplaza un panel con otro.

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>Parámetros

*pBarOrg*<br/>
de Puntero al panel original.

*pBarReplaceWith*<br/>
de Un puntero al panel que reemplaza al panel original.

##  <a name="savestate"></a>  CPaneFrameWnd::SaveState

Guarda el estado del panel en el registro.

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Nombre del perfil.

*uiID*<br/>
de IDENTIFICADOR del panel.

### <a name="return-value"></a>Valor devuelto

TRUE si el estado del panel se ha guardado correctamente; en caso contrario, FALSE.

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

Establece botones del título.

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>Parámetros

*dwButtons*<br/>
de Combinación OR bit a bit de los valores siguientes:

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>Parámetros

de *bDelayShow*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setdockingmanager"></a>  CPaneFrameWnd::SetDockingManager

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>Parámetros

de *pManager*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

Establece el temporizador de acoplamiento.

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>Parámetros

*nTimeOut*<br/>
de Valor de tiempo de espera en milisegundos.

##  <a name="setdockstate"></a>  CPaneFrameWnd::SetDockState

Establece el estado de acoplamiento.

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>Parámetros

*pDockManager*<br/>
de Un puntero a un administrador de acoplamiento.

##  <a name="sethotpoint"></a>  CPaneFrameWnd::SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>Parámetros

de *ptNew*<br/>

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

*preDockState*<br/>
de Valores posibles:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
de Puntero al panel que se va a acoplar.

*dockMethod*<br/>
de Método de acoplamiento. (Este parámetro se pasa por alto).

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana de marco reducido está desacoplada; FALSE si está acoplado.

##  <a name="sizetocontent"></a>  CPaneFrameWnd::SizeToContent

Ajusta el tamaño de una ventana de marco reducido para que sea equivalente a un panel contenido.

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Comentarios

Llame a este método para ajustar el tamaño de una ventana de marco reducido al tamaño de un panel contenido.

##  <a name="starttearoff"></a>  CPaneFrameWnd::StartTearOff

Desgaja un menú.

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>Parámetros

*pMenu*<br/>
de Un puntero a un menú.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>Parámetros

de *pBar*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="storerecenttabrelatedinfo"></a>  CPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
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
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
