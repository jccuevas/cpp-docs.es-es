---
title: CMFCStatusBar (clase)
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366049"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar (clase)

La `CMFCStatusBar` clase implementa una barra `CStatusBar` de estado similar a la clase. Sin embargo, la clase `CMFCStatusBar` tiene características que no ofrece la clase `CStatusBar` , tales como la capacidad para mostrar imágenes, animaciones y barras de progreso y la capacidad de responder a los doble clics del mouse.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Reemplaza [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Crear](#create)|Crea una barra de control y la adjunta al objeto [CPane.](../../mfc/reference/cpane-class.md) (Reemplaza [CPane::Crear](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Crea una barra de control y la adjunta al objeto [CPane.](../../mfc/reference/cpane-class.md) (Reemplaza [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si se puede insertar dinámicamente otro panel entre este panel y el marco primario. (Reemplaza [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Habilita o deshabilita el control de los clics dobles del ratón en la barra de estado.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Muestra una barra de progreso en el panel especificado.|
|[CMFCStatusBar::GetCount](#getcount)|Devuelve el número de paneles de la barra de estado.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Devuelve el estilo de panel. (Reemplaza [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Devuelve el ancho, en píxeles, del panel especificado de la barra de estado.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Devuelve el texto de información sobre herramientas para el panel especificado de la barra de estado.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Invalida el panel especificado y vuelve a dibujar su contenido.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Llamado por el marco de trabajo antes `CWnd` de la creación de la ventana de Windows adjunta a este objeto. (Reemplaza [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndicators](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Asigna una animación al panel especificado.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Establece el color de fondo para el panel especificado de la barra de estado.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Establece el icono del indicador para el panel especificado de la barra de estado.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Establece el progreso actual de la barra de progreso para el panel especificado de la barra de estado.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Establece el estilo del panel. (Reemplaza [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Establece el color del texto para el panel especificado de la barra de estado.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Establece el ancho en píxeles del panel especificado de la barra de estado.|
|[CMFCStatusBar::SetTipText](#settiptext)|Establece el texto de información sobre herramientas para el panel especificado de la barra de estado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Llamado por el marco de trabajo cuando vuelve a dibujar el panel de la barra de estado.|

## <a name="remarks"></a>Observaciones

En el diagrama siguiente se muestra una figura de la barra de estado de la aplicación de [ejemplo Demostración](../../overview/visual-cpp-samples.md) de barra de estado.

![Ejemplo de CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Ejemplo de CMFCStatusBar")

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran las variables locales que la aplicación utiliza para llamar a varios métodos de la `CMFCStatusBar` clase. Estas variables se declaran en StatusBarDemoView.h. El marco principal se declara en MainFrm.h, el documento se declara en StatusBarDemoDoc.h y la vista se declara en StatusBarDemoView.h. Este fragmento de código forma parte del [ejemplo Demostración](../../overview/visual-cpp-samples.md)de barra de estado.

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCStatusBar` cómo obtener `GetStatusBar` una referencia a object introduciendo el `GetStatusBar` método en MainFrm.h y, a continuación, llamando a este método desde el método en StatusBarDemoView.h. Este fragmento de código forma parte del [ejemplo Demostración](../../overview/visual-cpp-samples.md)de barra de estado.

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCStatusBar` cómo llamar a varios métodos de la clase en StatusBarDemoView.cpp. Las constantes se declaran en MainFrm.h. En el ejemplo se muestra cómo establecer el icono, establecer el texto de información sobre herramientas del panel de la barra de estado, mostrar una barra de progreso en el panel especificado, asignar una animación al panel especificado, establecer el texto y el ancho del panel de la barra de estado y establecer el indicador de progreso actual de la barra de progreso para el panel de la barra de estado. Este fragmento de código forma parte del [ejemplo Demostración](../../overview/visual-cpp-samples.md)de barra de estado.

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout

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

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIDFind*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFCStatusBar::Crear

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

[en] *pParentWnd*<br/>
[en] *dwStyle*<br/>
[en] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parámetros

[en] *pParentWnd*<br/>
[en] *dwCtrlStyle*<br/>
[en] *dwStyle*<br/>
[en] *nID*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick

Habilita o deshabilita el control de los clics dobles del ratón en la barra de estado.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] Si es TRUE, habilite el procesamiento del mouse con doble clic. De lo contrario, deshabilite el procesamiento del clic doble del ratón.

### <a name="remarks"></a>Observaciones

Si la barra de estado está habilitada para procesar doble clics, Windows envía la notificación WM_COMMAND junto con un identificador de recurso al propietario de la barra de estado cada vez que el usuario hace doble clic en el panel de la barra de estado.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar

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

*nIndex*<br/>
[en] Especifica el índice del panel cuya barra de progreso se va a habilitar.

*nTotal*<br/>
[en] Especifica el valor máximo de la barra de progreso.

*bDisplayText*<br/>
[en] Especifica si la barra de progreso debe mostrar el valor de progreso actual.

*clrBar*<br/>
[en] Especifica el color de fondo de la barra de progreso.

*clrBarDest*<br/>
[en] Especifica el color secundario del fondo de la barra de progreso. Utilice un valor diferente al *de clrBar* para rellenar un color mezclado en un degradado.

*clrProgressText*<br/>
[en] Especifica el color del texto de la barra de progreso.

### <a name="remarks"></a>Observaciones

Si desea deshabilitar la llamada `EnablePaneProgressBar` a la barra de progreso con *nTotal* establecido en -1. De forma *predeterminada, nTotal* se establece en 100. Por lo tanto, no necesita ningún cálculo adicional para mostrar el progreso como porcentaje.

Debe pasar valores diferentes para *clrBar* y *clrBarDest* para que el color de fondo de la barra de progreso muestre un color mezclado en un degradado. .

Para establecer el progreso actual, llame a la [CMFCStatusBar::SetPaneProgress](#setpaneprogress) método.

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStatusBar::GetCount

Recupera el número de paneles de la barra de estado.

```
int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de paneles de la barra de estado.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parámetros

[en] *rect*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *lpRect*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *nID*<br/>
[en] *nStyle*<br/>
[en] *cxWidth*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *s*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth

Recupera el ancho del panel de una barra de estado.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel de la barra de estado.

### <a name="return-value"></a>Valor devuelto

El ancho del panel de la barra de estado que *nIndex* especifica; de lo contrario, cero si no existe un panel de barra de estado.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStatusBar::GetTipText

Recupere el texto de información sobre herramientas del panel de una barra de estado.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel para el que se va a recuperar el texto de información sobre herramientas.

### <a name="return-value"></a>Valor devuelto

Texto de información sobre herramientas del panel de barra de estado que *nIndex* especifica. De lo contrario, la cadena vacía si no existe un panel de barra de estado para el *nIndex* especificado o si su texto de información sobre herramientas está vacío.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent

Invalide el panel de la barra de estado y vuelva a dibujar su contenido.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel cuyo contenido se va a invalidar y volver a dibujar.

### <a name="remarks"></a>Observaciones

Cuando se invalida la barra de estado, se marca para volver a dibujarla. Windows lo vuelve a `UpdateWindow` dibujar cuando el `OnPaint` método envía un mensaje de WM_PAINT al método.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane

Vuelva a dibujar el panel de la barra de estado.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo para dibujar.

*pPane*<br/>
[en] Puntero a `CMFCStatusBarPaneInfo` una estructura que contiene la información sobre el panel que se va a volver a dibujar.

### <a name="remarks"></a>Observaciones

De forma `OnDrawPane` predeterminada, vuelve a dibujar el panel mediante el *pDC* de contexto de dispositivo según el estilo y el contenido del panel.

Invalide este `CMFCStatusBar`método en una clase derivada para personalizar la apariencia de un panel.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parámetros

[en] *cs*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *bSet*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStatusBar::SetIndicators

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parámetros

[en] *lpIDArray*<br/>
[en] *nIDCount*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation

Asigna una animación al panel especificado.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel al que desea asignarle una animación.

*hImageList*<br/>
[en] Especifica un identificador de la lista de imágenes que contiene los fotogramas de animación.

*nFrameRate*<br/>
[en] Especifica la velocidad de fotogramas, en milisegundos, para la animación.

*bActualización*<br/>
[en] Si es TRUE, actualice el contenido del panel inmediatamente. De lo contrario, el contenido del panel se actualiza cuando se invalida.

### <a name="remarks"></a>Observaciones

Si desea deshabilitar la animación `SetPaneAnimation` `hImageList` actual, llame con establecido en NULL.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor

Establece el color de fondo del panel de la barra de estado.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel para el que se va a establecer un nuevo color de fondo.

*clrBackground*<br/>
[en] Especifica el nuevo color de fondo.

*bActualización*<br/>
[en] Si es TRUE, actualice el contenido del panel inmediatamente. De lo contrario, no actualice el contenido del panel hasta que otro método invalide el panel.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon

Establezca el icono del panel de la barra de estado.

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

*nIndex*<br/>
[en] Especifica el índice del panel para el que se va a establecer la imagen.

*hIcon*<br/>
[en] Especifica un identificador del icono que se establecerá como imagen del panel.

*bActualización*<br/>
[en] Especifica si se debe actualizar el contenido del panel inmediatamente.

*hBmp*<br/>
[en] Especifica un identificador del mapa de bits que se establecerá como la imagen del panel.

*clrTransparent*<br/>
[en] Especifica el color transparente del mapa de bits que indica el *hBmp.*

### <a name="remarks"></a>Observaciones

Puede pasar HICON o HBITMAP junto con el color transparente para establecer la imagen del panel. Si no desea mostrar la imagen más tiempo, pase el valor NULL como identificador de imagen.

Si hay alguna animación en ejecución que [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) ha establecido, la animación se detendrá.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *nID*<br/>
[en] *nStyle*<br/>
[en] *cxWidth*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress

Establezca el indicador de progreso actual de la barra de progreso para el panel especificado.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel para el que se va a actualizar el indicador de progreso.

*nCurr*<br/>
[en] Especifica el valor actual del indicador de progreso.

*bActualización*<br/>
[en] Especifica si el panel debe actualizarse inmediatamente.

### <a name="remarks"></a>Observaciones

Llame a este método cuando desee actualizar el indicador de progreso de la barra de progreso en el panel especificado.

Para utilizar esta función para el panel especificado, primero debe llamar a [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) .

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *nStyle*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parámetros

[en] *nIndex*<br/>
[en] *lpszNewText*<br/>
[en] *bActualización*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor

Establece el color del texto del panel especificado.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] Especifica el índice del panel al que desea asignar un nuevo color de texto.

*clrText*<br/>
[en] Especifica el color del texto.

*bActualización*<br/>
[en] Si es TRUE, actualice el contenido del panel inmediatamente. De lo contrario, no actualice el contenido del panel hasta que otro método invalide el panel.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth

Establezca el ancho del panel de la barra de estado.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] El índice del panel de la barra de estado para el que se debe establecer un nuevo ancho.

*Cx*<br/>
[en] El nuevo ancho del panel de la barra de estado, en píxeles.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStatusBar::SetTipText

Establezca el texto de información sobre herramientas de un panel de la barra de estado.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parámetros

*nIndex*<br/>
[en] El índice del panel al que desea asignar el texto de información sobre herramientas.

*pszTipText*<br/>
[en] El nuevo texto de información sobre herramientas.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[Clase CStatusBar](../../mfc/reference/cstatusbar-class.md)
