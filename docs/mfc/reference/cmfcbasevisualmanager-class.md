---
title: CMFCBaseVisualManager (Clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::CMFCBaseVisualManager
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawCheckBox
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboBorder
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawComboDropButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawPushButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawRadioButton
- AFXVISUALMANAGER/CMFCBaseVisualManager::DrawStatusBarProgress
- AFXVISUALMANAGER/CMFCBaseVisualManager::FillReBarPane
- AFXVISUALMANAGER/CMFCBaseVisualManager::GetStandardWindowsTheme
- AFXVISUALMANAGER/CMFCBaseVisualManager::CleanUpThemes
- AFXVISUALMANAGER/CMFCBaseVisualManager::UpdateSystemColors
helpviewer_keywords:
- CMFCBaseVisualManager [MFC], CMFCBaseVisualManager
- CMFCBaseVisualManager [MFC], DrawCheckBox
- CMFCBaseVisualManager [MFC], DrawComboBorder
- CMFCBaseVisualManager [MFC], DrawComboDropButton
- CMFCBaseVisualManager [MFC], DrawPushButton
- CMFCBaseVisualManager [MFC], DrawRadioButton
- CMFCBaseVisualManager [MFC], DrawStatusBarProgress
- CMFCBaseVisualManager [MFC], FillReBarPane
- CMFCBaseVisualManager [MFC], GetStandardWindowsTheme
- CMFCBaseVisualManager [MFC], CleanUpThemes
- CMFCBaseVisualManager [MFC], UpdateSystemColors
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
ms.openlocfilehash: a3288949bd4867115c32d2cbffd09cf4f7c6b40b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367810"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager (Clase)

Una capa entre los administradores visuales derivados y la API de temas de Windows.

`CMFCBaseVisualManager`carga UxTheme.dll, si está disponible, y administra el acceso a los métodos de la API de tema de Windows.

Esta clase es solo para uso interno.

## <a name="syntax"></a>Sintaxis

```
class CMFCBaseVisualManager: public CObject
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Construye e inicializa un objeto `CMFCBaseVisualManager`.|
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|Nombre|Descripción|
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dibuja un control de casilla de verificación mediante el tema actual de Windows.|
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dibuja un borde de cuadro combinado con el tema actual de Windows.|
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dibuja un botón desplegable de cuadro combinado con el tema actual de Windows.|
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dibuja un botón con el tema actual de Windows.|
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dibuja un control de botón de opción mediante el tema actual de Windows.|
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dibuja una barra de progreso en un control de barra de estado ( [CMFCStatusBar (clase)](../../mfc/reference/cmfcstatusbar-class.md)utilizando el tema actual de Windows.|
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Rellena el fondo del control de armadura mediante el tema actual de Windows.|
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtiene el tema actual de Windows.|

### <a name="protected-methods"></a>Métodos protegidos

|||
|-|-|
|Nombre|Descripción|
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Llamadas `CloseThemeData` para todos `UpdateSystemColors`los identificadores obtenidos en .|
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Llamadas `OpenThemeData` para obtener identificadores para dibujar varios controles: ventanas, barras de herramientas, botones, etc.|

## <a name="remarks"></a>Observaciones

No es necesario crear instancias de objetos de esta clase directamente.

Dado que es una clase base para todos los administradores visuales, puede llamar a [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtener un puntero al Administrador visual actual y tener acceso a los métodos para `CMFCBaseVisualManager` usar ese puntero. Sin embargo, si tiene que mostrar un control mediante el tema `CMFCVisualManagerWindows` actual de Windows, es mejor utilizar la interfaz.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxvisualmanager.h

## <a name="cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes

Llamadas `CloseThemeData` para todos `UpdateSystemColors`los identificadores obtenidos en .

```
void CleanUpThemes();
```

### <a name="remarks"></a>Observaciones

Solo para uso interno.

## <a name="cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager

Construye e inicializa un objeto `CMFCBaseVisualManager`.

```
CMFCBaseVisualManager();
```

## <a name="cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox

Dibuja un control de casilla de verificación mediante el tema actual de Windows.

```
virtual BOOL DrawCheckBox(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    int nState,
    BOOL bEnabled,
    BOOL bPressed);

);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Un puntero a un contexto de dispositivo

*Rect*<br/>
[en] El rectángulo delimitador de la casilla de verificación.

*bResaltado*<br/>
[en] Especifica si la casilla de verificación está resaltada.

*nEstado*<br/>
[in] 0 para desmarcado, 1 para la normalidad comprobada,

2 para normal mezclado.

*bHabilitado*<br/>
[en] Especifica si la casilla de verificación está habilitada.

*bPressed*<br/>
[en] Especifica si se presiona la casilla de verificación.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Los valores de *nState* corresponden a los siguientes estilos de casilla de verificación.

|nEstado|Estilo de casilla de verificación|
|------------|---------------------|
|0|CBS_UNCHECKEDNORMAL|
|1|CBS_CHECKEDNORMAL|
|2|CBS_MIXEDNORMAL|

## <a name="cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder

Dibuja el borde del cuadro combinado con el tema actual de Windows.

