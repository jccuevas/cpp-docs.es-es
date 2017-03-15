---
title: Clase CMFCBaseVisualManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseVisualManager
- CMFCBaseVisualManager.~CMFCBaseVisualManager
- ~CMFCBaseVisualManager
- CMFCBaseVisualManager::~CMFCBaseVisualManager
dev_langs:
- C++
helpviewer_keywords:
- ~CMFCBaseVisualManager destructor
- CMFCBaseVisualManager class, destructor
- CMFCBaseVisualManager class
ms.assetid: d56f3afc-cdea-4de1-825a-a08999c571e0
caps.latest.revision: 24
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7c726fe71b7dcf26353fe0ce3a6b383eb5b578b9
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasevisualmanager-class"></a>Clase CMFCBaseVisualManager
Una capa entre derivados administradores visuales y la API de tema de Windows.  
  
 `CMFCBaseVisualManager`carga el archivo UxTheme.dll, si está disponible y administra el acceso a los métodos de la API de tema de Windows.  
  
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
|[CMFCBaseVisualManager::DrawCheckBox](#drawcheckbox)|Dibuja un control de casilla de verificación mediante el tema de Windows actual.|  
|[CMFCBaseVisualManager::DrawComboBorder](#drawcomboborder)|Dibuja un borde de cuadro combinado con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawComboDropButton](#drawcombodropbutton)|Dibuja un botón de lista desplegable del cuadro combinado con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawPushButton](#drawpushbutton)|Dibuja un botón de inserción con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawRadioButton](#drawradiobutton)|Dibuja un control de botón de radio con el tema actual de Windows.|  
|[CMFCBaseVisualManager::DrawStatusBarProgress](#drawstatusbarprogress)|Dibuja una barra de progreso en un control de barra de estado ( [CMFCStatusBar clase](../../mfc/reference/cmfcstatusbar-class.md)) con el tema actual de Windows.|  
|[CMFCBaseVisualManager::FillReBarPane](#fillrebarpane)|Rellena el fondo del control rebar utilizando el tema actual de Windows.|  
|[CMFCBaseVisualManager::GetStandardWindowsTheme](#getstandardwindowstheme)|Obtiene el tema de Windows actual.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|||  
|-|-|  
|Nombre|Descripción|  
|[CMFCBaseVisualManager::CleanUpThemes](#cleanupthemes)|Llamadas `CloseThemeData` para todos los identificadores que se obtiene en `UpdateSystemColors`.|  
|[CMFCBaseVisualManager::UpdateSystemColors](#updatesystemcolors)|Llamadas `OpenThemeData` para obtener controladores para dibujar controles distintos: windows, barras de herramientas, botones y así sucesivamente.|  
  
## <a name="remarks"></a>Comentarios  
 No es necesario crear instancias de objetos de esta clase directamente.  
  
 Dado que es una clase base para todos los administradores visuales, puede llamar simplemente [CMFCVisualManager::GetInstance](../../mfc/reference/cmfcvisualmanager-class.md#getinstance), obtener un puntero al administrador Visual actual y tener acceso a los métodos para `CMFCBaseVisualManager` con ese puntero. Sin embargo, si se debe mostrar un control con el tema actual de Windows, es mejor utilizar el `CMFCVisualManagerWindows` interfaz.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxvisualmanager.h  
  
##  <a name="a-namecleanupthemesa--cmfcbasevisualmanagercleanupthemes"></a><a name="cleanupthemes"></a>CMFCBaseVisualManager::CleanUpThemes  
 Llamadas `CloseThemeData` para todos los identificadores que se obtiene en `UpdateSystemColors`.  
  
```  
void CleanUpThemes();
```  
  
### <a name="remarks"></a>Comentarios  
 Sólo para uso interno.  
  
##  <a name="a-namecmfcbasevisualmanagera--cmfcbasevisualmanagercmfcbasevisualmanager"></a><a name="cmfcbasevisualmanager"></a>CMFCBaseVisualManager::CMFCBaseVisualManager  
 Construye e inicializa un objeto `CMFCBaseVisualManager`.  
  
```  
CMFCBaseVisualManager();
```  
  
##  <a name="a-namedrawcheckboxa--cmfcbasevisualmanagerdrawcheckbox"></a><a name="drawcheckbox"></a>CMFCBaseVisualManager::DrawCheckBox  
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
 [in] `pDC`  
 Un puntero a un contexto de dispositivo  
  
 [in] `rect`  
 El rectángulo delimitador de la casilla de verificación.  
  
 [in] `bHighlighted`  
 Especifica si la casilla de verificación está resaltada.  
  
 [in] `nState`  
 0 para no está activada, 1 para activado normal,  
  
 2 para mixto normal.  
  
 [in] `bEnabled`  
 Especifica si está habilitada la casilla de verificación.  
  
 [in] `bPressed`  
 Especifica si la casilla de verificación está presionada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Los valores de `nState` se corresponden con los siguientes estilos de casilla de verificación.  
  
|nState|Estilo de la casilla de verificación|  
|------------|---------------------|  
|0|CBS_UNCHECKEDNORMAL|  
|1|CBS_CHECKEDNORMAL|  
|2|CBS_MIXEDNORMAL|  
  
##  <a name="a-namedrawcombobordera--cmfcbasevisualmanagerdrawcomboborder"></a><a name="drawcomboborder"></a>CMFCBaseVisualManager::DrawComboBorder  
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
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Rectángulo delimitador del borde de cuadro combinado.  
  
 [in] `bDisabled`  
 Especifica si está deshabilitado el borde del cuadro combinado.  
  
 [in] `bIsDropped`  
 Especifica si el borde del cuadro combinado está desplegado.  
  
 [in] `bIsHighlighted`  
 Especifica si se resalta el borde del cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namedrawcombodropbuttona--cmfcbasevisualmanagerdrawcombodropbutton"></a><a name="drawcombodropbutton"></a>CMFCBaseVisualManager::DrawComboDropButton  
 Dibuja un botón de lista desplegable del cuadro combinado con el tema actual de Windows.  
  
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
|[in] `pDC`|Puntero a un contexto de dispositivo.|  
|[in] `rect`|El rectángulo delimitador del botón de lista desplegable de cuadro combinado.|  
|[in] `bDisabled`|Especifica si el botón de lista desplegable del cuadro combinado está deshabilitado.|  
|[in] `bIsDropped`|Especifica si el botón de lista desplegable del cuadro combinado está desplegado.|  
|[in] `bIsHighlighted`|Especifica si se resalta el botón de lista desplegable del cuadro combinado.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namedrawpushbuttona--cmfcbasevisualmanagerdrawpushbutton"></a><a name="drawpushbutton"></a>CMFCBaseVisualManager::DrawPushButton  
 Dibuja un botón de inserción con el tema actual de Windows.  
  
```  
virtual BOOL DrawPushButton(
    CDC* pDC,   
    CRect rect,   
    CMFCButton* pButton,   
    UINT uiState);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 El rectángulo delimitador del botón de inserción.  
  
 [in] `pButton`  
 Un puntero a la [CMFCButton clase](../../mfc/reference/cmfcbutton-class.md) objeto que se va a dibujar.  
  
 [in] `uiState`  
 ignorado. El estado se toma del `pButton`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namedrawradiobuttona--cmfcbasevisualmanagerdrawradiobutton"></a><a name="drawradiobutton"></a>CMFCBaseVisualManager::DrawRadioButton  
 Dibuja un control de botón de radio con el tema actual de Windows.  
  
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
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 El rectángulo delimitador del botón de radio.  
  
 [in] `bHighlighted`  
 Especifica si se resalta el botón de radio.  
  
 [in] `bChecked`  
 Especifica si el botón de radio está activado.  
  
 [in] `bEnabled`  
 Especifica si está habilitado el botón de radio.  
  
 [in] `bPressed`  
 Especifica si se presiona el botón de radio.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namedrawstatusbarprogressa--cmfcbasevisualmanagerdrawstatusbarprogress"></a><a name="drawstatusbarprogress"></a>CMFCBaseVisualManager::DrawStatusBarProgress  
 Dibuja la barra de progreso en el control de barra de estado ( [CMFCStatusBar clase](../../mfc/reference/cmfcstatusbar-class.md)) con el tema actual de Windows.  
  
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
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pStatusBar`  
 Puntero a la barra de estado. Este valor se omite.  
  
 [in] `rectProgress`  
 El rectángulo delimitador de la barra de progreso `pDC` coordenadas.  
  
 [in] `nProgressTotal`  
 El valor de progreso total.  
  
 [in] `nProgressCurr`  
 El valor de progreso actual.  
  
 [in] `clrBar`  
 El color inicial. `CMFCBaseVisualManager`las omite. Las clases derivadas pueden utilizarlo para degradados de color.  
  
 [in] `clrProgressBarDest`  
 Color final. `CMFCBaseVisualManager`las omite. Las clases derivadas pueden utilizarlo para degradados de color.  
  
 [in] `clrProgressText`  
 Color del texto de progreso. `CMFCBaseVisualManager`las omite. Define el color del texto `afxGlobalData.clrBtnText`.  
  
 [in] `bProgressText`  
 Especifica si se muestra el texto de progreso.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namefillrebarpanea--cmfcbasevisualmanagerfillrebarpane"></a><a name="fillrebarpane"></a>CMFCBaseVisualManager::FillReBarPane  
 Rellena el fondo del control rebar utilizando el tema actual de Windows.  
  
```  
virtual void FillReBarPane(
    CDC* pDC,   
    CBasePane* pBar,   
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Un puntero a un panel debe dibujarse cuyo fondo.  
  
 [in] `rectClient`  
 El rectángulo delimitador del área que desea rellenar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si está habilitada la API del tema; de lo contrario, `FALSE`.  
  
##  <a name="a-namegetstandardwindowsthemea--cmfcbasevisualmanagergetstandardwindowstheme"></a><a name="getstandardwindowstheme"></a>CMFCBaseVisualManager::GetStandardWindowsTheme  
 Obtiene el tema de Windows actual.  
  
```  
virtual WinXpTheme GetStandardWindowsTheme();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color del tema de Windows seleccionado actualmente. Puede ser uno de los valores enumerados siguientes:  
  
- `WinXpTheme_None`-No hay ningún tema habilitado.  
  
- `WinXpTheme_NonStandard`-tema estándar no está activado (es decir, selecciona un tema, pero ninguno en la lista siguiente).  
  
- `WinXpTheme_Blue`-el tema azul (Luna).  
  
- `WinXpTheme_Olive`-tema olivo.  
  
- `WinXpTheme_Silver`-tema plateado.  
  
##  <a name="a-nameupdatesystemcolorsa--cmfcbasevisualmanagerupdatesystemcolors"></a><a name="updatesystemcolors"></a>CMFCBaseVisualManager::UpdateSystemColors  
 Llamadas `OpenThemeData` para obtener controladores para dibujar controles distintos: windows, barras de herramientas, botones y así sucesivamente.  
  
```  
void UpdateSystemColors();
```  
  
### <a name="remarks"></a>Comentarios  
 Sólo para uso interno.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)

