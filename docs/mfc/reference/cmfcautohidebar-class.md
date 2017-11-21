---
title: Clase CMFCAutoHideBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CMFCAutoHideBar
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AddAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::AllowShowOnPaneMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::CalcFixedLayout
- AFXAUTOHIDEBAR/CMFCAutoHideBar::Create
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetFirstAHWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::GetVisibleCount
- AFXAUTOHIDEBAR/CMFCAutoHideBar::OnShowControlBarMenu
- AFXAUTOHIDEBAR/CMFCAutoHideBar::RemoveAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetActiveInGroup
- AFXAUTOHIDEBAR/CMFCAutoHideBar::SetRecentVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::ShowAutoHideWindow
- AFXAUTOHIDEBAR/CMFCAutoHideBar::StretchPane
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UnSetAutoHideMode
- AFXAUTOHIDEBAR/CMFCAutoHideBar::UpdateVisibleState
- AFXAUTOHIDEBAR/CMFCAutoHideBar::m_nShowAHWndDelay
dev_langs: C++
helpviewer_keywords:
- CMFCAutoHideBar [MFC], CMFCAutoHideBar
- CMFCAutoHideBar [MFC], AddAutoHideWindow
- CMFCAutoHideBar [MFC], AllowShowOnPaneMenu
- CMFCAutoHideBar [MFC], CalcFixedLayout
- CMFCAutoHideBar [MFC], Create
- CMFCAutoHideBar [MFC], GetFirstAHWindow
- CMFCAutoHideBar [MFC], GetVisibleCount
- CMFCAutoHideBar [MFC], OnShowControlBarMenu
- CMFCAutoHideBar [MFC], RemoveAutoHideWindow
- CMFCAutoHideBar [MFC], SetActiveInGroup
- CMFCAutoHideBar [MFC], SetRecentVisibleState
- CMFCAutoHideBar [MFC], ShowAutoHideWindow
- CMFCAutoHideBar [MFC], StretchPane
- CMFCAutoHideBar [MFC], UnSetAutoHideMode
- CMFCAutoHideBar [MFC], UpdateVisibleState
- CMFCAutoHideBar [MFC], m_nShowAHWndDelay
ms.assetid: 54c8d84f-de64-4efd-8a47-3ea0ade40a70
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 925396faea529f2c8123f869b465e2aa4fdd4fea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcautohidebar-class"></a>Clase CMFCAutoHideBar
La clase `CMFCAutoHideBar` es una clase especial de la barra de herramientas que implementa la característica Ocultar automáticamente.  

 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]    
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCAutoHideBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideBar::CMFCAutoHideBar](#cmfcautohidebar)||  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideBar::AddAutoHideWindow](#addautohidewindow)||  
|[CMFCAutoHideBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|  
|[CMFCAutoHideBar::CalcFixedLayout](#calcfixedlayout)|(Invalida [cbasepane:: Calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCAutoHideBar::Create](#create)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPANE:: Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCAutoHideBar::GetFirstAHWindow](#getfirstahwindow)||  
|[CMFCAutoHideBar::GetVisibleCount](#getvisiblecount)||  
|[CMFCAutoHideBar::OnShowControlBarMenu](#onshowcontrolbarmenu)|Lo llama el marco de trabajo cuando está a punto de mostrarse un menú de panel especial. (Invalida [CPANE:: Onshowcontrolbarmenu](../../mfc/reference/cpane-class.md#onshowcontrolbarmenu).)|  
|[CMFCAutoHideBar::RemoveAutoHideWindow](#removeautohidewindow)||  
|[CMFCAutoHideBar::SetActiveInGroup](#setactiveingroup)|(Invalida [CPANE:: Setactiveingroup](../../mfc/reference/cpane-class.md#setactiveingroup).)|  
|[CMFCAutoHideBar::SetRecentVisibleState](#setrecentvisiblestate)||  
|[CMFCAutoHideBar::ShowAutoHideWindow](#showautohidewindow)||  
|[CMFCAutoHideBar::StretchPane](#stretchpane)|Expande un panel vertical u horizontalmente. (Invalida [cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#stretchpane).)|  
|[CMFCAutoHideBar::UnSetAutoHideMode](#unsetautohidemode)||  
|[CMFCAutoHideBar::UpdateVisibleState](#updatevisiblestate)||  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCAutoHideBar::m_nShowAHWndDelay](#m_nshowahwnddelay)|El tiempo de retardo entre el momento cuando el usuario coloca el cursor del mouse sobre un [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) y el momento en el marco muestra la ventana asociada.|  
  
## <a name="remarks"></a>Comentarios  
 Cuando el usuario cambia un panel de acoplamiento a modo de ocultación automática, el marco crea automáticamente un objeto `CMFCAutoHideBar`. También crea el necesario [CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md) y [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objetos. Cada objeto `CAutoHideDockSite` está asociado a un `CMFCAutoHideButton` individual.  
  
 La clase `CMFCAutoHideBar` implementa la presentación de un `CAutoHideDockSite` cuando el mouse de un usuario se mantiene sobre un `CMFCAutoHideButton`. Cuando la barra de herramientas recibe un mensaje WM_MOUSEMOVE, `CMFCAutoHideBar` inicia un temporizador. Cuando el temporizador finaliza, envía a la barra de herramientas una notificación de evento WM_TIMER. Para controlar este evento, la barra de herramientas comprueba si el puntero del mouse está situado sobre el mismo botón de ocultación automática que cuando se inició el temporizador. Si es así, se muestra el objeto `CAutoHideDockSite` adjunto.  
  
 Para controlar la duración del retraso del temporizador, defina `m_nShowAHWndDelay`. El valor predeterminado es de 400 ms.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAutoHideBar` y usar su método `GetDockSiteRow`.  
  
 [!code-cpp[NVC_MFC_RibbonApp#26](../../mfc/reference/codesnippet/cpp/cmfcautohidebar-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCAutoHideBar](../../mfc/reference/cmfcautohidebar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxautohidebar.h  
  
##  <a name="addautohidewindow"></a>CMFCAutoHideBar::AddAutoHideWindow  
 Agrega funcionalidad a una ventana `CDockablePane` que le permite ocultarse automáticamente.  
  
```  
CMFCAutoHideButton* AddAutoHideWindow(
    CDockablePane* pAutoHideWnd,  
    DWORD dwAlignment);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pAutoHideWnd`  
 La ventana que se quiere ocultar.  
  
 [in] `dwAlignment`  
 Un valor que especifica la alineación del botón de ocultación automática con la ventana de la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `dwAlignment` indica dónde reside el botón de ocultación automática en la aplicación. El parámetro puede establecerse en uno de los valores siguientes:  
  
- `CBRS_ALIGN_LEFT`  
  
- `CBRS_ALIGN_RIGHT`  
  
- `CBRS_ALIGN_TOP`  
  
- `CBRS_ALIGN_BOTTOM`  
  
##  <a name="allowshowonpanemenu"></a>CMFCAutoHideBar::AllowShowOnPaneMenu  

  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="calcfixedlayout"></a>CMFCAutoHideBar::CalcFixedLayout  

  
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
  
##  <a name="cmfcautohidebar"></a>CMFCAutoHideBar::CMFCAutoHideBar  
 Construye un objeto CMFCAutoHideBar.  
  
```  
CMFCAutoHideBar();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="create"></a>CMFCAutoHideBar::Create  

  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle = AFX_DEFAULT_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszClassName`  
 [in] `dwStyle`  
 [in] `rect`  
 [in] `pParentWnd`  
 [in] `nID`  
 [in] `dwControlBarStyle`  
 [in] `pContext`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getfirstahwindow"></a>CMFCAutoHideBar::GetFirstAHWindow  
 Devuelve un puntero a la primera ventana de ocultación automática de la aplicación.  
  
```  
CDockablePane* GetFirstAHWindow();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La primera ventana de ocultación automática de la aplicación o NULL si no existe ninguna.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getvisiblecount"></a>CMFCAutoHideBar::GetVisibleCount  
 Obtiene el número de botones de ocultación automática que se muestran.  
  
```  
int GetVisibleCount();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de botones de ocultación automática que se muestran.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="m_nshowahwnddelay"></a>CMFCAutoHideBar::m_nShowAHWndDelay  
 El tiempo de retardo entre el momento cuando el usuario coloca el cursor del mouse sobre un [clase CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) y el momento en el marco muestra la ventana asociada.  
  
```  
int CMFCAutoHideBar::m_nShowAHWndDelay = 400;  
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario coloca el cursor del mouse sobre un `CMFCAutoHideButton`, hay un breve lapso de tiempo antes de que el marco de trabajo muestra la ventana asociada. Este parámetro determina la longitud de dicho retraso en milisegundos.  
  
##  <a name="onshowcontrolbarmenu"></a>CMFCAutoHideBar::OnShowControlBarMenu  

  
```  
virtual BOOL OnShowControlBarMenu(CPoint);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CPoint`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removeautohidewindow"></a>CMFCAutoHideBar::RemoveAutoHideWindow  
 Elimina y destruye la ventana de ocultación automática.  
  
```  
    BOOL RemoveAutoHideWindow(CDockablePane* pAutoHideWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 CDockablePane *`pAutoHideWnd`  
 La ventana de ocultación automática que se va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setactiveingroup"></a>CMFCAutoHideBar::SetActiveInGroup  
 Marca una barra de ocultación automáticamente como activa.  
  
```  
virtual void SetActiveInGroup(BOOL bActive);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] BOOL`bActive`  
 TRUE para establecerlo como activo; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Vea [CPANE:: Setactiveingroup](../../mfc/reference/cpane-class.md#setactiveingroup).  
  
##  <a name="setrecentvisiblestate"></a>CMFCAutoHideBar::SetRecentVisibleState  

  
```  
void SetRecentVisibleState(BOOL bState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bState`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="showautohidewindow"></a>CMFCAutoHideBar::ShowAutoHideWindow  
 Muestra la ventana de ocultación automática.  
  
```  
BOOL ShowAutoHideWindow(
        CDockablePane* pAutoHideWnd,  
        BOOL bShow,  
        BOOL bDelay);  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] CDockablePane *`pAutoHideWnd`  
 [in] BOOL`bShow`  
 TRUE para mostrar la ventana.  
  
 [in] BOOL`bDelay`  
 Este parámetro se ignora.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="stretchpane"></a>CMFCAutoHideBar::StretchPane  
 Cambia el tamaño de la barra de ocultación automática en estado contraído para ajustarse al objeto `CMFCAutoHideButton` .  
  
```  
virtual CSize StretchPane(
    int nLength,   
    BOOL bVert);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nLength`  
 En la implementación base, no se usa este valor. En las implementaciones derivadas, use este valor para indicar la longitud del panel cuyo tamaño ha cambiado.  
  
 [in] `bVert`  
 En la implementación base, no se usa este valor. En las implementaciones derivadas, use `TRUE` para controlar el caso donde la barra de ocultación automática está contraída verticalmente y `FALSE` para el caso donde la barra de ocultación automática está contraída horizontalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño resultante del panel cuyo tamaño ha cambiado.  
  
### <a name="remarks"></a>Comentarios  
 Las clases derivadas pueden reemplazar este método para personalizar el comportamiento.  
  
##  <a name="unsetautohidemode"></a>CMFCAutoHideBar::UnSetAutoHideMode  
 Deshabilita el modo de ocultación automática para un grupo de barras de ocultación automática.  
  
```  
void UnSetAutoHideMode(CDockablePane* pFirstBarInGroup)  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] pFirstBarInGroup  
 Puntero a la primera barra de ocultación automática en el grupo.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="updatevisiblestate"></a>CMFCAutoHideBar::UpdateVisibleState  
 El marco de trabajo la llama cuando es necesario volver a dibujar la barra de ocultación automática.  
  
```  
void UpdateVisibleState();
```  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPane](../../mfc/reference/cpane-class.md)   
 [Clase CAutoHideDockSite](../../mfc/reference/cautohidedocksite-class.md)   
 [CMFCAutoHideButton (clase)](../../mfc/reference/cmfcautohidebutton-class.md)