```
virtual BOOL DrawComboBorder(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] Rectángulo delimitador del borde del cuadro combinado.

*bDiscapacitados*<br/>
[en] Especifica si el borde del cuadro combinado está deshabilitado.

*bIsDropped*<br/>
[en] Especifica si se coloca el borde del cuadro combinado.

*bIsHighlighted*<br/>
[en] Especifica si el borde del cuadro combinado está resaltado.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton

Dibuja un botón desplegable de cuadro combinado con el tema actual de Windows.

```
virtual BOOL DrawComboDropButton(
    CDC* pDC,
    CRect rect,
    BOOL bDisabled,
    BOOL bIsDropped,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*pDC*|[en] Puntero a un contexto de dispositivo.|
|*Rect*|[en] El rectángulo delimitador del botón desplegable del cuadro combinado.|
|*bDiscapacitados*|[en] Especifica si el botón desplegable del cuadro combinado está deshabilitado.|
|*bIsDropped*|[en] Especifica si se coloca el botón desplegable del cuadro combinado.|
|*bIsHighlighted*|[en] Especifica si el botón desplegable del cuadro combinado está resaltado.|

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton

Dibuja un botón con el tema actual de Windows.

```
virtual BOOL DrawPushButton(
    CDC* pDC,
    CRect rect,
    CMFCButton* pButton,
    UINT uiState);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] El rectángulo delimitador del pulsador.

*pButton*<br/>
[en] Puntero a la [CMFCButton clase](../../mfc/reference/cmfcbutton-class.md) objeto que se va a dibujar.

*uiState*<br/>
[en] Ignorado. El estado se toma de *pButton*.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton

Dibuja un control de botón de opción mediante el tema actual de Windows.

```
virtual BOOL DrawRadioButton(
    CDC* pDC,
    CRect rect,
    BOOL bHighlighted,
    BOOL bChecked,
    BOOL bEnabled,
    BOOL bPressed);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*Rect*<br/>
[en] El rectángulo delimitador del botón de opción.

*bResaltado*<br/>
[en] Especifica si el botón de opción está resaltado.

*bChecked*<br/>
[en] Especifica si el botón de opción está activado.

*bHabilitado*<br/>
[en] Especifica si el botón de opción está habilitado.

*bPressed*<br/>
[en] Especifica si se pulsa el botón de opción.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress

Dibuja la barra de progreso en el control de barra de estado ( [CMFCStatusBar (clase)](../../mfc/reference/cmfcstatusbar-class.md)utilizando el tema actual de Windows.

```
virtual BOOL DrawStatusBarProgress(
    CDC* pDC,
    CMFCStatusBar* pStatusBar,
    CRect rectProgress,
    int nProgressTotal,
    int nProgressCurr,
    COLORREF clrBar,
    COLORREF clrProgressBarDest,
    COLORREF clrProgressText,
    BOOL bProgressText);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*pStatusBar*<br/>
[en] Un puntero a la barra de estado. Este valor se omite.

*rectProgress*<br/>
[en] El rectángulo delimitador de la barra de progreso en coordenadas *pDC.*

*nProgressTotal*<br/>
[en] El valor de progreso total.

*nProgressCurr*<br/>
[en] El valor de progreso actual.

*clrBar*<br/>
[en] El color de inicio. `CMFCBaseVisualManager`ignora esto. Las clases derivadas pueden usarla para degradados de color.

*clrProgressBarDest*<br/>
[en] El color final. `CMFCBaseVisualManager`ignora esto. Las clases derivadas pueden usarla para degradados de color.

*clrProgressText*<br/>
[en] Color del texto de progreso. `CMFCBaseVisualManager`ignora esto. El color del `afxGlobalData.clrBtnText`texto se define mediante .

*bProgressText*<br/>
[en] Especifica si se debe mostrar el texto de progreso.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane

Rellena el fondo del control de armadura mediante el tema actual de Windows.

```
virtual void FillReBarPane(
    CDC* pDC,
    CBasePane* pBar,
    CRect rectClient);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo.

*pBar*<br/>
[en] Puntero a un panel cuyo fondo se debe dibujar.

*rectClient*<br/>
[en] El rectángulo delimitador del área que se va a rellenar.

### <a name="return-value"></a>Valor devuelto

TRUESi la API de tema está habilitada; de lo contrario FALSO.

## <a name="cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme

Obtiene el tema actual de Windows.

```
virtual WinXpTheme GetStandardWindowsTheme();
```

### <a name="return-value"></a>Valor devuelto

El color del tema de Windows seleccionado actualmente. Puede ser uno de los siguientes valores enumerados:

- `WinXpTheme_None`- no hay ningún tema habilitado.

- `WinXpTheme_NonStandard`- Se selecciona el tema no estándar (lo que significa que se selecciona un tema, pero ninguno de la lista siguiente).

- `WinXpTheme_Blue`- Tema azul (Luna).

- `WinXpTheme_Olive`- Tema de la aceituna.

- `WinXpTheme_Silver`- Tema de plata.

## <a name="cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors

Llamadas `OpenThemeData` para obtener identificadores para dibujar varios controles: ventanas, barras de herramientas, botones, etc.

```
void UpdateSystemColors();
```

### <a name="remarks"></a>Observaciones

Solo para uso interno.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
