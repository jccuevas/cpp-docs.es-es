---
title: CMFCOutlookBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
caps.latest.revision: "34"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 00988ef4a0b70561ec3a5687502ddae95508dad5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar (clase)
Un panel con pestañas con el aspecto visual del **Panel de navegación** en Microsoft Outlook 2000 u Outlook 2003. El `CMFCOutlookBar` objeto contiene un [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto y una serie de pestañas. Las pestañas pueden ser [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objetos o `CWnd`-objetos derivados. Para el usuario, la barra de Outlook aparece como una serie de botones y un área de presentación. Cuando el usuario hace clic en un botón, se muestra el panel de control o botón correspondiente .  
  
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
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Especifica si un panel con fichas vacío puede ser destruido. (Invalida [CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane).)|  
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Determina si el otro panel se puede acoplar en el panel de la barra de Outlook. (Reemplaza a CDockablePane::CanAcceptPane).|  
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Determina si el título para el panel con pestañas muestra el mismo texto como la pestaña activa. (Invalida [CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname).)|  
|[CMFCOutlookBar::Create](#create)|Crea el control de barra de Outlook.|  
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|Crea una pestaña personalizada de barra de Outlook.|  
|`CMFCOutlookBar::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Determina si un usuario puede acoplar una barra de control en el borde externo de la barra de Outlook.|  
|[CMFCOutlookBar::FloatTab](#floattab)|Convierte un panel en flotante, pero solo si el panel se encuentra actualmente en una pestaña desmontable. (Invalida [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).)|  
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Devuelve la fuente del texto en los botones de la barra de Outlook.|  
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Devuelve el tamaño y la posición de las áreas de ficha en la barra de Outlook. (Invalida [CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea).)|  
|`CMFCOutlookBar::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Determina si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003 (vea la sección Comentarios).|  
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|Llamado por el método [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que se ha establecido la pestaña activa con animación.|  
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|Llamado por el método [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una pestaña de página se establece como la pestaña activa con animación.|  
|[CMFCOutlookBar::OnScroll](#onscroll)|Lo llama el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.|  
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|Quita una pestaña personalizada de barra de Outlook.|  
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Establece la fuente del texto en los botones de la barra de Outlook.|  
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
2.  Cuando se procesa la `WM_CREATE` mensaje en el marco principal, llamada la [CMFCOutlookBar::Create](#create) método para crear el control de pestaña de la barra de Outlook.  
  
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
3.  Obtener un puntero al subyacente `CMFCOutlookBarTabCtrl` utilizando [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow).  
  
 ```  
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();

 ```  
4.  Crear un [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto para cada pestaña que contiene los botones.  
  
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
5.  Llame a [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregar cada nueva pestaña. Establecer el `bDetachable` parámetro `FALSE` para hacer que una página no se puede desasociar. O bien, use [CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol) para agregar capacidad de desasociar páginas.  
  
 ```  
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1,
    TRUE);

 ```  
6.  Para agregar una `CWnd`-control derivado (por ejemplo, [CMFCShellTreeCtrl clase](../../mfc/reference/cmfcshelltreectrl-class.md)) como una pestaña, crear el control y la llamada [CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) para agregarlo a la barra de Outlook.  
  
> [!NOTE]
>  Debe usar identificadores de control único para cada [CMFCOutlookBarPane clase](../../mfc/reference/cmfcoutlookbarpane-class.md) objeto y for each `CWnd`-objeto derivado.  
  
 Para agregar o eliminar nuevas páginas en tiempo de ejecución dinámicamente, use [CMFCOutlookBar::CreateCustomPage](#createcustompage) y [CMFCOutlookBar::RemoveCustomPage](#removecustompage).  
  
## <a name="outlook-2003-mode"></a>Modo de Outlook 2003  
 En el modo de Outlook 2003, los botones de ficha se colocan en la parte inferior del panel de barra de Outlook. Cuando no hay suficiente espacio para mostrar los botones, se muestran como iconos en un área de barra de herramientas similares a lo largo de la parte inferior del panel.  
  
 Use [CMFCOutlookBar::SetMode2003](#setmode2003) para habilitar el modo de Outlook 2003. Use [CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) para establecer el mapa de bits que contiene los iconos que se muestran en la parte inferior de la barra de Outlook. Los iconos del mapa de bits deben estar ordenados por índice de tabulación.  
  
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
 Especifica si un panel con fichas vacío puede ser destruido.  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si un panel con fichas vacío se puedan destruir; en caso contrario, `FALSE`. La implementación predeterminada siempre devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si no se puede destruir un panel con fichas vacío, el marco de trabajo, oculta en su lugar.  
  
##  <a name="canacceptpane"></a>CMFCOutlookBar::CanAcceptPane  
 Determina si el otro panel se puede acoplar en el panel de la barra de Outlook.  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Un puntero a otro panel que se está acoplada a este panel.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si otro panel se puede acoplar en el panel de barra de Outlook; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si la barra de Outlook está en modo de Outlook 2003, acoplamiento no se admite, por lo que el valor devuelto es `FALSE`.  
  
 Si el `pBar` parámetro es `NULL`, este método devuelve `FALSE`.  
  
 En caso contrario, este método se comporta como el método base [cbasepane:: Canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane), excepto que, incluso si no está habilitado el acoplamiento, una barra de Outlook puede habilitar otra barra de Outlook para acoplarse sobre él.  
  
##  <a name="cansetcaptiontexttotabname"></a>CMFCOutlookBar::CanSetCaptionTextToTabName  
 Determina si el título para el panel con pestañas muestra el mismo texto como la pestaña activa.  
  
```  
virtual BOOL CanSetCaptionTextToTabName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la barra de título de la ventana de Outlook se establece automáticamente en el texto de la pestaña activa; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Use [CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname) para habilitar o deshabilitar esta funcionalidad.  
  
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
 Especifica el identificador del control. Debe ser distinto de otro identificadores usados en la aplicación de control.  
  
 [in] `dwStyle`  
 Especifica el estilo de barra de control. Para los valores posibles, vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 [in] `dwControlBarStyle`  
 Especifica los estilos definidos por la biblioteca especiales.  
  
 [in] `pContext`  
 Crear el contexto.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el método es correcto; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CMFCOutlookBar` objeto en dos pasos. Llame primero al constructor y, a continuación, llame a `Create`, que crea el control de barra de outlook y lo adjunta a la `CMFCOutlookBar` objeto.  
  
 Vea [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex) para obtener la lista de los estilos definidos por la biblioteca disponibles que especificarse mediante `dwControlBarStyle`.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método de la `CMFCOutlookBar` clase. Este fragmento de código forma parte de la [ejemplo Outlook varias vistas](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]  
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]  
  
##  <a name="createcustompage"></a>CMFCOutlookBar::CreateCustomPage  
 Crea una pestaña personalizada de barra de Outlook.  
  
```  
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,  
    BOOL bActivatePage=TRUE,  
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,  
    BOOL bEnableTextLabels=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszPageName`  
 La etiqueta de página.  
  
 [in] `bActivatePage`  
 Si `TRUE`, la página se convierte en activa tras su creación.  
  
 [in] `dwEnabledDocking`  
 Una combinación de marcas CBRS_ALIGN_ que especifica los lados de acoplamiento habilitados cuando se separa la página.  
  
 [in] `bEnableTextLabels`  
 Si `TRUE`, se habilitan las etiquetas de texto para los botones que se encuentran en la página.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la página recién creada, o `NULL` si falló la creación.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para permitir a los usuarios crear páginas personalizadas de la barra de Outlook. Puede crear hasta 100 páginas por aplicación. El control de la página identificadores de inicio de 0xF000. La creación se produce un error si el número total de páginas personalizadas de la barra de Outlook es superior a 100.  
  
 Use [CMFCOutlookBar::RemoveCustomPage](#removecustompage) para eliminar las páginas personalizadas.  
  
##  <a name="doesallowdyninsertbefore"></a>CMFCOutlookBar::DoesAllowDynInsertBefore  
 Especifica si un usuario puede acoplar un panel en el borde externo de la barra de Outlook.  
  
```  
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas de framework la `DoesAllowDynInsertBefore` método cuando busque una ubicación acoplar un panel dinámico. Si la función devuelve `FALSE`, el marco de trabajo no permite el acoplamiento de un panel dinámico en los bordes exteriores del panel.  
  
 Normalmente, se crea una barra de Outlook como un control estático no flotante. Puede invalidar esta función en una clase derivada y devolver `TRUE` para cambiar este comportamiento.  
  
> [!NOTE]
>  Dado que paneles dinámicos comprueban el estado de paneles estáticos acoplados al acoplamiento, debe acoplar paneles de dinámicos después paneles estáticos siempre que sea posible.  
  
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
 Un puntero al panel a float.  
  
 [in] `nTabID`  
 Índice de base cero de la pestaña para float.  
  
 [in] `dockMethod`  
 Especifica el método que utilice para hacer flotar el panel.  Para obtener más información, consulte [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab).  
  
 [in] `bHide`  
 `TRUE`Para ocultar el panel antes flotante; en caso contrario, `FALSE`. A diferencia de la versión de la clase base de este método, este parámetro no tiene un valor predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el panel flota; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método es similar a [cbasetabbedpane:: Floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab) salvo que no habilita la última ficha restante en un control de barra de Outlook a float.  
  
##  <a name="getbuttonsfont"></a>CMFCOutlookBar::GetButtonsFont  
 Devuelve a la fuente del texto en la página de fichas de botón de la barra de Outlook.  
  
```  
CFont* GetButtonsFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto de fuente que se utiliza para mostrar texto en Outlook barra fichas de botón de la página.  
  
### <a name="remarks"></a>Comentarios  
 Utilice esta función para recuperar la fuente que se usa para mostrar el texto en las pestañas de botón de página de Outlook. Puede establecer la fuente mediante una llamada en [CMFCOutlookBar::SetButtonsFont](#setbuttonsfont).  
  
##  <a name="gettabarea"></a>CMFCOutlookBar::GetTabArea  
 Determina el tamaño y la posición de las áreas de ficha en la barra de Outlook.  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectTabAreaTop`  
 Cuando la función devuelve, contiene el tamaño y la posición (en las coordenadas de cliente) del área de ficha superior.  
  
 [out] `rectTabAreaBottom`  
 Cuando la función devuelve, contiene el tamaño y la posición (en las coordenadas de cliente) del área de pestañas de la parte inferior.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para determinar el tipo de acoplamiento en el panel de destino. Cuando el marco de trabajo determina que el usuario arrastra el panel de acoplarse en el área de pestañas del panel de destino, intenta agregar el primer panel como una nueva pestaña del panel de destino. En caso contrario, intenta acoplar el primer panel en un lado correspondiente del panel de destino. El marco de trabajo crea un nuevo contenedor con un control deslizante para alojar el panel acoplado adicional.  
  
 La implementación predeterminada de `GetTabArea` devuelve el área de cliente completa de la barra de Outlook, si la barra de Outlook es estático; que es, si no se puede desplazar la barra de Outlook. En caso contrario, devuelve el área que toman los botones de página en la parte superior e inferior del control de barra de Outlook.  
  
 Invalide este método en la clase derivada de `CMFCOutlookBar` para cambiar este comportamiento.  
  
##  <a name="ismode2003"></a>CMFCOutlookBar::IsMode2003  
 Especifica si el comportamiento de la barra de Outlook imita de Microsoft Office Outlook 2003.  
  
```  
BOOL IsMode2003() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la barra de Outlook se ejecuta en modo de Microsoft Office 2003; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede habilitar este modo utilizando [CMFCOutlookBar::SetMode2003](#setmode2003).  
  
##  <a name="onafteranimation"></a>CMFCOutlookBar::OnAfterAnimation  
 Llamado por el método [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) después de que se ha establecido la pestaña activa con animación.  
  
```  
virtual void OnAfterAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPage`  
 Índice de base cero de la página de ficha que se ha realizado active.  
  
### <a name="remarks"></a>Comentarios  
 El efecto de establecer la pestaña activa visual depende de si ha habilitado la animación. Para obtener más información, consulte [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation).  
  
##  <a name="onbeforeanimation"></a>CMFCOutlookBar::OnBeforeAnimation  
 Llamado por el método [CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab) antes de una pestaña de página se establece como la pestaña activa con animación.  
  
```  
virtual BOOL OnBeforeAnimation(int nPage);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nPage`  
 Índice de base cero de la ficha que se va a establecerse activo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la animación se debe usar en la configuración de la pestaña activa de nuevo, o `FALSE` si se debe deshabilitar la animación.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="onscroll"></a>CMFCOutlookBar::OnScroll  
 Lo llama el marco de trabajo si la barra de Outlook se desplaza hacia arriba o hacia abajo.  
  
```  
virtual void OnScroll(BOOL bDown);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDown`  
 `TRUE`Si la barra de Outlook se desplace hacia abajo, o `FALSE` si se desplaza hacia arriba.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="removecustompage"></a>CMFCOutlookBar::RemoveCustomPage  
 Quita una página de fichas de barra de Outlook personalizada.  
  
```  
BOOL RemoveCustomPage(
    UINT uiPage,  
    CMFCOutlookBarTabCtrl* pTargetWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiPage`  
 Índice de base cero de la página en la ventana de Outlook primaria.  
  
 [in] `pTargetWnd`  
 Pointerto la ventana de Outlook primaria.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la página personalizada se ha quitado correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para eliminar las páginas personalizadas. Cuando se quita la página de su Id. de control se devuelve al grupo de identificadores disponibles.  
  
 Debe proporcionar un puntero a [CMFCOutlookBarTabCtrl Class](../../mfc/reference/cmfcoutlookbartabctrl-class.md) objeto en el que reside la página que se va a quitar actualmente. Tenga en cuenta que un usuario puede mover las páginas separables entre diferentes barras de Outlook, pero la información sobre una página personalizada se encuentra en el objeto de barra de Outlook para la que se llamó a [CMFCOutlookBar::CreateCustomPage](#createcustompage).  
  
 Use [CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) para obtener un puntero a la ventana de Outlook.  
  
##  <a name="setbuttonsfont"></a>CMFCOutlookBar::SetButtonsFont  
 Establece la fuente del texto en los botones de la barra de Outlook.  
  
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
 Utilice este método para establecer una fuente para el texto mostrado en los botones de página de la ficha de outlook.  
  
##  <a name="setmode2003"></a>CMFCOutlookBar::SetMode2003  
 Especifica si el comportamiento de la barra de Outlook imita de Outlook 2003.  
  
```  
void SetMode2003(BOOL bMode2003=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMode2003`  
 Si es TRUE, se habilita el modo de Office 2003.  
  
### <a name="remarks"></a>Comentarios  
 Use esta función para habilitar o deshabilitar el modo de Office 2003. En este modo, la barra de Outlook tiene una barra de herramientas adicional con un botón de personalización. El comportamiento de la barra de Outlook se ajusta al comportamiento de la barra de Outlook de Microsoft Office 2003.  
  
 De forma predeterminada, este modo está deshabilitado.  
  
> [!NOTE]
>  Esta función debe llamarse antes [CMFCOutlookBar::Create](#create).  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CBaseTabbedPane (clase)](../../mfc/reference/cbasetabbedpane-class.md)   
 [Clase CMFCOutlookBarTabCtrl](../../mfc/reference/cmfcoutlookbartabctrl-class.md)   
 [CMFCOutlookBarPane (clase)](../../mfc/reference/cmfcoutlookbarpane-class.md)
