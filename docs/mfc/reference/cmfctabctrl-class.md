---
title: Clase CMFCTabCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl::ActivateMDITab
- AFXTABCTRL/CMFCTabCtrl::AllowDestroyEmptyTabbedPane
- AFXTABCTRL/CMFCTabCtrl::AutoSizeWindow
- AFXTABCTRL/CMFCTabCtrl::CalcRectEdit
- AFXTABCTRL/CMFCTabCtrl::Create
- AFXTABCTRL/CMFCTabCtrl::EnableActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::EnableInPlaceEdit
- AFXTABCTRL/CMFCTabCtrl::EnableTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::EnsureVisible
- AFXTABCTRL/CMFCTabCtrl::GetDocumentIcon
- AFXTABCTRL/CMFCTabCtrl::GetFirstVisibleTabNum
- AFXTABCTRL/CMFCTabCtrl::GetResizeMode
- AFXTABCTRL/CMFCTabCtrl::GetScrollBar
- AFXTABCTRL/CMFCTabCtrl::GetTabArea
- AFXTABCTRL/CMFCTabCtrl::GetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::GetTabsHeight
- AFXTABCTRL/CMFCTabCtrl::GetTabsRect
- AFXTABCTRL/CMFCTabCtrl::GetWndArea
- AFXTABCTRL/CMFCTabCtrl::HideActiveWindowHorzScrollBar
- AFXTABCTRL/CMFCTabCtrl::HideInactiveWindow
- AFXTABCTRL/CMFCTabCtrl::HideNoTabs
- AFXTABCTRL/CMFCTabCtrl::HideSingleTab
- AFXTABCTRL/CMFCTabCtrl::IsActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::IsDrawFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatTab
- AFXTABCTRL/CMFCTabCtrl::IsLeftRightRounded
- AFXTABCTRL/CMFCTabCtrl::IsMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsOneNoteStyle
- AFXTABCTRL/CMFCTabCtrl::IsSharedScroll
- AFXTABCTRL/CMFCTabCtrl::IsTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::IsVS2005Style
- AFXTABCTRL/CMFCTabCtrl::ModifyTabStyle
- AFXTABCTRL/CMFCTabCtrl::OnDragEnter
- AFXTABCTRL/CMFCTabCtrl::OnDragOver
- AFXTABCTRL/CMFCTabCtrl::OnShowTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::SetActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::SetActiveTab
- AFXTABCTRL/CMFCTabCtrl::SetActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::SetDrawFrame
- AFXTABCTRL/CMFCTabCtrl::SetFlatFrame
- AFXTABCTRL/CMFCTabCtrl::SetImageList
- AFXTABCTRL/CMFCTabCtrl::SetResizeMode
- AFXTABCTRL/CMFCTabCtrl::SetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::StopResize
- AFXTABCTRL/CMFCTabCtrl::SynchronizeScrollBar
- AFXTABCTRL/CMFCTabCtrl::m_bEnableActivate
dev_langs: C++
helpviewer_keywords:
- CMFCTabCtrl [MFC], ActivateMDITab
- CMFCTabCtrl [MFC], AllowDestroyEmptyTabbedPane
- CMFCTabCtrl [MFC], AutoSizeWindow
- CMFCTabCtrl [MFC], CalcRectEdit
- CMFCTabCtrl [MFC], Create
- CMFCTabCtrl [MFC], EnableActiveTabCloseButton
- CMFCTabCtrl [MFC], EnableInPlaceEdit
- CMFCTabCtrl [MFC], EnableTabDocumentsMenu
- CMFCTabCtrl [MFC], EnsureVisible
- CMFCTabCtrl [MFC], GetDocumentIcon
- CMFCTabCtrl [MFC], GetFirstVisibleTabNum
- CMFCTabCtrl [MFC], GetResizeMode
- CMFCTabCtrl [MFC], GetScrollBar
- CMFCTabCtrl [MFC], GetTabArea
- CMFCTabCtrl [MFC], GetTabMaxWidth
- CMFCTabCtrl [MFC], GetTabsHeight
- CMFCTabCtrl [MFC], GetTabsRect
- CMFCTabCtrl [MFC], GetWndArea
- CMFCTabCtrl [MFC], HideActiveWindowHorzScrollBar
- CMFCTabCtrl [MFC], HideInactiveWindow
- CMFCTabCtrl [MFC], HideNoTabs
- CMFCTabCtrl [MFC], HideSingleTab
- CMFCTabCtrl [MFC], IsActiveInMDITabGroup
- CMFCTabCtrl [MFC], IsActiveTabBoldFont
- CMFCTabCtrl [MFC], IsActiveTabCloseButton
- CMFCTabCtrl [MFC], IsDrawFrame
- CMFCTabCtrl [MFC], IsFlatFrame
- CMFCTabCtrl [MFC], IsFlatTab
- CMFCTabCtrl [MFC], IsLeftRightRounded
- CMFCTabCtrl [MFC], IsMDITabGroup
- CMFCTabCtrl [MFC], IsOneNoteStyle
- CMFCTabCtrl [MFC], IsSharedScroll
- CMFCTabCtrl [MFC], IsTabDocumentsMenu
- CMFCTabCtrl [MFC], IsVS2005Style
- CMFCTabCtrl [MFC], ModifyTabStyle
- CMFCTabCtrl [MFC], OnDragEnter
- CMFCTabCtrl [MFC], OnDragOver
- CMFCTabCtrl [MFC], OnShowTabDocumentsMenu
- CMFCTabCtrl [MFC], SetActiveInMDITabGroup
- CMFCTabCtrl [MFC], SetActiveTab
- CMFCTabCtrl [MFC], SetActiveTabBoldFont
- CMFCTabCtrl [MFC], SetDrawFrame
- CMFCTabCtrl [MFC], SetFlatFrame
- CMFCTabCtrl [MFC], SetImageList
- CMFCTabCtrl [MFC], SetResizeMode
- CMFCTabCtrl [MFC], SetTabMaxWidth
- CMFCTabCtrl [MFC], StopResize
- CMFCTabCtrl [MFC], SynchronizeScrollBar
- CMFCTabCtrl [MFC], m_bEnableActivate
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1aa415846d8f504ef907bf4e9a041b86062853cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cmfctabctrl-class"></a>CMFCTabCtrl Class
La `CMFCTabCtrl` clase proporciona la funcionalidad para un control de pestaña. El control de pestaña muestra una ventana acoplable con pestañas planas o tridimensionales en la parte superior o inferior. Las pestañas pueden mostrar texto y una imagen y pueden cambiar de color cuando están activas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCTabCtrl::CMFCTabCtrl`|Constructor predeterminado.|  
|`CMFCTabCtrl::~CMFCTabCtrl`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTabCtrl::ActivateMDITab](#activatemditab)|Muestra la ficha especificada del control de ficha actual y establece el foco en esa pestaña.|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)||  
|[CMFCTabCtrl::AutoSizeWindow](#autosizewindow)|Especifica si el marco de trabajo es cambiar el tamaño del área de cliente de todas las ventanas de control de ficha cuando un elemento de la interfaz de usuario de los cambios de control de pestaña.|  
|[CMFCTabCtrl::CalcRectEdit](#calcrectedit)|Desinfla el tamaño del área de ficha especificado. (Invalida `CMFCBaseTabCtrl::CalcRectEdit`).|  
|[CMFCTabCtrl::Create](#create)|Crea el control de ficha y se adjunta a la `CMFCTabCtrl` objeto.|  
|`CMFCTabCtrl::CreateObject`|Usado por el marco para crear una instancia dinámica de este tipo de clase.|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](#enableactivetabclosebutton)|Muestra u oculta el botón Cerrar ( **X**) en la pestaña activa.|  
|[CMFCTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|Habilita o deshabilita las etiquetas de pestaña editable. (Invalida [CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit).)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)|Reemplaza los dos botones que desplazarse por las fichas de la ventana con un botón que abre un menú de las ventanas con pestañas.|  
|[CMFCTabCtrl::EnsureVisible](#ensurevisible)|Garantiza que una pestaña esté visible.|  
|[CMFCTabCtrl::GetDocumentIcon](#getdocumenticon)|Recupera el símbolo que está asociado a una pestaña en un menú emergente de ventanas con fichas.|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)|Recupera el índice de la primera ficha que se muestra en el control de ficha actual.|  
|[CMFCTabCtrl::GetResizeMode](#getresizemode)|Recupera un valor que especifica cómo se puede cambiar el tamaño de control de ficha actual.|  
|[CMFCTabCtrl::GetScrollBar](#getscrollbar)|Recupera un puntero al objeto de barra de desplazamiento que está asociado con el control de ficha.|  
|[CMFCTabCtrl::GetTabArea](#gettabarea)|Recupera el rectángulo delimitador del área de etiqueta de ficha en la parte superior o inferior del control de ficha. (Invalida [CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea).)|  
|`CMFCTabCtrl::GetTabFromPoint`|Recupera la pestaña que contiene un punto especificado. (Invalida [CMFCBaseTabCtrl::GetTabFromPoint](../../mfc/reference/cmfcbasetabctrl-class.md#gettabfrompoint).)|  
|[CMFCTabCtrl::GetTabMaxWidth](#gettabmaxwidth)|Recupera el ancho máximo de una pestaña.|  
|[CMFCTabCtrl::GetTabsHeight](#gettabsheight)|Recupera el alto del área de ficha del control de ficha actual.|  
|[CMFCTabCtrl::GetTabsRect](#gettabsrect)|Recupera un rectángulo que delimita el área de fichas del control de ficha actual. (Invalida [CMFCBaseTabCtrl::GetTabsRect](../../mfc/reference/cmfcbasetabctrl-class.md#gettabsrect).)|  
|`CMFCTabCtrl::GetThisClass`|Usado por el marco de trabajo para obtener un puntero a la [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objeto que está asociado a este tipo de clase.|  
|[CMFCTabCtrl::GetWndArea](#getwndarea)|Recupera los límites del área cliente del control de ficha actual.|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)|Oculta la barra de desplazamiento horizontal, si la hubiera, de la ventana activa.|  
|[CMFCTabCtrl::HideInactiveWindow](#hideinactivewindow)|Especifica si el marco de trabajo consiste en Mostrar ventanas de control de pestaña inactiva.|  
|[CMFCTabCtrl::HideNoTabs](#hidenotabs)|Habilita o deshabilita el área de pestañas de dibujo si no hay ningún pestañas visibles.|  
|[CMFCTabCtrl::HideSingleTab](#hidesingletab)|Habilita o deshabilita el dibujo de una ficha cuando hay una sola ventana con pestañas. (Invalida [CMFCBaseTabCtrl::HideSingleTab](../../mfc/reference/cmfcbasetabctrl-class.md#hidesingletab).)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](#isactiveinmditabgroup)|Indica si la ficha actual de un control de ficha es la pestaña activa en un grupo de pestañas de interfaz de varios documentos.|  
|[CMFCTabCtrl::IsActiveTabBoldFont](#isactivetabboldfont)|Indica si el texto de la pestaña activa se muestra con una fuente en negrita.|  
|[CMFCTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)|Indica si el botón Cerrar ( **X**) se muestra en una pestaña activa o en la esquina superior derecha del área de ficha.|  
|[CMFCTabCtrl::IsDrawFrame](#isdrawframe)|Indica si la ventana con pestañas dibuja un rectángulo de marco alrededor de paneles incrustados.|  
|[CMFCTabCtrl::IsFlatFrame](#isflatframe)|Indica si el marco que rodea el área de pestañas es plano o 3D.|  
|[CMFCTabCtrl::IsFlatTab](#isflattab)|Indica si la apariencia de las fichas en el control de pestaña actual es plano o no.|  
|[CMFCTabCtrl::IsLeftRightRounded](#isleftrightrounded)|Indica si se redondea la apariencia de los lados izquierdo y derecho de una pestaña en el control de ficha actual.|  
|[CMFCTabCtrl::IsMDITabGroup](#ismditabgroup)|Indica si el control de ficha actual se encuentra en el área de cliente de una ventana de interfaz de múltiples documentos.|  
|[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)|Indica si el control de ficha actual se muestra en el estilo de Microsoft OneNote.|  
|`CMFCTabCtrl::IsPtInTabArea`|Determina si un punto está dentro del área de pestaña. (Invalida [CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea).)|  
|[CMFCTabCtrl::IsSharedScroll](#issharedscroll)|Indica si el control de ficha actual tiene una barra de desplazamiento que se puede desplazar sus pestañas como un grupo.|  
|[CMFCTabCtrl::IsTabDocumentsMenu](#istabdocumentsmenu)|Indica si el control de pestaña muestra los botones de desplazamiento o un botón que muestra un menú de las ventanas con pestañas.|  
|[CMFCTabCtrl::IsVS2005Style](#isvs2005style)|Indica si las pestañas se muestran en el estilo de Visual Studio .NET 2005.|  
|[CMFCTabCtrl::ModifyTabStyle](#modifytabstyle)|Especifica la apariencia de fichas en el control de ficha actual.|  
|`CMFCTabCtrl::MoveTab`|Mueve una pestaña a otra posición de tabulación. (Invalida [CMFCBaseTabCtrl::MoveTab](../../mfc/reference/cmfcbasetabctrl-class.md#movetab).)|  
|[CMFCTabCtrl::OnDragEnter](#ondragenter)|Lo llama el marco cuando el cursor se arrastra en primer lugar en la ventana de control de pestaña.|  
|[CMFCTabCtrl::OnDragOver](#ondragover)|Lo llama el marco de trabajo durante una operación de arrastre cuando se mueve el mouse sobre la ventana de destino de colocación. (Invalida [CMFCBaseTabCtrl::OnDragOver](../../mfc/reference/cmfcbasetabctrl-class.md#ondragover).)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](#onshowtabdocumentsmenu)|Muestra un menú emergente de ventanas con pestañas, espera hasta que el usuario selecciona una ficha y hace que la pestaña seleccionada la pestaña activa.|  
|`CMFCTabCtrl::PreTranslateMessage`|Convierte los mensajes de ventana antes de que se envíen a la [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funciones de Windows. (Invalida [CMFCBaseTabCtrl::PreTranslateMessage](../../mfc/reference/cmfcbasetabctrl-class.md#pretranslatemessage).)|  
|`CMFCTabCtrl::RecalcLayout`|Vuelve a calcular el diseño interno del control de ficha. (Invalida [CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout).)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](#setactiveinmditabgroup)|La ficha actual de un control de ficha se establece como la pestaña activa en un grupo de pestañas de interfaz de varios documentos.|  
|[CMFCTabCtrl::SetActiveTab](#setactivetab)|Activa una pestaña. (Invalida [CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab).)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)|Habilita o deshabilita el uso de una fuente en negrita en las pestañas activas.|  
|[CMFCTabCtrl::SetDrawFrame](#setdrawframe)|Habilita o deshabilita el rectángulo de trama drawinga alrededor de una barra incrustada.|  
|[CMFCTabCtrl::SetFlatFrame](#setflatframe)|Especifica si se debe dibujar un plano o una trama de 3D alrededor del área de pestaña.|  
|[CMFCTabCtrl::SetImageList](#setimagelist)|Especifica una lista de imágenes. (Invalida [CMFCBaseTabCtrl::SetImageList](../../mfc/reference/cmfcbasetabctrl-class.md#setimagelist).)|  
|[CMFCTabCtrl::SetResizeMode](#setresizemode)|Especifica cómo se puede cambiar el tamaño de control de ficha actual y, a continuación, vuelve a mostrar el control.|  
|[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)|Especifica el ancho máximo de ficha en una ventana con pestañas.|  
|[CMFCTabCtrl::StopResize](#stopresize)|Finaliza la operación de cambio de tamaño actual en el control de ficha.|  
|`CMFCTabCtrl::SwapTabs`|Intercambia un par de pestañas. (Invalida [CMFCBaseTabCtrl::SwapTabs](../../mfc/reference/cmfcbasetabctrl-class.md#swaptabs).)|  
|[CMFCTabCtrl::SynchronizeScrollBar](#synchronizescrollbar)|Dibuja una barra de desplazamiento horizontal de un control de ficha que muestra pestañas sin formato.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CMFCTabCtrl::m_bEnableActivate](#m_benableactivate)|Impide que pierde el foco cuando se inserta una nueva pestaña y se habilita la vista activa.|  
  
## <a name="remarks"></a>Comentarios  
 La `CMFCTabCtrl` clase es compatible con:  
  
-   Pestaña estilos de control que incluyan 3D, sin formato y sin formato con una barra de desplazamiento horizontal compartida.  
  
-   Pestañas situadas en la parte superior o inferior de la ventana.  
  
-   Pestañas que muestran texto, imágenes, o texto e imágenes.  
  
-   Pestañas que cambian de color cuando la pestaña está activa.  
  
-   Cambios de tamaño de borde para las pestañas ajustables.  
  
-   Ventanas con pestañas separables.  
  
 El `CMFCTabCtrl` clase puede usarse con un cuadro de diálogo, pero está pensado para las aplicaciones que utilizan acoplamiento controlan barras como [!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)] y [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]. Para obtener más información, consulte [clase CDockablePane](../../mfc/reference/cdockablepane-class.md).  
  
 Siga estos pasos para agregar un puede cambiar el tamaño, acoplar el control de pestaña en la aplicación:  
  
1.  Cree una instancia de [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md).  
  
2.  Llame a [CDockablePane::Create](../../mfc/reference/cdockablepane-class.md#create).  
  
3.  Use [cbasetabbedpane:: addTab](../../mfc/reference/cbasetabbedpane-class.md#addtab) o [cmfcbasetabctrl:: insertTab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab) para agregar nuevas pestañas.  
  
4.  Llame a [CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) por lo que puede acoplar el control de pestaña de acoplamiento actual en la ventana de marco principal.  
  
5.  Llame a [CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane) para acoplar la ventana con pestañas en el marco principal.  
  
 Para obtener un ejemplo de cómo crear una ventana con fichas como una barra de control de acoplamiento, vea [CTabbedPane clase](../../mfc/reference/ctabbedpane-class.md). Usar `CMFCTabCtrl` como un control no acoplamiento, cree un `CMFCTabCtrl` objeto y, a continuación, llame a [CMFCTabCtrl::Create](#create).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar distintos métodos en el `CMFCTabCtrl` clase para configurar un `CMFCTabCtrl` objeto. En el ejemplo se explica cómo agregar una pestaña, mostrar el botón de cierre en la pestaña activa, habilitar las etiquetas de pestaña editable y mostrar un menú emergente de etiquetas de ventana con pestañas. Este ejemplo forma parte de la [ejemplo de la colección de estados](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxtabctrl.h  
  
##  <a name="activatemditab"></a>CMFCTabCtrl::ActivateMDITab  
 Muestra la ficha especificada del control de ficha actual y establece el foco en esa pestaña.  
  
```  
void ActivateMDITab(int nTab = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTab`  
 Índice de base cero de una pestaña para mostrar, o -1 para especificar la pestaña actualmente activa.  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCTabCtrl::AllowDestroyEmptyTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="autosizewindow"></a>CMFCTabCtrl::AutoSizeWindow  
 Especifica si el marco de trabajo es cambiar el tamaño del área de cliente de todas las ventanas de control de ficha cuando un elemento de la interfaz de usuario de los cambios de control de pestaña.  
  
```  
void AutoSizeWindow(BOOL bAutoSize = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoSize`  
 `TRUE`Para cambiar automáticamente el tamaño de las ventanas de control de pestaña; en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="create"></a>CMFCTabCtrl::Create  
 Crea el control de ficha y se adjunta a la `CMFCTabCtrl` objeto.  
  
```  
BOOL Create(
    Style style,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    Location location=LOCATION_BOTTOM,  
    BOOL bCloseBtn=FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `style`  
 El estilo del control de ficha. Para obtener más información, vea la sección Comentarios.  
  
 [in] `rect`  
 Un rectángulo que delimita el control de ficha.  
  
 [in] `pParentWnd`  
 Un puntero a una ventana primaria. No debe ser `NULL`.  
  
 [in] `nID`  
 El identificador del control de ficha.  
  
 [in] `location`  
 La ubicación de las pestañas. El valor predeterminado es `LOCATION_BOTTOM`. Para obtener más información, vea la sección Comentarios.  
  
 [in] `bCloseBtn`  
 `TRUE`para mostrar un botón de cierre en la ficha; en caso contrario, `FALSE`. El valor predeterminado es `FALSE`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En la tabla siguiente se describe los valores que puede especificar para el `style` parámetro.  
  
|Estilo|Descripción|  
|-----------|-----------------|  
|STYLE_3D|Crea un control de pestaña con un aspecto tridimensional.|  
|STYLE_FLAT|Crea un control de pestaña con pestañas planas.|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|Crea un control de pestaña con pestañas sin formato y una barra de desplazamiento que se puede desplazar las fichas si se recortan una ventana primaria.|  
|STYLE_3D_ONENOTE|Crea un control de ficha en el estilo de Microsoft OneNote.|  
|STYLE_3D_VS2005|Crea un control de ficha en el estilo de Microsoft Visual Studio 2005.|  
|STYLE_3D_ROUNDED|Crea un control de pestaña con pestañas redondeadas en el estilo de Microsoft Visual Studio 2005.|  
|STYLE_3D_ROUNDED_SCROLL|Crea un control de pestaña con pestañas redondeadas y los botones de desplazamiento en el estilo de Microsoft Visual Studio 2005.|  
  
 En la tabla siguiente se enumera los valores que puede especificar para el `location` parámetro.  
  
|Ubicación|Descripción|  
|--------------|-----------------|  
|LOCATION_BOTTOM|Las pestañas se encuentran en la parte inferior del control de ficha.|  
|LOCATION_TOP|Las pestañas se encuentran en la parte superior del control de ficha.|  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `Create` método en la `CMFCTabCtrl` clase. Este ejemplo forma parte de la [ejemplo de la colección de estados](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#2](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_3.cpp)]  
  
##  <a name="calcrectedit"></a>CMFCTabCtrl::CalcRectEdit  
 Desinfla el tamaño del área de ficha especificado.  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `rectEdit`  
 Un rectángulo que especifica el área de una pestaña.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a este método cuando se cambia la etiqueta de una pestaña. Este método desinfla los lados izquierdo y derecho del rectángulo especificado por la mitad del alto actual de pestaña y desinfla superior e inferior en una unidad.  
  
##  <a name="enableactivetabclosebutton"></a>CMFCTabCtrl::EnableActiveTabCloseButton  
 Muestra u oculta el botón Cerrar ( **X**) en la pestaña activa.  
  
```  
void EnableActiveTabCloseButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para mostrar el botón de cierre en la pestaña activa; `FALSE` para mostrar el botón Cerrar en la esquina superior derecha del área de ficha. El valor predeterminado es `TRUE`.  
  
##  <a name="enableinplaceedit"></a>CMFCTabCtrl::EnableInPlaceEdit  
 Habilita o deshabilita las etiquetas de pestaña editable.  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`Para habilitar las etiquetas de pestaña editable; `FALSE` para deshabilitar las etiquetas de pestaña editable.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="enabletabdocumentsmenu"></a>CMFCTabCtrl::EnableTabDocumentsMenu  
 Alterna entre la interfaz de usuario que utiliza dos botones para desplazarse por las fichas de la ventana y una interfaz que muestra un menú emergente de ventanas con fichas.  
  
```  
void EnableTabDocumentsMenu(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE`para mostrar un menú emergente de etiquetas de ventana con pestañas; `FALSE` para mostrar botones de desplazamiento hacia delante y hacia atrás. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario hace clic en una etiqueta de ficha, el marco de trabajo muestra la ventana con pestañas correspondiente. Si está visible la etiqueta de ficha, se abre la ventana con pestañas sin cambiar su posición. Si el usuario selecciona un documento en el menú emergente y la correspondiente ventana con pestañas está fuera de la pantalla, la ventana con pestañas se convierte en la primera pestaña.  
  
##  <a name="ensurevisible"></a>CMFCTabCtrl::EnsureVisible  
 Garantiza que una pestaña esté visible.  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Índice de base cero de una pestaña.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si es correcto; `FALSE` si el `iTab` índice de parámetro no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para garantizar que la ficha especificada sea visible. Si es necesario, se desplazará el control de ficha.  
  
##  <a name="getdocumenticon"></a>CMFCTabCtrl::GetDocumentIcon  
 Recupera la imagen que está asociada a una pestaña en un menú emergente de ventanas con fichas.  
  
```  
static HICON __stdcall GetDocumentIcon(UINT nCmdID);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nCmdID`  
 El identificador de comando de una pestaña de un menú emergente de ventanas con fichas.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de una imagen de mapa de bits.  
  
##  <a name="getfirstvisibletabnum"></a>CMFCTabCtrl::GetFirstVisibleTabNum  
 Recupera el índice de la primera ficha que se muestra en el control de ficha actual.  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Índice de base cero de una pestaña en el control de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Use este método solo cuando el control de pestaña se muestra en el estilo de Microsoft OneNote. Use la [CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle) método para determinar el estilo.  
  
##  <a name="getresizemode"></a>CMFCTabCtrl::GetResizeMode  
 Recupera un valor que especifica cómo se puede cambiar el tamaño de control de ficha actual.  
  
```  
ResizeMode GetResizeMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los `CMFCTabCtrl::ResizeMode` valores de enumeración que especifica cómo se puede cambiar el tamaño de control de pestaña. Para obtener una lista de valores posibles, vea la sección Comentarios de la [CMFCTabCtrl::SetResizeMode](#setresizemode) método.  
  
##  <a name="getscrollbar"></a>CMFCTabCtrl::GetScrollBar  
 Recupera un puntero al objeto de barra de desplazamiento que está asociado con el control de ficha.  
  
```  
CScrollBar* GetScrollBar();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un objeto de barra de desplazamiento o un `NULL` si el control de ficha no se creó mediante la `STYLE_FLAT_SHARED_HORZ_SCROLL` estilo.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para tener acceso a la barra de desplazamiento incrustado del control de pestaña. Se crea un objeto de barra de desplazamiento solamente cuando el control de ficha no tiene la `STYLE_FLAT_SHARED_HORZ_SCROLL` estilo.  
  
##  <a name="gettabarea"></a>CMFCTabCtrl::GetTabArea  
 Recupera el rectángulo delimitador del área de etiqueta de ficha en la parte superior o inferior del control de ficha.  
  
```  
void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rectTabAreaTop`  
 Cuando este método vuelve, esta referencia contiene un rectángulo que delimita el área de etiqueta de ficha superior. El rectángulo está en coordenadas de cliente. Esta referencia está vacía si no existe ningún área de etiqueta de ficha en la parte superior del control de ficha.  
  
 [out] `rectTabAreaBottom`  
 Cuando este método vuelve, esta referencia contiene un rectángulo que delimita el área de etiqueta de ficha inferior. El rectángulo está en coordenadas de cliente. Esta referencia está vacía si no existe ningún área de etiqueta de ficha en la parte inferior del control de ficha.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para determinar el tamaño y la posición del área de ficha en la ventana con pestañas.  
  
##  <a name="gettabmaxwidth"></a>CMFCTabCtrl::GetTabMaxWidth  
 Recupera el ancho máximo de una pestaña.  
  
```  
int GetTabMaxWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Ancho máximo de una pestaña, en píxeles. Si el valor devuelto es 0, el ancho de la pestaña es ilimitado.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth) método para establecer el ancho máximo de pestaña.  
  
##  <a name="gettabsheight"></a>CMFCTabCtrl::GetTabsHeight  
 Recupera el alto del área de ficha del control de ficha actual.  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El alto del área de ficha si cualquier ficha está visible, o cero si no existe la ficha está visible.  
  
##  <a name="gettabsrect"></a>CMFCTabCtrl::GetTabsRect  
 Recupera un rectángulo que delimita el área de fichas del control de ficha actual.  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `rect`  
 Cuando este método finaliza, el `rect` parámetro contiene un rectángulo que delimita el área de pestañas.  
  
##  <a name="getwndarea"></a>CMFCTabCtrl::GetWndArea  
 Recupera los límites del área cliente del control de ficha actual.  
  
```  
void GetWndArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in, out] `rect`  
 Cuando este método finaliza, este parámetro contiene un rectángulo que delimita el control de ficha actual.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hideactivewindowhorzscrollbar"></a>CMFCTabCtrl::HideActiveWindowHorzScrollBar  
 Oculta la barra de desplazamiento horizontal, si existe alguno, en la ventana activa.  
  
```  
void HideActiveWindowHorzScrollBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para impedir que el control de pestaña parpadea cuando el usuario cambia entre las páginas de control de pestaña.  
  
##  <a name="hideinactivewindow"></a>CMFCTabCtrl::HideInactiveWindow  
 Especifica si el marco de trabajo muestra las ventanas de control de pestaña inactiva.  
  
```  
void HideInactiveWindow(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHide`  
 `TRUE`no se muestre una ventana inactiva; `FALSE` para mostrar una ventana inactiva. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hidenotabs"></a>CMFCTabCtrl::HideNoTabs  
 Habilita o deshabilita el dibujo del área de ficha, si no hay ningún pestañas visibles.  
  
```  
void HideNoTabs(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHide`  
 `TRUE`Para habilitar el área de pestañas; de dibujo `FALSE` para deshabilitar el dibujo. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="hidesingletab"></a>CMFCTabCtrl::HideSingleTab  
 Habilita o deshabilita el dibujo de la ficha si hay una sola ventana con pestañas.  
  
```  
virtual void HideSingleTab(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bHide`  
 `TRUE`para dibujar no una pestaña de una sola ventana con pestañas; `FALSE` para dibujar una única ficha. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isactiveinmditabgroup"></a>CMFCTabCtrl::IsActiveInMDITabGroup  
 Indica si la ficha actual de un control de ficha es la pestaña activa en un grupo de pestañas de interfaz de múltiples documentos.  
  
```  
BOOL IsActiveInMDITabGroup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ficha actual de un control de ficha es la pestaña activa en un grupo de pestañas MDI; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Puede organizar varias ventanas de documento en ambos grupos de pestañas horizontales o verticales y mover fácilmente los documentos de un grupo a otro.  
  
##  <a name="isactivetabboldfont"></a>CMFCTabCtrl::IsActiveTabBoldFont  
 Indica si el texto de la pestaña activa se muestra con una fuente en negrita.  
  
```  
BOOL IsActiveTabBoldFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se muestra la pestaña activa con la fuente en negrita; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont) método para cambiar la fuente de la pestaña activa.  
  
##  <a name="isactivetabclosebutton"></a>CMFCTabCtrl::IsActiveTabCloseButton  
 Indica si el botón Cerrar ( **X**) se muestra en una pestaña activa o en la esquina superior derecha del área de ficha.  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el botón de cierre se muestra en la pestaña activa; `FALSE` si se muestra el botón Cerrar en la esquina superior derecha del área de ficha.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="isdrawframe"></a>CMFCTabCtrl::IsDrawFrame  
 Indica si la ventana con pestañas dibuja un rectángulo de marco alrededor de paneles incrustados.  
  
```  
BOOL IsDrawFrame() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se dibuja un rectángulo de trama; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCTabCtrl::SetDrawFrame](#setdrawframe) método para habilitar o deshabilitar dibujar un rectángulo de trama.  
  
##  <a name="isflatframe"></a>CMFCTabCtrl::IsFlatFrame  
 Indica si el marco que rodea el área de pestañas es plano o 3D.  
  
```  
BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el marco que rodea el área de pestañas es plano; `FALSE` si el fotograma es tridimensional.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCTabCtrl::SetFlatFrame](#setflatframe) método para cambiar cómo se dibuja el marco.  
  
##  <a name="isflattab"></a>CMFCTabCtrl::IsFlatTab  
 Indica si la apariencia de las fichas en el control de pestaña actual es plano o no.  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la apariencia de las fichas en el control de pestaña actual es plana; en caso contrario, `FALSE`.  
  
##  <a name="isleftrightrounded"></a>CMFCTabCtrl::IsLeftRightRounded  
 Indica si se redondea la apariencia de los lados izquierdo y derecho de una pestaña en el control de ficha actual.  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se redondea los lados de cada ficha; en caso contrario, `FALSE`.  
  
##  <a name="ismditabgroup"></a>CMFCTabCtrl::IsMDITabGroup  
 Indica si el control de ficha actual se encuentra en el área de cliente de una ventana de interfaz de múltiples documentos.  
  
```  
virtual BOOL IsMDITabGroup() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de pestaña actual está en una ventana de área de cliente MDI; en caso contrario, `FALSE`.  
  
##  <a name="isonenotestyle"></a>CMFCTabCtrl::IsOneNoteStyle  
 Indica si el control de ficha actual se muestra en el estilo de Microsoft OneNote.  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de pestaña se muestra en el estilo de OneNote de Microsoft; en caso contrario, `FALSE`.  
  
##  <a name="issharedscroll"></a>CMFCTabCtrl::IsSharedScroll  
 Indica si el control de ficha actual tiene una barra de desplazamiento que se puede desplazar sus pestañas como un grupo.  
  
```  
BOOL IsSharedScroll() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el control de ficha tiene una barra de desplazamiento compartido; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si la `style` parámetro de la [CMFCTabCtrl::Create](#create) método es STYLE_FLAT_SHARED_HORZ_SCROLL.  
  
##  <a name="istabdocumentsmenu"></a>CMFCTabCtrl::IsTabDocumentsMenu  
 Indica si el control de pestaña muestra los botones de desplazamiento o un botón que muestra un menú de las ventanas con pestañas.  
  
```  
BOOL IsTabDocumentsMenu() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se desplazan ventanas con fichas mediante un menú emergente de etiquetas de ventana con pestañas; `FALSE` si ventanas con fichas se desplazan con los botones de desplazamiento hacia delante y hacia atrás.  
  
### <a name="remarks"></a>Comentarios  
 Use la [CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu) método para especificar el método de desplazamiento con pestañas de windows.  
  
##  <a name="isvs2005style"></a>CMFCTabCtrl::IsVS2005Style  
 Indica si las pestañas se dibujan utilizando el estilo de Visual Studio 2005.  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las pestañas se dibujan usando el estilo de Visual Studio 2005; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Use la `style` parámetro de la [CMFCTabCtrl::Create](#create) método para especificar cómo se dibujan las fichas.  
  
##  <a name="m_benableactivate"></a>CMFCTabCtrl::m_bEnableActivate  
 Impide que pierde el foco cuando se inserta una nueva pestaña y se habilita la vista activa.  
  
```  
static BOOL m_bEnableActivate;  
```  
  
### <a name="remarks"></a>Comentarios  
 El foco se realiza normalmente por una nueva ventana con pestañas cuando se inserta y se activa la ficha. Establecer el `CMFCTabCtrl::m_bEnableActivate` variable miembro en `FALSE` para conservar el foco original. El valor predeterminado es `TRUE`.  
  
##  <a name="modifytabstyle"></a>CMFCTabCtrl::ModifyTabStyle  
 Especifica la apariencia de fichas en el control de ficha actual.  
  
```  
BOOL ModifyTabStyle(Style style);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `style`  
 Uno de los valores de enumeración que especifica la apariencia del control de ficha. Para obtener más información, vea la tabla en la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 El valor de la `style` parámetro puede ser uno de los siguientes `CMFCTabCtrl::Style` enumeraciones.  
  
|nombre|Descripción|  
|----------|-----------------|  
|STYLE_3D|Muestra pestañas tridimensionales, rectangulares con esquinas redondeadas.|  
|STYLE_3D_ONENOTE|Muestra pestañas tridimensionales que tienen un lado vertical y el lado "uno" inclinada y esquinas redondeadas.|  
|STYLE_3D_ROUNDED|Muestra pestañas tridimensionales inclinado lados y esquinas redondeadas.|  
|STYLE_3D_ROUNDED_SCROLL|Muestra pestañas tridimensionales inclinado lados y esquinas redondeadas. Si hay más fichas que se pueden mostrar al mismo tiempo, el marco de trabajo muestra una flecha de lista desplegable y un menú de pestañas para activar.|  
|STYLE_3D_SCROLLED|Muestra pestañas tridimensionales, rectangulares. Si hay más fichas que se pueden mostrar al mismo tiempo, el marco de trabajo muestra una flecha de lista desplegable y un menú de pestañas para activar.|  
|STYLE_3D_VS2005|Muestra tridimensional, redondear las fichas que tienen un lado inclinado y un lado vertical.|  
|STYLE_FLAT|Muestra pestañas bidimensionales que han inclinado lados izquierdo y derecho.|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|Muestra pestañas bidimensionales. Si hay más fichas que se pueden mostrar al mismo tiempo, el marco de trabajo muestra las flechas de desplazamiento en los extremos del área de ficha.|  
  
##  <a name="ondragenter"></a>CMFCTabCtrl::OnDragEnter  
 Lo llama el marco de trabajo durante una operación de arrastrar y colocar cuando el cursor entra por primera vez la ventana del control de ficha actual.  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDataObject`  
 Apunta a un objeto de datos que contiene los datos que el usuario arrastra.  
  
 [in] `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Este parámetro es una combinación bit a bit (OR) de los siguientes valores: `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, y `MK_RBUTTON`. Para obtener más información, consulte el **parámetros de mensaje** sección de [acerca de la entrada del Mouse](http://msdn.microsoft.com/library/windows/desktop/ms645601).  
  
 [in] `point`  
 Contiene la ubicación actual del cursor en coordenadas de cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre `DROPEFFECT_NONE`, lo que significa que el destino de colocación no puede aceptar los datos.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para admitir una operación de arrastrar y colocar. Invalide este método para implementar su propio comportamiento personalizado.  
  
 De forma predeterminada, este método se llama solo `CMFCTabCtrl::OnDragOver`, que siempre devuelve `DROPEFFECT_NONE`.  
  
##  <a name="ondragover"></a>CMFCTabCtrl::OnDragOver  
 Lo llama el marco de trabajo durante una operación de arrastre cuando se mueve el mouse sobre la ventana de destino de colocación.  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDataObject`  
 Puntero a un [COleDataObject](../../mfc/reference/coledataobject-class.md) objeto que se está arrastrando sobre el destino de colocación.  
  
 [in] `dwKeyState`  
 El estado de las teclas modificadoras, que es una combinación bit a bit (o) de `MK_CONTROL`, `MK_SHIFT`, `MK_ALT`, `MK_LBUTTON`, `MK_MBUTTON`, y `MK_RBUTTON`. Para obtener más información, vea "Parámetros de mensajes" en [acerca de la entrada del Mouse](http://msdn.microsoft.com/library/windows/desktop/ms645601).  
  
 [in] `point`  
 La posición del mouse actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre es `DROPEFFECT_NONE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método con su implementación personalizada. Para obtener más información, consulte el [CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover) método.  
  
##  <a name="onshowtabdocumentsmenu"></a>CMFCTabCtrl::OnShowTabDocumentsMenu  
 Muestra un menú emergente de ventanas con pestañas, espera hasta que el usuario selecciona una ficha y hace que la pestaña seleccionada la pestaña activa.  
  
```  
virtual void OnShowTabDocumentsMenu(CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `point`  
 Las coordenadas de dónde desea mostrar el menú emergente.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setactiveinmditabgroup"></a>CMFCTabCtrl::SetActiveInMDITabGroup  
 La ficha actual de un control de ficha se establece como la pestaña activa en un grupo de pestañas de interfaz de múltiples documentos.  
  
```  
void SetActiveInMDITabGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bActive`  
 `TRUE`para realizar la ficha actual de la pestaña activa; `FALSE` para desactivar la ficha actual.  
  
### <a name="remarks"></a>Comentarios  
 Puede organizar varias ventanas de documento en ambos grupos de pestañas horizontales o verticales y mover fácilmente los documentos de un grupo a otro.  
  
##  <a name="setactivetab"></a>CMFCTabCtrl::SetActiveTab  
 Activa una pestaña.  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `iTab`  
 Especifica el índice de base cero de la pestaña para activar.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la ficha especificada se realizó activa; `FALSE` si especificado `iTab` valor de parámetro no es válido.  
  
### <a name="remarks"></a>Comentarios  
 Este método no envía el `AFX_WM_CHANGE_ACTIVE_TAB` notificación a la ventana primaria del control de ficha.  
  
 El `SetActiveTab` método llama automáticamente a la [CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar) método para impedir que la pantalla parpadea.  
  
##  <a name="setactivetabboldfont"></a>CMFCTabCtrl::SetActiveTabBoldFont  
 Habilita o deshabilita el uso de una fuente en negrita en las pestañas activas.  
  
```  
void SetActiveTabBoldFont(BOOL bIsBold=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bIsBold`  
 `TRUE`Para usar una fuente en negrita para mostrar la etiqueta de la pestaña activa; `FALSE` usar la fuente estándar para mostrar la etiqueta. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setdrawframe"></a>CMFCTabCtrl::SetDrawFrame  
 Especifica si se dibuja un rectángulo de marco alrededor de una barra incrustada.  
  
```  
void SetDrawFrame(BOOL bDraw=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDraw`  
 `TRUE`para mostrar un rectángulo de marco alrededor de una barra incrustado. en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setflatframe"></a>CMFCTabCtrl::SetFlatFrame  
 Especifica si se debe dibujar un plano o una trama de 3D alrededor del área de pestaña.  
  
```  
void SetFlatFrame(
    BOOL bFlat=TRUE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bFlat`  
 `TRUE`para dibujar un marco plana (2D) alrededor del área de pestaña; `FALSE` para dibujar un marco tridimensional (3D). El valor predeterminado es `TRUE`.  
  
 [in] `bRepaint`  
 `TRUE`Para volver a dibujar la ventana Inmediato; en caso contrario, `FALSE`. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="setimagelist"></a>CMFCTabCtrl::SetImageList  
 Especifica una lista de imágenes.  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx=15,  
    COLORREF clrTransp=RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `uiID`  
 El identificador de un recurso de mapa de bits que contiene la lista de imágenes.  
  
 [in] `cx`  
 El ancho de cada imagen, en píxeles. El valor predeterminado es 15.  
  
 [in] `clrTransp`  
 El color de imagen transparente. Las partes de la imagen que son de este color será transparentes. El valor predeterminado es el color fucsia, RGB(255,0,255).  
  
 [in] `hImageList`  
 Un identificador a una lista de imágenes previamente cargados.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente. `FALSE`Si el control de ficha se crea mediante un estilo plano o si la primera sobrecarga de método no puede cargar el mapa de bits especificado por el `uiID` parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para establecer una lista de imágenes para el control de ficha. Las imágenes de la lista de imágenes se muestran al lado de la etiqueta de ficha. Este método vuelve a calcular el alto de la pestaña para que la ficha tiene un tamaño para que contenga la imagen y el texto.  
  
 Use la [cmfcbasetabctrl:: addTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) método heredada por el control de ficha para especificar el índice de la imagen para mostrar.  
  
##  <a name="setresizemode"></a>CMFCTabCtrl::SetResizeMode  
 Especifica cómo se puede cambiar el tamaño de control de ficha actual y, a continuación, vuelve a mostrar el control.  
  
```  
void SetResizeMode(ResizeMode resizeMode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `resizeMode`  
 Uno de los `CMFCTabCtrl::ResizeMode` valores de enumeración que especifica cómo se puede cambiar el tamaño de control de pestaña. Para obtener una lista de valores posibles, vea la tabla en la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 El `resizeMode` parámetro puede ser uno de los siguientes `ResizeMode` valores de enumeración.  
  
|nombre|Descripción|  
|----------|-----------------|  
|RESIZE_NO|No puede cambiarse el control de ficha.|  
|RESIZE_VERT|El control de ficha puede cambiarse de tamaño verticalmente pero no horizontalmente.|  
|RESIZE_HORIZ|El control de ficha puede cambiarse de tamaño horizontalmente pero no verticalmente.|  
  
##  <a name="settabmaxwidth"></a>CMFCTabCtrl::SetTabMaxWidth  
 Especifica el ancho máximo de ficha en una ventana con pestañas.  
  
```  
void SetTabMaxWidth(int nTabMaxWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nTabMaxWidth`  
 El ancho de la pestaña máximo, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método para limitar el ancho de cada ficha en una ventana con pestañas. Este método es útil si las fichas tienen etiquetas muy largas. El [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md) constructor de clase inicializa el ancho máximo de ficha en 0, lo que en realidad significa que no se limita el ancho.  
  
##  <a name="stopresize"></a>CMFCTabCtrl::StopResize  
 Finaliza la operación de cambio de tamaño actual en el control de ficha.  
  
```  
void StopResize(BOOL bCancel);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bCancel`  
 `TRUE`para abandonar la operación de cambio de tamaño actual; `FALSE` para completar la actual cambiar el tamaño de operación. En cualquier caso, el marco de trabajo detiene dibujar el rectángulo de cambio de tamaño.  
  
##  <a name="synchronizescrollbar"></a>CMFCTabCtrl::SynchronizeScrollBar  
 Dibuja una barra de desplazamiento horizontal de un control de ficha que muestra pestañas sin formato.  
  
```  
BOOL SynchronizeScrollBar(SCROLLINFO* pScrollInfo = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 [out] `pScrollInfo`  
 Puntero a un [SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537) estructura o `NULL`. Cuando este método devuelve, y si este parámetro no es `NULL`, la estructura contiene todos los parámetros de la barra de desplazamiento. El valor predeterminado es `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método afecta a un control de pestaña que muestra pestañas sin formato. La barra de desplazamiento afecta a todas las tabulaciones al mismo tiempo.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [Clase CDockablePane](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl (clase)](../../mfc/reference/cmfcbasetabctrl-class.md)
