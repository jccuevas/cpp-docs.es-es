---
title: CMFCBaseVisualManager (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db5c1ee0a381d45ce951c627d5f59bfb6eb97ea3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724833"
---
# <a name="cmfcbasevisualmanager-class"></a>CMFCBaseVisualManager (clase)
Una capa entre administradores visuales derivados y la API de tema de Windows.  
  
 `CMFCBaseVisualManager` carga el archivo UxTheme.dll, si está disponible y administra el acceso a los métodos de la API de tema de Windows.  
  
 Esta clase es solo para uso interno.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCBaseVisualManager: public CObject  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::CMFCBaseVisualManager](#cmfcbasevisualmanager)|Construye e inicializa un objeto `CMFCBaseVisualManager`.|  
|`CMFCBaseVisualManager::~CMFCBaseVisualManager`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dibuja un control de casilla de verificación mediante el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dibuja un borde del cuadro combinado con el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dibuja un botón de lista desplegable del cuadro combinado con el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dibuja un botón de comando con el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dibuja un control de botón de radio con el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dibuja una barra de progreso en un control de barra de estado ( [CMFCStatusBar (clase)](../../mfc/reference/cmfcstatusbar-class.md)) con el tema de Windows actual.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Rellena el fondo del control rebar mediante el tema de Windows actual.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtiene el tema de Windows actual.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|||  
|-|-|  
|Name|Descripción|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Las llamadas `CloseThemeData` para obtienen todos los identificadores en `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Las llamadas `OpenThemeData` obtener identificadores para dibujar controles distintos: windows, las barras de herramientas, botones y así sucesivamente.|  
  
## <a name="remarks"></a>Comentarios  
 No es necesario crear instancias de objetos de esta clase directamente.  
  
 Dado que es una clase base para todos los administradores visuales, puede llamar simplemente [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtener un puntero para el administrador Visual actual y tener acceso a los métodos para `CMFCBaseVisualManager` mediante ese puntero. Sin embargo, si tiene que mostrar un control mediante el tema actual de Windows, es mejor usar la `CMFCVisualManagerWindows` interfaz.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxvisualmanager.h  
  
##  <a name="cleanupthemes"></a>  CMFCBaseVisualManager::CleanUpThemes  
 Las llamadas `CloseThemeData` para obtienen todos los identificadores en `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Comentarios  
 Sólo para uso interno.  
  
##  <a name="cmfcbasevisualmanager"></a>  CMFCBaseVisualManager::CMFCBaseVisualManager  
 Construye e inicializa un objeto `CMFCBaseVisualManager`.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="drawcheckbox"></a>  CMFCBaseVisualManager::DrawCheckBox  
 Dibuja un control de casilla de verificación mediante el tema de Windows actual.  
  
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
[in] Un puntero a un contexto de dispositivo  
  
*Rect*<br/>
[in] El rectángulo delimitador de la casilla de verificación.  
  
*bHighlighted*<br/>
[in] Especifica si la casilla de verificación está resaltada.  
  
*nState*<br/>
[in] 0 para no está activada, 1 para activado normal,  
  
 2 para mixto normal.  
  
*bHabilitado*<br/>
[in] Especifica si la casilla de verificación está habilitada.  
  
*bPressed*<br/>
[in] Especifica si la casilla de verificación está presionada.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Los valores de *nState* corresponden a los siguientes estilos de casilla de verificación.  
  
|nState|Casilla de verificación estilo|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="drawcomboborder"></a>  CMFCBaseVisualManager::DrawComboBorder  
 Dibuja el borde del cuadro combinado con el tema de Windows actual.  
  
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
[in] Un puntero a un contexto de dispositivo.  
  
*Rect*<br/>
[in] Rectángulo del borde de cuadro combinado.  
  
*bDeshabilitado*<br/>
[in] Especifica si el borde del cuadro combinado está deshabilitado.  
  
*bIsDropped*<br/>
[in] Especifica si se quita el borde del cuadro combinado.  
  
*bIsHighlighted*<br/>
[in] Especifica si se resalta el borde del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="drawcombodropbutton"></a>  CMFCBaseVisualManager::DrawComboDropButton  
 Dibuja un botón de lista desplegable del cuadro combinado con el tema de Windows actual.  
  
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
|*pDC*|[in] Un puntero a un contexto de dispositivo.|  
|*Rect*|[in] El rectángulo delimitador del botón de lista desplegable de cuadro combinado.|  
|*bDeshabilitado*|[in] Especifica si el botón de lista desplegable del cuadro combinado está deshabilitado.|  
|*bIsDropped*|[in] Especifica si el botón de lista desplegable del cuadro combinado está desplegado.|  
|*bIsHighlighted*|[in] Especifica si se resalta el botón de lista desplegable del cuadro combinado.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="drawpushbutton"></a>  CMFCBaseVisualManager::DrawPushButton  
 Dibuja un botón de comando con el tema de Windows actual.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.  
  
*Rect*<br/>
[in] El rectángulo delimitador del botón de inserción.  
  
*pButton*<br/>
[in] Un puntero a la [CMFCButton (clase)](../../mfc/reference/cmfcbutton-class.md) objeto que se va a dibujar.  
  
*uiState*<br/>
[in] Pasa por alto. El estado se toma del *pButton*.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="drawradiobutton"></a>  CMFCBaseVisualManager::DrawRadioButton  
 Dibuja un control de botón de radio con el tema de Windows actual.  
  
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
[in] Un puntero a un contexto de dispositivo.  
  
*Rect*<br/>
[in] El rectángulo delimitador del botón de radio.  
  
*bHighlighted*<br/>
[in] Especifica si se resalta el botón de radio.  
  
*bChecked*<br/>
[in] Especifica si se activa el botón de radio.  
  
*bHabilitado*<br/>
[in] Especifica si está habilitado el botón de radio.  
  
*bPressed*<br/>
[in] Especifica si se presiona el botón de radio.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="drawstatusbarprogress"></a>  CMFCBaseVisualManager::DrawStatusBarProgress  
 Dibuja la barra de progreso en el control de barra de estado ( [CMFCStatusBar (clase)](../../mfc/reference/cmfcstatusbar-class.md)) con el tema de Windows actual.  
  
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
[in] Un puntero a un contexto de dispositivo.  
  
*pStatusBar*<br/>
[in] Un puntero a la barra de estado. Este valor se omite.  
  
*rectProgress*<br/>
[in] El rectángulo delimitador de la barra de progreso *pDC* coordenadas.  
  
*nProgressTotal*<br/>
[in] El valor de progreso total.  
  
*nProgressCurr*<br/>
[in] El valor de progreso actual.  
  
*clrBar*<br/>
[in] El color inicial. `CMFCBaseVisualManager` pasa por alto esto. Las clases derivadas pueden utilizarlo para degradados de color.  
  
*clrProgressBarDest*<br/>
[in] Color final. `CMFCBaseVisualManager` pasa por alto esto. Las clases derivadas pueden utilizarlo para degradados de color.  
  
*clrProgressText*<br/>
[in] Color del texto de progreso. `CMFCBaseVisualManager` pasa por alto esto. El color del texto se define mediante `afxGlobalData.clrBtnText`.  
  
*bProgressText*<br/>
[in] Especifica si se debe mostrar el texto de progreso.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="fillrebarpane"></a>  CMFCBaseVisualManager::FillReBarPane  
 Rellena el fondo del control rebar mediante el tema de Windows actual.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
*pDC*<br/>
[in] Un puntero a un contexto de dispositivo.  
  
*pBar*<br/>
[in] Un puntero a un panel cuyo fondo debe dibujarse.  
  
*rectClient*<br/>
[in] El rectángulo delimitador del área que se va a rellenar.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la API de tema; en caso contrario, FALSE.  
  
##  <a name="getstandardwindowstheme"></a>  CMFCBaseVisualManager::GetStandardWindowsTheme  
 Obtiene el tema de Windows actual.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color del tema de Windows seleccionado actualmente. Puede ser uno de los valores enumerados siguientes:  
  
- `WinXpTheme_None` -No hay ningún tema habilitado.  
  
- `WinXpTheme_NonStandard` -tema estándar no está seleccionado (es decir, se selecciona un tema, pero ninguno en la lista siguiente).  
  
- `WinXpTheme_Blue` -el tema azul (Luna).  
  
- `WinXpTheme_Olive` -tema olivo.  
  
- `WinXpTheme_Silver` -tema plateado.  
  
##  <a name="updatesystemcolors"></a>  CMFCBaseVisualManager::UpdateSystemColors  
 Las llamadas `OpenThemeData` obtener identificadores para dibujar controles distintos: windows, las barras de herramientas, botones y así sucesivamente.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Comentarios  
 Sólo para uso interno.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)
