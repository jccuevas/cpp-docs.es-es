---
title: Clase CMFCMenuBar
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 278feca6b64915d0cf789e8f68af3c3fdf9b3129
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739474"
---
# <a name="cmfcmenubar-class"></a>Clase CMFCMenuBar

Una barra de menús que implementa el acoplamiento.
Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Invalida `CMFCToolBar::AdjustLocations`).|
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Especifica si las etiquetas de texto se pueden mostrar en las imágenes de los botones de la barra de herramientas. (Invalida [CMFCToolBar:: AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)).|
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Calcula el tamaño horizontal de la barra de herramientas. (Invalida [CMFCToolBar:: CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)).|
|[CMFCMenuBar::CalcLayout](#calclayout)|(Invalida `CMFCToolBar::CalcLayout`).|
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcula el alto máximo de los botones en la barra de herramientas. (Invalida [CMFCToolBar:: CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)).|
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Especifica si un usuario puede cerrar la barra de herramientas. (Invalida [CMFCToolBar:: CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)).|
|[CMFCMenuBar::CanBeRestored](#canberestored)|Determina si el sistema puede restaurar el estado original de una barra de herramientas después de la personalización. (Invalida [CMFCToolBar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)).|
|[CMFCMenuBar::Create](#create)|Crea un control de menú y lo adjunta a un `CMFCMenuBar` objeto.|
|[CMFCMenuBar::CreateEx](#createex)|Crea un `CMFCMenuBar` objeto con opciones de estilo adicionales.|
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicializa un `CMFCMenuBar` objeto. Acepta un parámetro HMENU que actúa como plantilla para un rellenado `CMFCMenuBar`.|
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Habilita un cuadro combinado de **ayuda** que se encuentra en el lado derecho de la barra de menús.|
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Especifica si se mostrarán las sombras de los menús emergentes.|
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Invalida [CPane:: GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize)).|
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Devuelve el ancho de los botones de la barra de herramientas. (Invalida [CMFCToolBar:: GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)).|
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Devuelve un identificador para el menú original en el archivo de recursos.|
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Devuelve el identificador de recursos del menú original en el archivo de recursos.|
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Devuelve un puntero al cuadro combinado de **ayuda** .|
|[CMFCMenuBar::GetHMenu](#gethmenu)|Devuelve el identificador del menú que está asociado al `CMFCMenuBar` objeto.|
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Devuelve la fuente global actual para los objetos de menú.|
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Devuelve el botón de la barra de herramientas asociado al índice del elemento proporcionado.|
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de la barra de herramientas. (Invalida [CMFCToolBar:: GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)).|
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Indica si se resaltan los elementos de menú deshabilitados.|
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que tienen bordes extendidos. (Invalida [CMFCToolBar:: IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)).|
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Indica si se resaltan los elementos deshabilitados.|
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Indica si se dibujan sombras para los menús emergentes.|
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Indica si los comandos de menú usados recientemente se muestran en la barra de menús.|
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Indica si los menús emergentes muestran todos los comandos.|
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Indica si los menús muestran todos los comandos después de un breve retraso.|
|[CMFCMenuBar::LoadState](#loadstate)|Carga el estado del `CMFCMenuBar` objeto desde el registro.|
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Lo llama el marco de trabajo cuando un usuario selecciona un botón en la barra de herramientas. (Invalida [CMFCToolBar:: OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)).|
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Lo llama el marco de trabajo cuando una ventana de marco carga el menú predeterminado del archivo de recursos.|
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Lo llama el marco de trabajo cuando un menú está en modo de personalización y el usuario cambia el texto de un elemento de menú.|
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Invalida `CMFCToolBar::OnToolHitTest`).|
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Invalida `CMFCToolBar::PreTranslateMessage`).|
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Lo llama el marco de trabajo cuando un menú está en modo de personalización y el usuario selecciona **restablecer** para una barra de menús.|
|[CMFCMenuBar::SaveState](#savestate)|Guarda el estado del `CMFCMenuBar` objeto en el registro.|
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Establece el menú original en el archivo de recursos.|
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Lo llama el marco de trabajo cuando una ventana secundaria MDI cambia el modo de presentación. Si la ventana secundaria MDI se acaba de maximizar o ya no está maximizada, este método actualiza la barra de menús.|
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Establece la información de clase en tiempo de ejecución que se genera cuando el usuario crea dinámicamente botones de menú.|
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Establece la fuente de todos los menús de la aplicación.|
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Especifica si una barra de menús muestra comandos de menú usados recientemente.|
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Especifica si la barra de menús muestra todos los comandos.|

## <a name="remarks"></a>Comentarios

La `CMFCMenuBar` clase es una barra de menús que implementa la funcionalidad de acoplamiento. Se parece a una barra de herramientas, aunque no se puede cerrar; siempre se muestra.

`CMFCMenuBar`admite la opción de mostrar los objetos de elemento de menú usados recientemente. Si esta opción está habilitada, `CMFCMenuBar` el muestra solo un subconjunto de los comandos disponibles en la primera visualización. A partir de ese momento, los comandos usados recientemente se muestran junto con el subconjunto original de comandos. Además, el usuario siempre puede expandir el menú para ver todos los comandos disponibles. Por lo tanto, cada comando disponible se configura para mostrarse constantemente o para mostrarse solo si se ha seleccionado recientemente.

Para usar un `CMFCMenuBar` objeto, insértelo en el objeto de marco de la ventana principal. Al procesar el `WM_CREATE` mensaje, llame `CMFCMenuBar::Create` a `CMFCMenuBar::CreateEx`o. Independientemente de la función de creación que use, pase un puntero a la ventana de marco principal. A continuación, habilite el acoplamiento llamando a [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Acople este menú mediante una llamada a [CFrameWndEx::D ockpane](../../mfc/reference/cframewndex-class.md#dockpane).

## <a name="example"></a>Ejemplo

En el siguiente ejemplo se muestra cómo usar los distintos métodos en la clase `CMFCMenuBar` . En el ejemplo se muestra cómo establecer el estilo del panel, cómo habilitar el botón personalizar, cómo habilitar un cuadro de ayuda, cómo habilitar sombras para los menús emergentes y cómo actualizar la barra de menús. Este fragmento de código forma parte del [ejemplo de demostración de IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxmenubar. h

##  <a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations

Ajusta las posiciones de los elementos de menú en la barra de menús.

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Comentarios

##  <a name="allowchangetextlabels"></a>  CMFCMenuBar::AllowChangeTextLabels

Determina si las etiquetas de texto se permiten en imágenes en la barra de menús.

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el usuario puede elegir Mostrar etiquetas de texto en imágenes.

### <a name="remarks"></a>Comentarios

##  <a name="allowshowonpanemenu"></a>  CMFCMenuBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="calcfixedlayout"></a>  CMFCMenuBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

de *bStretch*<br/>

de *bHorz*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="calclayout"></a>  CMFCMenuBar::CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>Parámetros

de *dwMode*<br/>

de *nLength*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="calcmaxbuttonheight"></a>  CMFCMenuBar::CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="canbeclosed"></a>  CMFCMenuBar::CanBeClosed

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="canberestored"></a>  CMFCMenuBar::CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="create"></a>  CMFCMenuBar::Create

Crea un control de menú y lo adjunta a un objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Puntero a la ventana primaria del nuevo `CMFCMenuBar` objeto.

*dwStyle*<br/>
de Estilo de la nueva barra de menús.

*nID*<br/>
de IDENTIFICADOR de la ventana secundaria de la barra de menús.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Después de construir un `CMFCMenuBar` objeto, debe llamar a `Create`. Este método crea el `CMFCMenuBar` control y lo adjunta `CMFCMenuBar` al objeto.

Para obtener más información sobre los estilos de barra de herramientas, vea [a cbasepane:: SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).

##  <a name="createex"></a>  CMFCMenuBar::CreateEx

Crea un objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) con los estilos extendidos especificados.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
de Puntero a la ventana primaria del nuevo `CMFCMenuBar` objeto.

*dwCtrlStyle*<br/>
de Estilos adicionales para la nueva barra de menús.

*dwStyle*<br/>
de Estilo principal de la nueva barra de menús.

*rcBorders*<br/>
de Parámetro que especifica los tamaños de los bordes `CMFCMenuBar` del objeto. `CRect`

*nID*<br/>
de IDENTIFICADOR de la ventana secundaria de la barra de menús.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Debe usar esta función en lugar de [CMFCMenuBar:: Create](#create) cuando desee especificar estilos además del estilo de la barra de herramientas. Algunos estilos adicionales usados con frecuencia son TBSTYLE_TRANSPARENT y CBRS_TOP.

Para obtener listas de estilos adicionales, vea [estilos de controles y botones](/windows/win32/Controls/toolbar-control-and-button-styles)de la barra de herramientas, estilos de [control comunes](/windows/win32/Controls/common-control-styles)y [estilos de ventana comunes](/windows/win32/winmsg/window-styles).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo utilizar `CreateEx` el método de `CMFCMenuBar` la clase. Este fragmento de código forma parte del [ejemplo de demostración de IE](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>  CMFCMenuBar::CreateFromMenu

Inicializa un objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) . Este método modela el `CMFCMenuBar` objeto después de un parámetro HMENU.

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
de Identificador de un recurso de menú. `CreateFromMenu`utiliza este recurso como plantilla para `CMFCMenuBar`.

*bDefaultMenu*<br/>
de Un valor booleano que indica si el nuevo menú es el menú predeterminado.

*bForceUpdate*<br/>
de Un valor booleano que indica si este método fuerza una actualización de un menú.

### <a name="remarks"></a>Comentarios

Use este método si desea que un control de menú tenga los mismos elementos de menú que un recurso de menú. Llame a este método después de llamar a [CMFCMenuBar:: Create](#create) o [CMFCMenuBar:: CreateEx](#createex).

##  <a name="enablehelpcombobox"></a>  CMFCMenuBar::EnableHelpCombobox

Habilita un cuadro combinado de **ayuda** que se encuentra en el lado derecho de la barra de menús.

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>Parámetros

*uiID*<br/>
de IDENTIFICADOR de comando para el botón del cuadro combinado de **ayuda** .

*lpszPrompt*<br/>
de Una cadena que contiene el texto que el marco de trabajo muestra en el cuadro combinado si está vacío y no activo. Por ejemplo, "Escriba aquí el texto".

*nComboBoxWidth*<br/>
de Ancho del botón del cuadro combinado en píxeles.

### <a name="remarks"></a>Comentarios

El cuadro combinado de **ayuda** es similar al cuadro combinado de **ayuda** de la barra de menús de Microsoft Word.

Cuando se llama a este método con *uiID* establecido en 0, este método oculta el cuadro combinado. De lo contrario, este método muestra el cuadro combinado automáticamente en el lado derecho de la barra de menús. Después de llamar a este método, llame a [CMFCMenuBar:: GetHelpCombobox](#gethelpcombobox) para obtener un puntero al objeto [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) insertado.

##  <a name="enablemenushadows"></a>  CMFCMenuBar::EnableMenuShadows

Habilita las sombras para los menús emergentes.

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de Un parámetro booleano que indica si se deben habilitar las sombras para los menús emergentes.

### <a name="remarks"></a>Comentarios

El algoritmo que utiliza este método es complejo y puede reducir el rendimiento de la aplicación en sistemas más lentos.

##  <a name="getavailableexpandsize"></a>  CMFCMenuBar::GetAvailableExpandSize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getcolumnwidth"></a>  CMFCMenuBar::GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getdefaultmenu"></a>  CMFCMenuBar::GetDefaultMenu

Recupera un identificador del menú original. El marco de trabajo carga el menú original desde el archivo de recursos.

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador de un recurso de menú.

### <a name="remarks"></a>Comentarios

Si la aplicación personaliza un menú, puede usar este método para recuperar un identificador del menú original.

##  <a name="getdefaultmenuresid"></a>  CMFCMenuBar::GetDefaultMenuResId

Recupera el identificador de recursos para el menú predeterminado.

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del recurso de menú.

### <a name="remarks"></a>Comentarios

El marco de trabajo carga el menú predeterminado `CMFCMenuBar` para el objeto desde el archivo de recursos.

##  <a name="getfloatpopupdirection"></a>  CMFCMenuBar::GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>Parámetros

de *pButton*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getforcedownarrows"></a>  CMFCMenuBar::GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="gethelpcombobox"></a>  CMFCMenuBar::GetHelpCombobox

Devuelve un puntero al cuadro combinado de **ayuda** .

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>Valor devuelto

Puntero al cuadro combinado de **ayuda** . NULL si el cuadro combinado de **ayuda** está oculto o no está habilitado.

### <a name="remarks"></a>Comentarios

El cuadro combinado de **ayuda** se encuentra en el lado derecho de la barra de menús. Llame al método [CMFCMenuBar:: EnableHelpCombobox](#enablehelpcombobox) para habilitar este cuadro combinado.

##  <a name="gethmenu"></a>  CMFCMenuBar::GetHMenu

Recupera el identificador del menú asociado al objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) .

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>  CMFCMenuBar::GetMenuFont

Recupera la fuente del menú actual.

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHorz*<br/>
de Parámetro booleano que especifica si se debe devolver la fuente horizontal o vertical. TRUE indica la fuente horizontal.

### <a name="return-value"></a>Valor devuelto

Un puntero a un parámetro [Cfont (](../../mfc/reference/cfont-class.md) que contiene la fuente de la barra de menús actual.

### <a name="remarks"></a>Comentarios

La fuente devuelta es un parámetro global de la aplicación. Se mantienen dos fuentes globales para todos `CMFCMenuBar` los objetos. Estas fuentes independientes se usan para barras de menús horizontales y verticales.

##  <a name="getmenuitem"></a>  CMFCMenuBar::GetMenuItem

Recupera un objeto [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) en una barra de menús basada en el índice del elemento.

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
de Índice del elemento de menú que se va a devolver.

### <a name="return-value"></a>Valor devuelto

Puntero al `CMFCToolBarButton` objeto que coincide con el índice especificado por *iItem*. NULL si el índice no es válido.

##  <a name="getrowheight"></a>  CMFCMenuBar::GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getsystembutton"></a>  CMFCMenuBar::GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>Parámetros

de *uiBtn*<br/>

de *bByCommand*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getsystembuttonscount"></a>  CMFCMenuBar::GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="getsystemmenu"></a>  CMFCMenuBar::GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="highlightdisableditems"></a>  CMFCMenuBar::HighlightDisabledItems

Controla si el marco resalta los elementos de menú deshabilitados.

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHighlight*<br/>
de Un parámetro booleano que indica si el marco resalta los elementos de menú no disponibles.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco no resalta los elementos de menú no disponibles cuando el usuario coloca el puntero del mouse sobre ellos.

##  <a name="isbuttonextrasizeavailable"></a>  CMFCMenuBar::IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="ishighlightdisableditems"></a>  CMFCMenuBar::IsHighlightDisabledItems

Indica si el marco resalta los elementos de menú no disponibles.

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>Valor devuelto

TRUE si los elementos de menú no disponibles están resaltados; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco no resalta los elementos de menú no disponibles cuando el usuario coloca el puntero del mouse sobre ellos. Use el método [CMFCMenuBar:: HighlightDisabledItems](#highlightdisableditems) para habilitar esta característica.

##  <a name="ismenushadows"></a>  CMFCMenuBar::IsMenuShadows

Indica si el marco de trabajo dibuja sombras para los menús emergentes.

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el marco de trabajo dibuja sombras de menú; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use el método [CMFCMenuBar:: EnableMenuShadows](#enablemenushadows) para habilitar o deshabilitar esta característica.

##  <a name="isrecentlyusedmenus"></a>  CMFCMenuBar::IsRecentlyUsedMenus

Indica si los comandos de menú usados recientemente se muestran en la barra de menús.

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `CMFCMenuBar` si el objeto muestra comandos de menú usados recientemente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Use la función [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus) para controlar si la barra de menús muestra comandos de menú usados recientemente.

##  <a name="isshowallcommands"></a>  CMFCMenuBar::IsShowAllCommands

Indica si los menús muestran todos los comandos.

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero `CMFCMenuBar` si muestra todos los comandos; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un `CMFCMenuBar` objeto puede configurarse para mostrar todos los comandos o mostrar solo un subconjunto de comandos. Para obtener más información sobre esta característica, consulte [clase CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

`IsShowAllCommands`le indicará cómo se configura esta característica para el `CMFCMenuBar` objeto. Para controlar los comandos de menú que se muestran, use los métodos [CMFCMenuBar:: SetShowAllCommands](#setshowallcommands) y [CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus).

##  <a name="isshowallcommandsdelay"></a>  CMFCMenuBar::IsShowAllCommandsDelay

Indica si el objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) muestra todos los comandos después de un breve retraso.

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la barra de menús muestra menús completos tras un breve retraso; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando se configura una barra de menús para mostrar los elementos usados recientemente, la barra de menús muestra el menú completo de una de estas dos maneras:

- Muestra el menú completo después de un retraso programado desde que el usuario mantiene el cursor sobre la flecha situada en la parte inferior del menú.

- Mostrar el menú completo después de que el usuario haga clic en la flecha situada en la parte inferior del menú.

De forma predeterminada, `CMFCMenuBar` todos los objetos usan la opción para mostrar el menú completo después de un breve retraso. Esta opción no se puede cambiar mediante programación en `CMFCMenuBar` la clase. Sin embargo, un usuario puede cambiar el comportamiento durante la personalización de la barra de herramientas mediante el cuadro de diálogo **personalizar** .

##  <a name="loadstate"></a>  CMFCMenuBar::LoadState

Carga el estado de la barra de menús desde el registro de Windows.

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Cadena que contiene la ruta de acceso de una clave del registro de Windows.

*nIndex*<br/>
de IDENTIFICADOR de control de la barra de menús.

*uiID*<br/>
de Valor reservado.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Use el método [CMFCMenuBar:: SaveState](#savestate) para guardar el estado de la barra de menús en el registro. La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.

En la mayoría de los casos, la `LoadState`aplicación no llama a. El marco llama a este método cuando inicializa el área de trabajo.

##  <a name="onchangehot"></a>  CMFCMenuBar::OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>Parámetros

de *iHot*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="ondefaultmenuloaded"></a>  CMFCMenuBar::OnDefaultMenuLoaded

El marco de trabajo llama a este método cuando carga el recurso de menú desde el archivo de recursos.

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>Parámetros

*hMenu*<br/>
de Identificador del menú asociado al `CMFCMenuBar` objeto.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función no hace nada. Invalide esta función para ejecutar código personalizado después de que el marco de trabajo cargue un recurso de menú desde el archivo de recursos.

##  <a name="onsendcommand"></a>  CMFCMenuBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

de *pButton*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="onsetdefaultbuttontext"></a>  CMFCMenuBar::OnSetDefaultButtonText

El marco de trabajo llama a este método cuando el usuario cambia el texto de un elemento en la barra de menús.

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
de Un puntero al objeto [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) que el usuario desea personalizar.

### <a name="return-value"></a>Valor devuelto

TRUE si el marco de trabajo aplica los cambios de usuario a la barra de menús; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de este método cambia el texto del botón por el texto que proporciona el usuario.

##  <a name="ontoolhittest"></a>  CMFCMenuBar::OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>Parámetros

de *punto* de<br/>

de *pTI*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="pretranslatemessage"></a>  CMFCMenuBar::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

de *pMsg*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="restoreoriginalstate"></a>  CMFCMenuBar::RestoreOriginalstate

Lo llama el marco de trabajo cuando el usuario selecciona **restablecer** en el cuadro de diálogo **personalizar** .

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el método es correcto; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Se llama a este método cuando el usuario selecciona **restablecer** en el menú de personalización. También puede llamar a este método manualmente para restablecer mediante programación el estado de la barra de menús. Este método carga el estado original del archivo de recursos.

Invalide este método si desea realizar cualquier procesamiento cuando el usuario seleccione la opción **restablecer** .

##  <a name="savestate"></a>  CMFCMenuBar::SaveState

Guarda el estado del objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) en el registro de Windows.

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>Parámetros

*lpszProfileName*<br/>
de Cadena que contiene la ruta de acceso de una clave del registro de Windows.

*nIndex*<br/>
de IDENTIFICADOR de control de la barra de menús.

*uiID*<br/>
de Valor reservado.

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Normalmente, la aplicación no llama a `SaveState`. El marco llama a este método cuando se serializa el área de trabajo. Para obtener más información, vea [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate).

La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.

##  <a name="setdefaultmenuresid"></a>  CMFCMenuBar::SetDefaultMenuResId

Establece el menú predeterminado para un objeto [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) basado en el identificador de recurso.

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>Parámetros

*uiResId*<br/>
de El identificador de recurso para el nuevo menú predeterminado.

### <a name="remarks"></a>Comentarios

El método [CMFCMenuBar:: RestoreOriginalstate](#restoreoriginalstate) restaura el menú predeterminado del archivo de recursos.

Use el método [CMFCMenuBar:: GetDefaultMenuResId](#getdefaultmenuresid) para recuperar el menú predeterminado sin restaurarlo.

##  <a name="setforcedownarrows"></a>  CMFCMenuBar::SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>Parámetros

de *bValue*<br/>

### <a name="remarks"></a>Comentarios

##  <a name="setmaximizemode"></a>  CMFCMenuBar::SetMaximizeMode

El marco de trabajo llama a este método cuando un MDI cambia el modo de presentación y la barra de menús debe actualizarse.

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>Parámetros

*bMax*<br/>
de Valor booleano que especifica el modo. Vea la sección Comentarios para obtener más información.

*pWnd*<br/>
de Puntero a la ventana secundaria MDI que está cambiando.

*bRecalcLayout*<br/>
de Un valor booleano que especifica si el diseño de la barra de menús se debe volver A calcular inmediatamente.

### <a name="remarks"></a>Comentarios

Cuando una ventana secundaria MDI está maximizada, una barra de menús asociada a la ventana marco principal MDI muestra el menú sistema y los botones **minimizar**, **maximizar** y **cerrar** . Si *Bmax* es true y *PWND* no es null, la ventana secundaria MDI está maximizada y la barra de menús debe incorporar los controles adicionales. De lo contrario, la barra de menús vuelve a su estado normal.

##  <a name="setmenubuttonrtc"></a>  CMFCMenuBar::SetMenuButtonRTC

Establece la información de clase en tiempo de ejecución que usa el marco cuando el usuario crea botones de menú.

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>Parámetros

*pMenuButtonRTC*<br/>
de La información de [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) para una clase derivada de la [clase cmfcmenubutton (](../../mfc/reference/cmfcmenubutton-class.md).

### <a name="remarks"></a>Comentarios

Cuando un usuario agrega nuevos botones a la barra de menús, el marco de trabajo crea los botones dinámicamente. De forma predeterminada, crea `CMFCMenuButton` objetos. Invalide este método para cambiar el tipo de objetos de botón que crea el marco de trabajo.

##  <a name="setmenufont"></a>  CMFCMenuBar::SetMenuFont

Establece la fuente para todas las barras de menús de la aplicación.

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
de Puntero a una estructura [LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta) que define la fuente que se va a establecer.

*bHorz*<br/>
de TRUE si desea que se use el parámetro *lpLogFont* para la fuente vertical, false si desea que se use para la fuente horizontal.

### <a name="return-value"></a>Valor devuelto

TRUE si el método se realizó correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Se utilizan dos fuentes para todos `CMFCMenuBar` los objetos. Estas fuentes independientes se usan para barras de menús horizontales y verticales.

Los valores de fuente son variables globales y afectan `CMFCMenuBar` a todos los objetos.

##  <a name="setrecentlyusedmenus"></a>  CMFCMenuBar::SetRecentlyUsedMenus

Controla si una barra de menús muestra comandos de menú usados recientemente.

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>Parámetros

*bOn*<br/>
de Un valor booleano que controla si se muestran los comandos de menú usados recientemente.

##  <a name="setshowallcommands"></a>  CMFCMenuBar::SetShowAllCommands

Controla si un menú muestra todos los comandos disponibles.

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>Parámetros

*bShowAllCommands*<br/>
de Un parámetro booleano que especifica si el menú emergente muestra todos los comandos de menú.

### <a name="remarks"></a>Comentarios

Si un menú no muestra todos los comandos de menú, oculta los comandos que rara vez se usan. Para obtener más información sobre cómo mostrar los comandos de menú, vea [clase CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
