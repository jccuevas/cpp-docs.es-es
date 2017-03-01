---
title: Clase CMFCBaseTabCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseTabCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseTabCtrl class
ms.assetid: 7270c55f-6f6e-4dd2-b0d2-291afeac3882
caps.latest.revision: 41
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d82cde70595bf6d7a4629f54cc48e2b422cd5e8c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasetabctrl-class"></a>Clase CMFCBaseTabCtrl
Implementa la funcionalidad básica para las ventanas con pestañas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCBaseTabCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::AddIcon](#addicon)||  
|[CMFCBaseTabCtrl::AddTab](#addtab)|Agrega una pestaña nueva a la ventana con pestañas.|  
|[CMFCBaseTabCtrl::ApplyRestoredTabInfo](#applyrestoredtabinfo)||  
|[CMFCBaseTabCtrl::AutoDestroyWindow](#autodestroywindow)||  
|[CMFCBaseTabCtrl::CalcRectEdit](#calcrectedit)||  
|[CMFCBaseTabCtrl::CleanUp](#cleanup)||  
|[CMFCBaseTabCtrl::ClearImageList](#clearimagelist)||  
|[CMFCBaseTabCtrl::DetachTab](#detachtab)|Desasocia una pestaña de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::EnableActivateLastActive](#enableactivatelastactive)||  
|[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)|Habilita o deshabilita el coloreado automático de las pestañas.|  
|[CMFCBaseTabCtrl::EnableCustomToolTips](#enablecustomtooltips)|Habilita o deshabilita la información sobre herramientas personalizada para las pestañas.|  
|[CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Habilita o deshabilita la edición directa de etiquetas de pestaña.|  
|[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)|Habilita la capacidad de desasociar pestañas.|  
|[CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap)|Permite o no que el usuario cambie el orden de las pestañas con el mouse.|  
|[CMFCBaseTabCtrl::EnsureVisible](#ensurevisible)|Desplaza las pestañas hasta que la pestaña especificada sea visible. Este método no tiene ningún efecto si la pestaña especificada ya es visible.|  
|[CMFCBaseTabCtrl::EnterDragMode](#enterdragmode)||  
|[CMFCBaseTabCtrl::FindTargetWnd](#findtargetwnd)|Devuelve un panel que contiene un punto especificado.|  
|[CMFCBaseTabCtrl::FireChangeActiveTab](#firechangeactivetab)||  
|[CMFCBaseTabCtrl::FireChangingActiveTab](#firechangingactivetab)||  
|[CMFCBaseTabCtrl::GetActiveTab](#getactivetab)|Devuelve el índice de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveTabColor](#getactivetabcolor)|Devuelve el color de fondo de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveTabTextColor](#getactivetabtextcolor)|Devuelve el color del texto de la pestaña activa.|  
|[CMFCBaseTabCtrl::GetActiveWnd](#getactivewnd)|Devuelve un puntero a la página activa del control de pestañas.|  
|[CMFCBaseTabCtrl::GetAutoColors](#getautocolors)|Devuelve una referencia a la matriz de colores que se usan para el coloreado automático.|  
|[CMFCBaseTabCtrl::GetFirstVisibleTab](#getfirstvisibletab)|Devuelve un puntero a la primera pestaña visible.|  
|[CMFCBaseTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)||  
|[CMFCBaseTabCtrl::GetHighlightedTab](#gethighlightedtab)|Devuelve el índice de la pestaña resaltada actualmente.|  
|[CMFCBaseTabCtrl::GetImageList](#getimagelist)||  
|[CMFCBaseTabCtrl::GetImageSize](#getimagesize)||  
|[CMFCBaseTabCtrl::GetLastVisibleTab](#getlastvisibletab)||  
|[CMFCBaseTabCtrl::GetLocation](#getlocation)|Devuelve una variable del tipo de datos LOCATION, que indica dónde se sitúa el área de pestañas en relación con el control de pestaña. Por ejemplo, en la parte superior o en la parte inferior.|  
|[CMFCBaseTabCtrl::GetMaxWindowSize](#getmaxwindowsize)||  
|[CMFCBaseTabCtrl::GetTabArea](#gettabarea)|Devuelve el tamaño y la posición del área de pestañas de la ventana con pestañas. La posición del área de pestañas se define con coordenadas.|  
|[CMFCBaseTabCtrl::GetTabBkColor](#gettabbkcolor)|Devuelve el color de fondo de la pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabBorderSize](#gettabbordersize)|Devuelve el tamaño de los bordes de la pestaña en el control de pestaña.|  
|[CMFCBaseTabCtrl::GetTabByID](#gettabbyid)|Devuelve el índice de la pestaña que se identifica con un id. especificado.|  
|[CMFCBaseTabCtrl::GetTabCloseButton](#gettabclosebutton)||  
|[CMFCBaseTabCtrl::GetTabFromHwnd](#gettabfromhwnd)|Devuelve el índice de una pestaña que contiene un objeto HWND especificado.|  
|[CMFCBaseTabCtrl::GetTabFromPoint](#gettabfrompoint)|Devuelve la pestaña que contiene un punto especificado.|  
|[CMFCBaseTabCtrl::GetTabFullWidth](#gettabfullwidth)||  
|[CMFCBaseTabCtrl::GetTabHicon](#gettabhicon)|Devuelve el icono asociado a la pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabID](#gettabid)|Devuelve el id. de una pestaña con el índice de la pestaña.|  
|[CMFCBaseTabCtrl::GetTabIcon](#gettabicon)|Devuelve el id. del icono de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabLabel](#gettablabel)|Devuelve el texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabRect](#gettabrect)|Recupera el tamaño y la posición de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabsHeight](#gettabsheight)||  
|[CMFCBaseTabCtrl::GetTabsRect](#gettabsrect)||  
|[CMFCBaseTabCtrl::GetTabTextColor](#gettabtextcolor)|Devuelve el color del texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabWnd](#gettabwnd)|Devuelve el puntero a un panel que se encuentra en una pestaña especificada.|  
|[CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper)|Devuelve el puntero directo a un control que se encuentra en una pestaña especificada, incluso si el control tiene un contenedor.|  
|[CMFCBaseTabCtrl::GetTabsNum](#gettabsnum)|Devuelve el número de pestañas que se encuentran en el control de pestaña.|  
|[CMFCBaseTabCtrl::GetToolTipCtrl](#gettooltipctrl)|Devuelve una referencia al control de información sobre herramientas asociado al objeto `CMFCBaseTabCtrl` .|  
|[CMFCBaseTabCtrl::GetVisibleTabsNum](#getvisibletabsnum)|Devuelve el número de pestañas visibles.|  
|[CMFCBaseTabCtrl::HasImage](#hasimage)||  
|[CMFCBaseTabCtrl::HideSingleTab](#hidesingletab)|Establece una opción que oculta la pestaña de una ventana, pero solo si la ventana con pestañas muestra una sola pestaña visible.|  
|[CMFCBaseTabCtrl::InsertTab](#inserttab)|Inserta una pestaña nueva.|  
|[CMFCBaseTabCtrl::InvalidateTab](#invalidatetab)||  
|[CMFCBaseTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)||  
|[CMFCBaseTabCtrl::IsAutoColor](#isautocolor)|Devuelve un valor que indica si una ventana con pestañas está en modo de color automático.|  
|[CMFCBaseTabCtrl::IsAutoDestroyWindow](#isautodestroywindow)||  
|[CMFCBaseTabCtrl::IsColored](#iscolored)||  
|[CMFCBaseTabCtrl::IsDialogControl](#isdialogcontrol)||  
|[CMFCBaseTabCtrl::IsDrawNoPrefix](#isdrawnoprefix)||  
|[CMFCBaseTabCtrl::IsFlatFrame](#isflatframe)|Devuelve un valor que indica si el formato del marco del área de pestañas es plano o en 3D.|  
|[CMFCBaseTabCtrl::IsFlatTab](#isflattab)||  
|[CMFCBaseTabCtrl::IsHideSingleTab](#ishidesingletab)|Devuelve un valor que indica si el control de pestaña está configurado para ocultar una pestaña, pero solo si la ventana con pestañas tiene una sola pestaña visible.|  
|[CMFCBaseTabCtrl::IsIconAdded](#isiconadded)||  
|[CMFCBaseTabCtrl::IsInPlaceEdit](#isinplaceedit)|Indica si los usuarios pueden modificar la etiqueta de una pestaña.|  
|[CMFCBaseTabCtrl::IsLeftRightRounded](#isleftrightrounded)||  
|[CMFCBaseTabCtrl::IsMDITab](#ismditab)||  
|[CMFCBaseTabCtrl::IsOneNoteStyle](#isonenotestyle)|Indica si una ventana con pestañas muestra las pestañas con el estilo de Microsoft OneNote.|  
|[CMFCBaseTabCtrl::IsPtInTabArea](#isptintabarea)|Comprueba si existe un punto especificado en el área de pestañas.|  
|[CMFCBaseTabCtrl::IsTabCloseButtonHighlighted](#istabclosebuttonhighlighted)||  
|[CMFCBaseTabCtrl::IsTabCloseButtonPressed](#istabclosebuttonpressed)||  
|[CMFCBaseTabCtrl::IsTabDetachable](#istabdetachable)|Indica si una pestaña se puede desasociar.|  
|[CMFCBaseTabCtrl::IsTabIconOnly](#istabicononly)|Indica si las pestañas muestran iconos pero no etiquetas.|  
|[CMFCBaseTabCtrl::IsTabSwapEnabled](#istabswapenabled)|Indica si el usuario puede cambiar la posición de las pestañas arrastrándolas.|  
|[CMFCBaseTabCtrl::IsTabVisible](#istabvisible)|Indica si una pestaña especificada es visible.|  
|[CMFCBaseTabCtrl::IsVS2005Style](#isvs2005style)||  
|[CMFCBaseTabCtrl::MoveTab](#movetab)||  
|[CMFCBaseTabCtrl::OnChangeTabs](#onchangetabs)|Llamado por el marco cuando cambia el número de pestañas.|  
|[CMFCBaseTabCtrl::OnDragEnter](#ondragenter)||  
|[CMFCBaseTabCtrl::OnDragLeave](#ondragleave)||  
|[CMFCBaseTabCtrl::OnDragOver](#ondragover)||  
|[CMFCBaseTabCtrl::OnDrop](#ondrop)||  
|[CMFCBaseTabCtrl::OnRenameTab](#onrenametab)||  
|[CMFCBaseTabCtrl::PreTranslateMessage](#pretranslatemessage)|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CWnd:: PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCBaseTabCtrl::RecalcLayout](#recalclayout)|Vuelve a calcular el diseño interno de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::RemoveAllTabs](#removealltabs)|Quita todas las pestañas de la ventana con pestañas.|  
|[CMFCBaseTabCtrl::RemoveTab](#removetab)|Quita una pestaña de una ventana con pestañas.|  
|[CMFCBaseTabCtrl::RenameTab](#renametab)||  
|[CMFCBaseTabCtrl::ResetImageList](#resetimagelist)|Restablece la lista de imágenes que se adjunta a una ventana con pestañas.|  
|[CMFCBaseTabCtrl::Serialize](#serialize)|Lee o escribe este objeto de o en un archivo. (Invalida [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCBaseTabCtrl::SetActiveTab](#setactivetab)|Activa una pestaña.|  
|[CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor)|Establece el color de fondo de la pestaña actualmente activa.|  
|[CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor)|Establece el color del texto de las pestañas activas.|  
|[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)|Establece los colores de control de pestaña que se aplican en el modo de color automático.|  
|[CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc)|Establece la clase de contenedor que se utiliza para todos los objetos no derivados de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).|  
|[CMFCBaseTabCtrl::SetDrawNoPrefix](#setdrawnoprefix)|Habilita y deshabilita el procesamiento de caracteres de prefijo cuando se dibujan las etiquetas de la pestaña.|  
|[CMFCBaseTabCtrl::SetImageList](#setimagelist)|Establece la lista de imágenes de iconos.|  
|[CMFCBaseTabCtrl::SetLocation](#setlocation)||  
|[CMFCBaseTabCtrl::SetTabBkColor](#settabbkcolor)|Establece el color de fondo de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize)|Establece un nuevo tamaño de borde de pestaña.|  
|[CMFCBaseTabCtrl::SetTabHicon](#settabhicon)|Establece un icono de pestaña.|  
|[CMFCBaseTabCtrl::SetTabIcon](#settabicon)|Establece un id. de icono de pestaña.|  
|[CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly)|Habilita y deshabilita el modo "solo icono" de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabLabel](#settablabel)|Establece una etiqueta de pestaña igual que un valor de cadena especificado.|  
|[CMFCBaseTabCtrl::SetTabsHeight](#settabsheight)||  
|[CMFCBaseTabCtrl::SetTabTextColor](#settabtextcolor)|Establece el color del texto de una pestaña especificada.|  
|[CMFCBaseTabCtrl::SetTabsOrder](#settabsorder)|Organiza las pestañas en el orden especificado.|  
|[CMFCBaseTabCtrl::ShowTab](#showtab)|Muestra u oculta la pestaña especificada.|  
|[CMFCBaseTabCtrl::StartRenameTab](#startrenametab)||  
|[CMFCBaseTabCtrl::SwapTabs](#swaptabs)||  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)|Crea un contenedor para un objeto derivado de [CWnd](../../mfc/reference/cwnd-class.md) que no se deriva de `CDockablePane`. Para acoplar un objeto `CMFCBaseTabCtrl` , cada control incrustado debe tener un contenedor de acoplamiento o bien debe derivarse de `CDockablePane`.<br /><br /> Establece la clase del contenedor mediante `SetDockingBayWrapperRTC`.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::m_bActivateTabOnRightClick](#m_bactivatetabonrightclick)|Especifica si las pestañas se seleccionan con un clic en el botón izquierdo o secundario del mouse.|  
|[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)|Especifica si los paneles incluidos en las pestañas se destruyen automáticamente.|  
  
## <a name="remarks"></a>Comentarios  
 La clase `CMFCBaseTabCtrl` es abstracta. Por lo tanto, no se pueden crear instancias en ella. Para crear una ventana con pestañas, debe derivar una clase de `CMFCBaseTabCtrl`. La biblioteca MFC contiene algunos ejemplos de la clase derivada, dos de los cuales son [CMFCTabCtrl clase](../../mfc/reference/cmfctabctrl-class.md) y [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md).  
  
 A partir de [!INCLUDE[vs_dev14](../../ide/includes/vs_dev14_md.md)], esta clase es compatible con Microsoft Active Accessibility.  
  
## <a name="customization-tips"></a>Sugerencias de personalización  
 Las sugerencias siguientes pertenecen a la `CMFCBaseTabCtrl Class` y todas las clases que heredan de él:  
  
-   Si permite que las pestañas se puedan desasociar, no mantenga los punteros a las ventanas con pestañas. Estas pestañas desasociables se pueden crear y destruir de forma dinámica. Por lo tanto, los punteros pueden quedar invalidados.  
  
-   Puede configurar el control de pestaña para que los usuarios puedan mover las pestañas dinámicamente en un control de pestaña con el mouse. Esta funcionalidad está integrada en la clase `CMFCBaseTabCtrl` . Para habilitarla, llame a [CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap).  
  
-   De forma predeterminada, las pestañas son desasociables al agregarlas a un control de pestaña. También puede agregar pestañas no son separables mediante [CMFCBaseTabCtrl::AddTab](#addtab). Si establece el parámetro `bDetachable` en `FALSE`, la pestaña no se podrá desasociar. También puede cambiar si las fichas son separables llamando al método [CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach).  
  
-   Objetos que se derivan de la [CWnd (clase)](../../mfc/reference/cwnd-class.md) pueden colocarse en una barra de control acoplables o ficha acoplable. Para que todo el control quede acoplado, debe convertir el objeto `CWnd` en acoplable. Para ello, MFC usa una clase contenedora. Esta clase de contenedor es el [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md). Cualquier objeto `CWnd` que se agregue a una barra de control acoplable o a una pestaña acoplable se ajustará dentro de un objeto `CDockablePaneAdapter` . Puede deshabilitar el ajuste automático estableciendo el parámetro `m_bEnableWrapping` del objeto `CMFCBaseTablCtrl` en `FALSE`. También puede cambiar la clase que utilizará la aplicación como un contenedor mediante el método [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxbasetabctrl.h  
  
##  <a name="a-nameaddicona--cmfcbasetabctrladdicon"></a><a name="addicon"></a>CMFCBaseTabCtrl::AddIcon  
 Agrega un icono a la lista de iconos en el modo protegido `CMap``m_mapAddedIcons` miembro.  
  
```  
void AddIcon(
    HICON hIcon,  
    int iIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hIcon`  
 Identificador del icono que se va a agregar.  
  
 [in] `iIcon`  
 Índice de base cero del icono de protegido `CImageList``m_Images` miembro.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameaddtaba--cmfcbasetabctrladdtab"></a><a name="addtab"></a>CMFCBaseTabCtrl::AddTab  
 Agrega una nueva ficha en el control de ficha.  
  
```  
virtual void AddTab(
    CWnd* pTabWnd,  
    LPCTSTR lpszTabLabel,  
    UINT uiImageId = (UINT)-1,,  
    BOOL bDetachable = TRUE);

 
virtual void AddTab(
    CWnd* pTabWnd,  
    UINT uiResTabLabel,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTabWnd`  
 Puntero a la ventana que este método se representa como una nueva pestaña.  
  
 [in] `lpszTabLabel`  
 Cadena que contiene la etiqueta para la nueva ficha.  
  
 [in] `uiImageId`  
 Un identificador de la imagen de la lista de imágenes. El control de ficha utiliza esta imagen como icono de la nueva pestaña.  
  
 [in] `uiResTabLabel`  
 El identificador de recurso para la etiqueta.  
  
 [in] `bDetachable`  
 Parámetro booleano que determina si la nueva ficha es desmontable.  
  
### <a name="remarks"></a>Comentarios  
 Si `pTabWnd` apunta a un objeto que no se deriva el [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) y si `bDetachable` es `TRUE`, framework crea automáticamente un contenedor para el `pTabWnd` objeto. Hace que el contenedor del `pTabWnd` objeto desmontable. De forma predeterminada, el contenedor es una instancia de la [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md). Si la funcionalidad proporcionada por el contenedor predeterminado es aceptable, utilice la [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc) método para especificar un contenedor diferente.  
  
##  <a name="a-nameapplyrestoredtabinfoa--cmfcbasetabctrlapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CMFCBaseTabCtrl::ApplyRestoredTabInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bUseTabIndexes`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameautodestroywindowa--cmfcbasetabctrlautodestroywindow"></a><a name="autodestroywindow"></a>CMFCBaseTabCtrl::AutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AutoDestroyWindow(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroy`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecalcrectedita--cmfcbasetabctrlcalcrectedit"></a><a name="calcrectedit"></a>CMFCBaseTabCtrl::CalcRectEdit  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectEdit`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecleanupa--cmfcbasetabctrlcleanup"></a><a name="cleanup"></a>CMFCBaseTabCtrl::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUp();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameclearimagelista--cmfcbasetabctrlclearimagelist"></a><a name="clearimagelist"></a>CMFCBaseTabCtrl::ClearImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClearImageList();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecreatewrappera--cmfcbasetabctrlcreatewrapper"></a><a name="createwrapper"></a>CMFCBaseTabCtrl::CreateWrapper  
 Crea un contenedor para una ventana de marco que se deriva el [CWnd (clase)](../../mfc/reference/cwnd-class.md) pero no se deriva el [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
```  
virtual CWnd* CreateWrapper(
    CWnd* pWndToWrap,  
    LPCTSTR lpszTabLabel,  
    BOOL bDetachable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndToWrap`  
 Puntero a la ventana de marco que se ajusta.  
  
 [in] `lpszTabLabel`  
 Una cadena que contiene la etiqueta de la ventana.  
  
 [in] `bDetachable`  
 Parámetro booleano que indica si la ventana es desmontable.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al contenedor derivado de la `CDockablePane` clase si `CreateWrapper` correctamente crea una clase contenedora para `pWndToWrap`. Si se produce un error en el método, se devuelve `pWndToWrap`.  
  
### <a name="remarks"></a>Comentarios  
 Una ventana con fichas puede acoplar cualquier objeto derivado de `CWnd`. Sin embargo, en orden para una `CMFCBaseTabCtrl Class` objeto sea acoplable, cada objeto en el `CMFCBaseTabCtrl` debe ser intercambiables. Por lo tanto, `CMFCBaseTabCtrl` ajusta automáticamente los objetos que no se derivan `CDockablePane`.  
  
 De forma predeterminada, el `CMFCBaseTabCtrl` crea instancias de la [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md). Para cambiar la clase de valor predeterminado del contenedor, llame a [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc).  
  
 Si `pWndToWrap` se deriva de `CDockablePane`, este método no creará un contenedor. En su lugar, se producirá un error y devolver `pWndToWrap`.  
  
##  <a name="a-namedetachtaba--cmfcbasetabctrldetachtab"></a><a name="detachtab"></a>CMFCBaseTabCtrl::DetachTab  
 El marco de trabajo llama a este método para separar una ficha del control de ficha.  
  
```  
virtual BOOL DetachTab(
    AFX_DOCK_METHOD dockMethod,  
    int nTabNum = -1,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `dockMethod`  
 Tipo de datos enumerado proporcionado por el [CBasePane clase](../../mfc/reference/cbasepane-class.md). Este tipo de datos especifica el método utilizado para separar la ficha.  
  
 [in] `nTabNum`  
 Índice de base cero de la ficha que se va a desconectar.  
  
 [in] `bHide`  
 Parámetro booleano que indica si el marco de trabajo debe ocultar la ficha desasociada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si la ficha especificada por `nTabNum` es no separable, esta función se produce un error y se devuelve `FALSE`.  
  
##  <a name="a-nameenableactivatelastactivea--cmfcbasetabctrlenableactivatelastactive"></a><a name="enableactivatelastactive"></a>CMFCBaseTabCtrl::EnableActivateLastActive  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableActivateLastActive(BOOL bLastActive = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bLastActive`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenableautocolora--cmfcbasetabctrlenableautocolor"></a><a name="enableautocolor"></a>CMFCBaseTabCtrl::EnableAutoColor  
 Controla si el marco de trabajo usa los colores de fondo automática al dibujar una pestaña.  
  
```  
void EnableAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Parámetro booleano que determina si el marco de trabajo usa colores automáticos.  
  
### <a name="remarks"></a>Comentarios  
 Un control de ficha tiene una matriz de varios colores predefinidos. Cuando el marco de trabajo usa colores automáticos, cada pestaña de una serie de fichas se asigna el siguiente color de esta matriz.  
  
 De forma predeterminada, los colores automático dependen de los colores definidos por la biblioteca. Puede proporcionar una matriz de colores personalizada mediante una llamada a [CMFCBaseTabCtrl::SetAutoColors](#setautocolors).  
  
##  <a name="a-nameenablecustomtooltipsa--cmfcbasetabctrlenablecustomtooltips"></a><a name="enablecustomtooltips"></a>CMFCBaseTabCtrl::EnableCustomToolTips  
 Habilita la información sobre herramientas personalizados para el control de ficha.  
  
```  
BOOL EnableCustomToolTips(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Un valor booleano que determina si se utiliza la información sobre herramientas personalizados.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si se habilita la información sobre herramientas personalizada, el control de ficha envía el `AFX_WM_ON_GET_TAB_TOOLTIP` mensaje al marco principal. Si desea admitir la información sobre herramientas personalizados en la aplicación, la ventana de marco principal debe controlar este método y proporcionar el texto de información sobre herramientas personalizado. Para obtener más información acerca de cómo proporcionar texto de información sobre herramientas personalizada, consulte [CMFCTabToolTipInfo estructura](../../mfc/reference/cmfctabtooltipinfo-structure.md).  
  
##  <a name="a-nameenableinplaceedita--cmfcbasetabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCBaseTabCtrl::EnableInPlaceEdit  
 Permite dirigir la edición de las etiquetas de la pestaña por el usuario.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Parámetro booleano que especifica si se habilita la edición directa de las etiquetas de la ficha.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, la edición directa de las etiquetas de la ficha está deshabilitada para los controles de ficha.  
  
 Puede habilitar la edición directa de un subconjunto de las fichas en el control de ficha. Para ello, reemplace el método `CMFCBaseTabCtrl::StartRenameTab`. `StartRenameTab`debe devolver un valor distinto de cero para todas las pestañas que admiten la edición directa de etiquetas.  
  
 En el `CMFCBaseTabCtrl Class`, este método es una función virtual pura y no tiene ninguna implementación. Si deriva una clase de `CMFCBaseTabCtrl`, debe implementar esta función.  
  
##  <a name="a-nameenabletabdetacha--cmfcbasetabctrlenabletabdetach"></a><a name="enabletabdetach"></a>CMFCBaseTabCtrl::EnableTabDetach  
 Habilita la capacidad de desasociar pestañas.  
  
```  
virtual BOOL EnableTabDetach(
    int iTab,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
 [in] `bEnable`  
 Valor booleano que indica si se debe establecer la ficha desmontable.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
##  <a name="a-nameenabletabswapa--cmfcbasetabctrlenabletabswap"></a><a name="enabletabswap"></a>CMFCBaseTabCtrl::EnableTabSwap  
 Permite al usuario cambiar el orden de tabulación con un mouse.  
  
```  
void EnableTabSwap(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 Valor booleano que indica si se debe permitir el intercambio de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se habilita el intercambio de ficha, el usuario puede arrastrar una pestaña y cambiar su posición relativa en el control de ficha.  
  
##  <a name="a-nameensurevisiblea--cmfcbasetabctrlensurevisible"></a><a name="ensurevisible"></a>CMFCBaseTabCtrl::EnsureVisible  
 Desplaza las pestañas hasta que la pestaña especificada sea visible.  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Este método no tiene ningún efecto si la ficha indicado por `iTab` ya está visible.  
  
 De forma predeterminada, este método no es compatible con la `CMFCBaseTabCtrl Class`. Debe implementar esta función en una clase personalizada derivada de `CMFCBaseTabCtrl` si dicho control de pestaña personalizada admite el desplazamiento de la ficha. Este método es compatible con la [CMFCTabCtrl clase](../../mfc/reference/cmfctabctrl-class.md).  
  
##  <a name="a-nameenterdragmodea--cmfcbasetabctrlenterdragmode"></a><a name="enterdragmode"></a>CMFCBaseTabCtrl::EnterDragMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnterDragMode();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefindtargetwnda--cmfcbasetabctrlfindtargetwnd"></a><a name="findtargetwnd"></a>CMFCBaseTabCtrl::FindTargetWnd  
 Identifica el panel que contiene un punto especificado.  
  
```  
virtual CWnd* FindTargetWnd(const CPoint& pt) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Coordenadas de un punto en el que se define mediante el área de cliente de la [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto si se realiza correctamente; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 En el `CMFCBaseTabCtrl` (clase), este método es una función virtual pura: debe implementar si deriva una clase de `CMFCBaseTabCtrl`.  
  
##  <a name="a-namefirechangeactivetaba--cmfcbasetabctrlfirechangeactivetab"></a><a name="firechangeactivetab"></a>CMFCBaseTabCtrl::FireChangeActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void FireChangeActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nNewTab`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namefirechangingactivetaba--cmfcbasetabctrlfirechangingactivetab"></a><a name="firechangingactivetab"></a>CMFCBaseTabCtrl::FireChangingActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL FireChangingActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nNewTab`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetactivetaba--cmfcbasetabctrlgetactivetab"></a><a name="getactivetab"></a>CMFCBaseTabCtrl::GetActiveTab  
 Recupera el índice de la ficha activa.  
  
```  
virtual int GetActiveTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha activa; -1 si no hay ninguna ficha activa.  
  
##  <a name="a-namegetactivetabcolora--cmfcbasetabctrlgetactivetabcolor"></a><a name="getactivetabcolor"></a>CMFCBaseTabCtrl::GetActiveTabColor  
 Recupera el color de fondo de la ficha activa.  
  
```  
virtual COLORREF GetActiveTabColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que especifica el color de fondo de la ficha activa.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el color de fondo de la ficha activa es `COLOR_WINDOW`. Puede cambiar el color de fondo de la ficha activa mediante el método [CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor).  
  
##  <a name="a-namegetactivetabtextcolora--cmfcbasetabctrlgetactivetabtextcolor"></a><a name="getactivetabtextcolor"></a>CMFCBaseTabCtrl::GetActiveTabTextColor  
 Recupera el color del texto de la ficha activa.  
  
```  
virtual COLORREF GetActiveTabTextColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que especifica el color del texto de la ficha activa.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, es el color del texto de fichas active `COLOR_WINDOWTEXT`. Puede cambiar el color del texto con el método [CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor).  
  
##  <a name="a-namegetactivewnda--cmfcbasetabctrlgetactivewnd"></a><a name="getactivewnd"></a>CMFCBaseTabCtrl::GetActiveWnd  
 Recupera un puntero a la ventana de la ficha activa.  
  
```  
virtual CWnd* GetActiveWnd() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a una ventana.  
  
##  <a name="a-namegetautocolorsa--cmfcbasetabctrlgetautocolors"></a><a name="getautocolors"></a>CMFCBaseTabCtrl::GetAutoColors  
 Recupera la matriz de colores utilizados para los colores automáticos.  
  
```  
const CArray<COLORREF,COLORREF>& GetAutoColors() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a una matriz de [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valores que el [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto se utiliza para seleccionar el color de ficha automática.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo inicializa la matriz de colores de colores definidos por la biblioteca. Puede proporcionar una matriz de colores personalizada llamando al método [CMFCBaseTabCtrl::SetAutoColors](#setautocolors).  
  
##  <a name="a-namegetfirstvisibletaba--cmfcbasetabctrlgetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CMFCBaseTabCtrl::GetFirstVisibleTab  
 Recupera un puntero a la primera pestaña visible.  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);

 
virtual CWnd* GetFirstVisibleTab(
    int iStartFrom,  
    int& iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `iTabNum`  
 Una referencia a un entero. Este método escribe el índice de base cero de la primera ficha visible para este parámetro.  
  
 [in] `iStartFrom`  
 Índice de base cero de la primera ficha comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la primera pestaña visible si es correcto; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en este método, escriba el valor -1 para `iStartFrom`.  
  
 Si `iStartFrom` es mayor o igual que el número de fichas del control de ficha, `GetFirstVisibleTab` automáticamente se produce un error.  
  
##  <a name="a-namegetfirstvisibletabnuma--cmfcbasetabctrlgetfirstvisibletabnum"></a><a name="getfirstvisibletabnum"></a>CMFCBaseTabCtrl::GetFirstVisibleTabNum  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegethighlightedtaba--cmfcbasetabctrlgethighlightedtab"></a><a name="gethighlightedtab"></a>CMFCBaseTabCtrl::GetHighlightedTab  
 Recupera el índice de la ficha resaltada.  
  
```  
int GetHighlightedTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha resaltada.  
  
##  <a name="a-namegetimagelista--cmfcbasetabctrlgetimagelist"></a><a name="getimagelist"></a>CMFCBaseTabCtrl::GetImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual const CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetimagesizea--cmfcbasetabctrlgetimagesize"></a><a name="getimagesize"></a>CMFCBaseTabCtrl::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetlastvisibletaba--cmfcbasetabctrlgetlastvisibletab"></a><a name="getlastvisibletab"></a>CMFCBaseTabCtrl::GetLastVisibleTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetLastVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTabNum`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetlocationa--cmfcbasetabctrlgetlocation"></a><a name="getlocation"></a>CMFCBaseTabCtrl::GetLocation  
 Recupera la ubicación de la parte del área de ficha del control de ficha.  
  
```  
Location GetLocation() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ubicación del área de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Ficha posibles valores de ubicación de área son `LOCATION_BOTTOM` y `LOCATION_TOP`.  
  
##  <a name="a-namegetmaxwindowsizea--cmfcbasetabctrlgetmaxwindowsize"></a><a name="getmaxwindowsize"></a>CMFCBaseTabCtrl::GetMaxWindowSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetMaxWindowSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabareaa--cmfcbasetabctrlgettabarea"></a><a name="gettabarea"></a>CMFCBaseTabCtrl::GetTabArea  
 Recupera el tamaño y posición del área de ficha del control de ficha.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectTabAreaTop`  
 Referencia a un objeto `CRect`. `GetTabArea`Este objeto se utiliza para almacenar el tamaño y posición del área de ficha superior.  
  
 [in] `rectTabAreaBottom`  
 Referencia a un objeto `CRect`. `GetTabArea`Este objeto se utiliza para almacenar el tamaño y posición del área de ficha inferior.  
  
### <a name="remarks"></a>Comentarios  
 Después de `GetTabArea` devuelve un valor, el `CRect` parámetros contienen el tamaño y posición del área de ficha en coordenadas de cliente del control de ficha. Si no hay ningún área de la ficha en la parte superior o inferior del control de ficha, `rectTabAreaTop` o `rectTabAreaBottom` están vacíos.  
  
 En el `CMFCBaseTabCtrl Class`, este método es una función virtual pura y no tiene ninguna implementación. Si deriva una clase de `CMFCBaseTabCtrl`, que tiene que implementar esta función.  
  
##  <a name="a-namegettabbkcolora--cmfcbasetabctrlgettabbkcolor"></a><a name="gettabbkcolor"></a>CMFCBaseTabCtrl::GetTabBkColor  
 Recupera el color de fondo de la ficha especificada.  
  
```  
virtual COLORREF GetTabBkColor(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que indica el color de fondo de la ficha especificada; -1 si `iTab` está fuera del intervalo.  
  
##  <a name="a-namegettabbordersizea--cmfcbasetabctrlgettabbordersize"></a><a name="gettabbordersize"></a>CMFCBaseTabCtrl::GetTabBorderSize  
 Recupera el tamaño de los bordes de ficha en el control de ficha.  
  
```  
virtual int GetTabBorderSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del borde de ficha, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño predeterminado para el borde de la ficha es tres píxeles. Puede cambiar el tamaño del borde con el método [CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize).  
  
##  <a name="a-namegettabbyida--cmfcbasetabctrlgettabbyid"></a><a name="gettabbyid"></a>CMFCBaseTabCtrl::GetTabByID  
 Recupera el índice de una pestaña basada en un identificador de ficha.  
  
```  
virtual int GetTabByID(int id) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `id`  
 Un identificador de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de una ficha, si se encuentra; -1 si no se encuentra el identificador de la pestaña.  
  
### <a name="remarks"></a>Comentarios  
 La ficha identificadores se asignan automáticamente cuando se agregan fichas a un control de ficha.  
  
##  <a name="a-namegettabclosebuttona--cmfcbasetabctrlgettabclosebutton"></a><a name="gettabclosebutton"></a>CMFCBaseTabCtrl::GetTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetTabCloseButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabfromhwnda--cmfcbasetabctrlgettabfromhwnd"></a><a name="gettabfromhwnd"></a>CMFCBaseTabCtrl::GetTabFromHwnd  
 Recupera el índice de la pestaña que contiene el objeto HWND especificado.  
  
```  
virtual int GetTabFromHwnd(HWND hwnd) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hwnd`  
 Identificador de una ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de la ficha si es correcto; -1 si ninguna ficha contiene `hwnd`.  
  
##  <a name="a-namegettabfrompointa--cmfcbasetabctrlgettabfrompoint"></a><a name="gettabfrompoint"></a>CMFCBaseTabCtrl::GetTabFromPoint  
 Recupera la ficha que contiene un punto especificado.  
  
```  
virtual int GetTabFromPoint(CPoint& pt) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pt`  
 Un punto en coordenadas de cliente del control de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de la pestaña que contiene `pt`; -1 si ninguna ficha contiene `pt`.  
  
##  <a name="a-namegettabfullwidtha--cmfcbasetabctrlgettabfullwidth"></a><a name="gettabfullwidth"></a>CMFCBaseTabCtrl::GetTabFullWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabFullWidth(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabhicona--cmfcbasetabctrlgettabhicon"></a><a name="gettabhicon"></a>CMFCBaseTabCtrl::GetTabHicon  
 Devuelve el HICON asociado a la ficha especificada.  
  
```  
virtual HICON GetTabHicon(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 HICON asociado a una etiqueta de ficha si es correcto; `NULL` si no hay ningún HICON o si se produce un error en el método.  
  
##  <a name="a-namegettabicona--cmfcbasetabctrlgettabicon"></a><a name="gettabicon"></a>CMFCBaseTabCtrl::GetTabIcon  
 Recupera el icono asociado a la ficha especificada.  
  
```  
virtual UINT GetTabIcon(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del icono de la ficha especificada si se realiza correctamente; -1 si el índice no es válido.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto almacena los iconos en el interno [CImageList](../../mfc/reference/cimagelist-class.md) objeto.  
  
##  <a name="a-namegettabida--cmfcbasetabctrlgettabid"></a><a name="gettabid"></a>CMFCBaseTabCtrl::GetTabID  
 Recupera el identificador de una ficha especificada por el índice de tabulación.  
  
```  
int GetTabID(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de la ficha o -1 si `iTab` está fuera del intervalo.  
  
##  <a name="a-namegettablabela--cmfcbasetabctrlgettablabel"></a><a name="gettablabel"></a>CMFCBaseTabCtrl::GetTabLabel  
 Recupera el texto de una etiqueta de ficha.  
  
```  
virtual BOOL GetTabLabel(
    int iTab,  
    CString& strLabel) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
 [out] `strLabel`  
 Referencia a un objeto `CString`. Este método almacena la etiqueta de la ficha de este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método produce un error si el índice `iTab` no es válido.  
  
 Establece la etiqueta de una ficha cuando crea la ficha mediante [CMFCBaseTabCtrl::AddTab](#addtab). También puede cambiar la etiqueta después de la creación con el método [CMFCBaseTabCtrl::SetTabLabel](#settablabel).  
  
##  <a name="a-namegettabrecta--cmfcbasetabctrlgettabrect"></a><a name="gettabrect"></a>CMFCBaseTabCtrl::GetTabRect  
 Recupera el tamaño y la posición de la ficha especificada.  
  
```  
virtual BOOL GetTabRect(
    int iTab,  
    CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
 [out] `rect`  
 Referencia a un objeto `CRect`. Este método almacena el tamaño y la posición de la pestaña en este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` si el índice de tabulación no es válido.  
  
##  <a name="a-namegettabsheighta--cmfcbasetabctrlgettabsheight"></a><a name="gettabsheight"></a>CMFCBaseTabCtrl::GetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabsnuma--cmfcbasetabctrlgettabsnum"></a><a name="gettabsnum"></a>CMFCBaseTabCtrl::GetTabsNum  
 Recupera el número de fichas del control de ficha.  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de fichas del control de ficha.  
  
##  <a name="a-namegettabsrecta--cmfcbasetabctrlgettabsrect"></a><a name="gettabsrect"></a>CMFCBaseTabCtrl::GetTabsRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabtextcolora--cmfcbasetabctrlgettabtextcolor"></a><a name="gettabtextcolor"></a>CMFCBaseTabCtrl::GetTabTextColor  
 Recupera el color del texto de la ficha especificada.  
  
```  
virtual COLORREF GetTabTextColor(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto de la ficha especificada; -1 si `iTab` está fuera del intervalo.  
  
##  <a name="a-namegettabwnda--cmfcbasetabctrlgettabwnd"></a><a name="gettabwnd"></a>CMFCBaseTabCtrl::GetTabWnd  
 Devuelve el puntero en el panel que se encuentra en la ficha especificada.  
  
```  
virtual CWnd* GetTabWnd(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto que reside en la ficha que `iTab` especifica. `NULL`Si `iTab` no es válido.  
  
### <a name="remarks"></a>Comentarios  
 El objeto devuelto es la que agregar la aplicación mientras llama [CMFCBaseTabCtrl::AddTab](#addtab) o [CMFCBaseTabCtrl::InsertTab](#inserttab).  
  
 Si el objeto en una ficha tiene un contenedor, este método devolverá el contenedor para el objeto. Para obtener más información acerca de los contenedores, consulte [CMFCBaseTabCtrl::CreateWrapper](#createwrapper). Si desea obtener acceso a un puntero al objeto directa sin el contenedor, utilice el método [CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper).  
  
##  <a name="a-namegettabwndnowrappera--cmfcbasetabctrlgettabwndnowrapper"></a><a name="gettabwndnowrapper"></a>CMFCBaseTabCtrl::GetTabWndNoWrapper  
 Devuelve un puntero al control que reside en una ficha, incluso si el control tiene un contenedor.  
  
```  
virtual CWnd* GetTabWndNoWrapper(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CWnd](../../mfc/reference/cwnd-class.md) objeto que reside en la ficha especificada; `NULL` si `iTab` no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Este método recupera un puntero directo a la `CWnd` de objeto que agregó mediante el método [CMFCBaseTabCtrl::AddTab](#addtab) o [CMFCBaseTabCtrl::InsertTab](#inserttab). `GetTabWndNoWrapper`Recupera un puntero al agregado `CWnd`, incluso si el marco de trabajo agrega un contenedor para el objeto. Para obtener más información acerca de los contenedores y los [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md), consulte [CMFCBaseTabCtrl::CreateWrapper](#createwrapper).  
  
 Utilice el método [CMFCBaseTabCtrl::GetTabWnd](#gettabwnd) si no desea pasar por alto la clase contenedora.  
  
##  <a name="a-namegettooltipctrla--cmfcbasetabctrlgettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCBaseTabCtrl::GetToolTipCtrl  
 Recupera una referencia a la información sobre herramientas de controlar.  
  
```  
CToolTipCtrl& GetToolTipCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al control de información sobre herramientas.  
  
##  <a name="a-namegetvisibletabsnuma--cmfcbasetabctrlgetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CMFCBaseTabCtrl::GetVisibleTabsNum  
 Recupera el número de fichas actualmente visibles.  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de fichas visibles.  
  
##  <a name="a-namehasimagea--cmfcbasetabctrlhasimage"></a><a name="hasimage"></a>CMFCBaseTabCtrl::HasImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasImage(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehidesingletaba--cmfcbasetabctrlhidesingletab"></a><a name="hidesingletab"></a>CMFCBaseTabCtrl::HideSingleTab  
 Establece la opción para ocultar las fichas del control de ficha cuando hay una ficha visible.  
  
```  
virtual void HideSingleTab(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHide`  
 Valor booleano que especifica si se debe habilitar ocultar fichas únicas.  
  
### <a name="remarks"></a>Comentarios  
 Cuando la aplicación está configurada para ocultar fichas únicas, el marco de trabajo muestra pestañas automáticamente cuando se agrega una segunda pestaña para el control de ficha.  
  
##  <a name="a-nameinserttaba--cmfcbasetabctrlinserttab"></a><a name="inserttab"></a>CMFCBaseTabCtrl::InsertTab  
 Inserta una ficha en el control de ficha.  
  
```  
Virtual void InsertTab(
    CWnd* pNewWnd,  
    LPCTSTR lpszTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);

 
virtual void InsertTab(
    CWnd* pNewWnd,  
    UINT uiResTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pNewWnd`  
 Puntero a la ventana que este método se agrega como una nueva pestaña.  
  
 [in] `lpszTabLabel`  
 Cadena que contiene la etiqueta para la nueva ficha.  
  
 [in] `nInsertAt`  
 Índice de base cero de la nueva pestaña.  
  
 [in] `uiImageId`  
 Un identificador de la imagen de la lista de imágenes. El control de ficha utiliza esta imagen como icono de la nueva pestaña.  
  
 [in] `bDetachable`  
 Parámetro booleano que determina si la nueva ficha es desmontable.  
  
 [in] `uiResTabLabel`  
 El identificador de recurso para la etiqueta.  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto indicado por `pNewWnd` no se deriva el [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) y si la `bDetachable` parámetro es `TRUE`, el marco de trabajo crea un contenedor especial para la nueva ficha. De forma predeterminada, el contenedor es una instancia de la [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md). Utilice la [CMFCBaseTabCtrl::SetDockingBarWrapperRTC](#setdockingbarwrapperrtc) método para crear una clase de contenedor diferente. Cualquier clase contenedora personalizada debe derivarse de `CDockablePaneAdapter`.  
  
##  <a name="a-nameinvalidatetaba--cmfcbasetabctrlinvalidatetab"></a><a name="invalidatetab"></a>CMFCBaseTabCtrl::InvalidateTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void InvalidateTab(int iTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisactivetabclosebuttona--cmfcbasetabctrlisactivetabclosebutton"></a><a name="isactivetabclosebutton"></a>CMFCBaseTabCtrl::IsActiveTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisautocolora--cmfcbasetabctrlisautocolor"></a><a name="isautocolor"></a>CMFCBaseTabCtrl::IsAutoColor  
 Determina si el control de pestaña está en modo de color automático.  
  
```  
BOOL IsAutoColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de ficha que se encuentra en modo de color automático; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar el modo de color automático mediante el [CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor) método.  
  
##  <a name="a-nameisautodestroywindowa--cmfcbasetabctrlisautodestroywindow"></a><a name="isautodestroywindow"></a>CMFCBaseTabCtrl::IsAutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAutoDestroyWindow() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiscoloreda--cmfcbasetabctrliscolored"></a><a name="iscolored"></a>CMFCBaseTabCtrl::IsColored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsColored() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdialogcontrola--cmfcbasetabctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCBaseTabCtrl::IsDialogControl  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdrawnoprefixa--cmfcbasetabctrlisdrawnoprefix"></a><a name="isdrawnoprefix"></a>CMFCBaseTabCtrl::IsDrawNoPrefix  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDrawNoPrefix() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisflatframea--cmfcbasetabctrlisflatframe"></a><a name="isflatframe"></a>CMFCBaseTabCtrl::IsFlatFrame  
 Indica si el marco del control de ficha se representa en un estilo plano o en un estilo 3D.  
  
```  
virtual BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco del control de ficha se representa en un estilo plano; `FALSE` si el marco se procesará con un estilo 3D.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CMFCTabCtrl::SetFlatFrame](../../mfc/reference/cmfctabctrl-class.md#setflatframe) para cambiar el estilo del marco del control de ficha.  
  
 Controles de fichas que utilicen el estilo de Outlook no se puede representar con fotogramas sin formato. Esto incluye la [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md) y todas las clases derivan de esa clase.  
  
##  <a name="a-nameisflattaba--cmfcbasetabctrlisflattab"></a><a name="isflattab"></a>CMFCBaseTabCtrl::IsFlatTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameishidesingletaba--cmfcbasetabctrlishidesingletab"></a><a name="ishidesingletab"></a>CMFCBaseTabCtrl::IsHideSingleTab  
 Determina si el control de ficha oculta la etiqueta de ficha si hay sólo una ficha.  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de pestaña oculta la etiqueta de ficha que tiene una ficha; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice el método [CMFCBaseTabCtrl::HideSingleTab](#hidesingletab) para habilitar Ocultar la etiqueta de ficha cuando hay sólo una ficha.  
  
##  <a name="a-nameisiconaddeda--cmfcbasetabctrlisiconadded"></a><a name="isiconadded"></a>CMFCBaseTabCtrl::IsIconAdded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsIconAdded(
    HICON hIcon,  
    int& iIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `hIcon`  
 [in] `iIcon`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisinplaceedita--cmfcbasetabctrlisinplaceedit"></a><a name="isinplaceedit"></a>CMFCBaseTabCtrl::IsInPlaceEdit  
 Indica si el control de pestaña está configurado para permitir al usuario modificar de forma dinámica las etiquetas de la ficha.  
  
```  
virtual BOOL IsInPlaceEdit() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si en el contexto de edición está habilitada; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar o deshabilitar la edición en contexto llamando al método [CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit).  
  
##  <a name="a-nameisleftrightroundeda--cmfcbasetabctrlisleftrightrounded"></a><a name="isleftrightrounded"></a>CMFCBaseTabCtrl::IsLeftRightRounded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameismditaba--cmfcbasetabctrlismditab"></a><a name="ismditab"></a>CMFCBaseTabCtrl::IsMDITab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMDITab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisonenotestylea--cmfcbasetabctrlisonenotestyle"></a><a name="isonenotestyle"></a>CMFCBaseTabCtrl::IsOneNoteStyle  
 Determina si las fichas se muestran en el estilo de Microsoft OneNote.  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestran las fichas en el estilo de Microsoft OneNote; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Llame al método [CMDIFrameWndEx::EnableMDITabs](../../mfc/reference/cmdiframewndex-class.md#enablemditabs) para habilitar el estilo de Microsoft OneNote. También puede habilitar este estilo al crear instancias de la [CMFCTabCtrl clase](../../mfc/reference/cmfctabctrl-class.md): basta con pasar el estilo STYLE_3D_ONENOTE al método [CMFCTabCtrl::Create](../../mfc/reference/cmfctabctrl-class.md#create).  
  
 De forma predeterminada, no se admite el estilo de Microsoft OneNote en una clase personalizada derivada de la `CMFCBaseTabCtrl Class`. Sin embargo, se admite en la `CMFCTabCtrl` clase.  
  
##  <a name="a-nameisptintabareaa--cmfcbasetabctrlisptintabarea"></a><a name="isptintabarea"></a>CMFCBaseTabCtrl::IsPtInTabArea  
 Determina si un punto está dentro del área de ficha.  
  
```  
virtual BOOL IsPtInTabArea(CPoint point) const = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 El punto de prueba.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el punto está en el área de fichas; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 En el `CMFCBaseTabCtrl Class`, este método es una función virtual pura y no tiene ninguna implementación. Si deriva una clase de `CMFCBaseTabCtrl`, que tiene que implementar esta función.  
  
##  <a name="a-nameistabclosebuttonhighlighteda--cmfcbasetabctrlistabclosebuttonhighlighted"></a><a name="istabclosebuttonhighlighted"></a>CMFCBaseTabCtrl::IsTabCloseButtonHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonHighlighted() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameistabclosebuttonpresseda--cmfcbasetabctrlistabclosebuttonpressed"></a><a name="istabclosebuttonpressed"></a>CMFCBaseTabCtrl::IsTabCloseButtonPressed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonPressed() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameistabdetachablea--cmfcbasetabctrlistabdetachable"></a><a name="istabdetachable"></a>CMFCBaseTabCtrl::IsTabDetachable  
 Determina si una pestaña es desmontable.  
  
```  
virtual BOOL IsTabDetachable(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la pestaña para comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ficha está desmontable; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para hacer una ficha separables, utilice el método [CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach).  
  
##  <a name="a-nameistabicononlya--cmfcbasetabctrlistabicononly"></a><a name="istabicononly"></a>CMFCBaseTabCtrl::IsTabIconOnly  
 Determina si una etiqueta de ficha contiene sólo los iconos y ningún texto.  
  
```  
virtual BOOL IsTabIconOnly(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si una etiqueta de ficha tiene sólo iconos; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer las fichas de la aplicación para mostrar sólo los iconos, llame al método [CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly).  
  
##  <a name="a-nameistabswapenableda--cmfcbasetabctrlistabswapenabled"></a><a name="istabswapenabled"></a>CMFCBaseTabCtrl::IsTabSwapEnabled  
 Determina si el control de pestaña permite al usuario cambiar las posiciones de tabulación mediante el mouse.  
  
```  
BOOL IsTabSwapEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si las posiciones de tabulación pueden cambiarse por el usuario; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los usuarios no pueden cambiar el orden de las fichas en un control de ficha. Utilice la [CMFCBaseTabCtrl::EnableTabSwap](#enabletabswap) método para habilitar esta funcionalidad.  
  
##  <a name="a-nameistabvisiblea--cmfcbasetabctrlistabvisible"></a><a name="istabvisible"></a>CMFCBaseTabCtrl::IsTabVisible  
 Indica si la ficha especificada está visible.  
  
```  
virtual BOOL IsTabVisible(int iTab) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la pestaña para comprobar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la ficha especificada es visible; en caso contrario, 0.  
  
##  <a name="a-nameisvs2005stylea--cmfcbasetabctrlisvs2005style"></a><a name="isvs2005style"></a>CMFCBaseTabCtrl::IsVS2005Style  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namembactivatetabonrightclicka--cmfcbasetabctrlmbactivatetabonrightclick"></a><a name="m_bactivatetabonrightclick"></a>CMFCBaseTabCtrl::m_bActivateTabOnRightClick  
 `m_bActivateTabOnRightClick`Determina si las fichas son foco cuando el usuario hace clic en una etiqueta de ficha con el botón secundario del mouse.  
  
```  
BOOL m_bActivateTabOnRightClick;  
```  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado para este miembro de datos es `FALSE`.  
  
##  <a name="a-namembautodestroywindowa--cmfcbasetabctrlmbautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCBaseTabCtrl::m_bAutoDestroyWindow  
 `m_bAutoDestroyWindow`Determina si el marco de trabajo destruye los objetos en fichas automáticamente cuando se quitan las fichas.  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este miembro es `FALSE`.  
  
##  <a name="a-namemovetaba--cmfcbasetabctrlmovetab"></a><a name="movetab"></a>CMFCBaseTabCtrl::MoveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void MoveTab(
    int nSource,  
    int nDest);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nSource`  
 [in] `nDest`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonchangetabsa--cmfcbasetabctrlonchangetabs"></a><a name="onchangetabs"></a>CMFCBaseTabCtrl::OnChangeTabs  
 El marco de trabajo llama a este método cuando el número de fichas en una ficha de control de cambios.  
  
```  
virtual void OnChangeTabs();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, este método no hace nada. Invalide este método para ejecutar código personalizado cuando el número de fichas en la ficha control de cambios.  
  
##  <a name="a-nameondropa--cmfcbasetabctrlondrop"></a><a name="ondrop"></a>CMFCBaseTabCtrl::OnDrop  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrop(
    COleDataObject*,
    DROPEFFECT,
    CPoint);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `COleDataObject*`  
 [in] `DROPEFFECT`  
 [in] `CPoint`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondragovera--cmfcbasetabctrlondragover"></a><a name="ondragover"></a>CMFCBaseTabCtrl::OnDragOver  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondragleavea--cmfcbasetabctrlondragleave"></a><a name="ondragleave"></a>CMFCBaseTabCtrl::OnDragLeave  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondragentera--cmfcbasetabctrlondragenter"></a><a name="ondragenter"></a>CMFCBaseTabCtrl::OnDragEnter  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonrenametaba--cmfcbasetabctrlonrenametab"></a><a name="onrenametab"></a>CMFCBaseTabCtrl::OnRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnRenameTab(int, CString&);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `int`  
 [in] `CString&`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namepretranslatemessagea--cmfcbasetabctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCBaseTabCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pMsg`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namerecalclayouta--cmfcbasetabctrlrecalclayout"></a><a name="recalclayout"></a>CMFCBaseTabCtrl::RecalcLayout  
 Vuelve a calcular el diseño interno del control de ficha.  
  
```  
virtual void RecalcLayout() = 0;  
```  
  
### <a name="remarks"></a>Comentarios  
 En el `CMFCBaseTabCtrl Class`, este método es una función virtual pura. Si deriva una clase de `CMFCBaseTabCtrl`, que tiene que implementar esta función.  
  
##  <a name="a-nameremovealltabsa--cmfcbasetabctrlremovealltabs"></a><a name="removealltabs"></a>CMFCBaseTabCtrl::RemoveAllTabs  
 Quita todas las fichas del control de ficha.  
  
```  
virtual void RemoveAllTabs();
```  
  
### <a name="remarks"></a>Comentarios  
 Si [CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow) es `TRUE`, el marco de trabajo elimina todos los [CWnd](../../mfc/reference/cwnd-class.md) objetos se agregan a las fichas quitadas.  
  
##  <a name="a-nameremovetaba--cmfcbasetabctrlremovetab"></a><a name="removetab"></a>CMFCBaseTabCtrl::RemoveTab  
 Quita una ficha del control de ficha.  
  
```  
virtual BOOL RemoveTab(
    int iTab,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
 [in] `bRecalcLayout`  
 Parámetro booleano que especifica si se va a calcular el diseño de la ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método quita la ficha correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si [CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow) es `TRUE`, `RemoveTab` destruye la [CWnd](../../mfc/reference/cwnd-class.md) objeto asociado a la ficha especificada.  
  
##  <a name="a-namerenametaba--cmfcbasetabctrlrenametab"></a><a name="renametab"></a>CMFCBaseTabCtrl::RenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL RenameTab();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameresetimagelista--cmfcbasetabctrlresetimagelist"></a><a name="resetimagelist"></a>CMFCBaseTabCtrl::ResetImageList  
 Restablece la lista de imágenes de una instancia de la [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md).  
  
```  
void ResetImageList();
```  
  
##  <a name="a-nameserializea--cmfcbasetabctrlserialize"></a><a name="serialize"></a>CMFCBaseTabCtrl::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `ar`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetactivetaba--cmfcbasetabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCBaseTabCtrl::SetActiveTab  
 Activa la ficha especificada.  
  
```  
virtual BOOL SetActiveTab(int iTab) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña. `SetActiveTab`activa la pestaña con este índice.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el `CMFCBaseTabCtrl Class`, este método es una función virtual pura. Si deriva una clase de `CMFCBaseTabCtrl`, que tiene que implementar esta función.  
  
##  <a name="a-namesetactivetabcolora--cmfcbasetabctrlsetactivetabcolor"></a><a name="setactivetabcolor"></a>CMFCBaseTabCtrl::SetActiveTabColor  
 Establece el color de fondo de la ficha activa.  
  
```  
virtual void SetActiveTabColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clr`  
 Especifica el nuevo color de fondo.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo Obtiene el color de fondo predeterminado para las fichas activas de la [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)método.  
  
##  <a name="a-namesetactivetabtextcolora--cmfcbasetabctrlsetactivetabtextcolor"></a><a name="setactivetabtextcolor"></a>CMFCBaseTabCtrl::SetActiveTabTextColor  
 Establece el color del texto de las pestañas activas.  
  
```  
virtual void SetActiveTabTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clr`  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que especifica el color del texto nuevo.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo Obtiene el color del texto de [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371). Reemplazar este color predeterminado mediante el `SetActiveTabTextColor` método.  
  
##  <a name="a-namesetautocolorsa--cmfcbasetabctrlsetautocolors"></a><a name="setautocolors"></a>CMFCBaseTabCtrl::SetAutoColors  
 Establece los colores del control de ficha que utiliza el marco de trabajo en el modo de color automático.  
  
```  
void SetAutoColors(const CArray<COLORREF,COLORREF>& arColors);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `arColors`  
 Una matriz de colores RGB.  
  
### <a name="remarks"></a>Comentarios  
 Si proporciona una matriz de colores personalizada, se omite la matriz predeterminada de colores. Si el parámetro `arColors` está vacío, el marco de trabajo revierte a la matriz predeterminada de colores.  
  
 Para habilitar el modo de color automático, use la [CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor) método.  
  
##  <a name="a-namesetdockingbarwrapperrtca--cmfcbasetabctrlsetdockingbarwrapperrtc"></a><a name="setdockingbarwrapperrtc"></a>CMFCBaseTabCtrl::SetDockingBarWrapperRTC  
 Establece la clase de contenedor que se utiliza para todos los objetos no derivados de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
```  
void SetDockingBarWrapperRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRTC`  
 La información de clase en tiempo de ejecución para la nueva clase de contenedor.  
  
### <a name="remarks"></a>Comentarios  
 Agregar fichas a un control de ficha mediante los métodos [CMFCBaseTabCtrl::AddTab](#addtab) y [CMFCBaseTabCtrl::InsertTab](#inserttab). Cuando se agrega una ficha, cada control en esa pestaña debe ser acoplable. Los objetos que no se derivan `CDockablePane` debe ser ajustado. `AddTab`y `InsertTab` crear un contenedor para estos objetos. La clase de contenedor predeterminada es el [CDockablePaneAdapter clase](../../mfc/reference/cdockablepaneadapter-class.md). El método `SetDockingBarWrapperRTC` permite cambiar la clase que se utiliza como una clase contenedora. La clase contenedora que proporcione debe derivarse de `CDockablePaneAdapter`.  
  
##  <a name="a-namesetdrawnoprefixa--cmfcbasetabctrlsetdrawnoprefix"></a><a name="setdrawnoprefix"></a>CMFCBaseTabCtrl::SetDrawNoPrefix  
 Habilita y deshabilita el procesamiento de caracteres de prefijo de etiquetas.  
  
```  
void SetDrawNoPrefix(
    BOOL bNoPrefix,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bNoPrefix`  
 `TRUE`Si desea procesar los caracteres de prefijo; de lo contrario, `FALSE`.  
  
 [in] `bRedraw`  
 `TRUE`Si desea volver a dibujar la ventana con fichas; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Un carácter de prefijo es un carácter de tecla de acceso que está precedido por un símbolo de y comercial (&).  
  
##  <a name="a-namesetimagelista--cmfcbasetabctrlsetimagelist"></a><a name="setimagelist"></a>CMFCBaseTabCtrl::SetImageList  
 Establece la lista de imágenes de icono para el control de ficha.  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx = 15,  
    COLORREF clrTransp = RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 Un identificador de recurso de mapa de bits. `SetImageList`carga la lista de imágenes de este recurso.  
  
 [in] `cx`  
 El ancho de cada imagen en píxeles.  
  
 [in] `clrTransp`  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color transparente de la imagen.  
  
 [in] `hImageList`  
 Identificador de una lista de imágenes cargadas previamente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método se realizó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Se muestran las imágenes de la lista de imágenes de icono junto a las etiquetas de la ficha. Para mostrar un icono, debe especificar su índice cuando se llama a [CMFCBaseTabCtrl::AddTab](#addtab).  
  
 `SetImageList`se producirá un error si el control de ficha se creó con un estilo plano. También producirá un error si el marco de trabajo no puede cargar la imagen indicada por `uiID`.  
  
 Este método vuelve a calcular el alto de la ficha de acuerdo con los tamaños de imagen y texto.  
  
##  <a name="a-namesetlocationa--cmfcbasetabctrlsetlocation"></a><a name="setlocation"></a>CMFCBaseTabCtrl::SetLocation  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetLocation(Location location);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `location`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettabbkcolora--cmfcbasetabctrlsettabbkcolor"></a><a name="settabbkcolor"></a>CMFCBaseTabCtrl::SetTabBkColor  
 Establece el color de fondo de la ficha especificada.  
  
```  
virtual BOOL SetTabBkColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
 [in] `color`  
 El color que desea establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` en caso contrario.  
  
##  <a name="a-namesettabbordersizea--cmfcbasetabctrlsettabbordersize"></a><a name="settabbordersize"></a>CMFCBaseTabCtrl::SetTabBorderSize  
 Establece un nuevo tamaño de borde para el control de ficha.  
  
```  
virtual void SetTabBorderSize(
    int nTabBorderSize,  
    BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTabBorderSize`  
 El nuevo tamaño de borde, en píxeles.  
  
 [in] `bRepaint`  
 Parámetro booleano que indica si el marco de trabajo vuelve a dibujarse el control.  
  
##  <a name="a-namesettabhicona--cmfcbasetabctrlsettabhicon"></a><a name="settabhicon"></a>CMFCBaseTabCtrl::SetTabHicon  
 Establece el icono para una etiqueta de ficha.  
  
```  
virtual BOOL SetTabHicon(
    int iTab,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña. Este método cambia el icono para esta ficha.  
  
 [in] `hIcon`  
 Identificador de un icono.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
##  <a name="a-namesettabicona--cmfcbasetabctrlsettabicon"></a><a name="settabicon"></a>CMFCBaseTabCtrl::SetTabIcon  
 Establece el icono de una ficha.  
  
```  
virtual BOOL SetTabIcon(
    int iTab,  
    UINT uiIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha para actualizar.  
  
 [in] `uiIcon`  
 El identificador de icono para el nuevo icono. Este identificador hace referencia interna [CImageList](../../mfc/reference/cimagelist-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
##  <a name="a-namesettabicononlya--cmfcbasetabctrlsettabicononly"></a><a name="settabicononly"></a>CMFCBaseTabCtrl::SetTabIconOnly  
 Permite mostrar sólo aparecerá un icono (y no hay ninguna etiqueta de texto) en una ficha específica.  
  
```  
virtual BOOL SetTabIconOnly(
    int iTab,  
    BOOL bIconOnly = TRUE,  
    BOOL bShowTooltipAlways = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha cambiar.  
  
 [in] `bIconOnly`  
 Parámetro booleano que determina si se debe mostrar sólo iconos.  
  
 [in] `bShowTooltipAlways`  
 Parámetro booleano que determina si el marco de trabajo muestra información sobre herramientas para una etiqueta de ficha que muestra sólo los iconos.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, un control de pestaña muestra la etiqueta de icono y texto para cada ficha.  
  
##  <a name="a-namesettablabela--cmfcbasetabctrlsettablabel"></a><a name="settablabel"></a>CMFCBaseTabCtrl::SetTabLabel  
 Establece el texto de una etiqueta de ficha.  
  
```  
virtual BOOL SetTabLabel(
    int iTab,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha para actualizar.  
  
 [in] `strLabel`  
 Una referencia a una cadena que contiene el nuevo texto para la etiqueta de ficha.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
##  <a name="a-namesettabsheighta--cmfcbasetabctrlsettabsheight"></a><a name="settabsheight"></a>CMFCBaseTabCtrl::SetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetTabsHeight();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettabsordera--cmfcbasetabctrlsettabsorder"></a><a name="settabsorder"></a>CMFCBaseTabCtrl::SetTabsOrder  
 Organiza las fichas en el orden especificado.  
  
```  
BOOL SetTabsOrder(const CArray<int,int>& arOrder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `arOrder`  
 Una matriz de índices de base cero que define el nuevo orden de tabulación.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FAIL` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El tamaño de la `arOrder` matriz debe ser igual que el número de fichas del control de ficha.  
  
##  <a name="a-namesettabtextcolora--cmfcbasetabctrlsettabtextcolor"></a><a name="settabtextcolor"></a>CMFCBaseTabCtrl::SetTabTextColor  
 Establece el color del texto de una ficha específica.  
  
```  
virtual BOOL SetTabTextColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de la ficha.  
  
 [in] `color`  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; en caso contrario, es 0.  
  
##  <a name="a-nameshowtaba--cmfcbasetabctrlshowtab"></a><a name="showtab"></a>CMFCBaseTabCtrl::ShowTab  
 Muestra u oculta la pestaña especificada.  
  
```  
virtual BOOL ShowTab(
    int iTab,  
    BOOL bShow = TRUE,  
    BOOL bRecalcLayout = TRUE,  
    BOOL bActivate = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 El índice de la pestaña que `ShowTab` mostrará u ocultará.  
  
 [in] `bShow`  
 Parámetro booleano que indica si se debe mostrar la ficha.  
  
 [in] `bRecalcLayout`  
 Parámetro booleano que indica si se debe actualizar inmediatamente el diseño de ventana.  
  
 [in] `bActivate`  
 Un parámetro booleano que indica si se selecciona la ficha especificada en `iTab`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El parámetro `bActivate` sólo se aplica si `bShow` es `TRUE`. Si `bActivate` es `TRUE` y si `ShowTab` es correcta, `ShowTab` enviará el mensaje AFX_WM_CHANGE_ACTIVE_TAB al elemento primario de la ventana de la ficha.  
  
##  <a name="a-namestartrenametaba--cmfcbasetabctrlstartrenametab"></a><a name="startrenametab"></a>CMFCBaseTabCtrl::StartRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL StartRenameTab(int iTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameswaptabsa--cmfcbasetabctrlswaptabs"></a><a name="swaptabs"></a>CMFCBaseTabCtrl::SwapTabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SwapTabs(
    int nFisrtTabID,  
    int nSecondTabID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nFisrtTabID`  
 [in] `nSecondTabID`  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)   
 [Clase CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

