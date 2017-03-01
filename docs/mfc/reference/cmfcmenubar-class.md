---
title: Clase CMFCMenuBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCMenuBar
dev_langs:
- C++
helpviewer_keywords:
- CMFCMenuBar class
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
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
ms.openlocfilehash: ab2896f5ebab0df894f70e5ddb85bae3a5e1d5af
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcmenubar-class"></a>Clase CMFCMenuBar
Una barra de menús que implementa el acoplamiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCMenuBar::AdjustLocations](#adjustlocations)|(Invalida `CMFCToolBar::AdjustLocations`).|  
|[CMFCMenuBar::AllowChangeTextLabels](#allowchangetextlabels)|Especifica si se pueden mostrar etiquetas de texto en imágenes en los botones de barra de herramientas. (Invalida [CMFCToolBar::AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels).)|  
|[CMFCMenuBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Invalida `CPane::AllowShowOnPaneMenu`).|  
|[CMFCMenuBar::CalcFixedLayout](#calcfixedlayout)|Calcula el tamaño horizontal de la barra de herramientas. (Invalida [CMFCToolBar::CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout).)|  
|[CMFCMenuBar::CalcLayout](#calclayout)|(Invalida `CMFCToolBar::CalcLayout`).|  
|[CMFCMenuBar::CalcMaxButtonHeight](#calcmaxbuttonheight)|Calcula el alto máximo de botones de la barra de herramientas. (Invalida [CMFCToolBar::CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight).)|  
|[CMFCMenuBar::CanBeClosed](#canbeclosed)|Especifica si un usuario puede cerrar la barra de herramientas. (Invalida [CMFCToolBar::CanBeClosed](../../mfc/reference/cmfctoolbar-class.md#canbeclosed).)|  
|[CMFCMenuBar::CanBeRestored](#canberestored)|Determina si el sistema puede restaurar una barra de herramientas a su estado original después de la personalización. (Invalida [CMFCToolBar::CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored).)|  
|[CMFCMenuBar::Create](#create)|Crea un control de menú y lo adjunta a un `CMFCMenuBar` objeto.|  
|[CMFCMenuBar::CreateEx](#createex)|Crea un `CMFCMenuBar` objeto con otras opciones de estilo.|  
|[CMFCMenuBar::CreateFromMenu](#createfrommenu)|Inicializa un `CMFCMenuBar` objeto. Acepta una `HMENU` parámetro que actúa como una plantilla para un rellenado `CMFCMenuBar`.|  
|[CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox)|Permite un **ayuda** cuadro combinado que se encuentra en el lado derecho de la barra de menús.|  
|[CMFCMenuBar::EnableMenuShadows](#enablemenushadows)|Especifica si se muestra sombras en los menús emergentes.|  
|[CMFCMenuBar::GetAvailableExpandSize](#getavailableexpandsize)|(Invalida [CPane::GetAvailableExpandSize](../../mfc/reference/cpane-class.md#getavailableexpandsize).)|  
|[CMFCMenuBar::GetColumnWidth](#getcolumnwidth)|Devuelve el ancho de los botones de barra de herramientas. (Invalida [CMFCToolBar::GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth).)|  
|[CMFCMenuBar::GetDefaultMenu](#getdefaultmenu)|Devuelve un identificador para el menú original del archivo de recursos.|  
|[CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid)|Devuelve el identificador de recurso para el menú original del archivo de recursos.|  
|[CMFCMenuBar::GetFloatPopupDirection](#getfloatpopupdirection)||  
|[CMFCMenuBar::GetForceDownArrows](#getforcedownarrows)||  
|[CMFCMenuBar::GetHelpCombobox](#gethelpcombobox)|Devuelve un puntero a la **ayuda** cuadro combinado.|  
|[CMFCMenuBar::GetHMenu](#gethmenu)|Devuelve el identificador del menú que se adjunta a la `CMFCMenuBar` objeto.|  
|[CMFCMenuBar::GetMenuFont](#getmenufont)|Devuelve la fuente actual global para los objetos de menú.|  
|[CMFCMenuBar::GetMenuItem](#getmenuitem)|Devuelve el botón de barra de herramientas asociado al índice del elemento proporcionado.|  
|[CMFCMenuBar::GetRowHeight](#getrowheight)|Devuelve el alto de los botones de barra de herramientas. (Invalida [CMFCToolBar::GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight).)|  
|[CMFCMenuBar::GetSystemButton](#getsystembutton)||  
|[CMFCMenuBar::GetSystemButtonsCount](#getsystembuttonscount)||  
|[CMFCMenuBar::GetSystemMenu](#getsystemmenu)||  
|[CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems)|Indica si se resaltan los elementos de menú desactivados.|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|Determina si la barra de herramientas puede mostrar botones que se han extendido bordes. (Invalida [CMFCToolBar::IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable).)|  
|[CMFCMenuBar::IsHighlightDisabledItems](#ishighlightdisableditems)|Indica si se resaltan los elementos deshabilitados.|  
|[CMFCMenuBar::IsMenuShadows](#ismenushadows)|Indica si se dibujan las sombras de los menús emergentes.|  
|[CMFCMenuBar::IsRecentlyUsedMenus](#isrecentlyusedmenus)|Indica si los comandos de menú utilizados recientemente se muestran en la barra de menús.|  
|[CMFCMenuBar::IsShowAllCommands](#isshowallcommands)|Indica si los menús emergentes mostrar todos los comandos.|  
|[CMFCMenuBar::IsShowAllCommandsDelay](#isshowallcommandsdelay)|Indica si los menús mostrarán todos los comandos después de un breve retraso.|  
|[CMFCMenuBar::LoadState](#loadstate)|Carga el estado de la `CMFCMenuBar` objeto desde el registro.|  
|[CMFCMenuBar::OnChangeHot](#onchangehot)|Llamado por el marco cuando un usuario selecciona un botón en la barra de herramientas. (Invalida [CMFCToolBar::OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot).)|  
|[CMFCMenuBar::OnDefaultMenuLoaded](#ondefaultmenuloaded)|Llamado por el marco cuando una ventana de marco, carga el menú predeterminado del archivo de recursos.|  
|[CMFCMenuBar::OnSendCommand](#onsendcommand)|(Invalida `CMFCToolBar::OnSendCommand`).|  
|[CMFCMenuBar::OnSetDefaultButtonText](#onsetdefaultbuttontext)|Llamado por el marco cuando un menú está en modo de personalización y el usuario cambia el texto de un elemento de menú.|  
|[CMFCMenuBar::OnToolHitTest](#ontoolhittest)|(Invalida `CMFCToolBar::OnToolHitTest`).|  
|[CMFCMenuBar::PreTranslateMessage](#pretranslatemessage)|(Invalida `CMFCToolBar::PreTranslateMessage`).|  
|[CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate)|Llamado por el marco cuando un menú está en modo de personalización y el usuario selecciona **restablecer** para una barra de menús.|  
|[CMFCMenuBar::SaveState](#savestate)|Guarda el estado de la `CMFCMenuBar` objeto en el registro.|  
|[CMFCMenuBar::SetDefaultMenuResId](#setdefaultmenuresid)|Establece el menú original del archivo de recursos.|  
|[CMFCMenuBar::SetForceDownArrows](#setforcedownarrows)||  
|[CMFCMenuBar::SetMaximizeMode](#setmaximizemode)|Llamado por el marco de trabajo cuando una ventana secundaria MDI cambia su modo de presentación. Si la ventana secundaria MDI recién está maximizada o ya no está maximizada, este método actualiza la barra de menús.|  
|[CMFCMenuBar::SetMenuButtonRTC](#setmenubuttonrtc)|Establece la información de clase en tiempo de ejecución que se genera cuando el usuario crea dinámicamente botones de menú.|  
|[CMFCMenuBar::SetMenuFont](#setmenufont)|Establece la fuente para todos los menús de la aplicación.|  
|[CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus)|Especifica si una barra de menús muestra los comandos de menú utilizados recientemente.|  
|[CMFCMenuBar::SetShowAllCommands](#setshowallcommands)|Especifica si la barra de menús muestra todos los comandos.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCMenuBar` clase es una barra de menús que implementa la funcionalidad de acoplamiento. Se parece a una barra de herramientas, aunque no se puede cerrar: siempre se muestra.  
  
 `CMFCMenuBar`admite la opción de mostrar los objetos de elemento de menú utilizados recientemente. Si esta opción está habilitada, el `CMFCMenuBar` muestra sólo un subconjunto de los comandos disponibles verlos por primera vez. Posteriormente, los comandos usados recientemente se muestran junto con el subconjunto de comandos original. Además, el usuario siempre puede expandir el menú para ver todos los comandos disponibles. Por lo tanto, cada comando disponible está configurado para mostrar constantemente, o para mostrar solo si se ha seleccionado recientemente.  
  
 Para usar un `CMFCMenuBar` de objeto, incrustar en el objeto de marco de ventana principal. Al procesar la `WM_CREATE` de mensaje, llame a `CMFCMenuBar::Create` o `CMFCMenuBar::CreateEx`. Independientemente de que crea la función que utilice, pase un puntero a la ventana de marco principal. A continuación, habilite el acoplamiento llamando a [CFrameWndEx::EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking). Acople este menú llamando a [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar varios métodos en la `CMFCMenuBar` clase. En el ejemplo se muestra cómo establecer el estilo del panel, habilitar el botón Personalizar, habilitar un cuadro de ayuda, habilitar las sombras de los menús emergentes y actualizar la barra de menús. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_IEDemo](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&3;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]  
  
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
  
##  <a name="a-nameadjustlocationsa--cmfcmenubaradjustlocations"></a><a name="adjustlocations"></a>CMFCMenuBar::AdjustLocations  
 Ajusta las posiciones de los elementos de menú en la barra de menús.  
  
```  
virtual void AdjustLocations();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameallowchangetextlabelsa--cmfcmenubarallowchangetextlabels"></a><a name="allowchangetextlabels"></a>CMFCMenuBar::AllowChangeTextLabels  
 Determina si se permiten las etiquetas de texto en imágenes en la barra de menús.  
  
```  
virtual BOOL AllowChangeTextLabels() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si el usuario puede elegir mostrar las etiquetas de texto en imágenes.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameallowshowonpanemenua--cmfcmenubarallowshowonpanemenu"></a><a name="allowshowonpanemenu"></a>CMFCMenuBar::AllowShowOnPaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowShowOnPaneMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcfixedlayouta--cmfcmenubarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCMenuBar::CalcFixedLayout  
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
  
##  <a name="a-namecalclayouta--cmfcmenubarcalclayout"></a><a name="calclayout"></a>CMFCMenuBar::CalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize CalcLayout(
    DWORD dwMode,  
    int nLength = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dwMode`  
 [in] `nLength`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcmaxbuttonheighta--cmfcmenubarcalcmaxbuttonheight"></a><a name="calcmaxbuttonheight"></a>CMFCMenuBar::CalcMaxButtonHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int CalcMaxButtonHeight();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecanbecloseda--cmfcmenubarcanbeclosed"></a><a name="canbeclosed"></a>CMFCMenuBar::CanBeClosed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecanberestoreda--cmfcmenubarcanberestored"></a><a name="canberestored"></a>CMFCMenuBar::CanBeRestored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL CanBeRestored() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreatea--cmfcmenubarcreate"></a><a name="create"></a>CMFCMenuBar::Create  
 Crea un control de menú y lo adjunta a un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,  
    UINT nID = AFX_IDW_MENUBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pParentWnd`  
 Puntero a la ventana primaria para el nuevo `CMFCMenuBar` objeto.  
  
 [in] `dwStyle`  
 El estilo de la nueva barra de menús.  
  
 [in] `nID`  
 El identificador de la ventana secundaria de la barra de menús.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Después de construir un `CMFCMenuBar` de objeto, se debe llamar a `Create`. Este método crea el `CMFCMenuBar` controlar y lo adjunta a la `CMFCMenuBar` objeto.  
  
 Para obtener más información acerca de los estilos de barra de herramientas, consulte [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).  
  
##  <a name="a-namecreateexa--cmfcmenubarcreateex"></a><a name="createex"></a>CMFCMenuBar::CreateEx  
 Crea un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto con estilos extendidos especificados.  
  
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
 [in] `pParentWnd`  
 Puntero a la ventana primaria del nuevo `CMFCMenuBar` objeto.  
  
 [in] `dwCtrlStyle`  
 Estilos adicionales para la nueva barra de menús.  
  
 [in] `dwStyle`  
 Estilo de la nueva barra de menús principal.  
  
 [in] `rcBorders`  
 Un `CRect` parámetro que especifica el tamaño de los bordes de la `CMFCMenuBar` objeto.  
  
 [in] `nID`  
 El identificador de la ventana secundaria de la barra de menús.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Debe utilizar esta función en lugar de [CMFCMenuBar::Create](#create) cuando desee especificar estilos además el estilo de barra de herramientas. Algunos estilos adicionales utilizados con frecuencia son `TBSTYLE_TRANSPARENT` y `CBRS_TOP`.  
  
 Para ver listas de estilos adicionales, consulte [Control de barra de herramientas y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439), [estilos de control comunes](http://msdn.microsoft.com/library/windows/desktop/bb775498), y [comunes estilos de ventana](http://msdn.microsoft.com/library/windows/desktop/ms632600).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `CreateEx` método de la `CMFCMenuBar` clase. Este fragmento de código forma parte de la [ejemplo de demostración de IE](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_IEDemo](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo&#2;](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]  
  
##  <a name="a-namecreatefrommenua--cmfcmenubarcreatefrommenu"></a><a name="createfrommenu"></a>CMFCMenuBar::CreateFromMenu  
 Inicializa un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto. Los modelos de este método la `CMFCMenuBar` objeto después de un `HMENU` parámetro.  
  
```  
virtual void CreateFromMenu(
    HMENU hMenu,  
    BOOL bDefaultMenu = FALSE,  
    BOOL bForceUpdate = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMenu`  
 Identificador de un recurso de menú. `CreateFromMenu`este recurso se utiliza como plantilla para el `CMFCMenuBar`.  
  
 [in] `bDefaultMenu`  
 Valor booleano que indica si el nuevo menú es el predeterminado.  
  
 [in] `bForceUpdate`  
 Valor booleano que indica si este método obliga a una actualización del menú.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método si desea que los mismos elementos de menú como un recurso de menú de un control de menú. Llamar a este método después de llamar a cualquiera [CMFCMenuBar::Create](#create) o [CMFCMenuBar::CreateEx](#createex).  
  
##  <a name="a-nameenablehelpcomboboxa--cmfcmenubarenablehelpcombobox"></a><a name="enablehelpcombobox"></a>CMFCMenuBar::EnableHelpCombobox  
 Permite un **ayuda** cuadro combinado que se encuentra en el lado derecho de la barra de menús.  
  
```  
void EnableHelpCombobox(
    UINT uiID,  
    LPCTSTR lpszPrompt = NULL,  
    int nComboBoxWidth = 150);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 El identificador de comando para el botón de la **ayuda** cuadro combinado.  
  
 [in] `lpszPrompt`  
 Una cadena que contiene el texto que muestra el marco de trabajo en el cuadro combinado si está vacío y no está activo. Por ejemplo, "Escriba aquí el texto".  
  
 [in] `nComboBoxWidth`  
 El ancho del botón para el cuadro combinado, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El **ayuda** cuadro combinado es similar a la **ayuda** cuadro combinado en la barra de menús de [!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)].  
  
 Cuando se llama a este método con `uiID` establecido en 0, este método oculta el cuadro combinado. De lo contrario, este método muestra automáticamente el cuadro combinado en el lado derecho de la barra de menús. Después de llamar a este método, llame a [CMFCMenuBar::GetHelpCombobox](#gethelpcombobox) para obtener un puntero a insertada [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) objeto.  
  
##  <a name="a-nameenablemenushadowsa--cmfcmenubarenablemenushadows"></a><a name="enablemenushadows"></a>CMFCMenuBar::EnableMenuShadows  
 Habilita las sombras de los menús emergentes.  
  
```  
static void EnableMenuShadows(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Parámetro booleano que indica si se deben habilitar las sombras de los menús emergentes.  
  
### <a name="remarks"></a>Comentarios  
 El algoritmo que utiliza este método es complejo y puede reducir el rendimiento de su aplicación en sistemas más lentos.  
  
##  <a name="a-namegetavailableexpandsizea--cmfcmenubargetavailableexpandsize"></a><a name="getavailableexpandsize"></a>CMFCMenuBar::GetAvailableExpandSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetAvailableExpandSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetcolumnwidtha--cmfcmenubargetcolumnwidth"></a><a name="getcolumnwidth"></a>CMFCMenuBar::GetColumnWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetColumnWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdefaultmenua--cmfcmenubargetdefaultmenu"></a><a name="getdefaultmenu"></a>CMFCMenuBar::GetDefaultMenu  
 Obtiene un identificador en el menú original. El marco de trabajo carga el menú original del archivo de recursos.  
  
```  
HMENU GetDefaultMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de un recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación personaliza un menú, puede utilizar este método para obtener un identificador para el menú original.  
  
##  <a name="a-namegetdefaultmenuresida--cmfcmenubargetdefaultmenuresid"></a><a name="getdefaultmenuresid"></a>CMFCMenuBar::GetDefaultMenuResId  
 Recupera el identificador de recurso para el menú predeterminado.  
  
```  
UINT GetDefaultMenuResId() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de recurso de menú.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo carga el menú predeterminado para la `CMFCMenuBar` objeto del archivo de recursos.  
  
##  <a name="a-namegetfloatpopupdirectiona--cmfcmenubargetfloatpopupdirection"></a><a name="getfloatpopupdirection"></a>CMFCMenuBar::GetFloatPopupDirection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetforcedownarrowsa--cmfcmenubargetforcedownarrows"></a><a name="getforcedownarrows"></a>CMFCMenuBar::GetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL GetForceDownArrows();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegethelpcomboboxa--cmfcmenubargethelpcombobox"></a><a name="gethelpcombobox"></a>CMFCMenuBar::GetHelpCombobox  
 Devuelve un puntero a la **ayuda** cuadro combinado.  
  
```  
CMFCToolBarComboBoxButton* GetHelpCombobox();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la **ayuda** cuadro combinado. `NULL`Si el **ayuda** cuadro combinado está oculto o no habilitado.  
  
### <a name="remarks"></a>Comentarios  
 El **ayuda** cuadro combinado se encuentra en el lado derecho de la barra de menús. Llame al método [CMFCMenuBar::EnableHelpCombobox](#enablehelpcombobox) para habilitar este cuadro combinado.  
  
##  <a name="a-namegethmenua--cmfcmenubargethmenu"></a><a name="gethmenu"></a>CMFCMenuBar::GetHMenu  
 Recupera el identificador del menú asociado a la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto.  
  
```  
HMENU GetHMenu() const;  
```  
  
##  <a name="a-namegetmenufonta--cmfcmenubargetmenufont"></a><a name="getmenufont"></a>CMFCMenuBar::GetMenuFont  
 Recupera la fuente actual del menú.  
  
```  
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHorz`  
 Parámetro booleano que especifica si se devuelve la fuente horizontal o vertical. `TRUE`indica la fuente horizontal.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CFont](../../mfc/reference/cfont-class.md) parámetro que contiene la fuente actual de barra de menús.  
  
### <a name="remarks"></a>Comentarios  
 La fuente devuelta es un parámetro global para la aplicación. Se mantienen dos fuentes globales para todos `CMFCMenuBar` objetos. Estas fuentes independientes se utilizan para las barras de menús horizontal y vertical.  
  
##  <a name="a-namegetmenuitema--cmfcmenubargetmenuitem"></a><a name="getmenuitem"></a>CMFCMenuBar::GetMenuItem  
 Recupera un [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objeto en una barra de menús basado en el índice del elemento.  
  
```  
CMFCToolBarButton* GetMenuItem(int iItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iItem`  
 El índice del elemento de menú para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `CMFCToolBarButton` objeto que coincide con el índice especificado por `iItem`. `NULL`Si el índice no es válido.  
  
##  <a name="a-namegetrowheighta--cmfcmenubargetrowheight"></a><a name="getrowheight"></a>CMFCMenuBar::GetRowHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRowHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsystembuttona--cmfcmenubargetsystembutton"></a><a name="getsystembutton"></a>CMFCMenuBar::GetSystemButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,  
    BOOL bByCommand = TRUE) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiBtn`  
 [in] `bByCommand`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsystembuttonscounta--cmfcmenubargetsystembuttonscount"></a><a name="getsystembuttonscount"></a>CMFCMenuBar::GetSystemButtonsCount  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetSystemButtonsCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsystemmenua--cmfcmenubargetsystemmenu"></a><a name="getsystemmenu"></a>CMFCMenuBar::GetSystemMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarSystemMenuButton* GetSystemMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehighlightdisableditemsa--cmfcmenubarhighlightdisableditems"></a><a name="highlightdisableditems"></a>CMFCMenuBar::HighlightDisabledItems  
 Controla si el marco resalta los elementos de menú desactivados.  
  
```  
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHighlight`  
 Parámetro booleano que indica si el marco resalta los elementos de menú no está disponible.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no resalta los elementos de menú no está disponible cuando el usuario coloca el puntero del mouse sobre ellos.  
  
##  <a name="a-nameisbuttonextrasizeavailablea--cmfcmenubarisbuttonextrasizeavailable"></a><a name="isbuttonextrasizeavailable"></a>CMFCMenuBar::IsButtonExtraSizeAvailable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsButtonExtraSizeAvailable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameishighlightdisableditemsa--cmfcmenubarishighlightdisableditems"></a><a name="ishighlightdisableditems"></a>CMFCMenuBar::IsHighlightDisabledItems  
 Indica si el marco resalta los elementos de menú no está disponible.  
  
```  
static BOOL IsHighlightDisabledItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se resaltan los elementos de menú no está disponible; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo no resalta los elementos de menú no está disponible cuando el usuario coloca el puntero del mouse sobre ellos. Utilice la [CMFCMenuBar::HighlightDisabledItems](#highlightdisableditems) método para habilitar esta característica.  
  
##  <a name="a-nameismenushadowsa--cmfcmenubarismenushadows"></a><a name="ismenushadows"></a>CMFCMenuBar::IsMenuShadows  
 Indica si el marco de trabajo dibuja sombras para los menús emergentes.  
  
```  
static BOOL IsMenuShadows();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo dibuja sombras de menú; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCMenuBar::EnableMenuShadows](#enablemenushadows) método para habilitar o deshabilitar esta característica.  
  
##  <a name="a-nameisrecentlyusedmenusa--cmfcmenubarisrecentlyusedmenus"></a><a name="isrecentlyusedmenus"></a>CMFCMenuBar::IsRecentlyUsedMenus  
 Indica si los comandos de menú utilizados recientemente se muestran en la barra de menús.  
  
```  
static BOOL IsRecentlyUsedMenus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `CMFCMenuBar` objeto muestra usado recientemente comandos de menú; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la función [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus) para controlar si se muestra la barra de menús recientemente usa comandos de menú.  
  
##  <a name="a-nameisshowallcommandsa--cmfcmenubarisshowallcommands"></a><a name="isshowallcommands"></a>CMFCMenuBar::IsShowAllCommands  
 Indica si los menús Mostrar todos los comandos.  
  
```  
static BOOL IsShowAllCommands();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el `CMFCMenuBar` todos los muestra comandos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCMenuBar` objeto puede configurarse para mostrar todos los comandos o mostrar sólo un subconjunto de comandos. Para obtener más información sobre esta característica, consulte [CMFCMenuBar clase](../../mfc/reference/cmfcmenubar-class.md).  
  
 `IsShowAllCommands`le indicará cómo esta característica se configura para la `CMFCMenuBar` objeto. Utilice los métodos para controlar qué comandos de menú se muestran [CMFCMenuBar::SetShowAllCommands](#setshowallcommands) y [CMFCMenuBar::SetRecentlyUsedMenus](#setrecentlyusedmenus).  
  
##  <a name="a-nameisshowallcommandsdelaya--cmfcmenubarisshowallcommandsdelay"></a><a name="isshowallcommandsdelay"></a>CMFCMenuBar::IsShowAllCommandsDelay  
 Indica si la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto muestra todos los comandos tras un breve retraso.  
  
```  
static BOOL IsShowAllCommandsDelay();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la barra de menús muestra menús completos transcurridos unos segundos; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se configura una barra de menús para mostrar elementos utilizados recientemente, la barra de menús muestra el menú completo de dos maneras:  
  
-   Mostrar el menú completo después de un retraso programado de cuando el usuario desplaza el cursor sobre la flecha en la parte inferior del menú.  
  
-   Mostrar el menú completo después de que el usuario hace clic en la flecha situada en la parte inferior del menú.  
  
 De forma predeterminada, todos los `CMFCMenuBar` objetos utilizan la opción para mostrar el menú completo después de un breve retraso. Esta opción no se puede cambiar mediante programación en el `CMFCMenuBar` clase. Sin embargo, un usuario puede cambiar el comportamiento durante la personalización de la barra de herramientas mediante el **personalizar** cuadro de diálogo...  
  
##  <a name="a-nameloadstatea--cmfcmenubarloadstate"></a><a name="loadstate"></a>CMFCMenuBar::LoadState  
 Carga el estado de la barra de menús del registro de Windows.  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Cadena que contiene la ruta de acceso de una clave del registro de Windows.  
  
 [in] `nIndex`  
 El identificador de control de la barra de menús.  
  
 [in] `uiID`  
 Un valor reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [CMFCMenuBar::SaveState](#savestate) método para guardar el estado de la barra de menús en el registro. La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.  
  
 En la mayoría de los casos la aplicación no llama a `LoadState`. El marco de trabajo llama a este método cuando se inicializa el área de trabajo.  
  
##  <a name="a-nameonchangehota--cmfcmenubaronchangehot"></a><a name="onchangehot"></a>CMFCMenuBar::OnChangeHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeHot(int iHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iHot`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondefaultmenuloadeda--cmfcmenubarondefaultmenuloaded"></a><a name="ondefaultmenuloaded"></a>CMFCMenuBar::OnDefaultMenuLoaded  
 El marco de trabajo llama a este método cuando se carga el recurso del archivo de recursos.  
  
```  
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hMenu`  
 El identificador del menú asociado a la `CMFCMenuBar` objeto.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplazar esta función para ejecutar código personalizado después de que el marco de trabajo carga un recurso de menú desde el archivo de recursos.  
  
##  <a name="a-nameonsendcommanda--cmfcmenubaronsendcommand"></a><a name="onsendcommand"></a>CMFCMenuBar::OnSendCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonsetdefaultbuttontexta--cmfcmenubaronsetdefaultbuttontext"></a><a name="onsetdefaultbuttontext"></a>CMFCMenuBar::OnSetDefaultButtonText  
 El marco de trabajo llama a este método cuando el usuario cambia el texto de un elemento en la barra de menús.  
  
```  
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero a la [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md) objeto que el usuario desea personalizar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo aplica los cambios del usuario a la barra de menús; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método cambia el texto del botón en el texto que proporciona el usuario.  
  
##  <a name="a-nameontoolhittesta--cmfcmenubarontoolhittest"></a><a name="ontoolhittest"></a>CMFCMenuBar::OnToolHitTest  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual INT_PTR OnToolHitTest(
    CPoint point,  
    TOOLINFO* pTI) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 [in] `pTI`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepretranslatemessagea--cmfcmenubarpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuBar::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerestoreoriginalstatea--cmfcmenubarrestoreoriginalstate"></a><a name="restoreoriginalstate"></a>CMFCMenuBar::RestoreOriginalstate  
 Llamado por el marco de trabajo cuando el usuario selecciona **restablecer** desde el **personalizar** cuadro de diálogo.  
  
```  
virtual BOOL RestoreOriginalstate();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método cuando el usuario selecciona **restablecer** en el menú de personalización. Manualmente, puede llamar a este método para restablecer mediante programación el estado de la barra de menús. Este método carga el estado original del archivo de recursos.  
  
 Invalide este método si desea realizar cualquier procesamiento cuando el usuario selecciona el **restablecer** opción.  
  
##  <a name="a-namesavestatea--cmfcmenubarsavestate"></a><a name="savestate"></a>CMFCMenuBar::SaveState  
 Guarda el estado de la [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto en el registro de Windows.  
  
```  
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,  
    int nIndex = -1,  
    UINT uiID = (UINT)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszProfileName`  
 Cadena que contiene la ruta de acceso de una clave del registro de Windows.  
  
 [in] `nIndex`  
 El identificador de control de la barra de menús.  
  
 [in] `uiID`  
 Un valor reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; de lo contrario, `FALSE`;  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, la aplicación no llama a `SaveState`. El marco de trabajo llama a este método cuando se serializa el área de trabajo. Para obtener más información, consulte [CWinAppEx::SaveState](../../mfc/reference/cwinappex-class.md#savestate).  
  
 La información guardada incluye los elementos de menú, el estado de acoplamiento y la posición de la barra de menús.  
  
##  <a name="a-namesetdefaultmenuresida--cmfcmenubarsetdefaultmenuresid"></a><a name="setdefaultmenuresid"></a>CMFCMenuBar::SetDefaultMenuResId  
 Establece el menú predeterminado para un [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md) objeto basado en el identificador de recurso.  
  
```  
void SetDefaultMenuResId(UINT uiResId);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiResId`  
 El identificador de recurso para el nuevo menú de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCMenuBar::RestoreOriginalstate](#restoreoriginalstate) método restaura el menú predeterminado del archivo de recursos.  
  
 Utilice la [CMFCMenuBar::GetDefaultMenuResId](#getdefaultmenuresid) método para recuperar el menú predeterminado sin restaurarlo.  
  
##  <a name="a-namesetforcedownarrowsa--cmfcmenubarsetforcedownarrows"></a><a name="setforcedownarrows"></a>CMFCMenuBar::SetForceDownArrows  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetForceDownArrows(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetmaximizemodea--cmfcmenubarsetmaximizemode"></a><a name="setmaximizemode"></a>CMFCMenuBar::SetMaximizeMode  
 El marco de trabajo llama a este método cuando una MDI cambia su modo de visualización y se debe actualizar la barra de menús.  
  
```  
void SetMaximizeMode(
    BOOL bMax,  
    CWnd* pWnd = NULL,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMax`  
 Valor booleano que especifica el modo. Vea la sección Comentarios para obtener más información.  
  
 [in] `pWnd`  
 Puntero a la ventana secundaria MDI que está cambiando.  
  
 [in] `bRecalcLayout`  
 Valor booleano que especifica si el diseño de la barra de menús debe volver a calcular inmediatamente.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria MDI, una barra de menús que se adjunta a la ventana de marco principal MDI muestra el menú de sistema y la **minimizar**, **maximizar** y **cerrar** botones. Si `bMax` es `TRUE` y `pWnd` no es `NULL`, se maximiza la ventana secundaria MDI y la barra de menús debe incorporar los controles adicionales. De lo contrario, se devuelve la barra de menús a su estado normal.  
  
##  <a name="a-namesetmenubuttonrtca--cmfcmenubarsetmenubuttonrtc"></a><a name="setmenubuttonrtc"></a>CMFCMenuBar::SetMenuButtonRTC  
 Establece la información de clase en tiempo de ejecución que el marco de trabajo se usa cuando el usuario crea botones de menú.  
  
```  
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMenuButtonRTC`  
 El [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) información para una clase derivada de la [CMFCMenuButton clase](../../mfc/reference/cmfcmenubutton-class.md).  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario agrega nuevos botones a la barra de menús, el marco de trabajo crea dinámicamente los botones. De forma predeterminada, crea `CMFCMenuButton` objetos. Invalide este método para cambiar el tipo de objetos de botón que crea el marco de trabajo.  
  
##  <a name="a-namesetmenufonta--cmfcmenubarsetmenufont"></a><a name="setmenufont"></a>CMFCMenuBar::SetMenuFont  
 Establece la fuente para todas las barras de menú en la aplicación.  
  
```  
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpLogFont`  
 Un puntero a un [LOGFONT](http://msdn.microsoft.com/library/windows/desktop/bb773327) estructura que define la fuente que se va a establecer.  
  
 [in] `bHorz`  
 TRUE si desea que el `lpLogFont` parámetro que se usará para la fuente vertical, FALSE si desea que se usará para la fuente horizontal.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método se realizó correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Se utilizan dos fuentes para todos los `CMFCMenuBar` objetos. Estas fuentes independientes se utilizan para las barras de menús horizontal y vertical.  
  
 La configuración de fuente son variables globales y afectan a todos los `CMFCMenuBar` objetos.  
  
##  <a name="a-namesetrecentlyusedmenusa--cmfcmenubarsetrecentlyusedmenus"></a><a name="setrecentlyusedmenus"></a>CMFCMenuBar::SetRecentlyUsedMenus  
 Controla si se muestra una barra de menús recientemente usa comandos de menú.  
  
```  
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bOn`  
 Un valor booleano que controla si se muestran los comandos de menú utilizados recientemente.  
  
##  <a name="a-namesetshowallcommandsa--cmfcmenubarsetshowallcommands"></a><a name="setshowallcommands"></a>CMFCMenuBar::SetShowAllCommands  
 Controla si un menú muestra todos los comandos disponibles.  
  
```  
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShowAllCommands`  
 Parámetro booleano que especifica si el menú emergente muestra todos los comandos de menú.  
  
### <a name="remarks"></a>Comentarios  
 Si un menú muestra todos los comandos de menú, oculta los comandos que se usan rara vez. Para obtener más información acerca de cómo mostrar comandos de menú, vea [CMFCMenuBar clase](../../mfc/reference/cmfcmenubar-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

