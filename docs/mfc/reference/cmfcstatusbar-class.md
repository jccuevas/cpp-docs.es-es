---
title: Clase CMFCStatusBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCStatusBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCStatusBar class
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
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
ms.openlocfilehash: 20881637d74bafffbcf2e0c3dcd1cc98e173aa07
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcstatusbar-class"></a>Clase de CMFCStatusBar
El `CMFCStatusBar` clase implementa una barra de estado similar a la `CStatusBar` clase. Sin embargo, la clase `CMFCStatusBar` tiene características que no ofrece la clase `CStatusBar` , tales como la capacidad para mostrar imágenes, animaciones y barras de progreso y la capacidad de responder a los doble clics del mouse.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCStatusBar : public CPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Invalida [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|  
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||  
|[CMFCStatusBar::Create](#create)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPane::Create](../../mfc/reference/cpane-class.md#create).)|  
|[CMFCStatusBar::CreateEx](#createex)|Crea una barra de control y lo adjunta a la [CPane](../../mfc/reference/cpane-class.md) objeto. (Invalida [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|  
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si se puede insertar otro panel dinámicamente entre este panel y el marco primario. (Invalida [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|  
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Habilita o deshabilita el control del mouse hace doble clic en la barra de estado.|  
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Muestra una barra de progreso en el panel especificado.|  
|[CMFCStatusBar::GetCount](#getcount)|Devuelve el número de paneles en la barra de estado.|  
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||  
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||  
|[CMFCStatusBar::GetItemID](#getitemid)||  
|[CMFCStatusBar::GetItemRect](#getitemrect)||  
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||  
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||  
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Devuelve el estilo del panel. (Invalida [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|  
|[CMFCStatusBar::GetPaneText](#getpanetext)||  
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Devuelve el ancho, en píxeles, del panel especificado de la barra de estado.|  
|[CMFCStatusBar::GetTipText](#gettiptext)|Devuelve el texto de sugerencia para el panel de la barra de estado especificado.|  
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalida el panel especificado y su contenido se vuelve a dibujar.|  
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Llamado por el marco antes de la creación de la ventana de Windows asociada a esta `CWnd` objeto. (Invalida [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|  
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||  
|[CMFCStatusBar::SetIndicators](#setindicators)||  
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Asigna una animación en el panel especificado.|  
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Establece el color de fondo del panel de la barra de estado especificado.|  
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Establece el icono de indicador del panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||  
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Establece el progreso actual de la barra de progreso para el panel de la barra de estado especificado.|  
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del panel. (Invalida [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|  
|[CMFCStatusBar::SetPaneText](#setpanetext)||  
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Establece el color del texto del panel de la barra de estado especificado.|  
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Establece el ancho en píxeles del panel especificado de la barra de estado.|  
|[CMFCStatusBar::SetTipText](#settiptext)|Establece el texto de sugerencia para el panel de la barra de estado especificado.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Llamado por el marco de trabajo cuando se vuelve a dibujar el panel de la barra de estado.|  
  
## <a name="remarks"></a>Comentarios  
 El siguiente diagrama muestra una ilustración de la barra de estado [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md) aplicación.  
  
 ![Ejemplo de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "cmfcstatusbar")  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra las variables locales que la aplicación usa para llamar a varios métodos la `CMFCStatusBar` clase. Estas variables se declaran en StatusBarDemoView.h. El marco principal se declara en MainFrm.h, el documento se declara en StatusBarDemoDoc.h y la vista se declara en StatusBarDemoView.h. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo&#9;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo obtener una referencia a `CMFCStatusBar` objeto introduciendo el `GetStatusBar` método en MainFrm.h y, a continuación, llamar a este método desde el `GetStatusBar` método en StatusBarDemoView.h. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo&#7;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]  
[!code-cpp[NVC_MFC_StatusBarDemo Nº&8;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo llamar a varios métodos en la `CMFCStatusBar` clase en StatusBarDemoView.cpp. Las constantes se declaran en MainFrm.h. En el ejemplo se muestra cómo configurar el icono, establecer el texto de información sobre herramientas del panel de barra de estado, mostrar una barra de progreso en el panel especificado, asignar una animación en el panel especificado, el texto y el ancho del panel de barra de estado y establecer el indicador de progreso actual de la barra de progreso para el panel de la barra de estado. Este fragmento de código forma parte de la [ejemplo de demostración de la barra de estado](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StatusBarDemo Nº&6;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]  
[!code-cpp[1 NVC_MFC_StatusBarDemo](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo&3;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo Nº&4;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]  
[!code-cpp[NVC_MFC_StatusBarDemo&#5;](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxstatusbar.h  
  
##  <a name="a-namecalcfixedlayouta--cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout  
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
  
##  <a name="a-namecommandtoindexa--cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIDFind`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreatea--cmfcstatusbarcreate"></a><a name="create"></a>CMFCStatusBar::Create  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreateexa--cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStatusBar::CreateEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = 0,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,  
    UINT nID = AFX_IDW_STATUS_BAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 [in] `dwCtrlStyle`  
 [in] `dwStyle`  
 [in] `nID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedoesallowdyninsertbeforea--cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablepanedoubleclicka--cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick  
 Habilita o deshabilita el control del mouse hace doble clic en la barra de estado.  
  
```  
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Si `TRUE`, habilitar el procesamiento del mouse, haga doble clic. De lo contrario, deshabilite el procesamiento del doble clic del mouse.  
  
### <a name="remarks"></a>Comentarios  
 Si está habilitada la barra de estado para procesar los dobles clics, Windows envía el `WM_COMMAND` notificación junto con un identificador de recurso para el propietario de la cada vez que el usuario hace doble clic en el panel de la barra de estado de la barra de estado.  
  
##  <a name="a-nameenablepaneprogressbara--cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar  
 Mostrar una barra de progreso en el panel especificado.  
  
```  
void EnablePaneProgressBar(
    int nIndex,  
    long nTotal=100,  
    BOOL bDisplayText=FALSE,  
    COLORREF clrBar=-1,  
    COLORREF clrBarDest=-1,  
    COLORREF clrProgressText=-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel a habilitar cuya barra de progreso.  
  
 [in] `nTotal`  
 Especifica el valor máximo de la barra de progreso.  
  
 [in] `bDisplayText`  
 Especifica si la barra de progreso debe mostrar el valor de progreso actual.  
  
 [in] `clrBar`  
 Especifica el color de fondo de la barra de progreso.  
  
 [in] `clrBarDest`  
 Especifica el color secundario del fondo de la barra de progreso. Utilice un valor distinto de `clrBar` para rellenar un combinado en un degradado de color.  
  
 [in] `clrProgressText`  
 Especifica el color del texto de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 Si desea deshabilitar la llamada de la barra de progreso `EnablePaneProgressBar` con `nTotal` establecido en -1. De forma predeterminada `nTotal` está establecido en 100. Por lo tanto, no es necesario ningún cálculo adicional para mostrar el progreso como porcentaje.  
  
 Debe pasar valores diferentes `clrBar` y `clrBarDest` para que el color de fondo de la barra de progreso muestra un combinado en un degradado de color. .  
  
 Para establecer el progreso actual, llame a la [CMFCStatusBar::SetPaneProgress](#setpaneprogress) método.  
  
##  <a name="a-namegetcounta--cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStatusBar::GetCount  
 Recupera el número de paneles de la barra de estado.  
  
```  
int GetCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de paneles de la barra de estado.  
  
##  <a name="a-namegetdrawextendedareaa--cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetDrawExtendedArea() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetextendedareaa--cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetExtendedArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetitemida--cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStatusBar::GetItemID  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetitemrecta--cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStatusBar::GetItemRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `lpRect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpaneinfoa--cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetPaneInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& cxWidth) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpaneprogressa--cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
long GetPaneProgress(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanestylea--cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
UINT GetPaneStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanetexta--cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStatusBar::GetPaneText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void GetPaneText(
    int nIndex,  
    CString& s) const;  
  
CString GetPaneText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `s`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpanewidtha--cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth  
 Recupera el ancho del panel de una barra de estado.  
  
```  
int GetPaneWidth(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel de barra de estado.  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del panel de barra de estado que `nIndex` especifica; de lo contrario, es cero si no existe un panel de barra de estado.  
  
##  <a name="a-namegettiptexta--cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStatusBar::GetTipText  
 Recuperar el texto de información sobre herramientas del panel de la barra de estado.  
  
```  
CString GetTipText(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel para el que se va a recuperar el texto de sugerencia.  
  
### <a name="return-value"></a>Valor devuelto  
 El texto de información sobre herramientas del panel de barra de estado que `nIndex` especifica. De lo contrario, la cadena vacía si no existe un panel de barra de estado especificado `nIndex` o si el texto de información sobre herramientas está vacío.  
  
##  <a name="a-nameinvalidatepanecontenta--cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent  
 Invalidar el panel de la barra de estado y volver a dibujar su contenido.  
  
```  
void InvalidatePaneContent(int nIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel cuyo contenido se invalida y se vuelve a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se invalida la barra de estado, se marca para volver a dibujar. Windows volverá a dibujar cuando el `UpdateWindow` método envía una `WM_PAINT` mensaje a la `OnPaint` (método).  
  
##  <a name="a-nameondrawpanea--cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane  
 Volver a dibujar el panel de la barra de estado.  
  
```  
virtual void OnDrawPane(
    CDC* pDC,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo para dibujar.  
  
 [in] `pPane`  
 Un puntero a un `CMFCStatusBarPaneInfo` estructura que contiene la información sobre el panel se vuelva a dibujar.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `OnDrawPane` vuelve a dibujar el panel mediante el contexto de dispositivo `pDC` según el estilo y el contenido del panel.  
  
 Invalide este método en un `CMFCStatusBar`-clase derivada para personalizar la apariencia de un panel.  
  
##  <a name="a-nameprecreatewindowa--cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `cs`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdrawextendedareaa--cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetDrawExtendedArea(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetindicatorsa--cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStatusBar::SetIndicators  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL SetIndicators(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpIDArray`  
 [in] `nIDCount`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpaneanimationa--cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation  
 Asigna una animación en el panel especificado.  
  
```  
void SetPaneAnimation(
    int nIndex,  
    HIMAGELIST hImageList,  
    UINT nFrameRate=500,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel al que desea que se le asigna una animación.  
  
 [in] `hImageList`  
 Especifica un identificador de la lista de imágenes que contiene los fotogramas de animación.  
  
 [in] `nFrameRate`  
 Especifica la velocidad de fotogramas, en milisegundos, para la animación.  
  
 [in] `bUpdate`  
 Si `TRUE`, actualice el contenido del panel inmediatamente. De lo contrario, el contenido del panel se actualiza cuando invalidarse.  
  
### <a name="remarks"></a>Comentarios  
 Si desea deshabilitar la animación actual, llame a `SetPaneAnimation` con `hImageList` establecido en `NULL`.  
  
##  <a name="a-namesetpanebackgroundcolora--cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor  
 Establece el color de fondo del panel de barra de estado.  
  
```  
void SetPaneBackgroundColor(
    int nIndex,  
    COLORREF clrBackground=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel para el que se establece un nuevo color de fondo.  
  
 [in] `clrBackground`  
 Especifica el nuevo color de fondo.  
  
 [in] `bUpdate`  
 Si `TRUE`, actualice el contenido del panel inmediatamente. De lo contrario, no se actualizan el contenido del panel hasta que el panel se invalida por cualquier otro método.  
  
##  <a name="a-namesetpaneicona--cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon  
 Establecer el icono del panel de barra de estado.  
  
```  
void SetPaneIcon(
    int nIndex,  
    HICON hIcon,  
    BOOL bUpdate=TRUE);

 
void SetPaneIcon(
    int nIndex,  
    HBITMAP hBmp,  
    COLORREF clrTransparent=RGB(255, 0, 255),  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel para el que se va a establecer la imagen.  
  
 [in] `hIcon`  
 Especifica un identificador para el icono que se establecerá como la imagen del panel.  
  
 [in] `bUpdate`  
 Especifica si el contenido del panel se actualizan inmediatamente.  
  
 [in] `hBmp`  
 Especifica un identificador para el mapa de bits que se establecerá como la imagen del panel.  
  
 [in] `clrTransparent`  
 Especifica el color transparente del mapa de bits que el `hBmp` indica.  
  
### <a name="remarks"></a>Comentarios  
 Puede pasar cualquiera `HICON` o `HBITMAP` junto con el color transparente para establecer la imagen del panel. Si no desea mostrar la imagen ya, pase el `NULL` valor como identificador de la imagen.  
  
 Si no hay ninguna animación en ejecución que [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) ha establecido, se detendrá la animación.  
  
##  <a name="a-namesetpaneinfoa--cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPaneInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int cxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `nID`  
 [in] `nStyle`  
 [in] `cxWidth`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpaneprogressa--cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress  
 Establezca el indicador de progreso actual de la barra de progreso del panel especificado.  
  
```  
void SetPaneProgress(
    int nIndex,  
    long nCurr,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel para el que se va a actualizar el indicador de progreso.  
  
 [in] `nCurr`  
 Especifica el valor actual del indicador de progreso.  
  
 [in] `bUpdate`  
 Especifica si se debe actualizar inmediatamente el panel.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando desee actualizar el indicador de progreso de la barra de progreso en el panel especificado.  
  
 Para utilizar esta función para el panel determinado, se debe llamar a [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) primero.  
  
##  <a name="a-namesetpanestylea--cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetPaneStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `nStyle`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpanetexta--cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStatusBar::SetPaneText  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL SetPaneText(
    int nIndex,  
    LPCTSTR lpszNewText,  
    BOOL bUpdate = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 [in] `lpszNewText`  
 [in] `bUpdate`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetpanetextcolora--cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor  
 Establece el color del texto del panel especificado.  
  
```  
void SetPaneTextColor(
    int nIndex,  
    COLORREF clrText=(COLORREF)-1,  
    BOOL bUpdate=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 Especifica el índice del panel que desea asignar un nuevo color de texto.  
  
 [in] `clrText`  
 Especifica el color del texto.  
  
 [in] `bUpdate`  
 Si `TRUE`, actualice el contenido del panel inmediatamente. De lo contrario, no se actualizan el contenido del panel hasta que el panel se invalida por cualquier otro método.  
  
##  <a name="a-namesetpanewidtha--cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth  
 Establezca el ancho del panel de barra de estado.  
  
```  
void SetPaneWidth(
    int nIndex,  
    int cx);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice del panel de barra de estado para el que se establece un nuevo ancho.  
  
 [in] `cx`  
 El nuevo ancho del panel de barra de estado, en píxeles.  
  
##  <a name="a-namesettiptexta--cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStatusBar::SetTipText  
 Establecer el texto de un panel de barra de estado.  
  
```  
void SetTipText(
    int nIndex,  
    LPCTSTR pszTipText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nIndex`  
 El índice de la sección a la que desea asignar el texto de información sobre herramientas.  
  
 [in] `pszTipText`  
 El nuevo texto de información sobre herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CPane](../../mfc/reference/cpane-class.md)   
 [CStatusBar (clase)](../../mfc/reference/cstatusbar-class.md)

