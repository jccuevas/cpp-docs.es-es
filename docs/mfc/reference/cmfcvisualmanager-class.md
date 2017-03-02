---
title: Clase CMFCVisualManager | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCVisualManager
dev_langs:
- C++
helpviewer_keywords:
- CMFCVisualManager class
ms.assetid: beed80f7-36a2-4d64-9f09-e807cfefc3fe
caps.latest.revision: 58
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
ms.openlocfilehash: 7054bcd099d7e66dcbcd3e11bfef8be46b8d272d
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcvisualmanager-class"></a>Clase CMFCVisualManager
Proporciona compatibilidad para cambiar la apariencia de la aplicación en el nivel global. La clase `CMFCVisualManager` funciona junto con una clase que proporciona instrucciones para dibujar los controles de la GUI de la aplicación utilizando un estilo coherente. Estas otras clases se conocen como administradores visuales y se heredan de `CMFCBaseVisualManager`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCVisualManager : public CMFCBaseVisualManager  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`CMFCVisualManager::CMFCVisualManager`|Constructor predeterminado.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCVisualManager::AdjustFrames](#adjustframes)||  
|[CMFCVisualManager::AdjustToolbars](#adjusttoolbars)||  
|[CMFCVisualManager::AlwaysHighlight3DTabs](#alwayshighlight3dtabs)|Llamado por el marco de trabajo para determinar si siempre se deben dibujar fichas 3D mediante un color de resaltado.|  
|[CMFCVisualManager::DestroyInstance](#destroyinstance)||  
|[CMFCVisualManager::DoDrawHeaderSortArrow](#dodrawheadersortarrow)||  
|[CMFCVisualManager::DrawComboDropButtonWinXP](#drawcombodropbuttonwinxp)||  
|[CMFCVisualManager::DrawPushButtonWinXP](#drawpushbuttonwinxp)||  
|[CMFCVisualManager::DrawTextOnGlass](#drawtextonglass)||  
|[CMFCVisualManager::GetAutoHideButtonTextColor](#getautohidebuttontextcolor)|Llamado por el marco de trabajo para recuperar el color del texto de un botón de ocultación automática.|  
|[CMFCVisualManager::GetButtonExtraBorder](#getbuttonextraborder)|Llamado por el marco de trabajo para recuperar el tamaño del botón mayor que requiere el administrador visual actual para dibujar un botón.|  
|[CMFCVisualManager::GetCaptionBarTextColor](#getcaptionbartextcolor)|Llamado por el marco de trabajo para recuperar el color del texto de una barra de título.|  
|[CMFCVisualManager::GetDockingTabsBordersSize](#getdockingtabsborderssize)|Llamado por el marco de trabajo para recuperar el tamaño del borde de una barra de pestañas acoplada.|  
|[CMFCVisualManager::GetHighlightedMenuItemTextColor](#gethighlightedmenuitemtextcolor)||  
|[CMFCVisualManager::GetInstance](#getinstance)|Devuelve un puntero a la `CMFCVisualManager` objeto.|  
|[CMFCVisualManager::GetMDITabsBordersSize](#getmditabsborderssize)|Llamado por el marco de trabajo para recuperar el tamaño del borde de la ventana /mditabs.|  
|[CMFCVisualManager::GetMenuItemTextColor](#getmenuitemtextcolor)||  
|[CMFCVisualManager::GetMenuShadowDepth](#getmenushadowdepth)|Devuelve un valor que determina el ancho y alto de una sombra de menú.|  
|[CMFCVisualManager::GetNcBtnSize](#getncbtnsize)|Llamado por el marco de trabajo para determinar el tamaño de los botones de sistema basados en el administrador visual actual. Los botones de sistema son los botones en el título del marco principal que se asignan a los comandos **cerrar**, **minimizar**, **maximizar**, y **restaurar**.|  
|[CMFCVisualManager::GetPopupMenuBorderSize](#getpopupmenubordersize)|Llamado por el marco de trabajo para recuperar el tamaño del borde de un menú emergente.|  
|[CMFCVisualManager::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|Llamado por el marco de trabajo para recuperar el color de fondo de una lista de propiedades.|  
|[CMFCVisualManager::GetPropertyGridGroupTextColor](#getpropertygridgrouptextcolor)|Llamado por el marco de trabajo para recuperar el color del texto de una lista de propiedades.|  
|[CMFCVisualManager::GetRibbonHyperlinkTextColor](#getribbonhyperlinktextcolor)||  
|[CMFCVisualManager::GetRibbonPopupBorderSize](#getribbonpopupbordersize)||  
|[CMFCVisualManager::GetRibbonQuickAccessToolBarTextColor](#getribbonquickaccesstoolbartextcolor)||  
|[CMFCVisualManager::GetRibbonSliderColors](#getribbonslidercolors)||  
|[CMFCVisualManager::GetShowAllMenuItemsHeight](#getshowallmenuitemsheight)||  
|[CMFCVisualManager::GetSmartDockingBaseGuideColors](#getsmartdockingbaseguidecolors)||  
|[CMFCVisualManager::GetSmartDockingHighlightToneColor](#getsmartdockinghighlighttonecolor)||  
|[CMFCVisualManager::GetSmartDockingTheme](#getsmartdockingtheme)|Devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.|  
|[CMFCVisualManager::GetStatusBarPaneTextColor](#getstatusbarpanetextcolor)||  
|[CMFCVisualManager::GetTabFrameColors](#gettabframecolors)|Llamado por el marco de trabajo para recuperar el conjunto de colores que se utilizará al dibujar un marco de ficha.|  
|[CMFCVisualManager::GetTabTextColor](#gettabtextcolor)||  
|[CMFCVisualManager::GetToolbarButtonTextColor](#gettoolbarbuttontextcolor)|Llamado por el marco de trabajo para recuperar el color actual del texto en el botón de barra de herramientas. Este color varía según el administrador visual actual y el estado del botón.|  
|[CMFCVisualManager::GetToolbarDisabledTextColor](#gettoolbardisabledtextcolor)|Llamado por el marco de trabajo para determinar el color del texto que se muestra en los elementos de barras de herramientas.|  
|[CMFCVisualManager::GetToolbarHighlightColor](#gettoolbarhighlightcolor)||  
|[CMFCVisualManager::GetToolTipInfo](#gettooltipinfo)||  
|[CMFCVisualManager::HasOverlappedAutoHideButtons](#hasoverlappedautohidebuttons)|Especifica si se superponen los botones de ocultación automática.|  
|[CMFCVisualManager::IsDockingTabHasBorder](#isdockingtabhasborder)|Especifica si el administrador visual actual dibuja un borde alrededor de las barras de acoplamiento con pestañas.|  
|[CMFCVisualManager::IsEmbossDisabledImage](#isembossdisabledimage)|Especifica si deben estar en relieve imágenes deshabilitadas.|  
|[CMFCVisualManager::IsFadeInactiveImage](#isfadeinactiveimage)|Llamado por el marco de trabajo para determinar si las imágenes inactivas en un menú o barra de herramientas aparecen atenuadas.|  
|[CMFCVisualManager::IsMenuFlatLook](#ismenuflatlook)|Especifica si los botones de menú tienen una apariencia plana.|  
|[CMFCVisualManager::IsOfficeXPStyleMenus](#isofficexpstylemenus)|Especifica si el administrador visual implementa los menús del estilo de Office XP.|  
|[CMFCVisualManager::IsOwnerDrawCaption](#isownerdrawcaption)|Especifica si el administrador visual actual implementa títulos dibujado por el propietario de una ventana de marco.|  
|[CMFCVisualManager::IsShadowHighlightedImage](#isshadowhighlightedimage)|Especifica si una imagen resaltada tiene una sombra.|  
|[CMFCVisualManager::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|Lo llama el marco de trabajo cuando dibuja el borde de un botón de ocultación automática.|  
|[CMFCVisualManager::OnDrawBarGripper](#ondrawbargripper)|Llamado por el marco de trabajo cuando dibuja el redimensionamiento de una barra de control. El usuario debe hacer clic en el punto de sujeción para mover la barra de control.|  
|[CMFCVisualManager::OnDrawBrowseButton](#ondrawbrowsebutton)|Llamado por el marco de trabajo cuando se dibuja un botón Examinar que pertenece a un control de edición ( [CMFCEditBrowseCtrl clase](../../mfc/reference/cmfceditbrowsectrl-class.md)).|  
|[CMFCVisualManager::OnDrawButtonBorder](#ondrawbuttonborder)|Llamado por el marco de trabajo cuando dibuja el borde de un botón de barra de herramientas.|  
|[CMFCVisualManager::OnDrawButtonSeparator](#ondrawbuttonseparator)||  
|[CMFCVisualManager::OnDrawCaptionBarBorder](#ondrawcaptionbarborder)|Llamado por el marco de trabajo cuando dibuja el borde de la barra de título.|  
|[CMFCVisualManager::OnDrawCaptionBarButtonBorder](#ondrawcaptionbarbuttonborder)||  
|[CMFCVisualManager::OnDrawCaptionBarInfoArea](#ondrawcaptionbarinfoarea)||  
|[CMFCVisualManager::OnDrawCaptionButton](#ondrawcaptionbutton)|Llamado por el marco de trabajo cuando se dibuja un botón de título.|  
|[CMFCVisualManager::OnDrawCheckBox](#ondrawcheckbox)||  
|[CMFCVisualManager::OnDrawCheckBoxEx](#ondrawcheckboxex)||  
|[CMFCVisualManager::OnDrawComboBorder](#ondrawcomboborder)|Lo llama el marco de trabajo cuando dibuja el borde de un botón de cuadro combinado.|  
|[CMFCVisualManager::OnDrawComboDropButton](#ondrawcombodropbutton)|Llamado por el marco de trabajo cuando se dibuja un botón de lista del cuadro combinado.|  
|[CMFCVisualManager::OnDrawControlBorder](#ondrawcontrolborder)||  
|[CMFCVisualManager::OnDrawDefaultRibbonImage](#ondrawdefaultribbonimage)|Llamado por el marco de trabajo cuando dibuja la imagen predeterminada de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawEditBorder](#ondraweditborder)|Llamado por el marco de trabajo cuando se dibuja un borde alrededor de un [CMFCToolBarEditBoxButton](../../mfc/reference/cmfctoolbareditboxbutton-class.md) objeto.|  
|[CMFCVisualManager::OnDrawExpandingBox](#ondrawexpandingbox)||  
|[CMFCVisualManager::OnDrawFloatingToolbarBorder](#ondrawfloatingtoolbarborder)|Llamado por el marco de trabajo cuando se dibuja los bordes de la barra de herramientas flotante. La barra de herramientas flotante es una barra de herramientas que aparece como una ventana de marco reducido.|  
|[CMFCVisualManager::OnDrawHeaderCtrlBorder](#ondrawheaderctrlborder)|Llamado por el marco de trabajo cuando dibuja el borde que contiene el control de encabezado.|  
|[CMFCVisualManager::OnDrawHeaderCtrlSortArrow](#ondrawheaderctrlsortarrow)|Llamado por el marco al dibujar la flecha de ordenación del control de encabezado.|  
|[CMFCVisualManager::OnDrawMenuArrowOnCustomizeList](#ondrawmenuarrowoncustomizelist)||  
|[CMFCVisualManager::OnDrawMenuBorder](#ondrawmenuborder)|Llamado por el marco de trabajo cuando se dibuja un borde del menú.|  
|[CMFCVisualManager::OnDrawMenuCheck](#ondrawmenucheck)||  
|[CMFCVisualManager::OnDrawMenuItemButton](#ondrawmenuitembutton)||  
|[CMFCVisualManager::OnDrawMenuLabel](#ondrawmenulabel)||  
|[CMFCVisualManager::OnDrawMenuResizeBar](#ondrawmenuresizebar)||  
|[CMFCVisualManager::OnDrawMenuScrollButton](#ondrawmenuscrollbutton)|Llamado por el marco de trabajo cuando dibuja un botón de desplazamiento del menú.|  
|[CMFCVisualManager::OnDrawMenuShadow](#ondrawmenushadow)||  
|[CMFCVisualManager::OnDrawMenuSystemButton](#ondrawmenusystembutton)|Llamado por el marco cuando dibuja los botones de menú sistema **cerrar**, **minimizar**, **maximizar**, y **restaurar**.|  
|[CMFCVisualManager::OnDrawMiniFrameBorder](#ondrawminiframeborder)||  
|[CMFCVisualManager::OnDrawOutlookBarSplitter](#ondrawoutlookbarsplitter)|Llamado por el marco de trabajo cuando se dibuja el separador de una barra de Outlook. El divisor es una barra horizontal que se utiliza para agrupar controles.|  
|[CMFCVisualManager::OnDrawOutlookPageButtonBorder](#ondrawoutlookpagebuttonborder)|Lo llama el marco de trabajo cuando dibuja el borde de un botón de la página de Outlook. Botones de la página de Outlook aparecen si el panel de la barra de Outlook contiene más botones del que puede mostrar.|  
|[CMFCVisualManager::OnDrawPaneBorder](#ondrawpaneborder)|Llamado por el marco de trabajo cuando dibuja el borde de un [CPane clase](../../mfc/reference/cpane-class.md).|  
|[CMFCVisualManager::OnDrawPaneCaption](#ondrawpanecaption)|Llamado por el marco al dibujar el título de un `CPane`.|  
|[CMFCVisualManager::OnDrawPaneDivider](#ondrawpanedivider)||  
|[CMFCVisualManager::OnDrawPopupWindowBorder](#ondrawpopupwindowborder)||  
|[CMFCVisualManager::OnDrawPopupWindowButtonBorder](#ondrawpopupwindowbuttonborder)||  
|[CMFCVisualManager::OnDrawPopupWindowCaption](#ondrawpopupwindowcaption)||  
|[CMFCVisualManager::OnDrawRibbonApplicationButton](#ondrawribbonapplicationbutton)|Llamado por el marco de trabajo cuando dibuja el **botón principal** en la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonButtonBorder](#ondrawribbonbuttonborder)|Llamado por el marco de trabajo cuando dibuja el borde de un botón de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonButtonsGroup](#ondrawribbonbuttonsgroup)|Llamado por el marco de trabajo cuando dibuja un grupo de botones en la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCaption](#ondrawribboncaption)|Llamado por el marco al dibujar el título del marco principal, pero sólo si la barra de cinta se integra con el marco.|  
|[CMFCVisualManager::OnDrawRibbonCaptionButton](#ondrawribboncaptionbutton)|Llamado por el marco de trabajo cuando se dibuja un botón de título que se encuentra en la barra de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCategory](#ondrawribboncategory)|Llamado por el marco de trabajo cuando dibuja una categoría de cinta.|  
|[CMFCVisualManager::OnDrawRibbonCategoryCaption](#ondrawribboncategorycaption)|Llamado por el marco de trabajo cuando dibuja el título de una categoría de cinta.|  
|[CMFCVisualManager::OnDrawRibbonCategoryScroll](#ondrawribboncategoryscroll)||  
|[CMFCVisualManager::OnDrawRibbonCategoryTab](#ondrawribboncategorytab)|Llamado por el marco de trabajo cuando dibuja la pestaña para una categoría de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonCheckBoxOnList](#ondrawribboncheckboxonlist)||  
|[CMFCVisualManager::OnDrawRibbonColorPaletteBox](#ondrawribboncolorpalettebox)||  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButtonContext](#ondrawribbondefaultpanebuttoncontext)||  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButton](#ondrawribbondefaultpanebutton)|Llamado por el marco de trabajo cuando dibuja el botón predeterminado de panel de cinta de opciones. El botón predeterminado aparece cuando el usuario reduce a un panel de la cinta para que sea demasiado pequeña para mostrar los elementos de la cinta de opciones. El botón predeterminado se dibuja en su lugar y los elementos de la cinta de opciones se agregan como elementos en un menú desplegable.|  
|[CMFCVisualManager::OnDrawRibbonDefaultPaneButtonIndicator](#ondrawribbondefaultpanebuttonindicator)||  
|[CMFCVisualManager::OnDrawRibbonGalleryBorder](#ondrawribbongalleryborder)||  
|[CMFCVisualManager::OnDrawRibbonGalleryButton](#ondrawribbongallerybutton)||  
|[CMFCVisualManager::OnDrawRibbonKeyTip](#ondrawribbonkeytip)||  
|[CMFCVisualManager::OnDrawRibbonLabel](#ondrawribbonlabel)|Llamado por el marco de trabajo cuando dibuja la etiqueta de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonMainPanelButtonBorder](#ondrawribbonmainpanelbuttonborder)|Llamado por el marco de trabajo cuando dibuja el borde de un botón de la cinta de opciones que se coloca en el **principal** panel. El **principal** panel es el panel que aparece cuando un usuario hace clic en el **botón principal**.|  
|[CMFCVisualManager::OnDrawRibbonMainPanelFrame](#ondrawribbonmainpanelframe)|Llamado por el marco al dibujar el marco que rodea el **principal** panel.|  
|[CMFCVisualManager::OnDrawRibbonMenuCheckFrame](#ondrawribbonmenucheckframe)||  
|[CMFCVisualManager::OnDrawRibbonPanel](#ondrawribbonpanel)|Llamado por el marco de trabajo cuando dibuja un panel de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonPanelCaption](#ondrawribbonpanelcaption)|Llamado por el marco de trabajo cuando dibuja el título de un panel de cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonProgressBar](#ondrawribbonprogressbar)|Llamado por el marco cuando dibuja una [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md) objeto.|  
|[CMFCVisualManager::OnDrawRibbonQuickAccessToolBarSeparator](#ondrawribbonquickaccesstoolbarseparator)|Llamado por el marco cuando dibuja un separador en una cinta **la barra de herramientas de acceso rápido**.|  
|[CMFCVisualManager::OnDrawRibbonRecentFilesFrame](#ondrawribbonrecentfilesframe)|Llamado por el marco de trabajo cuando se dibuja un marco alrededor de una lista de archivos recientes.|  
|[CMFCVisualManager::OnDrawRibbonSliderChannel](#ondrawribbonsliderchannel)|Llamado por el marco de trabajo cuando dibuja el canal de un [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) objeto.|  
|[CMFCVisualManager::OnDrawRibbonSliderThumb](#ondrawribbonsliderthumb)|Llamado por el marco de trabajo cuando se dibuja el control de posición de un `CMFCRibbonSlider` objeto.|  
|[CMFCVisualManager::OnDrawRibbonSliderZoomButton](#ondrawribbonsliderzoombutton)|Llamado por el marco cuando dibuja los botones de zoom de un `CMFCRibbonSlider` objeto.|  
|[CMFCVisualManager::OnDrawRibbonStatusBarPane](#ondrawribbonstatusbarpane)|Llamado por el marco de trabajo cuando dibuja el panel de la barra de estado de una cinta de opciones.|  
|[CMFCVisualManager::OnDrawRibbonTabsFrame](#ondrawribbontabsframe)|Llamado por el marco al dibujar un marco alrededor de un conjunto de fichas de la cinta de opciones.|  
|[CMFCVisualManager::OnDrawScrollButtons](#ondrawscrollbuttons)||  
|[CMFCVisualManager::OnDrawSeparator](#ondrawseparator)|Llamado por el marco de trabajo cuando dibuja un separador. El separador se utiliza normalmente en una barra de controles para separar grupos de iconos.|  
|[CMFCVisualManager::OnDrawShowAllMenuItems](#ondrawshowallmenuitems)||  
|[CMFCVisualManager::OnDrawSpinButtons](#ondrawspinbuttons)|Llamado por el marco de trabajo cuando se dibuja botones.|  
|[CMFCVisualManager::OnDrawSplitterBorder](#ondrawsplitterborder)|Llamado por el marco de trabajo cuando dibuja el borde de una ventana dividida.|  
|[CMFCVisualManager::OnDrawSplitterBox](#ondrawsplitterbox)|Llamado por el marco al dibujar el cuadro de arrastrar divisor para una ventana dividida.|  
|[CMFCVisualManager::OnDrawStatusBarPaneBorder](#ondrawstatusbarpaneborder)|Llamado por el marco de trabajo cuando dibuja el borde de un panel de barra de estado.|  
|[CMFCVisualManager::OnDrawStatusBarProgress](#ondrawstatusbarprogress)|Llamado por el marco de trabajo cuando se dibuja el indicador de progreso de la barra de estado.|  
|[CMFCVisualManager::OnDrawStatusBarSizeBox](#ondrawstatusbarsizebox)|Llamado por el marco de trabajo cuando se dibuja el cuadro de tamaño de la barra de estado.|  
|[CMFCVisualManager::OnDrawTab](#ondrawtab)|Llamado por el marco cuando dibuja una [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md) objeto.|  
|[CMFCVisualManager::OnDrawTabCloseButton](#ondrawtabclosebutton)|Llamado por el marco de trabajo cuando dibuja el **cerrar** botón en la ficha activa.|  
|[CMFCVisualManager::OnDrawTabContent](#ondrawtabcontent)|Llamado por el marco de trabajo cuando se dibuja el interior de la ficha (imágenes, textos).|  
|[CMFCVisualManager::OnDrawTabsButtonBorder](#ondrawtabsbuttonborder)|Lo llama el marco de trabajo cuando dibuja el borde de un botón de la ficha.|  
|[CMFCVisualManager::OnDrawTask](#ondrawtask)|Llamado por el marco de trabajo cuando se dibuja una tarea en el panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupAreaBorder](#ondrawtasksgroupareaborder)|Llamado por el marco de trabajo cuando dibuja un borde alrededor de un área de grupo en el panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupCaption](#ondrawtasksgroupcaption)|Lo llama el marco de trabajo cuando dibuja el título de un grupo de tareas en el panel de tareas.|  
|[CMFCVisualManager::OnDrawTasksGroupIcon](#ondrawtasksgroupicon)||  
|[CMFCVisualManager::OnDrawTearOffCaption](#ondrawtearoffcaption)|Llamado por el marco de trabajo cuando dibuja el título desplazable, una barra desplazable.|  
|[CMFCVisualManager::OnDrawToolBoxFrame](#ondrawtoolboxframe)||  
|[CMFCVisualManager::OnEraseMDIClientArea](#onerasemdiclientarea)|Llamado por el marco de trabajo cuando borra el área de cliente MDI.|  
|[CMFCVisualManager::OnErasePopupWindowButton](#onerasepopupwindowbutton)||  
|[CMFCVisualManager::OnEraseTabsArea](#onerasetabsarea)|Llamado por el marco de trabajo cuando borra el área de fichas en una ventana de la ficha.|  
|[CMFCVisualManager::OnEraseTabsButton](#onerasetabsbutton)|Llamado por el marco de trabajo cuando borran el icono y el texto de un botón de la ficha.|  
|[CMFCVisualManager::OnEraseTabsFrame](#onerasetabsframe)|Llamado por el marco de trabajo cuando borra un marco de la ficha.|  
|[CMFCVisualManager::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|Lo llama el marco de trabajo cuando se llena el fondo de un botón de ocultación automática.|  
|[CMFCVisualManager::OnFillBarBackground](#onfillbarbackground)|Lo llama el marco de trabajo cuando se llena el fondo de una barra de controles.|  
|[CMFCVisualManager::OnFillButtonInterior](#onfillbuttoninterior)|Lo llama el marco de trabajo cuando se llena el fondo de un botón de barra de herramientas.|  
|[CMFCVisualManager::OnFillCaptionBarButton](#onfillcaptionbarbutton)||  
|[CMFCVisualManager::OnFillCommandsListBackground](#onfillcommandslistbackground)|Lo llama el marco de trabajo cuando se llena el fondo de un botón de barra de herramientas a la que pertenece a una lista de comandos que, a su vez, forma parte de un cuadro de diálogo de personalización.|  
|[CMFCVisualManager::OnFillHeaderCtrlBackground](#onfillheaderctrlbackground)|Lo llama el marco de trabajo cuando se llena el fondo de un control de encabezado.|  
|[CMFCVisualManager::OnFillMiniFrameCaption](#onfillminiframecaption)|Lo llama el marco de trabajo cuando se llena el título de una ventana de marco flotante.|  
|[CMFCVisualManager::OnFillOutlookBarCaption](#onfilloutlookbarcaption)|Lo llama el marco de trabajo cuando se llena el fondo de una leyenda de la barra de Outlook.|  
|[CMFCVisualManager::OnFillOutlookPageButton](#onfilloutlookpagebutton)|Llamado por el marco de trabajo cuando rellena el interior de un botón de la página de Outlook.|  
|[CMFCVisualManager::OnFillPopupWindowBackground](#onfillpopupwindowbackground)|Lo llama el marco de trabajo cuando se llena el fondo de una ventana emergente.|  
|[CMFCVisualManager::OnFillRibbonButton](#onfillribbonbutton)|Llamado por el marco de trabajo cuando rellena el interior de un botón de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonEdit](#onfillribbonedit)|Llamado por el marco de trabajo cuando rellena el interior de un control de edición de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonMainPanelButton](#onfillribbonmainpanelbutton)|Llamado por el marco de trabajo cuando rellena el interior de un botón de cinta que se encuentra en la **principal** panel.|  
|[CMFCVisualManager::OnFillRibbonMenuFrame](#onfillribbonmenuframe)|Lo llama el marco de trabajo cuando se llena el marco de menús del panel principal de la cinta de opciones.|  
|[CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup](#onfillribbonquickaccesstoolbarpopup)||  
|[CMFCVisualManager::OnFillSplitterBackground](#onfillsplitterbackground)|Lo llama el marco de trabajo cuando se llena el fondo de una ventana dividida.|  
|[CMFCVisualManager::OnFillTab](#onfilltab)|Lo llama el marco de trabajo cuando se llena el fondo de una pestaña.|  
|[CMFCVisualManager::OnFillTasksGroupInterior](#onfilltasksgroupinterior)|Llamado por el marco de trabajo cuando rellena el interior de un [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) objeto en el [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md).|  
|[CMFCVisualManager::OnFillTasksPaneBackground](#onfilltaskspanebackground)|Llamado por el marco de trabajo cuando se llena el fondo de un `CMFCTasksPane` control.|  
|[CMFCVisualManager::OnHighlightMenuItem](#onhighlightmenuitem)|Llamado por el marco de trabajo cuando se dibuja un elemento de menú resaltado.|  
|[CMFCVisualManager::OnHighlightRarelyUsedMenuItems](#onhighlightrarelyusedmenuitems)|Llamado por el marco de trabajo cuando dibuja un resaltado y el elemento de menú poco usados.|  
|[CMFCVisualManager::OnNcPaint](#onncpaint)|Llamado por el marco de trabajo cuando se dibuja el área no cliente.|  
|[CMFCVisualManager::OnSetWindowRegion](#onsetwindowregion)|Llamado por el marco de trabajo cuando se establece una región que contiene marcos y menús emergentes.|  
|[CMFCVisualManager::OnUpdateSystemColors](#onupdatesystemcolors)|Llamado por el marco cuando cambia la configuración de color del sistema.|  
|[CMFCVisualManager::RedrawAll](#redrawall)|Vuelve a dibujar todas las barras de control en la aplicación.|  
|[CMFCVisualManager::RibbonCategoryColorToRGB](#ribboncategorycolortorgb)||  
|[CMFCVisualManager::SetDefaultManager](#setdefaultmanager)|Establece el administrador visual de forma predeterminada.|  
|[CMFCVisualManager::SetEmbossDisabledImage](#setembossdisabledimage)|Habilita o deshabilita el modo de relieve para imágenes de barras de herramientas.|  
|[CMFCVisualManager::SetFadeInactiveImage](#setfadeinactiveimage)|Habilita o deshabilita el efecto de iluminación para imágenes inactivos en un menú o barra de herramientas.|  
|[CMFCVisualManager::SetMenuFlatLook](#setmenuflatlook)|Establece una marca que indica si los botones de menú de la aplicación tienen una apariencia plana.|  
|[CMFCVisualManager::SetMenuShadowDepth](#setmenushadowdepth)|Establece el ancho y alto de la sombra del menú.|  
|[CMFCVisualManager::SetShadowHighlightedImage](#setshadowhighlightedimage)|Establece una marca que indica si se muestra la sombra al representar imágenes resaltadas.|  
  
## <a name="remarks"></a>Comentarios  
 Dado que la `CMFCVisualManager` clase controla la interfaz gráfica de usuario de la aplicación, cada aplicación puede tener ya sea una instancia de un `CMFCVisualManager`, o una instancia de una clase derivada de `CMFCVisualManager`. La aplicación también puede funcionar sin un `CMFCVisualManager`. Utilice el método estático `GetInstance` para obtener un puntero a la actual `CMFCVisualManager`-objeto derivado.  
  
 Para cambiar la apariencia de la aplicación debe utilizar otras clases que proporcionan métodos para dibujar todos los elementos visuales de la aplicación. Algunos ejemplos de estas clases son [CMFCVisualManagerOfficeXP clase](../../mfc/reference/cmfcvisualmanagerofficexp-class.md), [CMFCVisualManagerOffice2003 clase](../../mfc/reference/cmfcvisualmanageroffice2003-class.md), y [CMFCVisualManagerOffice2007 clase](../../mfc/reference/cmfcvisualmanageroffice2007-class.md). Si desea cambiar la apariencia de la aplicación, pase uno de estos administradores visuales en el método `SetDefaultManager`. Para obtener un ejemplo que muestra cómo la aplicación puede imitar el aspecto de Microsoft Office 2003, consulte [CMFCVisualManagerOffice2003 clase](../../mfc/reference/cmfcvisualmanageroffice2003-class.md).  
  
 Todos los métodos de dibujo son virtuales. Esto le permite crear un estilo visual personalizado para la interfaz gráfica de usuario de la aplicación. Si desea crear su propio estilo visual, derivar una clase de una de las clases de administrador visual y reemplazar los métodos de dibujos que desee cambiar.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo crear una instancia del estándar y personalizado `CMFCVisualManager` objetos.  
  
```  
void CMFCSkinsApp::SetSkin (int iIndex)  
{   // destroy the current visual manager  
    if (CMFCVisualManager::GetInstance () != NULL)  
 {  
    delete CMFCVisualManager::GetInstance ();

 }  
    switch (iIndex)  
 {  
    case 0:  
    CMFCVisualManager::GetInstance ();

// create the standard visual manager  
    break; 
    case 1:  
    new CMyVisualManager ();

// create the first custom visual manager  
    break; 
    case 2:  
    new CMacStyle ();
*// create the second custom visual manager  
    break; 
 }  
 *// access the manager and set it properly  
    CMFCVisualManager::GetInstance ()->SetLook2000 ();
CMFCVisualManager::GetInstance ()->RedrawAll ();

}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo recuperar los valores predeterminados de un `CMFCVisualManager` objeto. Este fragmento de código forma parte de la [ejemplo de panel de tareas](../../visual-cpp-samples.md).  
  
 [!code-cpp[1 NVC_MFC_TasksPane](../../mfc/reference/codesnippet/cpp/cmfcvisualmanager-class_1.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 `CMFCVisualManager`   
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxvisualmanager.h  
  
##  <a name="a-nameadjustframesa--cmfcvisualmanageradjustframes"></a><a name="adjustframes"></a>CMFCVisualManager::AdjustFrames  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall AdjustFrames();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameadjusttoolbarsa--cmfcvisualmanageradjusttoolbars"></a><a name="adjusttoolbars"></a>CMFCVisualManager::AdjustToolbars  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall AdjustToolbars();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namealwayshighlight3dtabsa--cmfcvisualmanageralwayshighlight3dtabs"></a><a name="alwayshighlight3dtabs"></a>CMFCVisualManager::AlwaysHighlight3DTabs  
 El marco de trabajo llama a este método para determinar si las fichas 3D siempre deben aparecer resaltadas en la aplicación.  
  
```  
virtual BOOL AlwaysHighlight3DTabs() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las fichas 3D deben aparecer resaltadas.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función en un administrador visual derivada y devolver `TRUE` si siempre deben aparecer resaltadas pestañas 3D. La implementación predeterminada de este método devuelve `FALSE`.  
  
##  <a name="a-namecmfcvisualmanagera--cmfcvisualmanagercmfcvisualmanager"></a><a name="cmfcvisualmanager"></a>CMFCVisualManager::CMFCVisualManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCVisualManager(BOOL bTemporary = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bTemporary`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedestroyinstancea--cmfcvisualmanagerdestroyinstance"></a><a name="destroyinstance"></a>CMFCVisualManager::DestroyInstance  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
static void __stdcall DestroyInstance(BOOL bAutoDestroyOnly = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bAutoDestroyOnly`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedodrawheadersortarrowa--cmfcvisualmanagerdodrawheadersortarrow"></a><a name="dodrawheadersortarrow"></a>CMFCVisualManager::DoDrawHeaderSortArrow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void DoDrawHeaderSortArrow(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsUp,  
    BOOL bDlgCtrl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `bIsUp`  
 [in] `bDlgCtrl`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawcomboborderwinxpa--cmfcvisualmanagerdrawcomboborderwinxp"></a><a name="drawcomboborderwinxp"></a>CMFCVisualManager::DrawComboBorderWinXP  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DrawComboBorderWinXP(CDC*,
    CRect,
    BOOL,
    BOOL,
    BOOL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDC*`  
 [in] `CRect`  
 [in] `BOOL`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawcombodropbuttonwinxpa--cmfcvisualmanagerdrawcombodropbuttonwinxp"></a><a name="drawcombodropbuttonwinxp"></a>CMFCVisualManager::DrawComboDropButtonWinXP  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DrawComboDropButtonWinXP(CDC*,
    CRect,
    BOOL,
    BOOL,
    BOOL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDC*`  
 [in] `CRect`  
 [in] `BOOL`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawpushbuttonwinxpa--cmfcvisualmanagerdrawpushbuttonwinxp"></a><a name="drawpushbuttonwinxp"></a>CMFCVisualManager::DrawPushButtonWinXP  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DrawPushButtonWinXP(CDC*,
    CRect,
    CMFCButton*,
    UINT);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CDC*`  
 [in] `CRect`  
 [in] `CMFCButton*`  
 [in] `UINT`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedrawtextonglassa--cmfcvisualmanagerdrawtextonglass"></a><a name="drawtextonglass"></a>CMFCVisualManager::DrawTextOnGlass  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DrawTextOnGlass(
    CDC* pDC,  
    CString strText,  
    CRect rect,  
    DWORD dwFlags,  
    int nGlowSize = 0,  
    COLORREF clrText = (COLORREF)-1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `strText`  
 [in] `rect`  
 [in] `dwFlags`  
 [in] `nGlowSize`  
 [in] `clrText`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenabletoolbarbuttonfilla--cmfcvisualmanagerenabletoolbarbuttonfill"></a><a name="enabletoolbarbuttonfill"></a>CMFCVisualManager::EnableToolbarButtonFill  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableToolbarButtonFill(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetautohidebuttontextcolora--cmfcvisualmanagergetautohidebuttontextcolor"></a><a name="getautohidebuttontextcolor"></a>CMFCVisualManager::GetAutoHideButtonTextColor  
 El marco de trabajo llama a este método para recuperar el color del texto de un botón de ocultación automática.  
  
```  
virtual COLORREF GetAutoHideButtonTextColor(CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Puntero a un botón de ocultación automática.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que especifica el color del texto de `pButton`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar el color del texto de un botón de ocultación automática en su aplicación. Para ello, devolver el color que desea que la aplicación para usar como el color del texto.  
  
##  <a name="a-namegetbuttonextrabordera--cmfcvisualmanagergetbuttonextraborder"></a><a name="getbuttonextraborder"></a>CMFCVisualManager::GetButtonExtraBorder  
 El marco de trabajo llama a este método cuando dibuja un botón de barra de herramientas.  
  
```  
virtual CSize GetButtonExtraBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el tamaño del borde de los botones de barra de herramientas adicional.  
  
### <a name="remarks"></a>Comentarios  
 Tienen algunas máscaras extender los bordes de los botones de barra de herramientas. Invalide este método en un administrador visual personalizado para extender los bordes de los botones de barra de herramientas de la aplicación. La implementación predeterminada de este método devuelve un tamaño vacío.  
  
##  <a name="a-namegetcaptionbartextcolora--cmfcvisualmanagergetcaptionbartextcolor"></a><a name="getcaptionbartextcolor"></a>CMFCVisualManager::GetCaptionBarTextColor  
 El marco de trabajo llama a este método para recuperar el color del texto de la barra de título.  
  
```  
virtual COLORREF GetCaptionBarTextColor(CMFCCaptionBar* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pBar`  
 Puntero a una barra de título.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto en `pBar`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar el color del texto de una barra de título. En el método reemplazado, devolver el color deseado.  
  
##  <a name="a-namegetcaptionbuttonextrabordera--cmfcvisualmanagergetcaptionbuttonextraborder"></a><a name="getcaptionbuttonextraborder"></a>CMFCVisualManager::GetCaptionButtonExtraBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetCaptionButtonExtraBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdockingpanecaptionextraheighta--cmfcvisualmanagergetdockingpanecaptionextraheight"></a><a name="getdockingpanecaptionextraheight"></a>CMFCVisualManager::GetDockingPaneCaptionExtraHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetDockingPaneCaptionExtraHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdockingtabsborderssizea--cmfcvisualmanagergetdockingtabsborderssize"></a><a name="getdockingtabsborderssize"></a>CMFCVisualManager::GetDockingTabsBordersSize  
 El marco de trabajo llama a este método cuando dibuja un panel acoplado y por fichas.  
  
```  
virtual int GetDockingTabsBordersSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que indica el tamaño del borde de un panel acoplado y por fichas.  
  
### <a name="remarks"></a>Comentarios  
 Un panel acoplado se convierte en fichas cuando el usuario acopla varios paneles a la misma ubicación en la aplicación.  
  
 Invalide este método en un administrador visual personalizado para cambiar el tamaño del borde de barras de control de fichas acoplado. La implementación predeterminada devuelve -1.  
  
##  <a name="a-namegethighlightedmenuitemtextcolora--cmfcvisualmanagergethighlightedmenuitemtextcolor"></a><a name="gethighlightedmenuitemtextcolor"></a>CMFCVisualManager::GetHighlightedMenuItemTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetHighlightedMenuItemTextColor(CMFCToolBarMenuButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetinstancea--cmfcvisualmanagergetinstance"></a><a name="getinstance"></a>CMFCVisualManager::GetInstance  
 Devuelve un puntero a la actual [CMFCVisualManager clase](../../mfc/reference/cmfcvisualmanager-class.md) objeto de la aplicación.  
  
```  
static CMFCVisualManager* GetInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CMFCVisualManager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Sólo puede tener una aplicación `CMFCVisualManager` objeto asociado a él. Esto incluye cualquier objeto derivado de la `CMFCVisualManager` clase. Este método devuelve un puntero al objeto asociado `CMFCVisualManager` objeto. Si la aplicación no tiene asociada una `CMFCVisualManager` de objeto, este método creará uno y asociar a la aplicación.  
  
##  <a name="a-namegetmditabsborderssizea--cmfcvisualmanagergetmditabsborderssize"></a><a name="getmditabsborderssize"></a>CMFCVisualManager::GetMDITabsBordersSize  
 El marco de trabajo llama a este método para determinar el tamaño del borde de una ventana /mditabs antes de que dibuja la ventana.  
  
```  
virtual int GetMDITabsBordersSize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del borde de la ventana /mditabs.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada para personalizar el tamaño del borde de la ventana /mditabs.  
  
##  <a name="a-namegetmenuimagemargina--cmfcvisualmanagergetmenuimagemargin"></a><a name="getmenuimagemargin"></a>CMFCVisualManager::GetMenuImageMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetMenuImageMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetmenuitemtextcolora--cmfcvisualmanagergetmenuitemtextcolor"></a><a name="getmenuitemtextcolor"></a>CMFCVisualManager::GetMenuItemTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetMenuItemTextColor(
    CMFCToolBarMenuButton* pButton,  
    BOOL bHighlighted,  
    BOOL bDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 [in] `bHighlighted`  
 [in] `bDisabled`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetmenushadowdeptha--cmfcvisualmanagergetmenushadowdepth"></a><a name="getmenushadowdepth"></a>CMFCVisualManager::GetMenuShadowDepth  
 Recupera el ancho y alto de la sombra del menú.  
  
```  
int GetMenuShadowDepth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho y alto de la sombra de menú en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El ancho y alto de la sombra del menú son equivalentes. El valor predeterminado es 7 píxeles.  
  
##  <a name="a-namegetncbtnsizea--cmfcvisualmanagergetncbtnsize"></a><a name="getncbtnsize"></a>CMFCVisualManager::GetNcBtnSize  
 Llamado por el marco que tiene que recuperar el tamaño de los botones del sistema.  
  
```  
virtual CSize GetNcBtnSize(BOOL bSmall) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bSmall`  
 Un parámetro booleano que indica si `GetNcBtnSize` debe recuperar el tamaño de un botón sistema pequeño o grande. Si `bSmall` es `TRUE`, `GetNcBtnSize` devuelve el tamaño de un botón pequeño del sistema. De lo contrario, devuelve el tamaño de un botón de gran sistema.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CSize](../../atl-mfc-shared/reference/csize-class.md) parámetro que indica el tamaño de los botones del sistema.  
  
### <a name="remarks"></a>Comentarios  
 Los botones de sistema son los botones en el título de la ventana de marco que se asignan a los comandos **cerrar**, **minimizar**, **maximizar**, y **restaurar**. El tamaño de estos botones depende el administrador visual actual. Invalide este método si desea personalizar el tamaño de los botones de sistema en la aplicación.  
  
##  <a name="a-namegetpopupmenubordersizea--cmfcvisualmanagergetpopupmenubordersize"></a><a name="getpopupmenubordersize"></a>CMFCVisualManager::GetPopupMenuBorderSize  
 El marco de trabajo llama a este método para obtener el tamaño del borde de los menús emergentes.  
  
```  
virtual int GetPopupMenuBorderSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que especifica el tamaño del borde de los menús emergentes.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para personalizar el tamaño del borde de los menús emergentes en la aplicación.  
  
##  <a name="a-namegetpopupmenugapa--cmfcvisualmanagergetpopupmenugap"></a><a name="getpopupmenugap"></a>CMFCVisualManager::GetPopupMenuGap  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetPopupMenuGap() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetpropertygridgroupcolora--cmfcvisualmanagergetpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManager::GetPropertyGridGroupColor  
 El marco de trabajo llama a este método para obtener el color de fondo de una lista de propiedades.  
  
```  
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPropList`  
 Puntero a la lista de propiedades que se está dibujando el marco de trabajo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color de fondo `pPropList`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el color de fondo de una lista de propiedades de la aplicación.  
  
##  <a name="a-namegetpropertygridgrouptextcolora--cmfcvisualmanagergetpropertygridgrouptextcolor"></a><a name="getpropertygridgrouptextcolor"></a>CMFCVisualManager::GetPropertyGridGroupTextColor  
 El marco de trabajo llama a este método para recuperar el color del texto de una lista de propiedades.  
  
```  
virtual COLORREF GetPropertyGridGroupTextColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pPropList`  
 Puntero a la lista de propiedades.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto de la lista de propiedades.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para personalizar el color del texto de una lista de propiedades de la aplicación.  
  
##  <a name="a-namegetribbonhyperlinktextcolora--cmfcvisualmanagergetribbonhyperlinktextcolor"></a><a name="getribbonhyperlinktextcolor"></a>CMFCVisualManager::GetRibbonHyperlinkTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetRibbonHyperlinkTextColor(CMFCRibbonLinkCtrl* pHyperLink);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pHyperLink`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonpopupbordersizea--cmfcvisualmanagergetribbonpopupbordersize"></a><a name="getribbonpopupbordersize"></a>CMFCVisualManager::GetRibbonPopupBorderSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRibbonPopupBorderSize(const CMFCRibbonPanelMenu*) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CMFCRibbonPanelMenu*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonquickaccesstoolbarchevronoffseta--cmfcvisualmanagergetribbonquickaccesstoolbarchevronoffset"></a><a name="getribbonquickaccesstoolbarchevronoffset"></a>CMFCVisualManager::GetRibbonQuickAccessToolBarChevronOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRibbonQuickAccessToolBarChevronOffset();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonquickaccesstoolbarrightmargina--cmfcvisualmanagergetribbonquickaccesstoolbarrightmargin"></a><a name="getribbonquickaccesstoolbarrightmargin"></a>CMFCVisualManager::GetRibbonQuickAccessToolBarRightMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetRibbonQuickAccessToolBarRightMargin();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonquickaccesstoolbartextcolora--cmfcvisualmanagergetribbonquickaccesstoolbartextcolor"></a><a name="getribbonquickaccesstoolbartextcolor"></a>CMFCVisualManager::GetRibbonQuickAccessToolBarTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetRibbonQuickAccessToolBarTextColor(BOOL bDisabled = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bDisabled`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonslidercolorsa--cmfcvisualmanagergetribbonslidercolors"></a><a name="getribbonslidercolors"></a>CMFCVisualManager::GetRibbonSliderColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void GetRibbonSliderColors(
    CMFCRibbonSlider* pSlider,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled,  
    COLORREF& clrLine,  
    COLORREF& clrFill);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pSlider`  
 [in] `bIsHighlighted`  
 [in] `bIsPressed`  
 [in] `bIsDisabled`  
 [in] `clrLine`  
 [in] `clrFill`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetribbonstatusbartextcolora--cmfcvisualmanagergetribbonstatusbartextcolor"></a><a name="getribbonstatusbartextcolor"></a>CMFCVisualManager::GetRibbonStatusBarTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetRibbonStatusBarTextColor(CMFCRibbonStatusBar* pStatusBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pStatusBar`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetshowallmenuitemsheighta--cmfcvisualmanagergetshowallmenuitemsheight"></a><a name="getshowallmenuitemsheight"></a>CMFCVisualManager::GetShowAllMenuItemsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetShowAllMenuItemsHeight(
    CDC* pDC,  
    const CSize& sizeDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `sizeDefault`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsmartdockingbaseguidecolorsa--cmfcvisualmanagergetsmartdockingbaseguidecolors"></a><a name="getsmartdockingbaseguidecolors"></a>CMFCVisualManager::GetSmartDockingBaseGuideColors  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void GetSmartDockingBaseGuideColors(
    COLORREF& clrBaseGroupBackground,  
    COLORREF& clrBaseGroupBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `clrBaseGroupBackground`  
 [in] `clrBaseGroupBorder`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsmartdockinghighlighttonecolora--cmfcvisualmanagergetsmartdockinghighlighttonecolor"></a><a name="getsmartdockinghighlighttonecolor"></a>CMFCVisualManager::GetSmartDockingHighlightToneColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetSmartDockingHighlightToneColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetsmartdockingthemea--cmfcvisualmanagergetsmartdockingtheme"></a><a name="getsmartdockingtheme"></a>CMFCVisualManager::GetSmartDockingTheme  
 Devuelve un tema que se usa para mostrar marcadores de acoplamiento inteligente.  
  
```  
virtual AFX_SMARTDOCK_THEME GetSmartDockingTheme();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores enumerados siguientes: AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetstatusbarpanetextcolora--cmfcvisualmanagergetstatusbarpanetextcolor"></a><a name="getstatusbarpanetextcolor"></a>CMFCVisualManager::GetStatusBarPaneTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetStatusBarPaneTextColor(
    CMFCStatusBar* pStatusBar,  
    CMFCStatusBarPaneInfo* pPane);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pStatusBar`  
 [in] `pPane`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabframecolorsa--cmfcvisualmanagergettabframecolors"></a><a name="gettabframecolors"></a>CMFCVisualManager::GetTabFrameColors  
 El marco de trabajo llama a esta función cuando tiene que recuperar el conjunto de colores para dibujar una ventana de ficha.  
  
```  
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,  
    COLORREF& clrDark,  
    COLORREF& clrBlack,  
    COLORREF& clrHighlight,  
    COLORREF& clrFace,  
    COLORREF& clrDarkShadow,  
    COLORREF& clrLight,  
    CBrush*& pbrFace,  
    CBrush*& pbrBlack);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pTabWnd`  
 Puntero a la ventana con fichas donde el marco está dibujando una pestaña.  
  
 [out] `clrDark`  
 Una referencia a un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro donde este método almacena el color del borde oscuro de una pestaña.  
  
 [out] `clrBlack`  
 Una referencia a un `COLORREF` parámetro donde este método almacena el color del borde de la ventana de la ficha. El color predeterminado del borde es negro.  
  
 [out] `clrHighlight`  
 Una referencia a un `COLORREF` parámetro donde este método almacena el color para el estado de resaltado de la ventana de la ficha.  
  
 [out] `clrFace`  
 Una referencia a un `COLORREF` parámetro donde este método almacena el color de la cara de la ventana de la ficha.  
  
 [out] `clrDarkShadow`  
 Una referencia a un `COLORREF` parámetro donde este método almacena el color de la sombra de la ventana de la ficha.  
  
 [out] `clrLight`  
 Una referencia a un `COLORREF` parámetro donde este método almacena el color del borde de la ventana de la ficha claro.  
  
 [out] `pbrFace`  
 Puntero a una referencia de un pincel. Este método almacena el pincel que se usa para rellenar la cara de la ventana de ficha en este parámetro.  
  
 [out] `pbrBlack`  
 Puntero a una referencia de un pincel. Este método almacena el pincel que se usa para rellenar el borde negro de la ventana de la ficha de este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada si desea personalizar el conjunto de colores que el marco de trabajo usa al dibujar una ventana de la ficha.  
  
##  <a name="a-namegettabhorzmargina--cmfcvisualmanagergettabhorzmargin"></a><a name="gettabhorzmargin"></a>CMFCVisualManager::GetTabHorzMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabHorzMargin(const CMFCBaseTabCtrl*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CMFCBaseTabCtrl*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettabtextcolora--cmfcvisualmanagergettabtextcolor"></a><a name="gettabtextcolor"></a>CMFCVisualManager::GetTabTextColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetTabTextColor(
    const CMFCBaseTabCtrl*,
    int,
    BOOL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CMFCBaseTabCtrl*`  
 [in] `int`  
 [in] `BOOL`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanegroupcaptionheighta--cmfcvisualmanagergettaskspanegroupcaptionheight"></a><a name="gettaskspanegroupcaptionheight"></a>CMFCVisualManager::GetTasksPaneGroupCaptionHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneGroupCaptionHeight() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanegroupcaptionhorzoffseta--cmfcvisualmanagergettaskspanegroupcaptionhorzoffset"></a><a name="gettaskspanegroupcaptionhorzoffset"></a>CMFCVisualManager::GetTasksPaneGroupCaptionHorzOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneGroupCaptionHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanegroupcaptionvertoffseta--cmfcvisualmanagergettaskspanegroupcaptionvertoffset"></a><a name="gettaskspanegroupcaptionvertoffset"></a>CMFCVisualManager::GetTasksPaneGroupCaptionVertOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneGroupCaptionVertOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanegroupvertoffseta--cmfcvisualmanagergettaskspanegroupvertoffset"></a><a name="gettaskspanegroupvertoffset"></a>CMFCVisualManager::GetTasksPaneGroupVertOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneGroupVertOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanehorzmargina--cmfcvisualmanagergettaskspanehorzmargin"></a><a name="gettaskspanehorzmargin"></a>CMFCVisualManager::GetTasksPaneHorzMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneHorzMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspaneiconhorzoffseta--cmfcvisualmanagergettaskspaneiconhorzoffset"></a><a name="gettaskspaneiconhorzoffset"></a>CMFCVisualManager::GetTasksPaneIconHorzOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneIconHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspaneiconvertoffseta--cmfcvisualmanagergettaskspaneiconvertoffset"></a><a name="gettaskspaneiconvertoffset"></a>CMFCVisualManager::GetTasksPaneIconVertOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneIconVertOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanetaskhorzoffseta--cmfcvisualmanagergettaskspanetaskhorzoffset"></a><a name="gettaskspanetaskhorzoffset"></a>CMFCVisualManager::GetTasksPaneTaskHorzOffset  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneTaskHorzOffset() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettaskspanevertmargina--cmfcvisualmanagergettaskspanevertmargin"></a><a name="gettaskspanevertmargin"></a>CMFCVisualManager::GetTasksPaneVertMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
int GetTasksPaneVertMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettoolbarbuttontextcolora--cmfcvisualmanagergettoolbarbuttontextcolor"></a><a name="gettoolbarbuttontextcolor"></a>CMFCVisualManager::GetToolbarButtonTextColor  
 El marco de trabajo llama a este método para determinar el color del texto de un botón de barra de herramientas.  
  
```  
virtual COLORREF GetToolbarButtonTextColor(
    CMFCToolBarButton* pButton,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pButton`  
 Un puntero al botón de barra de herramientas.  
  
 [in] `state`  
 El estado del botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Color del texto de `pButton` que tiene el estado indicado por `state`.  
  
### <a name="remarks"></a>Comentarios  
 Color del texto de un [CMFCToolBarButton clase](../../mfc/reference/cmfctoolbarbutton-class.md) objeto depende del estado del botón. Los Estados posibles de un botón de barra de herramientas son `ButtonsIsRegular`, `ButtonsIsPressed`, o `ButtonsIsHighlighted`.  
  
 Reemplazar esta función para personalizar el color del texto de un botón de barra de herramientas de la aplicación.  
  
##  <a name="a-namegettoolbarcustomizebuttonmargina--cmfcvisualmanagergettoolbarcustomizebuttonmargin"></a><a name="gettoolbarcustomizebuttonmargin"></a>CMFCVisualManager::GetToolBarCustomizeButtonMargin  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetToolBarCustomizeButtonMargin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettoolbardisabledcolora--cmfcvisualmanagergettoolbardisabledcolor"></a><a name="gettoolbardisabledcolor"></a>CMFCVisualManager::GetToolbarDisabledColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetToolbarDisabledColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettoolbardisabledtextcolora--cmfcvisualmanagergettoolbardisabledtextcolor"></a><a name="gettoolbardisabledtextcolor"></a>CMFCVisualManager::GetToolbarDisabledTextColor  
 El marco de trabajo llama a esta función para determinar el color del texto de los botones de barra de herramientas que no están disponibles.  
  
```  
virtual COLORREF GetToolbarDisabledTextColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color que utiliza el marco de trabajo para el color del texto de los botones de barra de herramientas que no están disponibles.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual personalizado para establecer el color del texto de los botones de barra de herramientas que no están disponibles.  
  
##  <a name="a-namegettoolbarhighlightcolora--cmfcvisualmanagergettoolbarhighlightcolor"></a><a name="gettoolbarhighlightcolor"></a>CMFCVisualManager::GetToolbarHighlightColor  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF GetToolbarHighlightColor();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegettooltipinfoa--cmfcvisualmanagergettooltipinfo"></a><a name="gettooltipinfo"></a>CMFCVisualManager::GetToolTipInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL GetToolTipInfo(
    CMFCToolTipInfo& params,  
    UINT nType = (UINT)(-1));
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `params`  
 [in] `nType`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehasoverlappedautohidebuttonsa--cmfcvisualmanagerhasoverlappedautohidebuttons"></a><a name="hasoverlappedautohidebuttons"></a>CMFCVisualManager::HasOverlappedAutoHideButtons  
 Devuelve si se superponen los botones de ocultación automática en el administrador visual actual.  
  
```  
virtual BOOL HasOverlappedAutoHideButtons() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se superponen los botones de ocultación automática; `FALSE` si no lo hace.  
  
##  <a name="a-nameisautodestroya--cmfcvisualmanagerisautodestroy"></a><a name="isautodestroy"></a>CMFCVisualManager::IsAutoDestroy  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAutoDestroy() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdefaultwinxppopupbuttona--cmfcvisualmanagerisdefaultwinxppopupbutton"></a><a name="isdefaultwinxppopupbutton"></a>CMFCVisualManager::IsDefaultWinXPPopupButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsDefaultWinXPPopupButton(CMFCDesktopAlertWndButton*) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CMFCDesktopAlertWndButton*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisdockingtabhasbordera--cmfcvisualmanagerisdockingtabhasborder"></a><a name="isdockingtabhasborder"></a>CMFCVisualManager::IsDockingTabHasBorder  
 Devuelve si el administrador visual actual dibuja bordes alrededor de los paneles que se acopla y por fichas.  
  
```  
virtual BOOL IsDockingTabHasBorder();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el administrador visual dibuja bordes alrededor de los paneles que se acopla y fichas; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Los paneles acoplados se convierten en fichas cuando varios paneles se acoplan en la misma ubicación.  
  
##  <a name="a-nameisembossdisabledimagea--cmfcvisualmanagerisembossdisabledimage"></a><a name="isembossdisabledimage"></a>CMFCVisualManager::IsEmbossDisabledImage  
 Especifica si el marco de trabajo se pone en relieve imágenes que no están disponibles.  
  
```  
BOOL IsEmbossDisabledImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el marco de trabajo se pone en relieve imágenes que no están disponibles; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por [CMFCToolBarImages::Draw](../../mfc/reference/cmfctoolbarimages-class.md#draw) cuando dibuja una imagen en la barra de herramientas que no está disponible.  
  
##  <a name="a-nameisfadeinactiveimagea--cmfcvisualmanagerisfadeinactiveimage"></a><a name="isfadeinactiveimage"></a>CMFCVisualManager::IsFadeInactiveImage  
 El marco de trabajo llama a este método cuando dibuja imágenes inactivas en la barra de herramientas o en un menú.  
  
```  
BOOL IsFadeInactiveImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el marco de trabajo utiliza el efecto de iluminación cuando dibuja imágenes inactivas en la barra de herramientas o en un menú; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Puede activar o desactivar el efecto de iluminación mediante una llamada a [CMFCVisualManager::SetFadeInactiveImage](#setfadeinactiveimage). El efecto de iluminación es lo que hace que las imágenes disponibles aparecen descolorida.  
  
##  <a name="a-nameisframemenucheckeditemsa--cmfcvisualmanagerisframemenucheckeditems"></a><a name="isframemenucheckeditems"></a>CMFCVisualManager::IsFrameMenuCheckedItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFrameMenuCheckedItems() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameishighlightonenotetabsa--cmfcvisualmanagerishighlightonenotetabs"></a><a name="ishighlightonenotetabs"></a>CMFCVisualManager::IsHighlightOneNoteTabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsHighlightOneNoteTabs() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameishighlightwholemenuitema--cmfcvisualmanagerishighlightwholemenuitem"></a><a name="ishighlightwholemenuitem"></a>CMFCVisualManager::IsHighlightWholeMenuItem  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsHighlightWholeMenuItem();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameislayeredribbonkeytipa--cmfcvisualmanagerislayeredribbonkeytip"></a><a name="islayeredribbonkeytip"></a>CMFCVisualManager::IsLayeredRibbonKeyTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsLayeredRibbonKeyTip() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameismenuflatlooka--cmfcvisualmanagerismenuflatlook"></a><a name="ismenuflatlook"></a>CMFCVisualManager::IsMenuFlatLook  
 Indica si los botones de menú aparecen sin formato.  
  
```  
BOOL IsMenuFlatLook() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si los botones de menú aparecen sin formato; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de menú no aparecen sin formato. Utilice la [CMFCVisualManager::SetMenuFlatLook](#setmenuflatlook) método para cambiar este comportamiento. Cuando los botones de menú aparecen sin formato, no cambie apariencia cuando el usuario hace clic en ellos.  
  
##  <a name="a-nameisofficexpstylemenusa--cmfcvisualmanagerisofficexpstylemenus"></a><a name="isofficexpstylemenus"></a>CMFCVisualManager::IsOfficeXPStyleMenus  
 Indica si el administrador visual implementa los menús del estilo de Office XP.  
  
```  
virtual BOOL IsOfficeXPStyleMenus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el administrador visual muestra los menús de estilo de Office XP. en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md) llama a este método cuando hay que dibujar el menú y las instantáneas. De forma predeterminada, este método devuelve `FALSE`. Si desea usar los menús emergentes similares a los menús emergentes en Office XP, invalide este método en un administrador visual personalizado y devolver `TRUE`.  
  
##  <a name="a-nameisoffsetpressedbuttona--cmfcvisualmanagerisoffsetpressedbutton"></a><a name="isoffsetpressedbutton"></a>CMFCVisualManager::IsOffsetPressedButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsOffsetPressedButton() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisownerdrawcaptiona--cmfcvisualmanagerisownerdrawcaption"></a><a name="isownerdrawcaption"></a>CMFCVisualManager::IsOwnerDrawCaption  
 Indica si el administrador visual actual implementa títulos dibujado por el propietario.  
  
```  
virtual BOOL IsOwnerDrawCaption();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si todas las ventanas de marco de la aplicación tienen títulos dibujados por el propietario; `FALSE` en caso contrario.  
  
##  <a name="a-nameisownerdrawmenuchecka--cmfcvisualmanagerisownerdrawmenucheck"></a><a name="isownerdrawmenucheck"></a>CMFCVisualManager::IsOwnerDrawMenuCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsOwnerDrawMenuCheck();
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisshadowhighlightedimagea--cmfcvisualmanagerisshadowhighlightedimage"></a><a name="isshadowhighlightedimage"></a>CMFCVisualManager::IsShadowHighlightedImage  
 Indica si el administrador visual muestra sombras al representar imágenes resaltadas.  
  
```  
BOOL IsShadowHighlightedImage() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero cuando el administrador visual muestra sombras en imágenes resaltadas; en caso contrario, es 0.  
  
##  <a name="a-nameistoolbarbuttonfillenableda--cmfcvisualmanageristoolbarbuttonfillenabled"></a><a name="istoolbarbuttonfillenabled"></a>CMFCVisualManager::IsToolbarButtonFillEnabled  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsToolbarButtonFillEnabled() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameistoolbarroundshapea--cmfcvisualmanageristoolbarroundshape"></a><a name="istoolbarroundshape"></a>CMFCVisualManager::IsToolbarRoundShape  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsToolbarRoundShape(CMFCToolBar*);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `CMFCToolBar*`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameiswindowsthemingsupporteda--cmfcvisualmanageriswindowsthemingsupported"></a><a name="iswindowsthemingsupported"></a>CMFCVisualManager::IsWindowsThemingSupported  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsWindowsThemingSupported() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonactivateappa--cmfcvisualmanageronactivateapp"></a><a name="onactivateapp"></a>CMFCVisualManager::OnActivateApp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnActivateApp(
    CWnd* pWnd,  
    BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `bActive`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawautohidebuttonbordera--cmfcvisualmanagerondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManager::OnDrawAutoHideButtonBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un botón de ocultación automática.  
  
```  
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectBounds`  
 El tamaño y la ubicación del botón Ocultar automáticamente.  
  
 [in] `rectBorderSize`  
 Un [CRect](../../atl-mfc-shared/reference/crect-class.md) parámetro que contiene los tamaños de los bordes.  
  
 [in] `pButton`  
 Un puntero al botón Ocultar automáticamente. El marco de trabajo dibuja el borde de este botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada si desea personalizar la apariencia del borde de un botón de ocultación automática. De forma predeterminada, este método rellena un borde plana con el color de sombra predeterminado para la aplicación.  
  
 El `rectBorderSize` parámetro contiene las coordenadas del borde. Contiene el tamaño del borde en el `top`, `bottom`, `left`, y `right` los miembros de datos. Un valor menor o igual que 0 no indica ningún borde de ese lado del botón Ocultar automáticamente.  
  
##  <a name="a-nameondrawbargrippera--cmfcvisualmanagerondrawbargripper"></a><a name="ondrawbargripper"></a>CMFCVisualManager::OnDrawBarGripper  
 Llamado por el marco de trabajo cuando dibuja el redimensionamiento de una barra de control.  
  
```  
virtual void OnDrawBarGripper(
    CDC* pDC,  
    CRect rectGripper,  
    BOOL bHorz,  
    CBasePane* pBar);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo para una barra de controles.  
  
 [in] `rectGripper`  
 El rectángulo delimitador de la barra de control.  
  
 [in] `bHorz`  
 Parámetro booleano que especifica si se acopla la barra de control horizontal o verticalmente.  
  
 [in] `pBar`  
 Puntero a una barra de controles. El administrador visual dibuja al redimensionamiento de esta barra de control.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método muestra al redimensionamiento estándar. Para personalizar la apariencia de la barra de redimensionamiento, invalide este método en una clase personalizada derivada de la `CMFCVisualManager` clase.  
  
##  <a name="a-nameondrawbrowsebuttona--cmfcvisualmanagerondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCVisualManager::OnDrawBrowseButton  
 El marco de trabajo llama a este método cuando dibuja el botón Examinar para un control de edición.  
  
```  
virtual BOOL OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    CMFCEditBrowseCtrl* pEdit,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica el límite para el botón Examinar.  
  
 [in] `pEdit`  
 Puntero a un control de edición. El administrador visual dibuja el botón Examinar para este control de edición.  
  
 [in] `state`  
 Un valor enumerado que especifica el estado del botón.  
  
 [out] `clrText`  
 Una referencia a un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro. Esto es un valor reservado y no se utiliza actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` si es correcto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada si desea personalizar la apariencia de los botones de exploración en instancias de la [CMFCEditBrowseCtrl clase](../../mfc/reference/cmfceditbrowsectrl-class.md). Los valores posibles para el estado del botón son `ButtonsIsRegular`, `ButtonsIsPressed`, y `ButtonsIsHighlighted`.  
  
##  <a name="a-nameondrawbuttonbordera--cmfcvisualmanagerondrawbuttonborder"></a><a name="ondrawbuttonborder"></a>CMFCVisualManager::OnDrawButtonBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un botón de barra de herramientas.  
  
```  
virtual void OnDrawButtonBorder(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo de un botón de barra de herramientas.  
  
 [in] `pButton`  
 Puntero a un botón de barra de herramientas. El marco dibuja el borde del botón.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón de barra de herramientas.  
  
 [in] `state`  
 Un tipo de datos enumerado que especifica el estado actual del botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método muestra el borde estándar. Invalide este método en un administrador visual derivado para personalizar la apariencia del borde de un botón de barra de herramientas.  
  
 Los Estados posibles de un botón de barra de herramientas son `ButtonsIsRegular`, `ButtonsIsPressed`, o `ButtonsIsHighlighted`.  
  
##  <a name="a-nameondrawbuttonseparatora--cmfcvisualmanagerondrawbuttonseparator"></a><a name="ondrawbuttonseparator"></a>CMFCVisualManager::OnDrawButtonSeparator  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawButtonSeparator(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rect`  
 [in] `state`  
 [in] `bHorz`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawcaptionbarbordera--cmfcvisualmanagerondrawcaptionbarborder"></a><a name="ondrawcaptionbarborder"></a>CMFCVisualManager::OnDrawCaptionBarBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un [CMFCCaptionBar Class](../../mfc/reference/cmfccaptionbar-class.md) objeto.  
  
```  
virtual void OnDrawCaptionBarBorder(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect,  
    COLORREF clrBarBorder,  
    BOOL bFlatBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Un puntero a un `CMFCCaptionBar` objeto. El marco dibuja esta barra de título.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la barra de título.  
  
 [in] `clrBarBorder`  
 El color del borde.  
  
 [in] `bFlatBorder`  
 Parámetro booleano que especifica si el borde tiene un aspecto plano 2D.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia del borde de una barra de título.  
  
##  <a name="a-nameondrawcaptionbarbuttonbordera--cmfcvisualmanagerondrawcaptionbarbuttonborder"></a><a name="ondrawcaptionbarbuttonborder"></a>CMFCVisualManager::OnDrawCaptionBarButtonBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawCaptionBarButtonBorder(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted,  
    BOOL bIsDisabled,  
    BOOL bHasDropDownArrow,  
    BOOL bIsSysButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pBar`  
 [in] `rect`  
 [in] `bIsPressed`  
 [in] `bIsHighlighted`  
 [in] `bIsDisabled`  
 [in] `bHasDropDownArrow`  
 [in] `bIsSysButton`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawcaptionbarinfoareaa--cmfcvisualmanagerondrawcaptionbarinfoarea"></a><a name="ondrawcaptionbarinfoarea"></a>CMFCVisualManager::OnDrawCaptionBarInfoArea  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawCaptionBarInfoArea(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pBar`  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawcaptionbuttona--cmfcvisualmanagerondrawcaptionbutton"></a><a name="ondrawcaptionbutton"></a>CMFCVisualManager::OnDrawCaptionButton  
 El marco de trabajo llama a este método cuando dibuja un [CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md) objeto.  
  
```  
virtual void OnDrawCaptionButton (
    CDC* pDC,  
    CMFCCaptionButton* pButton,  
    BOOL bActive,  
    BOOL bHorz,  
    BOOL bMaximized,  
    BOOL bDisabled,  
    int nImageID = -1);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a un `CMFCCaptionButton` objeto. El marco dibuja este botón de título.  
  
 [in] `bActive`  
 Parámetro booleano que especifica si el botón está activo.  
  
 [in] `bHorz`  
 Parámetro booleano que especifica si el título es horizontal.  
  
 [in] `bMaximized`  
 Parámetro booleano que especifica si el panel primario está maximizado.  
  
 [in] `bDisabled`  
 Parámetro booleano que especifica si se deshabilita el botón de título.  
  
 [in] `nImageID`  
 El índice de la imagen del icono que se utilizará para el botón. Si `nImageID` es -1, este método usa el índice de imagen se registra en `pButton`.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método muestra un pequeño botón de la instancia global de la `CMenuImages` clase. Los botones se enumeran en el archivo de encabezado `CMenuImages`. Some examples include `CMenuImages::IdClose`, `CMenuImages::IdArowLeft`, `CMenuImages::IdArowRight`, `CMenuImages::IdArowDown`, `CMenuImages::IdArowUp`, and `CMenuImages::IdPinHorz`.  
  
 Invalide este método en una clase derivada para personalizar la apariencia de los botones de título.  
  
##  <a name="a-nameondrawcheckboxa--cmfcvisualmanagerondrawcheckbox"></a><a name="ondrawcheckbox"></a>CMFCVisualManager::OnDrawCheckBox  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawCheckBox(
    CDC* pDC,  
    CRect rect,  
    BOOL bHighlighted,  
    BOOL bChecked,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `bHighlighted`  
 [in] `bChecked`  
 [in] `bEnabled`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawcheckboxexa--cmfcvisualmanagerondrawcheckboxex"></a><a name="ondrawcheckboxex"></a>CMFCVisualManager::OnDrawCheckBoxEx  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawCheckBoxEx(
    CDC* pDC,  
    CRect rect,  
    int nState,  
    BOOL bHighlighted,  
    BOOL bPressed,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `nState`  
 [in] `bHighlighted`  
 [in] `bPressed`  
 [in] `bEnabled`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawcombobordera--cmfcvisualmanagerondrawcomboborder"></a><a name="ondrawcomboborder"></a>CMFCVisualManager::OnDrawComboBorder  
 El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de la [CMFCToolBarComboBoxButton clase](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  
  
```  
virtual void OnDrawComboBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo de un botón de cuadro combinado.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón de cuadro combinado.  
  
 [in] `bDisabled`  
 Parámetro booleano que indica si el botón de cuadro combinado no está disponible.  
  
 [in] `bIsDropped`  
 Parámetro booleano que indica si el cuadro combinado está desplegado.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el botón de cuadro combinado.  
  
 [in] `pButton`  
 Un puntero a un `CMFCToolBarComboBoxButton` objeto. El marco dibuja este botón de cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en el administrador visual derivado para personalizar la apariencia del borde del cuadro combinado.  
  
##  <a name="a-nameondrawcombodropbuttona--cmfcvisualmanagerondrawcombodropbutton"></a><a name="ondrawcombodropbutton"></a>CMFCVisualManager::OnDrawComboDropButton  
 El marco de trabajo llama a este método cuando dibuja el botón desplegable de un [CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md).  
  
```  
virtual void OnDrawComboDropButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón desplegable.  
  
 [in] `bDisabled`  
 Parámetro booleano que indica si el botón no está disponible.  
  
 [in] `bIsDropped`  
 Parámetro booleano que indica si el cuadro combinado está desplegado.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el botón desplegable.  
  
 [in] `pButton`  
 Un puntero a un `CMFCToolBarComboBoxButton` objeto. El marco dibuja el botón desplegable de este botón de cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en el administrador visual derivado para personalizar el aspecto del botón desplegable de un botón de cuadro combinado.  
  
##  <a name="a-nameondrawcontrolbordera--cmfcvisualmanagerondrawcontrolborder"></a><a name="ondrawcontrolborder"></a>CMFCVisualManager::OnDrawControlBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawControlBorder(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWndCtrl`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawdefaultribbonimagea--cmfcvisualmanagerondrawdefaultribbonimage"></a><a name="ondrawdefaultribbonimage"></a>CMFCVisualManager::OnDrawDefaultRibbonImage  
 El marco de trabajo llama a este método cuando dibuja la imagen predeterminada que se utiliza para el botón de la cinta de opciones.  
  
```  
virtual void OnDrawDefaultRibbonImage(
    CDC* pDC,  
    CRect rectImage,  
    BOOL bIsDisabled = FALSE,  
    BOOL bIsPressed = FALSE,  
    BOOL bIsHighlighted = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectImage`  
 Un rectángulo que especifica los límites de la imagen predeterminada.  
  
 [in] `bIsDisabled`  
 Parámetro booleano que indica si el botón de la cinta de opciones está disponible.  
  
 [in] `bIsPressed`  
 Parámetro booleano que indica si se presiona el botón de la cinta de opciones.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el botón de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado si desea personalizar la imagen que se utiliza para el botón de la cinta de opciones.  
  
##  <a name="a-nameondraweditbordera--cmfcvisualmanagerondraweditborder"></a><a name="ondraweditborder"></a>CMFCVisualManager::OnDrawEditBorder  
 El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de la [CMFCToolBarEditBoxButton clase](../../mfc/reference/cmfctoolbareditboxbutton-class.md).  
  
```  
virtual void OnDrawEditBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsHighlighted,  
    CMFCToolBarEditBoxButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la `CMFCToolBarEditBoxButton` objeto.  
  
 [in] `bDisabled`  
 Parámetro booleano que indica si el botón no está disponible.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si el botón está resaltado.  
  
 [in] `pButton`  
 Un puntero a un `CMFCToolBarEditBoxButton` objeto. El marco dibuja el borde de este botón de cuadro de edición.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar el borde de un `CMFCToolBarEditBoxButton` objeto.  
  
##  <a name="a-nameondrawexpandingboxa--cmfcvisualmanagerondrawexpandingbox"></a><a name="ondrawexpandingbox"></a>CMFCVisualManager::OnDrawExpandingBox  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawExpandingBox(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsOpened,  
    COLORREF colorBox);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `bIsOpened`  
 [in] `colorBox`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawfloatingtoolbarbordera--cmfcvisualmanagerondrawfloatingtoolbarborder"></a><a name="ondrawfloatingtoolbarborder"></a>CMFCVisualManager::OnDrawFloatingToolbarBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de la barra de herramientas flotante.  
  
```  
virtual void OnDrawFloatingToolbarBorder(
    CDC* pDC,  
    CMFCBaseToolBar* pToolBar,  
    CRect rectBorder,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pToolBar`  
 Puntero a la barra de herramientas flotante.  
  
 [in] `rectBorder`  
 Un rectángulo que especifica los límites de la barra de herramientas flotante.  
  
 [in] `rectBorderSize`  
 Un rectángulo que especifica el tamaño del borde de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Barra de herramientas flotante es una barra de herramientas que aparece como una ventana de marco reducido. Normalmente, esto se produce cuando un usuario arrastra una barra de herramientas para que ya no está acoplado.  
  
 El tamaño del borde especificado por el parámetro correspondiente en `rectBorderSize`. Por ejemplo, se especifica el ancho del borde superior de la barra de herramientas por `rectBorderSize.top`.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del borde de la barra de herramientas flotante.  
  
##  <a name="a-nameondrawheaderctrlbordera--cmfcvisualmanagerondrawheaderctrlborder"></a><a name="ondrawheaderctrlborder"></a>CMFCVisualManager::OnDrawHeaderCtrlBorder  
 El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de la [CMFCHeaderCtrl clase](../../mfc/reference/cmfcheaderctrl-class.md).  
  
```  
virtual void OnDrawHeaderCtrlBorder(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect& rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCtrl`  
 Un puntero a un `CMFCHeaderCtrl` objeto. El marco dibuja el borde de este control de encabezado.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del control de encabezado.  
  
 [in] `bIsPressed`  
 Parámetro booleano que indica si se presiona el control de encabezado.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el control de encabezado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar el borde del control de encabezado.  
  
##  <a name="a-nameondrawheaderctrlsortarrowa--cmfcvisualmanagerondrawheaderctrlsortarrow"></a><a name="ondrawheaderctrlsortarrow"></a>CMFCVisualManager::OnDrawHeaderCtrlSortArrow  
 El marco de trabajo llama a esta función cuando dibuja la flecha de ordenación de un control de encabezado.  
  
```  
virtual void OnDrawHeaderCtrlSortArrow(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect& rect,  
    BOOL bIsUp);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCtrl`  
 Puntero a un control de encabezado. El administrador visual dibuja la flecha de ordenación de este [CMFCHeaderCtrl clase](../../mfc/reference/cmfcheaderctrl-class.md) objeto.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la flecha de ordenación.  
  
 [in] `bIsUp`  
 Valor booleano que especifica la dirección de la flecha de ordenación.  
  
### <a name="remarks"></a>Comentarios  
 Si `bIsUp` es `TRUE`, el administrador visual dibuja una flecha arriba de la ordenación. Si es `FALSE`, el administrador visual dibuja una flecha de ordenación descendente. Invalidar `OnDrawHeaderCtrlSortArrow` en una clase derivada para personalizar la apariencia del botón de ordenación.  
  
##  <a name="a-nameondrawmenuarrowoncustomizelista--cmfcvisualmanagerondrawmenuarrowoncustomizelist"></a><a name="ondrawmenuarrowoncustomizelist"></a>CMFCVisualManager::OnDrawMenuArrowOnCustomizeList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMenuArrowOnCustomizeList(
    CDC* pDC,  
    CRect rectCommand,  
    BOOL bSelected);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rectCommand`  
 [in] `bSelected`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenubordera--cmfcvisualmanagerondrawmenuborder"></a><a name="ondrawmenuborder"></a>CMFCVisualManager::OnDrawMenuBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un [CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md).  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo para un `CMFCPopupMenu` objeto.  
  
 [in] `pMenu`  
 Un puntero a un `CMFCPopupMenu` objeto. El marco dibuja un borde alrededor de este menú emergente.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del menú emergente.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método muestra el borde del menú estándar. Invalide este método en un administrador visual derivado para personalizar la apariencia del borde del menú.  
  
##  <a name="a-nameondrawmenuchecka--cmfcvisualmanagerondrawmenucheck"></a><a name="ondrawmenucheck"></a>CMFCVisualManager::OnDrawMenuCheck  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMenuCheck(
    CDC* pDC,  
    CMFCToolBarMenuButton* pButton,  
    CRect rect,  
    BOOL bHighlight,  
    BOOL bIsRadio);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rect`  
 [in] `bHighlight`  
 [in] `bIsRadio`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenuitembuttona--cmfcvisualmanagerondrawmenuitembutton"></a><a name="ondrawmenuitembutton"></a>CMFCVisualManager::OnDrawMenuItemButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMenuItemButton(
    CDC* pDC,  
    CMFCToolBarMenuButton* pButton,  
    CRect rectButton,  
    BOOL bHighlight,  
    BOOL bDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rectButton`  
 [in] `bHighlight`  
 [in] `bDisabled`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenulabela--cmfcvisualmanagerondrawmenulabel"></a><a name="ondrawmenulabel"></a>CMFCVisualManager::OnDrawMenuLabel  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnDrawMenuLabel(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenuresizebara--cmfcvisualmanagerondrawmenuresizebar"></a><a name="ondrawmenuresizebar"></a>CMFCVisualManager::OnDrawMenuResizeBar  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMenuResizeBar(
    CDC* pDC,  
    CRect rect,  
    int nResizeFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `nResizeFlags`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenuscrollbuttona--cmfcvisualmanagerondrawmenuscrollbutton"></a><a name="ondrawmenuscrollbutton"></a>CMFCVisualManager::OnDrawMenuScrollButton  
 El marco de trabajo llama a este método cuando dibuja un botón de desplazamiento de menú.  
  
```  
virtual void OnDrawMenuScrollButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsScrollDown,  
    BOOL bIsHighlited,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón de desplazamiento.  
  
 [in] `bIsScrollDown`  
 Dibuja el administrador visual de un valor booleano que indica qué tipo de botón. Un valor de `TRUE` indica que el administrador visual dibuja un botón hacia abajo.  
  
 [in] `bIsHighlited`  
 Valor booleano que indica si el botón está resaltado.  
  
 [in] `bIsPressed`  
 Valor booleano que indica si se presiona el botón.  
  
 [in] `bIsDisabled`  
 Valor booleano que indica si el botón está deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los botones de desplazamiento de menú. Botones de desplazamiento de menú aparecen en el borde de los menús emergentes cuando la altura total de los elementos de menú supera el alto del menú emergente.  
  
##  <a name="a-nameondrawmenushadowa--cmfcvisualmanagerondrawmenushadow"></a><a name="ondrawmenushadow"></a>CMFCVisualManager::OnDrawMenuShadow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMenuShadow(
    CDC* pDC,  
    const CRect& rectClient,  
    const CRect& rectExclude,  
    int nDepth,  
    int iMinBrightness,  
    int iMaxBrightness,  
    CBitmap* pBmpSaveBottom,  
    CBitmap* pBmpSaveRight,  
    BOOL bRTL);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rectClient`  
 [in] `rectExclude`  
 [in] `nDepth`  
 [in] `iMinBrightness`  
 [in] `iMaxBrightness`  
 [in] `pBmpSaveBottom`  
 [in] `pBmpSaveRight`  
 [in] `bRTL`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawmenusystembuttona--cmfcvisualmanagerondrawmenusystembutton"></a><a name="ondrawmenusystembutton"></a>CMFCVisualManager::OnDrawMenuSystemButton  
 El marco de trabajo llama a este método cuando se dibuja un botón de menú sistema para la aplicación.  
  
```  
virtual void OnDrawMenuSystemButton(
    CDC* pDC,  
    CRect rect,  
    UINT uiSystemCommand,  
    UINT nStyle,  
    BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón.  
  
 [in] `uiSystemCommand`  
 Una marca que especifica qué comando del sistema está asociada con el botón. Los valores posibles son SC_CLOSE, SC_MINIMIZE y SC_RESTORE.  
  
 [in] `nStyle`  
 Indicador que especifica el estilo del botón actual. Los valores posibles son 0, TBBS_DISABLED y TBBS_PRESSED.  
  
 [in] `bHighlight`  
 Parámetro booleano que especifica si el botón está resaltado.  
  
### <a name="remarks"></a>Comentarios  
 Los botones de menú system son el **cerrar**, **minimizar**, **maximizar**, y **restaurar** los botones situados en la barra de título.  
  
 La implementación predeterminada de este método llama [CDC::DrawFrameControl](../../mfc/reference/cdc-class.md#drawframecontrol) con el `DFC_CAPTION` tipo. Invalide este método en su clase derivada Administrador visual para personalizar la apariencia de los botones del sistema.  
  
##  <a name="a-nameondrawminiframebordera--cmfcvisualmanagerondrawminiframeborder"></a><a name="ondrawminiframeborder"></a>CMFCVisualManager::OnDrawMiniFrameBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawMiniFrameBorder(
    CDC* pDC,  
    CPaneFrameWnd* pFrameWnd,  
    CRect rectBorder,  
    CRect rectBorderSize);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pFrameWnd`  
 [in] `rectBorder`  
 [in] `rectBorderSize`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawoutlookbarsplittera--cmfcvisualmanagerondrawoutlookbarsplitter"></a><a name="ondrawoutlookbarsplitter"></a>CMFCVisualManager::OnDrawOutlookBarSplitter  
 El marco de trabajo llama a este método cuando dibuja el separador de una barra de Outlook.  
  
```  
virtual void OnDrawOutlookBarSplitter(
    CDC* pDC,  
    CRect rectSplitter);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectSplitter`  
 Un rectángulo que especifica los límites del divisor.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los separadores en una barra de Outlook.  
  
##  <a name="a-nameondrawoutlookpagebuttonbordera--cmfcvisualmanagerondrawoutlookpagebuttonborder"></a><a name="ondrawoutlookpagebuttonborder"></a>CMFCVisualManager::OnDrawOutlookPageButtonBorder  
 Lo llama el marco de trabajo cuando dibuja el borde de un botón de la página de Outlook.  
  
```  
virtual void OnDrawOutlookPageButtonBorder(
    CDC* pDC,  
    CRect& rectBtn,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectBtn`  
 Un rectángulo que especifica el límite del botón página de Outlook.  
  
 [in] `bIsHighlighted`  
 Valor booleano que especifica si el botón está resaltado.  
  
 [in] `bIsPressed`  
 Valor booleano que especifica si se presiona el botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual personalizado para cambiar la apariencia del botón de página de Outlook.  
  
##  <a name="a-nameondrawpanebordera--cmfcvisualmanagerondrawpaneborder"></a><a name="ondrawpaneborder"></a>CMFCVisualManager::OnDrawPaneBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un [CPane clase](../../mfc/reference/cpane-class.md) objeto.  
  
```  
virtual void OnDrawPaneBorder(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo de una barra de control.  
  
 [in] `pBar`  
 Un puntero a un panel. El administrador visual dibuja el borde de este panel.  
  
 [in] `rect`  
 Rectángulo que indica los límites del panel.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método muestra el borde estándar. Invalide este método en una clase derivada para personalizar la apariencia del borde.  
  
##  <a name="a-nameondrawpanecaptiona--cmfcvisualmanagerondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManager::OnDrawPaneCaption  
 El marco de trabajo llama a este método cuando dibuja un título para una instancia de la [CDockablePane Class](../../mfc/reference/cdockablepane-class.md).  
  
```  
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,  
    CDockablePane* pBar,  
    BOOL bActive,  
    CRect rectCaption,  
    CRect rectButtons);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Un puntero a un `CDockablePane` objeto. El marco dibuja el título de este panel.  
  
 [in] `bActive`  
 Parámetro booleano que indica si la barra de control está activa.  
  
 [in] `rectCaption`  
 Un rectángulo que especifica los límites del título.  
  
 [in] `rectButtons`  
 Un rectángulo que especifica los límites de los botones de título.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto del título.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los títulos de panel.  
  
##  <a name="a-nameondrawpanedividera--cmfcvisualmanagerondrawpanedivider"></a><a name="ondrawpanedivider"></a>CMFCVisualManager::OnDrawPaneDivider  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawPaneDivider(
    CDC* pDC,  
    CPaneDivider* pSlider,  
    CRect rect,  
    BOOL bAutoHideMode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pSlider`  
 [in] `rect`  
 [in] `bAutoHideMode`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawpopupwindowbordera--cmfcvisualmanagerondrawpopupwindowborder"></a><a name="ondrawpopupwindowborder"></a>CMFCVisualManager::OnDrawPopupWindowBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawPopupWindowBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawpopupwindowbuttonbordera--cmfcvisualmanagerondrawpopupwindowbuttonborder"></a><a name="ondrawpopupwindowbuttonborder"></a>CMFCVisualManager::OnDrawPopupWindowButtonBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawPopupWindowButtonBorder(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rectClient`  
 [in] `pButton`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawpopupwindowcaptiona--cmfcvisualmanagerondrawpopupwindowcaption"></a><a name="ondrawpopupwindowcaption"></a>CMFCVisualManager::OnDrawPopupWindowCaption  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnDrawPopupWindowCaption(
    CDC* pDC,  
    CRect rectCaption,  
    CMFCDesktopAlertWnd* pPopupWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rectCaption`  
 [in] `pPopupWnd`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbonapplicationbuttona--cmfcvisualmanagerondrawribbonapplicationbutton"></a><a name="ondrawribbonapplicationbutton"></a>CMFCVisualManager::OnDrawRibbonApplicationButton  
 El marco de trabajo llama a este método cuando dibuja el **botón principal** en la cinta de opciones.  
  
```  
virtual void OnDrawRibbonApplicationButton(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a la **botón principal** en la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado si desea personalizar la apariencia de la **botón principal**.  
  
##  <a name="a-nameondrawribbonbuttonbordera--cmfcvisualmanagerondrawribbonbuttonborder"></a><a name="ondrawribbonbuttonborder"></a>CMFCVisualManager::OnDrawRibbonButtonBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un botón en la cinta de opciones.  
  
```  
virtual void OnDrawRibbonButtonBorder(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a un [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) objeto. El marco dibuja el borde de este botón de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un `CMFCRibbonButton`.  
  
##  <a name="a-nameondrawribbonbuttonsgroupa--cmfcvisualmanagerondrawribbonbuttonsgroup"></a><a name="ondrawribbonbuttonsgroup"></a>CMFCVisualManager::OnDrawRibbonButtonsGroup  
 El marco de trabajo llama a este método cuando dibuja un grupo de botones en la cinta de opciones.  
  
```  
virtual COLORREF OnDrawRibbonButtonsGroup(
    CDC* pDC,  
    CMFCRibbonButtonsGroup* pGroup,  
    CRect rectGroup);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pGroup`  
 Puntero a un grupo de botones de la cinta de opciones. El marco dibuja este grupo de botones.  
  
 [in] `rectGroup`  
 Un rectángulo que especifica los límites del grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor reservado. La implementación predeterminada devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un grupo de botones de la cinta de opciones.  
  
##  <a name="a-nameondrawribboncaptiona--cmfcvisualmanagerondrawribboncaption"></a><a name="ondrawribboncaption"></a>CMFCVisualManager::OnDrawRibbonCaption  
 El marco de trabajo llama a este método cuando dibuja la barra de título de la ventana de marco principal. El marco de trabajo llama a este método sólo si la cinta de opciones está integrado en el marco principal.  
  
```  
virtual void OnDrawRibbonCaption(
    CDC* pDC,  
    CMFCRibbonBar* pBar,  
    CRect rect,  
    CRect rectText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Puntero a una barra de cinta. El administrador visual dibuja esta barra de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la barra de la cinta de opciones.  
  
 [in] `rectText`  
 Un rectángulo que especifica los límites del texto de la barra de título.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en un administrador visual derivada para personalizar la apariencia de la barra de título. Este método solo afecta a la barra de título si la cinta de opciones se integra con la ventana de marco principal.  
  
##  <a name="a-nameondrawribboncaptionbuttona--cmfcvisualmanagerondrawribboncaptionbutton"></a><a name="ondrawribboncaptionbutton"></a>CMFCVisualManager::OnDrawRibbonCaptionButton  
 El marco de trabajo llama a este método cuando dibuja un botón de título que se encuentra en la barra de la cinta de opciones.  
  
```  
virtual void OnDrawRibbonCaptionButton(
    CDC* pDC,  
    CMFCRibbonCaptionButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo.  
  
 `pButton`  
 Un puntero a un `CMFCRibbonCaptionButton` clase. El marco dibuja este botón de título.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un botón de título en la cinta de opciones.  
  
##  <a name="a-nameondrawribboncategorya--cmfcvisualmanagerondrawribboncategory"></a><a name="ondrawribboncategory"></a>CMFCVisualManager::OnDrawRibbonCategory  
 El marco de trabajo llama a este método cuando dibuja un [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md) objeto.  
  
```  
virtual void OnDrawRibbonCategory(
    CDC* pDC,  
    CMFCRibbonCategory* pCategory,  
    CRect rectCategory);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pCategory`  
 Un puntero a un `CMFCRibbonCategory` objeto. El marco dibuja esta categoría de cinta de opciones.  
  
 [in] `rectCategory`  
 Un rectángulo que especifica el límite de los paneles de categoría en la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Una categoría de cinta es una agrupación lógica de comandos de menú. Para obtener más información acerca de las categorías de la cinta de opciones, consulte [CMFCRibbonCategory clase](../../mfc/reference/cmfcribboncategory-class.md).  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de una categoría de cinta de opciones.  
  
##  <a name="a-nameondrawribboncategorycaptiona--cmfcvisualmanagerondrawribboncategorycaption"></a><a name="ondrawribboncategorycaption"></a>CMFCVisualManager::OnDrawRibbonCategoryCaption  
 El marco de trabajo llama a este método cuando dibuja la barra de título de una categoría de cinta de opciones.  
  
```  
virtual COLORREF OnDrawRibbonCategoryCaption(
    CDC* pDC,  
    CMFCRibbonContextCaption* pContextCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 El contexto de dibujo.  
  
 [in] `pContextCaption`  
 Puntero a una barra de título. El administrador visual dibuja esto [CMFCRibbonContextCaption clase](../../mfc/reference/cmfcribboncontextcaption-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color del texto de la barra de título.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia de la barra de título de una categoría de cinta de opciones. Para obtener más información acerca de la barra de título, consulte [CMFCRibbonContextCaption clase](../../mfc/reference/cmfcribboncontextcaption-class.md).  
  
##  <a name="a-nameondrawribboncategoryscrolla--cmfcvisualmanagerondrawribboncategoryscroll"></a><a name="ondrawribboncategoryscroll"></a>CMFCVisualManager::OnDrawRibbonCategoryScroll  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonCategoryScroll(
    CDC* pDC,  
    CRibbonCategoryScroll* pScroll);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pScroll`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribboncategorytaba--cmfcvisualmanagerondrawribboncategorytab"></a><a name="ondrawribboncategorytab"></a>CMFCVisualManager::OnDrawRibbonCategoryTab  
 El marco de trabajo llama a este método cuando dibuja la pestaña para una categoría de cinta de opciones.  
  
```  
virtual COLORREF OnDrawRibbonCategoryTab(
    CDC* pDC,  
    CMFCRibbonTab* pTab,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pTab`  
 Un puntero a una instancia de la `CMFCRibbonTab` clase. El marco dibuja esta ficha.  
  
 [in] `bIsActive`  
 Parámetro booleano que indica si la ficha está activa.  
  
### <a name="return-value"></a>Valor devuelto  
 El color que se usa para el texto en la ficha de la categoría de cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de una ficha de categoría de cinta de opciones. Para obtener más información acerca de las categorías de la cinta de opciones, consulte [CMFCRibbonCategory clase](../../mfc/reference/cmfcribboncategory-class.md).  
  
##  <a name="a-nameondrawribboncheckboxonlista--cmfcvisualmanagerondrawribboncheckboxonlist"></a><a name="ondrawribboncheckboxonlist"></a>CMFCVisualManager::OnDrawRibbonCheckBoxOnList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonCheckBoxOnList(
    CDC* pDC,  
    CMFCRibbonCheckBox* pCheckBox,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pCheckBox`  
 [in] `rect`  
 [in] `bIsSelected`  
 [in] `bHighlighted`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribboncolorpaletteboxa--cmfcvisualmanagerondrawribboncolorpalettebox"></a><a name="ondrawribboncolorpalettebox"></a>CMFCVisualManager::OnDrawRibbonColorPaletteBox  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonColorPaletteBox(
    CDC* pDC,  
    CMFCRibbonColorButton* pColorButton,  
    CMFCRibbonGalleryIcon* pIcon,  
    COLORREF color,  
    CRect rect,  
    BOOL bDrawTopEdge,  
    BOOL bDrawBottomEdge,  
    BOOL bIsHighlighted,  
    BOOL bIsChecked,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pColorButton`  
 [in] `pIcon`  
 [in] `color`  
 [in] `rect`  
 [in] `bDrawTopEdge`  
 [in] `bDrawBottomEdge`  
 [in] `bIsHighlighted`  
 [in] `bIsChecked`  
 [in] `bIsDisabled`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbondefaultpanebuttona--cmfcvisualmanagerondrawribbondefaultpanebutton"></a><a name="ondrawribbondefaultpanebutton"></a>CMFCVisualManager::OnDrawRibbonDefaultPaneButton  
 El marco de trabajo llama a este método cuando dibuja el botón predeterminado en el panel de la cinta de opciones.  
  
```  
virtual void OnDrawRibbonDefaultPaneButton(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero al botón predeterminado para el panel de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo muestra el botón predeterminado cuando se cambia el tamaño de un panel de cinta de opciones a su tamaño mínimo y no hay ninguna área para mostrar el contenido del panel. Cuando el usuario hace clic en el botón predeterminado, el marco de trabajo muestra un menú que contiene el contenido del panel desplegable.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del botón predeterminado.  
  
##  <a name="a-nameondrawribbondefaultpanebuttoncontexta--cmfcvisualmanagerondrawribbondefaultpanebuttoncontext"></a><a name="ondrawribbondefaultpanebuttoncontext"></a>CMFCVisualManager::OnDrawRibbonDefaultPaneButtonContext  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonDefaultPaneButtonContext(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbondefaultpanebuttonindicatora--cmfcvisualmanagerondrawribbondefaultpanebuttonindicator"></a><a name="ondrawribbondefaultpanebuttonindicator"></a>CMFCVisualManager::OnDrawRibbonDefaultPaneButtonIndicator  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonDefaultPaneButtonIndicator(
    CDC* pDC,  
    CMFCRibbonButton* pButton,  
    CRect rect,  
    BOOL bIsSelected,  
    BOOL bHighlighted);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rect`  
 [in] `bIsSelected`  
 [in] `bHighlighted`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbongallerybordera--cmfcvisualmanagerondrawribbongalleryborder"></a><a name="ondrawribbongalleryborder"></a>CMFCVisualManager::OnDrawRibbonGalleryBorder  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonGalleryBorder(
    CDC* pDC,  
    CMFCRibbonGallery* pButton,  
    CRect rectBorder);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rectBorder`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbongallerybuttona--cmfcvisualmanagerondrawribbongallerybutton"></a><a name="ondrawribbongallerybutton"></a>CMFCVisualManager::OnDrawRibbonGalleryButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonGalleryButton(
    CDC* pDC,  
    CMFCRibbonGalleryIcon* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbonkeytipa--cmfcvisualmanagerondrawribbonkeytip"></a><a name="ondrawribbonkeytip"></a>CMFCVisualManager::OnDrawRibbonKeyTip  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonKeyTip(
    CDC* pDC,  
    CMFCRibbonBaseElement* pElement,  
    CRect rect,  
    CString str);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pElement`  
 [in] `rect`  
 [in] `str`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbonlabela--cmfcvisualmanagerondrawribbonlabel"></a><a name="ondrawribbonlabel"></a>CMFCVisualManager::OnDrawRibbonLabel  
 El marco de trabajo llama a este método cuando dibuja la etiqueta de la cinta de opciones.  
  
```  
virtual void OnDrawRibbonLabel(
    CDC* pDC,  
    CMFCRibbonLabel* pLabel,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pLabel`  
 Un puntero a un [CMFCRibbonLabel](../../mfc/reference/cmfcribbonlabel-class.md) objeto. El marco dibuja esta etiqueta de cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la etiqueta de cinta de opciones.  
  
##  <a name="a-nameondrawribbonmainpanelbuttonbordera--cmfcvisualmanagerondrawribbonmainpanelbuttonborder"></a><a name="ondrawribbonmainpanelbuttonborder"></a>CMFCVisualManager::OnDrawRibbonMainPanelButtonBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) que está situado en el **principal** panel.  
  
```  
virtual void OnDrawRibbonMainPanelButtonBorder(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a un `CMFCRibbonButton` ubicado en el panel principal de la cinta de opciones. El marco dibuja el borde de este botón.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del borde de un `CMFCRibbonButton` en el **principal** panel.  
  
##  <a name="a-nameondrawribbonmainpanelframea--cmfcvisualmanagerondrawribbonmainpanelframe"></a><a name="ondrawribbonmainpanelframe"></a>CMFCVisualManager::OnDrawRibbonMainPanelFrame  
 El marco de trabajo llama a este método cuando dibuja el marco que rodea el [CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md).  
  
```  
virtual void OnDrawRibbonMainPanelFrame(
    CDC* pDC,  
    CMFCRibbonMainPanel* pPanel,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pPanel`  
 Un puntero a la `CMFCRibbonMainPanel`.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la `CMFCRibbonMainPanel`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del marco de la `CMFCRibbonMainPanel`.  
  
##  <a name="a-nameondrawribbonmenucheckframea--cmfcvisualmanagerondrawribbonmenucheckframe"></a><a name="ondrawribbonmenucheckframe"></a>CMFCVisualManager::OnDrawRibbonMenuCheckFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawRibbonMenuCheckFrame(
    CDC* pDC,  
    CMFCRibbonButton* pButton,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pButton`  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawribbonpanela--cmfcvisualmanagerondrawribbonpanel"></a><a name="ondrawribbonpanel"></a>CMFCVisualManager::OnDrawRibbonPanel  
 El marco de trabajo llama a este método cuando dibuja un [CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md) objeto.  
  
```  
virtual COLORREF OnDrawRibbonPanel(
    CDC* pDC,  
    CMFCRibbonPanel* pPanel,  
    CRect rectPanel,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pPanel`  
 Un puntero a un `CMFCRibbonPanel` objeto. El marco dibuja el panel de la cinta.  
  
 [in] `rectPanel`  
 Un rectángulo que especifica los límites del panel.  
  
 [in] `rectCaption`  
 Un rectángulo que especifica los límites del título del panel.  
  
### <a name="return-value"></a>Valor devuelto  
 El color del texto en el panel de la cinta.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia de un panel de cinta de opciones.  
  
##  <a name="a-nameondrawribbonpanelcaptiona--cmfcvisualmanagerondrawribbonpanelcaption"></a><a name="ondrawribbonpanelcaption"></a>CMFCVisualManager::OnDrawRibbonPanelCaption  
 El marco de trabajo llama a este método cuando se dibuja la leyenda de un [CMFCRibbonPanel clase](../../mfc/reference/cmfcribbonpanel-class.md).  
  
```  
virtual void OnDrawRibbonPanelCaption(
    CDC* pDC,  
    CMFCRibbonPanel* pPanel,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pPanel`  
 Un puntero a un `CMFCRibbonPanel` objeto. El marco dibuja el título de este panel de la cinta.  
  
 [in] `rectCaption`  
 Un rectángulo que especifica los límites del título del panel de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia de los títulos de los paneles de cinta.  
  
##  <a name="a-nameondrawribbonprogressbara--cmfcvisualmanagerondrawribbonprogressbar"></a><a name="ondrawribbonprogressbar"></a>CMFCVisualManager::OnDrawRibbonProgressBar  
 El marco de trabajo llama a este método cuando dibuja un [CMFCRibbonProgressBar clase](../../mfc/reference/cmfcribbonprogressbar-class.md).  
  
```  
virtual void OnDrawRibbonProgressBar(
    CDC* pDC,  
    CMFCRibbonProgressBar* pProgress,  
    CRect rectProgress,  
    CRect rectChunk,  
    BOOL bInfiniteMode);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pProgress`  
 Un puntero a un `CMFCRibbonProgressBar` objeto. El marco dibuja esta barra de progreso.  
  
 [in] `rectProgress`  
 Un rectángulo que especifica los límites de la barra de progreso.  
  
 [in] `rectChunk`  
 Un rectángulo que especifica los límites del área que rodea a la barra de progreso.  
  
 [in] `bInfiniteMode`  
 Parámetro booleano que indica el modo de la barra de progreso. Un valor de `TRUE` significa que la barra está en modo de infinito. La implementación predeterminada no utiliza este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia de una barra de progreso.  
  
##  <a name="a-nameondrawribbonquickaccesstoolbarseparatora--cmfcvisualmanagerondrawribbonquickaccesstoolbarseparator"></a><a name="ondrawribbonquickaccesstoolbarseparator"></a>CMFCVisualManager::OnDrawRibbonQuickAccessToolBarSeparator  
 El marco de trabajo llama a este método cuando dibuja un separador en el **la barra de herramientas de acceso rápido** de una cinta de opciones.  
  
```  
virtual void OnDrawRibbonQuickAccessToolBarSeparator(
    CDC* pDC,  
    CMFCRibbonSeparator* pSeparator,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSeparator`  
 Un puntero a un [CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md) objeto. El marco dibuja este separador de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del separador.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia de los separadores de la cinta de opciones en la **la barra de herramientas de acceso rápido**.  
  
##  <a name="a-nameondrawribbonrecentfilesframea--cmfcvisualmanagerondrawribbonrecentfilesframe"></a><a name="ondrawribbonrecentfilesframe"></a>CMFCVisualManager::OnDrawRibbonRecentFilesFrame  
 El marco de trabajo llama a este método cuando dibuja un marco alrededor de una lista de archivos recientes.  
  
```  
virtual void OnDrawRibbonRecentFilesFrame(
    CDC* pDC,  
    CMFCRibbonMainPanel* pPanel,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pPanel`  
 Un puntero a la **principal** panel en la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del marco de la lista de archivos recientes.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de la lista de archivos recientes.  
  
##  <a name="a-nameondrawribbonsliderchannela--cmfcvisualmanagerondrawribbonsliderchannel"></a><a name="ondrawribbonsliderchannel"></a>CMFCVisualManager::OnDrawRibbonSliderChannel  
 El marco de trabajo llama a este método cuando dibuja el canal de un [CMFCRibbonSlider clase](../../mfc/reference/cmfcribbonslider-class.md).  
  
```  
virtual void OnDrawRibbonSliderChannel(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSlider`  
 Puntero a un objeto CMFCRibbonSlider. El marco dibuja el canal para este control deslizante de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites para el canal del control deslizante de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en una clase derivada para personalizar la apariencia del canal del control deslizante de la cinta de opciones.  
  
##  <a name="a-nameondrawribbonsliderthumba--cmfcvisualmanagerondrawribbonsliderthumb"></a><a name="ondrawribbonsliderthumb"></a>CMFCVisualManager::OnDrawRibbonSliderThumb  
 El marco de trabajo llama a este método cuando se dibuja el control de posición de un [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) objeto.  
  
```  
virtual void OnDrawRibbonSliderThumb(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSlider`  
 Un puntero a un `CMFCRibbonSlider`. El marco dibuja el control de posición para este control deslizante de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del control de posición para el control deslizante de la cinta de opciones.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el control de posición.  
  
 [in] `bIsPressed`  
 Parámetro booleano que indica si el control está presionado.  
  
 [in] `bIsDisabled`  
 Parámetro booleano que indica si el control no está disponible.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del control de un `CMFCRibbonSlider`.  
  
##  <a name="a-nameondrawribbonsliderzoombuttona--cmfcvisualmanagerondrawribbonsliderzoombutton"></a><a name="ondrawribbonsliderzoombutton"></a>CMFCVisualManager::OnDrawRibbonSliderZoomButton  
 El marco de trabajo llama a este método cuando dibuja con los botones de zoom para un [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) objeto.  
  
```  
virtual void OnDrawRibbonSliderZoomButton(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsZoomOut,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSlider`  
 Un puntero a un `CMFCRibbonSlider` objeto. El marco dibuja este control deslizante de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de los botones de zoom en el control deslizante de la cinta de opciones.  
  
 [in] `bIsZoomOut`  
 Dibuja el marco de trabajo de un parámetro booleano que indica el botón. Un valor de `TRUE` indica que el botón primario con un "-" para alejar. Un valor de `FALSE` indica que el botón secundario con un signo "+" para acercar.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si el botón está resaltado.  
  
 [in] `bIsPressed`  
 Parámetro booleano que indica si se presiona el botón.  
  
 [in] `bIsDisabled`  
 Parámetro booleano que indica si el botón no está disponible.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, los botones de zoom en el control deslizante de la cinta de opciones son un círculo con cualquiera una + o - iniciar sesión en el centro. Para personalizar la apariencia de los botones de zoom, invalide este método en un administrador visual derivado.  
  
##  <a name="a-nameondrawribbonstatusbarpanea--cmfcvisualmanagerondrawribbonstatusbarpane"></a><a name="ondrawribbonstatusbarpane"></a>CMFCVisualManager::OnDrawRibbonStatusBarPane  
 El marco de trabajo llama a este método cuando dibuja un panel en la barra de estado.  
  
```  
virtual COLORREF OnDrawRibbonStatusBarPane(
    CDC* pDC,  
    CMFCRibbonStatusBar* pBar,  
    CMFCRibbonStatusBarPane* pPane);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Puntero a la barra de estado que contiene el panel.  
  
 [in] `pPane`  
 Puntero a un panel de barra de estado. El marco dibuja [CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor reservado. La implementación predeterminada devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un panel en la barra de estado.  
  
##  <a name="a-nameondrawribbontabsframea--cmfcvisualmanagerondrawribbontabsframe"></a><a name="ondrawribbontabsframe"></a>CMFCVisualManager::OnDrawRibbonTabsFrame  
 El marco de trabajo llama a este método cuando dibuja el marco alrededor de un conjunto de fichas de la cinta de opciones.  
  
```  
virtual COLORREF OnDrawRibbonTabsFrame(
    CDC* pDC,  
    CMFCRibbonBar* pWndRibbonBar,  
    CRect rectTab);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Puntero a un contexto de dispositivo.  
  
 `pWndRibbonBar`  
 Un puntero a un [CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md) objeto. El marco dibuja el marco para esta barra de la cinta de opciones.  
  
 `rectTab`  
 Un rectángulo que especifica los límites de las fichas de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor reservado. De forma predeterminada, este método devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar el marco que rodea un conjunto de pestañas en la cinta de opciones.  
  
##  <a name="a-nameondrawscrollbuttonsa--cmfcvisualmanagerondrawscrollbuttons"></a><a name="ondrawscrollbuttons"></a>CMFCVisualManager::OnDrawScrollButtons  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawScrollButtons(
    CDC* pDC,  
    const CRect& rect,  
    const int nBorderSize,  
    int iImage,  
    BOOL bHilited);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `nBorderSize`  
 [in] `iImage`  
 [in] `bHilited`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawseparatora--cmfcvisualmanagerondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManager::OnDrawSeparator  
 El marco de trabajo llama a este método cuando dibuja un separador.  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rect,  
    BOOL bIsHoriz);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo para una barra de controles.  
  
 [in] `pBar`  
 Puntero a un panel que contiene el separador.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del separador.  
  
 [in] `bIsHoriz`  
 Parámetro booleano que indica la orientación de un panel acoplado. Un valor de `TRUE` indica que el panel se acopla horizontalmente. Un valor de `FALSE` indica que el panel se acopla verticalmente.  
  
### <a name="remarks"></a>Comentarios  
 Los separadores se utilizan en las barras de control para separar grupos de iconos relacionados. La implementación predeterminada de este método muestra el separador estándar. Invalide este método en un administrador visual derivado para personalizar la apariencia del separador.  
  
##  <a name="a-nameondrawshowallmenuitemsa--cmfcvisualmanagerondrawshowallmenuitems"></a><a name="ondrawshowallmenuitems"></a>CMFCVisualManager::OnDrawShowAllMenuItems  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawShowAllMenuItems(
    CDC* pDC,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
 [in] `state`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawspinbuttonsa--cmfcvisualmanagerondrawspinbuttons"></a><a name="ondrawspinbuttons"></a>CMFCVisualManager::OnDrawSpinButtons  
 El marco de trabajo llama a este método cuando dibuja una instancia de la [CMFCSpinButtonCtrl clase](../../mfc/reference/cmfcspinbuttonctrl-class.md).  
  
```  
virtual void OnDrawSpinButtons(
    CDC* pDC,  
    CRect rectSpin,  
    int nState,  
    BOOL bOrientation,  
    CMFCSpinButtonCtrl* pSpinCtrl);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectSpin`  
 Un rectángulo que especifica los límites del control de giro.  
  
 [in] `nState`  
 Marca que indica el estado del control de giro. Vea la sección Comentarios para obtener más información.  
  
 [in] `bOrientation`  
 Parámetro booleano que especifica la orientación del control de giro. Un valor de `TRUE` indica el número control es horizontal. De lo contrario, es vertical.  
  
 [in] `pSpinCtrl`  
 Puntero a un control de número. El marco dibuja los botones para este control.  
  
### <a name="remarks"></a>Comentarios  
 El `nState` parámetro indica el estado del control de giro. El parámetro es uno de los siguientes valores:  
  
-   AFX_SPIN_PRESSEDUP  
  
-   AFX_SPIN_PRESSEDDOWN  
  
-   AFX_SPIN_HIGHLIGHTEDUP  
  
-   AFX_SPIN_HIGHLIGHTEDDOWN  
  
-   AFX_SPIN_DISABLED  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un control de número.  
  
##  <a name="a-nameondrawsplitterbordera--cmfcvisualmanagerondrawsplitterborder"></a><a name="ondrawsplitterborder"></a>CMFCVisualManager::OnDrawSplitterBorder  
 El marco de trabajo llama a este método cuando dibuja el borde alrededor de una instancia de la [CSplitterWndEx clase](csplitterwndex-class.md).  
  
```  
virtual void OnDrawSplitterBorder(
    CDC* pDC,  
    CSplitterWndEx* pSplitterWnd,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSplitterWnd`  
 Puntero a una ventana divisora. El marco dibuja el borde de esta ventana.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la ventana divisora.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del borde de una ventana divisora.  
  
##  <a name="a-nameondrawsplitterboxa--cmfcvisualmanagerondrawsplitterbox"></a><a name="ondrawsplitterbox"></a>CMFCVisualManager::OnDrawSplitterBox  
 El marco de trabajo llama a este método cuando dibuja el cuadro de arrastre de una instancia de la [CSplitterWndEx clase](csplitterwndex-class.md). El cuadro de arrastre aparece cuando el usuario selecciona la barra de división y cambia las dimensiones de las ventanas secundarias.  
  
```  
virtual void OnDrawSplitterBox(
    CDC* pDC,  
    CSplitterWndEx* pSplitterWnd,  
    CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSplitterWnd`  
 Puntero a una ventana divisora. El marco dibuja el cuadro de esta ventana divisora.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la ventana divisora.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del cuadro de arrastrar una ventana divisora.  
  
##  <a name="a-nameondrawstatusbarpanebordera--cmfcvisualmanagerondrawstatusbarpaneborder"></a><a name="ondrawstatusbarpaneborder"></a>CMFCVisualManager::OnDrawStatusBarPaneBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) objeto.  
  
```  
virtual void OnDrawStatusBarPaneBorder(
    CDC* pDC,  
    CMFCStatusBar* pBar,  
    CRect rectPane,  
    UINT uiID,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pBar`  
 Un puntero a un `CMFCStatusBar` objeto. El marco dibuja este objeto de la barra de estado.  
  
 [in] `rectPane`  
 Un rectángulo que especifica los límites de la barra de estado.  
  
 [in] `uiID`  
 El identificador de la barra de estado.  
  
 [in] `nStyle`  
 El estilo de la barra de estado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del borde de un `CMFCStatusBar` objeto.  
  
##  <a name="a-nameondrawstatusbarprogressa--cmfcvisualmanagerondrawstatusbarprogress"></a><a name="ondrawstatusbarprogress"></a>CMFCVisualManager::OnDrawStatusBarProgress  
 El marco de trabajo llama a este método cuando dibuja el indicador de progreso en la [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) objeto.  
  
```  
virtual void OnDrawStatusBarProgress(
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
 Un puntero al contexto de dispositivo para la barra de estado.  
  
 [in] `pStatusBar`  
 La `CMFCStatusBar` objeto que contiene la barra de progreso.  
  
 [in] `rectProgress`  
 Un rectángulo que especifica los límites de la barra de progreso.  
  
 [in] `nProgressTotal`  
 El número total de la barra de progreso.  
  
 [in] `nProgressCurr`  
 El progreso actual de la barra de progreso.  
  
 [in] `clrBar`  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro que indica el color inicial de la barra de progreso. El valor es el inicio de un degradado de color o el color de la barra de progreso completado.  
  
 [in] `clrProgressBarDest`  
 Un `COLORREF` parámetro que indica el final de un degradado de color de la barra de progreso. Si `clrProgressBarDest` es -1, el marco de trabajo no van a dibujar la barra de progreso como un degradado de color. En su lugar, que se llena la barra de progreso todo con el color especificado por `clrBar`.  
  
 [in] `clrProgressText`  
 Un `COLORREF` parámetro que indica el color del texto de la representación textual del progreso actual. Este parámetro se omite si `bProgressText` está establecido en `FALSE`.  
  
 [in] `bProgressText`  
 Parámetro booleano que indica si se muestra la representación textual del progreso actual.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de la `CMFCStatusBar` objeto.  
  
##  <a name="a-nameondrawstatusbarsizeboxa--cmfcvisualmanagerondrawstatusbarsizebox"></a><a name="ondrawstatusbarsizebox"></a>CMFCVisualManager::OnDrawStatusBarSizeBox  
 El marco de trabajo llama a este método cuando dibuja el cuadro de tamaño de una [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md).  
  
```  
virtual void OnDrawStatusBarSizeBox(
    CDC* pDC,  
    CMFCStatusBar* pStatBar,  
    CRect rectSizeBox);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pStatBar`  
 Puntero a una barra de estado. El marco dibuja el cuadro de tamaño para esta barra de estado.  
  
 [in] `rectSizeBox`  
 Un rectángulo que especifica los límites del cuadro de tamaño.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del cuadro de tamaño en un `CMFCStatusBar`.  
  
##  <a name="a-nameondrawtaba--cmfcvisualmanagerondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManager::OnDrawTab  
 El marco de trabajo llama a este método cuando dibuja las fichas para un [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto.  
  
```  
virtual void OnDrawTab(
    CDC* pDC,  
    CRect rectTab,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectTab`  
 Un rectángulo que especifica los límites del control de ficha.  
  
 [in] `iTab`  
 El índice de la pestaña que dibuja el marco de trabajo.  
  
 [in] `bIsActive`  
 Parámetro booleano que especifica si la ficha está activa.  
  
 [in] `pTabWnd`  
 Un puntero a un `CMFCBaseTabCtrl` objeto. El marco dibuja este control de pestaña.  
  
### <a name="remarks"></a>Comentarios  
 Un `CMFCBaseTabCtrl` objeto llama a este método cuando procesa el mensaje WM_PAINT.  
  
 Invalide este método en una clase derivada para personalizar la apariencia de fichas.  
  
##  <a name="a-nameondrawtabclosebuttona--cmfcvisualmanagerondrawtabclosebutton"></a><a name="ondrawtabclosebutton"></a>CMFCVisualManager::OnDrawTabCloseButton  
 El marco de trabajo llama a este método cuando dibuja el **cerrar** botón en la ficha activa.  
  
```  
virtual void OnDrawTabCloseButton(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la **cerrar** botón.  
  
 [in] `pTabWnd`  
 Puntero a un control de ficha. El marco se dibuja la **cerrar** botón para este control de pestaña.  
  
 [in] `bIsHighlighted`  
 Un parámetro booleano que indica si la **cerrar** botón está resaltado.  
  
 [in] `bIsPressed`  
 Un parámetro booleano que indica si la **cerrar** está presionado.  
  
 [in] `bIsDisabled`  
 Un parámetro booleano que indica si la **cerrar** botón está deshabilitado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de la **cerrar** en la ficha activa del botón `pTabWnd`.  
  
##  <a name="a-nameondrawtabcontenta--cmfcvisualmanagerondrawtabcontent"></a><a name="ondrawtabcontent"></a>CMFCVisualManager::OnDrawTabContent  
 El marco de trabajo llama a este método cuando dibuja el contenido que se encuentra en el interior de una instancia de la [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md).  
  
```  
virtual void OnDrawTabContent(
    CDC* pDC,  
    CRect rectTab,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd,  
    COLORREF clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectTab`  
 Un rectángulo que especifica los límites del interior de la ficha.  
  
 [in] `iTab`  
 Índice de base cero de la ficha. El marco dibuja el interior de esta ficha.  
  
 [in] `bIsActive`  
 Parámetro booleano que indica si está activa una ficha.  
  
 [in] `pTabWnd`  
 Un puntero al control de ficha que contiene la ficha que se va a dibujar.  
  
 [in] `clrText`  
 El color del texto en el interior de la ficha.  
  
### <a name="remarks"></a>Comentarios  
 El interior de una ficha contiene el texto y los iconos de la ficha. Invalide este método en un administrador visual derivado para personalizar la apariencia de fichas.  
  
##  <a name="a-nameondrawtabsbuttonbordera--cmfcvisualmanagerondrawtabsbuttonborder"></a><a name="ondrawtabsbuttonborder"></a>CMFCVisualManager::OnDrawTabsButtonBorder  
 El marco de trabajo llama a este método cuando dibuja el borde de un botón de la ficha.  
  
```  
virtual void OnDrawTabsButtonBorder(
    CDC* pDC,  
    CRect& rect,  
    CMFCButton* pButton,  
    UINT uiState,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón ficha.  
  
 [in] `pButton`  
 Un puntero a un [CMFCButton](../../mfc/reference/cmfcbutton-class.md) objeto. El marco dibuja el borde de este `CMFCButton` instancia.  
  
 [in] `uiState`  
 Un entero sin signo que especifica el estado del botón.  
  
 [in] `pWndTab`  
 Puntero a la ventana primaria de la ficha.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia del borde del botón ficha.  
  
##  <a name="a-nameondrawtaska--cmfcvisualmanagerondrawtask"></a><a name="ondrawtask"></a>CMFCVisualManager::OnDrawTask  
 El marco de trabajo llama a este método cuando dibuja un [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) objeto.  
  
```  
virtual void OnDrawTask(
    CDC* pDC,  
    CMFCTasksPaneTask* pTask,  
    CImageList* pIcons,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pTask`  
 Un puntero a un [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md) objeto. El marco dibuja esta tarea.  
  
 [in] `pIcons`  
 Puntero a la lista de imágenes asociada con el panel de tareas. Cada tarea contiene un índice de una imagen en esta lista.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que especifica si se resalta la tarea mostrada.  
  
 [in] `bIsSelected`  
 Parámetro booleano que especifica si se selecciona la tarea mostrada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo muestra las tareas en la barra de tareas como un icono y el texto. El `pIcons` parámetro contiene el icono de la tarea indicado por `pTask`.  
  
 Invalide este método en una clase derivada para personalizar la apariencia de las tareas en la barra de tareas.  
  
##  <a name="a-nameondrawtasksgroupareabordera--cmfcvisualmanagerondrawtasksgroupareaborder"></a><a name="ondrawtasksgroupareaborder"></a>CMFCVisualManager::OnDrawTasksGroupAreaBorder  
 El marco de trabajo llama a este método cuando dibuja un borde alrededor de un grupo en un [CMFCTasksPane clase](../../mfc/reference/cmfctaskspane-class.md).  
  
```  
virtual void OnDrawTasksGroupAreaBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE,  
    BOOL bNoTitle = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del área del grupo en el panel de tareas.  
  
 [in] `bSpecial`  
 Parámetro booleano que especifica si se resalta el borde. Un valor de `TRUE` indica que el borde se resalta.  
  
 [in] `bNoTitle`  
 Parámetro booleano que especifica si el área de grupo tiene un título. Un valor de `TRUE` indica que el área de grupo no tiene un título.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en una clase derivada para personalizar el borde alrededor de un área de grupo en el panel de tareas.  
  
##  <a name="a-nameondrawtasksgroupcaptiona--cmfcvisualmanagerondrawtasksgroupcaption"></a><a name="ondrawtasksgroupcaption"></a>CMFCVisualManager::OnDrawTasksGroupCaption  
 El marco de trabajo llama a este método cuando se dibuja la leyenda de un [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) objeto.  
  
```  
virtual void OnDrawTasksGroupCaption(
    CDC* pDC,  
    CMFCTasksPaneTaskGroup* pGroup,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE,  
    BOOL bCanCollapse = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pGroup`  
 Un puntero a un `CMFCTasksPaneTaskGroup` objeto. El marco dibuja la leyenda para este grupo.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el grupo.  
  
 [in] `bIsSelected`  
 Parámetro booleano que indica si el grupo está actualmente seleccionado.  
  
 [in] `bCanCollapse`  
 Parámetro booleano que indica si se puede contraer el grupo.  
  
### <a name="remarks"></a>Comentarios  
 Los grupos de tareas aparecen en la [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) objeto.  
  
 Invalide este método en una clase derivada para personalizar el título de un `CMFCTasksPaneTaskGroup`.  
  
##  <a name="a-nameondrawtasksgroupicona--cmfcvisualmanagerondrawtasksgroupicon"></a><a name="ondrawtasksgroupicon"></a>CMFCVisualManager::OnDrawTasksGroupIcon  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawTasksGroupIcon(
    CDC* pDC,  
    CMFCTasksPaneTaskGroup* pGroup,  
    int nIconHOffset = 5,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE,  
    BOOL bCanCollapse = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pGroup`  
 [in] `nIconHOffset`  
 [in] `bIsHighlighted`  
 [in] `bIsSelected`  
 [in] `bCanCollapse`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameondrawtearoffcaptiona--cmfcvisualmanagerondrawtearoffcaption"></a><a name="ondrawtearoffcaption"></a>CMFCVisualManager::OnDrawTearOffCaption  
 El marco de trabajo llama a este método cuando se dibuja la leyenda de un [CMFCPopupMenu clase](../../mfc/reference/cmfcpopupmenu-class.md).  
  
```  
virtual void OnDrawTearOffCaption(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del título.  
  
 [in] `bIsActive`  
 `TRUE`Si el título está activo; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función cuando un `CMFCPopupMenu` objeto procesa un mensaje WM_PAINT y debe dibujar un título desplazable.  
  
 Invalide este método en una clase derivada para personalizar el aspecto de los títulos de barras desplazable.  
  
##  <a name="a-nameondrawtoolboxframea--cmfcvisualmanagerondrawtoolboxframe"></a><a name="ondrawtoolboxframe"></a>CMFCVisualManager::OnDrawToolBoxFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDrawToolBoxFrame(
    CDC* pDC,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonerasemdiclientareaa--cmfcvisualmanageronerasemdiclientarea"></a><a name="onerasemdiclientarea"></a>CMFCVisualManager::OnEraseMDIClientArea  
 El marco de trabajo llama a este método cuando borra el área de cliente MDI.  
  
```  
virtual BOOL OnEraseMDIClientArea(
    CDC* pDC,  
    CRect rectClient);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectClient`  
 Un rectángulo que especifica los límites del área de cliente MDI.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor reservado. La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método para ejecutar código personalizado cuando el administrador visual borra el área de cliente MDI.  
  
##  <a name="a-nameonerasepopupwindowbuttona--cmfcvisualmanageronerasepopupwindowbutton"></a><a name="onerasepopupwindowbutton"></a>CMFCVisualManager::OnErasePopupWindowButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnErasePopupWindowButton(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `rectClient`  
 [in] `pButton`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonerasetabsareaa--cmfcvisualmanageronerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManager::OnEraseTabsArea  
 El marco de trabajo llama a este método cuando borra el área de la ficha de una ventana de ficha.  
  
```  
virtual void OnEraseTabsArea(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del área de ficha.  
  
 [in] `pTabWnd`  
 Puntero a una ventana de ficha. El marco de trabajo, borra el área de fichas de la ventana de la ficha especificada.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función cuando un [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md) objeto procesos un `WM_PAINT` mensaje y borra el área de fichas.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de fichas.  
  
##  <a name="a-nameonerasetabsbuttona--cmfcvisualmanageronerasetabsbutton"></a><a name="onerasetabsbutton"></a>CMFCVisualManager::OnEraseTabsButton  
 El marco de trabajo llama a este método cuando borran el texto y el icono de un botón de la ficha.  
  
```  
virtual void OnEraseTabsButton(
    CDC* pDC,  
    CRect rect,  
    CMFCButton* pButton,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón ficha.  
  
 [in] `pButton`  
 Puntero a un botón de la ficha. El marco de trabajo borra el texto y el icono para este botón.  
  
 [in] `pWndTab`  
 Un puntero al control de ficha que contiene el botón de la ficha.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo borra el texto y el icono de un botón cuando un [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) objeto procesos el `WM_ERASEBKGND` mensaje.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los botones de ficha.  
  
##  <a name="a-nameonerasetabsframea--cmfcvisualmanageronerasetabsframe"></a><a name="onerasetabsframe"></a>CMFCVisualManager::OnEraseTabsFrame  
 El marco de trabajo llama a este método cuando borra un marco en un [CMFCBaseTabCtrl clase](../../mfc/reference/cmfcbasetabctrl-class.md).  
  
```  
virtual BOOL OnEraseTabsFrame(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la ventana de la ficha.  
  
 [in] `pTabWnd`  
 Puntero a una ventana de ficha. El marco de trabajo borra un marco para este `CMFCBaseTabCtrl`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Este método rellena el área indicada por `rect` con el color de fondo de la ficha activa. Se llama cuando un `CMFCBaseTabCtrl` objeto procesos un `WM_PAINT` mensaje y borra un marco de ficha.  
  
##  <a name="a-nameonfillautohidebuttonbackgrounda--cmfcvisualmanageronfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManager::OnFillAutoHideButtonBackground  
 El marco de trabajo llama a este método cuando rellena el fondo de un botón de ocultación automática.  
  
```  
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,  
    CRect rect,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón Ocultar automáticamente.  
  
 [in] `pButton`  
 Un puntero a un [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md) objeto. El marco de trabajo rellena el fondo para este botón de ocultación automática.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un botón de ocultación automática.  
  
##  <a name="a-nameonfillbarbackgrounda--cmfcvisualmanageronfillbarbackground"></a><a name="onfillbarbackground"></a>CMFCVisualManager::OnFillBarBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de un [CBasePane](../../mfc/reference/cbasepane-class.md) objeto.  
  
```  
virtual void OnFillBarBackground(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rectClient,  
    CRect rectClip,  
    BOOL bNCArea = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo para una barra de controles.  
  
 [in] `pBar`  
 Un puntero a un `CBasePane` objeto. El marco de trabajo rellena el fondo de este panel.  
  
 [in] `rectClient`  
 Un rectángulo que especifica los límites del panel.  
  
 [in] `rectClip`  
 Un rectángulo que especifica el área de recorte del panel.  
  
 [in] `bNCArea`  
 Un valor reservado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método rellena el fondo de la barra con el color de fondo 3d de la variable global `afxGlobalData`. Invalide este método en un administrador visual derivado para personalizar el fondo de un panel.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el `OnFillBarBackground` en la `CMFCVisualManager` clase. Este fragmento de código forma parte de la [ejemplo de demostración de Outlook](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_OutlookDemo Nº&4;](../../mfc/reference/codesnippet/cpp/cmfcvisualmanager-class_2.cpp)]  
  
##  <a name="a-nameonfillbuttoninteriora--cmfcvisualmanageronfillbuttoninterior"></a><a name="onfillbuttoninterior"></a>CMFCVisualManager::OnFillButtonInterior  
 El marco de trabajo llama a este método cuando se llena el fondo de un botón de barra de herramientas.  
  
```  
virtual void OnFillButtonInterior(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo de un botón de barra de herramientas.  
  
 [in] `pButton`  
 Un puntero a un [CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md). El marco de trabajo rellena el fondo para este botón.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón de barra de herramientas.  
  
 [in] `state`  
 El estado del botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método utiliza el color predeterminado para rellenar el fondo. Invalide este método en un administrador visual derivado para personalizar el fondo de un botón de barra de herramientas.  
  
 Los Estados posibles de un botón de barra de herramientas son `ButtonsIsRegular`, `ButtonsIsPressed`, o `ButtonsIsHighlighted`.  
  
##  <a name="a-nameonfillcaptionbarbuttona--cmfcvisualmanageronfillcaptionbarbutton"></a><a name="onfillcaptionbarbutton"></a>CMFCVisualManager::OnFillCaptionBarButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF OnFillCaptionBarButton(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted,  
    BOOL bIsDisabled,  
    BOOL bHasDropDownArrow,  
    BOOL bIsSysButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pBar`  
 [in] `rect`  
 [in] `bIsPressed`  
 [in] `bIsHighlighted`  
 [in] `bIsDisabled`  
 [in] `bHasDropDownArrow`  
 [in] `bIsSysButton`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonfillcommandslistbackgrounda--cmfcvisualmanageronfillcommandslistbackground"></a><a name="onfillcommandslistbackground"></a>CMFCVisualManager::OnFillCommandsListBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de un botón de barra de herramientas a la que pertenece a una lista de comandos. Esta lista de comando forma parte del cuadro de diálogo de personalización.  
  
```  
virtual COLORREF OnFillCommandsListBackground(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón.  
  
 [in] `bIsSelected`  
 Parámetro booleano que indica si el botón está seleccionado.  
  
### <a name="return-value"></a>Valor devuelto  
 El color del texto del botón de barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de la lista de personalización, consulte [CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist). La implementación predeterminada de este método rellena el fondo basándose en la combinación de colores de la máscara seleccionada actualmente.  
  
##  <a name="a-nameonfillheaderctrlbackgrounda--cmfcvisualmanageronfillheaderctrlbackground"></a><a name="onfillheaderctrlbackground"></a>CMFCVisualManager::OnFillHeaderCtrlBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de un control de encabezado.  
  
```  
virtual void OnFillHeaderCtrlBackground(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pCtrl`  
 Un puntero a un [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md) objeto. El marco de trabajo rellena el fondo para este control de encabezado.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del control de encabezado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un control de encabezado.  
  
##  <a name="a-nameonfillminiframecaptiona--cmfcvisualmanageronfillminiframecaption"></a><a name="onfillminiframecaption"></a>CMFCVisualManager::OnFillMiniFrameCaption  
 El marco de trabajo llama a este método cuando se llena la barra de título de una ventana de marco flotante.  
  
```  
virtual COLORREF OnFillMiniFrameCaption(
    CDC* pDC,  
    CRect rectCaption,  
    CPaneFrameWnd* pFrameWnd,  
    BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectCaption`  
 Un rectángulo que especifica los límites de la barra de título.  
  
 [in] `pFrameWnd`  
 Puntero a una ventana de marco flotante. El marco dibuja la barra de título de esta ventana.  
  
 [in] `bActive`  
 Parámetro booleano que indica si la ventana está activa.  
  
### <a name="return-value"></a>Valor devuelto  
 El color que se usa para rellenar el fondo de la barra de título.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método rellena con el color de título actual de la máscara del activo en la barra de título.  
  
##  <a name="a-nameonfilloutlookbarcaptiona--cmfcvisualmanageronfilloutlookbarcaption"></a><a name="onfilloutlookbarcaption"></a>CMFCVisualManager::OnFillOutlookBarCaption  
 El marco de trabajo llama a este método cuando se llena el fondo de una barra de título de Outlook.  
  
```  
virtual void OnFillOutlookBarCaption(
    CDC* pDC,  
    CRect rectCaption,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectCaption`  
 Un rectángulo que especifica los límites de la barra de título.  
  
 [out] `clrText`  
 Una referencia a un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro. El método escribe el color del texto de la barra de título para este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método rellena la barra de título con el color de las sombras en función de la máscara actual. Invalide este método en un administrador visual derivado para personalizar el color de la barra de título de Outlook.  
  
##  <a name="a-nameonfilloutlookpagebuttona--cmfcvisualmanageronfilloutlookpagebutton"></a><a name="onfilloutlookpagebutton"></a>CMFCVisualManager::OnFillOutlookPageButton  
 El marco de trabajo llama a este método cuando rellena el interior de un botón de la página de Outlook.  
  
```  
virtual void OnFillOutlookPageButton(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del botón página de Outlook.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que especifica si el botón está resaltado.  
  
 [in] `bIsPressed`  
 Parámetro booleano que especifica si se presiona el botón.  
  
 [out] `clrText`  
 Una referencia a un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) parámetro. Este método almacena el color del texto del botón página de outlook en este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función en un administrador visual derivada para personalizar la apariencia de los botones de la página de Outlook.  
  
##  <a name="a-nameonfillpopupwindowbackgrounda--cmfcvisualmanageronfillpopupwindowbackground"></a><a name="onfillpopupwindowbackground"></a>CMFCVisualManager::OnFillPopupWindowBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de una ventana emergente.  
  
```  
virtual void OnFillPopupWindowBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la ventana emergente.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de las ventanas emergentes.  
  
##  <a name="a-nameonfillribbonbuttona--cmfcvisualmanageronfillribbonbutton"></a><a name="onfillribbonbutton"></a>CMFCVisualManager::OnFillRibbonButton  
 El marco de trabajo llama a este método cuando rellena el interior de un botón de la cinta de opciones.  
  
```  
virtual COLORREF OnFillRibbonButton(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a un [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md) objeto. El marco de trabajo rellena el interior de este botón de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 El color del texto del botón de la cinta de opciones especificado por `pButton` si el botón de la cinta de opciones admite texto. Un valor de -1 si el texto no es válido para el botón de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los botones de la cinta.  
  
##  <a name="a-nameonfillribbonedita--cmfcvisualmanageronfillribbonedit"></a><a name="onfillribbonedit"></a>CMFCVisualManager::OnFillRibbonEdit  
 El marco de trabajo llama a este método cuando rellena el interior de una instancia de la `CMFCRibbonRichEditCtrl` clase.  
  
```  
virtual void OnFillRibbonEdit(
    CDC* pDC,  
    CMFCRibbonRichEditCtrl* pEdit,  
    CRect rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPaneHighlighted,  
    BOOL bIsDisabled,  
    COLORREF& clrText,  
    COLORREF& clrSelBackground,  
    COLORREF& clrSelText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pEdit`  
 Un puntero a un `CMFCRibbonRichEditCtrl` objeto. El marco de trabajo rellena el interior de este control de edición.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del control de edición.  
  
 [in] `bIsHighlighted`  
 Parámetro booleano que indica si se resalta el control de edición.  
  
 [in] `bIsPaneHighlighted`  
 Parámetro booleano que indica si se resalta el panel principal.  
  
 [in] `bIsDisabled`  
 Parámetro booleano que indica si el control de edición no está disponible.  
  
 [in] `clrText`  
 Una referencia para el color del texto del control de edición.  
  
 [in] `clrSelBackground`  
 Una referencia al color de fondo del control de edición cuando se resalta.  
  
 [in] `clrSelText`  
 Una referencia al color del texto seleccionado en el control de edición.  
  
### <a name="remarks"></a>Comentarios  
 El `CMFCRibbonRichEditCtrl` indicado por `pEdit` puede formar parte de un botón de cuadro combinado en la cinta de opciones.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un `CMFCRibbonRichEditCtrl`.  
  
##  <a name="a-nameonfillribbonmainpanelbuttona--cmfcvisualmanageronfillribbonmainpanelbutton"></a><a name="onfillribbonmainpanelbutton"></a>CMFCVisualManager::OnFillRibbonMainPanelButton  
 El marco de trabajo llama a este método cuando rellena el interior de un botón de cinta que se encuentra en la **principal** panel.  
  
```  
virtual COLORREF OnFillRibbonMainPanelButton(
    CDC* pDC,  
    CMFCRibbonButton* pButton);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pButton`  
 Un puntero a un [CMFCRibbonButton clase](../../mfc/reference/cmfcribbonbutton-class.md) objeto. El marco de trabajo rellena este botón de la cinta de opciones.  
  
### <a name="return-value"></a>Valor devuelto  
 El color del texto del botón de la cinta de opciones especificado por `pButton` si el botón de la cinta de opciones admite texto. Un valor de -1 si el texto no es válido para el botón de la cinta de opciones.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los botones de la cinta en la **principal** panel.  
  
##  <a name="a-nameonfillribbonmenuframea--cmfcvisualmanageronfillribbonmenuframe"></a><a name="onfillribbonmenuframe"></a>CMFCVisualManager::OnFillRibbonMenuFrame  
 El marco de trabajo llama a este método cuando se llena el marco de menú del panel de la cinta.  
  
```  
virtual void OnFillRibbonMenuFrame(
    CDC* pDC,  
    CMFCRibbonMainPanel* pPanel,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pPanel`  
 Un puntero a una instancia de la [CMFCRibbonMainPanel clase](../../mfc/reference/cmfcribbonmainpanel-class.md). El marco de trabajo rellena el marco de menú para este panel de la cinta de opciones.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del marco de menú.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de la barra de menús para el `CMFCRibbonMainPanel`.  
  
##  <a name="a-nameonfillribbonquickaccesstoolbarpopupa--cmfcvisualmanageronfillribbonquickaccesstoolbarpopup"></a><a name="onfillribbonquickaccesstoolbarpopup"></a>CMFCVisualManager::OnFillRibbonQuickAccessToolBarPopup  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnFillRibbonQuickAccessToolBarPopup(
    CDC* pDC,  
    CMFCRibbonPanelMenuBar* pMenuBar,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 [in] `pMenuBar`  
 [in] `rect`  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonfillsplitterbackgrounda--cmfcvisualmanageronfillsplitterbackground"></a><a name="onfillsplitterbackground"></a>CMFCVisualManager::OnFillSplitterBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de una ventana divisora.  
  
```  
virtual void OnFillSplitterBackground(
    CDC* pDC,  
    CSplitterWndEx* pSplitterWnd,  
    CRect rect);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `pSplitterWnd`  
 Un puntero a una instancia de la [CSplitterWndEx clase](csplitterwndex-class.md). El marco de trabajo rellena en el fondo de esta ventana divisora.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites de la ventana divisora.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de una ventana divisora.  
  
##  <a name="a-nameonfilltaba--cmfcvisualmanageronfilltab"></a><a name="onfilltab"></a>CMFCVisualManager::OnFillTab  
 El marco de trabajo llama a este método cuando se llena el fondo de una ventana de ficha.  
  
```  
virtual void OnFillTab(
    CDC* pDC,  
    CRect rectFill,  
    CBrush* pbrFill,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectFill`  
 Un rectángulo que especifica los límites de la ventana de la ficha.  
  
 [in] `pbrFill`  
 Puntero a un pincel. El marco de trabajo usa este pincel para rellenar la ventana de la ficha.  
  
 [in] `iTab`  
 El índice de tabulación de base cero de una pestaña para que el marco de trabajo rellena el fondo.  
  
 [in] `bIsActive`  
 `TRUE`Si la ficha está activa; de lo contrario, `FALSE`.  
  
 [in] `pTabWnd`  
 Un puntero al control primario.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de fichas.  
  
##  <a name="a-nameonfilltasksgroupinteriora--cmfcvisualmanageronfilltasksgroupinterior"></a><a name="onfilltasksgroupinterior"></a>CMFCVisualManager::OnFillTasksGroupInterior  
 El marco de trabajo llama a este método cuando rellena el interior de un [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md) objeto.  
  
```  
virtual void OnFillTasksGroupInterior(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del grupo de tareas.  
  
 [in] `bSpecial`  
 Valor booleano que indica si el interior se rellena con un color especial.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un grupo de tareas.  
  
##  <a name="a-nameonfilltaskspanebackgrounda--cmfcvisualmanageronfilltaskspanebackground"></a><a name="onfilltaskspanebackground"></a>CMFCVisualManager::OnFillTasksPaneBackground  
 El marco de trabajo llama a este método cuando se llena el fondo de un [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) control.  
  
```  
virtual void OnFillTasksPaneBackground(
    CDC* pDC,  
    CRect rectWorkArea);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectWorkArea`  
 Un rectángulo que especifica los límites del panel de tareas.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de un `CMFCTasksPane` objeto.  
  
##  <a name="a-nameonhighlightmenuitema--cmfcvisualmanageronhighlightmenuitem"></a><a name="onhighlightmenuitem"></a>CMFCVisualManager::OnHighlightMenuItem  
 El marco de trabajo llama a este método cuando dibuja un elemento de menú resaltado.  
  
```  
virtual void OnHighlightMenuItem(
    CDC* pDC,  
    CMFCToolBarMenuButton* pButton,  
    CRect rect,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Un puntero al contexto de dispositivo para un menú.  
  
 [in] `pButton`  
 Un puntero a un [CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md) objeto que se va a mostrar. La implementación predeterminada no utiliza este parámetro.  
  
 [in] `rect`  
 Un rectángulo que especifica los límites del elemento de menú.  
  
 [in] `clrText`  
 Color del texto actual de elementos de menú seleccionados. La implementación predeterminada no utiliza este parámetro.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de este método no utiliza los parámetros `pButton` o `clrText`. Rellene el rectángulo especificado por `rect` con el color de fondo estándar.  
  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los elementos de menú seleccionados. Utilice la `clrText` parámetro para modificar el color del texto de un elemento de menú resaltado.  
  
##  <a name="a-nameonhighlightrarelyusedmenuitemsa--cmfcvisualmanageronhighlightrarelyusedmenuitems"></a><a name="onhighlightrarelyusedmenuitems"></a>CMFCVisualManager::OnHighlightRarelyUsedMenuItems  
 El marco de trabajo llama a este método cuando dibuja un comando de menú resaltado.  
  
```  
virtual void OnHighlightRarelyUsedMenuItems(
    CDC* pDC,  
    CRect rectRarelyUsed);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `rectRarelyUsed`  
 Un rectángulo que especifica los límites del comando resaltado.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los comandos de menú resaltado.  
  
##  <a name="a-nameonncactivatea--cmfcvisualmanageronncactivate"></a><a name="onncactivate"></a>CMFCVisualManager::OnNcActivate  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnNcActivate(
    CWnd* pWnd,  
    BOOL bActive);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 [in] `bActive`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameonncpainta--cmfcvisualmanageronncpaint"></a><a name="onncpaint"></a>CMFCVisualManager::OnNcPaint  
 El marco de trabajo llama a este método cuando dibuja el área no cliente.  
  
```  
virtual BOOL OnNcPaint(
    CWnd* pWnd,  
    const CObList& lstSysButtons,  
    CRect rectRedraw);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana cuyo área no cliente dibuja el marco de trabajo.  
  
 [in] `lstSysButtons`  
 Una lista de botones de sistema. También conocido como estos son los botones de título.  
  
 [in] `rectRedraw`  
 Un rectángulo que especifica los límites del área no cliente.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor reservado. La implementación predeterminada devuelve `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Invalide este método en un administrador visual derivado para personalizar la apariencia de los botones de fotograma y el título de ventana.  
  
##  <a name="a-nameonsetwindowregiona--cmfcvisualmanageronsetwindowregion"></a><a name="onsetwindowregion"></a>CMFCVisualManager::OnSetWindowRegion  
 El marco de trabajo llama a este método después de establecer una región que contiene marcos y menús emergentes.  
  
```  
virtual BOOL OnSetWindowRegion(
    CWnd* pWnd,  
    CSize sizeWindow);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Puntero a la ventana con la región que ha cambiado.  
  
 [in] `sizeWindow`  
 El tamaño de la ventana.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el método es correcto; `FALSE` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método para notificar al administrador visual que se ha establecido una región para los marcos y los menús emergentes. Para obtener más información, consulte [CWindow::SetWindowRgn](../../atl/reference/cwindow-class.md#setwindowrgn).  
  
##  <a name="a-nameonupdatesystemcolorsa--cmfcvisualmanageronupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManager::OnUpdateSystemColors  
 El marco de trabajo llama a esta función cuando cambia los colores del sistema.  
  
```  
virtual void OnUpdateSystemColors();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a este método como parte del procesamiento de la `WM_SYSCOLORCHANGE` mensaje. La implementación predeterminada no hace nada. Invalide este método en un administrador visual derivado si desea ejecutar código personalizado cuando cambian los colores de la aplicación.  
  
##  <a name="a-nameredrawalla--cmfcvisualmanagerredrawall"></a><a name="redrawall"></a>CMFCVisualManager::RedrawAll  
 Inmediatamente se vuelve a dibujar las barras de control en la aplicación.  
  
```  
static void RedrawAll();
```  
  
##  <a name="a-nameribboncategorycolortorgba--cmfcvisualmanagerribboncategorycolortorgb"></a><a name="ribboncategorycolortorgb"></a>CMFCVisualManager::RibbonCategoryColorToRGB  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual COLORREF RibbonCategoryColorToRGB(AFX_RibbonCategoryColor color);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `color`  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdefaultmanagera--cmfcvisualmanagersetdefaultmanager"></a><a name="setdefaultmanager"></a>CMFCVisualManager::SetDefaultManager  
 Establece el administrador predeterminado.  
  
```  
static void SetDefaultManager(CRuntimeClass* pRTI);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `pRTI`  
 Puntero a la información en tiempo de ejecución para un administrador visual.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `CMFCVisualManager` clase y cualquier derivado administradores visuales para personalizar la apariencia de la aplicación. Después de establecer el administrador visual de forma predeterminada, este método vuelve a dibujar la aplicación mediante el administrador visual de nuevo. Para obtener más información sobre cómo usar administradores visuales, vea [Administrador de visualización](../../mfc/visualization-manager.md).  
  
 Utilice este método para cambiar el administrador visual que utiliza la aplicación.  
  
##  <a name="a-namesetembossdisabledimagea--cmfcvisualmanagersetembossdisabledimage"></a><a name="setembossdisabledimage"></a>CMFCVisualManager::SetEmbossDisabledImage  
 Habilita o deshabilita el modo de relieve para imágenes de barras de herramientas.  
  
```  
void SetEmbossDisabledImage (BOOL bEmboss = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEmboss`  
 Parámetro booleano que indica si se debe habilitar el modo de relieve para imágenes de barras de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la función [CMFCVisualManager::IsEmbossDisabledImage](#isembossdisabledimage) para determinar si está habilitado el modo en relieve.  
  
##  <a name="a-namesetfadeinactiveimagea--cmfcvisualmanagersetfadeinactiveimage"></a><a name="setfadeinactiveimage"></a>CMFCVisualManager::SetFadeInactiveImage  
 Habilita o deshabilita el efecto de iluminación para imágenes inactivos en un menú o barra de herramientas.  
  
```  
void SetFadeInactiveImage(BOOL bFade = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bFade`  
 Parámetro booleano que especifica si se habilita el efecto de iluminación.  
  
### <a name="remarks"></a>Comentarios  
 Controles de esta característica si aparecen imágenes inactivas erróneas en un menú o barra de herramientas. Utilice el método [CMFCVisualManager::IsFadeInactiveImage](#isfadeinactiveimage) para determinar si está habilitada esta característica.  
  
##  <a name="a-namesetmenuflatlooka--cmfcvisualmanagersetmenuflatlook"></a><a name="setmenuflatlook"></a>CMFCVisualManager::SetMenuFlatLook  
 Establece una marca que indica si los botones de menú aparecen sin formato. De lo contrario, aparecen tridimensionales.  
  
```  
void SetMenuFlatLook(BOOL bMenuFlatLook = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bMenuFlatLook`  
 Parámetro booleano que indica si los botones de menú aparecen sin formato.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta característica no está habilitada.  
  
##  <a name="a-namesetmenushadowdeptha--cmfcvisualmanagersetmenushadowdepth"></a><a name="setmenushadowdepth"></a>CMFCVisualManager::SetMenuShadowDepth  
 Establece el ancho y alto de la sombra del menú.  
  
```  
void SetMenuShadowDepth(int nDepth);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nDepth`  
 Un entero que especifica la profundidad de la sombra de menú en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 El alto y ancho de la sombra de menú deben ser idénticos. El valor predeterminado es 7 píxeles.  
  
##  <a name="a-namesetshadowhighlightedimagea--cmfcvisualmanagersetshadowhighlightedimage"></a><a name="setshadowhighlightedimage"></a>CMFCVisualManager::SetShadowHighlightedImage  
 Establece una marca que indica si la [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md) muestra sombras para imágenes de resaltado.  
  
```  
void SetShadowHighlightedImage(BOOL bShadow = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bShadow`  
 Parámetro booleano que indica si el administrador visual muestra una sombra en imágenes resaltadas.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, esta característica está deshabilitada.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager::GetInstance](#getinstance)   
 [Administrador de visualización](../../mfc/visualization-manager.md)



