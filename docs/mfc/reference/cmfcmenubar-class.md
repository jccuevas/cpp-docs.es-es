---
title: CMFCMenuBar (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4d8961cc929196c21838fd21132146deddabcc1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540900"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar (clase)
Una barra de menús que implementa el acoplamiento.  
 Para obtener más información, vea el código fuente ubicado en el **VC\\atlmfc\\src\\mfc** carpeta de la instalación de Visual Studio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Invalida `CMFCToolBar::AdjustLocations`).|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Especifica si se pueden mostrar etiquetas de texto en imágenes en los botones de barra de herramientas. (Invalida [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Calcula el tamaño horizontal de la barra de herramientas. (Invalida [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|(Invalida `CMFCToolBar::CalcLayout`).|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcula el alto máximo de botones en la barra de herramientas. (Invalida [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Especifica si un usuario puede cerrar la barra de herramientas. (Invalida [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización. (Invalida [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCMenuBar::Create](#create)|Crea un control de menú y lo adjunta a un `CMFCMenuBar` objeto.|  
|[CMFCMenuBar::CreateEx](#createex)|Crea un `CMFCMenuBar` objeto con otras opciones de estilo.|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicializa un `CMFCMenuBar` objeto. Acepta un parámetro HMENU que actúa como una plantilla para un rellenado `CMFCMenuBar`.|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Permite un **ayuda** cuadro combinado que se encuentra en el lado derecho de la barra de menús.|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Especifica si se mostrarán las sombras en los menús emergentes.|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Invalida [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Devuelve el ancho de los botones de barra de herramientas. (Invalida [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Devuelve un identificador al menú original del archivo de recursos.|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Devuelve el identificador de recurso para el menú original del archivo de recursos.|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Devuelve un puntero a la **ayuda** cuadro combinado.|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|Devuelve el identificador del menú que se adjunta a la `CMFCMenuBar` objeto.|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Devuelve la fuente actual global para los objetos de menú.|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Devuelve el botón de barra de herramientas asociado con el índice del elemento proporcionado.|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de barra de herramientas. (Invalida [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Indica si se resaltan los elementos de menú deshabilitado.|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que se han ampliado a los bordes. (Invalida [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Indica si se resaltan los elementos deshabilitados.|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Indica si las sombras se dibujan en los menús emergentes.|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Indica si los comandos de menú usados recientemente aparecen en la barra de menús.|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Indica si los menús emergentes mostrar todos los comandos.|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Indica si los menús Mostrar todos los comandos tras un breve retraso.|  
|[CMFCMenuBar::LoadState](#loadstate)|Carga el estado de la `CMFCMenuBar` objeto desde el registro.|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Lo llama el marco cuando un usuario selecciona un botón en la barra de herramientas. (Invalida [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Lo llama el marco cuando una ventana de marco carga el menú predeterminado del archivo de recursos.|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Lo llama el marco cuando un menú está en modo de personalización y el usuario cambia el texto de un elemento de menú.|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Invalida `CMFCToolBar::OnToolHitTest`).|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Invalida `CMFCToolBar::PreTranslateMessage`).|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Lo llama el marco cuando un menú está en modo de personalización y el usuario selecciona **restablecer** para una barra de menús.|  
|[CMFCMenuBar::SaveState](#savestate)|Guarda el estado de la `CMFCMenuBar` objeto en el registro.|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Establece el menú original del archivo de recursos.|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Lo llama el marco cuando una ventana secundaria MDI cambia su modo de presentación. Si la ventana secundaria MDI recién está maximizada o ya no está maximizada, este método actualiza la barra de menús.|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Establece la información de clase en tiempo de ejecución que se genera cuando el usuario crea dinámicamente los botones de menú.|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Establece la fuente para todos los menús de la aplicación.|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Especifica si una barra de menús muestra los comandos de menú usados recientemente.|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Especifica si la barra de menús muestra todos los comandos.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCMenuBar` clase es una barra de menús que implementa la funcionalidad de acoplamiento. Se parece a una barra de herramientas, aunque no se puede cerrar: siempre se muestra.  
  
 `CMFCMenuBar` es compatible con la opción de mostrar los objetos de elemento de menú usados recientemente. Si esta opción está habilitada, el `CMFCMenuBar` muestra solo un subconjunto de los comandos disponibles en la primera vista. A partir de entonces, los comandos usados recientemente se muestran junto con el subconjunto de comandos original. Además, el usuario siempre puede expandir el menú para ver todos los comandos disponibles. Por lo tanto, cada comando disponible está configurado para mostrar constantemente, o para mostrar solo si se ha seleccionado recientemente.  
  
 Para usar un `CMFCMenuBar` de objetos, insertarlo en el objeto de marco de ventana principal. Al procesar la `WM_CREATE` de mensajes, llame a `CMFCMenuBar::Create` o `CMFCMenuBar::CreateEx`. Independientemente de que crea la función use, pase un puntero a la ventana de marco principal. A continuación, habilite el acoplamiento mediante una llamada a [cframewndex:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Acoplar este menú llamando [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCMenuBar` clase. El ejemplo muestra cómo establecer el estilo del panel, habilitar el botón Personalizar, habilite un cuadro de ayuda, habilitar las sombras en los menús emergentes y actualizar la barra de menús. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
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
 **Encabezado:** afxmenubar.h  
  
##  <a name="adjustlocations"></a>  CMFCMenuBar::AdjustLocations  
 Ajusta las posiciones de los elementos de menú en la barra de menús.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="allowchangetextlabels"></a>  CMFCMenuBar::AllowChangeTextLabels  
 Determina si se permiten las etiquetas de texto en imágenes en la barra de menús.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el usuario puede elegir mostrar etiquetas de texto en imágenes.  
  
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
 [in] *bStretch*  
 [in] *bHorz*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="calclayout"></a>  CMFCMenuBar::CalcLayout  

  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *dwMode*  
 [in] *nLength*  
  
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
 Crea un control de menú y lo adjunta a un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pParentWnd*  
 Puntero a la ventana primaria para el nuevo `CMFCMenuBar` objeto.  
  
 [in] *dwStyle*  
 El estilo de la nueva barra de menús.  
  
 [in] *nID*  
 El identificador de la ventana secundaria de la barra de menús.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si es correcto; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Después de crear un `CMFCMenuBar` objeto, debe llamar a `Create`. Este método crea el `CMFCMenuBar` controlar y lo adjunta a la `CMFCMenuBar` objeto.  
  
 Para obtener más información sobre los estilos de barra de herramientas, consulte [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).  
  
##  <a name="createex"></a>  CMFCMenuBar::CreateEx  
 Crea un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto con los estilos extendidos especificados.  
  
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
 [in] *pParentWnd*  
 Puntero a la ventana primaria de la nueva `CMFCMenuBar` objeto.  
  
 [in] *dwCtrlStyle*  
 Estilos adicionales para la nueva barra de menús.  
  
 [in] *dwStyle*  
 Estilo de la nueva barra de menús principal.  
  
 [in] *rcBorders*  
 Un `CRect` parámetro que especifica los tamaños de los bordes de la `CMFCMenuBar` objeto.  
  
 [in] *nID*  
 El identificador de la ventana secundaria de la barra de menús.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe usar esta función en lugar de [CMFCMenuBar::Create](#create) cuando desee especificar estilos además el estilo de barra de herramientas. Algunos estilos adicionales usados con frecuencia son TBSTYLE_TRANSPARENT y CBRS_TOP.  
  
 Para obtener listas de estilos adicionales, vea [Control de barra de herramientas y los estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439), [estilos de control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498), y [estilos de ventana comunes](http://msdn.microsoft.com/library/windows/desktop/ms632600).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el `CreateEx` método de la `CMFCMenuBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="createfrommenu"></a>  CMFCMenuBar::CreateFromMenu  
 Inicializa un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto. Los modelos de este método la `CMFCMenuBar` objeto después de un parámetro HMENU.  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hMenu*  
 Identificador de un recurso de menú. `CreateFromMenu` este recurso se utiliza como plantilla para el `CMFCMenuBar`.  
  
 [in] *bDefaultMenu*  
 Un valor booleano que indica si el nuevo menú es el predeterminado.  
  
 [in] *bForceUpdate*  
 Un valor booleano que indica si este método fuerza una actualización de menú.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método si desea que los mismos elementos de menú como un recurso de menú en un control de menú. Llame a este método después de llamar a cualquiera [CMFCMenuBar::Create](#create) o [CMFCMenuBar::CreateEx](#createex).  
  
##  <a name="enablehelpcombobox"></a>  CMFCMenuBar::EnableHelpCombobox  
 Permite un **ayuda** cuadro combinado que se encuentra en el lado derecho de la barra de menús.  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *uiID*  
 El identificador de comando para el botón de la **ayuda** cuadro combinado.  
  
 [in] *lpszPrompt*  
 Cadena que contiene el texto que muestra el marco de trabajo en el cuadro combinado si está vacío y no está activo. Por ejemplo, "Escriba aquí el texto".  
  
 [in] *nComboBoxWidth*  
 El ancho del botón del cuadro combinado en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El **ayuda** cuadro combinado es similar a la **ayuda** cuadro combinado en la barra de menús de Microsoft Word.  
  
 Cuando se llama a este método con *uiID* establece en 0, este método oculta el cuadro combinado. En caso contrario, este método muestra automáticamente el cuadro combinado en el lado derecho de la barra de menús. Después de llamar a este método, llame a [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) para obtener un puntero a la insertado [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objeto.  
  
##  <a name="enablemenushadows"></a>  CMFCMenuBar::EnableMenuShadows  
 Habilita las sombras en los menús emergentes.  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHabilitar el*  
 Un parámetro booleano que indica si se deben habilitar las sombras en los menús emergentes.  
  
### <a name="remarks"></a>Comentarios  
 El algoritmo que utiliza este método es complejo y puede disminuir el rendimiento de la aplicación en sistemas más lentos.  
  
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
 Recupera un identificador del menú original. El marco de trabajo carga el menú original del archivo de recursos.  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de un recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación personaliza un menú, puede usar este método para recuperar un identificador del menú original.  
  
##  <a name="getdefaultmenuresid"></a>  CMFCMenuBar::GetDefaultMenuResId  
 Recupera el identificador de recurso para el menú predeterminado.  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo carga el menú de forma predeterminada el `CMFCMenuBar` objeto desde el archivo de recursos.  
  
##  <a name="getfloatpopupdirection"></a>  CMFCMenuBar::GetFloatPopupDirection  

  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="getforcedownarrows"></a>  CMFCMenuBar::GetForceDownArrows  

  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="gethelpcombobox"></a>  CMFCMenuBar::GetHelpCombobox  
 Devuelve un puntero a la **ayuda** cuadro combinado.  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la **ayuda** cuadro combinado. NULL si el **ayuda** cuadro combinado está oculto o no habilitado.  
  
### <a name="remarks"></a>Comentarios  
 El **ayuda** cuadro combinado se encuentra en el lado derecho de la barra de menús. Llame al método [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) para habilitar este cuadro combinado.  
  
##  <a name="gethmenu"></a>  CMFCMenuBar::GetHMenu  
 Recupera el identificador del menú asociado a la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto.  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="getmenufont"></a>  CMFCMenuBar::GetMenuFont  
 Recupera la fuente del menú actual.  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHorz*  
 Un parámetro booleano que especifica si se debe devolver la fuente horizontal o vertical. TRUE indica que la fuente horizontal.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CFont](../../mfc/reference/cfont-class.md) parámetro que contiene la fuente de barra de menú actual.  
  
### <a name="remarks"></a>Comentarios  
 La fuente devuelta es un parámetro global para la aplicación. Se mantienen dos fuentes globales para todos los `CMFCMenuBar` objetos. Estas fuentes independientes se usan para las barras de menús horizontal y vertical.  
  
##  <a name="getmenuitem"></a>  CMFCMenuBar::GetMenuItem  
 Recupera un [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objeto en una barra de menús según el índice del elemento.  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iItem*  
 El índice del elemento de menú para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCToolBarButton` objeto que coincide con el índice especificado por *iItem*. Es NULL si el índice no es válido.  
  
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
 [in] *uiBtn*  
 [in] *bByCommand*  
  
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
 Controla si el marco de trabajo resalta los elementos de menú deshabilitado.  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bHighlight*  
 Un parámetro booleano que indica si el marco de trabajo resalta los elementos de menú no está disponible.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no resaltar los elementos de menú no está disponible cuando el usuario coloca el puntero del mouse sobre ellos.  
  
##  <a name="isbuttonextrasizeavailable"></a>  CMFCMenuBar::IsButtonExtraSizeAvailable  

  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ishighlightdisableditems"></a>  CMFCMenuBar::IsHighlightDisabledItems  
 Indica si el marco de trabajo resalta los elementos de menú no está disponible.  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se resaltan los elementos de menú no está disponible; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no resaltar los elementos de menú no está disponible cuando el usuario coloca el puntero del mouse sobre ellos. Use la [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) método para habilitar esta característica.  
  
##  <a name="ismenushadows"></a>  CMFCMenuBar::IsMenuShadows  
 Indica si el marco de trabajo dibuja sombras en los menús emergentes.  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el marco de trabajo dibuja sombras de menú; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) método para habilitar o deshabilitar esta característica.  
  
##  <a name="isrecentlyusedmenus"></a>  CMFCMenuBar::IsRecentlyUsedMenus  
 Indica si los comandos de menú usados recientemente aparecen en la barra de menús.  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CMFCMenuBar` objeto usado recientemente se muestra los comandos de menú; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Use la función [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) para controlar si se muestra la barra de menús recientemente usa comandos de menú.  
  
##  <a name="isshowallcommands"></a>  CMFCMenuBar::IsShowAllCommands  
 Indica si los menús Mostrar todos los comandos.  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CMFCMenuBar` muestra todos los comandos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCMenuBar` objeto puede configurarse para mostrar todos los comandos o mostrar solo un subconjunto de comandos. Para obtener más información sobre esta característica, consulte [CMFCMenuBar (clase)](../../mfc/reference/cmfcmenubar-class.md).  
  
 `IsShowAllCommands` le indicará cómo esta característica se configura para el `CMFCMenuBar` objeto. Para controlar qué comandos de menú se muestran, utilice los métodos [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) y [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).  
  
##  <a name="isshowallcommandsdelay"></a>  CMFCMenuBar::IsShowAllCommandsDelay  
 Indica si el [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto muestra todos los comandos tras un breve retraso.  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la barra de menús muestra los menús completos transcurridos unos segundos; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se configura una barra de menús para mostrar elementos utilizados recientemente, la barra de menú muestra el menú completo en uno de dos maneras:  
  
-   Mostrar el menú completo tras un retraso programado desde cuando el usuario desplace el cursor sobre la flecha en la parte inferior del menú.  
  
-   Mostrar el menú completo después de que el usuario hace clic en la flecha situada en la parte inferior del menú.  
  
 De forma predeterminada, todos los `CMFCMenuBar` objetos utilizan la opción para mostrar el menú completo tras un breve retraso. Esta opción no se puede cambiar mediante programación en el `CMFCMenuBar` clase. Sin embargo, un usuario puede cambiar el comportamiento durante la personalización de la barra de herramientas mediante el **personalizar** cuadro de diálogo...  
  
##  <a name="loadstate"></a>  CMFCMenuBar::LoadState  
 Carga el estado de la barra de menús del registro de Windows.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszProfileName*  
 Una cadena que contiene la ruta de acceso de una clave del registro de Windows.  
  
 [in] *nIndex*  
 Identificador del control de la barra de menús.  
  
 [in] *uiID*  
 Un valor reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCMenuBar::SaveState](#savestate) método para guardar el estado de la barra de menús en el registro. La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.  
  
 En la mayoría de los casos la aplicación no llama a `LoadState`. El marco llama a este método cuando inicializa el área de trabajo.  
  
##  <a name="onchangehot"></a>  CMFCMenuBar::OnChangeHot  

  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *iHot*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="ondefaultmenuloaded"></a>  CMFCMenuBar::OnDefaultMenuLoaded  
 El marco llama a este método cuando se carga el recurso de menú desde el archivo de recursos.  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *hMenu*  
 El identificador del menú asociado a la `CMFCMenuBar` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplace esta función para ejecutar código personalizado después de que el marco de trabajo carga un recurso de menú desde el archivo de recursos.  
  
##  <a name="onsendcommand"></a>  CMFCMenuBar::OnSendCommand  

  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onsetdefaultbuttontext"></a>  CMFCMenuBar::OnSetDefaultButtonText  
 El marco llama a este método cuando el usuario cambia el texto de un elemento en la barra de menús.  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pButton*  
 Un puntero a la [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objeto que el usuario desea personalizar.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se aplica el marco de trabajo que el usuario cambia a la barra de menús; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada para este método cambia el texto del botón en el texto que proporciona el usuario.  
  
##  <a name="ontoolhittest"></a>  CMFCMenuBar::OnToolHitTest  

  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *punto*  
 [in] *pTI*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="pretranslatemessage"></a>  CMFCMenuBar::PreTranslateMessage  

  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMsg*  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="restoreoriginalstate"></a>  CMFCMenuBar::RestoreOriginalstate  
 Lo llama el marco cuando el usuario selecciona **restablecer** desde el **personalizar** cuadro de diálogo.  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama cuando el usuario selecciona **restablecer** desde el menú de personalización. Asimismo puede llamar a este método para restablecer mediante programación el estado de la barra de menús. Este método carga el estado original del archivo de recursos.  
  
 Invalide este método si desea realizar cualquier procesamiento cuando el usuario selecciona el **restablecer** opción.  
  
##  <a name="savestate"></a>  CMFCMenuBar::SaveState  
 Guarda el estado de la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto en el registro de Windows.  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpszProfileName*  
 Una cadena que contiene la ruta de acceso de una clave del registro de Windows.  
  
 [in] *nIndex*  
 Identificador del control de la barra de menús.  
  
 [in] *uiID*  
 Un valor reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, la aplicación no llama a `SaveState`. El marco llama a este método cuando se serializa el área de trabajo. Para obtener más información, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
 La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.  
  
##  <a name="setdefaultmenuresid"></a>  CMFCMenuBar::SetDefaultMenuResId  
 Establece el menú de forma predeterminada para un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto según el identificador de recurso.  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *uiResId*  
 El identificador de recurso para el nuevo menú de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) método restaura el menú predeterminado del archivo de recursos.  
  
 Use la [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) método para recuperar el menú predeterminado sin restaurarlo.  
  
##  <a name="setforcedownarrows"></a>  CMFCMenuBar::SetForceDownArrows  

  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bValue*  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setmaximizemode"></a>  CMFCMenuBar::SetMaximizeMode  
 El marco llama a este método cuando una MDI cambia su modo de presentación y debe actualizarse la barra de menús.  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bmáx*  
 Un valor booleano que especifica el modo. Vea la sección Comentarios para obtener más información.  
  
 [in] *conquistado*  
 Un puntero a la ventana secundaria MDI que se va a cambiar.  
  
 [in] *bRecalcLayout*  
 Un valor booleano que especifica si el diseño de la barra de menús se debe recalcular inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria MDI, una barra de menús que se adjunta a la ventana de marco principal MDI muestra el menú del sistema y la **minimizar**, **maximizar** y **cerrar** botones. Si *bmáx* es TRUE y *conquistado* no es NULL, se maximiza la ventana secundaria MDI y la barra de menús debe incorporar los controles adicionales. En caso contrario, la barra de menús se vuelve a su estado normal.  
  
##  <a name="setmenubuttonrtc"></a>  CMFCMenuBar::SetMenuButtonRTC  
 Establece la información de clase en tiempo de ejecución que usa el marco cuando el usuario crea botones de menú.  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *pMenuButtonRTC*  
 El [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) información para una clase derivada de la [CMFCMenuButton (clase)](../../mfc/reference/cmfcmenubutton-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario agrega nuevos botones a la barra de menús, el marco de trabajo crea los botones de forma dinámica. De forma predeterminada, crea `CMFCMenuButton` objetos. Invalide este método para cambiar el tipo de objetos de botón que crea el marco de trabajo.  
  
##  <a name="setmenufont"></a>  CMFCMenuBar::SetMenuFont  
 Establece la fuente para todas las barras de menús en la aplicación.  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *lpLogFont*  
 Un puntero a un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327) estructura que define la fuente para establecer.  
  
 [in] *bHorz*  
 TRUE si desea que el *lpLogFont* parámetro que se usa para la fuente vertical, FALSE si desea que se usará para la fuente horizontal.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el método se realizó correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Se usan dos fuentes para todos los `CMFCMenuBar` objetos. Estas fuentes independientes se usan para las barras de menús horizontal y vertical.  
  
 La configuración de fuente son variables globales y afectarán a todas `CMFCMenuBar` objetos.  
  
##  <a name="setrecentlyusedmenus"></a>  CMFCMenuBar::SetRecentlyUsedMenus  
 Determina si se muestra una barra de menús recientemente comandos de menú que usa los controles.  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *Ben*  
 Un valor booleano que controla si se muestran los comandos de menú usados recientemente.  
  
##  <a name="setshowallcommands"></a>  CMFCMenuBar::SetShowAllCommands  
 Controla si un menú muestra todos los comandos disponibles.  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] *bShowAllCommands*  
 Un parámetro booleano que especifica si el menú emergente muestra todos los comandos de menú.  
  
### <a name="remarks"></a>Comentarios  
 Si un menú no muestra todos los comandos de menú, oculta los comandos que se usan con poca frecuencia. Para obtener más información acerca de cómo mostrar comandos de menú, vea [CMFCMenuBar (clase)](../../mfc/reference/cmfcmenubar-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar (clase)](../../mfc/reference/cmfctoolbar-class.md)
