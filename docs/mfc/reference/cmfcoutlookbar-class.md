---
title: Clase CMFCOutlookBar | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCOutlookBar class
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: 34
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
ms.openlocfilehash: ff58cf786e4979d64aa2b5d7ad4d1a32b96bec3d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar (Clase)
Un panel con pestañas con el aspecto visual del **Panel de navegación** en Microsoft Outlook 2000 u Outlook 2003. El `CMFCOutlookBar` objeto contiene un [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto y una serie de fichas. Las fichas pueden ser [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objetos o `CWnd`-objetos derivados. Para el usuario, la barra de Outlook aparece como una serie de botones y un área de presentación. Cuando el usuario hace clic en un botón, se muestra el panel de control o botón correspondiente .  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCOutlookBar : public CBaseTabbedPane  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCOutlookBar::CMFCOutlookBar`|Constructor predeterminado.|  
|`CMFCOutlookBar::~CMFCOutlookBar`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si se puede destruir un panel con fichas vacío. (Invalida [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Determina si el otro panel se puede acoplar en el panel de la barra de Outlook. (Invalida CDockablePane::CanAcceptPane).|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título para el panel con fichas muestra el mismo texto como la ficha activa. (Invalida [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|  
|[CMFCOutlookBar::Create](#create)|Crea el control de barra de Outlook.|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crea una ficha personalizada de barra de Outlook.|  
|`CMFCOutlookBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si un usuario puede acoplar una barra de controles en el borde exterior de la barra de Outlook.|  
|[CMFCOutlookBar::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable. (Invalida [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Devuelve la fuente del texto en los botones de la barra de Outlook.|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Devuelve el tamaño y posición de las áreas de ficha en la barra de Outlook. (Invalida [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|  
|`CMFCOutlookBar::GetThisClass`|Usar el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Determina si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003 (vea comentarios).|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Llama a [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que se ha establecido la ficha activa con la animación.|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Llama a [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una ficha de página se establece como la ficha activa con la animación.|  
|[CMFCOutlookBar::OnScroll](#onscroll)|Llamado por el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Quita una pestaña personalizada de barra de Outlook.|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Establece la fuente del texto de los botones de la barra de Outlook.|  
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Especifica si el comportamiento de la barra de Outlook imita de Outlook 2003 (vea la sección Comentarios).|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de una barra de Outlook, consulte el [ejemplo de OutlookDemo: aplicación OutlookDemo de MFC](../../visual-cpp-samples.md).  
  
## <a name="implementing-the-outlook-bar"></a>Implementación de la barra de Outlook  
 Para usar el control `CMFCOutlookBar` de la aplicación, siga estos pasos:  
  
1.  Incruste un objeto `CMFCOutlookBar` en la clase de ventana de marco principal.  
  
 ```  
    class CMainFrame : public CMDIFrameWnd  
 { ...  
    CMFCOutlookBar m_wndOutlookBar;  
    CMFCOutlookBarPane m_wndOutlookPane;  
 ... };  
 ```  
2.  Al procesar la `WM_CREATE` mensaje en el marco principal, llamada la [CMFCOutlookBar::Create](#create) método para crear el control de ficha de la barra de Outlook.  
  
 ```  
    m_wndOutlookBar.Create (_T("Shortcuts"),
    this,
    CRect (0,
    0,
    100,
    100),
    ID_VIEW_OUTLOOKBAR,
    WS_CHILD | WS_VISIBLE | CBRS_LEFT);

 ```  
3.  Obtener un puntero al propio `CMFCOutlookBarTabCtrl` utilizando [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  Crear un [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto para cada ficha que contiene los botones.  
  
 ```  
    m_wndOutlookPane.Create (&m_wndOutlookBar,
    AFX_DEFAULT_TOOLBAR_STYLE,
    ID_OUTLOOK_PANE_GENERAL,
    AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);
*// make the Outlook pane detachable (enable docking)  
    m_wndOutlookPane.EnableDocking (CBRS_ALIGN_ANY);
*// add buttons  
    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_MAINFRAME), "About",
    ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON), "Open",
    ID_FILE_OPEN);

 ```  
5.  Llame a [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregar cada nueva pestaña. Establecer el `bDetachable` parámetro `FALSE` para hacer que una página no son intercambiables. O bien, utilice [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) para agregar páginas desmontables.  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  Para agregar una `CWnd`-control derivado (por ejemplo, [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md)) como una pestaña, crear el control y la llamada [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregarlo a la barra de Outlook.  
  
> [!NOTE]
>  Debe usar los identificadores de control único para cada [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto y para cada `CWnd`-objeto derivado.  
  
 Para agregar o eliminar nuevas páginas en tiempo de ejecución dinámicamente, use [CMFCOutlookBar::CreateCustomPage](#createcustompage) y [CMFCOutlookBar::RemoveCustomPage](#removecustompage).  
  
## <a name="outlook-2003-mode"></a>Modo de Outlook 2003  
 En el modo de Outlook 2003, los botones de ficha se colocan en la parte inferior del panel de barra de Outlook. Cuando no hay espacio suficiente para mostrar los botones, se muestran como iconos en un área similar en la barra de herramientas en la parte inferior del panel.  
  
 Utilice [CMFCOutlookBar::SetMode2003](#setmode2003) para habilitar el modo de Outlook 2003. Utilice [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) para establecer el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook. Los iconos del mapa de bits deben estar ordenados por índice de tabulación.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxoutlookbar.h  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCOutlookBar::AllowDestroyEmptyTabbedPane  
 Especifica si se puede destruir un panel con fichas vacío.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se puede destruir un panel con fichas vacío; de lo contrario, `FALSE`. La implementación predeterminada siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se puede destruir un panel con fichas vacío, el marco de trabajo oculta en su lugar.  
  
##  <a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane  
 Determina si el otro panel se puede acoplar en el panel de la barra de Outlook.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a otro panel acoplado a este panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si otro panel se puede acoplar en el panel de la barra de Outlook; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si la barra de Outlook está en modo de Outlook 2003, acoplamiento no se admite, por lo que el valor devuelto es `FALSE`.  
  
 Si el `pBar` parámetro es `NULL`, este método devuelve `FALSE`.  
  
 De lo contrario, este método se comporta como el método base [CBasePane::CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane), excepto que, incluso si no está habilitado el acoplamiento, una barra de Outlook puede habilitar otra barra de Outlook para acoplarse sobre él.  
  
##  <a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName  
 Determina si el título para el panel con fichas muestra el mismo texto como la ficha activa.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el título de la ventana de la barra de Outlook se establece automáticamente en el texto de la pestaña activa; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) para habilitar o deshabilitar esta funcionalidad.  
  
 En el modo de Outlook 2003, esta opción siempre está habilitada.  
  
##  <a name="create"></a>CMFCOutlookBar::Create  
 Crea el control de barra de Outlook.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszCaption`  
 Especifica el título de ventana.  
  
 [in] `pParentWnd`  
 Especifica un puntero a una ventana primaria. No debe ser NULL.  
  
 [in] `rect`  
 Especifica el tamaño y la posición en píxeles la barra de outlook.  
  
 [in] `nID`  
 Especifica el identificador del control. Debe ser diferente de otro identificadores utilizados en la aplicación de control.  
  
 [in] `dwStyle`  
 Especifica el estilo de barra de control. Para los valores posibles, consulte [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 [in] `dwControlBarStyle`  
 Especifica los estilos definidos por la biblioteca especiales.  
  
 [in] `pContext`  
 Crear el contexto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el método es correcto; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CMFCOutlookBar` objeto en dos pasos. Llame primero al constructor y, a continuación, llame a `Create`, que crea el control de barra de outlook y lo adjunta a la `CMFCOutlookBar` objeto.  
  
 Consulte [CBasePane::CreateEx](../../mfc/reference/cbasepane-class.md#createex) para obtener la lista de los estilos definidos por la biblioteca disponibles que especificarse mediante `dwControlBarStyle`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CMFCOutlookBar` clase. Este fragmento de código forma parte de la [ejemplo Outlook múltiples vistas](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_OutlookMultiViews](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews&#2;](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage  
 Crea una ficha personalizada de barra de Outlook.  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPageName`  
 La etiqueta de la página.  
  
 [in] `bActivatePage`  
 Si `TRUE`, la página se vuelve activa durante la creación.  
  
 [in] `dwEnabledDocking`  
 Combinación de marcas CBRS_ALIGN_ que especifica los lados de acoplamiento habilitados cuando se desasocia la página.  
  
 [in] `bEnableTextLabels`  
 Si `TRUE`, se habilitan las etiquetas de texto para los botones que se encuentran en la página.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la página recién creada, o `NULL` si falló la creación.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para que los usuarios puedan crear páginas personalizadas de barra de Outlook. Puede crear hasta 100 páginas por aplicación. El control de página identificadores de inicio de 0xF000. Se produce un error en la creación si el número total de páginas personalizadas de barra de Outlook es superior a 100.  
  
 Utilice [CMFCOutlookBar::RemoveCustomPage](#removecustompage) eliminar páginas personalizadas.  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore  
 Especifica si un usuario puede acoplar un panel en el borde exterior de la barra de Outlook.  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El marco llama el `DoesAllowDynInsertBefore` método cuando se busca una ubicación para acoplar un panel dinámico. Si la función devuelve `FALSE`, el marco de trabajo no admite el acoplamiento de cualquier panel dinámico en los bordes exteriores del panel.  
  
 Normalmente, se crea una barra de Outlook como un control estático no flotante. Puede invalidar esta función en una clase derivada y devolver `TRUE` para cambiar este comportamiento.  
  
> [!NOTE]
>  Porque paneles dinámicos comprobación el estado de paneles estáticos acoplados al acoplamiento, debe acoplar paneles dinámicos después paneles estáticos siempre que sea posible.  
  
##  <a name="floattab"></a>CMFCOutlookBar::FloatTab  
 Desplaza un panel.  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero al panel para float.  
  
 [in] `nTabID`  
 Índice de base cero de la ficha para float.  
  
 [in] `dockMethod`  
 Especifica el método que utilice para hacer flotar el panel.  Para obtener más información, consulte [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab).  
  
 [in] `bHide`  
 `TRUE`Para ocultar el panel antes flotante; de lo contrario, `FALSE`. A diferencia de la versión de la clase base de este método, este parámetro no tiene un valor predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel flotante; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método es similar a [CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab) excepto en que no permite la última ficha restante de un control de barra de Outlook para float.  
  
##  <a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont  
 Devuelve a la fuente del texto en la página de fichas de botón de la barra de Outlook.  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de fuente que se utiliza para mostrar texto en Outlook barra de pestañas de botón de la página.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar la fuente que se utiliza para mostrar el texto en las fichas de botón de página de Outlook. Puede establecer la fuente mediante una llamada de [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).  
  
##  <a name="gettabarea"></a>CMFCOutlookBar::GetTabArea  
 Determina el tamaño y posición de las áreas de ficha en la barra de Outlook.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectTabAreaTop`  
 Contiene el tamaño y posición (en coordenadas de cliente) del área de ficha superior cuando se devuelve la función.  
  
 [out] `rectTabAreaBottom`  
 Contiene el tamaño y posición (en coordenadas de cliente) del área de ficha inferior cuando se devuelve la función.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar el tipo de acoplamiento al panel de destino. Cuando el marco de trabajo determina que el usuario arrastra el panel se acopla sobre el área de la ficha del panel de destino, intenta agregar el primer panel como una nueva pestaña del panel de destino. De lo contrario, intenta acoplar el primer panel en un lado correspondiente del panel de destino. El marco de trabajo crea un nuevo contenedor con un control deslizante para acomodar el panel acoplado adicional.  
  
 La implementación predeterminada de `GetTabArea` devuelve el área de cliente de la barra de Outlook si la barra de Outlook es estático; que es, si no se puede desplazar la barra de Outlook. De lo contrario, devuelve el área que toman los botones de página en la parte superior e inferior del control de barra de Outlook.  
  
 Invalide este método en la clase derivada de `CMFCOutlookBar` para cambiar este comportamiento.  
  
##  <a name="ismode2003"></a>CMFCOutlookBar::IsMode2003  
 Especifica si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la barra de Outlook se ejecuta en modo de Microsoft Office 2003; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar este modo mediante [CMFCOutlookBar::SetMode2003](#setmode2003).  
  
##  <a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation  
 Llama a [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que se ha establecido la ficha activa con la animación.  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPage`  
 Índice de base cero de la página de ficha que se ha realizado activo.  
  
### <a name="remarks"></a>Comentarios  
 El efecto visual de la configuración de la ficha activa depende de si ha habilitado la animación. Para obtener más información, consulte [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).  
  
##  <a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation  
 Llama a [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una ficha de página se establece como la ficha activa con la animación.  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPage`  
 Índice de base cero de la página de ficha que se va a establecerse activo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si debe utilizarse la animación en la configuración de la ficha activa de nuevo, o `FALSE` si se debe deshabilitar la animación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onscroll"></a>CMFCOutlookBar::OnScroll  
 Llamado por el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDown`  
 `TRUE`Si la barra de Outlook se desplaza hacia abajo, o `FALSE` si se desplaza hacia arriba.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage  
 Quita una página personalizada de ficha de barra de Outlook.  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiPage`  
 Índice de base cero de la página en la ventana primaria de Outlook.  
  
 [in] `pTargetWnd`  
 Pointerto la ventana primaria de Outlook.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la página personalizada se ha quitado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para eliminar páginas personalizadas. Cuando la página se quita su Id. de control se devuelve al grupo de identificadores disponibles.  
  
 Debe proporcionar un puntero a [CMFCOutlookBarTabCtrl clase](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto en el que reside la página Quitar actualmente. Tenga en cuenta que un usuario puede mover páginas separables entre las distintas barras de Outlook, pero la información sobre una página personalizada reside en el objeto de la barra de Outlook para la que ha llamado [CMFCOutlookBar::CreateCustomPage](#createcustompage).  
  
 Utilice [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) para obtener un puntero a la ventana de Outlook.  
  
##  <a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont  
 Establece la fuente del texto de los botones de la barra de Outlook.  
  
```  
void SetButtonsFont(
    CFont* pFont,  
    BOOL bRedraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pFont`  
 Especifica la nueva fuente.  
  
 [in] `bRedraw`  
 Si `TRUE`, se volverá a dibujar la barra de Outlook.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer una fuente para el texto mostrado en los botones de página de ficha de outlook.  
  
##  <a name="setmode2003"></a>CMFCOutlookBar::SetMode2003  
 Especifica si el comportamiento de la barra de Outlook imita de Outlook 2003.  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMode2003`  
 Si es TRUE, el modo de Office 2003 está habilitado.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para habilitar o deshabilitar el modo de Office 2003. En este modo, la barra de Outlook tiene una barra de herramientas adicional con un botón de personalización. El comportamiento de la barra de Outlook se ajusta al comportamiento de la barra de Outlook de Microsoft Office 2003.  
  
 De forma predeterminada, este modo está deshabilitado.  
  
> [!NOTE]
>  Esta función debe llamarse antes [CMFCOutlookBar::Create](#create).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)   
 [Clase CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [Clase CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

