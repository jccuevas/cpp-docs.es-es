---
title: Clase CMFCPopupMenu | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCPopupMenu
dev_langs:
- C++
helpviewer_keywords:
- CMFCPopupMenu class
ms.assetid: 9555dca1-8c9c-44c9-af72-0659ddad128e
caps.latest.revision: 40
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
ms.openlocfilehash: a45f4e1b73c7cbff994c0b360c01c2f331ccab23
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcpopupmenu-class"></a>Clase CMFCPopupMenu
Implementa la funcionalidad del menú emergente de Windows y lo prolonga agregando características tales como los menús con barra desplazable e información sobre herramientas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCPopupMenu : public CMiniFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::CMFCPopupMenu](#cmfcpopupmenu)|Construye un objeto `CMFCPopupMenu`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::ActivatePopupMenu](#activatepopupmenu)||  
|[CMFCPopupMenu::AlwaysShowEmptyToolsEntry](#alwaysshowemptytoolsentry)|Establece si se habilita un menú emergente para mostrar entradas vacías para herramientas definidas por el usuario.|  
|[CMFCPopupMenu::AreAllCommandsShown](#areallcommandsshown)||  
|[CMFCPopupMenu::CheckArea](#checkarea)|Determina la ubicación de un punto en relación con el menú emergente.|  
|[CMFCPopupMenu::CloseMenu](#closemenu)||  
|[CMFCPopupMenu::Create](#create)|Crea un menú emergente y lo adjunta a la `CMFCPopupMenu` objeto.|  
|[CMFCPopupMenu::DefaultMouseClickOnClose](#defaultmouseclickonclose)||  
|[CMFCPopupMenu::EnableMenuLogo](#enablemenulogo)|Inicializa el logotipo de un menú emergente.|  
|[CMFCPopupMenu::EnableMenuSound](#enablemenusound)|Habilita el sonido del menú.|  
|[CMFCPopupMenu::EnableResize](#enableresize)||  
|[CMFCPopupMenu::EnableScrolling](#enablescrolling)||  
|[CMFCPopupMenu::EnableVertResize](#enablevertresize)||  
|[CMFCPopupMenu::FindSubItemByCommand](#findsubitembycommand)||  
|[CMFCPopupMenu::GetActiveMenu](#getactivemenu)|Devuelve el menú activo actualmente.|  
|[CMFCPopupMenu::GetAnimationSpeed](#getanimationspeed)|Devuelve la velocidad de animación de menús emergentes.|  
|[CMFCPopupMenu::GetAnimationType](#getanimationtype)|Devuelve el tipo actual de la animación del menú emergente.|  
|[CMFCPopupMenu::GetDropDirection](#getdropdirection)||  
|[CMFCPopupMenu::GetForceMenuFocus](#getforcemenufocus)|Indica si el foco se devuelve al menú de la barra cuando se muestra un menú emergente.|  
|[CMFCPopupMenu::GetForceShadow](#getforceshadow)||  
|[CMFCPopupMenu::GetHMenu](#gethmenu)|Devuelve un identificador para el recurso de menú asociada.|  
|[CMFCPopupMenu::GetMenuBar](#getmenubar)|Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) incrustado en el menú emergente.|  
|[CMFCPopupMenu::GetMenuItem](#getmenuitem)|Devuelve un puntero al elemento de menú en el índice especificado.|  
|[CMFCPopupMenu::GetMenuItemCount](#getmenuitemcount)|Devuelve el número de elementos de un menú emergente.|  
|[CMFCPopupMenu::GetMessageWnd](#getmessagewnd)|Devuelve un puntero a la ventana donde el marco de trabajo enruta los mensajes de menú emergente.|  
|[CMFCPopupMenu::GetParentArea](#getparentarea)||  
|[CMFCPopupMenu::GetParentButton](#getparentbutton)|Devuelve un puntero al botón de barra de herramientas primario.|  
|[CMFCPopupMenu::GetParentPopupMenu](#getparentpopupmenu)|Devuelve un puntero al menú emergente primario.|  
|[CMFCPopupMenu::GetParentRibbonElement](#getparentribbonelement)||  
|[CMFCPopupMenu::GetParentToolBar](#getparenttoolbar)|Devuelve un puntero a la barra de herramientas primario.|  
|[CMFCPopupMenu::GetQuickCustomizeType](#getquickcustomizetype)||  
|[CMFCPopupMenu::GetSelItem](#getselitem)|Devuelve un puntero al comando de menú seleccionado.|  
|[CMFCPopupMenu::HasBeenResized](#hasbeenresized)||  
|[CMFCPopupMenu::HideRarelyUsedCommands](#hiderarelyusedcommands)|Indica si el menú emergente puede ocultar comandos usados con poca frecuencia.|  
|[CMFCPopupMenu::InCommand](#incommand)||  
|[CMFCPopupMenu::InsertItem](#insertitem)|Inserta un nuevo elemento en el menú emergente en la ubicación especificada.|  
|[CMFCPopupMenu::InsertSeparator](#insertseparator)|Inserta un separador en el menú emergente en la ubicación especificada.|  
|[CMFCPopupMenu::IsAlwaysClose](#isalwaysclose)||  
|[CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry](#isalwaysshowemptytoolsentry)||  
|[CMFCPopupMenu::IsCustomizePane](#iscustomizepane)|Indica si el menú emergente está funcionando como un **QuickCustomizePane**.|  
|[CMFCPopupMenu::IsEscClose](#isescclose)||  
|[CMFCPopupMenu::IsIdle](#isidle)|Indica si un menú emergente está inactivo.|  
|[CMFCPopupMenu::IsMenuSound](#ismenusound)||  
|[CMFCPopupMenu::IsQuickCustomize](#isquickcustomize)|Determina si el asociado [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md) está en modo de QuickCustomize.|  
|[CMFCPopupMenu::IsResizeble](#isresizeble)||  
|[CMFCPopupMenu::IsRightAlign](#isrightalign)|Indica si el menú está alineado a la derecha o alineado a la izquierda.|  
|[CMFCPopupMenu::IsScrollable](#isscrollable)||  
|[CMFCPopupMenu::IsSendMenuSelectMsg](#issendmenuselectmsg)|Indica si el marco de trabajo notifica el marco primario cuando el usuario selecciona un comando en el menú emergente.|  
|[CMFCPopupMenu::IsShown](#isshown)|Indica si el menú emergente es visible actualmente.|  
|[CMFCPopupMenu::MoveTo](#moveto)||  
|[CMFCPopupMenu::OnCmdMsg](#oncmdmsg)|(Invalida `CFrameWnd::OnCmdMsg`).|  
|[CMFCPopupMenu::PostCommand](#postcommand)||  
|[CMFCPopupMenu::PreTranslateMessage](#pretranslatemessage)|(Invalida `CFrameWnd::PreTranslateMessage`).|  
|[CMFCPopupMenu::RecalcLayout](#recalclayout)|Llamado por el marco de trabajo cuando las barras de controles estándar se activan o desactivan o cuando se cambia el tamaño de la ventana de marco. (Invalida [RecalcLayout](../../mfc/reference/cframewnd-class.md#recalclayout).)|  
|[CMFCPopupMenu::RemoveAllItems](#removeallitems)|Borra todos los elementos de un menú emergente.|  
|[CMFCPopupMenu::RemoveItem](#removeitem)|Quita el elemento especificado de un menú emergente.|  
|[CMFCPopupMenu::SaveState](#savestate)||  
|[CMFCPopupMenu::SetAnimationSpeed](#setanimationspeed)|Establece la velocidad de animación de menús emergentes.|  
|[CMFCPopupMenu::SetAnimationType](#setanimationtype)|Establece el tipo de animación para el menú emergente.|  
|[CMFCPopupMenu::SetAutoDestroy](#setautodestroy)||  
|[CMFCPopupMenu::SetDefaultItem](#setdefaultitem)|Establece el comando predeterminado para el menú emergente.|  
|[CMFCPopupMenu::SetForceMenuFocus](#setforcemenufocus)|Fuerza el foco de entrada para volver al menú de barra cuando se muestra un menú emergente.|  
|[CMFCPopupMenu::SetForceShadow](#setforceshadow)|Fuerza el marco de menú dibujar sombras cuando aparecen los menús emergentes fuera del marco principal.|  
|[CMFCPopupMenu::SetMaxWidth](#setmaxwidth)|Establezca el ancho máximo para el menú emergente.|  
|[CMFCPopupMenu::SetMessageWnd](#setmessagewnd)||  
|[CMFCPopupMenu::SetParentRibbonElement](#setparentribbonelement)||  
|[CMFCPopupMenu::SetQuickCustomizeType](#setquickcustomizetype)||  
|[CMFCPopupMenu::SetQuickMode](#setquickmode)||  
|[CMFCPopupMenu::SetRightAlign](#setrightalign)|Establece la alineación de menú para los menús emergentes.|  
|[CMFCPopupMenu::SetSendMenuSelectMsg](#setsendmenuselectmsg)|Establece un indicador que controla si el menú emergente notifica su marco primario cuando el usuario selecciona un comando.|  
|[CMFCPopupMenu::ShowAllCommands](#showallcommands)|Fuerza el menú emergente para mostrar todos los comandos.|  
|[CMFCPopupMenu::TriggerResize](#triggerresize)||  
|[CMFCPopupMenu::UpdateAllShadows](#updateallshadows)|Actualiza las sombras para todos los menús emergentes abiertos.|  
|[CMFCPopupMenu::UpdateShadow](#updateshadow)|Actualiza la sombra para el menú emergente.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCPopupMenu::CreateTearOffBar](#createtearoffbar)||  
|[CMFCPopupMenu::OnChangeHot](#onchangehot)||  
|[CMFCPopupMenu::OnChooseItem](#onchooseitem)||  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, MFC crea automáticamente los menús emergentes. Si desea crear un `CMFCPopupMenu` objeto manualmente, asignar uno del montón y, a continuación, llame a [CMFCPopupMenu::Create](#create).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo configurar un objeto de menú emergente. En el ejemplo se muestra cómo configurar el logotipo y el sonido del menú emergente, el tipo y la velocidad de animación, menú dibujar sombras cuando aparezca el menú emergente fuera del marco principal, establezca el ancho máximo, y establecer la alineación del menú de la derecha del menú emergente. Este fragmento de código forma parte de la [ejemplo Custom Pages](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_CustomPages&#2;](../../mfc/reference/codesnippet/cpp/cmfcpopupmenu-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [CMiniFrameWnd](../../mfc/reference/cminiframewnd-class.md)  
  
 `CMFCPopupMenu`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpopupmenu.h  
  
##  <a name="a-nameactivatepopupmenua--cmfcpopupmenuactivatepopupmenu"></a><a name="activatepopupmenu"></a>CMFCPopupMenu::ActivatePopupMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall ActivatePopupMenu(
    CFrameWnd* pTopFrame,  
    CMFCPopupMenu* pPopupMenu);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTopFrame`  
 [in] `pPopupMenu`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namealwaysshowemptytoolsentrya--cmfcpopupmenualwaysshowemptytoolsentry"></a><a name="alwaysshowemptytoolsentry"></a>CMFCPopupMenu::AlwaysShowEmptyToolsEntry  
 Establece si se habilita un menú emergente para mostrar entradas vacías para herramientas definidas por el usuario.  
  
```  
static void AlwaysShowEmptyToolsEntry(BOOL bShow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShow`  
 `TRUE`Si el menú emergente puede mostrar entradas vacías; `FALSE` en caso contrario.  
  
##  <a name="a-nameareallcommandsshowna--cmfcpopupmenuareallcommandsshown"></a><a name="areallcommandsshown"></a>CMFCPopupMenu::AreAllCommandsShown  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL AreAllCommandsShown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecheckareaa--cmfcpopupmenucheckarea"></a><a name="checkarea"></a>CMFCPopupMenu::CheckArea  
 Determina la ubicación de un punto en relación con el menú emergente.  
  
```  
MENUAREA_TYPE CheckArea(const CPoint& ptScreen) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ptScreen`  
 Un punto en coordenadas de pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 Parámetro MENUAREA_TYPE que indica que es el punto en relación con el menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 Un parámetro MENUAREA_TYPE puede tener uno de los siguientes valores.  
  
-   EXTERIOR - `ptScreen` está fuera del menú emergente.  
  
-   LOGOTIPO - `ptScreen` sobre un área de logotipo.  
  
-   TEAROFF_CAPTION - `ptScreen` es a través de la leyenda desplazable.  
  
-   SHADOW_BOTTOM - `ptScreen` es a través de la sombra de la parte inferior del menú emergente.  
  
-   SHADOW_RIGHT - `ptScreen` es a través de la sombra derecho del menú emergente.  
  
-   MENÚ - `ptScreen` es a través de un comando.  
  
##  <a name="a-nameclosemenua--cmfcpopupmenuclosemenu"></a><a name="closemenu"></a>CMFCPopupMenu::CloseMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void CloseMenu(BOOL bSetFocusToBar = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSetFocusToBar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecmfcpopupmenua--cmfcpopupmenucmfcpopupmenu"></a><a name="cmfcpopupmenu"></a>CMFCPopupMenu::CMFCPopupMenu  
 Construye un [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) objeto.  
  
```  
CMFCPopupMenu(
    CMFCToolBarsMenuPropertyPage* pCustPage,  
    LPCTSTR lpszTitle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCustPage`  
 Un puntero a una página de personalización.  
  
 [in] `lpszTitle`  
 Una cadena que contiene el título de menú.  
  
### <a name="remarks"></a>Comentarios  
 Este método asigna los recursos de un `CMFCPopupMenu`. Para crear el elemento de menú emergente, llame a [CMFCPopupMenu::Create](#create).  
  
##  <a name="a-namecreatea--cmfcpopupmenucreate"></a><a name="create"></a>CMFCPopupMenu::Create  
 Crea un menú emergente y lo adjunta a un [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md) objeto.  
  
```  
virtual BOOL Create(
    CWnd* pWndParent,  
    int x,  
    int y,  
    HMENU hMenu,  
    BOOL bLocked = FALSE,  
    BOOL bOwnMessage = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndParent`  
 La ventana primaria para el `CMFCPopupMenu`.  
  
 [in] `x`  
 La coordenada horizontal de pantalla para la ubicación del menú emergente  
  
 [in] `y`  
 La coordenada vertical de pantalla de la ubicación del menú emergente.  
  
 [in] `hMenu`  
 Identificador de un recurso de menú.  
  
 [in] `bLocked`  
 Parámetro booleano que indica si se puede personalizar el menú. `FALSE`indica que se puede personalizar el menú emergente.  
  
 [in] `bOwnMessage`  
 Parámetro booleano que indica cómo el marco de trabajo enruta los mensajes de menú. Vea la sección Comentarios para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si `bOwnMessage` es `TRUE`, el marco de trabajo enruta los mensajes de menú para `pWndParent`. `pWndParent`no debe ser `NULL` si `bOwnMessage` es `TRUE.` si `bOwnMessage` es `FALSE`, el marco de trabajo enruta los mensajes de menú al menú emergente primario.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CMFCPopuMenu` clase. Este fragmento de código forma parte de la [ejemplo Custom Pages](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_CustomPages](../../mfc/reference/codesnippet/cpp/cmfcpopupmenu-class_2.cpp)]  
  
##  <a name="a-namecreatetearoffbara--cmfcpopupmenucreatetearoffbar"></a><a name="createtearoffbar"></a>CMFCPopupMenu::CreateTearOffBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CPane* CreateTearOffBar(
    CFrameWnd* pWndMain,  
    UINT uiID,  
    LPCTSTR lpszName);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndMain`  
 [in] `uiID`  
 [in] `lpszName`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedefaultmouseclickonclosea--cmfcpopupmenudefaultmouseclickonclose"></a><a name="defaultmouseclickonclose"></a>CMFCPopupMenu::DefaultMouseClickOnClose  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DefaultMouseClickOnClose() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablemenulogoa--cmfcpopupmenuenablemenulogo"></a><a name="enablemenulogo"></a>CMFCPopupMenu::EnableMenuLogo  
 Inicializa el logotipo de un menú emergente.  
  
```  
void EnableMenuLogo(
    int iLogoSize,  
    LOGO_LOCATION nLogoLocation = MENU_LOGO_LEFT);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iLogoSize`  
 El tamaño del logotipo, en píxeles.  
  
 [in] `nLogoLocation`  
 Tipo de datos enumerado que indica la ubicación del logotipo.  
  
### <a name="remarks"></a>Comentarios  
 Para mostrar el logotipo, implemente el método [CFrameWndEx::OnDrawMenuLogo](../../mfc/reference/cframewndex-class.md#ondrawmenulogo) en la ventana de marco principal.  
  
 Los valores posibles de `nLogoLocation` son MENU_LOGO_LEFT, MENU_LOGO_RIGHT, MENU_LOGO_TOP y MENU_LOGO_BOTTOM.  
  
##  <a name="a-nameenablemenusounda--cmfcpopupmenuenablemenusound"></a><a name="enablemenusound"></a>CMFCPopupMenu::EnableMenuSound  
 Habilita el sonido del menú.  
  
```  
static void EnableMenuSound(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar el sonido, `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Si habilita el sonido, el marco llama a la [PlaySound](http://msdn.microsoft.com/library/windows/desktop/bb774426) método cuando un usuario abre un menú emergente o selecciona un comando de menú. De forma predeterminada, esta característica está habilitada.  
  
##  <a name="a-nameenableresizea--cmfcpopupmenuenableresize"></a><a name="enableresize"></a>CMFCPopupMenu::EnableResize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableResize(CSize sizeMinResize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `sizeMinResize`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablescrollinga--cmfcpopupmenuenablescrolling"></a><a name="enablescrolling"></a>CMFCPopupMenu::EnableScrolling  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableScrolling(BOOL = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `BOOL`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenablevertresizea--cmfcpopupmenuenablevertresize"></a><a name="enablevertresize"></a>CMFCPopupMenu::EnableVertResize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableVertResize(int nMinResize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nMinResize`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindsubitembycommanda--cmfcpopupmenufindsubitembycommand"></a><a name="findsubitembycommand"></a>CMFCPopupMenu::FindSubItemByCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCToolBarMenuButton* FindSubItemByCommand(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetactivemenua--cmfcpopupmenugetactivemenu"></a><a name="getactivemenu"></a>CMFCPopupMenu::GetActiveMenu  
 Devuelve el menú activo actualmente.  
  
```  
static CMFCPopupMenu* GetActiveMenu();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al menú emergente activo, o NULL si no hay menú emergente está activo actualmente.  
  
### <a name="remarks"></a>Comentarios  
 Cada aplicación puede tener a lo sumo uno activo menú emergente.  
  
##  <a name="a-namegetanimationspeeda--cmfcpopupmenugetanimationspeed"></a><a name="getanimationspeed"></a>CMFCPopupMenu::GetAnimationSpeed  
 Devuelve la velocidad de animación de menús emergentes.  
  
```  
static UINT GetAnimationSpeed();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que indica el tiempo, en milisegundos, que una animación de menús emergentes que se tarda en Finalizar.  
  
### <a name="remarks"></a>Comentarios  
 La velocidad de animación es un valor global. Utilice [CMFCPopupMenu::SetAnimationSpeed](#setanimationspeed) para cambiar la velocidad de animación de menús emergentes.  
  
##  <a name="a-namegetanimationtypea--cmfcpopupmenugetanimationtype"></a><a name="getanimationtype"></a>CMFCPopupMenu::GetAnimationType  
 Devuelve el tipo actual de animación emergente.  
  
```  
static CMFCPopupMenu::ANIMATION_TYPE GetAnimationType(BOOL bNoSystem = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNoSystem`  
 Parámetro booleano que indica si este método comprueba el valor global. FALSE si desea que este método para devolver el estilo de animación de esta instancia de la [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor enumerado que describe el tipo de animación.  
  
### <a name="remarks"></a>Comentarios  
 El estilo de animación de menús emergentes es global para la aplicación. Utilice [CMFCPopupMenu::SetAnimationType](#setanimationtype) para establecer el estilo de animación.  
  
 En la tabla siguiente enumera los tipos posibles de animación.  
  
 NO_ANIMATION  
 El menú emergente no está animado y aparece inmediatamente.  
  
 EXPANDIR  
 El marco de trabajo muestra el menú emergente de la esquina superior izquierda a la esquina inferior derecha.  
  
 DIAPOSITIVA  
 El menú emergente mueve de arriba a abajo.  
  
 ATENUACIÓN  
 El menú emergente aparece por primera vez transparente y solidificación gradualmente.  
  
##  <a name="a-namegetdropdirectiona--cmfcpopupmenugetdropdirection"></a><a name="getdropdirection"></a>CMFCPopupMenu::GetDropDirection  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
DROP_DIRECTION GetDropDirection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetforcemenufocusa--cmfcpopupmenugetforcemenufocus"></a><a name="getforcemenufocus"></a>CMFCPopupMenu::GetForceMenuFocus  
 Indica si el foco se devuelve al menú de la barra cuando se muestra un menú emergente.  
  
```  
static BOOL GetForceMenuFocus();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el foco de entrada se devuelve a la barra de menús cuando se muestra un menú emergente; `FALSE` si el menú emergente conserva el foco.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la aplicación no devolver el foco a la barra de menús. Para cambiar esta configuración, use [CMFCPopupMenu::SetForceMenuFocus](#setforcemenufocus).  
  
##  <a name="a-namegetforceshadowa--cmfcpopupmenugetforceshadow"></a><a name="getforceshadow"></a>CMFCPopupMenu::GetForceShadow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall GetForceShadow();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegethmenua--cmfcpopupmenugethmenu"></a><a name="gethmenu"></a>CMFCPopupMenu::GetHMenu  
 Devuelve un identificador para el recurso de menú asociada.  
  
```  
HMENU GetHMenu();
```  
  
##  <a name="a-namegetmenubara--cmfcpopupmenugetmenubar"></a><a name="getmenubar"></a>CMFCPopupMenu::GetMenuBar  
 Devuelve el [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md) incrustado en el menú emergente.  
  
```  
virtual CMFCPopupMenuBar* GetMenuBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a los datos incrustados `CMFCPopupMenuBar`.  
  
### <a name="remarks"></a>Comentarios  
 El menú emergente tiene incrustado `CMFCPopupMenuBar` objeto. Debe invalidar este método en una clase derivada si está utilizando una clase incrustada diferente.  
  
##  <a name="a-namegetmenuitema--cmfcpopupmenugetmenuitem"></a><a name="getmenuitem"></a>CMFCPopupMenu::GetMenuItem  
 Devuelve un puntero al elemento de menú en el índice especificado.  
  
```  
CMFCToolBarMenuButton* GetMenuItem(int iIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero de un elemento de menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un elemento de menú. `NULL`Si el índice no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de menú se representan mediante la [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md). Cuando se llama a este método, devuelve un puntero a la correspondiente `CMFCToolBarMenuButton`.  
  
##  <a name="a-namegetmenuitemcounta--cmfcpopupmenugetmenuitemcount"></a><a name="getmenuitemcount"></a>CMFCPopupMenu::GetMenuItemCount  
 Devuelve el número de elementos de un menú emergente.  
  
```  
int GetMenuItemCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el menú.  
  
##  <a name="a-namegetmessagewnda--cmfcpopupmenugetmessagewnd"></a><a name="getmessagewnd"></a>CMFCPopupMenu::GetMessageWnd  
 Devuelve un puntero a la ventana donde el marco de trabajo enruta los mensajes de menú emergente.  
  
```  
CWnd* GetMessageWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana que recibe los mensajes de menú emergente; `NULL` si no hay ninguna ventana.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se utiliza el método [CMFCPopupMenu::Create](#create) para crear un menú emergente, debe especificar qué ventana recibe los mensajes de menú.  
  
##  <a name="a-namegetparentareaa--cmfcpopupmenugetparentarea"></a><a name="getparentarea"></a>CMFCPopupMenu::GetParentArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetParentArea(CRect& rectParentBtn);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectParentBtn`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparentbuttona--cmfcpopupmenugetparentbutton"></a><a name="getparentbutton"></a>CMFCPopupMenu::GetParentButton  
 Devuelve un puntero al botón de barra de herramientas primario.  
  
```  
CMFCToolBarMenuButton* GetParentButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al botón de barra de herramientas primario. `NULL`Si el menú emergente no tiene ningún botón de barra de herramientas primario.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCPopupMenu` se puede asociar con un botón en el menú. En este escenario, el menú emergente aparece cuando un usuario selecciona el botón de barra de herramientas primario.  
  
 Si el menú emergente es un menú contextual, no tendrá ningún botón de barra de herramientas primario.  
  
##  <a name="a-namegetparentpopupmenua--cmfcpopupmenugetparentpopupmenu"></a><a name="getparentpopupmenu"></a>CMFCPopupMenu::GetParentPopupMenu  
 Devuelve un puntero al menú emergente primario.  
  
```  
CMFCPopupMenu* GetParentPopupMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al elemento primario `CMFCPopupMenu` objeto; `NULL` si no hay ningún menú emergente del elemento primario.  
  
### <a name="remarks"></a>Comentarios  
 Un menú emergente tiene un elemento primario `CMFCPopupMenu` objeto sólo si es un submenú.  
  
##  <a name="a-namegetparentribbonelementa--cmfcpopupmenugetparentribbonelement"></a><a name="getparentribbonelement"></a>CMFCPopupMenu::GetParentRibbonElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCRibbonBaseElement* GetParentRibbonElement() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetparenttoolbara--cmfcpopupmenugetparenttoolbar"></a><a name="getparenttoolbar"></a>CMFCPopupMenu::GetParentToolBar  
 Devuelve un puntero a la barra de herramientas primario.  
  
```  
CMFCToolBar* GetParentToolBar() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la barra de herramientas primario. `NULL`Si el menú emergente no tiene ninguna barra de herramientas principal.  
  
### <a name="remarks"></a>Comentarios  
 Si la `CMFCPopupMenu` es un menú contextual y, a continuación, no se tiene ninguna barra de herramientas principal.  
  
##  <a name="a-namegetquickcustomizetypea--cmfcpopupmenugetquickcustomizetype"></a><a name="getquickcustomizetype"></a>CMFCPopupMenu::GetQuickCustomizeType  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
QUICK_CUSTOMIZE_TYPE GetQuickCustomizeType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetselitema--cmfcpopupmenugetselitem"></a><a name="getselitem"></a>CMFCPopupMenu::GetSelItem  
 Devuelve un puntero al comando de menú seleccionado.  
  
```  
CMFCToolBarMenuButton* GetSelItem();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al comando de menú seleccionado actualmente; `NULL` si se selecciona ningún elemento.  
  
### <a name="remarks"></a>Comentarios  
 Los comandos de menú en un menú emergente se representan mediante la [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md), o una clase derivada de `CMFCToolBarMenuButton`.  
  
##  <a name="a-namehasbeenresizeda--cmfcpopupmenuhasbeenresized"></a><a name="hasbeenresized"></a>CMFCPopupMenu::HasBeenResized  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL HasBeenResized() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehiderarelyusedcommandsa--cmfcpopupmenuhiderarelyusedcommands"></a><a name="hiderarelyusedcommands"></a>CMFCPopupMenu::HideRarelyUsedCommands  
 Indica si el menú emergente puede ocultar comandos usados con poca frecuencia.  
  
```  
BOOL HideRarelyUsedCommands() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú emergente puede ocultar los comandos que se usan con poca frecuencia; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método especifica sólo si se puede ocultar un menú emergente rara vez utiliza comandos, no si se habilita esta configuración. Un menú emergente puede ocultar comandos poco usados, si tiene un botón primario y se deriva de la ventana primaria del [CMFCMenuBar clase](../../mfc/reference/cmfcmenubar-class.md). Utilice [CMFCMenuBar::SetRecentlyUsedMenus](../../mfc/reference/cmfcmenubar-class.md#setrecentlyusedmenus) para habilitar esta característica y [CMFCMenuBar::IsRecentlyUsedMenus](../../mfc/reference/cmfcmenubar-class.md#isrecentlyusedmenus) para determinar si esta característica está habilitada actualmente. Debe llamar a ambos métodos para la ventana primaria.  
  
##  <a name="a-nameincommanda--cmfcpopupmenuincommand"></a><a name="incommand"></a>CMFCPopupMenu::InCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL InCommand();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameinsertitema--cmfcpopupmenuinsertitem"></a><a name="insertitem"></a>CMFCPopupMenu::InsertItem  
 Inserta un nuevo elemento en el menú emergente en la ubicación especificada.  
  
```  
int InsertItem(
    const CMFCToolBarMenuButton& button,  
    int iInsertA = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `button`  
 Una referencia al elemento de menú para agregar.  
  
 [in] `iInsertAt`  
 Índice de base cero para el nuevo elemento. Si `iInsertAt` es -1, el elemento se agrega al final del menú.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición donde se insertó el elemento. -1 si se produce un error en el método.  
  
### <a name="remarks"></a>Comentarios  
 Este método se producirá un error si proporciona un valor no válido para `iInsertAt`, por ejemplo, un entero mayor que el número de elementos en el menú emergente.  
  
##  <a name="a-nameinsertseparatora--cmfcpopupmenuinsertseparator"></a><a name="insertseparator"></a>CMFCPopupMenu::InsertSeparator  
 Inserta un separador en el menú emergente en la ubicación especificada.  
  
```  
int InsertSeparator(int iInsertAt = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iInsertAt`  
 Índice de base cero de la posición donde este método insertará el separador.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la posición donde se insertó el separador. -1 si se produce un error en este método.  
  
### <a name="remarks"></a>Comentarios  
 Un valor de -1 para `iInsertAt` significa que este método agregará el separador al final del menú emergente.  
  
 Este método produce un error si `iInsertAt` es un valor no válido.  
  
##  <a name="a-nameisalwaysclosea--cmfcpopupmenuisalwaysclose"></a><a name="isalwaysclose"></a>CMFCPopupMenu::IsAlwaysClose  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsAlwaysClose() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisalwaysshowemptytoolsentrya--cmfcpopupmenuisalwaysshowemptytoolsentry"></a><a name="isalwaysshowemptytoolsentry"></a>CMFCPopupMenu::IsAlwaysShowEmptyToolsEntry  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static BOOL __stdcall IsAlwaysShowEmptyToolsEntry();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiscustomizepanea--cmfcpopupmenuiscustomizepane"></a><a name="iscustomizepane"></a>CMFCPopupMenu::IsCustomizePane  
 Indica si el menú emergente está funcionando como un **QuickCustomizePane**.  
  
```  
BOOL IsCustomizePane();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el elemento emergente es una **QuckCustomizePane**; en caso contrario `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la **QuickCustomizePane** para permitir al usuario personalizar directamente el menú emergente. El **QuickCustomizePane** es un `CMFCPopupMenu` que aparece cuando el usuario hace clic en un botón de barra de herramientas para editarlo directamente.  
  
 La aplicación debe llamar a este método durante la [CMDIFrameWndEx::OnShowCustomizePane](../../mfc/reference/cmdiframewndex-class.md#onshowcustomizepane).  
  
##  <a name="a-nameisescclosea--cmfcpopupmenuisescclose"></a><a name="isescclose"></a>CMFCPopupMenu::IsEscClose  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsEscClose();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisidlea--cmfcpopupmenuisidle"></a><a name="isidle"></a>CMFCPopupMenu::IsIdle  
 Indica si un menú emergente está inactivo.  
  
```  
virtual BOOL IsIdle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú emergente está en modo inactivo; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un menú emergente está en modo inactivo si la animación de presentación está completa y el usuario desplaza el menú emergente.  
  
##  <a name="a-nameismenusounda--cmfcpopupmenuismenusound"></a><a name="ismenusound"></a>CMFCPopupMenu::IsMenuSound  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static UINT __stdcall IsMenuSound();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisquickcustomizea--cmfcpopupmenuisquickcustomize"></a><a name="isquickcustomize"></a>CMFCPopupMenu::IsQuickCustomize  
 Determina si el asociado [CMFCToolBarMenuButton clase](../../mfc/reference/cmfctoolbarmenubutton-class.md) está en modo de QuickCustomize.  
  
```  
BOOL IsQuickCustomize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón de menú asociado está en modo de QuickCustomize; de lo contrario, `FALSE`. Este método también devuelve `FALSE` si el menú emergente no está asociado con un `CMFCToolBarMenuButton`.  
  
### <a name="remarks"></a>Comentarios  
 En QuickCustomize modo el usuario selecciona un botón de una barra de herramientas para personalizar el botón directamente.  
  
##  <a name="a-nameisresizeblea--cmfcpopupmenuisresizeble"></a><a name="isresizeble"></a>CMFCPopupMenu::IsResizeble  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsResizeble() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisrightaligna--cmfcpopupmenuisrightalign"></a><a name="isrightalign"></a>CMFCPopupMenu::IsRightAlign  
 Indica si el menú está alineado a la derecha o alineado a la izquierda.  
  
```  
BOOL IsRightAlign() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el menú está alineado a la derecha; `FALSE` si el menú alineado a la izquierda.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar [CMFCPopupMenu::SetRightAlign](#setrightalign) para establecer la alineación de los menús. De forma predeterminada, los menús emergentes utilizan alineación a la izquierda.  
  
 Alineación de los menús no es una configuración global y puede variar entre los menús emergentes.  
  
##  <a name="a-nameisscrollablea--cmfcpopupmenuisscrollable"></a><a name="isscrollable"></a>CMFCPopupMenu::IsScrollable  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsScrollable() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameissendmenuselectmsga--cmfcpopupmenuissendmenuselectmsg"></a><a name="issendmenuselectmsg"></a>CMFCPopupMenu::IsSendMenuSelectMsg  
 Indica si el marco de trabajo notifica el marco primario cuando el usuario selecciona un comando en el menú emergente.  
  
```  
static BOOL IsSendMenuSelectMsg();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco de trabajo notifica el marco primario; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo notifica el marco primario enviándole el `WM_MENUSELECT` el mensaje cuando selecciona un utiliza un comando de menú.  
  
##  <a name="a-nameisshowna--cmfcpopupmenuisshown"></a><a name="isshown"></a>CMFCPopupMenu::IsShown  
 Indica si el menú emergente es visible actualmente.  
  
```  
BOOL IsShown() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un menú emergente es visible; de lo contrario, `FALSE`.  
  
##  <a name="a-namemovetoa--cmfcpopupmenumoveto"></a><a name="moveto"></a>CMFCPopupMenu::MoveTo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void MoveTo(const CPoint& pt);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchangehota--cmfcpopupmenuonchangehot"></a><a name="onchangehot"></a>CMFCPopupMenu::OnChangeHot  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChangeHot(int nHot);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nHot`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchooseitema--cmfcpopupmenuonchooseitem"></a><a name="onchooseitem"></a>CMFCPopupMenu::OnChooseItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnChooseItem(UINT uidCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uidCmdID`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoncmdmsga--cmfcpopupmenuoncmdmsg"></a><a name="oncmdmsg"></a>CMFCPopupMenu::OnCmdMsg  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nID`  
 [in] `nCode`  
 [in] `pExtra`  
 [in] `pHandlerInfo`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepostcommanda--cmfcpopupmenupostcommand"></a><a name="postcommand"></a>CMFCPopupMenu::PostCommand  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL PostCommand(UINT uiCommandID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCommandID`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepretranslatemessagea--cmfcpopupmenupretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCPopupMenu::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerecalclayouta--cmfcpopupmenurecalclayout"></a><a name="recalclayout"></a>CMFCPopupMenu::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNotify`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameremoveallitemsa--cmfcpopupmenuremoveallitems"></a><a name="removeallitems"></a>CMFCPopupMenu::RemoveAllItems  
 Borra todos los elementos de un menú emergente.  
  
```  
void RemoveAllItems();
```  
  
##  <a name="a-nameremoveitema--cmfcpopupmenuremoveitem"></a><a name="removeitem"></a>CMFCPopupMenu::RemoveItem  
 Quita el elemento especificado en el menú emergente.  
  
```  
BOOL RemoveItem(int iIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iIndex`  
 Índice de base cero del elemento que se va a eliminar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método organiza automáticamente los separadores que se ven afectados por la eliminación de un elemento. Para obtener más información acerca de cómo el marco de trabajo reorganiza separadores, consulte [CMFCToolBar::RemoveButton](../../mfc/reference/cmfctoolbar-class.md#removebutton).  
  
##  <a name="a-namesavestatea--cmfcpopupmenusavestate"></a><a name="savestate"></a>CMFCPopupMenu::SaveState  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SaveState();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetanimationspeeda--cmfcpopupmenusetanimationspeed"></a><a name="setanimationspeed"></a>CMFCPopupMenu::SetAnimationSpeed  
 Establece la velocidad de animación de menús emergentes.  
  
```  
static void SetAnimationSpeed(UINT nElapse);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nElapse`  
 La nueva velocidad de animación, en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 La velocidad de animación es un valor global y afecta a todos los menús emergentes en la aplicación. Este valor especifica cuánto tiempo tarda la animación de un menú emergente a finalizar.  
  
 De forma predeterminada, este parámetro se establece en 30 milisegundos. El intervalo de valores válidos para `nElapse` es de 0 a 200.  
  
##  <a name="a-namesetanimationtypea--cmfcpopupmenusetanimationtype"></a><a name="setanimationtype"></a>CMFCPopupMenu::SetAnimationType  
 Establece el tipo de animación de este menú emergente.  
  
```  
static void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `type`  
 Tipo de datos enumerado que especifica el tipo de animación.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [CMFCPopupMenu::GetAnimationType](#getanimationtype) para obtener una lista de valores válidos para `type`.  
  
##  <a name="a-namesetautodestroya--cmfcpopupmenusetautodestroy"></a><a name="setautodestroy"></a>CMFCPopupMenu::SetAutoDestroy  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroy`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdefaultitema--cmfcpopupmenusetdefaultitem"></a><a name="setdefaultitem"></a>CMFCPopupMenu::SetDefaultItem  
 Establece el comando predeterminado para el menú emergente.  
  
```  
void SetDefaultItem(UINT uiCmd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiCmd`  
 El identificador de comando de menú del nuevo comando de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 El comando predeterminado en el menú emergente es el comando que está seleccionado cuando aparezca el menú emergente.  
  
##  <a name="a-namesetforcemenufocusa--cmfcpopupmenusetforcemenufocus"></a><a name="setforcemenufocus"></a>CMFCPopupMenu::SetForceMenuFocus  
 Fuerza el foco de entrada para volver al menú de barra cuando se muestra un menú emergente.  
  
```  
static void SetForceMenuFocus(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
 `TRUE`Si desea que el marco de trabajo para forzar el foco de entrada a la barra de menú cuando un menú emergente se muestra. `FALSE`Si desea que el menú emergente para conservar el foco.  
  
### <a name="remarks"></a>Comentarios  
 Este método establece una marca que es global para todos los menús emergentes en la aplicación. De forma predeterminada, esta característica no está habilitada.  
  
##  <a name="a-namesetforceshadowa--cmfcpopupmenusetforceshadow"></a><a name="setforceshadow"></a>CMFCPopupMenu::SetForceShadow  
 Fuerza el marco de menú dibujar sombras cuando aparecen los menús emergentes fuera del marco principal.  
  
```  
static void SetForceShadow(BOOL bValue);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bValue`  
 `TRUE`Si desea que el marco de menú dibujar sombras, `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a este método, Establece una marca global de la aplicación. Este indicador afecta a todos los menús emergentes en la aplicación.  
  
##  <a name="a-namesetmaxwidtha--cmfcpopupmenusetmaxwidth"></a><a name="setmaxwidth"></a>CMFCPopupMenu::SetMaxWidth  
 Establezca el ancho máximo para el menú emergente.  
  
```  
void SetMaxWidth(int iMaxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iMaxWidth`  
 El ancho máximo para el menú emergente, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Si el texto asociado a un comando de menú no cabe en el ancho máximo, se trunca y se reemplaza la parte que no se ajusta por tres puntos.  
  
##  <a name="a-namesetmessagewnda--cmfcpopupmenusetmessagewnd"></a><a name="setmessagewnd"></a>CMFCPopupMenu::SetMessageWnd  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetMessageWnd(CWnd* pMsgWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsgWnd`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetparentribbonelementa--cmfcpopupmenusetparentribbonelement"></a><a name="setparentribbonelement"></a>CMFCPopupMenu::SetParentRibbonElement  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetParentRibbonElement(CMFCRibbonBaseElement* pElem);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pElem`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetquickcustomizetypea--cmfcpopupmenusetquickcustomizetype"></a><a name="setquickcustomizetype"></a>CMFCPopupMenu::SetQuickCustomizeType  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetQuickCustomizeType(QUICK_CUSTOMIZE_TYPE Type);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `Type`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetquickmodea--cmfcpopupmenusetquickmode"></a><a name="setquickmode"></a>CMFCPopupMenu::SetQuickMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void SetQuickMode();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetrightaligna--cmfcpopupmenusetrightalign"></a><a name="setrightalign"></a>CMFCPopupMenu::SetRightAlign  
 Establece la alineación de menú para los menús emergentes.  
  
```  
void SetRightAlign(BOOL bRightAlign = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bRightAlign`  
 Valor booleano que indica la alineación de los menús. `TRUE`indica la alineación a la derecha, `FALSE` indica la alineación a la izquierda.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, todos los menús emergentes están alineados a la izquierda.  
  
##  <a name="a-namesetsendmenuselectmsga--cmfcpopupmenusetsendmenuselectmsg"></a><a name="setsendmenuselectmsg"></a>CMFCPopupMenu::SetSendMenuSelectMsg  
 Establece un indicador que controla si el menú emergente notifica su marco primario cuando el usuario selecciona un comando.  
  
```  
static void SetSendMenuSelectMsg(BOOL bSet = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSet`  
 `TRUE`Si el menú emergente notifica su marco primario, `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una opción global para todos los menús emergentes en una aplicación. Si está habilitada, los menús emergentes enviará un `WM_MENUSELECT` mensaje al marco primario cuando el usuario selecciona un comando.  
  
##  <a name="a-nameshowallcommandsa--cmfcpopupmenushowallcommands"></a><a name="showallcommands"></a>CMFCPopupMenu::ShowAllCommands  
 Fuerza el menú emergente para mostrar todos los comandos.  
  
```  
void ShowAllCommands();
```  
  
### <a name="remarks"></a>Comentarios  
 Esto no es una configuración global y afecta sólo al menú emergente actual.  
  
##  <a name="a-nametriggerresizea--cmfcpopupmenutriggerresize"></a><a name="triggerresize"></a>CMFCPopupMenu::TriggerResize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void TriggerResize();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameupdateallshadowsa--cmfcpopupmenuupdateallshadows"></a><a name="updateallshadows"></a>CMFCPopupMenu::UpdateAllShadows  
 Actualiza las sombras para todos los menús emergentes abiertos.  
  
```  
static void UpdateAllShadows(LPRECT lprectScreen = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lprectScreen`  
 Un rectángulo que especifica la región de actualización, en coordenadas de pantalla.  
  
### <a name="remarks"></a>Comentarios  
 Este método es útil cuando se muestran los menús emergentes sobre controles animados u otras ventanas que tienen contenido dinámico.  
  
##  <a name="a-nameupdateshadowa--cmfcpopupmenuupdateshadow"></a><a name="updateshadow"></a>CMFCPopupMenu::UpdateShadow  
 Actualiza la sombra para el menú emergente.  
  
```  
void UpdateShadow(LPRECT lprectScreen = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lprectScreen`  
 Un rectángulo, en coordenadas de pantalla, que especifica los límites de la región de actualización.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método cuando un menú emergente que tiene una sombra superpone a una imagen animada.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

